# ISO/IEC/IEEE 24765:2017 - Systems and software engineering
[**ISO/IEC/IEEE 24765:2017**](https://www.iso.org/obp/ui#iso:std:iso-iec-ieee:24765:ed-2:v1:en:sec:11.22)

<br>

**Component**:
- an entity with discrete structure, such as an assembly or software module, within a system considered at a particular level of analysis;
- one of the parts that make up a system;

<br>

A *component* may be **hardware** or **software** and may be subdivided into *other components*.<br>

<br>

**Module**:
- a program **unit** that is **discrete** and identifiable with respect to **compiling**, **combining with other units**, and **loading**;
- a logically separable part of a program;
- a set of source code files under version control that can be manipulated together as one;

<br>

**Note**: the terms **module**, **component**, and **unit** are **often used interchangeably** or **defined to be subelements of one another** in different ways depending upon the context. The relationship of these terms is not yet standardized.<br>

<br>

# Component vs. Module
**Модуль** — это **независимая единица организации кода**.<br>
**Компонент** — это **единица композиции системы**, которую можно заменять и которая взаимодействует с другими через интерфейсы.<br>

<br>

**Модуль** отвечает на вопрос: **Как организован код?**.<br>
**Компонент** отвечает на вопрос: **Из каких заменяемых частей состоит система и как они взаимодействуют?**.<br>

<br>

**Сравнение**:
|Характеристика|Компонент|Модуль|
|:-------------|:--------|:-----|
|Уровень абстракции|Архитектура, дизайн|Уровень сборки|
|Ключевое назначение|Единица декомпозиции, зависит от уровня анализа системы|Единица организации кода|

<br>
