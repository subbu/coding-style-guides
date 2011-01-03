# jQuery Style Guide and Good Practices

## Mighty $

* Use `$(function(){...})` instead of `$(document).ready();`

* Prefix all jQuery variable with $ except in one case. (The exception is defined in the next point). This helps to remember that this variable is a jQ variable.

* Name reference to the current element as e within a callback. eg.


    $('.class').click(function(){
      var e = $(this);
      //...;
    })

## General

* Always cache the jQ variables. eg.

  *  `var $calendar = $('#calendar');`
  *  `var $someOtherElements = $('.className');`
  *  `$calendar.live('click', ...);`

* Use context if available. eg.

  * `var $calendar = $('#calendar');`
  * `var $cells = $('td', $calendar);`

## Chaining

* If there are more than 3 events chained in the same call, split it up into separate lines. eg.

* If the chaining touches upon more than one element then indent the calls as described in http://benjaminsterling.com/better-jquery-code-2
