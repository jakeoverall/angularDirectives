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
			}				  //in the name attribute on the directive's element.
		}
	})
````