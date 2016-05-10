#Скрипт запуска для minecraft/bukkit сервера

##Описание:##
Скрипт позволяет запускать и останавливать сервер при старте и остановке системы, создавать бэкапы мира

##Зависимости##
screen, rsync

##Консоль##
###Для доступа к консоли###
`service minecraft screen`

###Закрыть консоль###
`Ctrl+A D`

##Установка##
*Создаем символическую ссылку для файла minecraft в /etc/init.d/minecraft, устанавливаем разрешения и обновляем rc.d.
```
sudo ln -s /patch-to-script/minecraft /etc/init.d/minecraft
chmod 755  ~/patch-to-script/minecraft
sudo update-rc.d minecraft defaults 99 10
```
1.Правим переменные в config
2.Перемещаем миры в папку указанную в WORLDSTORAGE
3.Редактируем crontab
  
  `sudo crontab -e`

  Добавляем строки

    `02  05  *   *   *   /etc/init.d/minecraft backup`
    
##Для вывода списка всех команд##

  `service minecraft help`
