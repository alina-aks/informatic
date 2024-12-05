## Лабораторная работа 4 | Отчет

1. Устанавливаю докер на виртуальную машину
2. Создаю папку для лабораторной и открываю ее:
   ```
   mkdir lab4 && cd lab4
   ```
3. Создаю Dockerfile и открываю его для редактирования
   ```
   touch Dockerfile && nano Dockerfile
   ```
4. Вписываю в файл следующее и сохраняю:
   ```
   FROM ubuntu:24.10

   RUN apt-get update && apt-get install -y libaa-bin iputils-ping

   ENV FIRE="false"

   CMD ["aafire"]
   ```
  <img width="600" alt="Снимок экрана 2024-12-05 в 17 34 42" src="https://github.com/user-attachments/assets/b1e44766-4391-42bd-a3c0-44c273b53820">

5. Собираю образ контейнера с помощью следующей команды:
   ```
   sudo docker build -t aafire:latest .
   ```
   <img width="600" alt="Снимок экрана 2024-12-05 в 19 37 03" src="https://github.com/user-attachments/assets/b069d27d-7651-4cc4-981f-ed682a599018">
   
6. Запускаю приложение aafire в двух терминалах, каждому задаю соответственное название:
   ```
   sudo docker run -it --name first --network myNetwork aafire:latest 
   ```
   ```
   sudo docker run -it --name second --network myNetwork aafire:latest 
   ```
   
  <img width="600" alt="Снимок экрана 2024-12-05 в 17 37 44" src="https://github.com/user-attachments/assets/63a9eaa3-b471-4bd4-bd0a-46684560039f">

7. Вывожу список запущенных контейнеров:
   ```
   sudo docker ps
   ```
  <img width="600" alt="Снимок экрана 2024-12-05 в 17 41 07" src="https://github.com/user-attachments/assets/bcd6da98-30bf-4eaa-9393-80a01c0e9889">
  
8. Далее создаю сеть
   ```
   docker network create myNetwork
   ```
  <img width="600" alt="Снимок экрана 2024-12-05 в 19 40 51" src="https://github.com/user-attachments/assets/a2394d6c-d3f7-4807-8e47-23d61f3b22c2">

9. Подключаю оба докера к сети:
    ```
    docker network connect myNetwork first
    docker network connect myNetwork second
    ```

10. Вывожу информацию о сети:
  ```
  sudo docker network inspect myNetwork
  ```
  <img width="600" alt="Снимок экрана 2024-12-05 в 17 52 51" src="https://github.com/user-attachments/assets/0b5445c0-6c75-449f-a6b9-b9df8eb7d98f">

  <img width="600" alt="Снимок экрана 2024-12-05 в 17 52 59" src="https://github.com/user-attachments/assets/a6fe90e5-18c7-401c-ae3b-0cf79c1d2740">

11. Проверяю наличие соединения между контейнерами:
    
    Первый
    
    <img width="600" alt="Снимок экрана 2024-12-05 в 19 55 04" src="https://github.com/user-attachments/assets/749f061c-2a34-4c16-9299-e8960a076c85">


    Второй
    
    <img width="600" alt="Снимок экрана 2024-12-05 в 19 55 44" src="https://github.com/user-attachments/assets/b89cf173-30c3-4e20-b0ad-c4fd2e5e42d2">

13. Отключаю контейнеры и проверяю соединение ( пакеты не пришли ведь контейнеры отключены)
    <img width="600" alt="Снимок экрана 2024-12-05 в 19 58 31" src="https://github.com/user-attachments/assets/1416bb86-0ece-4e76-8c47-cea2b230f3a2">

Вывод:
Я научилась создавать контейнеры, запускать в них приложения и устанавливать соединение между контейнерами.


   
