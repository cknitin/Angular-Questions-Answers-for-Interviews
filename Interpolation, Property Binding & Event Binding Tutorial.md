# Interpolation 
It allows you to define properties in a component class, and communicate these properties to and from the template.

    export class HomeComponent implements OnInit {
             itemCount: number = 4;
        constructor() { }
        ngOnInit() {
     
     }
    }

    <!-- From: -->
    <p>Your bucket list</p>

    <!-- To: -->
    <p>Your bucket list ({{ itemCount }})</p>


# Property binding 
    It's the same thing as interpolation, except you can set the properties and attributes of various HTML elements.

        btnText: string = 'Add an Item';    // Add this line

        <input type="submit" class="btn" [value]="btnText">

    # Two-Way Data Binding
    What if we wanted to use our input textfield to both retrieve and set its value from a component class? We can use what's called ngModel to create that 2-way data binding.
    First, we have to import the FormsModule in order to have access to ngModule

        import { FormsModule } from '@angular/forms';

        // Other imports removed for brevity

        @NgModule({
          ...
          imports: [
            BrowserModule,
            AppRoutingModule,
            FormsModule // Add the FormsModule here
          ],

          goalText: string = 'My first life goal';

          <input type="text" class="txt" name="item" placeholder="Life goal.." [(ngModel)]="goalText">

# Event binding 
It allows you to define events that occur in the template (user-initiated), and communicate to the component class. 

    <input type="submit" class="btn" value="{{ btnText }}" (click)="addItem()">

    export class HomeComponent implements OnInit {

      itemCount: number = 4;
      btnText: string = 'Add an Item';
      goalText: string = 'My first life goal';
      goals = [];

      constructor() { }

      ngOnInit() {
        this.itemCount = this.goals.length;
      }

      addItem() {
        this.goals.push(this.goalText);
        this.goalText = '';
        this.itemCount = this.goals.length;
      }

    }


      
