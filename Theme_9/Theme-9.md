# Тема 9. Концепции и принципы ООП.
### Отчет по Теме #9 выполнил:
- Козлов Максим Игоревич
- ПИЭ-21-2

| Задание | Лаб. раб. | Сам. раб. |
| ------ | ------ | ------ |
| Задание 1 |  | + |
| Задание 2 |  | + |
| Задание 3 |  | + |
| Задание 4 |  | + |
| Задание 5 |  | + |

Работу проверили:
- к.э.н., доцент Панов М.А.

## Самостоятельная работа №1
## Задание №1
### Задания для самостоятельного выполнения:
Задание Садовник и помидоры.
Классовая структура:
Есть Помидор со следующими характеристиками:
• Индекс
• Стадия созревания (стадии: отсутствует, цветение, зеленый, красный)
Помидор может:
• Расти (переходить на следующую стадию созревания)
• Предоставлять информацию о своей зрелости
Есть Куст с помидорами, который:
• Содержит список томатов, которые на нем растут
А также может:
• Расти вместе с томатами
• Предоставлять информацию о зрелости всех томатов
• Предоставлять урожай
И также есть Садовник, который имеет:
• Имя
• Растение, за которым он ухаживает
Он может:
• Ухаживать за растением
• Собирать с него урожай

Задание:
Класс Tomato:
1) Создайте класс Tomato
2) Создайте статическое свойство states, которое будет содержать все
стадии созревания помидора
3) Создайте метод __init__(), внутри которого будут определены два
динамических свойства: _index (передается параметром) и _state

(принимает первое значение из словаря states). После написания
этого блока кода в комментарии к нему укажите какими являются
эти два свойства
4) Создайте метод grow(), который будет переводить томат на
следующую стадию созревания
5) Создайте метод is_ripe(), который будет проверять, что томат созрел
Класс TomatoBush:
1) Создайте класс TomatoBush
2) Определите метод __init__(), который будет принимать в качестве
параметра количество томатов и на его основе будет создавать
список объектов класса Tomato. Данный список будет храниться
внутри динамического свойства tomatoes
3) Создайте метод grow_all(), который будет переводить все объекты
из списка томатов на следующий этап созревания
4) Создайте метод all_are_ripe(), который будет возвращать True, если
все томаты из списка стали спелыми.
5) Создайте метод give_away_all(), который будет чистить список
томатов после сбора урожая
Класс Gardener:
1) Создайте класс Gardener
2) Создайте метод __init__(), внутри которого будут определены два
динамических свойства: name (передается параметром, является
публичным) и _plant (принимает объект класса TomatoBush). После
написания этого блока кода в комментарии к нему укажите какими
являются эти два свойства
3) Создайте метод work(), который заставляет садовника работать, что
позволяет растению становиться более зрелым
4) Создайте метод harvest(), который проверяет, все ли плоды созрели.
Если все, то садовник собирает урожай. Если нет, то метод печатает
предупреждение
5) Создайте статический метод knowledge_base(), который выведет в
консоль справку по садоводству
Тесты:
1) Вызовите справку по садоводству
2) Создайте объекты классов TomatoBush и Gardener
3) Используя объект класса Gardener, поухаживайте за кустом с
помидорами
4) Попробуйте собрать урожай, когда томаты еще не дозрели.
Продолжайте ухаживать за ними
5) Соберите урожай
Результатом работы вашей программы будет листинг кода с подробными
комментариями и скриншоты выполенния всех тестов.

## Тест 1
#### Выполнение:
```python
class Tomato:
    states = {
        0: "отсутствует",
        1: "цветение",
        2: "зеленый",
        3: "красный"
    }

    def __init__(self, index):
        self._index = index
        self._state = 0

    def grow(self):
        if self._state < 3:
            self._state += 1

    def is_ripe(self):
        return self._state == 3


class TomatoBush:
    def __init__(self, num_tomatoes):
        self.tomatoes = [Tomato(index) for index in range(1, num_tomatoes + 1)]

    def grow_all(self):
        for tomato in self.tomatoes:
            tomato.grow()

    def all_are_ripe(self):
        return all(tomato.is_ripe() for tomato in self.tomatoes)

    def give_away_all(self):
        self.tomatoes = []


class Gardener:
    def __init__(self, name, plant):
        self.name = name
        self._plant = plant

    def work(self):
        self._plant.grow_all()

    def harvest(self):
        if self._plant.all_are_ripe():
            print("Сбор урожая...")
            self._plant.give_away_all()
        else:
            print("Помидоры не созрели. Продолжай выращивать.")

    @staticmethod
    def knowledge_base():
        print("База знаний садовода:")
        print("- Поливай растения регулярно.")
        print("- Нужно больше солнечнного света.")
        print("- ИСпользуй удобрение для улучшение почвы.")

Gardener.knowledge_base()
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/f1390e53-4c01-4f70-9a51-cb8c5122e3af)

## Тест 2
#### Выполнение:
```python
class Tomato:
    states = {
        0: "отсутствует",
        1: "цветение",
        2: "зеленый",
        3: "красный"
    }

    def __init__(self, index):
        self._index = index
        self._state = 0

    def grow(self):
        if self._state < 3:
            self._state += 1

    def is_ripe(self):
        return self._state == 3


class TomatoBush:
    def __init__(self, num_tomatoes):
        self.tomatoes = [Tomato(index) for index in range(1, num_tomatoes + 1)]

    def grow_all(self):
        for tomato in self.tomatoes:
            tomato.grow()

    def all_are_ripe(self):
        return all(tomato.is_ripe() for tomato in self.tomatoes)

    def give_away_all(self):
        self.tomatoes = []


class Gardener:
    def __init__(self, name, plant):
        self.name = name
        self._plant = plant

    def work(self):
        self._plant.grow_all()

    def harvest(self):
        if self._plant.all_are_ripe():
            print("Сбор урожая...")
            self._plant.give_away_all()
        else:
            print("Помидоры не созрели. Продолжай выращивать.")

    @staticmethod
    def knowledge_base():
        print("База знаний садовода:")
        print("- Поливай растения регулярно.")
        print("- Нужно больше солнечнного света.")
        print("- ИСпользуй удобрение для улучшение почвы.")

# Создаем объекты классов TomatoBush и Gardener
tomato_bush = TomatoBush(num_tomatoes=5)
gardener = Gardener(name="Max", plant=Potato_bush)
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/d733c39b-f07b-4fcf-aca8-1379e652089c)
## Тест 3
#### Выполнение:
```python

class Tomato:
    states = {
        0: "отсутствует",
        1: "цветение",
        2: "зеленый",
        3: "красный"
    }

    def __init__(self, index):
        self._index = index
        self._state = 0

    def grow(self):
        if self._state < 3:
            self._state += 1

    def is_ripe(self):
        return self._state == 3


class TomatoBush:
    def __init__(self, num_tomatoes):
        self.tomatoes = [Tomato(index) for index in range(1, num_tomatoes + 1)]

    def grow_all(self):
        for tomato in self.tomatoes:
            tomato.grow()

    def all_are_ripe(self):
        return all(tomato.is_ripe() for tomato in self.tomatoes)

    def give_away_all(self):
        self.tomatoes = []


class Gardener:
    def __init__(self, name, plant):
        self.name = name
        self._plant = plant

    def work(self):
        self._plant.grow_all()

    def harvest(self):
        if self._plant.all_are_ripe():
            print("Сбор урожая...")
            self._plant.give_away_all()
        else:
            print("Помидоры не созрели. Продолжай выращивать.")

    @staticmethod
    def knowledge_base():
        print("База знаний садовода:")
        print("- Поливай растения регулярно.")
        print("- Нужно больше солнечнного света.")
        print("- ИСпользуй удобрение для улучшение почвы.")

tomato_bush = TomatoBush(num_tomatoes=5)
gardener = Gardener(name="Max", plant=tomato_bush)

gardener.work()
gardener.work()
gardener.work()
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/4cf0fc3f-d0f7-472d-87fb-d744ff89bd5c)

## Тест 4
#### Выполнение:
```python

class Tomato:
    states = {
        0: "отсутствует",
        1: "цветение",
        2: "зеленый",
        3: "красный"
    }

    def __init__(self, index):
        self._index = index
        self._state = 0

    def grow(self):
        if self._state < 3:
            self._state += 1

    def is_ripe(self):
        return self._state == 3


class TomatoBush:
    def __init__(self, num_tomatoes):
        self.tomatoes = [Tomato(index) for index in range(1, num_tomatoes + 1)]

    def grow_all(self):
        for tomato in self.tomatoes:
            tomato.grow()

    def all_are_ripe(self):
        return all(tomato.is_ripe() for tomato in self.tomatoes)

    def give_away_all(self):
        self.tomatoes = []


class Gardener:
    def __init__(self, name, plant):
        self.name = name
        self._plant = plant

    def work(self):
        self._plant.grow_all()

    def harvest(self):
        if self._plant.all_are_ripe():
            print("Сбор урожая...")
            self._plant.give_away_all()
        else:
            print("Помидоры не созрели. Продолжай выращивать.")

    @staticmethod
    def knowledge_base():
        print("База знаний садовода:")
        print("- Поливай растения регулярно.")
        print("- Нужно больше солнечнного света.")
        print("- ИСпользуй удобрение для улучшение почвы.")

tomato_bush = TomatoBush(num_tomatoes=5)
gardener = Gardener(name="Max", plant=tomato_bush)
gardener.harvest()

gardener.work()
gardener.work()
gardener.work()

gardener.harvest()
```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/339e4099-9668-4a79-b3e9-ccfb635bb975)
## Тест 5
#### Выполнение:
```python
class Tomato:
    states = {
        0: "отсутствует",
        1: "цветение",
        2: "зеленый",
        3: "красный"
    }

    def __init__(self, index):
        self._index = index
        self._state = 0

    def grow(self):
        if self._state < 3:
            self._state += 1

    def is_ripe(self):
        return self._state == 3


class TomatoBush:
    def __init__(self, num_tomatoes):
        self.tomatoes = [Tomato(index) for index in range(1, num_tomatoes + 1)]

    def grow_all(self):
        for tomato in self.tomatoes:
            tomato.grow()

    def all_are_ripe(self):
        return all(tomato.is_ripe() for tomato in self.tomatoes)

    def give_away_all(self):
        self.tomatoes = []


class Gardener:
    def __init__(self, name, plant):
        self.name = name
        self._plant = plant

    def work(self):
        self._plant.grow_all()

    def harvest(self):
        if self._plant.all_are_ripe():
            print("Сбор урожая...")
            self._plant.give_away_all()
        else:
            print("Помидоры не созрели. Продолжай выращивать.")

    @staticmethod
    def knowledge_base():
        print("База знаний садовода:")
        print("- Поливай растения регулярно.")
        print("- Нужно больше солнечнного света.")
        print("- ИСпользуй удобрение для улучшение почвы.")

tomato_bush = TomatoBush(num_tomatoes=5)
gardener = Gardener(name="Max", plant=tomato_bush)
gardener.harvest()

gardener.work()
gardener.work()
gardener.work()

gardener.harvest()

gardener.harvest()

print("\nВсе помидоры созрели?", gardener._plant.all_are_ripe())

for i, tomato in enumerate(gardener._plant.tomatoes, 1):
    print(f"Tomato {i}: State - {Tomato.states[tomato._state]}, Ripe - {tomato.is_ripe()}")

```
#### Результат:
![image](https://github.com/CauseLove7/Program-Engineering/assets/145790904/6aef291d-e8dc-403e-8b8a-e73f8fe7d9a6)

### Вывод: В конечном итоге нашего кода мы получили некую программку, можно даже назвать игру! Сбор урожая! Единственная незавершенность у нас получилось в конце, что не выводиться что все томаты собраны. А так в данном коде создается классы Tomato,TomatoBush,Gardener.

## Общий вывод: 
Благодаря ООП в том числе и на Python, мы можем создавать и писать удивительные вещи, игры,программы, боты и прочее. ООП - является основопологающей в программировании в Python. 
