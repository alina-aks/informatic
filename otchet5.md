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
  
## Задание 2

1. Устанавливаю Git Flow
   ```
   brew install git-flow
   ```
2. В репозитории инициализирую Git Flow:
   ```
   git flow init
   ```
   <img width="600" alt="Снимок экрана 2024-12-10 в 16 40 18" src="https://github.com/user-attachments/assets/68f90c73-1fd9-4d7a-9468-84d767bae213">

3. Создаю новую ветку task-management:
   ```
   git flow feature start task-management
   ```
   в ней создаю файл task_manager.py:
   ```
   def create_task(title, description):
    # Логика создания задачи
    print(f"Создана новая задача: {title}")
   ```
   и выполняю коммит 
   ```
   git add task_manager.py
   git commit -m "Добавлен функционал управления задачами"
   ```
   
   <img width="600" alt="Снимок экрана 2024-12-10 в 16 41 51" src="https://github.com/user-attachments/assets/fede4c23-2371-424e-8709-a90a7f37d58d">

4. Далее обьединяю фичу с основной веткой
   ```
   git flow feature finish task-management
   ```

5. Git автоматически переключился на ветку develop, в ней создаю релиз
   ```
   git flow release start v1.0.0
   ```

   <img width="600" alt="Снимок экрана 2024-12-10 в 16 43 10" src="https://github.com/user-attachments/assets/1190a13b-2918-4ddf-90a8-6ac4f4c3cb56">


6. вношу изменения и коммичу:
   ```
   echo "v1.0.0" > version.txt
   git add version.txt
   git commit -m "Обновлена версия для релиза v1.0.0"
   ```
7. завершаю релиз и объединяю с ветками "develop" и "main":
   ```
   git flow release finish v1.0.0
   ```
   
   <img width="600" alt="Снимок экрана 2024-12-10 в 17 13 30" src="https://github.com/user-attachments/assets/012f9125-683d-4c77-bdd7-0891ab260f28">

8. создаю hotfix
   ```
   git flow hotfix start hotfix-1.0.1
   ```
   <img width="600" alt="Снимок экрана 2024-12-10 в 17 17 12" src="https://github.com/user-attachments/assets/0bdc0886-2b5e-4a7f-8c4d-4ede8ad814d7">

9. вношу изменения для ошибки и коммитичу:
   ```
   git add file_with_error.py
   git commit -m "Исправлена критическая ошибка"
   ```
   <img width="600" alt="Снимок экрана 2024-12-10 в 17 05 35" src="https://github.com/user-attachments/assets/09eb3d0d-a5e9-4bf6-a679-e1df0ed3014f">

10. Завершаю hotfix и объединяю его с ветками "develop" и "main":
   ```
   git flow hotfix finish hotfix-1.0.1
   ```
11. Отправляю изменения на удаленный репозиторий
    ```
    git push origin develop
    git push origin main
    ```


Вывод:
Я изучила основные команды Git, Git Hooks, Git Flow.


   
