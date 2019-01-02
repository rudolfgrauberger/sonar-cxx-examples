# Include C++
Dieses Projekt erweitert das "SimpleCpp" darum, dass Include-Verzeichnisse benötigt werden.


## Versuch
Mit dem nachfolgendem Befehl wird das Projekt mit MSBUILD mit der Konfiguration "Release" kompiliert und die Ausgabe zusätzlich in eine Datei geloggt. Hier nehmen wir jetzt mal bewusst die gleichen Einstellungen für den Logger wie bei dem SimpleCpp-Projekt.

```PowerShell
PS > cd <project root>\IncludeCpp
PS > MSBuild.exe .\IncludeCpp.vcxproj /t:rebuild /p:Configuration=Release /fileLogger "/fileLoggerParameters:LogFile=buildlog.log;Verbosity=normal;Encoding=UTF-8"
```

Mit dem nachfolgendem Befehl wird der Sonner-Scanner ausgeführt und das Ergebnis auf dem angegebenen Host (`sonar.host.url`) und dem Projekt-Schlüssel (`sonar.projectKey`) hochgeladen.

```PowerShell
PS > sonar-scanner
```

Jetzt erhalten wir aber

```PowerShell
...
WARN: Preprocessor: 1 include directive error(s). This is only relevant if parser creates syntax errors. The preprocessor searches for include files in the with 'sonar.cxx.includeDirectories' defined directories and order.
INFO: Turn debug info on to get more details (sonar-scanner -X -Dsonar.verbose=true ...).
INFO: Task total time: 13.333 s
INFO: ------------------------------------------------------------------------
INFO: EXECUTION SUCCESS
INFO: ------------------------------------------------------------------------
INFO: Total time: 16.174s
INFO: Final Memory: 22M/313M
INFO: ------------------------------------------------------------------------
```

## Korrektur
Man kann natürlich wie in der Warnung angegeben die Include-Verzeichnisse setzen, allerdings ist das nicht schön (da absolute Pfade angegeben werden müssten) und auch überhaupt nicht notwendig.

Wir haben ja bereit in der Visual Studio Projektdatei (.vcxproj) alles was zum Kompilieren benötigt wird und dazu gehören auch Include-Verzeichnisse und Defines.

MSBuild ist in der Lage diese Informationen als Ausgabe auszugeben, allerdings erst ab der **Verbosity** `detailed`. Aus diesem Grund müssen wir beim Aufruf von MSBuild `normal` durch `detailed` ersetzen.

```PowerShell
PS > cd <project root>\IncludeCpp
PS > MSBuild.exe .\IncludeCpp.vcxproj /t:rebuild /p:Configuration=Release /fileLogger "/fileLoggerParameters:LogFile=buildlog.log;Verbosity=detailed;Encoding=UTF-8"
```

Da der Sonar-Scanner auf der Basis der Log-Datei arbeitet, müssen wir diesen jetzt nochmal ausführen:

```PowerShell
PS > sonar-scanner
```

Jetzt gibt es keine Warnung mehr.

**Hinweis:** Wenn bei dem Projekt auf dem Host (`sonar.host.url`) keine **Code Smells** angezeigt werden, dann wurde vergessen das eigene C++ (Community) Quality Profile als **Default** zu setzen.