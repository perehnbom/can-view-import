@page can-view-import.pages.dynamic Dynamic Imports
@parent can-view-import.pages

Dynamic imports are used in conditional situations such as within a [can-stache.helpers.if], to prevent unnecessarily fetching resources that might not be needed in all cases.

To make your import be loaded dynamically it *cannot* but self closing like `/>` but rather must have a closing tag `</can-import>`.

### Example

```
<can-import from="components/foobar">
  {{#if isResolved}}
  <foobar/>
  {{/if}}
</can-import>
```

which is equivalent to a Steal import like:

```
steal.import('components/foobar').then(function(foobar) {
 // access to the module you loaded.
 // e.g. access to a component's ViewModel 
 // foobar.ViewModel
});
```

Please notice that when dynamically importing modules in a stache file, the scope inside [can-view-import <can-import>] is a Promise, so you have to wait until it is resolved before injecting something like a [can-component].

Use the `{{#if isResolved}}` helper for that.
