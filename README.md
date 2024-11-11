необходимо добавить плагин war то есть секцию :

plugins {
id ‘war’
}

из-за этого меняется жизненный цикл , то есть при вызове gradle assemble  перед задачей assemble идет задача war , то есть пропускается задача jar (сборка jar-архива)

добавим зависимость compileOnly "jakarta.servlet:jakarta.servlet-api:5.0.0"
так как  jakarta.servlet-api будет в tomcat

данная зависимость в tomcat 10 , следовательно нам надо будем установить tomcat 10

сборка архива  : gradle assemble

https://tomcat.apache.org/download-10.cgi

установка tomcat : скачать zip архив и разархивировать

/Users/tmikhaylovskaya/Downloads/apache-tomcat-10.1.31

надо положить наш war-файл в директорию /apache-tomcat-10.1.31/webapps

запуск tomcat
дать права на запуск всех sh скриптов
chmod -R 777 ~/Downloads/apache-tomcat-10.1.31/bin
~/Downloads/apache-tomcat-10.1.31/bin/startup.sh

проверка запуска tomcat - идем в браузер http://localhost:8080

запущенный tomcat сам разархивирует war-файл

http://localhost:8080/dmdev/index.html

http://localhost:8080/dmdev

http://localhost:8080/dmdev/users

останов tomcat
~/Downloads/apache-tomcat-10.1.31/bin/shutdown.sh
