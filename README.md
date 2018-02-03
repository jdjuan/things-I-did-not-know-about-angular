# Things I didn't know about Angular

1. That the `<input>` element has a method called `input` which can be used to detect when typing happens
1. Template variables serve mainly as a refernce to the element they are attached to. So later with an event, I can send them over to the component and work with them and their properties (element's properties)
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
1. When working with routes you can add the `[routerLinkActiveOptions]="{exact: true}"` directive to force the active class gets added only when it matches the exact route
1. Instead of creating every link in the navigation you might want to have a `*ngFor` instead.
1. The OnPush detection strategy allows you to makes updates to the template DOM by waiting for user's events or parent's. But when the component itself is the one causing the change, like when you subscribe inside the component instead of using the `async` pipe, then you can use: `ChangeDetectorRef.detectChanges()` or `ChangeDetectorRef.markForCheck()` to make force this edge cases to be considered
1. `NgComponentOutlet` is a router outlet without routes: A way to dynamically render components in a Host View.
1. Using a custom pipe brings the following advantages
    1. Performance: change detection strategy, once the DOM is update it won't re-operate the pipe into data passed
    1. Separation of concerns
1. You localize services per component ignoring the global instance of a service using the `providers` property of the `@component` decorator
1. `trackBy` helps you improve performance by rendering only the elements that changed inside an array of a `ngFor`
1. The newest version of `http` has `interceptors` that allow you to insert middleware logic in the pipeline. Request/Response objects become immutable. JSON format is assumed by default and no longer needs to be parsed
1. The TransferState module allows you to pass your state information from the server to the new bootstrapping client and so avoiding for example double http requests.
1. Guard events: `CanActivate, CanDeactivate, CanActivateChild, CanLoad (lazy), Resolve`

## JavaScript

1. That you can make object mutation immnutable by doing it like this: `passenger = Object.assign({}, passenger, newPassenger);`

## Notes

1. Tutorials are better understood when there is styling set up beforehand
