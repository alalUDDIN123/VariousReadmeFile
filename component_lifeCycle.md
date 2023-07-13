In Angular, components have a defined lifecycle consisting of several phases or hooks that allow developers to manage the behavior of a component at different stages. 

1. ngOnChanges(): This hook is called when one or more input properties of a component change. It receives a SimpleChanges object that contains the previous and current values of the input properties. This hook is commonly used to respond to input changes and perform calculations or updates based on the new values.

2. ngOnInit(): This hook is called after the first ngOnChanges() and only once when the component is initialized. It is used for initialization tasks such as retrieving data from a server, setting up subscriptions, or initializing variables.

3. ngDoCheck(): This hook is called during every change detection run, which can be triggered by various events such as user interactions or data changes. It is used for custom change detection and is often used with other hooks to optimize the performance of your application.

4. ngAfterContentInit(): This hook is called after the component's content has been projected into its view. It is used when a component has projected content using ng-content and you need to access that content or perform initialization tasks related to the projected content.

5. ngAfterContentChecked(): This hook is called after the change detection has checked the component's projected content. It is used for additional checks or actions that need to be performed after the content has been checked.

6. ngAfterViewInit(): This hook is called after the component's view and child views have been initialized. It is used when you need to access or manipulate the component's view or its child views.

7. ngAfterViewChecked(): This hook is called after the change detection has checked the component's view and child views. It is used for additional checks or actions that need to be performed after the view has been checked.

8. ngOnDestroy(): This hook is called just before the component is destroyed. It is used for cleanup tasks such as unsubscribing from observables, canceling timers, or releasing resources.

By implementing these lifecycle hooks in  component class, developers can control the behavior of  component at different stages of its lifecycle and perform necessary operations.

---
---


1. ngOnChanges():
```typescript
import { Component, Input, SimpleChanges } from '@angular/core';

@Component({
  selector: 'app-my-component',
  template: 'Input value: {{ inputValue }}'
})
export class MyComponent {
  @Input() inputValue: string;

  ngOnChanges(changes: SimpleChanges) {
    if (changes.inputValue) {
      console.log('Input value changed:', changes.inputValue.currentValue);
    }
  }
}
```

2. ngOnInit():
```typescript
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-my-component',
  template: 'Hello, {{ name }}!'
})
export class MyComponent implements OnInit {
  name: string;

  ngOnInit() {
    this.name = 'John Doe';
    console.log('Component initialized');
  }
}
```

3. ngDoCheck():
```typescript
import { Component, DoCheck } from '@angular/core';

@Component({
  selector: 'app-my-component',
  template: 'Counter: {{ counter }}'
})
export class MyComponent implements DoCheck {
  counter: number = 0;

  ngDoCheck() {
    console.log('Change detection triggered');
    // Perform custom change detection logic
    if (this.counter > 10) {
      // Do something
    }
  }

  incrementCounter() {
    this.counter++;
  }
}
```

4. ngAfterContentInit():
```typescript
import { Component, AfterContentInit, ContentChild } from '@angular/core';

@Component({
  selector: 'app-my-component',
  template: '<ng-content></ng-content>'
})
export class MyComponent implements AfterContentInit {
  @ContentChild('contentElement') contentElement: ElementRef;

  ngAfterContentInit() {
    console.log('Content initialized');
    console.log('Content Element:', this.contentElement.nativeElement);
  }
}
```
In the parent component:
```html
<app-my-component>
  <div #contentElement>Projecting content</div>
</app-my-component>
```

5. ngAfterContentChecked():
```typescript
import { Component, AfterContentChecked, ContentChild } from '@angular/core';

@Component({
  selector: 'app-my-component',
  template: '<ng-content></ng-content>'
})
export class MyComponent implements AfterContentChecked {
  @ContentChild('contentElement') contentElement: ElementRef;

  ngAfterContentChecked() {
    console.log('Content checked');
  }
}
```
In the parent component:
```html
<app-my-component>
  <div #contentElement>{{ someValue }}</div>
</app-my-component>
```

6. ngAfterViewInit():
```typescript
import { Component, AfterViewInit, ViewChild } from '@angular/core';

@Component({
  selector: 'app-my-component',
  template: '<p #viewElement>View Element</p>'
})
export class MyComponent implements AfterViewInit {
  @ViewChild('viewElement') viewElement: ElementRef;

  ngAfterViewInit() {
    console.log('View initialized');
    console.log('View Element:', this.viewElement.nativeElement);
  }
}
```

7. ngAfterViewChecked():
```typescript
import { Component, AfterViewChecked, ViewChild } from '@angular/core';

@Component({
  selector: 'app-my-component',
  template: '<p #viewElement>{{ someValue }}</p>'
})
export class MyComponent implements AfterViewChecked {
  @ViewChild('viewElement') viewElement: ElementRef;

  ngAfterViewChecked() {
    console.log('View checked');
  }
}
```

8. ngOnDestroy():
```typescript
import { Component, OnDestroy } from '@angular/core';

@Component({
  selector: 'app-my-component',
  template: 'Component will be destroyed'
})
export class MyComponent implements OnDestroy {
  ngOnDestroy() {
    console.log('Component destroyed');
    // Perform cleanup tasks
  }
}
```

These examples demonstrate the usage of Angular component lifecycle hooks to perform specific tasks at different stages of a component's lifecycle.