# Discord.js Music Plugin

![alt text](https://nodei.co/npm/discord.js-music-v11.png?downloads=true&stars=true "discord.js-music-v11 stats")

__Описание:__
Эта версия не стабильная, мы (изначальные разработчики) всё тестили, но не углублялись. Всё рабочее работает, но мы не уверены в этом.  
Это форк [nexu-dev](https://github.com/nexu-dev/discord.js-music) форка [ruiqimao](https://github.com/ruiqimao/discord.js-music) для [Discord.js](https://discord.js.org/) версии v11.x. Также добавляет несколько своих фишек. До сих пор нуждается в тестировании и фиксах, но да, это ЧТО-ТО!

__Действующие команды:__  
* `play (<url>|<search string>)`: Воспроизводит видео/музыку. Можно взять ссылку с YouTube, Vimeo, YouKu и других (SoundCloud не поддерживается). Вы также можете искать песни с помощью поиска.
* `skip [number]`: Пропускает некоторое кол-во песен. По умолчанию пропускает 1 песню.
* `queue`: Показывает воспроизводимую песню.
* `pause`: Ставит воспроизведение на паузу. (нужен music manager)
* `resume`: Продолжает воспроизведение. (нужен music manager)
* `volume`: Регулирует громкость между 1 и 200 (нужен music manager)
* `leave`: Очищает список заказанных песен и выходит из голосового канала.
* `clearqueue`: Очищает список заказанных песен.

__Разрешения/права:__  
* Если переменная `anyoneCanSkip` установлена в false, тогда только админы и заказавший песню человек может пропустить её.
* Только админы могут изменять громкость и ставить паузу/возобновлять воспроизведение.

__Добавлено:__  
* Поиск снова работает.
* Добавлена команда 'volume'
* Добавлена команда 'leave'
* Добавлена команда 'clearqueue'
* Видно, кто заказал песню

__Изменилось:__  
* Permissions

__Перед установкой:__  
1. `npm install discord.js` // Основная библиотека Discord.  
2. `npm install ffmpeg-binaries` // Даёт возможность "петь" боту (нужно войти в голосовой канал)  
3. `npm install node-opus` or `npm install opusscript` // Нужен для возпроизведения музыки, node-opus рекомендуется

__Установка:__  
1. `npm install discord.js-music-v11`

__Популярные проблемы:__  
__Проблема:__ FFMPEG не найден в системе, так что аудио не может воспроизводиться. Убедитесь в том, что FFMPEG установлен и, если это так, проверьте ваш путь к нему.  
__Решение:__ `npm install ffmpeg-binaries`  
__Проблема:__ Не могу найти движок OPUS.  
__Решение:__ `npm install node-opus` or `npm install opusscript`  
__Проблема:__ Любые ошибки node-gyp. (проблема с установкой, нет cl.exe и др.)  
__Решение:__ Решение состоит из нескольких этапов.  
1. Скачать и установить [Visual Studio 2015](https://www.visualstudio.com/downloads/)  
2. Новый проект -> Visual C++  
3. Установить Visual C++  

Если не помогло;  
1. Скачать и установить это => [Windows 8.1 SDK](https://developer.microsoft.com/en-us/windows/downloads/windows-8-1-sdk)

Это простой плагин для воспроизведения музыки. В использовании прост как корка лимона.:  
```javascript
const Discord = require('discord.js');
const music = require('discord.js-music-v11');
const client = new Discord.Client();
const token = "<auth_token>" // Recommended to load from json file.

client.on('ready', () => {
    console.log(`[Start] ${new Date()}`);
});

music(client);
client.login(token);
```

Модуль состоит из одной функции, которая принимает два аргумента:  
```javascript
/*
 * @param {Client} client - discord.js клиент.
 * @param {object} options - (Опциональный) Опции для конфигурирования бота. Принимаемые опции:
 * 		prefix: Префикс для всех команд (по умолчанию: '!').
 * 		global: Использовать глобальную очередь для всех серверов или для каждого свою (по умолчанию: false).
 * 		maxQueueSize: Квота на список проигрываемых файлов (по умолчанию: 20).
 * 		anyoneCanSkip: Любой может пропустить песню.
 * 		clearInvoker: Очищать ли команды.
 * 		volume: Громкость по умолчанию при входе на сервер.
 */
music(client, options);
```
