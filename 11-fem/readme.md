## Simple FEM Solver

* duplicated node numbers  are not allowed
* duplicated element tags are not allowed



### sample input

```
* NODES 
10 0 0
20 1 0
30 2 0
40 1 1
50 2 1
60 1 2

* ELEMS
100 10 20
200 20 30
300 10 40
400 20 40
500 20 50
600 30 50
700 40 50
800 40 60
900 50 60
```

### converted json input
```json
{
    "nodes": {
        10: [0, 0],
        20: [1, 0],
        30: [2, 0],
        40: [1, 1],
        50: [2, 1],
        60: [1, 2],
    },
    "links": {
        100: [10, 20],
        200: [20, 30],
        300: [10, 40],
        400: [20, 40],
        500: [20, 50],
        600: [30, 50],
        700: [40, 50],
        800: [40, 60],
        900: [50, 60],
    },
}
```