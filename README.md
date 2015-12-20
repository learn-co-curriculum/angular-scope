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
references `$scope.name` in the controller. 
