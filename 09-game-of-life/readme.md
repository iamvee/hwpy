## Conway's Game of Life 

| topics |
| :- |
| object oriented programming   |
| standard libraries  |


### Description 



### general format

```python

class Grid:
    def __init__(self, width, height):
        # complete grid locations
        # change the following line 
        self.__grid = [[None for i in range(width)] for j in range(height)]

    def __getitem__(self, key):
        if not isinstance(key, tuple):
            raise TypeError

        if not len(key) == 2:
            raise ValueError

        try:
            return self.__grid[key[0]][key[1]]
        except IndexError:
            raise KeyError

    def __setitem__(self, key, value):
        try:
            self[key]
        except KeyError:
            pass

        self.__grid[key[0]][key[1]] == value


class GameOfLife(Grid):
    def __setitem__(self, key, value):
        if not isinstance(value, bool):
            raise TypeError   # grid only cointains values of typew boolean
        return super().__setitem__(key, value)

    def __next__(self):
        pass

    def __iter__(self):
        pass
```