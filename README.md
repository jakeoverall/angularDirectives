angularDirecitves
=================
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
