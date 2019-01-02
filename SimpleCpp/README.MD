# Simple C++
Das Projekt ist so minimalistisch, dass nichmals Defines und Includes angegeben/ausgelesen werden müssen. 


Mit dem nachfolgendem Befehl wird das Projekt mit MSBUILD mit der Konfiguration "Release" kompiliert und die Ausgabe zusätzlich in eine Datei geloggt.
```PowerShell
PS > cd <project root>\simple
PS > MSBuild.exe .\SimpleCpp.vcxproj /t:rebuild /p:Configuration=Release /fileLogger "/fileLoggerParameters:LogFile=buildlog.log;Verbosity=normal;Encoding=UTF-8"
```

Mit dem nachfolgendem Befehl wird der Sonner-Scanner ausgeführt und das Ergebnis auf dem angegebenen Host (`sonar.host.url`) und dem Projekt-Schlüssel (`sonar.projectKey`) hochgeladen.

```PowerShell
PS > sonar-scanner
```