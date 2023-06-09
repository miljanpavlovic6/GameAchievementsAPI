# GameAchievementsAPI -> related to project https://github.com/miljanpavlovic6/apiGame

Installing Java 8 on CentOS 7
--------------------------------------------------------------------------------------------------------------
yum -y update <br />
yum install java-1.8.0-openjdk <br />
java -version <br />

Install MariaDB
--------------------------------------------------------------------------------------------------------------
sudo yum update -y <br />
sudo yum install -y mariadb-server <br />
sudo systemctl enable mariadb <br />
sudo systemctl start mariadb <br />
sudo mysql_secure_installation (for pass type 'root') <br />
mysql -uroot -p; <br />
show databases; <br />

--------------------------------------------------------------------------------------------------------------
CREATE DATABASE `development` /*!40100 DEFAULT CHARACTER SET utf8 */; 
CREATE TABLE `game` (
  `id` bigint(20) NOT NULL PRIMARY KEY,
  `displayname` varchar(255) NOT NULL,
  `gameid` varchar(255) NOT NULL UNIQUE KEY
) ENGINE=InnoDB DEFAULT CHARSET=utf8; <br />

CREATE TABLE `achievement` (
  `id` bigint(20) NOT NULL PRIMARY KEY,
  `achievementid` varchar(255) NOT NULL UNIQUE KEY,
  `game_id` bigint(20) NOT NULL,
  `displayname` varchar(100) NOT NULL,
  `description` varchar(500) NOT NULL,
  `icon` varchar(255) DEFAULT NULL,
  `displayorder` int(11) DEFAULT NULL,
  `created` datetime(6) NOT NULL,
  `updated` datetime(6) NOT NULL,
  CONSTRAINT FOREIGN KEY (`game_id`) REFERENCES `game` (`id`)
)ENGINE=InnoDB DEFAULT CHARSET=utf8; <br />

--------------------------------------------------------------------------------------------------------------
INSERT INTO `development`.`game`(`id`,`displayname`,`gameid`)VALUES(1,'Ninja Warriot Pro Deluxe Plus','QQtdv4owdT'); <br />

INSERT INTO `development`.`game`(`id`,`displayname`,`gameid`)VALUES(2,'Call of Duty','QQqqqqwwww'); <br />

INSERT INTO `development`.`game`(`id`,`displayname`,`gameid`)VALUES(3,'Crysis','wwwQQQSSS'); <br />

INSERT INTO `development`.`game`(`id`,`displayname`,`gameid`)VALUES(4,'Cobra','qwerQQQSSS'); <br />

INSERT INTO `development`.`achievement`(`id`,`achievementid`,`game_id`, `displayname`,`description`, `icon`, `displayorder`, `created`,`updated`)
VALUES(1,'21',1,'High_Flyer', 'Win 49 games by only using your sword.','www.gom.com',1, '2008-7-04','2008-7-04'); <br />

INSERT INTO `development`.`achievement`(`id`,`achievementid`,`game_id`, `displayname`,`description`, `icon`, `displayorder`, `created`,`updated`)
VALUES(2,'gfds',1,'Causal_Gamer', 'Win 1000 games. You need to defeat a giant cookie.','www.gom.com',2, '2008-7-04','2008-7-04'); <br />

INSERT INTO `development`.`achievement`(`id`,`achievementid`,`game_id`, `displayname`,`description`, `icon`, `displayorder`, `created`,`updated`)
VALUES(3,'125yhy',1,'Raze_the_Roof', 'I dont think robots will ever be able to automate achievement names, which is kind of weird because robots are able to automate a lot of other things that seem much more difficult.','www.gom.com',3, '2008-7-04','2008-7-04'); <br />

--------------------------------------------------------------------------------------------------------------
DOWNLOAD Spring appp

git clone https://github.com/miljanpavlovic6/GameAchievementsAPI.git <br />
cd GameAchievementsAPI <br />
chmod 777 gameApi.jar <br />
java -jar gameApi.jar $ //start in detach mode <br />
Go to browser and put <ipaddress>:8082/find/21 <br />
  API details from AchievementController: <br />
  ![image](https://github.com/miljanpavlovic6/GameAchievementsAPI/assets/47641359/25b4698a-9744-4ac1-80b3-8c7490f86f85)

