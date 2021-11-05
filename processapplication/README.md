Björn Scheppler, 20.9.2021

# Incident Management Process Application
TODO

## Vorbereitungen, Deployment und Start
1. Wenn man die **Enterprise Edition** von Camunda verwenden will, benötigt man die Zugangsdaten zum Nexus Repository und eine gültige Lizenz. Wie man diese "installiert", steht in den Kommentaren im pom.xml.
2. **Erstmalig** oder bei Problemen ein `mvn clean install` durchführen
3. Bei Änderungen am POM-File oder bei **(Neu)kompilierungsbedarf** genügt ein `mvn install`
4. Für den **Start** ist ein `java -jar .\target\NAME DES JAR-FILES.jar` erforderlich. Dabei wird Tomcat gestartet, die Datenbank erstellt/hochgefahren, Camunda entsprechend den Eigenschaften (application.properties) hochgefahren.
5. Das **Beenden** geschieht mit **CTRL+C**
6. Falls man die bestehenden **Prozessdaten nicht mehr benötigt** und die Datenbank inzwischen recht angewachsen ist, genügt es, die Datei h2-db.mv.db im Wurzelverzeichnis des Projekts zu löschen.

## Grundlegende Nutzung
1. http://localhost:8081 aufrufen
2. Anmelden mit Benutzername und Passwort a

## Fortgeschrittene Nutzung (H2 Console)
1. Um auf die Datenbankverwaltungs-Umgebung zuzugreifen, http://localhost:8081/console eingeben.
2. Anmeldung über:
    1. Benutzername sa
    2. Passwort: leer lassen
    3. URL jdbc:h2:./h2-db

## Fortgeschrittene Nutzung (Zugriff über REST)
Die Engine kann auch per REST API gesteuert werden. Wegen Spring Boot ist die URL für die REST API minimal anders als in der Dokumentation beschrieben. Sie ist: http://localhost:8081/engine-rest/. So gibt z.B. http://localhost:8081/engine-rest/engine den Namen der Engine (default) zurück.