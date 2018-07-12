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

# Event binding 
It allows you to define events that occur in the template (user-initiated), and communicate to the component class. 
