vk_friends
==========

Граф дружеских связей в vk.com

##Первые шаги

Для начала необходимо создать [Standalone-приложение](https://vk.com/dev/standalone) в VK. Делается это [там](https://vk.com/editapp?act=create). В итоге попросят ввести код-подтверждения, высланный на мобильный, после чего мы попадаем на страницу управления приложением. На вкладке **Настройки** нам пригодится **ID приложения** для получения **access_token**. 

Чтобы его получить необходимо [сформировать](https://vk.com/dev/auth_mobile) **url**:
```
https://oauth.vk.com/authorize?client_id=IDприложения&scope=friends&redirect_uri=https://oauth.vk.com/blank.html&display=page&v=5.21&response_type=token
```

Если адрес сформирован правильно, переходим по нему и получаем нечто вроде:
```
https://oauth.vk.com/blank.html#access_token=ACCESS_TOKEN&expires_in=86400&user_id=USER_ID
```

После этого редактируем файл **settings.py**, вставляя туда полученные **access_token** и **user_id**.
Ура!

##Что дальше

Если просто хочется посмотреть свой список друзей и общих с ними друзей, переходим в каталог с кодом и запускаем:

```
python main.py
```

Если хочется этот список визуализировать:

```
python 2d3.py
```
Затем папке **web** (использовался код [d3](https://github.com/mbostock/d3) для представления графа) открываем **index.html** в браузере и наслаждаемся. [Скриншот](https://db.tt/8Jw8cx9I)

##Полезности
В **settings.py** можете вбить **id** любого интересующего вас человека.

##Что нужно

* Python 3.4
* [requests](https://github.com/kennethreitz/requests)
* Mozilla FireFox, так как в Chrome нельзя использовать **XMLHttpRequest** для загрузки локальных файлов (никто не мешает сделать ```python -m http.server 8000```) 

##Как работает

Если код не понятен ~~то мне очень жаль~~, более-менее понятное объяснение можно найти [здесь](#) (схема переделывается).
