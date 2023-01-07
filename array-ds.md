if `const a = []` isn't an array, what is?

Array - an un-breaking memory space that contains a certain amount of bytes

```ts
const a = new ArrayBuffer(6);
const a8 = new Uint8Array(a); // unsigned int numbers 0-255

a8[0] = 45;
```
