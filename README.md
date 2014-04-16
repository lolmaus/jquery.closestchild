jquery-closestchild
===================

An opposite of `closest()`: find the nearest child that matches a selector, ignore deeper matching children.


What this plugin is for
-----------------------

Let's say you've got an HTML module like this:

```html
<div class="module">
  module
  <div class="module-title">title</div>
  <div class="module-foo">
    foo
    <div class="module-bar">bar</div>
  </div>
  <div class="module-children">
  </div>
</div>

```

These modules can nest into each other in a tree-like fashion:

```html
<div class="module" id="module1">
  module
  <div class="module-title">title</div>
  <div class="module-foo">
    foo
    <div class="module-bar" id="module1bar">bar</div>
  </div>
  <div class="module-children">
  
    <div class="module" id="module2">
      module
      <div class="module-title">title</div>
      <div class="module-foo">
        foo
        <div class="module-bar">bar</div>
      </div>
      <div class="module-children">
      
        <div class="module" id="module3">
          module
          <div class="module-title">title</div>
          <div class="module-foo">
            foo
            <div class="module-bar">bar</div>
          </div>
          <div class="module-children">
          
          </div>
        </div>
        
      </div>
    </div>
    
    <div class="module" id="module4">
      module
      <div class="module-title">title</div>
      <div class="module-foo">
        foo
        <div class="module-bar">bar</div>
      </div>
      <div class="module-children">
      
      </div>
    </div>

  </div>
</div>

```

Now, for any given module you would like to select an `.module-foo` element that belongs to that module. But you don't want to include `.module-foo`s of any child modules!

jQuery provides a `.closest()` method that selects the nearest parent that matches a criteria. If only there were a similar method that selects the nearest child...

Well, now there is! `$('#foo').closestChild('.module-bar')` will select only one element: the `#module1bar` from the example above.


## Installation

Require `jquery.closestchild` after jQuery:


```html
<script src="/jquery.js"></script>
<script src="/jquery.closestchild.js"></script>
```


## Usage

```
$('.some-element').closestChild( selector )
```

Note that there's capital `C` in the middle of method name, while file and project names are all lowercase.

`selector` can be anything that the jQuery [`.filter()` method](http://api.jquery.com/filter/) uses.

`closestChild` returns a jQuery collection of matched elements.

Please keep in mind the following features:

* It starts matching with the children of the given element (unlike `.closest()` which starts matching with the element itself).
* It traverses the tree of children one step at a time. It can return multpile elements if they are found on the same level of depth.
* Once at least one match is found, it returns the match(es) and stops traversing, saving performance.

This behavior is different from [jquery-nearest](https://github.com/jstnjns/jquery-nearest) which would traverse each branch of the DOM tree as deep as it goes. jquery-nearest only prevents traversing inside matched elements.


## Demo

See jquery.closestchild in action: http://lolmaus.github.io/jquery.closestchild/ .


## Credit

Created by [Andrey Mikhaylov aka lolmaus](http://github.com/lolmaus/).

Thanks to [adeneo](http://stackoverflow.com/users/965051/adeneo) from StackOverflow.

Sponsored by [Hivemind](http://hiveminded.net/), a knowledge base SaaS solution for your business.


## License

MIT License.
