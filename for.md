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
