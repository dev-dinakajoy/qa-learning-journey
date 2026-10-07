## Practice Exercise

Consider this requirement: A product quantity must be between **1 and 10**.

Create:

### Positive tests

Write at least **3 valid test cases**.

**Answer:**

```text
1
5
10
```

### Negative tests

Write at least **5 invalid test cases**.

**Answer:**

```text
0
11
-1
"abc"
empty
```

Then apply:

* **Equivalence Partitioning**
Answer:
```text
< 1 -> Invalid
1 - 10 -> valid
> 10 -> Invalid
```
* **Boundary Value Analysis**
Answer:
```text
0 -> Invalid
1 -> valid
2 -> valid
9 -> valid
10 -> valid
11 -> Invalid
```
* **Positive Testing**
**Answer:**
```text
3 -> valid
6 -> valid
8 -> valid
```
* **Negative Testing**
Answer:
```text
-2 -> Invalid
13 -> Invalid
"  10" -> Invalid
```
