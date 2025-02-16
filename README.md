# Работа с git и bash

Все команды выполнены в терминале Ubuntu 

Работа с файлами и папками в bash: 
---
```python
anastasia@MY-PC:~$ cd                                  # Открыть домашнюю директорию через терминал
anastasia@MY-PC:~$ pwd                                 # Определить имя папки, в которой вы находитесь
    /home/anastasia
anastasia@MY-PC:~$ mkdir test1                         # Создать внутри этой папки каталог с именем test1
anastasia@MY-PC:~$ cd test1                            # Перейти в папку test1
anastasia@MY-PC:~/test1$ touch 1.txt 2.txt 3.txt       # Создать файл 1,2 и 3 внутри каталога test1
anastasia@MY-PC:~/test1$ ls                            # Проверить содержимое каталога test1
    1.txt  2.txt  3.txt                                    

anastasia@MY-PC:~/test1$ cd                            # Перейти в домашнюю директорию (любой из вариантов)
anastasia@MY-PC:~$ cd test1
anastasia@MY-PC:~/test1$ cd ..                         

anastasia@MY-PC:~$ mkdir test2                         # Создать папку test2 внутри домашней директории
anastasia@MY-PC:~$ rmdir test2                         # Удалить папку test2
anastasia@MY-PC:~$ rm test1/2.txt                      # Удалить файл 2 из папки test1

anastasia@MY-PC:~$ cd                                  # Создать папку в домашней директории test3 и добавить в нее два файла
anastasia@MY-PC:~$ mkdir test3
anastasia@MY-PC:~$ touch 4.txt 5.txt               

anastasia@MY-PC:~$ rm -r test3                         # Удалить папку test3
anastasia@MY-PC:~$ mkdir test4                         # Создать папку test4 в домашней директории

anastasia@MY-PC:~$ cd test1
anastasia@MY-PC:~/test1$ mv "1.txt" "3.txt" ~/test4    # Переместить файлы 1 и 3 из папки test1 в папку test4

anastasia@MY-PC:~$ cd test4
anastasia@MY-PC:~/test4$ echo "Line 1" >> 1.txt
anastasia@MY-PC:~/test4$ echo "Line 2" >> 1.txt
anastasia@MY-PC:~/test4$ echo "Line 3" >> 1.txt        # Добавить в файл 1 три строки со словами line

anastasia@MY-PC:~/test4$ cat 1.txt                     # Посмотреть содержимое файла 1
anastasia@MY-PC:~/test4$ echo "Line 1" >> 3.txt
anastasia@MY-PC:~/test4$ echo "Line 2" >> 3.txt
anastasia@MY-PC:~/test4$ echo "Line 3" >> 3.txt        # Добавьте в файл 3 три строки со словами line

anastasia@MY-PC:~/test4$ cat 1.txt 3.txt               # Просмотрите содержимое двух файлов (1 и 3) сразу

anastasia@MY-PC:~/test4$ echo "line line line 1" > 1.txt
anastasia@MY-PC:~/test4$ echo "line line line 2" >> 1.txt
anastasia@MY-PC:~/test4$ echo "line line line 3" >> 1.txt # Используя один из редакторов, заменить все строки в файле 1
```
Поиск и редактирование файлов, работа с процессами, проверка доступности сервера, передача данных на сервер в bash: 
---
```python

anastasia@MY-PC:~$ cd                                    # Зайти в домашнюю директорию через терминал.
anastasia@MY-PC:~$ mkdir test3                           # Создать папку test 3

anastasia@MY-PC:~/test3$ echo -e "row1\nrow2\nrow3\nrow4"
> 4.txt & echo -e "row1\nrow2\nrow3\nrow4"
> 5.txt & echo -e "row1\nrow2\nrow3\nrow4" > 6.txt       # Добавить в папку test 3 три файла 4, 5 и 6, в каждом из которых должно быть по 4 строки row1, row2, row3, row4

anastasia@MY-PC:~/test3$ grep -i "row2" 5.txt            # Найти строку row2 в файле 5
anastasia@MY-PC:~$ grep -ir "row" ~/test3                # Найти строку row в папке test3
anastasia@MY-PC:~$ cd test3 && grep -ic "row" 6.txt      # Посчитать сколько строк с содержимым row в файле 6
    4
anastasia@MY-PC:~$ find ~/test3 -name "5*"               # Найти файл 5 внутри папки test3
anastasia@MY-PC:~$ find ~/test3 -name "5*" -exec rm {} + # Используя команду find, удалить файл 5
anastasia@MY-PC:~$ cd test3 && echo "test" >> 4.txt      # Используя команду echo, добавить слово test в файл 4 
anastasia@MY-PC:~/test3$ sed -i 's/test/fail/' 4.txt     # Заменить слово test в файле 4 на fail
 anastasia@MY-PC:~/test3$ echo "test" >> 4.txt           # Добавить в файл 4 слово test так, чтобы сохранилось содержимое
anastasia@MY-PC:~$ ps aux                                # Просмотреть все процессы для юзеров не только в консоли, которые происходят в системе
anastasia@MY-PC:~$ kill 666                              # Убить процесс 666 в консоли
anastasia@MY-PC:~$ ping rusau.net                        # Узнать доступность ресурса rusau.net, используя ping
anastasia@MY-PC:~$ ping -c 5 rusau.net                   # Отправить 5 пакетов на сайт rusau.net

anastasia@MY-PC:~$ curl https://petstore.swagger.io/
v2/pet/findByStatus?status=sold                          # Используя GET и команду curl, получить информацию о зарегистрированных питомцах с любым статусом на https://petstore.swagger.io/

anastasia@MY-PC:~$ curl -X POST -H "Content-Type: application/json" -d '{
        "username": "Baby",
        "firstName": "Lola",
        "lastName": "Morris",
        "email": "123qw@lis.ru",
        "password": "password987",
        "phone": "8789654522"
      }' https://petstore.swagger.io/v2/user                # Используя POST и команду curl, создать нового пользователя на https://petstore.swagger.io/
