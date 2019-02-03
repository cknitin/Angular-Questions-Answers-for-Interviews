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
 
