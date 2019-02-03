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
 

# Form State and Input State
AngularJS is constantly updating the state of both the form and the input fields.

## Input fields have the following states:

$untouched The field has not been touched yet
$touched The field has been touched
$pristine The field has not been modified yet
$dirty The field has been modified
$invalid The field content is not valid
$valid The field content is valid
They are all properties of the input field, and are either true or false.

## Forms have the following states:

$pristine No fields have been modified yet
$dirty One or more have been modified
$invalid The form content is not valid
$valid The form content is valid
$submitted The form is submitted
They are all properties of the form, and are either true or false.
