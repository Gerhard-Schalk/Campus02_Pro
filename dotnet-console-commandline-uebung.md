# Übung: .NET-Konsolenanwendung über die Commandline erstellen

> **Ziel:** Eine einfache C#-Konsolenanwendung mit der .NET CLI erstellen, bearbeiten und ausführen.  
> **Umgebung:** Windows Command Prompt (`cmd.exe`), .NET SDK und Editor `notepad.exe`

## Lernziele

Nach dieser Übung können die Teilnehmenden:

- die Windows Commandline öffnen,
- einen Übungsordner im Benutzerverzeichnis erstellen,
- die installierte .NET-Umgebung überprüfen,
- eine C#-Konsolenanwendung erstellen,
- den Quellcode mit Notepad bearbeiten,
- die Anwendung über die Commandline ausführen.

---

## 1. Windows Commandline öffnen

1. Drücke `Windows-Taste + R`.
2. Gib `cmd` ein.
3. Drücke `Enter`.

Die Windows-Eingabeaufforderung wird geöffnet. Die Eingabezeile sieht beispielsweise so aus:

```text
C:\Users\Vorname>
```

Der Text vor `>` zeigt das aktuelle Verzeichnis.

---

## 2. Übungsordner im Benutzerverzeichnis erstellen

Wechsle zuerst in dein Benutzerverzeichnis:

```cmd
cd /d %USERPROFILE%
```

Erstelle dort einen Ordner für die Übung:

```cmd
mkdir dotnet-uebung
```

Wechsle in den neuen Ordner:

```cmd
cd dotnet-uebung
```

Zeige zur Kontrolle den aktuellen Pfad an:

```cmd
cd
```

> `%USERPROFILE%` ist eine Windows-Umgebungsvariable. Sie verweist auf das Benutzerverzeichnis des aktuell angemeldeten Benutzers, zum Beispiel `C:\Users\Vorname`.

---

## 3. Installierte .NET-Umgebung überprüfen

### Allgemeine Informationen anzeigen

```cmd
dotnet --info
```

Dieser Befehl zeigt detaillierte Informationen zur .NET-Installation und zur Systemumgebung an.

### Installierte Runtimes anzeigen

```cmd
dotnet --list-runtimes
```

Eine **Runtime** wird benötigt, um eine bereits erstellte .NET-Anwendung auszuführen.

### Installierte SDKs anzeigen

```cmd
dotnet --list-sdks
```

Das **SDK** enthält die Werkzeuge zum Erstellen, Kompilieren und Ausführen von .NET-Projekten.

> **Wichtig:** Für `dotnet new` und `dotnet run` muss ein .NET SDK installiert sein. Eine Runtime allein ist für diese Übung nicht ausreichend.

---

## 4. Konsolenprojekt erstellen

Erstelle eine neue C#-Konsolenanwendung im Unterordner `myHelloWorld`:

```cmd
dotnet new console -o myHelloWorld
```

Bedeutung der Bestandteile:

- `dotnet` startet die .NET CLI.
- `new` erstellt ein neues Projekt.
- `console` wählt die Vorlage für eine Konsolenanwendung.
- `-o myHelloWorld` legt das Projekt im Ordner `myHelloWorld` an.

Wechsle anschließend in den Projektordner:

```cmd
cd myHelloWorld
```

Zeige die erzeugten Dateien an:

```cmd
dir
```

Unter anderem sollten eine Projektdatei mit der Endung `.csproj` und die C#-Quelldatei `Program.cs` vorhanden sein.

---

## 5. C#-Programm mit Notepad bearbeiten

Öffne die Datei `Program.cs` im Windows-Editor:

```cmd
notepad.exe Program.cs
```

Ersetze den vorhandenen Inhalt beispielsweise durch:

```csharp
Console.WriteLine("Hallo aus meiner ersten C#-Konsolenanwendung!");
Console.Write("Wie heißt du? ");

string? name = Console.ReadLine();

Console.WriteLine($"Willkommen, {name}!");
```

Speichere die Datei in Notepad mit `Strg + S` und schließe anschließend den Editor.

> Achte darauf, dass die Datei weiterhin `Program.cs` heißt und nicht versehentlich als `Program.cs.txt` gespeichert wird.

---

## 6. Programm ausführen

Stelle sicher, dass du dich im Projektordner `myHelloWorld` befindest:

```cmd
cd
```

Starte danach die Anwendung:

```cmd
dotnet run
```

Eine mögliche Ausgabe ist:

```text
Hallo aus meiner ersten C#-Konsolenanwendung!
Wie heißt du? Hansi
Willkommen, Hansi!
```

`dotnet run` erstellt und startet das Projekt. Nach einer Änderung an `Program.cs` kann derselbe Befehl erneut ausgeführt werden.

---

## 7. Kompletter Befehlsablauf

```cmd
cd /d %USERPROFILE%
mkdir dotnet-uebung
cd dotnet-uebung

dotnet --info
dotnet --list-runtimes
dotnet --list-sdks

dotnet new console -o myHelloWorld
cd myHelloWorld
notepad.exe Program.cs
dotnet run
```

---

## 8. Kleine Zusatzaufgaben

1. Ändere die Begrüßung im Programm.
2. Ergänze eine Frage nach dem Wohnort.
3. Gib Name und Wohnort gemeinsam aus.
4. Speichere die Datei und führe erneut `dotnet run` aus.

<details>
<summary>Beispiellösung anzeigen</summary>

```csharp
Console.Write("Wie heißt du? ");
string? name = Console.ReadLine();

Console.Write("Wo wohnst du? ");
string? wohnort = Console.ReadLine();

Console.WriteLine($"Hallo {name} aus {wohnort}!");
```

</details>

---

## 9. Häufige Probleme

### `dotnet` wird nicht erkannt

Prüfe, ob .NET installiert und über den Windows-Suchpfad erreichbar ist:

```cmd
dotnet --info
```

### Es wird kein SDK aufgelistet

Prüfe:

```cmd
dotnet --list-sdks
```

Wenn keine SDK-Version angezeigt wird, ist möglicherweise nur eine Runtime installiert. Zum Erstellen des Projekts wird ein .NET SDK benötigt.

### `Couldn't find a project to run`

Prüfe mit `cd` und `dir`, ob du dich im Projektordner `myHelloWorld` befindest:

```cmd
cd
dir
```

Wechsle bei Bedarf in den Projektordner:

```cmd
cd /d %USERPROFILE%\dotnet-uebung\myHelloWorld
```

Führe die Anwendung danach erneut aus:

```cmd
dotnet run
```

---

## Referenzen

- [Übersicht über den dotnet-Befehl](https://learn.microsoft.com/de-de/dotnet/core/tools/dotnet)
- [Installierte .NET-Versionen überprüfen](https://learn.microsoft.com/de-de/dotnet/core/install/how-to-detect-installed-versions)
