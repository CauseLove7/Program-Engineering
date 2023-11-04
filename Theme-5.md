# Тема 5. Базовые коллекции:множества,списки
### Отчет по Теме #5 выполнил:
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
### Найди отличия и убери повторения
#### Выполнение:
```python
1.set_1 = {'White,Red,Black,Pink'}
  set_2 = {'Red,Green,Black,Blue/'}

print(set_1 - set_2)
```
#### Результат:
1.![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/766d4b4c-7e70-4356-9950-489b0507bc2b)

2. С Разными повторениями
``` python
set_1 = {'White,Red,Black,Pink'}
set_2 = {'Red,Green,Black,Blue'}

print("1",set_1 - set_2)

set_1 = {'White,Red,Black,Pink,Purple,Green'}
set_2 = {'Red,Green,Black,Blue'}
print("2",set_1 - set_2)

set_1 = {'White,Red,Black,Pink,Green,Red,Red'}
set_2 = {'Red,Green,Black,Blue,Red,Red'}
print("3",set_1 - set_2)
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/a693847e-c3d6-4dc1-8ece-40293af58c42)

## Задание №2
### Напишите две одинаковые программы, только одна будет использовать set(), а вторая frozenset() и попробуйте к исходному множеству добавить несколько элементов,например через цикл:
#### Выполнение:
1.SET()
``` python
a = set('abfrgejbe')
print(a)
for i in range(1,5):
    a.add(i)
print(a)
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/1ed9d3b3-be2c-4a1b-83e4-2a0eabd24dcf)

2.FROZENSET()
``` python
a = frozenset('abfrgejbe')
print(a)
for i in range(1,5):
    a.add(i)
print(a)
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/6b066c6a-04f3-445a-b670-4ca84a14c29b)

## Задание №3
### На вход в программу поступает список(минимальной длиной 2 символа). Напишите программу,которая будет менять первый и последний элемент списка.
#### Выполнение:
``` python
def replace(input_list):
    memory = input_list[0]
    input_list[0] = input_list[-1]
    input_list[-1] = memory
    
    return input_list

print(replace([1,2,3,4,5]))
```
#### Результат:

![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/96491d0c-8df0-4393-8de5-c2433c87bffe)

## Задание №4
### На вход в программу поступает список(минимальной длиной 10 символа). Напишите программу,которая выводит элементы с индексами от 2 до 6. В программе необходимо использовать "срез".
#### Выполнение:
``` python
a = [12,54,32,57,843,1356,65,342,87,23,42]
print(a[2:6])
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/45f8f27d-6989-4490-a08d-3cb085fbc444)

## Задание №5
### Бесполезное число
#### Выполнение:
``` python
def useless(lst):
    return max(lst) / len(lst)

print(useless([3,5,7,3,33]))
print(useless([-12.5,33,77.3,-36,98.2,-63,21.7,47]))
print(useless([-25.8,86,12.5,3,73.2],0,43,-91.5))
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/1e8f3d8b-7666-45ce-8905-b47867e72c9e)

## Задание №6
### Супергерои
#### Выполнение:
``` python
superheroes = ['superman','spiderman','batman']
nikolay,vasiliy, ivan = superheroes

print("Николай - ", nikolay)
print("Василий - ", vasiliy)
print("Иван - ", ivan)
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/d3eb923f-b7b3-49a0-b616-7a64f08a1789)

## Задание №7
### Слабое звено
#### Выполнение:
``` python
a = [-25.8,86,12.5,-56,73.2,0,43,-91.5,65.9,-7]
a.sort()
print('Отсортированный список:\n', a)
a.pop(0)
print('Отсортированный список без наименьшего элемента:\n', a)
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/632a3673-3603-48c5-82bd-7b6099ee6f8f)
## Задание №8
### N-мерный список
#### Выполнение:
``` python
from random import randint

def list_maker():
    a = [randint(1,100)] * randint(3,100)
    return a

if __name__ == '__main__':
    result = []
    for i in range (randint(1,5)):
        result.append(list_maker())
        
    print (result)
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/24702374-365e-480f-8a58-bc74eb30a5c0)

## Задание №9
### Ресторан
#### Выполнение:
``` python
def superset(set_1,set_2):
    if set_1 > set_2:
        print(f'Обьект {set_1} является числом множественным')
    elif set_1 == set_2:
        print(f'Множества равны')
    elif set_1 < set_2:
        print(f'Обьект {set_2} является чистым супермножеством')
    else:
        print('Супермножество не обнаружено')
        

if __name__ == '__maim__':
    superset({1,8,3,5},{3,5})
    superset({1,8,3,5},{5,3,8,1})
    superset({3,5},{5,3,8,1})
    superset({90,100},{3,5})
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/95ffd957-f1da-4477-8df0-e14d23061dfb)

## Задание №10
### Стопка бумаг
#### Выполнение:
``` python
my_list = [2,5,8,3]
print(my_list[::-1])
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/08c86d7b-2461-43ac-a0c9-0b5f7cb13b38)


## Самостоятельная работа №1
## Задание №1
### Посещения работников
#### Выполнение:
```python
checks = [8734, 2345, 8201, 6621, 9999, 1234, 5678, 8201, 8888, 4321, 3365,
          1478, 9865, 5555, 7777, 9998, 1111, 2222, 3333, 4444, 5556, 6666,
          5410, 7778, 8889, 4445, 1439, 9604, 8201, 3365, 7502, 3016, 4928,
          5837, 8201, 2643, 5017, 9682, 8530, 3250, 7193, 9051, 4506, 1987,
          3365, 5410, 7168, 7777, 9865, 5678, 8201, 4445, 3016, 4506, 4506]

total_checks = len(checks)

humans = len(set(checks))

# Создаем словарь для подсчета посещений каждого работника
worker_count = {}
for worker in checks:
    if worker in worker_count:
        worker_count[worker] += 1
    else:
        worker_count[worker] = 1

most_frequent_worker = max(worker_count, key=worker_count.get)
visits_by_most_worker = worker_count[most_frequent_worker]

# Выводим результаты
print(f"Сколько было выдано чеков: {total_checks}")
print(f"Сколько разных людей посетило ресторан: {humans}")
print(f"Работник, посетивший ресторан больше всех раз, код: {most_frequent_worker}, количество посещений: {visits_by_most_worker}")
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/308213da-9c6c-4177-9305-62156ae06be1)
#### Вывод: Данная программа позволяет упростить ведения учета по приходу сотрудников. Программа выполнена с помощью листинга, который и позволяет сделать этот код максимально удобным и коротким.
## Задание №2
###
#### Выполнение:
```python
results = [10.2, 14.8, 19.3, 22.7, 12.5, 33.1, 38.9, 21.6, 26.4, 17.1, 30.2, 35.7, 16.9,
           27.8, 24.5, 16.3, 18.7, 31.9, 12.9, 37.4]

best_results = sorted(results)[:3]
print("Три лучших результата:", best_results)
worst_results = sorted(results)[-3:]
print("Три худших результата:", worst_results)
results_10 = [result for result in results if result >= 10]
print("Все результаты начиная с 10:", results_10)
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/1c2a54fc-90ec-4a4b-b6c0-72e4aa1c57e7)
#### Вывод: С помощью данного кода можно ускорить введение учительского журнаала и быстрее проставить результаты. Достигается данное упрощение с помощью сортировки и выбора нужных нам данных из массива.
## Задание №3
###
#### Выполнение:
```python
one = [12, 25, 3, 48, 71]
two = [5, 18, 40, 62, 98]
three = [4, 21, 37, 56, 84]

one_max = max(one)
one_min = min(one)

two_max = max(two)
two_min = min(two)

three_max = max(three)
three_min = min(three)

def calculate_triangle(a, b, c):
    s = (a + b + c) / 2
    area = (s * (s - a) * (s - b) * (s - c)) ** 0.5
    return area

first_max_min = calculate_triangle(one_max, two_min, three_min)
second_max_min = calculate_triangle(one_min, two_max, three_max)

print("Площадь треугольника, составленного из максимальных и минимальных элементов списков:")
print("Первый треугольник:", first_max_min)
print("Второй треугольник:", second_max_min)
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/22128f30-0476-4861-bc21-52ea1464b59b)
#### Вывод: Самое трудное в данной задаче было правильно посчитать формулы, которые нам нужны. Данный код может упростить решение тяжелых задач с правильным выводом ответа.
## Задание №4
###
#### Выполнение:
```python
def process_grades(grades):

    grades = [grade for grade in grades if grade != 2]
   
    grades = [4 if grade == 3 else grade for grade in grades]
    return grades

grades1 = [2, 3, 4, 5, 3, 4, 5, 2, 2, 5, 3, 4, 3, 5, 4]
grades2 = [4, 2, 3, 5, 3, 5, 4, 2, 2, 5, 4, 3, 5, 3, 4]
grades3 = [5, 4, 3, 3, 4, 3, 3, 5, 5, 3, 3, 3, 3, 4, 4]

updated_grades1 = process_grades(grades1)
updated_grades2 = process_grades(grades2)
updated_grades3 = process_grades(grades3)

print("Обновленный список оценок 1:", updated_grades1)
print("Обновленный список оценок 2:", updated_grades2)
print("Обновленный список оценок 3:", updated_grades3)
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/338c6cce-0e06-45d6-ac52-8180082f12d0)
#### Вывод: Крайне тяжелая задача, в которой пришлось использовать функции, с помощью которых и получилось решить данную задачу.
## Задание №5
###
#### Выполнение:
```python
def transform_and_create_sets(input_list):
    result_set = set()
    num_counts = {}

    for num in input_list:
        num_str = str(num)
        count = num_counts.get(num, 0)

        while num_str in result_set:
            count += 1
            num_str += str(num)

        num_counts[num] = count
        result_set.add(num_str)

    return result_set

list_1 = [1, 1, 3, 3, 1]
list_2 = [5, 5, 5, 5, 5, 5, 5]
list_3 = [2, 2, 1, 2, 2, 5, 6, 7, 1, 3, 2, 2]

set_1 = transform_and_create_sets(list_1)
set_2 = transform_and_create_sets(list_2)
set_3 = transform_and_create_sets(list_3)

print(set_1)
print(set_2)
print(set_3)
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/e97ec98f-aafb-45ba-a69e-0b6241f8529a)
#### Вывод: Самая трудная задача с множеством циклов и массивов, в данной задаче также как и предыдущих ипользовались функции, которые и помогают нам в решении такхи задач.
## Общий вывод: Базовые коллекции на питоне — списки и множества — играют особую роль в хранении данных. Лист предлагает упорядочивание элементов, которое может дублировать контент и позволяет выполнять различные операции над элементами.
