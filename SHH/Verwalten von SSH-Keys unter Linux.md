# Verwalten von SSH-Keys unter Linux

In dieser Anleitung lernen erfahren Sie über die folgenden Punkte:
- Wie überprüfe ich vorhandene SSH-Keys?
- Wie lösche ich vorhandene SSH-Keys?
- Wie erstelle ich neue SSH-Keys?
- Wie aktiviere ich den SSH-Agent?

> [!NOTE]
> Die folgenden Schritte sind auch für das Verwalten von SSH-Keys unter WSL2 relevant.

## Überprüfen von SSH-Keys

Um zu überprüfen ob SSH-Keys bereits vorhanden sind, führt man im Terminal den folgenden Befehl aus.

```CLI
ls ~/.ssh
```

Dieser Befehl listet alle Dateien im `.ssh`-Verzeichnis auf. Im Regelfall haben SSH-Key-Dateien Namen wie `id_rsa` (privater Schlüssel)
und `id_rsa.pub` (öffentlicher Schlüssel).

