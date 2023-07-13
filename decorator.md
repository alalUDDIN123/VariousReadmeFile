In Angular, decorators are functions that know the configuration of classes and how they are supposed to work.

Decorators in Angular are denoted by the `@` symbol and are applied using the TypeScript language feature called "decorators." Some commonly used decorators in Angular include:

There are four main types of angular decorators:

- `Class decorators` : @Component, @NgModule, @Directive & @Pipe
- `Property decorator` : @Input and @Output
- `Method decorators` : @HostListener
- `Parameter decorators` :  @Inject

1. `@Component`: This decorator is used to define an Angular component. It is applied to a class and specifies metadata such as the HTML template, CSS styles, and other component-related configurations.

```typescript
@Component({
  selector: 'app-example',
  templateUrl: './example.component.html',
  styleUrls: ['./example.component.css']
})
export class ExampleComponent {
  // Component logic goes here
}
```

2. `@NgModule`: This decorator is used to define an Angular module. It is applied to a class and provides metadata about the module, including its imports, exports, and declarations.

```typescript
@NgModule({
  imports: [CommonModule],
  declarations: [ExampleComponent],
  exports: [ExampleComponent]
})
export class ExampleModule {
  // Module logic goes here
}
```

3. `@Directives`: It is used to define a custom directive, which is a reusable behavior or functionality that can be applied to elements in the DOM.

```typescript
@Directive({
  selector: '[appCustomDirective]'
})
export class CustomDirective {
  constructor(private elementRef: ElementRef) {
    this.elementRef.nativeElement.style.backgroundColor = 'yellow';
  }
}

```

4. `@Input` and `@Output`: These decorators are used to define the input and output properties of an Angular component. The `@Input` decorator allows a value to be passed into a component from its parent, while the `@Output` decorator emits events from a component to its parent.

```typescript
@Component({
  selector: 'app-child',
  template: `
    <button (click)="onClick()">Click Me</button>
  `
})
export class ChildComponent {
  @Input() name: string;
  @Output() clicked: EventEmitter<void> = new EventEmitter<void>();

  onClick() {
    this.clicked.emit();
  }
}
```

