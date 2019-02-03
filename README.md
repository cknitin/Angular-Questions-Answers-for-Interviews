# Angular-Questions-Answers-for-Interviews
This repo contains all basic and advance angular questions for interviews

# *ngFor

    <p class="life-container" *ngFor="let goal of goals">
      {{ goal }}
    </p>


# Form Submit & Validation

    <form (ngSubmit)="register()" #registerForm="ngForm">
          <div class="form-group">
            <label for="email">Email</label>
            <input type="email" class="form-control" placeholder="email" pattern="^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$"    id="email"
              required [(ngModel)]="model.email" name="email" #email="ngModel">


            <div class="alert alert-danger" [hidden]="email.valid || email.untouched">
              <div *ngIf="email.errors && email.errors.required">
                Email is required
              </div>
              <div *ngIf="email.errors && email.errors.pattern">
                Email is invalid
              </div>
            </div>
          </div>
     </form>     
 

### CSS

    .ng-valid[required], .ng-valid.required  {
      border-left: 5px solid #42A948; /* green */
    }

    .ng-invalid:not(form)  {
      border-left: 5px solid #a94442; /* red */
    }

# Form State and Input State
AngularJS is constantly updating the state of both the form and the input fields.

## Input fields have the following states:

 - $untouched The field has not been touched yet
 - $tuched The field has been touched
 - $pistine The field has not been modified yet
 - $dirty The field has been modified
 - $invalid The field content is not valid
 - $valid The field content is valid
 - They are all properties of the input field, and are either true or false.

## Forms have the following states:

 - $pristine No fields have been modified yet
 - $dirty One or more have been modified
 - $invalid The form content is not valid
 - $valid The form content is valid
 - $submitted The form is submitted
 - They are all properties of the form, and are either true or false.
 
 # Reactive Form
 
 ## Step 1: Registering the reactive forms module
 
#### src/app/app.module.ts 

    import { ReactiveFormsModule } from '@angular/forms';

    @NgModule({
      imports: [
        ReactiveFormsModule
      ],
    })
    export class AppModule { }
 
 ## Step 2: Generating and importing a new form control
 
 ### Generate a component for the control.

    ng generate component NameEditor
    
 ### src/app/name-editor/name-editor.component.ts
 
    import { Component } from '@angular/core';
    import { FormControl } from '@angular/forms';

    @Component({
      selector: 'app-name-editor',
      templateUrl: './name-editor.component.html',
      styleUrls: ['./name-editor.component.css']
    })
    export class NameEditorComponent {
      name = new FormControl('');
    }
 
## Step 3: Registering the control in the template

### src/app/name-editor/name-editor.component.html

    <label>
      Name:
      <input type="text" [formControl]="name">
    </label>
    
### src/app/app.component.html (name editor)

    <app-name-editor></app-name-editor>
    
For more infromation

https://angular.io/guide/reactive-forms
