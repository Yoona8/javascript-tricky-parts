# JavaScript Tricky Parts (Interview questions)

### 1. What is the output?

```JavaScript
(window.foo || (window.foo = 'bar'));
console.log(window.foo);
```

<details>
<summary>Answer</summary>
<p>

`'bar'`

</p>
</details>

### 2. What is the difference?

```JavaScript
!!(obj1 && obj2);
(obj1 && obj2);
```

<details>
<summary>Answer</summary>
<p>

`!!(obj1 && obj2);` returns boolean and `(obj1 && obj2);` returns obj2 (if both objects exist, otherwise reference error)

</p>
</details>

### 3. What is the output?

```JavaScript
console.log('1' + 2 + 4);
```

<details>
<summary>Answer</summary>
<p>

`124`

</p>
</details>

### 4. What is the output?

```JavaScript
console.log('2' > '14');
```

<details>
<summary>Answer</summary>
<p>

`true` string `2` is > string `14`

</p>
</details>

### 5. What is the output?

```JavaScript
console.log(2 + 5 + '8');
```

<details>
<summary>Answer</summary>
<p>

`78`

</p>
</details>

### 6. What is the output?

```JavaScript
'use strict';

var age = 20;

if (age >= 18) {
    function sayHi() {
        console.log('Allowed');
    }
} else {
    function sayHi() {
        console.log('Under 18 is not allowed');
    }
}

sayHi();
```

<details>
<summary>Answer</summary>
<p>

Reference error (`sayHi` is not defined). Without use strict one of the functions (depending on the age).

</p>
</details>

### 7. What does new do?

```JavaScript
function Animal(name) {
    this.name = name;
    this.canTalk = true;
}

const cat = new Animal('Cat');
```

<details>
<summary>Answer</summary>
<p>

```JavaScript
function Animal(name) {
    this = {}; // added by interpreter
    this.name = name;
    this.canTalk = true;
    return this; // added by interpreter
}

const cat = new Animal('Cat');
```

</p>
</details>

### 8. What is the output in any case?

```JavaScript
let cat = new Animal('Cat');
console.log(cat.name);

function Animal(name) {
    this.name = name;
    this.canTalk = true;
}

function Animal(name) {
    this.name = name;
    this.canTalk = true;

    return 'Dog';
}

function Animal(name) {
    this.name = name;
    this.canTalk = true;

    return {
        name: 'Dog'
    };
}
```

<details>
<summary>Answer</summary>
<p>

`1 - Cat; 2 - Cat; 3 - Dog`

</p>
</details>

### 9. How can you hide properties and methods of the object (like private)?

<details>
<summary>Answer</summary>
<p>

```JavaScript
function Animal(name) {
    var privateMethod = (text) => {
        console.log(text);
    };

    this.sayHi = (name) => {
        privateMethod(`Hello ${name}`)
    };

    this.name = name;
    this.canTalk = true;
}
```

</p>
</details>

### 10. Is it possible to create functions A and B so that object a = object b?

```JavaScript
function A() {}
function B() {}

var a = new A();
var b = new B();

console.log(a === b); // true
```

<details>
<summary>Answer</summary>
<p>

```JavaScript
var animal = {
    name: 'Cat'
};

function A() {
    // some code
    return animal;
}
function B() {
    // some code
    return animal;
}

var a = new A();
var b = new B();

console.log(a === b); // true
```

</p>
</details>

### 11. What is the output?

```JavaScript
var arr = [1, 2, 15];

arr.sort();
console.log(arr);
```

<details>
<summary>Answer</summary>
<p>

`[1, 15, 2]`

</p>
</details>