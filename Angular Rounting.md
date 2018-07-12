
# Routing

Create and add below line of code in src/app/app-routing.module.ts

    import { NgModule } from '@angular/core';
    import { Routes, RouterModule } from '@angular/router';
    import { HomeComponent } from './home/home.component';     // Add this
    import { AboutComponent } from './about/about.component';  // Add this

        const routes: appRoutes = [
          {
            path: '',
            component: HomeComponent
          },
          {
            path: 'about',
            component: AboutComponent
          }
        ];
    
       @NgModule({
        imports: [ RouterModule.forRoot(appRoutes) ],
        exports: [
            RouterModule
         ]
       }) 
       
Now Add below lines in src/app/app.module.ts
 
    import { RoutingModule } from './common/routing.module';
    
    @NgModule({
        imports: [ RoutingModule ]
       }) 
    
    export class AppModule { }
    
Open the app.component.html and add the following code

<ul>
  <li><a routerLink="">Home</a></li>
  <li><a routerLink="about">About</a></li>
</ul>

<router-outlet></router-outlet>
