# Objects

- primitive values
- reference values -> these are all objects

## Making objects

```javascript

let person = {
    name: 'thing',
    integer: 20, 
    listing: [1,2,3]
    greet: function(){
        console.log("hello")
    }
}

```

## Editing objects

```javascript

// adding
person.newThing = 'newvalue'

// deleting (setting to undefined)
delete person.newThing

```
!!! warning "using undefined"
    never define something as "undefined" (bad practice, use "null" instead)


## Special Key names, bracket notation

```javascript

let myObject = {

fist name: "name" // not allowed
first-name: "name" // not allowed

"first-name": "name" // valid!
'first name': 'name' // valid!
}

gettingTheValue = person["first-name"]
gettingTheValue = person["first name"]

```

## Property types and order

```javascript

let myObject = {
    1.5: 'hello'  // valid
    -2: 'hello' // not allowed

}

value = myObject[1.5] // this works
value = myObject['1.5'] // this works

```

when viewing the properties, the order is kept as we've added them. 

!!! info "exception to default ordering"
    When using numbers as keys, they will be sorted, otherwise the original definition order will be kept

## Dynamic Property Access

```javascript

const keyName = "firt-name"
value = myObject[keyName] // this works
value = myObject.keyName // will not work 

const chosenKeyName = 'level';

let myObject = {
    [chosenKeyName]: "badaboom" // key='level'
    'level': 'badaboom' // same as above
}


```

## Shorthand property syntax

if you havea property name that's the same as the key name (when you use a variable for example), yo can ommit the colon colon syntax.

```javascript

const title = 'thetitle'

const myObject = {
    title: title, //valid
    title, // also valid! does the same thing
}

```

## For-in loops 

```javascript

const myObject = {
    a: 1,
    b: 2,
    c: 3,
    d: 4,
}

for (const key in myObject) {
    key = key
    value = myObject[key]
}


```

## Chaining

Having multiple dots to reference nested elements in the object.

- available on objects
- avaialble on methods as well

```js

const id = Math.random().toString()
const nested = myObject.movie.title

```

## Spread Operator

Just like in arrays, you can use the spread operator to quickly copy over values into new objects.
```js

const Object1 = {
    person: 'max',
    age: 30,
    profession: 'webdev',
}

const Object2 = {
    ...Object1 // merges all kv pairs into new object
}

const Object3 = {
    profession:'otherprofession', // overrides profession,
    ...Object2
}

```

## Object.assign()
This is another way of copying variables
Does the same as the spread operator, can use both.

```js
const person1 = {... lots of stuff...}
const person2 = Object.assign({}, person1) // copy properties from exisitng object to new object
```

## Object destructuring

Similar to array destructuring

!!! info 'keys matter'
    Object desctructuring is nice, but make sure the keys that you try to catch are located inside the object that you are reading from.

```js
const {info} = existingObject
const {info, ...otherProps} = existingObject
console.log(info) // info is now an existing thing
console.log(otherProps) // otherProps is also a thing now


//reassigning the variable name
const {info: movieTitle} = existingObject
console.log(info) // will not exist
console.log(movieTitle) // works!

```

## Checking property existance

```js
if ('key' in myObject){...} // check if key is there

if (myObject.key === undefined) // same thing


```

## this
A special keyword with regards to objects

It's the same as `self` in python

```js
const myObject= {
    title: "The Movie Title"
    getFormattedTitle: function(){
        return this.title.toUpperCase() 
    }
}
```
sometimes the "this" is not referring to the object, but to something else that has called it. 
You can point it back to the thing you want by using the `bind()` function

inside a function, "this" always refers to the think that called it. (so what's in front of the function)

```js
const a = getFormattedTitle.bind(myObject) // execute on an object
const b = getFormattedTitle.call(myObject, arg1, arg2, arg3) // call the function
const c = getFormattedTitle.apply(myObject, [arg1, arg2, arg3])


```

!!! info "debugging this"
    this can sometimes be a bit weird. `console.log(this)` is a good way to figure out what context it belongs to when it doesn't behave as expected.

    The reason that it can behave unexpected is because it refers to what is calling the function, this could be the object, but could also be a bigger global scope or an eventlistener for example.


## method shorthand syntax

```js
const myObject= {
    title: "The Movie Title"
    getFormattedTitle: function(){
        return this.title.toUpperCase() 
    }
}
const myObject= {
    title: "The Movie Title"
    //same as method above, but shorter 
    getFormattedTitle(){
        return this.title.toUpperCase() 
    }
}

```
## Getters & Setters

- get = retrieving thing
- set  = assinging thing

to customize how the get and set happens, you can use getters and setters.

```js

const myObject = {
    // customise what happens when people try to assign something tot title
    set title(value){
        if (valuel.trim()===''){
            this._title= "DEFAULT VALUE"
        }

        this._title = value

        }
    // customize what happens when people try to retrieve the title. 
    get title(){
        return this._title

    }
}

// getter activated
const newThing = myObject.title // just get stuff like this

//setter activated
myObject.title = 3 // just add stuff like normally

```

