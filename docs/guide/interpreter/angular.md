# Angular Interpreter

>Please note that this feature is in beta and is only available for selected customers.

The AngularJS interpreter is the port of the [Frontend Angular API](https://zeppelin.apache.org/docs/0.8.0/usage/display_system/angular_frontend.html#frontend-angular-api-in-apache-zeppelin) in *Apache Zeppelin*
.

Using the AngularJS interpreter you can render [AngularJS 1.7](https://docs.angularjs.org/misc/version-support-status#long-term-support) templates on Zepl paragraphs and leverage the robust two-way binding system. Similar to *Apache Zeppelin* we expose a simple `AngularJS z object` on the front-end side to expose the same capabilities. This z object is accessible in the Angular isolated scope for each paragraph.

You don't need to create new resources or interpreters to start using the Angular interpreter. All you need to do is add the magic keyword `%angular` to the first line of your paragraph.

### API

| Actions             | API                                           |
|---------------------|-----------------------------------------------|
| Initiate binding    | z.angularBind(var, initialValue, paragraphId) |
| Update value        | z.angularBind(var, newValue, paragraphId)     |
| Destroy binding     | z.angularUnbind(var, paragraphId)             |
| Execute Paragraph   | z.runParagraph(paragraphId)                   |

#### Basic example

* In paragraph A (you can find each paragraph's id in its context menu):

```
%angular

<form class="form-inline">
  <div class="form-group">
    <label for="superheroId">Super Hero: </label>
    <input type="text" class="form-control" id="superheroId" placeholder="Superhero name ..." ng-model="superhero"></input>
  </div>
  <p>We will bind {{superhero}} to next paragraph</p>
  <button type="submit" class="btn btn-primary" ng-click="z.angularBind('superhero',superhero,'20181127-043625_2107755481')"> Bind</button>
  <button type="submit" class="btn btn-primary" ng-click="z.runParagraph('20181127-043625_210775548')"> Run {{superhero}}</button>
  <button type="submit" class="btn btn-primary" ng-click="z.angularUnbind('superhero','20181127-043625_210775548')"> UnBind {{superhero}}</button>
</form>
```

* In paragraph `20181127-043625_210775548`:

```
%angular

<div class="card" style="width: 18rem;">
  <img class="card-img-top" src="//cdn.zepl.com/032d0183959db90c080f31a2dbae0b7e.gif" alt="Card image cap">
  <div class="card-body">
    <h5 class="card-title">SuperHero</h5>
    <p class="card-text">{{superhero}}</p>
  </div>
</div>
```
<img src="../../../img/intp_angular.gif" class="image-box big-img" />

### Angular API

We support Angular's [ng-directives](https://docs.angularjs.org/api/ng/directive) and [ng-filters](https://docs.angularjs.org/api/ng/filter). You can combine these to build interactive applications on the front-end.

#### Example

The following example uses `ng-init`, `ng-model` and `ng-repeat` directives and `ng-filter(filter:searchText)` to make a filterable table.

```
%angular

<div ng-init="friends = [{name:'John', phone:'555-1276'},
                         {name:'Mary', phone:'800-BIG-MARY'},
                         {name:'Mike', phone:'555-4321'},
                         {name:'Adam', phone:'555-5678'},
                         {name:'Julie', phone:'555-8765'},
                         {name:'Juliette', phone:'555-5678'}]"></div>

<label>Search: <input ng-model="searchText"></label>
<table id="searchTextResults" class="table">
  <thead>
    <tr>
      <th>Name</th>
      <th>Phone</th>
    </tr>
  </thead>
  <tbody>
    <tr ng-repeat="friend in friends | filter:searchText">
      <td>{{friend.name}}</td>
      <td>{{friend.phone}}</td>
    </tr>
  </tbody>

</table>
```
