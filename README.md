# mis
Init script for minecraft/bukkit servers
A init script that apart from starting and stopping the server correctly also has some extra features for running a mincraft/craftbukkit server.

Features

Utilization of ramdisk for world data, decreases lag when getting world chunks
Cleaning of server.log, a big log file slows down the server
Backup for worlds
Server updating and complete backup
Exclude files and directories from full backup by adding them to "exclude.list"
Requirements

screen, rsync

Access server console
screen -r minecraft
Exit the console

Ctrl+A D
Setup
Symlink the minecraft file to /etc/init.d/minecraft, set the required premissions and update rc.d.

sudo ln -s ~/minecraft-init/minecraft /etc/init.d/minecraft
chmod 755  ~/minecraft-init/minecraft
sudo update-rc.d minecraft defaults 99 10
Edit the variables in config.example to your needs and rename it to config (leaving it in the same folder as the original minecraft script)

Move your worlds to the folder specified by WORLDSTORAGE

Edit crontab

As the server user:

crontab -e
Add these lines:

#m  h   dom mon dow command
02  05  *   *   *   /etc/init.d/minecraft backup
55  04  *   *   *   /etc/init.d/minecraft log-roll
*/30    *   *   *   *   /etc/init.d/minecraft to-disk
To load a world from ramdisk run:

/etc/init.d/minecraft ramdisk WORLDNAME
to disable ramdisk, run the same command again.

For more help with the script, run

/etc/init.d/minecraft help
Flattr this git repo

Good stuff
Backup rotation script good if you want some kind or rolling of the world backups.
