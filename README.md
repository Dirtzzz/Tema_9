# Тема 9. Базовые операции языка Python
Отчет по Теме #9 выполнил:
- Ильдейкин Антон Александрович
- ИНО ЗБ ПОАС-22-2

| Задание | Лаб_раб | Сам_раб |
| ------ | ------ | ------ |
| Задание 1 | - | + |


Работу проверили:
- к.э.н., доцент Панов М.А.
## Самостоятельная работа №1
### Задание Садовник и помидоры.
1) Вызовите справку по садоводству
2) Создайте объекты классов TomatoBush и Gardener
3) Используя объект класса Gardener, поухаживайте за кустом с помидорами
4) Попробуйте собрать урожай, когда томаты еще не дозрели. Продолжайте ухаживать за ними
5) Соберите урожай
Результатом работы вашей программы будет листинг кода с подробными комментариями и скриншоты выполенния всех тестов.

```python
class Tomato: # Создаем класс томатов
    states = ['отсутствует', 'цветение', 'зеленый', 'красный'] # Варианты развития

    # Установка начального состояния роста
    def __init__(self, index):
        self._index = index
        self._state = Tomato.states[0]

    # Перевод томата на следующую стандию созревания
    def grow(self):
        self._state = Tomato.states[(Tomato.states.index(self._state) + 1) % len(Tomato.states)]

    def is_ripe(self):
        return self._state == 'красный' #Созрел

class TomatoBush:
    # количество всех томатов
    def __init__(self, num_tomatoes):
        self.tomatoes = [Tomato(i) for i in range(num_tomatoes)]

    # Рост томатов на кусте
    def grow_all(self):
        for tomato in self.tomatoes:
            tomato.grow()

    # Проверка созрел или не созрел
    def all_are_ripe(self):
        return all(tomato.is_ripe() for tomato in self.tomatoes)

    # сбор с куста
    def give_away_all(self):
        self.tomatoes = []

 # создаем клас садовника, который проводит манипуляции с растением
class Gardener:
    # Определение свойств
    def __init__(self, name, plant):
        self.name = name
        self._plant = plant

    # Уход за садом
    def work(self):
        self._plant.grow_all()
        print(f'{self.name} Позаботился о растении.')

    # Проверка зрелости и сбор урожая, если томаты созрели
    def harvest(self):
        if self._plant.all_are_ripe():
            print(f'Томаты красные. {self.name} собрал урожай.')
            self._plant.give_away_all()
        else:
            print('Томаты ещё не красные')

    # справка
    @staticmethod
    def knowledge_base():
        print('Справка по садоводству')

# Вызов справки по садоводству
Gardener.knowledge_base()

tomato_bush = TomatoBush(int(input('Сколько томатов на кусте?: ')))  # Создание объектов классов TomatoBush
gardener = Gardener(input('Введите имя: '), tomato_bush) # Создание объектов классов Садовника

# цикл с условием, зависящим от состояния урожая
while len(tomato_bush.tomatoes) != 0:
    action = int(input('Выберите действие: 1 - позаботиться о саде; 2 - Попробовать собрать урожай: '))
    if action == 1:
        gardener.work()  # Уход за кустом
    elif action == 2:
        gardener.harvest()  # Сбор урожая
        print()
    else:
        print('Ошибка')
```
### Результат:
![Меню](https://github.com/Dirtzzz/Tema_9/blob/main/9.1.png)
Полный вывод с консоли:
![Меню](https://github.com/Dirtzzz/Tema_9/blob/main/9.1(1).png)
