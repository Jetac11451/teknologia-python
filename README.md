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
```
### Лабораторная 4
**Файл:** 4laba.sln
Улучшенная, структурированная версия программы:

Использует функции
Читает первую строку из файла a.txt
Вводит вторую строку с клавиатуры
Проверяет корректность через функцию normalize_bits
Выполняет побитовое И (конъюнкцию)
Выводит результаты на экран и сохраняет в файл result.txt
```
import sys

def normalize_bits(s):
    if len(s) > 8 or not all(c in '01' for c in s):
        print("Incorrect input")
        sys.exit(0)
    return '0' * (8 - len(s)) + s

def input_bits():
    s = input("Input bs 2: ")
    s = normalize_bits(s)
    return list(s)

def file_input_bits(filename):
    try:
        with open(filename, 'r') as f:
            s = f.read().strip()
    except FileNotFoundError:
        print("File not found")
        sys.exit(0)
    s = normalize_bits(s)
    return list(s)

def output_bits(bits):
    print("Stroka =", ''.join(bits))

def file_output_bits(filename, bits):
    with open(filename, 'w') as f:
        f.write("Stroka = " + ''.join(bits))

def conjaction(bits1, bits2):
    return ['1' if b1 == '1' and b2 == '1' else '0' for b1, b2 in zip(bits1, bits2)]

def main():
    bs1 = file_input_bits("a.txt")
    bs2 = input_bits()
    print("BS 1:", end=' ')
    output_bits(bs1)
    print()
    print("BS 2:", end=' ')
    output_bits(bs2)
    print()
    res = conjaction(bs1, bs2)
    print("Result:", end=' ')
    output_bits(res)
    file_output_bits("result.txt", res)

if __name__ == "__main__":
    main()
    input("Press Enter to continue...")
```

print("Result=", bs3)
