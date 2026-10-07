# Windows Commandline - Zusätzliche Übungen mit Lösungen

Bearbeite jede Aufgabe zuerst selbst. Die Lösungen sind auf GitHub ausklappbar. Alle Übungen werden unter `%USERPROFILE%\cmd-training` ausgeführt.

### Übung 1: Orientierung

Wechsle in den Trainingsordner, zeige den aktuellen Pfad und liste den Inhalt in Kurzform auf.

<details>
<summary>Lösung anzeigen</summary>

```cmd
cd /d %USERPROFILE%\cmd-training
cd
dir /b
```

</details>

### Übung 2: Projektstruktur erstellen

Erstelle die Ordnerstruktur `kursprojekt` mit den Unterordnern `docs`, `src` und `tests`. Zeige danach die gesamte Struktur an.

<details>
<summary>Lösung anzeigen</summary>

```cmd
cd /d %USERPROFILE%\cmd-training
mkdir kursprojekt
cd kursprojekt
mkdir docs
mkdir src
mkdir tests
dir /s
```

</details>

### Übung 3: Textdatei erzeugen

Erstelle in `kursprojekt` eine Datei `README.txt`. Die erste Zeile soll `Mein erstes Commandline-Projekt` und die zweite Zeile deinen Namen enthalten. Zeige den Inhalt an.

<details>
<summary>Lösung anzeigen</summary>

```cmd
cd /d %USERPROFILE%\cmd-training\kursprojekt
echo Mein erstes Commandline-Projekt > README.txt
echo Name: Bob >> README.txt
type README.txt
```

Ersetze `Bob` durch deinen Namen.

</details>

### Übung 4: Datei kopieren

Kopiere `README.txt` nach `docs`. Die Kopie soll `anleitung.txt` heißen. Kontrolliere ihren Inhalt.

<details>
<summary>Lösung anzeigen</summary>

```cmd
cd /d %USERPROFILE%\cmd-training\kursprojekt
copy README.txt docs\anleitung.txt
type docs\anleitung.txt
```

</details>

### Übung 5: Umbenennen und verschieben

Erstelle in `src` die Datei `programm.txt` mit dem Text `Hallo Programmierung`. Benenne sie in `main.txt` um, verschiebe sie nach `tests` und kontrolliere das Ergebnis.

<details>
<summary>Lösung anzeigen</summary>

```cmd
cd /d %USERPROFILE%\cmd-training\kursprojekt
echo Hallo Programmierung > src\programm.txt
ren src\programm.txt main.txt
move src\main.txt tests\main.txt
dir src
dir tests
type tests\main.txt
```

</details>

### Übung 6: Platzhalter einsetzen

Erstelle die Dateien `eins.txt`, `zwei.txt`, `drei.txt` und `ausgabe.log`. Zeige anschließend nur die `.txt`-Dateien an.

<details>
<summary>Lösung anzeigen</summary>

```cmd
cd /d %USERPROFILE%\cmd-training\kursprojekt
echo Datei 1 > eins.txt
echo Datei 2 > zwei.txt
echo Datei 3 > drei.txt
echo Protokoll > ausgabe.log
dir *.txt
```

Der Platzhalter `*` steht für eine beliebige Zeichenfolge.

</details>

### Übung 7: Ausgabe umleiten

Speichere die kurze Ordnerauflistung in `dateiliste.txt`. Zeige die Datei an und ergänze die Zeile `Ende der Liste`.

<details>
<summary>Lösung anzeigen</summary>

```cmd
cd /d %USERPROFILE%\cmd-training\kursprojekt
dir /b > dateiliste.txt
type dateiliste.txt
echo Ende der Liste >> dateiliste.txt
type dateiliste.txt
```

`>` erzeugt oder überschreibt eine Datei. `>>` hängt Text an.

</details>

### Übung 8: Pfad mit Leerzeichen

Erstelle den Ordner `Mein Projekt`, wechsle hinein und lege dort `info.txt` an. Wechsle danach wieder eine Ebene nach oben.

<details>
<summary>Lösung anzeigen</summary>

```cmd
cd /d %USERPROFILE%\cmd-training
mkdir "Mein Projekt"
cd "Mein Projekt"
echo Ordner mit Leerzeichen > info.txt
type info.txt
cd ..
```

</details>

### Übung 9: Einen Fehler untersuchen

Führe `type nicht-vorhanden.txt` aus. Ermittle die Ursache, prüfe vorhandene Dateien und korrigiere die Situation.

<details>
<summary>Lösung anzeigen</summary>

Die Datei existiert noch nicht. Die genaue Fehlermeldung hängt von der Windows-Sprache ab.

```cmd
dir /b
echo Jetzt existiert die Datei > nicht-vorhanden.txt
type nicht-vorhanden.txt
```

</details>

### Übung 10: Befehle verketten

Erstelle mit einer einzigen Eingabe den Ordner `kette`, wechsle hinein und erzeuge `erfolg.txt`. Jeder Schritt soll nur ausgeführt werden, wenn der vorherige erfolgreich war.

<details>
<summary>Lösung anzeigen</summary>

```cmd
cd /d %USERPROFILE%\cmd-training && mkdir kette && cd kette && echo Erfolgreich > erfolg.txt && type erfolg.txt
```

`&&` startet den nächsten Befehl nur, wenn der vorherige erfolgreich war.

</details>


### Übung 11: Kontrolliert aufräumen

Lösche ausschließlich den in Übung 10 erstellten Ordner `kette`. Prüfe vorher den aktuellen Pfad und den Ordnerinhalt.

<details>
<summary>Lösung anzeigen</summary>

```cmd
cd /d %USERPROFILE%\cmd-training
cd
dir /b
rmdir /s kette
```

Bestätige die Rückfrage nur, wenn der angezeigte Ordner tatsächlich `kette` ist.

</details>


### Lernkontrolle

1. Was ist der Unterschied zwischen `copy` und `move`?
2. Wozu dienen Anführungszeichen bei Pfaden?
3. Was bewirken `>` und `>>`?
4. Wann wird bei einer `&&`-Kette der nächste Befehl ausgeführt?
5. Warum soll vor `rmdir /s` der aktuelle Pfad geprüft werden?

<details>
<summary>Lösungen anzeigen</summary>

1. `copy` erstellt eine Kopie; `move` verschiebt eine Datei oder einen Ordner.
2. Sie fassen einen Pfad mit Leerzeichen als ein Argument zusammen.
3. `>` erzeugt oder überschreibt eine Datei; `>>` hängt Text an.
4. Nur wenn der vorherige Befehl erfolgreich war.
5. Ein falscher Pfad kann zum Löschen unerwünschter Daten führen.

</details>

## Weiterführende Quellen

- [Windows-Befehle auf Microsoft Learn](https://learn.microsoft.com/de-de/windows-server/administration/windows-commands/windows-commands)
- [Dokumentation zu cmd.exe](https://learn.microsoft.com/de-de/windows-server/administration/windows-commands/cmd)

---

## Aufräumen nach dem Training

Wechsle zuerst aus dem Trainingsordner heraus und lösche danach ausschließlich den Übungsordner:

```cmd
cd /d %USERPROFILE%
rmdir /s cmd-training
```

Windows fragt vor dem Löschen nach einer Bestätigung.
