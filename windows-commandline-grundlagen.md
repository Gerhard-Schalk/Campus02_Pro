# Windows Commandline Grundlagen

Nach diesem kurzen Training können Sie:

- eine Commandline öffnen und grundlegende Befehle ausführen,
- sich im Dateisystem orientieren,
- Ordner und Textdateien erstellen, anzeigen, kopieren, verschieben und löschen,
- einfache Unterschiede zwischen Windows `cmd`, Linux und macOS erkennen,
- die Commandline als Grundlage für spätere Programmierwerkzeuge nutzen.

---

## 1. Was ist eine Commandline?

Eine **Commandline**, auch **Befehlszeile**, **Konsole**, **Shell** oder **Terminal** genannt, ist eine textbasierte Schnittstelle zum Computer. Statt Ordner und Programme mit der Maus auszuwählen, gibt man Befehle über die Tastatur ein.

Beispiel:

```cmd
dir
```

Der Computer führt den Befehl aus und zeigt das Ergebnis als Text an.

### Warum ist die Commandline für die Programmierung wichtig?

Viele Entwicklungswerkzeuge werden über die Commandline verwendet, zum Beispiel:

- Compiler und Build-Werkzeuge,
- Git,
- C#, .NET, Java oder Node.js,
- Paketmanager,
- Test- und Analysewerkzeuge,
- Skripte zur Automatisierung wiederkehrender Aufgaben.

Ein typischer Befehl besteht aus einem **Befehlsnamen**, optionalen **Optionen** und **Argumenten**:

```text
Befehl  Option  Argument
  dir     /b    *.txt
```

In Windows zeigt `dir /b *.txt` alle Textdateien im aktuellen Ordner in einer einfachen Liste an.

> **Hinweis:** Windows bietet mehrere Shells. Dieses Training verwendet bewusst die klassische Eingabeaufforderung `cmd.exe`. PowerShell verwendet teilweise andere Befehle und eine andere Syntax.

---

## 2. Eingabeaufforderung öffnen

1. Drücke `Windows-Taste + R`.
2. Gib `cmd` ein.
3. Drücke `Enter`.

Die aktuelle Eingabezeile kann beispielsweise so aussehen:

```text
C:\Users\Vorname>
```

Der Text vor `>` zeigt das aktuelle Verzeichnis. Hinter `>` wird der nächste Befehl eingegeben.

### Wichtige Bedienungstipps

- `Enter`: Befehl ausführen
- `Tab`: Datei- oder Ordnernamen vervollständigen
- `Pfeil nach oben`: vorherigen Befehl erneut anzeigen
- `Ctrl + C`: laufenden Befehl abbrechen
- Anführungszeichen verwenden, wenn ein Pfad Leerzeichen enthält:

```cmd
cd "Mein Ordner"
```

---

## 3. Vergleich der wichtigsten Befehle

Linux und macOS verwenden üblicherweise sehr ähnliche Unix-Shell-Befehle. Bei Linux und macOS wird Groß- und Kleinschreibung bei Datei- und Ordnernamen normalerweise unterschieden. Windows behandelt sie üblicherweise gleich.

| Nr. | Aufgabe | Windows `cmd` | Linux/macOS |
|---:|---|---|---|
| 1 | Hilfe anzeigen | `help`, `befehl /?` | `man befehl`, `befehl --help` |
| 2 | Anzeige leeren | `cls` | `clear` |
| 3 | Aktuellen Ordner anzeigen/wechseln | `cd`, `cd ordner` | `pwd`, `cd ordner` |
| 4 | Dateien und Ordner auflisten | `dir` | `ls` |
| 5 | Ordner erstellen | `mkdir` | `mkdir` |
| 6 | Text ausgeben oder Datei erzeugen | `echo` | `echo` |
| 7 | Textdatei anzeigen | `type` | `cat` |
| 8 | Datei kopieren | `copy` | `cp` |
| 9 | Datei verschieben/umbenennen | `move`, `ren` | `mv` |
| 10 | Datei oder Ordner löschen | `del`, `rmdir` | `rm`, `rmdir` |

> **Vorsicht:** Gelöschte Dateien werden bei `del` beziehungsweise `rm` normalerweise nicht in den Papierkorb verschoben. Führe die Übungen deshalb nur im eigens angelegten Trainingsordner aus.

---

## 4. Gemeinsame Vorbereitung

Lege einen sicheren Übungsordner in deinem Benutzerprofil an:

```cmd
cd /d %USERPROFILE%
mkdir cmd-training
cd cmd-training
```

Kontrolliere anschließend den aktuellen Pfad:

```cmd
cd
```

Alle folgenden Übungen werden in diesem Ordner ausgeführt.

---

### Was bedeutet `%USERPROFILE%`?

`%USERPROFILE%` ist eine **Windows-Umgebungsvariable**. Sie enthält den Pfad zum persönlichen Benutzerverzeichnis des aktuell angemeldeten Benutzers.

```cmd
echo %USERPROFILE%
```

Die Ausgabe könnte beispielsweise so aussehen:

```text
C:\Users\Vorname
```

Dadurch können Befehle unabhängig vom konkreten Benutzernamen geschrieben werden:

```cmd
cd /d %USERPROFILE%
```

statt beispielsweise:

```cmd
cd /d C:\Users\Vornamme
```

Das ist besonders für Skripte und Programme hilfreich, weil der Benutzername nicht fest im Befehl eingetragen werden muss.

> **Merke:** In `cmd.exe` werden Umgebungsvariablen zwischen zwei `%`-Zeichen geschrieben. Windows ersetzt `%USERPROFILE%` beim Ausführen durch den aktuellen Wert der Variable.

Alle verfügbaren Umgebungsvariablen können mit folgendem Befehl angezeigt werden:

```cmd
set
```

## 5. Zehn wichtige Befehle mit Übungen

### 1. `help` und `/?` – Hilfe anzeigen

`help` zeigt eine Übersicht interner Windows-Befehle. Mit `/?` erhält man Hilfe zu einem bestimmten Befehl.

```cmd
help
```

```cmd
dir /?
```

**Linux/macOS:**

```bash
man ls
```

oder:

```bash
ls --help
```

**Mini-Aufgabe:** Suche in der Hilfe von `dir` nach der Option für eine einfache Auflistung. Probiere danach:

```cmd
dir /b
```

---

### 2. `cls` – Anzeige leeren

`cls` leert den sichtbaren Inhalt der Eingabeaufforderung. Dateien oder Befehle werden dadurch nicht gelöscht.

```cmd
cls
```

**Linux/macOS:**

```bash
clear
```

**Mini-Aufgabe:** Führe zuerst `help` und danach `cls` aus.

---

### 3. `cd` – Aktuellen Ordner anzeigen oder wechseln

Ohne Argument zeigt `cd` unter Windows den aktuellen Ordner an.

```cmd
cd
```

Zuerst einen Beispielordner anlegen und anschließend hineinwechseln:

```cmd
mkdir beispiele
cd beispiele
```

Eine Ebene nach oben wechseln:

```cmd
cd ..
```

Direkt in den Trainingsordner wechseln:

```cmd
cd /d %USERPROFILE%\cmd-training
```

`/d` wechselt bei Bedarf gleichzeitig das Laufwerk und den Ordner.

**Linux/macOS:**

```bash
pwd
cd beispiele
cd ..
```

**Mini-Aufgabe:** Wechsle mit `cd ..` eine Ebene nach oben und danach wieder in `cmd-training`.

---

### 4. `dir` – Inhalt eines Ordners anzeigen

```cmd
dir
```

Nur Namen anzeigen:

```cmd
dir /b
```

Nur Textdateien anzeigen:

```cmd
dir *.txt
```

**Linux/macOS:**

```bash
ls
ls -l
ls *.txt
```

**Mini-Aufgabe:** Vergleiche die Ausgabe von `dir` und `dir /b`.

---

### 5. `mkdir` – Ordner erstellen

```cmd
mkdir beispiele
```

Mehrere verschachtelte Ordner erstellen:

```cmd
mkdir projekt\src
```

**Linux/macOS:**

```bash
mkdir beispiele
mkdir -p projekt/src
```

**Mini-Aufgabe:** Erstelle die Ordner `daten` und `backup`.

```cmd
mkdir daten
mkdir backup
```

---

### 6. `echo` – Text ausgeben und Dateien erzeugen

Text auf dem Bildschirm ausgeben:

```cmd
echo Hallo Commandline!
```

Text in eine neue Datei schreiben:

```cmd
echo Mein erstes Beispiel > notiz.txt
```

Eine weitere Zeile anhängen:

```cmd
echo Zweite Zeile >> notiz.txt
```

- `>` erstellt oder überschreibt eine Datei.
- `>>` hängt Text an eine Datei an.

**Linux/macOS:** Die gezeigten `echo`-Beispiele funktionieren in der Regel genauso.

**Mini-Aufgabe:** Erstelle `name.txt` mit deinem Namen und füge eine zweite Zeile mit deinem Lieblingsprogramm hinzu.

---

### 7. `type` – Inhalt einer Textdatei anzeigen

```cmd
type notiz.txt
```

**Linux/macOS:**

```bash
cat notiz.txt
```

**Mini-Aufgabe:** Zeige den Inhalt von `name.txt` an.

```cmd
type name.txt
```

---

### 8. `copy` – Datei kopieren

```cmd
copy notiz.txt backup\notiz-kopie.txt
```

Prüfe das Ergebnis:

```cmd
dir backup
```

**Linux/macOS:**

```bash
cp notiz.txt backup/notiz-kopie.txt
```

**Mini-Aufgabe:** Kopiere `name.txt` in den Ordner `backup`.

```cmd
copy name.txt backup\name.txt
```

---

### 9. `move` und `ren` – Datei verschieben oder umbenennen

Eine Datei in einen anderen Ordner verschieben:

```cmd
move notiz.txt daten\notiz.txt
```

Eine Datei im aktuellen Ordner umbenennen:

```cmd
ren name.txt teilnehmer.txt
```

**Linux/macOS:** Für beide Aufgaben wird `mv` verwendet.

```bash
mv notiz.txt daten/notiz.txt
mv name.txt teilnehmer.txt
```

**Mini-Aufgabe:** Verschiebe `teilnehmer.txt` in den Ordner `daten`.

```cmd
move teilnehmer.txt daten\teilnehmer.txt
```

---

### 10. `del` und `rmdir` – Dateien und Ordner löschen

Eine Datei löschen:

```cmd
del backup\name.txt
```

Einen leeren Ordner löschen:

```cmd
mkdir leer
rmdir leer
```

Einen Ordner samt Inhalt löschen:

```cmd
rmdir /s /q backup
```

- `/s` löscht auch Unterordner und Dateien.
- `/q` unterdrückt die Sicherheitsabfrage.

**Linux/macOS:**

```bash
rm backup/name.txt
rmdir leer
rm -r backup
```

**Mini-Aufgabe:** Zeige zuerst den Inhalt von `backup` an und lösche den Ordner anschließend.

```cmd
dir backup
rmdir /s /q backup
```

> **Sicherheitsregel:** Prüfe vor jedem Löschbefehl mit `cd` und `dir`, ob du dich im richtigen Ordner befindest. Verwende bei echten Projekten `/q` erst, wenn du die Wirkung sicher verstanden hast.

---



## 7. Verständnisfragen

1. Mit welchem Befehl wird der aktuelle Ordner angezeigt?
2. Was ist der Unterschied zwischen `>` und `>>`?
3. Wie wechselt man in den übergeordneten Ordner?
4. Welcher Windows-Befehl entspricht ungefähr `ls` unter Linux und macOS?
5. Warum sollte man vor `del` oder `rmdir /s` den aktuellen Pfad prüfen?
6. Wie erhält man Hilfe zum Befehl `copy`?

<details>
<summary>Lösungen anzeigen</summary>

1. `cd`
2. `>` erstellt oder überschreibt eine Datei, `>>` hängt Text an.
3. `cd ..`
4. `dir`
5. Weil die Befehle Daten unmittelbar löschen können und ein falscher Pfad zu Datenverlust führen kann.
6. `copy /?`

</details>

---

## 8. Kurzübersicht

```text
help             Hilfeübersicht anzeigen
Befehl /?        Hilfe zu einem Befehl anzeigen
cls              Anzeige leeren
cd               aktuellen Ordner anzeigen
cd Ordner        in einen Ordner wechseln
cd ..            eine Ebene nach oben wechseln
dir              Ordnerinhalt anzeigen
mkdir Ordner     Ordner erstellen
echo Text        Text ausgeben
type Datei       Textdatei anzeigen
copy Quelle Ziel Datei kopieren
move Quelle Ziel Datei verschieben
ren Alt Neu      Datei umbenennen
del Datei        Datei löschen
rmdir Ordner     leeren Ordner löschen
```


---

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
