# Auth Guard

ng generate guard auth

      import { Injectable } from '@angular/core';
      import { CanActivate, ActivatedRouteSnapshot, RouterStateSnapshot, Router } from '@angular/router';
      import { Observable } from 'rxjs';
      import { UserService } from './services/userservice.service';

      @Injectable({
        providedIn: 'root'
      })
      export class AuthguardGuard implements CanActivate {
        constructor(private userService: UserService, private route: Router) {
        }
        canActivate(
          next: ActivatedRouteSnapshot,
          state: RouterStateSnapshot): Observable<boolean> | Promise<boolean> | boolean {
            if (!this.userService.isLoggednIn()) {
              this.route.navigate(['/login']);
            }
          return this.userService.isLoggednIn();
        }
      }
    
  
  
        import { RouterModule, Routes } from '@angular/router';

        import { DashboardComponent } from '../components/dashboard/dashboard.component';

        export const appRoutes: Routes = [
            { path: 'dashboard', component: DashboardComponent, canActivate: [AuthguardGuard] },
            { path: '**', redirectTo: 'login' }
          ];

          @NgModule({
            imports: [ RouterModule.forRoot(appRoutes) ],
            exports: [
                RouterModule
             ]
          })
         export class AppModule { }



