<div align="center">
    <img src="https://github.com/frappe/design/blob/master/logos/logo-2019/frappe-gantt-logo.png" height="128">
    <h2>Frappe Gantt</h2>
    <p align="center">
        <p>A simple, interactive, modern gantt chart library for the web</p>
        <a href="https://frappe.github.io/gantt">
            <b>View the demo »</b>
        </a>
    </p>
</div>

<p align="center">
    <a href="https://frappe.github.io/gantt">
        <img src="https://cloud.githubusercontent.com/assets/9355208/21537921/4a38b194-cdbd-11e6-8110-e0da19678a6d.png">
    </a>
</p>

### Install
```
npm install frappe-gantt
```

### Usage
Include it in your HTML:
```
<script src="frappe-gantt.min.js"></script>
<link rel="stylesheet" href="frappe-gantt.css">
```

And start hacking:
```js
var tasks = [
  {
    id: 'Task 1',
    name: 'Redesign website',
    custom_index: 0,
    custom_class: 'color-teagreen',
    start: '2016-12-28',
    end: '2016-12-31',
    progress: 20,
    dependencies: 'Task 2, Task 3'
  },
  ...
]
var gantt = new Gantt("#gantt", tasks);
```

You can also pass various options to the Gantt constructor:
```js
var gantt = new Gantt("#gantt", tasks, {
    header_height: 50,
    column_width: 30,
    step: 24,
    view_modes: ['Quarter Day', 'Half Day', 'Day', 'Week', 'Month'],
    row_labels: ['first row name'],
    bar_height: 20,
    bar_corner_radius: 3,
    arrow_curve: 5,
    padding: 18,
    view_mode: 'Day',   
    date_format: 'YYYY-MM-DD',
    custom_popup_html: null
});
```

### changelog (Author: sminghan)
```
Tasks properties
-   custom_index: 0
      forces specific row (starts from 0)
-   custom_class: 'color-teagreen'
      sets css class on parent element 
      .gantt .bar-wrapper.color-teagreen .bar {
        fill: #C3ECB2
      }

Gantt properties
-   row_labels: ['T1','T2','T3','T4','T5','T6']
    adds labels to start of row, moves with scrolling
    index follows same as custom_index
    
Gantt functions
-   set_scroll_to_time: function(datetime in ms)
    scrolls LEFT side of gantt container to the specified time
    
Gantt fixes/mods
-   header label spacing was wrong when view_mode set to MONTH
    caused by grid ticks spacing being based on number of days per month
    fix was to include similar spacing for header label spacing calculations.
        its only similar, deviation goes to 0 every 4 years.
-   popup blocks mouse click even when hidden
    fix changes css class to ignore mouse events
-   popup causes scrollbar to stay wide when shrinking timeline
    fix to reset popup x position when change_view_mode is called
-   disabled all progress bar slider / mouse interactions for dragging progress
    removed render function
    removed mouse event listeners
```

License: MIT
------------------
This is not a maintained fork/dist. Original project by [frappe](https://github.com/frappe)
