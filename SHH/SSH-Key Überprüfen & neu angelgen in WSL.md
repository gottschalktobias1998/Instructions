## Anleitung zur Verwaltung von SSH-Keys in WSL

### 1\. Überprüfen vorhandener SSH-Keys

Öffne dein WSL-Terminal und führe den folgenden Befehl aus, um zu sehen, ob du bereits SSH-Keys hast:

```bash
ls ~/.ssh
```

Dieser Befehl listet alle Dateien im `.ssh`\-Verzeichnis auf. Typische SSH-Keys-Dateien haben Namen wie `id_rsa` (privater Schlüssel) und `id_rsa.pub` (öffentlicher Schlüssel).

### 2\. Löschen vorhandener SSH-Keys

Wenn du die vorhandenen SSH-Keys löschen möchtest, kannst du die entsprechenden Dateien mit dem folgenden Befehl entfernen:

```bash
rm ~/.ssh/id_rsa ~/.ssh/id_rsa.pub
```

Stelle sicher, dass du die richtigen Dateien löschst, da dieser Befehl die Dateien permanent entfernt.

### 3\. Erstellen neuer SSH-Keys

Um neue SSH-Keys zu erstellen, verwende den folgenden Befehl:

```bash
ssh-keygen -t rsa -b 4096 -C "deine_email@test.com"
```

Ersetze `deine_email@test.com` durch deine tatsächliche E-Mail-Adresse. Du wirst aufgefordert, einen Speicherort für den Schlüssel anzugeben. Drücke einfach `Enter`, um den Standardort (`~/.ssh/id_rsa`) zu verwenden. Du kannst auch ein Passwort für zusätzlichen Schutz eingeben, wenn du möchtest.

### 4\. Hinzufügen des SSH-Keys zum SSH-Agent

Um sicherzustellen, dass der SSH-Agent läuft und dein neuer Schlüssel hinzugefügt wird, führe die folgenden Befehle aus:

```bash
# Starte den SSH-Agenten
eval "$(ssh-agent -s)"

# Füge den SSH-Schlüssel hinzu
ssh-add ~/.ssh/id_rsa
```

### 5\. Hinzufügen des öffentlichen Schlüssels zu GitHub/GitLab

Um den öffentlichen Schlüssel zu GitHub oder GitLab hinzuzufügen, musst du den Inhalt der Datei `id_rsa.pub` kopieren. Verwende dazu den folgenden Befehl:

```bash
cat ~/.ssh/id_rsa.pub | clip.exe
```

Jetzt ist der öffentliche Schlüssel in deiner Zwischenablage. Gehe zu deinem GitHub- oder GitLab-Konto, navigiere zu den SSH-Schlüssel-Einstellungen und füge den Schlüssel dort hinzu.

## 6\. Verbindung überprüfen

```
ssh -T git@gitlab.bbwausbildung-digital.de
```

Antwort sollte so aussehen: Welcome to GitLab, @username!