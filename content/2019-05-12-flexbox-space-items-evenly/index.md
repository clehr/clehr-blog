---
title: Learn how to align your items evenly with flexbox
date: 2019-05-05
tags: [sass]
path: blog/2019-05-12-flexbox-space-items-evenly
cover: ./flexbox.jpg
excerpt: In this post I will give you an easy to follow example how you can align your items evenly with flexbox
---

The code in this example will be fairly simple:

1. we have an **index.html** with following content:

```html
<html>
<header>
    <link rel="stylesheet" href="styles.css">
</header>
<body>
<div class="flex-container">
    <div>
        Div 1
    </div>
    <div>
        Div 2
    </div>
    <div>
        Div 3
    </div>
</div>
</body>
</html>
```

We will just import a styles.css and add three divs with a surrounding parent div to it.
The parent div will have a css class **flex-container** with the purpose to align the child divs evenly.

2. The styles.css will give our divs borders to make them better visible:

```css
div {
    border-style: solid;
}

.flex-container {
    display: flex;
    justify-content: space-evenly;
    border-color: red;
}
```

The **.flex-container** is the important part: 
1. To be able to use flexbox we need to call **display: flex;**

2. The command to align the items evenly is **justify-content: space-evenly;**


And that's it! Now you know how to align your items evenly in a row :)

If you want to play around a bit more you can use following codesandbox example:

https://codesandbox.io/s/mmm9647knj?fontsize=14


Flexbox can do a lot more than this example.
For More tips and tricks on how to use flexbox visit:

https://css-tricks.com/snippets/css/a-guide-to-flexbox/

Have fun!

    


    
    
    
    
   

   

