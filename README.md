## Итоговая контрольная работа
1. Используя команду cat в терминале операционной системы Linux, создать два файла Домашние животные (заполнив файл собаками, кошками, хомяками) и Вьючные животными заполнив файл Лошадьми, верблюдами и ослы), а затем объединить их. Просмотреть содержимое созданного файла. Переименовать файл, дав ему новое имя (Друзья человека). 
2. Создать директорию, переместить файл туда.
![enter image description here](https://github.com/Zorrki/Control/blob/main/1_2.png?raw=true)
3. Подключить дополнительный репозиторий MySQL. Установить любой пакет из этого репозитория.
![enter image description here](https://github.com/Zorrki/Control/blob/main/3.png?raw=true)
![enter image description here](https://github.com/Zorrki/Control/blob/main/3_1.png?raw=true)
4. Установить и удалить deb-пакет с помощью dpkg.
![enter image description here](https://github.com/Zorrki/Control/blob/main/4.png?raw=true)
![enter image description here](https://github.com/Zorrki/Control/blob/main/4_1.png?raw=true)
5. Выложить историю команд в терминале ubuntu
```
      310  mkdir Control
      311  rm Control
      312  rm -r Control
      313  clear
      314  mkdir Control
      315  cd Control/
      316  cat > home_animals
      317  cat home_animals 
      318  cat > ride_animals
      319  cat ride_animals 
      320  cat home_animals ride_animals > animals
      321  cat animals 
      322  mv animals mans_friends
      323  ls -lh
      324  ls
      325  cat mans_friends 
      326  sudo wget -c https://dev.mysql.com/get/mysql-apt-config_0.8.23-1_all.deb
      327  sudo dpkg -i mysql-apt-config_0.8.23-1_all.deb 
      328  sudo apt-get update
      329* 
      330  sudo apt autoremove
      331  sudo apt-get install mysql-client-core-8.0 
      332  sudo apt-get install mysql-server
      333  sudo apt-get install mysql-source
      334  sudo apt-get install mysql-source-8.0 
      335  clear
      336  wget https://repo.zabbix.com/zabbix/6.4/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest+ubuntu22.04_all.deb
      337  dpkg -i zabbix-release_latest+ubuntu22.04_all.deb
      338  sudo dpkg -i zabbix-release_latest+ubuntu22.04_all.deb
      339  apt update 
      340  sudo apt update 
      341  systemctl status zabbix-web-service.service 
      342  sudo dpkg -r zabbix-release 
      343  sudo dpkg -i zabbix-release_latest+ubuntu22.04_all.deb
      344  sudo dpkg -r zabbix-release 
      345  sudo dpkg -i zabbix-release_latest+ubuntu22.04_all.deb
      346  sudo dpkg -r zabbix-release 
      347  sudo dpkg -r zabbix-release --purge
      348  sudo dpkg -i zabbix-release_latest+ubuntu22.04_all.deb
      349  sudo dpkg -r zabbix-release
      350  history
```
