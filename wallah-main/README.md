# Zum Bergfrieden · Sprachbrücke

Die Sprachbrücke ist eine responsive Website und Progressive Web App (PWA). Sie kann auf PC, Tablet und Smartphone im Browser genutzt und auf dem Startbildschirm installiert werden.

## Website starten

`index.html` lässt sich auf einem Computer direkt im Browser öffnen. Für die Installation, den Offline-Betrieb und den Mikrofonzugriff benötigt die Website jedoch eine **HTTPS-Adresse** (außer auf `localhost`).

Zum lokalen Testen im Projektordner einen lokalen Server starten:

```powershell
python -m http.server 8080
```

Dann `http://localhost:8080` im Browser öffnen. Die lokale Adresse ist nur auf diesem Computer erreichbar; auf dem iPhone funktioniert die Installation erst über eine veröffentlichte HTTPS-Adresse.

## Website veröffentlichen

Die Seite besteht aus statischen Dateien und benötigt weder Datenbank noch Server-Anwendung. Den **gesamten Inhalt dieses Ordners** auf einen HTTPS-fähigen statischen Webhost laden, zum Beispiel GitHub Pages oder Netlify. Die Dateien `index.html`, `app.js`, `styles.css`, `manifest.webmanifest`, `service-worker.js`, `brand-logo.png` und `icons/` müssen gemeinsam am selben Pfad veröffentlicht sein. Änderungen an der Website sind nach dem Hochladen unter der HTTPS-Adresse verfügbar.

## Auf dem iPhone hinzufügen

1. Die veröffentlichte HTTPS-Adresse in **Safari** öffnen.
2. Auf **Teilen** tippen.
3. **Zum Home-Bildschirm** auswählen und **Hinzufügen** antippen.

Auf anderen Geräten können Sie die Schaltfläche **Installieren** oder den Installieren-Eintrag im Browser-Menü nutzen. Beim ersten Seitenaufruf werden App-Oberfläche, Logo und App-Symbole zwischengespeichert; danach funktioniert die Oberfläche auch ohne Internet. Erkennungs- und Aussprache-Funktionen hängen vom jeweiligen Gerät und Browser ab.

## Xcode-Projekt (optional)

Für eine native iOS-Hülle liegt weiterhin ein Projekt unter `ios/ZumBergfrieden.xcodeproj`. Das Erstellen einer `.ipa` verlangt macOS, Xcode und ein Apple-Signaturprofil.

## Xcode-Projekt

Öffnen Sie auf einem Mac mit Xcode 15 oder neuer:

`ios/ZumBergfrieden.xcodeproj`

Wählen Sie das Ziel **Zum Bergfrieden**, dann unter **Signing & Capabilities** ein eigenes Apple Developer Team. Falls erforderlich, ändern Sie `PRODUCT_BUNDLE_IDENTIFIER` in `ios/ZumBergfrieden.xcodeproj/project.pbxproj` in eine weltweit eindeutige Kennung. Wählen Sie ein iPhone oder iPad als Ziel und starten Sie die App zunächst direkt über Xcode.

Für ein `.ipa`: In Xcode **Product → Archive** ausführen und im Organizer **Distribute App** wählen. Xcode benötigt dafür macOS, ein installiertes iOS-SDK und ein passendes Apple-Signatur-/Bereitstellungsprofil. Ohne dieses Zertifikat wäre eine erzeugte `.ipa` nicht auf einem iPhone installierbar.

## Beim Start

Das große Willkommensfenster mit dem Bergfrieden-Logo und der Schaltfläche zum Eintreten öffnet sich bei jedem App-Start. Über **Tor öffnen** können Sie es jederzeit erneut aufrufen. Die Kurzanleitung bleibt separat über **Kurzanleitung** erreichbar.

Die mitgelieferte Bewohnerin ist ein fiktives Beispielprofil und kann entfernt oder angepasst werden.

## Funktionen

- Bild-Aktivierung mit 22 deutsch-russischen Fotokarten, immer sichtbarer deutscher Bedeutung und einem anklickbaren Schritt-für-Schritt-Lernweg.
- Russische Aussprache zum normalen oder langsamen Anhören; beim Sprechen zeigt ein animierter Balken die aktive Mikrofonphase an.
- Je Bewohner lokal gespeicherte Übungen, Lernpunkte, Level, Wochensterne, Wochenübersicht und druckbare Urkunden nach Übungen und für die Woche.
- Wort-Spiel mit zwei Zuordnungsarten, Punkten, Sternen, Serienanzeige und deutschen Bedeutungen.
- Pflege-Schnellkarten mit geprüften russischen Sätzen und Lautschrift. Unbekannte freie Sätze werden nicht als übersetzt ausgegeben.
- Bewohnerprofile, Karten-Studio mit echten Foto-URLs für eigene Karten, lokale Übungshistorie und kopierbarer SIS-Entwurf.
- Originales Bergfrieden-Logo und iPhone-/iPad-Layout.

## Datenschutz und Grenzen

Profile, Karten und Protokolle werden lokal im Browserspeicher des verwendeten Geräts gehalten; es gibt keinen Server, kein Konto und keine automatische Synchronisierung. Die Web-App kann Sprache nur verarbeiten, wenn der Browser die Spracherkennung unterstützt. Das Mikrofon wird erst nach Antippen der Sprechfunktion angefragt. SIS-Texte sind Entwürfe und müssen fachlich geprüft werden. Die Schnellübersetzungen ersetzen keinen professionellen Dolmetschdienst. Bei Bewohnerdaten sind die Datenschutzregeln der Einrichtung zu beachten.

Die mitgelieferten Fotokarten liegen lokal unter `images/cards/`; sie werden beim App-Start für die Offline-Nutzung vorgeladen. Die Fotos wurden von Unsplash unter der Unsplash-Lizenz bezogen. Eigene Karten benötigen eine HTTPS-Foto-URL.

## Build-Hinweis für diese Arbeitsumgebung

Eine veröffentlichte öffentliche Domain muss beim gewählten Webhost eingerichtet werden. Der Quellcode allein stellt keine Website unter einer öffentlichen Internetadresse bereit.
