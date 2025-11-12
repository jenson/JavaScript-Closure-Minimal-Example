# JavaScript-Closure-Minimal-Example
# 🔒 Simple JavaScript Closure Counter demonstrating private state.

This repository contains a simple, yet powerful, example demonstrating the concept of **Closures** in JavaScript. The code creates independent, private counters that maintain their own state.

---

## What is a Closure?

A closure is the combination of a function and the lexical environment within which that function was declared. Essentially, it allows an inner function to **access and remember** the variables of its outer function, even after the outer function has finished executing.

---

## The Code Example

### 1. The Function Definition (The Closure Factory)

The `counterFnOuter` is a **factory function** that creates and returns a new function (`counterFnInner`) every time it's called.

```javascript
function counterFnOuter(){
    // 'count' is the private variable that gets "closed over"
    let count = 0; 
    
    // The inner function that remembers and updates 'count'
    return function counterFnInner(){
      count = count + 1;
      return count;
    }
}

## Creating Independent Instances

The function calls below create two separate, independent closures.

```javascript
counter1 = counterFnOuter();
counter2 = counterFnOuter();

counter1 is bound to the first unique memory space where its private count starts at 0.

counter2 is bound to a second, completely independent memory space where its own private count starts at 0.

## Execution and Output

```javascript
console.log(counter1()); //1
console.log(counter1()); //2
console.log(counter1()); //3
console.log(counter2()); //1
console.log(counter2()); //2
console.log(counter1()); //4
console.log(counter1()); //5
console.log(counter2()); //3

**Try it live on JSFiddle:** [https://jsfiddle.net/jenson555/3nf6tp7r/15/](https://jsfiddle.net/jenson555/3nf6tp7r/15/)
