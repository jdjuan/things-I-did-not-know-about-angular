# Things I didn't know about Angular

1. That the `<input>` element has a method called `input` which can be used to detect when typing happens
1. Template variables serve mainly as a refernce to the element they are attached to. So later with an event, I can send them over to the component and work with them and their properties (element's properties)
1. That you can make object mutation immnutable by doing it like this: `passenger = Object.assign({}, passenger, newPassenger);`
1. `@Injectable()` does not mean the class can be injected using DI, but instead that dependencies can be injected in that class such as: `private http: Http`
1. In forms, when using `ngModel` directive I can use the `(ngModelChange)` output to call a method when the model changes
1. In a `select` element I can have:
```
<select name="baggage" [ngModel]="detail?.baggage">
    <option *ngFor="let item of baggage" [value]="item.key" [selected]="item.key === detail?.baggage" >
    </option>
</select>

// It's the same as
<select name="baggage" [ngModel]="detail?.baggage">
    <option *ngFor="let item of baggage" [ngValue]="item.key">
      {{ item.value }}
    </option>
</select>
```

1. When you create a template variable you are exporting the element by default, but you can also export a specific proterty of that element, for example when you do: `#fullname = "ngModel"` so that you can validate it later
1. Tutorials are better understood when there is styling set up beforehand
1. When working with routes you can add the `[routerLinkActiveOptions]="{exact: true}"` directive to force the active class gets added only when it matches the exact route
1. Instead of creating every link in the navigatin you might want to have a `*ngFor` instead.