## Лабораторная работа 5 | Отчет

## Задание 1

1. Создаю тестовый репозиторий и открываю его локально
2. Перехожу в папку .git/hooks и создаю файл pre-commit и открываю для редактирования:
   ```
   cd .git/hooks
   touch pre-commit
   nano pre-commit
   ```
   
   <img width="451" alt="Снимок экрана 2024-12-10 в 16 19 34" src="https://github.com/user-attachments/assets/317e5c47-02f6-4707-b230-91b4f607f1cf">


3. Вписываю следующий bash-скрипт:
   ```
   #!/bin/bash

    is_valid=true
    
    # Поиск всех .txt файлов, добавленных для коммита
    staged_files=$(git diff --cached --name-only --diff-filter=ACMR | grep -E '\.txt$')
    
    # Если .txt файлы найдены
    if [[ -n "$staged_files" ]]; then
      echo "Checking .txt files for required content..."
      for file in $staged_files; do
        # Проверяем, что файл существует
        if [[ -f "$file" ]]; then
          # Проверяем, есть ли в файле строка "Author: "
          if ! grep -q "Author:" "$file"; then
            echo "Error: File '$file' does not contain required text 'Author:'."
            is_valid=false
          fi
        else
          echo "Error: File '$file' not found."
          is_valid=false
        fi
      done
    else
      echo "No .txt files staged for commit."
    fi
    
    # Если проверка не прошла, отменяем коммит
    if [[ "$is_valid" == false ]]; then
      echo "Commit aborted due to file format issues."
      exit 1
    fi
    
    echo "All .txt files passed the check."
    exit 0

   ```
4. Делаю файл исполняемым:
   ```
   chmod +x .git/hooks/pre-commit
   ```
  
5. Создаю текстовый файл, который не должен пройти проверку,добавляю его для коммита и пробую закоммитить
   ```
   echo "Test text, shouldn't be pulled" › test.txt
   git add test.txt
   git commit -m "Test commit"
   ```
   
   <img width="725" alt="Снимок экрана 2024-12-10 в 16 20 58" src="https://github.com/user-attachments/assets/145f7091-0874-40fa-9be9-9d169c4dbcc5">

   Коммит не проходит, ведь нет нужной строки

  
6. Изменяю файл, добавив нужную строку, повторяю все вышеперечисленное

  <img width="324" alt="Снимок экрана 2024-12-10 в 16 22 20" src="https://github.com/user-attachments/assets/c18aabd1-cdbe-47d4-bedc-9ba10d8e9797">

  <img width="542" alt="Снимок экрана 2024-12-10 в 16 22 46" src="https://github.com/user-attachments/assets/99fa0bbf-115f-4b66-9912-91337165c7a9">

  Коммит проходит, так как файл имеет строку "Author:"


Вывод:
Я научилась создавать контейнеры, запускать в них приложения и устанавливать соединение между контейнерами.


   
