Apache Tomcat Image mit Debug-Modus
==================================
Image basiert auf dem offiziellen Tomcat -Image und ist um Debug-Einstellungen erweitert.

Java-Version: **8.0.x**

Tomcat- Version: **8.0.41**

Erweiterungen:
----------------
* Start-Routine **catalina.sh** ist erweitert und ersetzt.
```
JAVA_OPTS="$JAVA_OPTS -Xdebug -Xrunjdwp:transport=dt_socket,address=8000,server=y,suspend=n"
```
* Dockerfile
```
....
ADD bin/* ${CATALINA_HOME}/bin/
RUN chmod +x ${CATALINA_HOME}/bin/*.sh

EXPOSE 8000
EXPOSE 8080

CMD ["catalina.sh", "run"]
```

Image erstellen:
```
docker build -t tomcat-debug .
```

Links
-----
* Tomcat dockerHub -- https://hub.docker.com/_/tomcat/
* Tomcat FAQ/Deployment -- https://wiki.apache.org/tomcat/FAQ/Developing
