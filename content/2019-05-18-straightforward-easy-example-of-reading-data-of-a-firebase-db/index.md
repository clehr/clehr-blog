---
title: Easy straightforward example of reading data from a Firebase database with Vue
date: 2019-05-18
tags: [vuejs,firebase]
path: blog/2019-05-18-read-data-from-firebase
cover: ./easter-fire.jpg
excerpt: In this post I will show you a straightforward easy example on how to read data from a Firebase database.
---
##Motivation
I often find it difficult to start with new technologies because though the documentation is good as soon as you know about the topic,
it is often not designed for pure newcomers.

This post is designed to help newcomers dive into firebase by providing an on point documentation on how
to setup firebase and read values from a firebase database.

##Firebase setup:

1. Login to firebase:
https://firebase.google.com/

2. Create a new project

   ![new Project](./addProject.png)


3. Create a database

   ![find database](./findDatabase.png)


4. Click on Realtime database

   ![realtime database](./realtime.png)

5. Create an entry **system** with value **firebase**

   ![add entry](./addEntry.png)


##Setup your Vue application 

1. Install Vue CLI:
```
npm install -g @vue/cli
```

2. Create your vue application

```
vue create firebase-example
```


##Add firebase to your application:

1. Go into your project

```
cd firebase-example
```

2. Add firebase via **yarn/npm**

```
yarn add vuefire firebase

or

npm install vuefire firebase --save
```

3. Inside the **src** folder create a subfolder with name **config**. Inside there create a file **db.js**

4. Go to <a name="firebase" href="https://firebase.google.com/" target="_blank">Firebase</a> and find out your Firebase API Key. The following images show how this is done:

   ![configuration](./getConfiguration.png "as we will build a webapp in this example we need the third option")
   
   
   ![fire base config](./firebaseConfig.png)



5. Add the firebase config to your **db.js** file. It should look like this:

```javascript
import Firebase from 'firebase'
var firebaseConfig = {
    apiKey: "AIzaSyDIPHIVsOny6JfoAWcajKVikIHhn_1Q_Uo",
    authDomain: "fir-example-575a5.firebaseapp.com",
    databaseURL: "https://fir-example-575a5.firebaseio.com",
    projectId: "fir-example-575a5",
    storageBucket: "fir-example-575a5.appspot.com",
    messagingSenderId: "748107576734",
    appId: "1:748107576734:web:6f7e3e93f4eb1b4b"
};
// Initialize Firebase
let app = Firebase.initializeApp(firebaseConfig)
export const db = app.database()
```


6. Import firebase to Vue App:

Inside the **main.js** file add the following:

```javascript
import VueFire from 'vuefire'

Vue.use(VueFire)
```

7. Import the firebase database to your current Vue component:

a) Therefor add:
```
import {db} from './config/db';
```

to your **App.vue** file


b) Add the property "system" to display it in the template later:

```
data: function () {
            return {
                system: '',
            };
        },
```



c) Call the firebase database an read the value for system stored and set the property in vue to that value:

```
created() {
            db.ref('system').once('value', storedValue => this.system = storedValue);
        }
```

   

d) Use the value in the template:
        
```html
<template>
<div>
{{system}}
</div>
</template>
```

Your **App.vue** should now look like this:

```vue
<template>
  <div id="app">
    {{system}}
  </div>
</template>

<script>
import {db} from './config/db';

export default {
  name: 'app',
  data: function () {
    return {
      system: ''
    };
  },
  created() {
    db.ref('system').once('value', storedValue => this.system = storedValue);
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
```

In the browser you should see this:

   ![browser](./browser.png)


If you don't see this result make sure that for this example you allow read and write access to your database as shown in the image below:

   ![security](./security.png)


Congratulations! You read your first value from a Firebase database.

##Further reading
Here is some further reading I found quite helpful if you want to dive deeper into the topic:

https://vueschool.io/courses/vuejs-firebase-realtime-database
 
https://appdividend.com/2018/04/18/vue-firebase-example-tutorial/ 

https://firebase.google.com/docs/database/web/read-and-write

    


    
    
    
    
   

   

