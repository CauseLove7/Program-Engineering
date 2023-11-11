# Тема 6. Базовые коллекции: словари, кортежи.
### Отчет по Теме #6 выполнил:
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
### Ключ доступа в школьные кабинеты
#### Выполнение:
```python
request = int(input('Введите номер кабинета'))

dictionary = {
    101: {'key': 1234, 'access': True},
    102: {'key': 1337, 'access': True},
    103: {'key': 8943, 'access': True},
    104: {'key': 5555, 'access': False},
    None: {'key': None, 'access': False},
}

response = dictionary.get(request)
if not response:
    response = dictionary[None]
key = response.get('key')
access = response.get('access')
print(key,access)
```
#### Результат
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/ceef62b4-2dc0-47c6-b731-e4422c70c8cd)
## Задание №2
### Самый большой словарь в мире
#### Выполнение:
```python
from pprint import pprint

my_dict = {'first':'so easy'}

def dict_maker(**kwargs):
    my_dict.update(**kwargs)

dict_maker(a1 = 1, a2 = 20, a3 = 54, a4  = 13)
dict_maker(name = 'Maxim', age = 1, weight = 100, eyes_color = 'red')
pprint(my_dict)
```
#### Результат
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/793fe868-be90-4d25-8a34-a32c57ff20d6)
## Задание №3
### Разложение строки на символы
#### Выполнение:
```python
input_string = 'HelloWorld'
result = tuple(input_string)
print(result)
print(list(result))
```
#### Результат
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/f8e7f08a-bf09-49ab-a333-bcc2b9ef9b09)

## Задание №4
### 
#### Выполнение:
```python

```
#### Результат

## Задание №5
### 
#### Выполнение:
```python

```
#### Результат

## Самостоятельная работа №1
## Задание №1
### 
#### Выполнение:
```python

```
#### Результат

#### Вывод:

## Задание №2
### 
#### Выполнение:
```python

```
#### Результат

#### Вывод:

## Задание №3
### 
#### Выполнение:
```python

```
#### Результат

#### Вывод:

## Задание №4
### 
#### Выполнение:
```python

```
#### Результат

#### Вывод:

## Задание №5
### 
#### Выполнение:
```python

```
#### Результат

#### Вывод:

## Общий вывод:
