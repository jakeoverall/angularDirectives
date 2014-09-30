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