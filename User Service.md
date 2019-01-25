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

---------------------------------------------------------------------------------------
# TO DO Services

    import { Injectable } from '@angular/core';
    import { HttpClient, HttpHandler, HttpHeaders } from '@angular/common/http';
    import { Todo } from '../models/todo';
    import { Observable } from 'rxjs';

    const httpOptions = {
      headers: new HttpHeaders({
        'Content-Type': 'application/json'
      })
    };

    @Injectable({
      providedIn: 'root'
    })

    export class TodoService {
      todosUrl = 'https://jsonplaceholder.typicode.com/todos';
      toDos: Todo[];
      constructor(private http: HttpClient) { }

      public GetToDos(): Observable<Todo[]> {
        return this.http.get<Todo[]>(this.todosUrl);
      }

      public PutToDos(toDo: Todo) {
        return this.http.put(this.todosUrl + '/post/1', toDo, httpOptions);
      }

      // Toggle Completed
      toggleCompleted(todo: Todo): Observable<any> {
        const url = `${this.todosUrl}/${todo.id}`;
        return this.http.put(url, todo, httpOptions);
      }
    }
-----------------------------------------------------------------------------
    
# Using ToDo Service in controller


    import { Component, OnInit } from '@angular/core';
    import { TodoService } from '../../services/todo.service';
    import { Todo } from '../../models/todo';

    @Component({
      selector: 'app-todo',
      templateUrl: './todo.component.html',
      styleUrls: ['./todo.component.css']
    })
    export class TodoComponent implements OnInit {

      toDos: Todo[];
      constructor(private toDoService: TodoService) {

          toDoService.GetToDos().subscribe(todos => {
            this.toDos = todos;
            console.log(JSON.stringify(todos));
          });
       }

      ngOnInit() {
      }

    }


