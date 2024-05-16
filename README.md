# Установка
Склонируй репозиторий
```
git clone https://github.com/Lans657/lab2.git
```

Сделай ``chmod +x ./setup.sh``, чтобы дать разрешение скрипту ``setup.sh`` на исполнение

Запусти ``./setup.sh``, этот скрипт установит .net 8 sdk, забилдит проект и создаст демона **lab2-host**


## Запуск клиента
Запусти ``./run_client.sh``

## Запуск сервера из терминала
Если хочется запустить сервер из терминала, запусти ``./run_host.sh``


## Дополнительно
Посмотреть состояние демона можно командой
```bash
sudo systemctl status lab2-host
```

Журнал доступен по команде
```bash
sudo journalctl -u lab2-host
```

Запуск, перезагрузка и остановка демона
```bash
sudo systemctl start lab2-host
sudo systemctl restart lab2-host
sudo systemctl stop lab2-host
```

Для удаление демона из системы, запусти ``uninstall_daemon.sh``


# Использование
После запуска ``setup.sh`` демон-сервер уже настроен и готов к работе.

В директории ``./lab2-host/build/`` лежат исполняемый файл и файл конфигурации ``appsettings.json``, в котором можно указать:
- директорию, в которую будут сохраняться файлы
- максимальный размер файла
- максимальное кол-во одновременно обслуживаемых клиентов 
- порт сервера

После изменения конфигурации необходимо перезапустить демона командой
```bash
sudo systemctl restart lab2-host
```

После запуска клиент запросит ip и порт сервера, после чего попытается к ним подключится.
- Если сервер разрешает подключение, пользователь вводит путь к файлу, который нужно передать
- Если сервер не разрешает подключение, клиент ждет

Нужно указывать абсолютный путь до файла, начинающийся с `/home`. Чтобы узнать имя пользователя, пройди в `cd /home` и запусти `ls`

Полный путь будет выглядеть как `/home/{имя пользователя}/lab2/test.txt`, где `/lab2/test.txt` - заранее созданный тестовый файл

После указания пути начинается передача файла с указанием прогресса в терминале.
После завершения передачи пользователь может передать еще один файл.
