# Тема 11. Декораторы и исключения.
### Отчет по Теме #11 выполнил:
- Козлов Максим Игоревич
- ПИЭ-21-2

| Задание | Лаб. раб. | Сам. раб. |
| ------ | ------ | ------ |
| Задание 1 | + | + |
| Задание 2 | + | + |
| Задание 3 | + | - |
| Задание 4 | + | - |
| Задание 5 | + | - |

Работу проверили:
- к.э.н., доцент Панов М.А.

## Лабораторная работа 
## Задание №1 Простой итератор.
#### Выполнение:
```python
numbers = [0, 1, 2, 3, 4, 5]
for item in numbers:
    print(item)
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/4016909c-295d-42ee-9e11-e019035a5102)
## Задание №2 Итератор с гибкой настройкой.
#### Выполнение:
```python
class CountDown:
    def __init__(self, start):
        self.count = start + 1

    def __iter__(self):
        return self

    def __next__(self):
        self.count -= 1
        if self.count < 0:
            raise StopIteration
        return self.count

if __name__ == '__main__':
    counter = CountDown(5)
    for i in counter:
        print(i)
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/13ba2c07-993e-435b-bf0c-38749e9a879e)
## Задание №3 Генератор списка.
#### Выполнение:
```python
a = [i ** 2 for i in range(1, 5)]

print('a - ', a)
for i in a:
    print(i)

print ('iter(a) - ', iter(a))
for i in a:
    print(i)
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/2024b0b5-154a-40a6-a363-abeadbeb7ea7)
## Задание №4 Выражение генераторы.
#### Выполнение:
```python
b = (i ** 2 for i in range(1, 5))
print(b)
print('first')
for i in b:
    print(i)
print('second')
for i in b:
    print(i)
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/1c836b54-174e-497f-82c8-76b777e5ed92)
## Задание №5 Счетчик с yield.
#### Выполнение:
```python
def countdown(count):
    while count >= 0:
        yield count
        count -= 1

if __name__ == '__main__':
    counter = countdown(5)
    for i in counter:
        print(i)
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/67d2197a-4d7f-4a94-8722-1d199d74600d)
## Самостоятельная работа 
## Задание №1 Числа Фибоначчи
#### Выполнение:
```python
def numfib(n):
    a, b = 1, 1
    for _ in range(n):
        yield a
        a, b = b, a + b

fibonacci_sequence = list(numfib(200))
print(fibonacci_sequence)
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/5d580e81-d82c-454d-b99f-4021d22ff8bf)
### Вывод: 
Числа Фибоначчи генерируется при помощи nubfib, функция yield - для возвращения чисел генератора. fibonacci_sequence - пример использования чисел. print - вывод наших чисел.
## Задание №2
```python
def numfib(n):
    a, b = 1, 1
    with open("fib.txt", "w") as file:
        for _ in range(n):
            file.write(f"{a}\n")
            yield a
            a, b = b, a + b

# Пример использвоания 200 чисел в файл
for number in numfib(200):
    pass  # Проход по числам,для их записи

print("Первые 10 чисел Фибоначчи:", list(numfib(10)))
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/8ff7891b-1f36-45b6-87e3-efd50823f0e6)
### Вывод: 
В коде есть небольшое описание новых строк. pass - пропуск чисел через генератор для последующей записи в файл. Цикл for number - Для прокрутки наших 200-ста чисел, которые есть в файле, часть из которых выпишется в консоль.
## Общий вывод: Декораторы - гибкий и мощный механизм,который позволяет изменять функции или методы в коде. Также улучшает читаемость кода, гибкость кода и т.д.
