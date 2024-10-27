## Итоговая контрольная работа
1. Используя команду cat в терминале операционной системы Linux, создать два файла Домашние животные (заполнив файл собаками, кошками, хомяками) и Вьючные животными заполнив файл Лошадьми, верблюдами и ослы), а затем объединить их. Просмотреть содержимое созданного файла. Переименовать файл, дав ему новое имя (Друзья человека). 
2. Создать директорию, переместить файл туда.
![2 задание](https://github.com/Zorrki/Control/Screens/blob/main/1_2.png?raw=true)
3. Подключить дополнительный репозиторий MySQL. Установить любой пакет из этого репозитория.
![3 задание](https://github.com/Zorrki/Control/Screens/blob/main/3.png?raw=true)
![3 задание](https://github.com/Zorrki/Control/Screens/blob/main/3_1.png?raw=true)
4. Установить и удалить deb-пакет с помощью dpkg.
![4 задание](https://github.com/Zorrki/Control/Screens/blob/main/4.png?raw=true)
![4 задание](https://github.com/Zorrki/Control/Screens/blob/main/4_1.png?raw=true)
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
6. Нарисовать [диаграмму](https://drive.google.com/file/d/1OpnFGyM6d6wxuNl3QNw0fpAk4WiFN5n4/view?usp=sharing), в которой есть класс родительский класс, домашние животные и вьючные животные, в составы которых в случае домашних животных войдут классы: собаки, кошки, хомяки, а в класс вьючные животные войдут: Лошади, верблюды и ослы).
![6 задание](https://github.com/Zorrki/Control/Screens/blob/main/6.png?raw=true)
7. В подключенном MySQL репозитории создать базу данных “Друзья человека”
```
CREATE DATABASE Human_friends;
```
8. Создать таблицы с иерархией из диаграммы в БД
```USE Human_friends;
CREATE TABLE animal_classes
(
  Id INT AUTO_INCREMENT PRIMARY KEY, 
  Class_name VARCHAR(20)
);

INSERT INTO animal_classes (Class_name)
VALUES ('вьючные'),
('домашние');  


CREATE TABLE ride_animals
(
    Id INT AUTO_INCREMENT PRIMARY KEY,
    Genus_name VARCHAR (20),
    Class_id INT,
    FOREIGN KEY (Class_id) REFERENCES animal_classes (Id) ON DELETE CASCADE ON UPDATE CASCADE
);

INSERT INTO ride_animals (Genus_name, Class_id)
VALUES ('Лошади', 1),
('Ослы', 1),  
('Верблюды', 1); 
    
CREATE TABLE home_animals
(
    Id INT AUTO_INCREMENT PRIMARY KEY,
    Genus_name VARCHAR (20),
    Class_id INT,
    FOREIGN KEY (Class_id) REFERENCES animal_classes (Id) ON DELETE CASCADE ON UPDATE CASCADE
);

INSERT INTO home_animals (Genus_name, Class_id)
VALUES ('Кошки', 2),
('Собаки', 2),  
('Хомяки', 2);
```
![8 задание](https://github.com/Zorrki/Control/Screens/blob/main/8_1.jpg?raw=true)

9. Заполнить низкоуровневые таблицы именами(животных), командами которые они выполняют и датами рождения
```CREATE TABLE cats 
(       
    Id INT AUTO_INCREMENT PRIMARY KEY, 
    Name VARCHAR(20), 
    Birthday DATE,
    Commands VARCHAR(50),
    Genus_id int,
    Foreign KEY (Genus_id) REFERENCES home_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE
);

INSERT INTO cats (Name, Birthday, Commands, Genus_id)
VALUES ('Стеша', '2013-03-12', 'кис-кис-кис', 1),
('Пёс', '2014-02-06', "фу!", 1), 
('Хакамада', '2014-02-06', "брысь!", 1),  
('Муся', '2015-11-11', "мяу!", 1); 

CREATE TABLE dogs 
(       
    Id INT AUTO_INCREMENT PRIMARY KEY, 
    Name VARCHAR(20), 
    Birthday DATE,
    Commands VARCHAR(50),
    Genus_id int,
    Foreign KEY (Genus_id) REFERENCES home_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE
);
INSERT INTO dogs (Name, Birthday, Commands, Genus_id)
VALUES ('Марта', '2020-10-11', 'ко мне, лежать, лапу, голос', 2),
('Ваня', '2021-06-08', "сидеть, лежать, лапу", 2),  
('Москвич', '2023-02-10', "сидеть, лежать, фу, место", 2);

CREATE TABLE hamsters 
(       
    Id INT AUTO_INCREMENT PRIMARY KEY, 
    Name VARCHAR(20), 
    Birthday DATE,
    Commands VARCHAR(50),
    Genus_id int,
    Foreign KEY (Genus_id) REFERENCES home_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE
);
INSERT INTO hamsters (Name, Birthday, Commands, Genus_id)
VALUES ('Сплинтер', '2020-10-12', '', 3),
('Бурый', '2021-03-12', "атака сверху", 3),  
('Хома', '2022-07-11', NULL, 3), 
('Малой', '2022-05-10', NULL, 3);

CREATE TABLE horses 
(       
    Id INT AUTO_INCREMENT PRIMARY KEY, 
    Name VARCHAR(20), 
    Birthday DATE,
    Commands VARCHAR(50),
    Genus_id int,
    Foreign KEY (Genus_id) REFERENCES ride_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE
);
INSERT INTO horses (Name, Birthday, Commands, Genus_id)
VALUES ('Гром', '2020-01-12', 'бегом, шагом', 1),
('Закат', '2017-03-12', "бегом, шагом, хоп", 1),  
('Байкал', '2016-07-12', "бегом, шагом, хоп, брр", 1), 
('Молния', '2020-11-10', "бегом, шагом, хоп", 1);

CREATE TABLE donkeys 
(       
    Id INT AUTO_INCREMENT PRIMARY KEY, 
    Name VARCHAR(20), 
    Birthday DATE,
    Commands VARCHAR(50),
    Genus_id int,
    Foreign KEY (Genus_id) REFERENCES ride_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE
);
INSERT INTO donkeys (Name, Birthday, Commands, Genus_id)
VALUES ('Первый', '2019-04-10', NULL, 2),
('Второй', '2020-03-12', "", 2),  
('Третий', '2021-07-12', "", 2), 
('Четвертый', '2022-12-10', NULL, 2);

CREATE TABLE camels 
(       
    Id INT AUTO_INCREMENT PRIMARY KEY, 
    Name VARCHAR(20), 
    Birthday DATE,
    Commands VARCHAR(50),
    Genus_id int,
    Foreign KEY (Genus_id) REFERENCES ride_animals (Id) ON DELETE CASCADE ON UPDATE CASCADE
);
INSERT INTO camels (Name, Birthday, Commands, Genus_id)
VALUES ('Горбатый', '2022-04-10', 'вернись', 3),
('Самец', '2019-03-12', "остановись", 3),  
('Сифон', '2015-07-12', "повернись", 3), 
('Борода', '2022-12-10', "улыбнись", 3);
``` 
![9 задание](https://github.com/Zorrki/Control/Screens/blob/main/9.jpg?raw=true)
![9 задание](https://github.com/Zorrki/Control/Screens/blob/main/9_1.jpg?raw=true)

10. Удалив из таблицы верблюдов, т.к. верблюдов решили перевезти в другой питомник на зимовку. Объединить таблицы лошади, и ослы в одну таблицу.
```SET SQL_SAFE_UPDATES = 0;
DELETE FROM camels;

SELECT Name, Birthday, Commands FROM horses
UNION SELECT  Name, Birthday, Commands FROM donkeys;
```
![10 задание](https://github.com/Zorrki/Control/Screens/blob/main/10.jpg?raw=true)

11. Создать новую таблицу “молодые животные” в которую попадут все животные старше 1 года, но младше 3 лет и в отдельном столбце с точностью до месяца подсчитать возраст животных в новой таблице
```CREATE TEMPORARY TABLE animals AS 
SELECT *, 'Лошади' as genus FROM horses
UNION SELECT *, 'Ослы' AS genus FROM donkeys
UNION SELECT *, 'Собаки' AS genus FROM dogs
UNION SELECT *, 'Кошки' AS genus FROM cats
UNION SELECT *, 'Хомяки' AS genus FROM hamsters;

CREATE TABLE yang_animal AS
SELECT Name, Birthday, Commands, genus, TIMESTAMPDIFF(MONTH, Birthday, CURDATE()) AS Age_in_month
FROM animals WHERE Birthday BETWEEN ADDDATE(curdate(), INTERVAL -3 YEAR) AND ADDDATE(CURDATE(), INTERVAL -1 YEAR);
 
SELECT * FROM yang_animal;
```
![11 задание](https://github.com/Zorrki/Control/Screens/blob/main/11.jpg?raw=true)

12. Объединить все таблицы в одну, при этом сохраняя поля, указывающие на прошлую принадлежность к старым таблицам.
```SELECT h.Name, h.Birthday, h.Commands, pa.Genus_name, ya.Age_in_month 
FROM horses h
LEFT JOIN yang_animal ya ON ya.Name = h.Name
LEFT JOIN ride_animals pa ON pa.Id = h.Genus_id
UNION 
SELECT d.Name, d.Birthday, d.Commands, pa.Genus_name, ya.Age_in_month 
FROM donkeys d 
LEFT JOIN yang_animal ya ON ya.Name = d.Name
LEFT JOIN ride_animals pa ON pa.Id = d.Genus_id
UNION
SELECT c.Name, c.Birthday, c.Commands, ha.Genus_name, ya.Age_in_month 
FROM cats c
LEFT JOIN yang_animal ya ON ya.Name = c.Name
LEFT JOIN home_animals ha ON ha.Id = c.Genus_id
UNION
SELECT d.Name, d.Birthday, d.Commands, ha.Genus_name, ya.Age_in_month 
FROM dogs d
LEFT JOIN yang_animal ya ON ya.Name = d.Name
LEFT JOIN home_animals ha ON ha.Id = d.Genus_id
UNION
SELECT hm.Name, hm.Birthday, hm.Commands, ha.Genus_name, ya.Age_in_month 
FROM hamsters hm
LEFT JOIN yang_animal ya ON ya.Name = hm.Name
LEFT JOIN home_animals ha ON ha.Id = hm.Genus_id;
```
![12 задание](https://github.com/Zorrki/Control/Screens/blob/main/12.jpg?raw=true)

13.  Создать [класс с Инкапсуляцией](https://github.com/Zorrki/Control/tree/main/Program/src/Model) методов и наследованием по диаграмме

14.  Написать [программу, имитирующую работу реестра домашних животных](https://github.com/Zorrki/Control/tree/main/Program/). 
В программе должен быть реализован следующий функционал:  
	14.1 Завести новое животное  
	14.2 определять животное в правильный класс  
	14.3 увидеть список команд, которое выполняет животное  
	14.4 обучить животное новым командам  
	14.5 Реализовать навигацию по меню

15. Создайте [класс Счетчик](https://github.com/Zorrki/Control/tree/main/Program/src/Controller), у которого есть метод add(), увеличивающий̆ значение внутренней int переменной на 1 при нажатии “Завести новое животное”. Сделайте так, чтобы с объектом такого типа можно было работать в блоке try-with-resources. Нужно бросить исключение, если работа с объектом типа счетчик была не в ресурсном try и/или ресурс остался открыт. Значение считать в ресурсе try, если при заведения животного заполнены все поля.