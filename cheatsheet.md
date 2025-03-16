```python
# Definition af Variables & Data Types
name = "Alice"  # String
age = 12        # Integer
height = 1.55   # Float
is_happy = True # Boolean

# Lists, Tuples, Sets, and Dictionaries
fruits = ["apple", "banana", "cherry"]  # List
colors = ("red", "green", "blue")       # Tuple
unique_numbers = {1, 2, 3, 3, 4}        # Set (removes duplicates)
student = {"name": "Alice", "age": 12}  # Dictionary

# Loops
for fruit in fruits:
    print(fruit)  # Loop through a list

for key, value in student.items():
    print(key, "->", value)  # Loop through a dictionary

x = 0
while x < 3:
    print(x)
    x += 1

# Functions
def greet(name):
    return "Hello, " + name + "!"

print(greet("Alice"))  # Output: Hello, Alice!

# Objects (Classes) & Looping Through Objects (Det har vi ikke lært endnu)
# Defining a Class
class Student:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def introduce(self):
        return f"My name is {self.name} and I am {self.age} years old."

# Creating Objects
students = [
    Student("Alice", 12),
    Student("Bob", 14),
    Student("Charlie", 13)
]

# Looping Through Objects
for student in students:
    print(student.introduce())
