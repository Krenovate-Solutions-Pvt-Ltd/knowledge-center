# Times are showing incorrect on Apple devices.
#### Problem
It was found that the time was shown incorrectly on certain apple devices for the client. The times were somewhat around `5:30 hours` slow on apple devices.

#### Solution
This was identified due to the reason that different browser interpret the time very differently. And usually Apple device users use safari as there default browser time was coming out to be different. 

To solve the issue, [Moment JS](https://momentjs.com/ "Read More") was used.

* **Step 1** : Use Enqueue script in order to add the moment js file from a cdn.

``` php linenums="1"
<?php 
wp_enqueue_script( 'momentjs' , 'https://cdn.jsdelivr.net/npm/moment@2.25.3/min/moment.min.js', null, null, true);
?>
```

!!! info
    `wp_enqueue_script` is the wordpress core function used to call the script on the frontend of the website. You can read about it in [wordpress core documentation here](https://developer.wordpress.org/reference/functions/wp_enqueue_script/). 

* Step 2 : Using the moment object ensures that the time is correct on all the devices.

```js linenums="1"
// Store the value of time
var cardTime = div.querySelector("#time").innerHTML;

// Use moment obejct to parse the time      
var eventTime= moment(cardTime); 
   
// On Every Second   
var x = setInterval(function() {

// Get the current time
var now = moment(new Date(), 'YYYY-MM-DD HH:mm'); 

// Use  duration to get the tine difference.
var duration = moment.duration(eventTime.diff(now));

// Get difference in day, hours, minutes and seconds
var days = duration._data.days;
var hours = duration._data.hours;
var minutes = duration._data.minutes;
var seconds = duration._data.seconds;
},1000 );
```
