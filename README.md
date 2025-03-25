# VM
FLASK on virtual machine
#### Установим на виртуальную машину Ubuntu Server (ubuntu-24.04.2-live-server-amd64.iso)
![image](https://github.com/user-attachments/assets/08a699ce-afee-4f5f-ae6e-bfe2fbdb87f3)
#### Узнаем ip-адрес машины для подключения по ssh через cmd через ifconfig, если он не установлен команда sudo apt install net-tools поможет
![image](https://github.com/user-attachments/assets/269ffad9-a20a-4977-aafe-a98d4462b481)
#### Далее все команды будем выполнять через cmd на windows-хосте
![image](https://github.com/user-attachments/assets/0a71912b-feba-4a9f-9941-933db65201e9)
#### Откроем папку с проектом в проводника, нажмем правой кнопкой мыши и откроем cmd в папке для удобства. Не будем устанавливать ftp-клиент воспользуемся командой scp с флагом рекурсии.
![image](https://github.com/user-attachments/assets/edb7ec0d-e3a0-4396-98f4-4e4c68a4347d)
#### Для того чтобы скопировать рабочую папку на сервер буду использовать команду:
##### D:\Документы\Учеба\джанго>scp -r myproject admiral@192.168.56.102:/home/admiral/
#### проект залит на сервер
![image](https://github.com/user-attachments/assets/2bf9a4c1-227a-4419-8b8c-08975611a19f)
#### Коннечусь по ssh на сервер, проверяю скопированные файлы:
![image](https://github.com/user-attachments/assets/30520eb1-a26f-4646-a285-80994566239c)
#### Пытаюсь запустить скрипт manage.py, получаю ошибку:
![image](https://github.com/user-attachments/assets/c7b8075a-1e81-4799-b11d-32bb025c693d)
#### не установлены библиотеки
![image](https://github.com/user-attachments/assets/c789c189-a8bf-42dd-aadb-1ef939e3756c)
#### Устанавливаем pip: sudo apt install python3-pip
#### Устанавливаем необходимые библиотеки
#### sudo apt install python3-flask
#### django
#### Вводим команду: pytho3 manage.py runserver 0.0.0.0:8000
![image](https://github.com/user-attachments/assets/789cafef-25f6-4ed9-97bc-64ca7e75f476)
#### Забыли добавить в алловед хостс явно
![image](https://github.com/user-attachments/assets/97944f1f-9439-4f05-a97b-c186dd358da4)
#### откроем nano файл settings.py и добавим
![image](https://github.com/user-attachments/assets/216efe57-c884-4fad-a4ae-0dd91c361a8b)
![image](https://github.com/user-attachments/assets/f85658cc-8466-46ac-8344-a2024dbf327b)
#### Проверяем обратно работу сервера
![image](https://github.com/user-attachments/assets/b7bd81fa-ef0c-44a1-b01e-2221b21a4dcf)
#### Заработало:
![image](https://github.com/user-attachments/assets/016a76b1-56c2-4d08-8a03-3ee066efd078)
![image](https://github.com/user-attachments/assets/1852e30e-5d08-4155-a6d0-e0741f228a6a)
![image](https://github.com/user-attachments/assets/10b4373e-5ab1-40da-a699-2f56f26d5947)
#### Устанвливаем постгресс: sudo apt install postgresql postgresql-contrib
#### Проверяем работу службы:
![image](https://github.com/user-attachments/assets/8ec879a1-781d-493e-9191-ab3a99de8617)
#### Создаем пользователя: sudo -i -u postgres
![image](https://github.com/user-attachments/assets/1a7627f2-9739-4926-baf2-a5d376c0604d)
#### Создадим базу и зададим пароль
![image](https://github.com/user-attachments/assets/616e17ab-78b1-4faa-98dc-5064b62a3b19)
#### Подключим созданную базу данных:
![image](https://github.com/user-attachments/assets/eed34a3a-0584-48f2-b8bf-02de0621154a)
#### Добавим данные о базе данных в settings.py через nano:
![image](https://github.com/user-attachments/assets/08d6c101-0d15-4b74-95f3-4d665710bb70)
#### Пытаемся мигрировать, получаем ошибку:
![image](https://github.com/user-attachments/assets/017fedf1-8818-4505-9c47-cfff722af4a0)
#### Установим недостающее: pip install psycopg2-binary --break-system-packages
#### Минрируем и исправляем очепятку:
![image](https://github.com/user-attachments/assets/14e53463-d1e1-4f0d-984e-09bfa6f1495d)
#### Мигрируем еще раз:
![image](https://github.com/user-attachments/assets/0d6543d0-7265-43de-91b6-3a588304fec0)
#### И еще одна писка, это уже система:
![image](https://github.com/user-attachments/assets/3771c706-57d7-4312-a44f-0fe30199e948)
#### Ура! Миграция прошла успешно:
![image](https://github.com/user-attachments/assets/0f24eb1c-94fe-4253-a1ee-d66ac26558ac)
#### Устанавливаем gunicorn
![image](https://github.com/user-attachments/assets/9324bbcb-8993-4c3e-8e5b-a8dc2b511650)
#### Добавляем в ПУТЬ и запускаем сайт:
![image](https://github.com/user-attachments/assets/f036dc86-7fdd-44aa-8e94-3286e14e09e8)
#### Идем дальше
![image](https://github.com/user-attachments/assets/5033d301-5881-4928-bf25-c6d9bbbbaed5)
#### Сервис работает
![image](https://github.com/user-attachments/assets/30f4868f-773d-4af9-a014-a9223f439f4b)
#### Создадим конфиг: sudo nano /etc/nginx/sites-available/myproject
![image](https://github.com/user-attachments/assets/a9b0334b-6c64-4894-a45f-a53e01e9c5fa)
#### Already in use:
![image](https://github.com/user-attachments/assets/28f63d49-2a05-414c-bd90-af2e806e5d01)
#### Попробуем выбрать 8001 порт, чтобы оценить работоспособность.
#### Заработало.
![image](https://github.com/user-attachments/assets/d3e3f20f-a171-45b2-9cc5-977091ae0c0b)
#### сайт доступен по ссылке: http://192.168.56.102 (локально)

























