### Changing the URL without reloading the page in JS

To accomplish this, we use the html5 history API:

``` coffeescript
update_url = (url,state)->
    window.history.pushState(state,"", url);
```

I am using coffeescript, but you would call window.history exactly the same way
in JS. You can pass an object storing state variables, so that in case the user
presses the back button the previous screen can be restored properly.

To handle back presses, we answer to the onpopstate event:

``` coffeescript
$(window).on 'popstate', (event) ->
  if(event.originalEvent.state)
    s = event.originalEvent.state
    window.location.assign(s.url);
```

[History API Docs](https://developer.mozilla.org/en-US/docs/Web/API/Window/history)
|
[CSSTricks Tutorial](https://css-tricks.com/using-the-html5-history-api/)
