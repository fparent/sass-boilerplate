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


Structure
====================

* Mixins
* StarterCSS
* Helpers / Utility classes
* Brand, Skins and Themes
* Typography
* Base
* Structure (Layouts)
* Modules
* Pages
* Forms
* Plugins
* Media Queries
* CSS Print


Predefined Mixins and helpers
====================


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
    &lt;button class="btn"&gt;Default&lt;/button&gt;
    &lt;button class="btn btn-primary"&gt;Login&lt;/button&gt;


* A good rule of thumb is that anything within the body of a container is clearly a 
separate object. (OOCSS)
.sidebar ul { ... }
This is questionable because the UL is clearly a separate object.


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
    .module &gt; .box .title


* Every font-size property should be using REM units (root em) now. This way
every sizes will be relative to the base element (html in our projects) and allow
to create fully scalable projects. With a fallback to pixels for older browsers
(&lt;IE8), we have a consistent and predictable sizing in all browsers.(snook.ca).
<br /><br />To use, simply use the predefined mixins "@include font-size(nbPixels);".<br />For example:
    h1 { @include font-size(48); }
