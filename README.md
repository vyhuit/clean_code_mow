# Clean code in Javascript with Mow

## What is clean code?
* Clean code means that your code is **easy to read**, **understand**, and **change**. 
* It’s as simple as having descriptively **named variables, functions, and classes** so that as you read, you know what each contains or does **without guesswork**.

## Why clean code is important?
* Allows you to **clearly communicate** with the next person who works with what you've written. 
* Being able to return to previously written code and understand what it does is key, especially in the software development world. 
* By writing clean code, you will make yourself a **better teammate, employee, and developer**.

## What does clean code actually look like?

### 1. Naming convention:
#### Keep them clear and concise
* **Constant variables** are in **SNAKE_UPPERCASE**.
* **Classes** are in **PascalCase**.
* **Normal variables & functions** are in **lowerCamelCase**.
* Use **Noun** for variables and **Verb** for functions as thier prefix.
* Use the **same prefix for similar functions** (**get**Users, **set**RoomStatus, **add**Members).
* Don't use one-char name like ```p``` for ```product```

Some examples:
###### Bad:
```javascript
  const a = 24;
  const b = 7;
  const c = a * b;
  console.log(c);
```
###### Good:
```javascript
  const HOURS_PER_DAY = 24;
  const DAYS_PER_WEEK = 7;
  const HOURS_PER_WEEK = HOURS_PER_DAY * DAYS_PER_WEEK;
  console.log(HOURS_PER_WEEK);;
```