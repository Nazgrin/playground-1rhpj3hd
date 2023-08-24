# "Magic Methods" or "Dunder Methods" of Python Classes

The `__str__` method of the Fruit class has been overridden for a formatted string representation. 

```python runnable
class Fruit:
    def __init__(self, name, color):
        self.name = name
        self.color = color

    def __str__(self):
        return f"{self.color} {self.name}"

class Vegetable:
    def __init__(self, name, color):
        self.name = name
        self.color = color


apple = Fruit("Apple", "Red")
banana = Fruit("Banana", "Yellow")
carrot = Vegetable("Carrot", "Orange")

print(apple)                            # Red Apple
print(banana)                           # Yellow Banana

print(carrot)                           # <__main__.Vegetable object at 0x000000000000>
```
The `__eq__` method has been overridden to check the equality of objects.
\n -Note that in the `__eq__` method, we ensure that the passed other object is of the correct type before checking equality to avoid errors (`isinstance()`).

```python runnable
class Fruit:
    def __init__(self, name, color):
        self.name = name
        self.color = color

    def __eq__(self, other):
        if isinstance(other, Fruit):
            return self.name == other.name and self.color == other.color
        return False

class Vegetable:
    def __init__(self, name, color):
        self.name = name
        self.color = color

apple = Fruit("Apple", "Red")
another_apple = Fruit("Apple", "Red")
carrot = Vegetable("Carrot", "Orange")
another_carrot = Vegetable("Carrot", "Orange")

print(apple == apple)                                                                 # True
print(apple == another_apple)                                                         # True

print(carrot == carrot)                                                               # True
print(carrot == another_carrot)                                                       # False

print(carrot.name == another_carrot.name and carrot.color == another_carrot.color)    # True

```
Using `__getitem__`, we can retrieve the attribute values of a Fruit object using a key, and with `__setitem__`, we can update the attribute values using a key. This allows us to access and modify the attributes of an object as if it were a dictionary.

```python runnable
class Fruit:
    def __init__(self, name, color):
        self.name = name
        self.color = color

    def __str__(self):
        return f"{self.color} {self.name}"

    def __getitem__(self, key):
        if key == "name":
            return self.name
        elif key == "color":
            return self.color
        else:
            raise KeyError(f"Invalid key: {key}")

    def __setitem__(self, key, value):
        if key == "name" or key == "designation":
            self.name = value
        elif key == "color":
            self.color = value
        else:
            raise KeyError(f"Invalid key: {key}")

class Vegetable:
    def __init__(self, name, color):
        self.name = name
        self.color = color

    def __str__(self):
        return f"{self.color} {self.name}"

apple = Fruit("Appel", "Red")
print(apple["color"])                   # Red               __getitem__
print(apple["name"])                    # Appel             __getitem__
apple["name"]   = "Apple"               #                   __setitem__
apple["color"]  = "Green"               #                   __setitem__
print(apple)                            # Green Apple

banana = Fruit("Banana", "Gold")
banana["designation"] = "Gros Michel"   #                   __setitem__
print(banana)                           # Gold Gros Michel

pumpkin = Vegetable("Pumpkin", "Green") 
pumpkin.color = "Orange"                                   
print(pumpkin)                          # Orange Pumpkin
```
# Advanced usage

If you want a more complex example (external libraries, viewers...), use the [Advanced Python template](https://tech.io/select-repo/429)
