## Лабораторная работа grep | решение

1. создаю папку для лабораторной работы и в нее добавляю 3 файла с расписанием
   
<img width="350" alt="Снимок экрана 2024-12-15 в 17 16 13" src="https://github.com/user-attachments/assets/4ff505f7-6542-4d74-bf19-35d016fa8360" />

<img width="500" alt="Снимок экрана 2024-12-15 в 17 33 55" src="https://github.com/user-attachments/assets/38a18b03-77c2-40cb-b3ae-9317bea847c6" />



2. создаю bash-скрипт для задачи:
   ```
   #!/bin/bash

   echo "Введите время урока (пример ввода: 10:00):"
   read time
   echo "Введите класс (пример ввода: 10 класс):"
   read class
   echo "Введите предмет для подсветки (пример ввода: Математика):"
   read subject
   
   
   echo -e "\nУроки, которые начинаются в $time:"
   grep "^$time" file*.txt
   
   
   echo -e "\nУроки для класса $class:"
   grep "$class" file*.txt
   
   
   echo -e "\nУроки с предметом '$subject':"
   grep --color=always "$subject" file*.txt
   
   
   echo -e "\nКоличество уроков по предметам:"
   grep -h -oE '\|\s[А-Яа-яЁё ]+\s\|' file*.txt | sort | uniq -c | sort -rn
   ```
<img width="500" alt="Снимок экрана 2024-12-15 в 17 38 42" src="https://github.com/user-attachments/assets/0b8ced34-7a9b-4070-ba0e-165c9dd79def" />


3. делаю скрипт исполняемым с помощью следующей команды 
   ```
   chmod +x schedule.sh
   ```
4. запускаю скрипт:
   ```
   ./schedule.sh
   ```
<img width="420" alt="Снимок экрана 2024-12-15 в 17 35 50" src="https://github.com/user-attachments/assets/5eb4ddfa-4430-4f13-9c13-823a02b9b9dd" />
