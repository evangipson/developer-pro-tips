## CSS tips
- [Specificity](#specificity)
- [Flexbox](#flexbox)

### Specificity
When using CSS, a rule will take precedence over another rule when it is more *specific*, or when the CSS rule is "more" targeted at the element than the previous rule.

#### Selectors
We can use *selectors* to force a rule to be more specific and take effect in the browser. CSS Selectors such as classes, ids, and data-attributes (for CSS3) can be read about in more detail on [MDN's reference](https://developer.mozilla.org/en-US/docs/Web/CSS/Reference#Selectors).

To see selectors in use, take the following example:
```css
<div>
  <p class="bar">Copy</p> // Will be red text.
</div>

div { color: black }
p.bar { color: red }
```

#### Cascading
It's good to start with very basic or *shallow* CSS and build rules *on top* of that easily-overridable, shallow CSS.

To see selectors in use for proper *cascading* CSS, take the following example:
```css
<div id="foo">
  <p class="bar">Copy</p> // Will be purple text.
</div>

div#test p { color: purple }
div p { color: blue }
p { color: red }
```

#### Inline Style Priority
When CSS is drawn, specificity isn't the only thing that matters! CSS that is *inline* (or written right on the HTML element) will be taken with higher priority than a rule of any specificity from an external file or ```<style>``` section. Of course, inline style can't be reused like a class you write. Take the following example:
```css
<div id="foo">
  <p class="bar" style="color:green">Copy</p> // Will be green text.
</div>

div#test p { color: purple }
div p { color: blue }
p { color: red }
```

#### !important
Sometimes cascading isn't an option, or you need to override a rule generated in JavaScript (therefore, inline and higher priority). For that, there is the ```!important``` tag. Take the following example:
```css
<div id="foo">
  <p class="bar" style="color:green">Copy</p> // Will be red text, due to the !important on the <p> rule.
</div>

div#test p { color: purple }
div p { color: blue }
p { color: red!important; }
```

### Flexbox
Flexbox is a way to save time when writing CSS layouts. If you'd like to learn it, a great way is to play [Flexbox Froggy](http://flexboxfroggy.com/)!

#### Compatability
You can see a compatability table for [flexbox on caniuse](https://caniuse.com/#search=flexbox). IE10 and below are not supported at this time.
