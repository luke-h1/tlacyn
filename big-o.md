## what is big o?

Big o is a way to categorize your algorithms time or memory
requirements based on input. It is not meant to be an exact
measurement. It will not tell you how many CPU cycles it takes,
instead it is meant to generalize the growth of your algorithm.

Example:
When someone says Oh of N, they mean your algorithm will grow
linearily based on the input.

Example:

How does this function's execution time grow with respect to input?

```ts
function sum_char_codes(n: string): number {
  let sum = 0;

  for (let i = 0; i < n.length; i += 1) {
    sum += n.charCodeAt(i);
  }

  return sum;
}
```

The for loop has to execute the length of the string. If the
string grows by 50%, how much slower will the function be? : 50%.
It grows linearly. For everyone one more unit of string, there is
one more loop that it has to do.

finding the big o in things can be easy as looking for loops.

What's the running time?

If the previous example was o(n), what's this?

```ts
function sum_char_codes(n: string): number {
  let sum = 0;

  for (let i = 0; i < n.length; i += 1) {
    sum += n.charCodeAt(i);
  }

  for (let i = 0; i < n.length; i += 1) {
    sum += n.charCodeAt(i);
  }

  return sum;
}
```

It's 0(2N). This is because big o is meant to describe the upper
bound of the algorithm (the growth of the algorithm). The constant
eventually becomes irrelevant. It's still 0(N).

i.e.

N = 1, O(10N) = 10, O(N^2) = 1

N = 5, O(10N) = 50, O(N^2) = 25

N = 100, O(10N) = 1,000, O(N^2) = 10,000 // 10x bigger

N = 1000, O(10N) = 10,000, O(N^2) = 1,000,000 // 100x bigger

N = 10000, O(10N) = 100,000, O(N^2) = 100,000,000 // 1000x bigger

As your input grows, how fast does computation or memory grow?
Concepts:

1. growth is with respect to input

In the real world:

1. Memory growing is not computationally free, but when thinking
   in terms of algorithms, we don't necessarily think about that.

2. In languages like Go or Javascript, you pay even heavier
   penalties because the memory can be kept around, grows
   faster & can cause halts in your program.

Another example:

```ts
function sum_char_codes(n: string): number {
  let sum = 0;

  for (let i = 0; i < n.length; i += 1) {
    const charCode = n.charCodeAt(i);

    // Capital E
    if (charCode === 69) {
      return sum;
    }

    sum += charCode;
  }

  return sum;
}
```

this is considered the worst case. Any string with E in it
will terminate early (unless E is the last item in the list).
It's still O(N).

Important concepts (time & complexity):

1. Growth is with respect to input
2. Constant are dropped
3. Worst case is usually the way we measure - rarely going to be asked in interviews about best cases

O(N^2) example (squared):

```ts
function sum_char_codes(n: string): number {
    let sum = 0;
    for (let i = 0; i < n.length i += 1) {
        for (let j = 0; j < n.length; j += 1) {
            sum += n.charCodeAt(i);
        }
    }

    return sum;
}
```

for every single character, we go over every single character again. This is O(N^2).

O(N^3) example (cubed):

```ts
function sum_char_codes(n: string): number {
  let sum = 0;
  for (let i = 0; i < n.length; i += 1) {
    for (let j = 0; j < n.length; j += 1) {
      for (let k = 0; k < n.length; k += 1) {
        sum += n.charCodeAt(i);
      }
    }
  }

  return sum;
}
```

O(n log n):
* quicksort (implement & explain later)


O(log n):
* Binary search trees (implement & explain later)


O(sqrt(n)):
* unique algorithm (implement & explain later)

