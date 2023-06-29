# bookmarks
Социальная сеть для публикаций своих картинок. Есть возможность лайкать, подписываться, авторизация через Google, Twitter, Facebook

You can install all the requirements at once with the command pip install -r requirements.txt.

A social website,
including user registration, password management, profile editing, and authentication. Users can share images and interact
with each other. Users can to bookmark any image on the internet and share it with other
users. You can to see activity on the platform from the users they follow and like/unlike
the images shared by them. 


Социальный веб-сайт,включающий регистрацию пользователей, управление паролями, редактирование профиля и аутентификацию. Пользователи могут обмениваться изображениями и взаимодействовать
друг с другом. Могут добавлять в закладки любое изображение в Интернете и делиться ими с другими
пользователями. Вы можете видеть активность на платформе от пользователей, на которых они подписаны, и лайки / дизлайки
на странице картинки, которыми они делятся.

# Установка

* Создаем виртуальное окружение
```
python -m venv .venv
.venv/scripts/activate
```

* Устанавливаем зависимости проекта
pip install -r requirements.txt

* В файле .env укажите API ключи для социальной аутентификации через Google, Twitter, Facebook:
```env
# Facebook auth
SOCIAL_AUTH_FACEBOOK_KEY = "your_key"
SOCIAL_AUTH_FACEBOOK_SECRET = "your_secret"

# Google auth
SOCIAL_AUTH_GOOGLE_OAUTH2_KEY = ""
SOCIAL_AUTH_GOOGLE_OAUTH2_SECRET = ""

# Twitter auth
SOCIAL_AUTH_TWITTER_KEY = ""
SOCIAL_AUTH_TWITTER_SECRET = ""

# Twitter
CLIENT_ID = ""
CLIENT_SECRET = ""
BEARER_TOKEN = ""
```
* Установите и запустите Redis (требуется Docker)
```
docker pull redis
docer run --name redis -p 6379:6379 redis
```


* Проведите миграцию базы данных:
```
python manage.py migrate
```

* Создайте superuser:
```
python manage.py creatsuperuser
```

* Обычный запуск проекта http://127.0.0.1:8000/account/:
```
python manage.py runserver
```


* Запуск проекта с имитацией https протокола для тестирования социальной аутентификации:
Сначало отредактируйте главный hosts файл и добавить в его конец:
```
# django bookmarks project
127.0.0.1 mysite.com
```

Запуск сервера команой:
```
python manage.py runserver_plus --cert-file cert.crt
```
После этого вы может войти на сайт по https://mysite.com:8000/account/


Этот проект лицензирован в соответствии с лицензией MIT. Подробности можно найти в файле [LICENSE](LICENSE).
