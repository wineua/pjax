## PJAX for Laravel 5.*

Enable the use of PJAX in Laravel 5.*.

#### Installation

Add `jacobbennett/pjax` to `require` section in your `composer.json`

	"jacobbennett/pjax": "0.*"

Add `'JacobBennett\Pjax\PjaxMiddleware',` to `$middleware` in `app/Http/Kernel.php`

#### How to use

This middleware will check, before outputting the http response, for the `X-PJAX`'s 
header in the request. If found, it will crawl the response to return the requested 
element defined by `X-PJAX-Container`'s header.

Works great with [jquery.pjax.js](https://github.com/defunkt/jquery-pjax).

### Notes:

Sometimes when using PJAX it will timeout and trigger a standard page reload. This could be due to various factors but one thing you may try is to extend the default timeout for PJAX using this little snippet when you initialize PJAX.

```js

$(document).ready(function(){

    // does current browser support PJAX
    if ($.support.pjax) {
    	$.pjax.defaults.timeout = 1000; // time in milliseconds
    }
    
});

```
