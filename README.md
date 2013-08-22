Website
=======


The two main libraries that are used to create this website are bootstrap and highcharts.  
	
	
Bootstrap is for the layout (Tabs, dropdown menus, popups) and information can be found from their website, http://getbootstrap.com/2.3.2/. Some of the layout uses ` .row` and `.span` from bootstrap (http://getbootstrap.com/2.3.2/scaffolding.html#gridSystem).  Additional resources can be found from jasny (http://jasny.github.io/bootstrap/index.html).  File upload was used from jasny.  
	
	
 Highcharts is a charts library written in javascript.  There are two javascript files.  Highcharts.js creates the actual chart and exporting.js lets a user print or save the image (button on the top right corner of a chart).  There are other resources that can be found on their website, but these are the two necessary ones.  The documentation for highcharts can be found here http://api.highcharts.com/highcharts and examples for specific types of charts can be found here http://www.highcharts.com/demo/.  The one extension from highcharts that was added was the regression.js page.  This creates the regression line from the scatter plot.  The code to create the line can be found from the scan vs. favourite scatter plot.  Under series, there is a type: ‘line’.  Under ‘data’, it shows:` (function() {return fitData(favourite).data;})()` , where favourite is the data (array of points).  The source of this can be found here: https://github.com/virtualstaticvoid/highcharts_trendline.
	
There are brief comments throughout the code to identify what they are.
	
Javascript Code
---------------

The variable `string` is a json object with all the data for the charts in the website.  It also includes a boolean value (under `warning`) to denote whether or not there is a scanning error. 
The next 100 lines of code or so are to extract the information from the json object into variables that will later be used in the charts.  
All the charts in the website are created from lines 193-995.  	Most of the code to create the graph is intuitive and further features can be added to these graphs by looking at the highcharts API.  All graphs have to be rendered to a div in the html section. For example,`$('#UniqueScanCount').highcharts...` will render the graph to the div with id `UniqueScanCount`.  There are other methods to render graphs as shown from lines 311-386, where the same graph is rendered to two different divs.  For the bar graph, `x-axis -> categories` defines the x-axis titles and the corresponding data can be inputted under `series -> data`.  Both inputs for categories and data should be arrays.  
For line charts, they are very similar to bar charts, except the type of the chart should be `line` instead of `column`.  
The scatter plot (line 592-643) has  type `scatter`.  The data in a scatter plot can be inputted under `series -> data` as a 2D array.  The regression line is created from lines 635-639.
The pie chart needs to have `pie` under `plotOptions` (the type is unnecessary).  Under `series -> data`, the data is a 2D array as well where the category is in the first index and the number is in the second index.  All the pie charts have a change function associated with them because the pie chart will be reloaded when a different select option is selected.  Look at the sample code from lines 775-786.
