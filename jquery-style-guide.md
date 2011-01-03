# jQuery Style Guide and Good Practices

## Including JavaScript

* Use Google hosted jquery.js.

      <script src='https://ajax.googleapis.com/ajax/libs/jquery/1.4.4/jquery.min.js'></script>
      <script src='https://ajax.googleapis.com/ajax/libs/jqueryui/1.8.7/jquery-ui.min.js'></script>

* Place the above lines as far below as possible in the html. Ideally just before the closing body tag. The only exception for this should be when the html contains any UI elements like tabs that depend on jQuery to initialize.
* Use noConflict function or the following to free the $ variable.

      (function($) {
        $(function() {
          //place rest of js here
        })
      })(jQuery);

## Mighty $

* Use `$(function(){...})` instead of `$(document).ready();`

* Prefix all jQuery variable with $ except in one case. (The exception is defined in the next point). This helps to remember that this variable is a jQ variable.

* Name reference to the current element as e within a callback. eg.

      $('.class').live('click', function() {
        var e = $(this);
        //...;
      })

## General

* No inline JavaScript
* Always cache the jQ variables. eg.

  *  `var $calendar = $('#calendar');`
  *  `var $someOtherElements = $('.className');`
  *  `$calendar.live('click', ...);`

* Use context if available. eg.

  * `var $calendar = $('#calendar');`
  * `var $cells = $('td', $calendar);`
  * or `$calendar.find('.childClassName');`

* Use data-* prefix for all custom attributes. For example, `data-val1='some value'` or `data-some-different-attr='value'`. This is consistent with W3C's [custom data attributes](http://www.w3.org/html/wg/html5/#custom). Read [John Resig's article](http://ejohn.org/blog/html-5-data-attributes/).
* Use .live() event handler as much as possible

## Chaining

* If there are more than 3 events chained in the same call, split it up into separate lines. eg.

      $('.class').doSomething()
      .someThingMore()
      .doEvenMore()
      .addClass('class');

* If the chaining touches upon more than one element then indent the calls as described in http://benjaminsterling.com/better-jquery-code-2

## Common plugins

* [jQuery form](http://jquery.malsup.com/form/)

* Define a custom plugin if you want to show a spinner while making an Ajax request.

      $.fn.throbber = function(){
        var e = $(this);
        e.html("<img src='/images/ajax-loader.gif' />");
        return e;
      };

## Further reading

* [jQuery tips and tricks](http://stackoverflow.com/questions/182630/jquery-tips-and-tricks)
