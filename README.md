# traffidesk_copy_pk_top
Einfaches Script um sicherzustellen das alle aktuellen pk und top Datein auf dem Cleint liegen
Bitte Verzeichnisse selber anlegen. 

Bestehende Datein werden direkt überschrieben


Script in der Übersicht


@echo off
REM ================================================
REM  Script:   copy_keys.bat
REM  Zweck:    Kopiert alle .pk und .tok Dateien von
REM            K:\Traffi\keys nach C:\Traffi\keys
REM            und überschreibt dabei bestehende Dateien.
REM
REM ================================================

REM Quelle und Zielverzeichnis definieren
set SOURCE=K:\Traffi\keys
set TARGET=C:\Traffi\keys

REM Ausgabe zur Kontrolle
echo ================================================
echo Starte Kopiervorgang
echo Quelle: %SOURCE%
echo Ziel:   %TARGET%
echo Bitte alle Traffidesk Programme schließen und nach der Ausführung des Scripts neu starten. Danke
echo ================================================
echo.

REM Prüfen, ob Quellverzeichnis existiert
if not exist "%SOURCE%" (
    echo Fehler: Quellverzeichnis %SOURCE% existiert nicht.
    pause
    exit /b 1
)

REM Prüfen, ob Zielverzeichnis existiert, falls nicht -> erstellen
if not exist "%TARGET%" (
    echo Zielverzeichnis %TARGET% wird erstellt...
    mkdir "%TARGET%"
)

REM Kopieren der Dateien (.pk und .tok), /Y = überschreiben ohne Rückfrage
echo Kopiere .pk Dateien...
copy /Y "%SOURCE%\*.pk" "%TARGET%\" >nul

echo Kopiere .tok Dateien...
copy /Y "%SOURCE%\*.tok" "%TARGET%\" >nul

echo.
echo ================================================
echo Kopiervorgang abgeschlossen!
echo ================================================
pause
