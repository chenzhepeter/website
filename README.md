Website
=======


The two main libraries that are used to create this website are bootstrap and highcharts.  
	
	
Bootstrap is for the layout (Tabs, dropdown menus, popups) and information can be found from their website, http://getbootstrap.com/2.3.2/.  Additional resources can be found from jasny (http://jasny.github.io/bootstrap/index.html).  File upload was used from jasny.  
	
	
 Highcharts is a charts library written in javascript.  There are two javascript files.  Highcharts.js creates the actual chart and exporting.js lets a user print or save the image (button on the top right corner of a chart).  There are other resources that can be found on their website, but these are the two necessary ones.  The documentation for highcharts can be found here http://api.highcharts.com/highcharts and examples for specific types of charts can be found here http://www.highcharts.com/demo/.  The one extension from highcharts that was added was the regression.js page.  This creates the regression line from the scatter plot.  The code to create the line can be found from the scan vs. favourite scatter plot.  Under series, there is a type: ‘line’.  Under ‘data’, it shows:` (function() {return fitData(favourite).data;})()` , where favourite is the data (array of points).  The source of this can be found here: https://github.com/virtualstaticvoid/highcharts_trendline.
	
The website content is located in the dashboard.html page.  There are brief comments throughout the page to identify what each section is.  Since there is no server-side scripting, there are a lot of links and submit buttons that do not do anything.  The White Wine page will look exactly like the Red Wine page, but it is not done.  The form values are just added in the input attribute.  	
Javascript
----------

The variable `string` is a json object with all the data for the charts in the website.  It also includes a boolean value (under `warning`) to denote whether or not there is a scanning error. 
The next 100 lines of code or so are to extract the information from the json object into variables that will later be used in the charts.  
All the charts in the website are created from lines 193-995.  	Most of the code to create the graph is intuitive and further features can be added to these graphs by looking at the highcharts API.  All graphs have to be rendered to a div in the html section. For example,`$('#UniqueScanCount').highcharts...` will render the graph to the div with id `UniqueScanCount`.  There are other methods to render graphs as shown from lines 311-386, where the same graph is rendered to two different divs.  For the bar graph, `x-axis -> categories` defines the x-axis titles and the corresponding data can be inputted under `series -> data`.  Both inputs for categories and data should be arrays.  
For line charts, they are very similar to bar charts, except the type of the chart should be `line` instead of `column`.  
The scatter plot (line 592-643) has  type `scatter`.  The data in a scatter plot can be inputted under `series -> data` as a 2D array.  The regression line is created from lines 635-639.
The pie chart needs to have `pie` under `plotOptions` (the type is unnecessary).  Under `series -> data`, the data is a 2D array as well where the category is in the first index and the number is in the second index.  All the pie charts have a change function associated with them because the pie chart will be reloaded when a different select option is selected.  Look at the sample code from lines 775-786.

Line 990 enables the bootstrap popover which is used in the Product and Interaction sections of the website. 
Lines 992-999 changes the content of the warning div to change it from NO ERROR to ERROR.  It changes css styles, icons, and the text of the Warning. 
The purpose of line 1001-1003 is to give each tab a unique url so it can be linked from other pages.  It is necessary for the Add Category select option under category in the page, Add/Edit Product.	

HTML 
----
The header is the black section of the page.

The tab menu is the first line under the header with the links to all the tabs in the page.  There are dropdowns for two of the tabs.  The `data-toggle` attribute is necessary to navigate between different bootstrap components(tabs, dropdowns, modals, popovers, etc.).  To link from  a tab to its page, the `<a>` tag is used such as `<a href="#authentication" data-toggle='tab'>Authentication</a>`.  There is an div with the id `authentication` with the content of the authentication page.  All the tabs are under the `.tab-content` and each specific tab is contained inside of `tab-pane`.

If there is a class used in the html section, it is a probably a bootstrap component.  A lot of them are used so the can be looked up in the bootstrap documentation if necessary.  Everything used in this website so far are:

* [rows and spans (for layout)](http://getbootstrap.com/2.3.2/scaffolding.html#gridSystem)
* [modals](http://getbootstrap.com/2.3.2/javascript.html#modals)
* [popovers](http://getbootstrap.com/2.3.2/javascript.html#popovers)
* [form-horizontal, control labels, and controls (form layout)](http://getbootstrap.com/2.3.2/base-css.html#forms)
* [breadcrumb](http://getbootstrap.com/2.3.2/components.html#breadcrumbs)
* [buttons](http://getbootstrap.com/2.3.2/base-css.html#buttons)
* [tables](http://getbootstrap.com/2.3.2/base-css.html#tables)
* [icons](http://getbootstrap.com/2.3.2/base-css.html#icons)
* [navigation (tab menu)](http://getbootstrap.com/2.3.2/components.html#navs) and [tabs](http://getbootstrap.com/2.3.2/javascript.html#tabs)

CSS
---
Most of the CSS is located in the file `bootstrap.css`.  Lines 11-188 are user-defined and most of it is positioning.  Some of it might be redundant because of changes that were made to the original code.  
