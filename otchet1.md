## Лабораторная работа 1 | Отчет

Для выполнения лабораторной работы я использовала программу Терминал, предустановленную в MacOS
1. С создала файл с именем `script.bash1` , введя в терминал команду `touch script.bash`
<img width="445" alt="Снимок экрана 2024-09-23 в 19 51 02" src="https://github.com/user-attachments/assets/fc75edea-6105-4105-8865-e8bd1ff56104">

2. Открыла этот файл с помощью стандартного текстового редактора TextEdit
   
<img width="646" alt="Снимок экрана 2024-09-23 в 19 52 03" src="https://github.com/user-attachments/assets/0463c3ec-2ea5-4092-a584-286753d7344d">

3. Вписываю в файл следующий скрипт:

`#!/bin/bash`


`echo "Welcome to ITMO University"`

<img width="646" alt="Снимок экрана 2024-09-23 в 19 56 24" src="https://github.com/user-attachments/assets/4efb0072-2ff0-4324-846d-9dacc7007bdd">

4. Ввожу в терминал ` bash script.bash1 ` и терминал выводит нужный нам текст: `Welcome to ITMO University`
<img width="490" alt="Снимок экрана 2024-09-23 в 20 01 03" src="https://github.com/user-attachments/assets/473d081a-42fc-49c3-b0ee-93bf0a95fce8">



Далее модифицирую файл, чтобы выполнить задание:
1. Чтобы считать введенное с клавиатуры имя и вывести его после фразы `Welcome` использую переменную `$@`, которая позволяет нам вести имя, состоящее более чем из 1 слова
<img width="490" alt="Снимок экрана 2024-09-23 в 20 09 17" src="https://github.com/user-attachments/assets/88e1add9-ee23-4a79-8679-7ab01e318a7f">

2. Ввожу команду `bash script.bash1 Vasya Pupkin` в терминал, результат :

<img width="474" alt="Снимок экрана 2024-09-23 в 20 10 32" src="https://github.com/user-attachments/assets/bd057910-62b6-45da-ae8b-f87a9056836c">

Для дополнительной проверки попробую второй пример:

<img width="632" alt="Снимок экрана 2024-09-23 в 20 11 53" src="https://github.com/user-attachments/assets/4a0de426-9860-4905-9eb3-4d1bb6a32388">

Вывод:
Я узнала основы работы в терминале, научилась работать с файлами и выводить текст, с помощью переменной.


