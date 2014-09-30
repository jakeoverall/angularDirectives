angularDirecitves
=================
Angular allows us to create these great things called directives. Directives are essentially small pieces of functionality our app needs that can be bundled up into individual components. 

These components allow us to reuse code within our project, and throughout other projects.



#The Anatomy of an Angular Directive - a reference.
````javascript
	var app = angular.module('NAME-OF-APP', []);

	app.directive('nameOfDirective', function() {
		//our directive's name 'nameOfDirective' will be 
		//parsed to show up as 'name-of-directive' in our HTML.

		return {
			//you have 4 restrict options. You can use any of the 4 in any combonation.
			//{'E': 'Element', 'A': 'Attribute', 'C': 'Class', 'M': 'Comment'}
			//typically we create them as Elements or Attributes.
			restrict: 'EA',
			scope: {
				name: '=name' //The name of the directives scope and be set
			},				  //in the name attribute on the directive's element.
			template: '<div><h1>Hello World</h1></div>', 
			// the template can take raw HTML, or a file path that leads to an HTML file.
			// Like so:
			templateUrl: 'app/views/directiveView.html',

			controller: function($scope) { //We can create a controller in our directive!
				$scope.test = 'OMG!';
			},
			//this allows us to a special controller that nothing else can touch. 
			replace: true, //If we are using a template, we can choose to 
			//insert it's value wherever we call the directive.
			    link: function(scope, elem, attr) {
		      // scope is the directive's scope,
		      // elem is a jquery lite (or jquery full) object for the directive root element.
		      // attr is a dictionary of attributes on the directive element.
		      elem.bind('dblclick', function() {

		      });
		    }
		}

	})
````

###Note:
Most of these attributes within the directive example above are optional. For more information about directives visit the documentation at: https://docs.angularjs.org/guide/directive


###Walkthrough
If you dig through the angular documentation and as you become more familiar with directives you will notice that angular is heavily dependent in its use of directives. A few example directives that you use all the time even if you weren't aware of it are: 

+ ng-app
+ ng-view
+ ng-repeat
+ ng-click
+ ect...

####Step 1

We are now going to embrace the modularity of angular and create our first reusable module. This means that the custom directive that you write here will be easy to reuse in all of your projects by simply injecting your module into your apps dependencies. To get started lets create a new and setup our angular module. 

<i>myDirectives.js</i>

  var app = angular.module('myDirectives', []);
  
You are familiar with creating controllers, factories, and services already and the markup for starting a directive looks very similar. 

  app.directive('camelCase', function(){
    //directive stuff here...
  });

####Dont get tripped up.
Despite looking just like a controller or a service there are a few things to be cautious of when working with directives. The first is naming conventions. Remember that Javascript conventions say we should use camelCase while Html conventions state that we should use snake-case. Angular trying to keep with best practices holds true to these conventions so whatever you name your directive here will later be called in your Html using snake-case

  ex. <div camel-case></div>
  ex. <div ng-view></div>
  
Angular handles the conversion of your naming process itself so you don't have to worry about it, however if you didn't know it was happening you would have a very hard time debugging your code.  

####Step 2

#####pending Directive
Now that we have created our basic setup lets focus on building a directive that we can put on a <button></button> element that will show a loading gif while we wait for our data from an $http request. Lets create a new directive on our app and lets give it the name 'pending'. We then will setup the basic anatomy of a directive.

  return {
    restrict: 'AE',
    scope: {},
    link: function(){
      //Code Here
    }
  }
  
Notice a directive is a really a function that is returning an object, and on this object we are adding some very specific keys. These keys are setup and will be evaluted by angular  