---
title: Introduction
seoTitle: Javascript Concepts
seoDescription: Free Javascript Lessons
isFree: true

---

# Introduction

Welcome to Javascript Concepts!

Source material for this course comes from the book [Eloquent JavaScript](http://eloquentjavascript.net/). Following it's beginner-friendly format, we will introduce students to core javascript concepts, then build on their progress. 

For students following course material, I recommend they start [here](http://eloquentjavascript.net/code/ ), which includes coding exercises for each chapter after chapter 1. 

After chapter 5, we would use [code pen](https://codepen.io/) as a sandbox environment. If they feel comfortable, they can begin using a text editor like [Sublime](https://www.sublimetext.com/). 

## Intro: What is Code - How We Rule the World
    
Before diving into source material, it would be great to establish that coding is one of the most sought-after skills in the modern world. Coding can be compared to learning a foreign language, to visit and navigate a new land. 
    
> "You’re building your own maze, in a way, and you might just get lost in it." - Marijn Haverbeke

Coding sits at the crossroads between art and logic, where both designers and developers may  offer their creative talents. 


## 1. Values and Types
Most of the things you read in code will fall into the following categories:
1. Numbers

        1, Infinity, 0
2. Strings

        'Patch my boat with chewing gum'
3. Operators

        console.log(typeof 4.5) 
        // → number

4. Booleans

        true, false  
5. Comparisons

        console.log(1 < 2) 
        // → true
6. Logical Operators

        ==, &&, ||
        
        console.log(true ? 1 : 2);
        // → 1
        console.log(false ? 1 : 2);
        // → 2
        
"true ? 1 : 2" is called the ternary operator. The value on the left of the question mark "picks" which of the other two values will come out. When it is true, the middle value is chosen, and when it is false, the value on the right comes out.


Aside from these values, there are three you may want to avoid, because they have no value. 

    undefined, null, NaN

    console.log(null == undefined);
    // → true
    console.log(null == 0);
    // → false

These categories give you enough information to use JavaScript as a pocket calculator, but not much more. **Functions** will start tying these expressions together into basic programs.

## 2. Functions

In this chapter, we walk through functions with arguments, parameters and scopes. Here are some examples:

    var makeNoise = function() {
      console.log("Pling!");
    };

    makeNoise();
    // → Pling!

    var power = function(base, exponent) {
      var result = 1;
      for (var count = 0; count < exponent; count++)
        result *= base;
      return result;
    };

    console.log(power(2, 10));
    // → 1024
    
Scopes: Global and Local

    var x = "outside";

    var f1 = function() {
      var x = "inside f1";
    };
    f1();
    console.log(x);
    // → outside

    var f2 = function() {
      x = "inside f2";
    };
    f2();
    console.log(x);
    // → inside f2
    
Closures: A function that “closes over” some local variables is called a closure. 

    function wrapValue(n) {
      var localVariable = n;
      return function() { return localVariable; };
    }

    var wrap1 = wrapValue(1);
    var wrap2 = wrapValue(2);
    console.log(wrap1());
    // → 1
    console.log(wrap2());
    // → 2
    
With a slight change, we can turn the previous example into a way to create functions that multiply by an arbitrary amount.

    function multiplier(factor) {
      return function(number) {
        return number * factor;
      };
    }

    var twice = multiplier(2);
    console.log(twice(5));
    // → 10

[Chapter 2 Exercises](http://eloquentjavascript.net/03_functions.html#h_TcUD2vzyMe)

## 3. Data Structures - Objects and Arrays
 
What is an Object? - ```{}```

What is an Array? 

    var listOfNumbers = [2, 3, 5, 7, 11];

In an array, we start with a base ```0``` reference to each array item. So in the above ```listOfNumbers```, we would find:
    
    console.log(listOfNumbers[0]);
    // → 2
    console.log(listOfNumbers[2 - 1]);
    // → 3

Array Properties - 

    ```listOfNumbers.length``` 
    ```5````

    var doh = "Doh";
    console.log(typeof doh.toUpperCase);
    // → function
    console.log(doh.toUpperCase());
    // → DOH
    
Array Methods - 

    var mack = [];
    mack.push("Mack");
    mack.push("the", "Knife");
    console.log(mack);
    // → ["Mack", "the", "Knife"]
    console.log(mack.join(" "));
    // → Mack the Knife
    console.log(mack.pop());
    // → Knife
    console.log(mack);
    // → ["Mack", "the"]
    
Arrays and For Loops

Cool, let's write our first for loop!

    for (var i = 0; i < listOfNumbers.length; i++) {
        console.log(listOfNumbers[i]);
    }
    
    2
    3
    5
    7
    11

[Chapter 3 Exercises](http://eloquentjavascript.net/04_data.html#h_TcUD2vzyMe)

## 4. JSON - What tweets are made of

Now we can begin to understand what goes on behind the scenes of your favorite social media app.

    {
            "id": 18,
            "user": {
                "username": "mbs480",
                "first_name": "",
                "last_name": "",
                "follower_count": 0,
                "url": "/profiles/mbs480/",
                "email": "mbs480@nyu.edu"
            },
            "content": "#herbiehancock",
            "timestamp": "2017-11-22T16:37:16.077099Z",
            "date_display": "Nov 22, 2017 at 04:37 PM",
            "timesince": "3 weeks, 6 days ago",
            "parent": null,
            "likes": 1,
            "did_like": false,
            "reply": false
        },

JSON comprise most of the responses from Twitter, Facebook, Instagram. In order to begin writing websites, we want to know how to compose our own twitter-like backend framework. Which brings us to...
        
## 5. The Web

The World Wide Web (not to be confused with the Internet as a whole) is a set of protocols and formats that allow us to visit web pages in a browser. The “Web” part in the name refers to the fact that such pages can easily link to each other, thus connecting into a huge mesh that users can move through.

To add content to the Web, all you need to do is connect a machine to the Internet, and have it listen on port 80, using the Hypertext Transfer Protocol (HTTP). This protocol allows other computers to request documents over the network.

A simple HTML document looks like this:

    <!doctype html>
    <html>
      <head>
        <title>My home page</title>
      </head>
      <body>
        <h1>My home page</h1>
        <p>Hello, I am Marijn and this is my home page.</p>
        <p>I also wrote a book! Read it
          <a href="http://eloquentjavascript.net">here</a>.</p>
      </body>
    </html>
    
    
Ready for more lessons?

Continue with [Prototypal Inheritence](https://michaelstromer.nyc/books/javascript-concepts/prototypal-inheritance).