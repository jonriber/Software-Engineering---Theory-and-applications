# Oberserver Design Pattern

The `Observer Design Pattern` is a behavioral pattern that allows an object to maintain a list of dependents (observers)
and notify them automatically of any state changes, usually by calling one of their methods.

## When to use

- When I want to notify multiple objects about changes in another object
- When there is a `one-to-many` relationship between objects
- To implement `event handling systems`, like GUIs, logging systems, or messaging queues.

## Key concepts

- Subject: Maintains a list of observers and provides methods to attach/detach them.
- Observer: Defines an interface for objects that should be notified of changes in the subject.

## Basic example in Python

```python

class Observer:
  def update(self, message: str):
    pass

class Subject:
  def __init__(self):
    self._observers = []

  def attach(self, observer: Observer):
    self._observers.append(observer)

  def detach(self, observer: Observer):
    self._observers.remove(observer)
  
  def notify(self, message:str):
    for observer in self._observers:
      observer.update(message)

# Concrete Observers

class EmailNotifier(Observer):
  def update(self, message:str):
    print(f"[Email] Reveived notification: {message}")

class SMSNotifier(Observer):
  def update(self, message:str):
    print(f"[SMS] Received notification: {message}")

if __name__ == "__main__":
  subject = Subject()

  email = EmailNotifier()
  sms = SMSNotifier()

  subject.attach(email)
  subject.attach(sms)

  subject.notify("Product back in stock")

```

## Use Cases - Real life

- Event-driven programming
- Logging Services
- Realtime update systems (stock price tickers)
- Model-View-Controller (MVC) architecture: where views are observers of the model