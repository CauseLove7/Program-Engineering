### Отчет по Теме #8 выполнил:
- Трофименко Артем Сергеевич
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

myCar = Car("Toyota", "Mazda")
myCar.drive()
```
#### Результат:

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


