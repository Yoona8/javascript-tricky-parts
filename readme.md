# JavaScript Tricky Parts (Interview questions)

### 1. What is the output?

```JavaScript
(window.foo || (window.foo = 'bar'));
console.log(window.foo);
```

<details>
<summary>Answer</summary>

`'bar'`

</details>