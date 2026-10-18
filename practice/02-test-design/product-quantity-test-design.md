## Test Design Exercise

Requirement: A product quantity must be between **1 and 10**.

Create:

- Positive tests: Write at least 3 valid test cases.
- Negative tests: Write at least 5 invalid test cases.  
Then apply:
- Equivalence Partitioning
- Boundary Value Analysis

### Answers
- **Positive tests**
```text
1
5
10
```

| ID           | Test Case                                              | Test Data                | Expected Result           |
| ------------ | ------------------------------------------------------ | ------------------------ | ------------------------- |
| TC_PROD_001  | Add a product with the minimum allowed quantity        | product quantity: 1      | 1 product can be added    |
| TC_PROD_002  | Add a product with a quantity within the allowed range | product quantity: 5      | 5 products can be added   |
| TC_PROD_003  | Add a product with the maximum allowed quantity.       | product quantity: 10     | 10 product can be added   |

- **Negative tests**
```text
0
11
-1
"abc"
empty
"  10" -> Invalid
```

| ID           | Test Case                                    | Test Data                | Expected Result         |
| ------------ | -------------------------------------------- | ------------------------ | ----------------------- |
| TC_PROD_004  | Reject a product quantity below the minimum  | product quantity: 0      | Quantity is rejected    |
| TC_PROD_005  | Reject a product quantity above the maximum  | product quantity: 11     | Quantity is rejected    |
| TC_PROD_006  | Reject negative product quantity             | product quantity: -1     | Quantity is rejected    |
| TC_PROD_007  | Reject non-numeric product quantity          | product quantity: "abc"  | Quantity is rejected    |
| TC_PROD_008  | Reject an empty product quantity             | product quantity:        | Quantity is rejected    |

- **Equivalence Partitioning**
```text
< 1 -> Invalid
1 - 10 -> valid
> 10 -> Invalid
```

| Equivalence partition  | Example | Expected Result   |
| ---------------------- | ------- | ----------------- |
| Quantity below 1       | 0       | Invalid           |
| Quantity from 1 to 10  | 5       | Valid             |
| Quantity above 10      | 11      | Invalid           |

- **Boundary Value Analysis**
```text
0 -> Invalid
1 -> valid
2 -> valid
9 -> valid
10 -> valid
11 -> Invalid
```

| Value  | Expected Result | Why                    |
| ------ | --------------- | ---------------------- |
| 0      | Invalid         | Just below minimum     |
| 1      | Valid           | Minimum boundary       |
| 2      | Valid           | Just above minimum     |
| 9      | Valid           | Just below maximum     |
| 10     | Valid           | Maximum boundary       |
| 11     | Invalid         | Just above maximum     |
