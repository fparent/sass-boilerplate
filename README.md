Sass Boilerplate
====================

This is a lightweight Sass boilerplate to help you start and structure your projects properly. This codebase serves as your CSS starting point and will make development easier, faster, cleaner and funnier (according to Sass website).

If you're not familiar with Sass, no problem! You can still use this boilerplate with plain CSS (you'll need to install Sass on your server though) and get lots of benefits:

* StarterCSS: a custom CSS normalizer/reset (based on normalize.css by Nicolas Gallagher and Jonathan Neal) that will improve consistency and stability of all elements in different browsers
* Fragmented structure using multiple files to keep your code readable and simple to debug
* When rendering, files are merged in one monolithic and minimized file for performance
* Some helpers and utility classes predefined to speed up development
* Media queries available to help you create responsive websites
* Combines CSS best practices, tricks and techniques (such as OOCSS and SMACSS)



Mixins
--------------------

Predefined general styles. To use, simply use "@include nameOfMixin" in the selector.
Currently, the following mixins are available:
* font-size(px) - This should be called everywhere you would use the font-size property. It will convert the pixels value in "REM" for a more flexible approach in modern browsers, but keep the pixels value as fallback for older browsers.
* clearfix - if you want to apply the clearfix code directly in a selector instead of using the .clearfix class
* inline-block - apply the "inline-block" display mode to a container and fallback for old IEs
* add-border-radius(position, value) - set the border-radius for either all sides or a specified one


StarterCSS
--------------------

Corrects inconsistencies and provide useful basic styles
More info: https://github.com/fparent/StarterCSS


Helpers / Utility classes
--------------------

Predefined classes to manage states and layout. I strongly recommand you take a look on the available styles and used them as they reflect the latest development best practices.
Here's a preview of the most used helpers:
* .hide-text, .ir - clean approach for hidding text when using a background image
* .hidden, .hide - hide an element from the DOM
* .visible, .show - display an element as block
* .visuallyhidden - hide an element visually but NOT from screenreaders
* .clearfix
* .clear, .clearer - clear floated elements
* .right, .left - float an element in a specific direction


Brand, Skins and Themes
--------------------

 I find that most apps and sites utilize a couple main colors, which I describe as "brand". They are often used in the menus, buttons, etc and it's a good practice (for consistency's sake) to declare them once in a Sass variable and use them everywhere.
 Besides the main colors, this section can be used to declare styles for your logos, skins & themes specific to the websites, etc.


Typography
--------------------

Used to define the main headings, font styles, sizes, alternate text presentations, etc.


Base
--------------------

The base file is usually just for html & body selectors, but can be used to store the site's backgrounds and language specific elements.


Structure (Layouts)
--------------------

This is the blueprint of your project. It defines your grid design, your layout architecture (as suggested in SMACSS) but also your menus, sidebars, header/footer, wrappers and main container.
I personally like to use a structure similar to this:

<pre>
------------------------------------------------
|                    header                    |
------------------------------------------------
|                .main .wrapper                |
|  ------------------------------------------  |
|  |             .content .full             |  |
|  |   ---------------------------------    |  |
|  |   |                                |   |  |
|  |   |                                |   |  |
|  |   |                                |   |  |
|  |   |                                |   |  |
|  |   |                                |   |  |
|  |   |                                |   |  |
|  |   |                                |   |  |
|  |   ----------------------------------   |  |
|  |                                        |  |
|  ------------------------------------------  |
|                                              |
------------------------------------------------
|                    footer                    |
------------------------------------------------
</pre>


Modules
--------------------

As taught in SMACSS, modules are the reusable, modular, site-specific parts of our design. "They are the callouts, the sidebar sections, the product lists and so on. It is your navigation
bars and your carousels and your dialogs and your widgets and so on. This is the meat of the page." 


Pages
--------------------

This is where the page-specific styles reside.


Forms
--------------------

Basic styles for all your forms, inputs, buttons, error, etc.


Plugins
--------------------

Third party plugin stylesheets can become a mess in large websites. Sometimes your pages can require several plugins and instead of loading them all individually, you can place them all in one place (unless you need to edit them often). 


Media Queries
--------------------

Supports mobile/tablet landscape and portrait, laptop, desktop, large screens


CSS Print
--------------------

Custom CSS Print based on the one in HTML5 Boilerplate




Best practices and things to remember
====================

* Use classes to name your objects and their components rather than relying solely 
on the semantics of HTML. By referencing these classes in your stylesheets (say, 
rather than directly styling the &lt;img&gt; element), your HTML can be flexible. (OOCSS)


* An object should look the same no matter where you put it. So instead of styling 
a specific &lt;h2&gt; with .myObject h2 {...}, create and apply a class that describes the 
&lt;h2&gt; in question, like &lt;h2 class="category"&gt;. (OOCSS)


* Avoid using IDs unless they have a semantic meaning or serve a specific purpose,
like a JS hook or styling a very specific independant element. Otherwise they mess 
up specificity because they are too strong and are unique identifiers, which make 
them not reusable. (OOCSS)


* To create component variants that extend a base component (e.g., a button with 
a different coloured background or border), the "multi-class" pattern is more
scalable and allows more flexibility in big projects:
(About HTML semantics and front-end architecture)

        .btn { button template styles }
    	.btn-primary { styles specific to primary button }
    	<button class="btn">Default</button>
    	<button class="btn btn-primary">Login</button>

* A good rule of thumb is that anything within the body of a container is clearly a 
separate object.<br />The example below is questionable because the UL is clearly a separate 
object (OOCSS):

        .sidebar ul { ... }

* A state is something that augments and overrides all other styles. For example, 
an accordion section may be in a collapsed or expanded state. A message may be in a
success or error state. Use the "is-state" naming pattern. (SMACSS)


* Whenever possible, include third-party stylesheets inside the main css to prevent
additional server request and save time. This can be done automatically using a 
CSS pre-processor. 


* A "too-specific" name if always better than a "too-generic" name. It might be a
better idea to name the class of specific button "btn-big-red" instead of "btn".
(Help! My Stylesheets are a Mess!)


* Keep your CSS selectors short! To increase efficiency and reduces chances of 
selector breakage, a good rule of thumb is to use, when possible, a maximum of 
3 selectors:

        .module > .box .title


* Every font-size property should be using REM units (root em) now. This way
every sizes will be relative to the base element (html in our projects) and allow
to create fully scalable projects. With a fallback to pixels for older browsers
(&lt;IE8), we have a consistent and predictable sizing in all browsers.(snook.ca).
<br /><br />To use, simply use the predefined mixins "@include font-size(nbPixels);".
<br />For example:

        h1 { @include font-size(48); }
