# Kiez‑App Frontend

Dieses Verzeichnis enthält einen einfachen Prototyp für die Kartenoberfläche der Kiez‑App. Die Karte zeigt alle derzeit im Backend registrierten Geschäfte auf einer interaktiven OpenStreetMap‑Karte an und erlaubt das Abrufen des aktuellen Status (geöffnet, Spieß vorhanden).

## Voraussetzungen

- **Laufendes Backend**: Der Prototyp geht davon aus, dass das Backend aus dem Verzeichnis `kiez_app_backend` gestartet wurde und unter `http://localhost:3000` erreichbar ist. Stellen Sie sicher, dass der Server mit `npm start` läuft.
- **Lokale Webserver**: Aus Sicherheitsgründen blockieren moderne Browser den direkten Zugriff auf lokale Dateien (`file:///…`) mit JavaScript‑Fetch‐Aufrufen. Daher sollten Sie die Frontend‑Datei über einen kleinen Webserver ausliefern. Die Installation weiterer Software ist dafür nicht notwendig; macOS und andere Systeme bringen passende Werkzeuge mit.

## Starten des Frontends

1. Öffnen Sie ein Terminal und wechseln Sie in dieses Verzeichnis:
   ```bash
   cd path/zum/Projekt/kiez_app_frontend
   ```
2. Starten Sie einen einfachen HTTP‑Server. Unter macOS und Linux können Sie z. B. Python verwenden (Python 3 ist auf vielen Systemen vorinstalliert):
   ```bash
   python3 -m http.server 8000
   ```
   Dadurch werden alle Dateien im aktuellen Verzeichnis unter `http://localhost:8000` erreichbar.
   
   Alternativ können Sie das `http-server`‑Paket aus Node.js verwenden, wenn Sie dieses bereits installiert haben:
   ```bash
   npx http-server -p 8000
   ```

3. Öffnen Sie im Browser die Adresse `http://localhost:8000/index.html`. Die Karte sollte erscheinen und die vorhandenen Geschäfte auf der Karte anzeigen. Mit einem Klick auf den Link „Status abrufen“ im Popup erhalten Sie eine Benachrichtigung mit dem aktuellen Status.

## Hinweise zur weiteren Entwicklung

- **Cross‑Origin‑Requests**: Da das Backend auf Port 3000 läuft und das Frontend auf Port 8000, ist der Zugriff per CORS freigegeben. Die CORS‑Konfiguration im Backend ermöglicht dies bereits. Wenn Sie andere Ports nutzen, passen Sie die entsprechenden URLs in `index.html` sowie ggf. die CORS‑Einstellungen im Backend an.
- **Sicherheit und Authentifizierung**: Der Prototyp dient nur zu Demonstrationszwecken. In einer echten Anwendung sollten Sie Authentifizierung integrieren, damit nur berechtigte Ladenbesitzer Statusmeldungen ändern können. Zudem sollte die Kommunikation idealerweise verschlüsselt (HTTPS) erfolgen.
- **Persistente Daten**: Aktuell speichert das Backend die Daten im Arbeitsspeicher. Beim Neustart des Servers gehen diese verloren. In einer späteren Version sollte eine Datenbank angebunden werden, um Daten dauerhaft zu speichern.

Viel Spaß beim Testen des Kartenprototyps!