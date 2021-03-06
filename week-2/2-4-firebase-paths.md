# 2.4: Intro to Firebase challenges: Accessing data with paths

[Firebase](https://firebase.google.com/) is a set of tools (now owned by Google) that help software developers build web and mobile apps more quickly and easily.

We'll be using their real-time database platform as the backend for our app, so we don't have to worry about setting up or maintaining our own server and our own database from scratch! It's a great beginner-friendly way to start learning about databases, and these "Backend as a Service" (BaaS) tools are a huge trend in the tech industry right now.

:tv: **Watch [this 2-minute video introducing the Firebase database service](https://youtube.com/watch?v=U5aeM5dvUpA)**

<hr/>

## The structure of Firebase databases

Firebase databases store data as a **hierarchy** (also called a **tree**), just like how files and folders are stored on your computer, or how web pages are structured in the Document Object Model (DOM).

And if you know how to work with JavaScript objects, you pretty much already know how to work with data stored in a Firebase database, because **Firebase stores** ***everything*** **as JSON data**! Hurray!

  > **Note:** There are many different types of databases, and the Firebase database is an example of what are commonly called **NoSQL databases**. That's a topic to look up later if you're curious! (Definitely a more advanced topic though.)

<br/>

Here's how our example penguin data is represented in an actual Firebase database:

![Fictional penguins Firebase database](https://user-images.githubusercontent.com/1555022/27147872-37732274-50f3-11e7-90f2-70c82e539477.png)

:star: **There are four key concepts for accessing data from Firebase:**

  1. Determining the **path** to your data's location in the database
  2. Creating a **reference object** in your JavaScript code, which represents a database location (a chunk of data)
  3. Setting up Firebase **event listeners** to retrieve the data from your database (which also updates in real time!)
  4. Using the **data snapshot** object to extract the **value** of the data

We'll learn about the first of those concepts -- ***paths*** -- in this section.

<br/>

## Follow the path to find your data!

In Firebase, each part of your database is treated as a *location* specified by a ***path***, which is a ***specially formatted string***. We use paths with the same format in many other areas of computing, not just with Firebase!

**Examples of paths in general:**

  - Paths can refer to files or folders on your computer. For example, you might access the documents folder on your computer with the path `C:/Users/Liz/Documents`

  - Paths can also refer to the part of the URL that specifies the location of a web page. For example: `example.com/events/birthday-party/` or `example.com/login.html`

  > For more than you ever wanted to know about paths, see [Wikipedia's page on Path (computing)](https://en.wikipedia.org/wiki/Path_(computing))

<br/>

:star: **Just like the examples above, *Firebase paths* are strings indicating the location of a chunk of data, with each level of the hierarchy separated by a *slash*:**
  - The path to the *name* of penguin #7344 is the string `"penguins/7344/name"`
  - And the path to that penguin's *origin* is the string `"penguins/7344/origin"`

<br/>

## Challenge 1:

Looking at the image of our penguin database from above, what path would let you access the section of the database that contains the entire list of penguins?

  > This is the second level in the hierarchy, whereas the *root* or the database itself is the top level.


<br/>

## Challenge 2:

How would you access the database location containing all the data for the penguin with ID number `1152`?

<br/>

## Challenge 3:

And what would be the path to that penguin's name?

<br/>

## Accessing the *root*, the entire database

We use the special path `/` (just a single forward slash) to access the entire database (the ***root*** of the tree or hierarchy). In our case, the root is `test-web-app-4fde9` (which you can see at the top of the penguin database hierarchy in the image).

  > **Note:** It's an old convention in computing to use `/` as the path for the **root** of any system. By root, we mean the top-level element containing the whole tree or hierarchy, continuing the metaphor of a *tree* which has a *root* and *branches*. (Another example: the `document` object is the root of the DOM representing the hierarchy of elements on a web page.)  

<br/>

## Challenge 4:

Did you notice that accessing nested data in Firebase is exactly like accessing nested objects within our JavaScript code, just with a slash instead of a dot?

:star: **The keys/property names of an object make up the** ***path*** **that leads you to a specific section of the data.**

<br/>

**Your challenge:** Looking at the JavaScript code below, how would you access the contents of the `resumeFile` and display it in the console? **Test your code in your browser console and/or [Python Tutor](http://pythontutor.com/javascript.html#mode=edit)!**

```javascript
let myComputer = {
  users: {
    liz: {
      documents: {
        resumeFile: "I am awesome, please hire me!",
        recipesFile: "How to boil water..."
      }
    },
    guest: {
      documents: null
    }
  }
};
```

  > **Fun fact:** If you really wanted to, you could essentially represent all the files and folders of your computer as a giant JavaScript object! In fact, you can represent just about *any data* in a JavaScript object.

<br/>

## Challenge 5:

**Remix this Glitch project: https://glitch.com/edit/#!/firebase-practice-1**

That project is linked to a working Firebase database that contains our example penguin data! **On line 22 of the JavaScript file, replace the path `"penguins/7344/name"` with the paths to access the following data:**

  1. Access the name of the penguin with ID number 1152.
  2. Access the `canFly` property of penguin number 7344.
  3. What happens if you try to access a location in the database that doesn't exist? Does that cause any error messages or break anything?

**View the live app to make sure your code works** -- the data will be displayed on the web page!

</br>

## Bonus challenge:

Create a JavaScript object (using object literal notation) that represents the DOM (Document Object Model) for [our Firebase practice page](https://glitch.com/edit/#!/firebase-practice-1) that we used for the previous challenges.

  - The keys/properties and the structure of your object should reflect the entire *tree* or *hierarchy* of the HTML elements of our web page.
  
  - You can use placeholders for the values, so you don't have to do a bunch of typing!
  
  - For elements of the same type, you can name them something like `thing1`, `thing2`, `thing3` if needed.
  
  - The details don't have to perfectly match the HTML code. Again, just the *overall structure* of your object should match the DOM of our example web page.

</br>

<hr/>

:trophy: **Congratulations!** Once you're familiar with paths and hierarchical data structures, you'll start seeing them *everywhere!* The next time you look at a URL, search for files or folders on your computer, or work with just about *any* programming language, your  knowledge of paths will come in handy.

:point_right: **Next up:** [in section 2.5 we'll take a closer look at creating database reference objects for Firebase](https://github.com/LearnTeachCode/intro-javascript-class/tree/may-2018-int/week-2/2-5-firebase-reference-objects.md), which allow us to access many built-in Firebase functions to access or modify our data.
