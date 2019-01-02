# Native C++ Beispiele mit dem SonarQube C++ plugin (Community)

Dieses Repository beinhaltet einige C++ Visual Studio-Projekte. An diesen Projekten zeige ich wie man auch C++-Projekte mit der statischen Code-Analyse managen und auswerten kann.

Außerdem können diese Projekte als Basis für Test-Szenarien genommen werden, da diese bereits funktionieren. Dabei spielt es überhaupt keine Rolle ob man damit sich damit einarbeiten oder ein Issue beschreiben möchte.

Für alle diese Projekte werden entsprechende sonar-project.properties-Datei zur Verfügung gestellt und in der jeweiligen README die besonderheiten beschrieben.

Die Einstellungen in den `sonar-project.properties` werden in den Dateien selbst ausführlich beschrieben.

# Voraussetzungen
## Schritt 1 - Donwload & Installation
### Option 1: SonarQube auf lokalem System
- [SonarQube installiert/eingerichtet](https://docs.sonarqube.org/latest/setup/get-started-2-minutes/)
- C++ plugin (Community)  - [Install the plugin](https://github.com/SonarOpenCommunity/sonar-cxx/wiki/Installation)

### Option 2: SonarQube als Docker-Container
In der Anleitung [Installation into Docker Sonarqube Image](https://github.com/SonarOpenCommunity/sonar-cxx/wiki/Installation-into-Docker-Sonarqube-Image) sind die Schritte aufgeführt.

**Hinweis:** Es zeigt noch auf eine alte Version, deswegen bitte unbedingt die URL zu der neusten jar-Datei angeben.

## Schritt 2 - C++ (Community)-Quality Profiles aktivieren
- [Quality Profiles aktivieren](https://github.com/SonarOpenCommunity/sonar-cxx/wiki/Activate-quality-rules)

## Schritt 3 - SonarQube Scanner
- Sonar Scanner nach [Anleitung](https://docs.sonarqube.org/display/SCAN/Analyzing+with+SonarQube+Scanner) herunterladen 

## Schritt 3 - Hilfreich
- MSBUILD in PATH-Umgebungsvariable hinzufügen
## Aktuelle Projekte
Hier bereits einige Projekte:
- SimpleCpp (einfachstes C++-Programm)
- IncludeCpp (nutzt ein Include)

