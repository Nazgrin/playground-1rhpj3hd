# "Magic Methods" of Python Objects

The __str__ method of the Fruit class has been overridden for a formatted string representation. 

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
The __eq__ method has been overridden to check the equality of objects. Note that in the __eq__ method, we ensure that the passed other object is of the correct type before checking equality to avoid errors.

```python runnable
class Fruit:
    def __init__(self, name, color):
        self.name = name
        self.color = color

    def __str__(self):
        return f"{self.color} {self.name}"

    def __eq__(self, other):
        if isinstance(other, Fruit):
            return self.name == other.name and self.color == other.color
        return False

class Vegetable:
    def __init__(self, name, color):
        self.name = name
        self.color = color

    def __str__(self):
        return f"{self.color} {self.name}"

    def __eq__(self, other):
        if isinstance(other, Vegetable):
            return self.name == other.name and self.color == other.color
        return False


apple = Fruit("Apple", "Red")
banana = Fruit("Banana", "Yellow")
carrot = Vegetable("Carrot", "Orange")

print(apple == banana)                  # False
print(apple == Fruit("Apple", "Red"))   # True
print(carrot == apple)                  # False
```

```python runnable
class Fruit:
    def __init__(self, name, color):
        self.name = name
        self.color = color

    def __str__(self):
        return f"{self.color} {self.name}"

    def __eq__(self, other):
        if isinstance(other, Fruit):
            return self.name == other.name and self.color == other.color
        return False

    def __getitem__(self, key):
        if key == "name":
            return self.name
        elif key == "color":
            return self.color
        else:
            raise KeyError(f"Invalid key: {key}")

    def __setitem__(self, key, value):
        if key == "name":
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

    def __eq__(self, other):
        if isinstance(other, Vegetable):
            return self.name == other.name and self.color == other.color
        return False


apple = Fruit("Apple", "Red")

print(apple["name"])        # Apple
print(apple["color"])       # Red

apple["color"] = "Green"
print(apple)                # Green Apple
```


# Advanced usage

If you want a more complex example (external libraries, viewers...), use the [Advanced Python template](https://tech.io/select-repo/429)
