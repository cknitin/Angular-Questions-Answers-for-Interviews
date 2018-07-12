
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
Component Router Navigation            path: 'about',
            component: AboutComponent
          }
        ];
    
Component Router Navigation       @NgModule({
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
    
# Setting and Fetching Angular 5 Route Parameters

    {
        path: 'about/:id',             // Add /:id here
        component: AboutComponent
    }
    
    <li><a routerLink="about/48">About</a></li>
    
Open the about.component.ts and import ActivatedRoute

    import { Component, OnInit } from '@angular/core';
    import { ActivatedRoute } from '@angular/router';      // Add this
    
    export class AboutComponent implements OnInit {
  
      constructor(private route: ActivatedRoute) { 
        this.route.params.subscribe(res => console.log(res.id));
      }

      ngOnInit() {
      }

    }

# Component Router Navigation
    
Sometimes, you may need to change the router outlet component based on logic occurring in a component class.
In this case, let's import the Router from the angular/router within our about.component.ts file:

    import { Component, OnInit } from '@angular/core';
    import { ActivatedRoute } from '@angular/router';
    import { Router } from '@angular/router';             // Add this
    
    constructor(private route: ActivatedRoute, private router: Router) { 
        sendMeHome() {
        this.router.navigate(['']);
    }
    
    <p>
        This is what I'm all about. <a href="" (click)="sendMeHome()"><strong>Take me back</strong></a>.
    </p>
    
