# Тема 4. Функции и модули
### Отчет по Теме #4 выполнил:
- Козлов Максим Игоревич
- ПИЭ-21-2

| Задание | Лаб. раб. | Сам. раб. |
| ------ | ------ | ------ |
| Задание 1 | + | + |
| Задание 2 | + | + |
| Задание 3 | + | + |
| Задание 4 | + | + |
| Задание 5 | + | + |
| Задание 6 | + | - |
| Задание 7 | + | - |
| Задание 8 | + | - |
| Задание 9 | + | - |
| Задание 10 | + | - |

Работу проверили:
- к.э.н., доцент Панов М.А.

## Лабораторная работа №1
## Задание №1
### Напишите функцию, которая выполняет любые арифметические действия и выводит результат в консоль. Вызовите функцию используя “точку входа”.
#### Выполнение:
```python
def main():
    print(2+2)

if __name__ == '__main__':
    main()
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/fd357272-df14-4b47-ae0c-c76ac6007caa)
## Задание №2
### Напишите функцию, которая выполняет любые арифметические действия, возвращает при помощи return значение в место, откуда вызывали функцию. Выведите результат в консоль. Вызовите функцию используя “точку входа”.
#### Выполнение:
```python
def main():
    result = 2 + 2
    return result

if __name__ == '__main__':
    answer = main()
    print(answer)
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/f4d97172-a0dc-4485-a23f-ef694eda1b23)

## Задание №3
### Напишите функцию, в которую передаются два аргумента, над ними производится арифметическое действие, результат возвращается туда, откуда эту функцию вызывали. Выведите результат в консоль. Вызовите функцию в любом небольшом цикле.
#### Выполнение
```python
def main(one, two):
    result = one + two
    return result

for i in range(5):
    x = 1
    y = 10
    answer = main(x, y)
    print(answer)
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/4cf72216-41a2-487d-b7f0-0d42240b6a6e)

## Задание №4
### Напишите функцию, на вход которой подается какое-то изначальное неизвестное количество аргументов, над которыми будет производится арифметические действия. Для выполнения задания необходимо использовать кортеж “*args”
#### Выполнение:
```python
def main(x, *args):
    one = x
    two = sum(args)
    three = float(len(args))
    print(f"one={one}\ntwo={two}\nthree={three}")

    return x + sum(args) / float(len(args))

if __name__ == '__main__':
    result = main(10, 0, 1, 2, -1, 0, -1, 1, 2)
    print(f"\nresult={result}")
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/af38147b-8337-4d11-b45d-8df92a0fc01d)
## Задание №5
### Напишите функцию, которая на вход получает кортеж “**kwargs” и при помощи цикла выводит значения, поступившие в функцию
#### Выполнение:
```python
def main(**kwargs):
    for i in kwargs.items():
        print(i[0], i[1])

        print()

        for key in kwargs:
            print(f"{key} = {kwargs[key]}")

if __name__ == '__main__':
    main(x=[1,2,3], y=[3,3,0], z=[2,3,0], q=[3,3,0], w=[3,3,0])
    print()
    main(**{'x': [1,2,3], 'y': [3,3,0]})
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/b2605fee-cd97-459b-8487-440597a7d843)

## Задание №6
### Напишите две функции. Первая – получает в виде параметра “**kwargs”. Вторая считает среднее арифметическое из значений первой функции. Вызовите первую функцию используя “точку входа” и минимум 4 аргумента
#### Выполнение:
```python
def main(**kwargs):
    for i,j in kwargs.items():
        print(f"{i}. Mean = {mean(j)}")

def mean(data):
    return sum(data) / float(len(data))

if __name__ == '__main__':
    main(x=[1, 2, 3], y=[3, 3, 0])
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/20e59ae3-b9f8-4ae6-aae4-ec43a4f9ea2c)
## Задание №7
### Создайте дополнительный файл .py. Напишите в нем любую функцию, которая будет что угодно выводить в консоль, но не вызывайте ее в нем. Откройте файл main.py, импортируйте в него функцию из нового файла и при помощи “точки входа” вызовите эту функцию.
#### Выполнение:
```python
def say_hello():
    print('Hello World!')
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/ceb9f0ef-3c9b-47f7-8a1c-49fa11179b94)
## Задание №8
### Напишите программу, которая будет выводить корень, синус, косинус полученного от пользователя числа.
#### Выполнение:
```python
import math

def main():
    value = int(input('Введите значение: '))
    print(math.sqrt(value))
    print(math.sin(value))
    print(math.cos(value))

if __name__ == '__main__':
    main()
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/f5abc3da-b13b-4d51-8c69-9ca9e7caab9f)
## Задание №9
### Напишите программу, которая будет рассчитывать какой день недели будет через n-нное количество дней, которые укажет пользователь.
#### Выполнение:
```python
from datetime import datetime as dt
from datetime import timedelta as td

def main():
    print(
        f"Сегодня {dt.today().date()}. "
        f"День недели - {dt.today().isoweekday()}"
    )
    n = int(input('Введите количество дней: '))
    today = dt.today()
    result = today + td(days=n)
    print(
        f"Через {n} дней будет {result.date()}. "
        f"День недели - {result.isoweekday()}"
    )

if __name__ == '__main__':
    main()
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/92754f45-3638-41c9-ac69-587cb7524672)
## Задание №10
### Напишите программу с использованием глобальных переменных, которая будет считать площадь треугольника или прямоугольника в зависимости от того, что выберет пользователь. Получение всей необходимой информации реализовать через input(), а подсчет площадей выполнить при помощи функций. Результатом программы будет число, равное площади, необходимой фигуры.
#### Выполнение:
```python
global result

def rectangle():
    a = float(input("Ширина: "))
    b = float(input("Высота: "))
    global result
    result = a * b

def triangle():
    a = float(input("Основание: "))
    h = float(input("Высота: "))
    global result
    result = 0.5 * a * h

figure = input("1 - Прямоугольник, 2 - Трегуольник: ")

if figure == '1':
    rectangle()
elif figure == '2':
    triangle()

print(f"Площадь: {result}")
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/3a01e443-ce9a-43ca-9e75-2ed7dbc47929)
## Самостоятельная работа №1
## Задание №1
### Дайте подробный комментарий для кода, написанного ниже. Комментарий нужен для каждой строчки кода, нужно описать что она делает. Не забудьте, что функции комментируются по-особенному.
#### Выполнение:
```python
