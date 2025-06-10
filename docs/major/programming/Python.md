## learning path
David J. Malan(@Harvard University): [CS50P Introduction to Programming with Python](https://csdiy.wiki/%E7%BC%96%E7%A8%8B%E5%85%A5%E9%97%A8/Python/CS50P/){:target="_blank"}

Achieving CS50P final project: [Extract metadata from Instagram](https://github.com/Pengyu-Jin/CS50P-2022){:target="_blank"}

John DeNero(@UC Berkeley): [CS61A Structure and Interpretation of Computer Programs](https://csdiy.wiki/%E7%BC%96%E7%A8%8B%E5%85%A5%E9%97%A8/Python/CS61A/){:target="_blank"}

CS61A online textbook: [SICP in Python](https://www.composingprograms.com/){:target="_blank"}

CS61A soulutions, notes and final project: [...](){:target="_blank"}

!!! note "Pointview of Prof. Hany Farid in the CS61A course"

    There is this notion that learning happens when you solve a problem. That is completely wrong. **Learning happens when you don't solve the problem.** The process of failure, the process of struggling, and the process of taking hours to solve something are where the learning is happening.

    "Don't be frustrated by things not working. That’s the way it’s supposed to be. That’s what the process of learning is."

[相关资料](https://github.com/136108Haumea/my-manim/tree/master/book){:target="_blank}

## Unicode

&#10007;的unicode代码是`&#10007;`
复制&#10007;，然后利用网站，ascii码转unicode,即可得到

## Tips from Dr.Deng

> Material
>
> [清华邓博士/python课程资料](https://cmuw3vn7lg.feishu.cn/docx/KycuduTtUotbR1x3crzcewXKnfe){target="_blank"}


## Notes

**object**: A "bundle" of related attributes (variables) and methods (functions).

You need a "class" to create many objects.

**class**: (blueprint) Used to design the structure and layout of an object.

**class variable**: Shared among all instances of a class. Defined outside the constructor. Allow you to share data among all objects created from the class.

**Inheritance**: Allows a class to inherit attributes and methods from another class. Helps with cold reusability and extensibility.

class Child(Parent)

class Sub(Super)

!!! tips "Attention"

    In Python, a method is a type of attribute of an object.
    
    When you try to access a non-existent attribute--whether it's a data attribute or a method--Python raises an `AttributeError`.

    - Methods are callable attributes (bound functions).
    - Python doesn't distinguish between "missing method" and "missing attribute" errors -- both trigger `AttributeError`.
    - This design aligns with Python's dynamic nature (e.g., methods can be added/modified at runtime).

**multiple inheritance**: inherit from more than one parent class.

C(A, B)

**multilevel inheritance**: inherit from a parent which inherits from another parent.

C(B) <- B(A) <- A

**Abstract class**: A class that cannot be instantiated on its own; Meant to be subclassed.

They can contain abstract methods, which are declared but have no implementation.

Abstract classes benefits:

1. Prevents instantiation of the class itself
2. Requires children to use inherited abstract method

```python
from abs import ABC, abstractmethod

class Animal(ABC):
    @abstractmethod
    def eat(self):
        pass

    @abstractmethod
    def sleep(stop):
        pass
```

**super()**: Function used in a child class to call methods from a parent class (superclass). Allows you to extend the functionality of the inherited method.

**Polymorphism**: Greek word that means to "have many forms or faces". Poly = Many. Morphe = Form.

Two ways to achieve polymorphism

1. Inheritance. An object could be treated of the same type as a parent class.
2. Duck Typing. Object must have necessary attributes/methods.

**Duck Typing**: Object must have the minimum necessary attributes/methods.

"If it looks like a duck and quacks like a duck, it must be a duck."

**Aggregation**: Represents a relationship where one object (the whole) contains references to one or more INDEPENDENT objects (the parts).

