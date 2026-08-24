# SOLID Principles in Python

SOLID is a set of five design principles that help developers write object-oriented code that is easier to maintain, extend, and test. These principles were introduced to solve common problems that arise in software as it grows in size and complexity, such as tightly coupled classes and code that breaks easily when new features are added. Each letter in SOLID stands for one principle. Below, I have explained each principle in my own words with Python code samples I wrote to demonstrate them.

## 1. Single Responsibility Principle (SRP)

A class should have only one reason to change, responsibility should be encapsulated by class.

```python
class Invoice:
    def __init__(self, amount):
        self.amount = amount

    def calculate_total(self, tax_rate):
        return self.amount + (self.amount * tax_rate)

class InvoicePrinter:
    def print_invoice(self, invoice, total):
        print(f"Invoice amount: {invoice.amount}, Total with tax: {total}")

invoice = Invoice(1000)
total = invoice.calculate_total(0.18)
printer = InvoicePrinter()
printer.print_invoice(invoice, total)
```

Here, the `Invoice` class only handles the calculation logic, while the `InvoicePrinter` class only handles the display logic. Separating these responsibilities means a change in how invoices are printed will not affect how totals are calculated.

## 2. Open/Closed Principle (OCP)

open for extension, but closed for modification. It allows adding new functionality as new classes keeping as much as possible existing code unchanged.

```python
from abc import ABC, abstractmethod

class Discount(ABC):
    @abstractmethod
    def apply(self, price):
        pass

class NoDiscount(Discount):
    def apply(self, price):
        return price

class FestiveDiscount(Discount):
    def apply(self, price):
        return price * 0.9

def get_final_price(price, discount: Discount):
    return discount.apply(price)

print(get_final_price(1000, NoDiscount()))
print(get_final_price(1000, FestiveDiscount()))
```

If we want to add a new discount type in the future, such as a clearance sale discount, we can create a new class that extends `Discount` instead of modifying the existing `get_final_price` function.

## 3. Liskov Substitution Principle (LSP)

A child class should be able to replace its parent class without breaking the program.

```python
class Bird:
    def move(self):
        print("This bird moves.")

class Sparrow(Bird):
    def move(self):
        print("Sparrow flies in the sky.")

class Penguin(Bird):
    def move(self):
        print("Penguin swims in water.")

def make_bird_move(bird: Bird):
    bird.move()

make_bird_move(Sparrow())
make_bird_move(Penguin())
```

Both `Sparrow` and `Penguin` override the `move` method in a way that still makes sense for a `Bird`, so either can be substituted wherever a `Bird` object is expected, without causing incorrect behaviour.

## 4. Interface Segregation Principle (ISP)

A class should not be forced to implement methods that it does not need.

```python
from abc import ABC, abstractmethod

class Printer(ABC):
    @abstractmethod
    def print_document(self):
        pass

class Scanner(ABC):
    @abstractmethod
    def scan_document(self):
        pass

class SimplePrinter(Printer):
    def print_document(self):
        print("Printing document...")

class MultiFunctionPrinter(Printer, Scanner):
    def print_document(self):
        print("Printing document...")

    def scan_document(self):
        print("Scanning document...")
```

Here, `SimplePrinter` only implements the `Printer` interface since it cannot scan, while `MultiFunctionPrinter` implements both interfaces. If we had combined printing and scanning into a single interface, `SimplePrinter` would have been forced to implement a `scan_document` method it does not need.

## 5. Dependency Inversion Principle (DIP)

A class should depend on abstraction instead of depending on the specific class.

```python
from abc import ABC, abstractmethod

class NotificationService(ABC):
    @abstractmethod
    def send(self, message):
        pass

class EmailNotification(NotificationService):
    def send(self, message):
        print(f"Sending email: {message}")

class SMSNotification(NotificationService):
    def send(self, message):
        print(f"Sending SMS: {message}")

class OrderService:
    def __init__(self, notifier: NotificationService):
        self.notifier = notifier

    def place_order(self):
        print("Order placed.")
        self.notifier.send("Your order has been placed.")

order = OrderService(EmailNotification())
order.place_order()
```

The `OrderService` class depends on the `NotificationService` abstraction rather than a specific notification class. This means we can pass in `EmailNotification`, `SMSNotification`, or any other class that implements `NotificationService`, without changing the `OrderService` code at all.



## References

* Digital Ocean, SOLID Design Principles Explained: https://www.digitalocean.com/community/conceptual-articles/s-o-l-i-d-the-first-five-principles-of-object-oriented-design
* Real Python, SOLID Principles: https://realpython.com/solid-principles-python/
* Python official documentation, abc module: https://docs.python.org/3/library/abc.html
