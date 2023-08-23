# "Magic Methods" of Python Objects

This Python template lets you get started quickly with a simple one-page playground.

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

print(apple)

print(apple == banana)
print(apple == Fruit("Apple", "Red"))

print(carrot == apple)
```

# Advanced usage

If you want a more complex example (external libraries, viewers...), use the [Advanced Python template](https://tech.io/select-repo/429)