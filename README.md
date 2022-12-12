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

###### ❌ Don't: 
```javascript
  const a = 24; 
  const b = 7;
  const c = a * b;
  console.log(c);
  //What are the a, b, and c variables?
```
###### ✅ It should be::
```javascript
  const HOURS_PER_DAY = 24;
  const DAYS_PER_WEEK = 7;
  const HOURS_PER_WEEK = HOURS_PER_DAY * DAYS_PER_WEEK;
  console.log(HOURS_PER_WEEK);;
```

* **Class** names are in **PascalCase** and **do not** start with a **Verb**
###### ❌ Don't: 
```javascript
class makeCar {
  color: string;
  type: string
}
```
###### ✅ It should be::
```javascript
class Car {
  color: string;
  type: string
}
```

* **Normal variables & functions** are in **lowerCamelCase**.

* Use **Noun** for variables and **Verb** for functions as thier prefix.
###### ❌ Don't: 
```javascript
let user = "123456"; //This should be userId instead user
function UserGet(user){
  //do something
};
```
###### ✅ It should be:
```javascript
let userId = "123456";
function getUserById(userId){
  //do something
};
```


* Don't use one-char name

###### ❌ Don't: 
```javascript
let p = {
  name: "ABC",
  price: 123000
};
```
###### ✅ It should be:
```javascript
let product = {
  name: "ABC",
  price: 123000
};
```

* Use the **same prefix for similar functions** (**get**Users, **set**RoomStatus, **add**Members).


###### ❌ Don't: 
```javascript
function addItem(){
  //do something
};

function pushProduct(){
  //do something
};
```
###### ✅ It should be:
```javascript
function addItem(){
  //do something
};

function addProduct(){
  //do something
};
```

### 2. Function rules:
  * Function is too long: A good function should be written in a block of less than 10-15 lines
###### ❌ Don't: 
  ```javascript
  function renderHomePage(){
    let logoItem = '';
    let navBar = '';
    ...
    let header = logoItem + navBar;
    ...
  }
  ```

###### ✅ It should be:
  ```javascript
  function renderHomePage(){
    renderHeader();
    ...
  }

  function renderHeader(){
    let logoItem = '';
    let navBar = '';
    ...
    let header = logoItem + navBar;
  }
  ```
  * Always use 2 spaces for indentation of code blocks
###### ❌ Don't: 
  ```javascript
  function toCelsius(fahrenheit) return (5 / 9) * (fahrenheit - 32);
  ```

###### ✅ It should be:
  ```javascript
  function toCelsius(fahrenheit) {
    return (5 / 9) * (fahrenheit - 32);
  }
  ```
* Separate 2 functions or mission-paragraphs with a blank line will make your code easier to read
###### ❌ Don't: 
  ```javascript
  function renderProductList(){
    //data processing
    ...
    //render product
    ...
  }
  ```

###### ✅ It should be:
  ```javascript
  function renderProductList(){
    //data processing
    ...

    //add a blank line between these 2 paragraphs for cleaner code
    
    //render product
    ...
  }
  ```

* A function should process one mission:
###### ❌ Don't: 
  ```javascript
  function renderProductList(){
    //get data from api calling
    let data = fetch(...)

    //render product
    let productListWrapper = document.createElement("div");
    ...
  }
  ```

###### ✅ It should be:
  ```javascript
  let data = await getProductList();

  function renderProductList(data){
    let productListWrapper = document.createElement("div");
    ...
  }
  ```

* Do not pass params to a function with unlimited param quantity:
###### ❌ Don't: 
```javascript
function renderProducts(item1, item2, ...){
  //do something
}
```

###### ✅ It should be:
```javascript
function renderProducts(productList){
  //do something
}
```


### 3. Code repetition:
###### ❌ Don't: 
```javascript
let totalWearingProductPrice = 0;
for (let index = 0; index < wearingProductList.length; index++) {
  let wearingProduct = wearingProductList[index];
  totalWearingProductPrice += wearingProduct.price;
};

let totalFoodProductPrice = 0;
for (let index = 0; index < foodProductList.length; index++) {
  let foodProduct = foodProductList[index];
  totalFoodProductPrice += foodProduct.price;
};
```

###### ✅ It should be:
```javascript
function calculateProductPrice (products) => {
  let total = 0;
  for (let index = 0; index < products.length; index++) {
    let product = products[index];
    total += product.price;
  };
  return total;
}

let totalWearingProductPrice = calculateProductsPrice(wearingProductList);
let totalFoodProductPrice = calculateProductsPrice(foodProductList);

```

### 4. Coding tricks:
##### 4.1. Enum:
* If you have to compare 2 values, let use a enum:
###### ❌ Don't: 
```javascript
if(orderStatusCode === 123){
  //do something
}
```

###### ✅ It should be:
```javascript
const ORDER_STATUS_CODE={
  "NEW": 1,
  "DELIVERY": 2,
  "SHIPPING": 3,
  "COMPLETE": 10,
  ...
};

if (oderStatusCode === ORDER_STATUS_CODE.SHIPPING) {
  //do something
}
```

