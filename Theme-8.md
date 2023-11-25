### Отчет по Теме #8 Введение ООП
- Козлов Максим Игоревич
- ПИЭ-21-2

| Задание | Лаб. раб. | Сам. раб. |
| ------ | ------ | ------ |
| Задание 1 | + | + |
| Задание 2 | + | + |
| Задание 3 | + | + |
| Задание 4 | + | + |
| Задание 5 | + | + |

Работу проверили:
- к.э.н., доцент Панов М.А.

## Лабораторная работа №1
## Задание №1
### Создание класса Car.
#### Выполнение:
```python
class Car:
    def __init__(self, make, model):
        self.make = make
        self.model = model

myCar = Car("Nissan", "GTR")
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/8f883401-3d23-4110-a397-9f1cfe3cb03e)
## Задание №2
### Дополнение кода из первого задания + атрибуты.
#### Выполнение:
```python
class Car:
    def __init__(self, make, model):
        self.make = make
        self.model = model
    def drive(self):
        print(f"Driving the {self.make} {self.model}")

myCar = Car("Nissan", "GTR")
myCar.drive()
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/dc28656e-4e53-4193-93d2-dbab303752ab)
## Задание №3
### Создание класса ElectricCar.
#### Выполнение
```python
class Car:
    def __init__(self, make, model):
        self.make = make
        self.model = model

    def drive(self):
        print(f"Driving the {self.make} {self.model}")

class ElectricCar(Car):
    def __init__(self, make, model, battery_capacity):

        super().__init__(make, model)
        self.battery_capacity = battery_capacity

    def charge(self):
        print(f"Charging the {self.make} {self.model} with {self.battery_capacity} kWh")

my_electric_car = ElectricCar("Tesla", "Model S", 75)

my_electric_car.drive()

my_electric_car.charge()
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/2437b477-cdd9-48d5-9763-6a093c5c89fb)
## Задание №4
### Реализуйте инкапсуляцию для класса, созданного в первом задании.
#### Выполнение:
```python
class Car:
    def __init__(self, make, model):
        self.make = make
        self.model = model

    def drive(self):
        print(f"Driving the {self.make} {self.model}")

myCar = Car("Nissan", "GTR")
print(myCar.make)
myCar.drive()
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/bf10c5b0-cee0-4953-ad85-810d5f3732a4)
## Задание №5
### Реализация полиморфизма.
#### Выполнение:
```python
class Shape:
    def area(self):
        pass

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return 3.14 * self.radius * self.radius

myRectangle = Rectangle(5, 10)

result1 = myRectangle.area()

myCircle = Circle(10)
result2 = myCircle.area()

print(result1)
print(result2)
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/2d6debd0-5366-4800-be1b-33cc30ebc447)
## Самостоятельная работа №1
## Задание №1
### Самостоятельно придумать класс.
#### Выполнение:
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/5339e330-d181-4d97-98fd-3c0ef53db8cb)
#### Вывод:
Я решил написать простой класс,который будет выдавать имя человека и возраст.
## Задание №2
### Самостоятельно придумать класс и добавить атрибуты.
#### Выполнение:
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def introduce(self):
        print(f"My name is {self.name}")
        print(f"I'm {self.age} old")

person = Person("Maxim", 20)

person.introduce()
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/35c534eb-4241-4e28-8e19-429b6c4b81ee)
#### Вывод:
К первоначальному коду добавились строки, которые помогут выводить имя человека и возраст строка под именем "Person"
## Задание №3
### Реализация наследования в ранее написанном коде
#### Выполнение:
```python

```
#### Результат:

#### Вывод:

## Задание №4
### Самостоятельно придумать класс
#### Выполнение:
```python

```
#### Результат:

#### Вывод:

## Задание №5
### Самостоятельно придумать класс
#### Выполнение:
```python

```
#### Результат:

#### Вывод:
