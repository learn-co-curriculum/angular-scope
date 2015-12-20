# The Angular Scope

## Objectives

1. Understanding that the scope is the ViewModel
2. Know how to use the scope in a view and a controller

## `$scope`

Now that we have created a controller and a template, we
need to somehow link them together. In our previous example,
our secretary was our way of communicating between the view 
and the controller. In Angular, our secretary is the scope.

To use the scope in our controller, we need to reference it
in as a function parameter.

```js
MyApp.controller('BigBoss', function($scope) {

})
```

So what can we do with the scope? Well, because it acts
like an empty object, we can store data in it!

```js
MyApp.controller('BigBoss', function($scope) {
  $scope.name = 'Big Boss'
})
```

Scope works very similarly in a view, except that any
variable reference in a view referrs to a key in the
scope.

```html
<script type="text/ng-template" id="telephone.html">
  <h1>Call for {{name}}</h1>
  <form class="telephone">
    <input type="text" name="notes" />
  </form>
</script>
```

In templates, we reference variables with handlebars, 
or `{{}}`. In our example, `{{name}}` in the view 
references `$scope.name` in the controller. And if you've
noticed, we created our first one-way binding! Essentially,
our handlebars served as our instruction to let the scope
update our view whenever the variable changes.

Now that we're able to pass data from the controller to the
view, how do we pass data from the view to controller? Angular 
does this through directives which are two-way bindings.

In order to pass the notes from the telephone back to our 
controller, we'll use a directive called `ng-model`

```html
<script type="text/ng-template" id="telephone.html">
  <h1>Call for {{name}}</h1>
  <form class="telephone">
    <input type="text" name="notes" ng-model="notes" />
  </form>
</script>
```

How does `ng-model` work? Well, lets trace its steps.

1. Type a letter into the input
2. Input has changed and notifies the scope of the change
3. The scope then updates `$scope.notes` with the value of 
   the field

Now at first, this looks like a one-way binding, but if we
were somehow able to change the value in the controller
the input would update itself with the scope's value making
it two ways.