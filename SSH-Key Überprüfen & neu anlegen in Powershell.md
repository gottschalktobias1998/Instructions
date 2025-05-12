
```
Hoffentlich dient diese Anleitung als guter Weg, um mögliche Fehler mit GitHub und GitLab zu vermeiden.
```

Diese Guide geht darauf ein, wie man bereits vorhandene Schlüssel löscht, sollten diese falsch gelegt sein. Sollte dem nicht der Fall sein, kann ab Schritt "3" gestartet werden.

## 1\. Überprüfen vorhandener SSH-Keys

Öffne PowerShell und führe den folgenden Befehl aus, um zu sehen, ob du bereits SSH-Keys hast:

```powershell
sl ~/.ssh
```

Dieser Befehl listet alle Dateien im `.ssh`\-Verzeichnis auf. Typische SSH-Keys-Dateien haben Namen wie `id_rsa` (private key) und `id_rsa.pub` (public key)

## 2\. Löschen vorhandener SHH-Keys

Wenn du die vorhandenen SHH-Keys löschen möchtest, kannst du die entsprechenden Dateien mit dem folgenden Befehl entfernen:

```powershell
Remove-Item ~/.ssh/id_rsa, ~/.ssh/id_rsa.pub
```

Stelle sicher, dass du die richtigen Dateien löschst, da dieser Befehl die Dateien permanent entfernt.

## 3\. Erstellen neuer SHH-Keys

Um neue SSH-Keys zu erstellen, verwende den folgenden Befehl:

```powershell
ssh-keygen -t rsa -b 4096 -C "deine_email@test.com"
```

Ersetze `deine_email@example.com` durch deine tatsächliche E-Mail-Adresse. Du wirst aufgefordert, einen Speicherort für den Schlüssel anzugeben. Drücke einfach `Enter`, um den Standardort (`~/.ssh/id_rsa`) zu verwenden. Du kannst auch ein Passwort für zusätzlichen Schutz eingeben, wenn du möchtest.

## 4\. Hinzufügen des SSH-Keys zum SSH-Agent

Um sicherzustellen, dass der SSH-Agent läuft und dein neuer Schlüssel hinzugefügt wird, führe die folgenden Befehle aus:

```powershell
# Starte den SSH-Agenten
Start-Service ssh-agent

# Füge den SSH-Schlüssel hinzu
ssh-add ~/.ssh/id_rsa
```

## 5\. Hinzufügen des öffentlichen Schlüssels zu GitHub/GitLab

Um den öffentlichen Schlüssel zu GitHub oder GitLab hinzuzufügen, musst du den Inhalt der Datei `id_rsa.pub` kopieren. Verwende dazu den folgenden Befehl:

```powershell
Get-Content ~/.ssh/id_rsa.pub | Set-Clipboard
```

Jetzt ist der öffentliche Schlüssel in deiner Zwischenablage. Gehe zu deinem GitHub- oder GitLab-Konto, navigiere zu den SSH-Schlüssel-Einstellungen und füge den Schlüssel dort hinzu.

## 6\. Verbindung überprüfen

```powershell
ssh -T git@gitlab.bbwausbildung-digital.de
```

Die Antwort sollte so aussehen:

```powershell
Welcome to GitLab, @your_username!
```

## 7\. Überprüfen bei weiteren Fehlern

// TODO