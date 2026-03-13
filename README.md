# Лабораторные работы по Python

Репозиторий студента Jetac1451  
Дисциплина: Технология программирования (или аналогичная)

## Описание проектов

Здесь лежат две лабораторные работы, связанные с побитовой обработкой двоичных строк (8 бит).

### Лабораторная 2  
**Файл:** `2labatech.sln`

Простая версия программы без функций:  
- Вводит две двоичные строки с клавиатуры  
- Проверяет корректность (только 0 и 1, не длиннее 8 символов)  
- Дополняет ведущими нулями до 8 бит  
- Выполняет побитовую конъюнкцию (логическое И)  
- Выводит результат

```python
bs1 = input('Input bs 1: ')
if len(bs1) > 8:
    print("Incorrect input")
    exit()
for b in bs1:
    if b != "0" and b != "1":
        print("Incorrect input")
        exit()
d = 8 - len(bs1)
suffix = "0" * d
bs1 = suffix + bs1

bs2 = input('Input bs 2: ')
if len(bs2) > 8:
    print("Incorrect input")
    exit()
for b in bs2:
    if b != "0" and b != "1":
        print("Incorrect input")
        exit()
d = 8 - len(bs2)
suffix = "0" * d
bs2 = suffix + bs2

bs3 = ""
i = 0
while i < 8:
    if bs1[i] == "1" and bs2[i] == "1":
        bs3 += "1"
    else:
        bs3 += "0"
    i += 1

print("Result=", bs3)
