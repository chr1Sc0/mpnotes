# Dashboards
Dashboards contain graphs and indicators composed by a series of widgets. These show data analytics about the performance of their web or mobile applications. These graphs are normally based on aggregate data collected by the beacons.

There are system dashboards provided ouf of the box a which are contained in the "/System Object/Dashboard" Library path. The user can create custom dashboards though combining the available widgets.

You should see the collected beacons in mPulse dashboards within seconds, except for the Waterfall Dashboard, where beacons may take up to five minutes to be available.

There are some default dashboards that provide useful information and could be used initially.

### Summary Dashboard
mPulse's Summary Dashboard presents trackable metrics such as conversion rate, number of items sold, total sales in dollars, and number of comments.  The top widgets show a graph with the number of measurements over time (beacons) vs. the percentile of Page Load time in seconds.

Is worth reminding that percentile differs significantly from average. It indicates the value below which a given percentage of observations in a group of observations fall. For example, the 80th percentile is the value (or score) below which 80% of the observations may be found. The 50% percentiles can be also called "median".

For more info about percentiles, check [this](https://www.dynatrace.com/blog/why-averages-suck-and-percentiles-are-great/) article.

It's possible to filter from a number of mPulse dimensions in the graph.

### Waterfall Dashboard
The Waterfall dashboard does not show aggregate data but the raw data received on each beacon. Element-level performance details used in the Waterfall Analysis Dashboard are collected from browsers that support the W3C Resource Timing API.

The latency of Waterfall dashboard is higher and data sent from beacons can take up to 5 mins to be available. Viewing historical data (collected more than 24 hours in the past) in the Waterfall dashboard may also take several minutes to load.

Also, if an extended time filter is selected, like for example spanning for a number of days (say a week), the Waterfall Dashboard will only display beacons for a 60 minute (or shorter) time frame contained in the first chunk of the time interval selected. That is, the beacons that you see in the list in the Beacons widget of the dashboard will be from the first 60 minutes starting from the beginning of the week in the filter you select. It’s highly recommended that you use the ‘between’ option in the Date/Time filter to choose a specific hour in which you know beacons exist.

### What-If Dashboard
This dashboard can levarages from the two most important custom metrics to set up for any web app in which customers are able to make purchases, which are:

* Conversion Rate and
* Revenue

The mPulse What-If dashboard can use these two metric to help predict the monetary value to site performance improvements. As every site is different, there is no standard way to configure mPulse to capture these values.
(see the Metrics topic)
