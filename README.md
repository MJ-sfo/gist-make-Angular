Stuff that has been said about Angular:

A "framework for dynamic web apps"
"Lets you use HTML as your template language"
"Handles all of the DOM and AJAX glue code you once wrote by hand and puts it in a well-defined structure"
"Not every app is a good fit for Angular. Angular was built with the CRUD application in mind."

__________________
Event Binding
Here's an example how we might bind to a button tag being clicked (the "click event").

<button>Pick Me!</button>

$("button").on("click", function(event){
    alert("You clicked the button!")
});
// or, using the shorthand
$("button").click(function(event){
    alert("You clicked the button!")
});

To make the same button alert us on click, Angular would do it this way:
<button ng-click="$window.alert('Holy moly!')">Pick Me!</button>

__________________
In Angular, we add behavior to HTML through directives. A directive is a marker on a HTML tag that tells Angular to run or reference Angular code. You've already seen several!

Angular directives start with the prefix ng-

A few that will be important to know:

ng-app turns ordinary HTML into an Angular application. You will need Angular loaded into your project (via a package manager or CDN) for this to work.

ng-controller connects a controller (a JavaScript file containing logic) to a section of our application.

ng-model ties together (binds) values in HTML and data in the controller.

ng-repeat iterates over a collection and can display a chunk of html once for each element in the collection.

ng-controller

Controllers contain the business logic for our application. They're the place that we're going to be writing our JavaScript.

__________________
This is typically what it looks like to define a controller:
(example using app.js)

angular
  .module('tunely',[])
  .controller('AlbumsIndexController', AlbumsIndexController);

  function AlbumsIndexController() {
    var vm = this;
    vm.thing = {};
    vm.func = function(){};
    // more logic here
  }

  we give a controller a name 'AlbumsIndexController'
  then pass a function that defines all of the logic within that controller

  To use our controller in our View we have to declare it somewhere - but with abriviated name.    In index.html

<div ng-controller="AlbumsIndexController as albumsIndexCtrl">
	<!--placeholder for now-->
</div>

In our view, if we want to refer to any of the logic defined in the controller, we can use {{albumsIndexCtrl.thing}} or {{albumsIndexCtrl.func()}}.

__________________
If a user wants to use an input element to create a piece of accessible data, ng-model is the directive for the job!.

  <div ng-controller="SampleCtrl">

    <span>Enter your name:</span>
    <input type="text" ng-model="myName">

    <h1>{{ myName }}</h1>

  </div>
 Using an angular expression we can then display the current value of that myName variable as it changes.

 
