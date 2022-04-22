## Fun with CSS variables and Tailwind

Version 3 of Tailwind includes a plethora of new and awesome features. One of them is the ability to use arbitrary values and properties in your utility classes – this even works with CSS variables! Here's the example we're going to build today:

![hover-me.gif](https://cdn.hashnode.com/res/hashnode/image/upload/v1649932246768/WORStOYOc.gif)

The top and bottom lines should grow from 0% to 100% width when you hover over the button. Let's start with the basic html for this component:

```html
<button class="relative">
  <span class="absolute left-0 w-full h-1 bg-green-500 transition-all"></span>
  <div class="p-4">HOVER ME</div>
  <span class="absolute right-0 w-full h-1 bg-green-500 transition-all"></span>
</button>
```

So far so good. Next, let's use Tailwind's new bracket syntax to define and use a CSS variable called `--fill` that represents the width of the lines. To do that, add `[--fill:0%]` to the button element and replace `w-full` with `w-[var(--fill)]` in both span elements.

The final piece of the puzzle is updating the variable on hover. Tailwind makes this easy, just add `hover:[--fill:100%]` to the button element and you're done. 

And here's the final result:

%[https://codepen.io/simon-jaeger/pen/ExodgrB]

Pretty neat! I'm looking forward to exploring this technique more in the future. Let me know in the comments if you stumble across other use cases.