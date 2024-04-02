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
import re

file = open('text.txt', 'r', encoding='utf-8-sig')
words = file.read().split()
stopwords = ['в', 'на', 'и', 'с', 'к', 'а','но', 'за', 'до', 'по', 'о']
print(f'Длина статьи: {len(words)} слов.')


def clean_text(words, stopwords):
    words = [re.sub(r'[,()."—:«»]', '', i) for i in words if i not in stopwords and len(i) > 1]
    return words


def find_most_wstr(words):
    words = clean_text(words, stopwords)
    num_freq = {}

    for word in words:
        num_freq[word] = num_freq.get(word, 0) + 1
    sorted_num_freq = sorted(num_freq.items(), key=lambda item: item[1])
    top = sorted_num_freq[-1]
    return top

res = find_most_wstr(words)
print(f'Самое встречающееся слово: "{res[0]}". Встречается {res[1]} раз.')

file.close()
```
### Результат:
![Меню](https://github.com/Dirtzzz/Tema_7/blob/main/7.1.png)
Текст в файле:
![Меню](https://github.com/Dirtzzz/Tema_7/blob/main/7.1(1).png)
