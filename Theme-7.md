# Тема 7. Работа с файлами (ввод, вывод)
### Отчет по Теме #7 выполнил:
- Козлов Максим Игоревич
- ПИЭ-21-2

| Задание | Сам. раб. |
| ------ | ------ |
| Задание 1 | + |
| Задание 2 | + |
| Задание 3 | + |
| Задание 4 | + |
| Задание 5 | + |

Работу проверили:
- к.э.н., доцент Панов М.А.

## Самостоятельная работа №7
## Задание №1
### Статья.
#### Выполнение:
```python
from collections import Counter
import re

def count_words(text):

    words = re.findall(r'\b\w+\b', text.lower())

    word_counts = Counter(words)

    most_common_word, count = word_counts.most_common(1)[0]

    return most_common_word, count

if __name__ == "__main__":
    file_path = "A:\Program-Engineering\lab7/Test.txt"

    try:
        with open(file_path, 'r', encoding='utf-8') as file:
            text = file.read()

        most_common_word, count = count_words(text)

        print(f"Самое популярное слово: {most_common_word}")
        print(f"Количество использований: {count}")

    except FileNotFoundError:
        print(f"Файл по пути '{file_path}' не найден.")
    except Exception as e:
        print(f"Произошла ошибка: {e}")
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/85f10434-f1f3-4793-8673-d27c3e846e12)
#### Вывод: 
Как мы видим, при открытии файла, программа просматривает ваш код и выводит самое популярное слово(и не только). Также, важное примечание!!!! Если в вашем файле ничего не будет, то есть файл будет пустой, данная программа выдаст данный результат.
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/acde61bf-26c6-4dd2-8df5-9c7ec45c56fb)
## Задание №2
### Книга расходов.
#### Выполнение:
```python
import json
import os

def load_expenses():
    test_file = 'test.txt'
    if os.path.exists(test_file):
        with open(test_file, 'r') as file:
           test = json.load(file)
    else:
        test = []
    return test

def save_expenses(expenses):
    test_file = 'test.txt'
    with open(test_file, 'w') as file:
        json.dump(expenses, file, indent=2)

def add_expense(expenses, category, amount):
    expense = {'category': category, 'amount': amount}
    expenses.append(expense)
    save_expenses(expenses)
    print(f"Расход в размере {amount} добавлен в категорию {category}.")

def display_expenses(expenses):
    if not expenses:
        print("Нет сохраненных расходов.")
    else:
        print("Существующие расходы:")
        for expense in expenses:
            print(f"Категория: {expense['category']}, Сумма: {expense['amount']}")

if __name__ == "__main__":
    expenses = load_expenses()

    while True:
        print("\nВыберите действие:")
        print("1. Ввести новый расход")
        print("2. Просмотреть существующие расходы")
        print("3. Выйти")

        choice = input("Введите номер действия: ")

        if choice == '1':
            category = input("Введите категорию расхода: ")
            amount = float(input("Введите сумму расхода: "))
            add_expense(expenses, category, amount)
        elif choice == '2':
            display_expenses(expenses)
        elif choice == '3':
            print("Программа завершена.")
            break
        else:
            print("Некорректный выбор. Пожалуйста, выберите 1, 2 или 3.")
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/82e2a2d4-c8ff-491f-8fac-dbd39f2f2f16)
#### Вывод: 
Данная программа позволяет упростить введение книги учета, с добавлением нового файла, но в самом коде(консоли ничего сохранятся не будет, поэтому мы создаем отдельный файл) Пример сохраненного файла. Название файла вы придумываете сами в моем случае это test.txt
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/ecaedfce-6761-42ed-969a-e654d5424e0d)
## Задание №3
### Статистика по тексту.
#### Выполнение:
```python
def calculate_statistics(file_path):
    with open(file_path, 'r', encoding='utf-8') as file:
        text = file.read()

    latin_letters_count = sum(1 for char in text if char.isalpha() and char.isascii())

    words_count = len(text.split())

    lines_count = text.count('\n') + 1

    return latin_letters_count, words_count, lines_count

if __name__ == "__main__":
    file_path = 'C:/Users\Saharok\Program-Engineering\Lab7\Test2.txt'

    try:
        latin_letters_count, words_count, lines_count = calculate_statistics(file_path)
        print(f"Количество букв латинского алфавита: {latin_letters_count}")
        print(f"Количество слов: {words_count}")
        print(f"Количество строк: {lines_count}")
    except FileNotFoundError:
        print(f"Файл '{file_path}' не найден.")
    except Exception as e:
        print(f"Произошла ошибка: {e}")
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/57173993-fe6e-4118-96d9-d801c325f920)
#### Вывод: 
В данной программе можем проанализировать данные,которые мы вставили в файл. Программа считывает символы,которые есть внутри файла. Важное примечание для правильной работы программы стоит обратить внимание на строку  "file_path = 'C:/Users\Saharok\Program-Engineering\Lab7\Test2.txt'" - строка пути к файлу. В моем случае корневая папка Users - программой не читалась, поэтому стоило обратить на это внимание!
Пример файла: 
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/e43ebe61-f0b5-4a54-a414-70ec9bbf0820)
## Задание №4 
### Запрещенные слова.
#### Выполнение:
```python
if __name__ == "__main__":
    import re

    def load_censor_words(file_path):
        with open(file_path, 'r', encoding='utf-8') as file:
            censor_words = [word.strip().lower() for word in file.readlines()]
        return censor_words

    def censor_text(text, forbidden_words):
        for word in forbidden_words:

            text = re.sub(rf'\b{re.escape(word)}\b', '*' * len(word), text, flags=re.IGNORECASE)
        return text


    if __name__ == "__main__":
        forbidden_words = load_censor_words('C:/Users\Saharok\Program-Engineering\Lab7\input.txt') 
        sentence = input("Введите предложение: ")

        censored_sentence = censor_text(sentence, forbidden_words)

        print("Исходное предложение:", sentence)
        print("Предложение с замененными запрещенными словами:", censored_sentence)
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/8b86b860-caa7-4d47-966c-efeba147cfbf)
#### Вывод: 
В своем созданном файле помещаем запрещенное слово,которое программа должна будет вывести в консоли в состоянии ****. Прмиер файла:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/4ab26416-36cf-4708-982b-9f2c70ad2030)
## Задание №5
### Своя задача
#### Выполнение:
```python
from collections import Counter

def analyze_logs(file_path):
    try:
        with open(file_path, 'r', encoding='utf-8') as file:
            logs = file.readlines()

        events = [log.split('-')[-1].strip() for log in logs]

        event_counts = Counter(events)

        return event_counts

    except FileNotFoundError:
        return None

if __name__ == "__main__":
    file_path = 'C:/Users\Saharok\Program-Engineering\Lab7\log.txt'

    result = analyze_logs(file_path)

    if result:
        print("Статистика событий в логах:")
        for event, count in result.items():
            print(f"{event}: {count} раз")
    else:
        print(f"Файл '{file_path}' не найден.")
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/dcbc44b4-1513-4537-af56-9f6dabf5eb7f)
#### Вывод: 
С помощью данной программы мы можем отсматривать своих сотрудников/клиентов, сколько раз человек заходил в сеть. Если в файле не будет никакой информации будет данный ответ в консоли
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/36ca417d-78a5-401c-b72e-d491766c4d2d)
Пример файла:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/e2fd8070-4b53-41ba-9066-e1f1b4730567)

## Общий вывод: В данной теме я изучил важные темы в изучении языка Python. Создание и работа с файлами. Очень нужная тема для создания игр, ботов или прочего. Изучение работы с файлами позволило мне создать программы, способные читать и записывать текстовые данные.
