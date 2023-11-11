![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/ed9731b5-a9f7-46b7-ae1d-d82ddc3021c9)# Тема 6. Базовые коллекции: словари, кортежи.
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
### Вовочка крутой программист
#### Выполнение:
```python
def personal_info(name,age,company = 'unnamed'):
    print(f"Имя: {name} Возраст:{age} Компания:{company}")

tom = ("Григорий", 22)
personal_info(*tom)

bob = ("Виталий", 18, "Yandex")
personal_info(*bob)
```
#### Результат
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/fc7b4381-796f-47f5-b512-3e3148129987)
## Задание №5
### Сопровождение президента
#### Выполнение:
```python
def tuple_sort(tpl):
    for elm in tpl:
        if not isinstance(elm ,int):
            return tpl
    return tuple(sorted(tpl))

if __name__ == '__main__':
    print(tuple_sort((5,5,3,1,9)))
    print(tuple_sort((5,5,2.1,'1',9)))
```
#### Результат
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/e8d9166c-778c-48a1-bb53-2f795ab7cf38)
## Самостоятельная работа №1
## Задание №1
### Удобная последовательность чисел.
#### Выполнение:
```python
user_input_string = input("Введите последовательность ")

numbers_result = [int(num) for num in user_input_string]

result = tuple(numbers_result)

print("Список:", numbers_result)
print("Кортеж:", list(result))
```
#### Результат
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/8ed9db0d-7479-4929-8501-fd65564c4774)
#### Вывод:
Благодаря нашему переводу чисел в последовательность мы можем сразу упростить и ускорить работу последующих программ, например выставление чисел в порядках убывания и возрастаний, если такая работа потребуется. Также стоить отметить, что благодаря кортежу и списку можно отчетливо наблоюдать каждый символ введеный пользователем(это нам ничего не дает, просто удобнее и приятнее глазу).
## Задание №2
### Николай и его удаление.
#### Выполнение:
```python
def tuple_sort(tpl, elm):
    if elm in tpl:
        index = tpl.index(elm)
        new_tpl = tpl[:index] + tpl[index + 1:]
        return new_tpl
    else:
        return tpl
tuple1 = (1, 2, 3)
result1 = tuple_sort(tuple1, 1)
print(result1)

tuple2 = (1, 2, 3, 1, 2, 3, 4, 5, 2, 3, 4, 2, 4, 2)
result2 = tuple_sort(tuple2, 3)
print(result2)

tuple3 = (2, 4, 6, 6, 4, 2)
result3 = tuple_sort(tuple3, 9)
print(result3)
```
#### Результат
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/8f0eba27-a516-4f8b-bbc4-ca68ee7aab9e)
#### Вывод:
В данной задаче нам представлены 3 ввида ввода данных, и чтобы вывести правильный ответ, понадобилось 3 раза применить кортеж, который мы можем наблюдать в моем коде. В каждом блоке мы сортируем числа, которые нам нужны по задаче.
## Задание №3
### Numpad.
#### Выполнение:
```python
def common_numbers(digits_string):
    digit_count = {}

    for digit in digits_string:
        digit = int(digit)
        digit_count[digit] = digit_count.get(digit, 0) + 1

    most_common_numbers = sorted(digit_count.items(), key=lambda x: x[1], reverse=True)[:3]


    result_dict = dict(most_common_numbers)

    return result_dict

random_digits = "3266350645789476567406450784"
result = common_numbers(random_digits)

print("Самые часто встречаемые числа:")
for key in sorted(result.keys()):
    print(f"{key}: {result[key]}")
```
#### Результат
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/f8eead2f-2226-4018-ba73-3dd21ae074cc)
#### Вывод:
Для обозначения часто встречающихся чисел, мне понадобилось применить словарь в котором я и отбирал часто встречающиеся числа, пример которого можно увидеть в моем коде.
## Задание №4
### Друг и его офис.
#### Выполнение:
```python
def tuple_index(log_tuple, employee_id):
    first_occurrence = log_tuple.index(employee_id) if employee_id in log_tuple else -1
    second_occurrence = log_tuple[first_occurrence + 1:].index(employee_id) + first_occurrence + 1 \
        if first_occurrence != -1 and employee_id in log_tuple[first_occurrence + 1:] \
        else -1

    if first_occurrence == -1 or second_occurrence == -1:
        return ()

    if first_occurrence == second_occurrence:
        return log_tuple[first_occurrence:]

    return log_tuple[first_occurrence:second_occurrence + 1] if second_occurrence != -1 else log_tuple[first_occurrence:]

tpl1 = (1, 2, 3)
result1 = tuple_index(tpl1, 8)
print(result1)

tpl2 = (1, 8, 3, 4, 8, 8, 9, 2)
result2 = tuple_index(tpl2, 8)
print(result2)

tpl3 = (1, 2, 8, 5, 1, 2, 9)
result3 = tuple_index(tpl3, 8)
print(result3)
```
#### Результат
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/8c4ec607-77f6-4f43-a407-50187424e36d)
#### Вывод:
Трудная задача, которая содержала в себе подводные камни, были ошибки в коде при считывании индексов первого и второго элемента и при их выводе. Ошибка была исправлена и результат мы можем увидеть. 
## Задание №5
### Поиск и преобразования для удаления дубликатов.
#### Выполнение:
```python
def tuple_duplicates(input_list):
    tuple_list = list(set(input_list))
    return tuple_list

test_tuple_list1 = [1, 8, 2, 2, 7, 3, 4, 4, 8]
result1 = tuple_duplicates(test_tuple_list1)
print(result1)

test_tuple_list2 = [10, 20, 10, 30, 70, 20, 40, 50, 40]
result2 = tuple_duplicates(test_tuple_list2)
print(result2)

test_tuple_list3 = [2, 8, 14, 4, 6, 8, 10, 12, 14]
result3 = tuple_duplicates(test_tuple_list3)
print(result3)
```
#### Результат
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/f16c69e3-d381-4c3d-8c2b-1e31bf7c1f03)
#### Вывод:
Простая задача для удаления из кортежей дублированных чисел. Упрощение задачи, для сокращения ненужных данных. Простота = удобство.
## Общий вывод:
Кортежи и списки. Удобные функиции в Python, благодаря которым мы можем упростить не просто вид чисел, которые мы вводим, но и упрощаем работу в будущем, которая может возникнуть перед нами. Наглядно я показывал в своих задачах в этой работе.
