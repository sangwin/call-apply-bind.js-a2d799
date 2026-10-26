
# JavaScript call(), apply(), and bind()

## Overview

In JavaScript, `call()`, `apply()`, and `bind()` are methods used to control the value of `this` when invoking a function.

This example demonstrates how to use these methods to access an object's properties and methods from another function.

## Example Object

```javascript
var pokemon = {
    firstname: 'Pika',
    lastname: 'Chu ',
    getPokeName: function() {
        var fullname = this.firstname + ' ' + this.lastname;
        return fullname;
    }
};
```

The `pokemon` object contains properties for the name and a method that returns the full name using `this`.

## 1. bind()

The `bind()` method returns a new function with `this` permanently bound to the specified object.

```javascript
var pokemonName = function() {
    console.log(this.getPokeName() + 'I choose you!');
};

var logPokemon = pokemonName.bind(pokemon);

logPokemon();
```

### Passing Arguments with bind()

```javascript
var pokemonName = function(snack, hobby) {
    console.log(this.getPokeName() + 'I choose you!');
    console.log(this.getPokeName() + ' loves ' + snack + ' and ' + hobby);
};

var logPokemon = pokemonName.bind(pokemon);

logPokemon('sushi', 'algorithms');
```

**Key Point:** `bind()` creates a new function that can be called later.

## 2. call()

The `call()` method invokes a function immediately, allowing you to specify the value of `this` and pass arguments individually.

```javascript
var pokemonName = function(snack, hobby) {
    console.log(this.getPokeName() + ' loves ' + snack + ' and ' + hobby);
};

pokemonName.call(pokemon, 'sushi', 'algorithms');
```

**Key Point:** Arguments are passed individually.

## 3. apply()

The `apply()` method works like `call()`, but accepts function arguments as an array or array-like object.

```javascript
pokemonName.apply(pokemon, ['sushi', 'algorithms']);
```

**Key Point:** Arguments are passed as an array.

## Output

```text
Pika Chu  I choose you!
Pika Chu  I choose you!
Pika Chu  loves sushi and algorithms
Pika Chu  loves sushi and algorithms
Pika Chu  loves sushi and algorithms
```

The exact output depends on which examples are executed.

## Comparison

| Method | Executes Immediately | Arguments |
|---|---|---|
| `call()` | Yes | Individual arguments |
| `apply()` | Yes | Array or array-like object |
| `bind()` | No | Individual arguments when called, or partially at binding time |

## When to Use

- **call():** Invoke a function immediately with a specific `this` value.
- **apply():** Invoke a function immediately with arguments provided as an array.
- **bind():** Create a reusable function with a specific `this` value.

## Reference

[JavaScript call(), apply(), and bind()](https://medium.com/@omergoldberg/javascript-call-apply-and-bind-e5c27301f7bb)

## Author

**Sangwin Gawande**

Website: [https://sangw.in](https://sangw.in)

---

Cheers!!
