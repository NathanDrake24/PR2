В ветке **MAIN** находится только описание работы **README**, сама работа выполнена в ветке **MASTER**
# Первоначальная настройка Git.
Добавляем пользователя

<img width="605" height="109" alt="image" src="https://github.com/user-attachments/assets/0e0624dc-8510-44ac-90cf-6d5ad6f845a0" />


# Инициализация Git-репозитория

Создаем папку и переходим в нее

<img width="243" height="107" alt="image" src="https://github.com/user-attachments/assets/4f63d636-94a4-4f21-aff1-d60445c4a328" />


Создаем репозиторий с название PR2 на github

<img width="1937" height="908" alt="image" src="https://github.com/user-attachments/assets/94005f14-0245-4d8d-98ba-105391cd9b69" />

Инициализируем локальный репозиторий и подключи к GitHub

```bash
git init
git remote add origin https://github.com/NathanDrake24/PR2.git
```

<img width="633" height="57" alt="image" src="https://github.com/user-attachments/assets/62d69cb9-4817-484c-ac2a-400323ac7bc0" />



# Создадим начальный коммит в ветку master:


```bash
echo "# PR2" > README.md
git add README.md
git commit -m "Initial commit"
git push -u origin master
```

<img width="819" height="517" alt="image" src="https://github.com/user-attachments/assets/cc7571cd-af81-4a9d-bdef-ac5366f8e0b8" />


# Создаем ветку feature/TASK-123 от master

```bash
git checkout -b feature/TASK-123
```

Создай файл с ФИО и группой 

```bash
$ echo "Имя: Гизулин Тагир" > info.txt
echo "Университет: УУНИТ" >> info.txt
```

# Делаем коммит

git add info.txt
git commit -m "Add student info"


# Еще 2 коммита


```bash
echo "Дополнительная строка 1" >> info.txt
git add info.txt
git commit -m "Update info: add line 1"

echo "Дополнительная строка 2" >> info.txt
git add info.txt
git commit -m "Update info: add line 2"
```



<img width="708" height="833" alt="image" src="https://github.com/user-attachments/assets/c847f083-a281-445a-96b6-e7f470c75130" />



# Создаем ветк bugfix/TASK-3321 от master

```bash
git checkout master
git checkout -b bugfix/TASK-3321
```


Теперь изменяем тот же файл info.txt, но в другие строки

```bash
$ echo "Университет: УУНИТ" > info.txt

$ echo "Имя: Гизулин Тагир" >> info.txt

$ echo "Email: gizulintagir@gmail.com" >> info.txt
```


<img width="468" height="161" alt="image" src="https://github.com/user-attachments/assets/2e502610-6a99-4e69-b6e5-3d55ba47e356" />



---

Коммитим

``bash
git add info.txt
git commit -m "Add email to student info"
```

И еще 2 коммита

```bash
$ echo "Телефон: +123456789" >> info.txt
git add info.txt
git commit -m "Add phone number"

echo "GitHub: @NathanDrake24" >> info.txt
git add info.txt
git commit -m "Add GitHub handle"

```
---

<img width="1075" height="328" alt="image" src="https://github.com/user-attachments/assets/390fb061-00f7-4eaf-8d02-b8c1b30f2114" />

---

Вносим временные изменения


```bash
echo "ВРЕМЕННЫЕ ИЗМЕНЕНИЯ" >> info.txt
git stash
```

<img width="956" height="142" alt="image" src="https://github.com/user-attachments/assets/87ec9028-5c30-47b9-bba9-def7bf619932" />


Переключаемся на feature/TASK-123, смотрим файлы:

---

<img width="455" height="179" alt="image" src="https://github.com/user-attachments/assets/b777aeb6-ac9b-405d-bdb4-bd62fabf3fe6" />

---



Возвращаемся обратно в bugfix/TASK-3321 и восстановливаем изменения:

```bash
git checkout bugfix/TASK-3321
git stash pop
```

Убеждаемся, что строка "ВРЕМЕННЫЕ ИЗМЕНЕНИЯ" вернулась:

```bash
cat info.txt
```

<img width="714" height="411" alt="image" src="https://github.com/user-attachments/assets/a96e0bc1-d004-47c9-bf54-7409b3c7171d" />



Теперь можно закоммитить эти изменения

```bash
git add info.txt
git commit -m "Add temporary note (restored from stash)"
```


# Пушим ветки

```bash
git push -u origin feature/TASK-123
git push -u origin bugfix/TASK-3321
```

<img width="827" height="643" alt="image" src="https://github.com/user-attachments/assets/6b418450-834d-4437-8d39-bc214b5561df" />


# Сливаем в мастер

```bash
git checkout master
git merge feature/TASK-123
```

<img width="511" height="227" alt="image" src="https://github.com/user-attachments/assets/80bd0c32-a621-41b6-98b7-32bbebeaca23" />

```bash
git merge bugfix/TASK-3321
```

<img width="641" height="110" alt="image" src="https://github.com/user-attachments/assets/c29aa4c9-5b13-41ad-a4c3-1c3789713849" />


Решаем конфликт

```bash
nano info.txt
```

В ручную удаляем конфликтующие строки

<img width="439" height="305" alt="image" src="https://github.com/user-attachments/assets/e95f985c-161a-4e88-9ca6-01839b0d56df" />



```bash
git add info.txt
git commit -m "Merge bugfix/TASK-3321 into main with conflict resolution"
git push origin main
```







