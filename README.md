website
=======


The two main libraries that are used to create this website are bootstrap and highcharts.  
	
	
Bootstrap is for the layout (Tabs, dropdown menus, popups) and information can be found from their website, http://getbootstrap.com/2.3.2/. Some of the layout uses ` .row` and `.span` from bootstrap (http://getbootstrap.com/2.3.2/scaffolding.html#gridSystem).  Additional resources can be found from jasny (http://jasny.github.io/bootstrap/index.html).  File upload was used from jasny.  
	
	
 Highcharts is a charts library written in javascript.  There are two javascript files.  Highcharts.js creates the actual chart and exporting.js lets a user print or save the image (button on the top right corner of a chart).  There are other resources that can be found on their website, but these are the two necessary ones.  The documentation for highcharts can be found here http://api.highcharts.com/highcharts and examples for specific types of charts can be found here http://www.highcharts.com/demo/.  The type of chart is defined by ` chart: {type: 'CHART_TYPE'}` . So far, there are only three types of charts in this website: column, line, and scatter.  Most of it is fairly self-explanatory if one were to look at the examples.  The one extension from highcharts that was added was the regression.js page.  This creates the regression line from the scatter plot.  The code to create the line can be found from the scan vs. favourite scatter plot.  Under series, there is a type: ‘line’.  Under ‘data’, it shows:` (function() {return fitData(favourite).data;})()` , where favourite is the data (array of points).
	
