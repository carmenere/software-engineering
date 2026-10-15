# Proxy pattern
In essence, the **proxy pattern** is about creating a intermediate object that controls **access**, **logging**, **lazy instantiation**, or even add enhancements to the real object.<br>
It’s a **perfect choice** for **controlled**, **enhanced**, or **delayed access to an underlying system**.<br>

<br>

## Example
Consider 2 classes: `RealDocument` and `DocumentProxy`, in such example:
- the `RealDocument` class represents the **real object** with methods to display and modify content;
- the `DocumentProxy` class **acts as a proxy**, controlling access to the `RealDocument`:
  - it checks if the user has write permissions before allowing modifications;
  - if the user doesn't have the required permissions, it prints an error;

<br>

# Delegation pattern
In **delegation pattern**, a **delegator** handles a request by delegating part of its functionality to a another object (the **delegate**). The **delegate** is a **helper object**, but with the original context.<br>

<br>

The **delegation pattern** has 3 parts:
- the **delegating object** (**delegator**): it handles a request **by delegating** it to a another object (**delegate**);
- the **delegate** (**helper object**): it handles a request;
- the **delegation protocol**: it is an **interface** the **delegate** must implement;
  - that **delegator may** implement the the **delegation protocol**, but this is **not a requirement** of the **delegation pattern**;

<br>

Delegation usually use **composition**, to store reference to its delegates, but *delegator* can provide method that recieve *delegate* and call appropriate method on it but **does not store it**.<br>

<br>

When **both** *delegator* and *delegate* **implement** *delegation protocol* the whole pattern work as follows:<br>
![delegation](/img/delegation-1.png)

<br>

## Example: Printers implementation (java)
### Printer Interface
```java
public interface Printer {
    void print(String message);
}
```

<br>

### CanonPrinter Class
```java
public class CanonPrinter implements Printer {
    @Override
    public void print(String message) {
        System.out.println("Canon Printer: " + message);
    }
}
```

<br>

### EpsonPrinter Class
```java
public class EpsonPrinter implements Printer {
    @Override
    public void print(String message) {
        System.out.println("Epson Printer: " + message);
    }
}
```

<br>

### PrinterController Class
```java
public class PrinterController implements Printer {

    private final Printer printer;

    public PrinterController(Printer printer) {
        this.printer = printer;
    }

    @Override
    public void print(String message) {
        printer.print(message);
    }
}
```

<br>

The `PrinterController` class does not handle the actual printing process. Instead, it **delegates** this responsibility to the classes that implement the `Printer` interface.<br>
The `PrinterController` is a **delegator**, and the `EpsonPrinter` and `CanonPrinter` are the **delegates**.<br>

<br>

The delegation is achieved via the **constructor** which accepts a `Printer` object. The `print()` method calls the `print()` method of the **delegated** `Printer` object:
```java
public class App {

    public static final String MESSAGE_TO_PRINT = "hello world";

    public static void main(String[] args) {
        PrinterController hpPrinterController = new PrinterController(new HpPrinter());
        PrinterController canonPrinterController = new PrinterController(new CanonPrinter());
        PrinterController epsonPrinterController = new PrinterController(new EpsonPrinter());

        hpPrinterController.print(MESSAGE_TO_PRINT);    // Output: HP Printer: hello world
        canonPrinterController.print(MESSAGE_TO_PRINT); // Output: Canon Printer: hello world
        epsonPrinterController.print(MESSAGE_TO_PRINT); // Output: Epson Printer: hello world
    }
}
```


<br>

# Visitor vs. Delegation
**Visitor** uses **delegation**. **Delegation** is a **general mechanism**. **Visitor** is a **specific pattern** built on top of it.<br>

Relationship:
- **Delegator** ≈ **Element** (the one that calls out);
- **Delegate** ≈ **Visitor** (the one being called);

<br>

Structurally they look the same. But they have some **key differences**:
- **who controls the operation?** - the most important difference:

||**Caller**|**Callee**|
|:-|:-----|:-----|
|**Delegation**|**active** (*delegator*), it decides which method to call and when|**passive** (*delegate*), it just handles request|
|**Visitor**|**passive** (*element*), it just passes itself to appropriate visitor's method|**active** (*visitor*), it decides what to do with element|

<br> 

- **cardinality and coupling**
||**Cardinality**|**Methods**|
|:-|:-----|:-----|
|**Delegation**|usually 1 delegator <-> 1 delegate|The *delegate protocol* is **specific to** delegator. Different delegators have different protocols.|
|**Visitor**|1 visitor <-> many element types|The element's interface has only one method - usually called `accept(visitor)`. The visitor's interface has one method per element type - the total number of methods is equal to the total number of elements. The same visitor works across the whole element hierarchy.|

<br>

- **does the caller store called object?**:
  - the **visitor** is **not stored** inside **element**, and it is usually per-call;
  - the **delegate** is **usually stored** inside **delegator**;
