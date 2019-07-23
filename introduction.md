---
title: Prototypal Inheritance 
seoTitle: Prototypal Inheritance
seoDescription: Prototypal Inheritance
isFree: true

---

# Prototypal Inheritance 

### Agenda
- Define Prototypal Inheritance and Class Inheritance
- Identify differences between Prototypal Inheritance and Class Inheritance

### By the end of the lesson, students will be able to... 
- Define their own class inheritance
    - Example: Create a child class that inherits from a parent.
- Define their own prototype objects
    - Example: Compose a prototype that inherits from factory functions.
- Identify which definitions are useful in specific scenarios. 

## Intro - What's this Inheritance?
- In the real world… 
- In the programming world… 
    - Class extension
    - **Reusable Code**

## JS Class Inheritance

**Class Inheritance**: A class is like a blueprint — a description of the object to be created. Classes inherit from classes and create subclass relationships: hierarchical class taxonomies.

```
// parent class
class Media {
  constructor(info = {}) {
    this.publishDate = info.publishDate;
    this.name = info.name;
  }
}

// child class
class Song extends Media {
 construcor(songData = {}) {
     super(songData);
     this.artist = songData.artist;
 }
}

// child class instance
const mySong = new Song({
    artist: 'Queen', 
    name: 'Bohemian Rhapsody',
    publishDate: 1975
});

console.log(mySong.artist);
// Queen
```

Javascript classes support the concept of inheritance - a child class can extend a parent class. This is accomplished by using the `extends` keyword as part of the class definition.

Child classes have access to all of the instance properties and methods of their parent class. They can add their own properties and methods in addition to those. A child class constructor calls the parent class constructor using the `super()` method.

## JS Prototypal Inheritance

**Prototypal Inheritance**: A prototype is a working object instance. Objects inherit directly from other objects.

```
// factory function
const media = (state) => ({
    play: () => console.log("Now Playing: " + state.name)
});

// factory function
const song = (state) => ({
    download: () => console.log(`Downloading: ${state.name}, 
    by ${state.artist}`) 
});

// prototype object
const jukeBox = ({ name, artist, publishDate }) => {
  let state = {
    name,
    artist,
    publishDate
  }
  return Object.assign(
    {},
    media(state),
    song(state)
  )
};

const favoriteSong = jukeBox({
    name: 'We Are the Champions', 
    artist: 'Queen', 
    publishDate: 1975
});

console.log(favoriteSong.play());
// Now Playing: We Are the Champions
```

## What’s the Difference Between Class and Prototypal Inheritance?

- Class inheritance can lead to many problems...
    - Tight Coupling
    - Fragile base class
    - Inflexibility
    - Duplication
    - Gorilla/Banana problem
        - You wanted a banana, but you got a gorilla holding a banana 🍌🦍  

- Prototypal inheritance solves all these problems.

## Exercises
#### Exercise One - Write your own child `class` that `extends` the following base class:

```
class Animal {
  constructor(state = {}) {
    this.legs = state.legs;
  }
}
```
- Declare an instance of your new animal child `class`, which should include a number of legs and a new `name` property.

#### Exercise Two - Write your own prototype object that inherits from this factory function:

```
// factory function
const vehicle = (state) => ({
    drive: () => console.log("Vrrroom! Speed: " + state.speed),
});
```
- Declare an instance of your new prototype object, which should include a number of wheels and new `speed`.

## Discussion: In what scenarios would each type of inheritance apply?

- Example A: Whole Foods asks you for a web site that lists their selection of fruits based on calory count and color.
- Example B: Tesla is introducing their latest car model: Tesla Z! They ask you to create a functional car program that includes several methods: 
    - `honk`
    - `accelerate`
    - `break`

#### Bonus - Video Resource:

[![Source: Youtube](https://img.youtube.com/vi/wfMtDGfHWpA/0.jpg)](https://www.youtube.com/watch?v=wfMtDGfHWpA)

#
### Thank you!