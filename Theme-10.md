# Тема 10. Декораторы и исключения.
### Отчет по Теме #10 выполнил:
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

## Лабораторная работа 
## Задание №1 Числа Фибоначчи.
#### Выполнение:
```python
from functools import lru_cache

@lru_cache
def fib(n):
    return n if n <= 1 else fib(n - 1) + fib(n - 2)

result_without_cache = fib(100)
print(f"Без декоратора: {result_without_cache}")

result_with_cache = fib(100)
print(f"С декоратором: {result_with_cache}")
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/998979c8-5b7a-4ff3-92b2-1cc56ebec0ae)
## Задание №2 Илья - программист.
#### Выполнение:
```python
def validate_user_data(x):
    def wrapper(name, age, *args, **kwargs):
        if 0 < age < 130:
            return x(name, age, *args, **kwargs)
        else:
            print("Ошибка: Некорректный возраст")
    return wrapper
@validate_user_data
def print_user_data(name, age):
    print(f"Имя: {name}, Возраст: {age}")

name = "Илья"
age = 17
print_user_data(name, age)

invalid_age = 150
print_user_data(name, invalid_age)

```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/c20684da-6950-462f-bae5-a074d958db37)
## Задание №3 Недохакер и сайт.
#### Выполнение:
```python
def validate_user_data(func):
    def wrapper(name, age, *args, **kwargs):
        try:
            age = int(age)
        except ValueError:
            print("Ошибка: Некорректный тип данных для возраста. Введите целое число.")
            return

        try:
            if 0 < age < 100:
                func(name, age, *args, **kwargs)
            else:
                print("Ошибка: Некорректный возраст")
        except Exception as e:
            print(f"Произошла ошибка: {e}")
        finally:
            print("Завершение функции")

    return wrapper

@validate_user_data
def print_user_data(name, age):
    print(f"Имя: {name}, Возраст: {age}")

name = "Илья"
valid_age = 17
invalid_age = "abc"

print_user_data(name, valid_age)
print_user_data(name, invalid_age)

```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/139e87a2-dba2-433a-87c9-1d8be33e1ac1)
## Задание №4 Успешная регистрация.
#### Выполнение:
```python
class NameTooLongError(Exception):
    pass

def validate_user_data(func):
    def wrapper(name, age, *args, **kwargs):
        user_name = input("Введите ваше имя: ")
        try:
            age = int(age)
        except ValueError:
            print("Ошибка: Некорректный тип данных для возраста. Введите целое число.")
            return

        try:
            if len(name) > 10:
                raise NameTooLongError("Ошибка: Имя пользователя слишком длинное")
            elif 0 < age < 100:
                func(name, age, *args, **kwargs)
                print("Успешная регистрация")
            else:
                print("Ошибка: Некорректный возраст")
        except NameTooLongError as e:
            print(e)
        except Exception as e:
            print(f"Произошла ошибка: {e}")
        finally:
            print("Завершение функции")

    return wrapper

@validate_user_data
def print_user_data(name, age):
    print(f"Имя: {name}, Возраст: {age}")

valid_name = "Илья"
invalid_name = "ОченьДлинноеИмя"

valid_age = 17

print_user_data(valid_name, valid_age)
print_user_data(invalid_name, valid_age)

```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/f12d04fe-9eca-4403-b9ec-3cc6dd35233e)

## Задание №5 Числа Фибоначчи.
#### Выполнение:
```python
class NameTooLongError(Exception):
    pass

def simple_logger_decorator(func):
    def wrapper(*args, **kwargs):
        try:
            result = func(*args, **kwargs)
            print(f"Результат выполнения функции {func.__name__}: {result}")
            return result
        except Exception as e:
            print(f"Произошла ошибка: {e}")
        finally:
            print("Завершение функции")

    return wrapper

@simple_logger_decorator
def validate_user_data(name, age, *args, **kwargs):
    user_name = input("Введите ваше имя: ")
    try:
        age = int(age)
    except ValueError:
        print("Ошибка: Некорректный тип данных для возраста. Введите целое число.")
        return
    try:
        if len(name) > 10:
            raise NameTooLongError("Ошибка: Имя пользователя слишком длинное")
        elif 0 < age < 100:
            print_user_data(name, age, *args, **kwargs)
            print("Успешная регистрация")
        else:
            print("Ошибка: Некорректный возраст")
    except NameTooLongError as e:
        print(e)

@simple_logger_decorator
def print_user_data(name, age, *args, **kwargs):
    print(f"Имя: {name}, Возраст: {age}")

valid_name = "Илья"
invalid_name = "ОченьДлинноеИмя"
valid_age = 17

validate_user_data(valid_name, valid_age)
validate_user_data(invalid_name, valid_age)

```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/622c49cc-d1bd-4b12-a6ee-aefc94f0c83b)

## Самостоятельная работа 
## Задание №1 Вова. Спорт.программирование.
#### Выполнение:
```python
import time
def timing_decorator(func):
    def wrapper(*args, **kwargs):
        start_time = time.time()
        result = func(*args, **kwargs)
        end_time = time.time()
        execution_time = end_time - start_time
        print(f"Время выполнения функции {func.__name__}: {execution_time} секунд")
        return result

    return wrapper

@timing_decorator
def timescore():
    for _ in range(1000000):
        pass

timescore()
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/9bb29fff-5a12-4154-94b9-d79613a0e5fd)
### Вывод:
Благодаря этому коду, можно подробно посмотреть сколько выполняется самая простая программа, например: Функция wrapper который измеряет время timing_decorator в функции, которую timing_decorator принимает - func.
## Задание №2
#### Выполнение:
```python
def read_file_content(file_path):
    try:
        with open(file_path, 'r') as file:
            content = file.read()
            if not content:
                raise ValueError("Файл пустой")
            return content
    except FileNotFoundError:
        print(f"Ошибка: Файл '{file_path}' не найден")
    except ValueError as ve:
        print(f"Ошибка: {ve}")
    except Exception as e:
        print(f"Произошла ошибка при чтении файла: {e}")

empty_file_path = 'empty_file.txt'
open(empty_file_path, 'w').close()

non_empty_file_path = 'non_empty_file.txt'
with open(non_empty_file_path, 'w') as file:
    file.write("Это какие-то данные в файле")

print("Содержимое пустого файла:")
read_file_content(empty_file_path)

print("\nСодержимое файла с данными:")
read_file_content(non_empty_file_path)
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/2fb64824-cb53-4f85-ade2-fb88c853fc40)
### Вывод:
Данный код позволяет создать,открыть уже созданный файл, и вывести информацию  в консоль из файла. Если файл пустой(данный скриншот) - мы получим ответ "Файл пустой". Если файл содержит в себе информацию, то получим информацию.
## Задание №3 Сложение +2.
#### Выполнение:
```python
def add_two_numbers():
    try:
        user_input = input("Введите число: ")
        number = float(user_input)
        result = 2 + number
        print(f"Результат сложения: {result}")
    except ValueError:
        print("Ошибка: Неподходящий тип данных. Ожидалось число.")

add_two_numbers()
add_two_numbers()
add_two_numbers()
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/c26c2759-7b24-41e3-88b7-c5fef8af2496)

### Вывод:
Результатом данного кода соответствует введение пользователем числа, который поступает в код и начинается сумма чисел на 2. Имеются свои подвохи. Числа могут быть целыми, с плавающей точкой, отрицательными. Все остальное код будет выдавать за ошибку.
## Задание №4
#### Выполнение:
```python
class MyDecorator:#Класс декоратора
    def __init__(self, func):
        self.func = func

    def __call__(self, *args, **kwargs):#Вызов декоратора и начало выполнения работы
        print(f"Декоратор начал работу для функции {self.func.__name__}")
        result = self.func(*args, **kwargs)
        print(f"Декоратор завершил работу для функции {self.func.__name__}")
        return result

# Пример функций
@MyDecorator
def startengine(x):
    return x * 2

@MyDecorator
def compliting(x):
    return x ** 2
#Результаты выполнения декораторов
result_1 = startengine(5)
result_2 = compliting(3)
#Выведение результатов в консоль
print(f"Результат умножения на 2: {result_1}")
print(f"Результат возведения в квадрат: {result_2}")

```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/db6c1a38-33c1-40af-8a8f-0685c062170f)
### Вывод:
В коде есть пояснения.
## Задание №5
#### Выполнение:
```python
import time
import random
import math

class ExecutionTimeDecorator:
    def __init__(self, func):
        self.func = func

    def __call__(self, *args, **kwargs):
        start_time = time.time()
        result = self.func(*args, **kwargs)
        end_time = time.time()
        execution_time = end_time - start_time
        print(f"Функция {self.func.__name__} выполнилась за {execution_time:.6f} секунд")
        return result

# Функция, которая генерирует случайное число
@ExecutionTimeDecorator
def Generator():
    return random.randint(1, 100)

# Функция, которая находит факториал числа
@ExecutionTimeDecorator
def Factorial():
    return math.factorial(random.randint(1,5))

# Пример использования декораторов
random_result = Generator()
factorial_result = Factorial()

print(f"Случайное число: {random_result}")
print(f"Факториал числа: {factorial_result}")


```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/a6c54f28-b5b9-4efa-8b28-7c13d61c9266)
### Вывод:
Генератор выводит случайное число, которое выводится в консоли. Также я написал код, чтобы факториал тоже брал из массива случайное числа и находил его факториал. Все это дело(для каждого!) имеется свой подсчет времени. Подсчет времени для вывода случайного числа и для факториала соответственно.
## Общий вывод:
Достаточно интересная тема Декораторов. Более подробно изучил момент облегчения кода. Сокращения в том числе. Декораторы позволяют более гибко изучать свои ошибки и более точно делить информацию на нужные группы и подгруппы.
