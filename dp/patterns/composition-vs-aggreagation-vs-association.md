# Association vs. Aggregation
Consider 3 examples:
1. The **whole team** consists of **players** (holds references to its parts), it is **aggregation**:
```c++
class Team {
    std::vector<Player*> players;  // Team has Players as members → aggregation
};
```

2. The driver **uses** a car, it is **association**:
```c++
class Driver {
    Car* car;  // Driver uses a Car → association
};
```

3. That’s still usually an **association**, because the *driver* **doesn’t part of** *car*:
```c++
class Car {
    Driver* driver;  // Car has an assigned Driver
};
```

<br>

But, *third example* **could become aggregation** only if you model the `Driver` as a **temporary part of** the `Car` **during driving**.<br>

<br>

- `Player` <-> `Team`: `Team` is a whole made of `Players`, `Player` is a member/part of the `Team`: it is **aggregation** (which is also an **association**, **but more specific**);
- `Driver` <-> `Car`: `Driver` **operates**/**uses** a `Car`: it is plain **association**;
  - you can **force** `Driver` <-> `Car` into **aggregation** by defining "the `Driver` as a **temporary part of** the `Car` **during driving**" but that is an **extra modeling decision**, **not the natural domain meaning**;

<br>

# Quick summary
|Relationship|Typical syntax in the code|Ownership|Lifetime|
|:-----------|:-------------------------|:--------|:-------|
|**Association**|reference/collection of references|**none**|independent|
|**Aggregation**|reference/collection of references|**weak**/shared|independent|
|**Composition**|instance is **created inside** and assigned to attribute|**strong**/exclusive|tied to owner|
