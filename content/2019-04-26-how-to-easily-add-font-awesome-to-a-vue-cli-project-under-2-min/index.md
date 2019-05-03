---
title: How to easily add font awesome to your Vue CLI project in under 2 min.
date: 2019-04-26
tags: [vuejs, javascript]
path: blog/2019-04-26-how-to-easily-add-font-awesome-to-a-vue-cli-project-under-2-min
cover: ./fire.jpg
excerpt: In this post I will shortly show you how to easily add fontawesome to your Vue Cli project.
---

So basically we will just use a library called **vue-cli-plugin-fontawesome**.

##Installation
                                  
If you haven't yet installed vue-cli 3, first follow the install instructions here: https://github.com/vuejs/vue-cli

Generate a project using **vue-cli 3.0**:

```none
vue create my-app
```

To install the fontawesome plugin:

```none
cd my-app
vue add fontawesome
```

##Usage

The plugin is using the **FontAwesome 5 vue-fontawesome component**.


```html
 <font-awesome-icon icon="user-secret"></font-awesome-icon>
```

#How to add a Twitter icon to your App
if you want to use social icons like the one from twitter make sure to install the @fontawesome/free-brands-svg-icons

1. import library
 
 ```none
 npm i --save @fontawesome/free-brands-svg-icons
 ```
 
2. Add it to your **fontawesome.js**. It should look like the following:
 
```javascript
import Vue from 'vue'

import { library } from '@fortawesome/fontawesome-svg-core'
import { fas } from '@fortawesome/free-solid-svg-icons'
import { fab } from '@fortawesome/free-brands-svg-icons'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'

library.add(fas)
library.add(fab)

Vue.component('font-awesome-icon', FontAwesomeIcon)
```

3. Now you can use the twitter icon like this:

```html
<font-awesome-icon :icon="['fab', 'twitter']" size="3x" />
```

##Search for free icons
To search for free icons have a look here:

https://fontawesome.com/icons?d=gallery


