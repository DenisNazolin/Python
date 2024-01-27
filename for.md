### Задача 1

### Задание 1: Запросить у пользователя ввод IP-адреса в формате 10.0.1.1. Ввод данных
### осуществляется в виде строки. В зависимости от типа адреса (описаны ниже), вывести на
### стандартный поток вывода:


### Задание 2: Сделать копию скрипта задания 1 Добавить проверку введенного IP-адреса.
### Адрес считается корректно заданным, если он:

```
ip_address = input("Введите IP-адрес: ")

# Проверка корректности введенного IP-адреса
ip_parts = ip_address.split('.')
if len(ip_parts) != 4:
    print("Неправильный IP-адрес")
else:
    correct_format = True
    for part in ip_parts:
        if not part.isdigit() or not 0 <= int(part) <= 255:
            correct_format = False
            break
    if not correct_format:
        print("Неправильный IP-адрес")
    else:
        first_byte = int(ip_parts[0])
        if ip_address == '255.255.255.255':
            print("local broadcast")
        elif ip_address == '0.0.0.0':
            print("unassigned")
        elif 1 <= first_byte <= 223:
            print("unicast")
        elif 224 <= first_byte <= 239:
            print("multicast")
        else:
            print("Неправильный IP-адрес")
```

### Задание 3: 

```

trunk_template = [
    "switchport trunk encapsulation dot1q",
    "switchport mode trunk",
    "switchport trunk allowed vlan",
]

trunk = {
    "0/1": ["add", "10", "20"],
    "0/2": ["only", "11", "30"],
    "0/4": ["del", "17"]
}

for intf, vlans in trunk.items():
    print("interface FastEthernet " + intf)
    for command in trunk_template:
        if command.endswith("allowed vlan"):
            if vlans[0] == "add":
                print(f" {command} add {','.join(vlans[1:])}")
            elif vlans[0] == "del":
                print(f" {command} remove {','.join(vlans[1:])}")
            elif vlans[0] == "only":
                print(f" {command} {','.join(vlans[1:])}")
        else:
            print(f" {command}")

```

###  Задание 4: Написать программу – игра - угадай, в которой с помощью функции random
### генерируется случайное число от 1 до 50 Пользователю предлагается угадать данное
###  число, на основе подсказать – загаданное число больше или меньше числа пользователя.
### Вывести число попыток отгадывания числа

```
import random
a=random.randint(1,50)
count = 0
flag = 0

while flag == 0:
    b = int(input("введите число",))
    if a == b:
        flag =1
        count = count+1
    elif a > b:
        print("число больше")
        count = count + 1
    elif b > a:
        print("число меньше")
        count = count + 1
print("колличество попыток ", count )

```

