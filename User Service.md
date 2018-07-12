# User Service
Create user service to set token in local storage and get it from there.

Create a file name userservice.service.ts

import { Injectable } from '@angular/core';
import { Router } from '@angular/router';

@Injectable({
  providedIn: 'root'
})
export class UserService {

  constructor(private router: Router) { }

  setToken(token: string) {
    localStorage.setItem('LoggedInUser', token);
  }

  getToken() : string {
    return localStorage.getItem('LoggedInUser');
  }
  isLoggednIn() {
    if (this.getToken() !== null) {
      return true;
    }
    return false;
  }
  logout() {
    localStorage.removeItem('LoggedInUser');
    this.router.navigate(['/login']);
  }

}


Add the UserService in app.module.ts

import { RouterModule, Routes } from '@angular/router';

  @NgModule({
    imports: [],
    exports: [],
    providers: [UserService],
  })
 export class AppModule { }

