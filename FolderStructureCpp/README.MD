# Folder Structure C++
In diesem Projekt befinden sich die Quelltext-Dateien nicht direkt in dem Projekt-Hauptverzeichnis.


## Versuch
Mit dem nachfolgendem Befehl wird das Projekt mit MSBUILD mit der Konfiguration "Release" kompiliert und die Ausgabe zusätzlich in eine Datei geloggt. 

```PowerShell
PS > cd <project root>\FolderStructureCpp
PS > MSBuild.exe .\FolderStructureCpp.vcxproj /t:rebuild /p:Configuration=Release /fileLogger "/fileLoggerParameters:LogFile=buildlog.log;Verbosity=detailed;Encoding=UTF-8"
```

Mit dem nachfolgendem Befehl wird der Sonner-Scanner ausgeführt und das Ergebnis auf dem angegebenen Host (`sonar.host.url`) und dem Projekt-Schlüssel (`sonar.projectKey`) hochgeladen.

```PowerShell
PS > sonar-scanner
```

**Hinweis:** Wenn bei dem Projekt auf dem Host (`sonar.host.url`) keine **Code Smells** angezeigt werden, dann wurde vergessen das eigene C++ (Community) Quality Profile als **Default** zu setzen.