Angular JSPM directory and file layout
######################################

I've long been more of a server side developer, but recently I've been thrust 
into working with more and more front end code using Angular. Because of my 
general inexperience with front end stuff, I'm just now learning about things 
like "gulp", "grunt", "bower", "node" and "angular".  While all the "hip" kids 
are checking out Ember.js, with TypeScript, Babel, and gulp, I'm doing my best 
to catch up by learning Angular, Gulp, Karma and such. 

However, at a recent meeting, one of our really solid UI folks recommend that
we checkout and start working with JSPM, so I'm converting a sandbox app that 
I've been fiddling with into using the module loading style that JSPM 
encourages along with ES6. This project is (currently) an Angular 1.4 project
with the angular-material Material Design library stacked atop it. 

So far, the style has been pretty easy to adapt.  The ES6 require structure 
has necessitated changing the layout of my code quite a bit, but overall the
new structure has been pretty simple to adapt to, and it's easy to comprehend
what the changes are and why they're happening. 

One of the big changes is that each and every bit of the framework gets split 
out into a separate file. I was already breaking up my files a lot, but with 
JSPM, I find that I'm breaking things up into even more files. As an 
advantage, I find that I've hit upon a naming convention that, while verbose,
is pretty easy to find my way around using my editor (Usually Visual Studio
Code or Sublime Text). My general file layout is this:

 * static
   * components
     * user-list
	   * user-list.directive.js
	   * user-list.template.js
	   * user-list.tests.js
	   * user-list.controller.js
	 * calendar
	   * calendar.directive.js
	   * calendar.template.js
	   * calendar.tests.js
	 * components.module.js
	 * components.config.js
   * services
     * data
	   * data.service.js
	 * date
	   * date.service.js
     * services.module.js
   * app.js
   * app.config.js
   * app.controller.js
   
The contents of these various files should be roughly self-evident from the 
names, but the idea is that effectively every Angular component is defined 
and exported in its own file, and then imported into the appropriate file(s).
For example, the controllers for each component are defined in the 
".controller.js" file for that component, but is imported only into the 
".directive.js" file in most cases.  Each directive is defined and exported 
from the ".directive.js" file, and then imported into the 
"components.module.js" file.  In turn, the app.js imports all of the 
".module.js" files to define the top level module. 