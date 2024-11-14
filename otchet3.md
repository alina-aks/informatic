# Отчет Лабораторная 3
## 1) Создание виртуальных машин
создаю 3 виртуальных машины с убунту

<img width="236" alt="Снимок экрана 2024-11-14 в 20 31 02" src="https://github.com/user-attachments/assets/89833859-53df-419f-98b0-b6fd365518f2">

## 2) Настройка сети
подключаю виртуальные машины к сети и проверяю подключение командой
  ```
   ping google.com
   ```
<img width="350" alt="Снимок экрана 2024-11-13 в 18 12 11" src="https://github.com/user-attachments/assets/d5e4e055-f600-4697-870a-b8ea255edada">
<img width="350" alt="Снимок экрана 2024-11-13 в 18 11 45" src="https://github.com/user-attachments/assets/bbf40681-67ba-42b6-a800-b03982126485">
<img width="350" alt="Снимок экрана 2024-11-13 в 18 11 15" src="https://github.com/user-attachments/assets/66cde199-e053-4701-aa55-4a9e940f0d7f">

## 2) IP
далее необходимо узнать ip адрес каждой машины
ввожу в терминал следующую команду:
 ```
   ip addr show
   ```
>> - A: 192.168.64.3
>> - B: 192.168.64.4
>> - C: 192.168.64.5

<img width="300" alt="Снимок экрана 2024-11-13 в 18 14 54" src="https://github.com/user-attachments/assets/efcf6c7a-5bf7-4c4f-9240-c4b91c353470">
<img width="300" alt="Снимок экрана 2024-11-13 в 18 15 37" src="https://github.com/user-attachments/assets/5c14f851-6f1c-4ed4-93b3-949aaa6e5d36">
<img width="300" alt="Снимок экрана 2024-11-13 в 18 16 31" src="https://github.com/user-attachments/assets/59592043-7896-4811-a821-d9a31ff47fb4">

## 3) связь
настроим связь машины А с Б и С с помощью команды:
 ```
   pind <ip>
   ```
<img width="450" alt="Снимок экрана 2024-11-13 в 18 19 56" src="https://github.com/user-attachments/assets/ec336aef-c909-48a8-911c-7760b14feca7">
<img width="450" alt="Снимок экрана 2024-11-13 в 18 20 44" src="https://github.com/user-attachments/assets/20b6750a-684e-4710-8188-d48524b48dd4">

прерываю связь между машинами Б и В командой:
```
   sudo iptables -A INPUT -s {ip} -j DROP
   ```
и проверяю доступ между машинами:

<img width="450" alt="Снимок экрана 2024-11-13 в 18 23 40" src="https://github.com/user-attachments/assets/69b6de40-565d-4fbd-9e12-cfd1cfd764a7">
<img width="450" alt="Снимок экрана 2024-11-13 в 18 24 35" src="https://github.com/user-attachments/assets/f574a874-9647-4cf7-8614-273fe5565965">
