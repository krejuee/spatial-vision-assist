# Ähnliche Apps und Grundlagen auf GitHub

Geprüft am 17. November 2026. Ziel: Kameraobjekte lokal erkennen und ihre Bezeichnung räumlich wiedergeben. Die folgenden Bewertungen beruhen auf Repository-Dokumentation und den ausdrücklich genannten Codepfaden. Es wurde keine dieser Apps gebaut oder auf einem Telefon getestet.

## Ergebnis

Es gibt mehrere nahe Vorarbeiten. Unter den geprüften Projekten ist jedoch keine nachgewiesen fertige iOS-/Android-Lösung für alle Anforderungen: sparsame lokale Erkennung, Deutsch, umschaltbare Kameras, während der Sprache bewegte Objektposition und gesondert validierte Treppenrichtung.

Die passendsten Ausgangspunkte sind **Project Daredevil** für native iOS-Audio-/Tiefenverarbeitung und **Saartheye** für eine kleine lokale Kamera-/Sprachdemo. Ihre Audioausgabe erfüllt das gewünschte Mitwandern der gesprochenen Objektbezeichnung noch nicht vollständig.

## 1. Project Daredevil — native iOS-Grundlage

[Repository](https://github.com/MIT-Assistive-Technology/Project-Daredevil) · [iOS-Anleitung](https://github.com/MIT-Assistive-Technology/Project-Daredevil/blob/main/ios/README.md) · [MIT-Lizenz](https://github.com/MIT-Assistive-Technology/Project-Daredevil/blob/main/LICENSE)

- Native iOS-App mit LiDAR-Tiefe, Erkennung von Öffnungen und Hindernissen sowie räumlicher HRTF-Ausgabe.
- Die iOS-Anleitung verlangt ein LiDAR-fähiges iPhone Pro. Der ältere Python-Teil hat eine andere Erkennungspipeline; dessen YOLO-Funktionen dürfen nicht automatisch der nativen App zugeschrieben werden.
- Im geprüften [Audio-Code](https://github.com/MIT-Assistive-Technology/Project-Daredevil/blob/main/ios/Daredevil/Engine/SpatialAudioEngine.swift) laufen Geräuschquellen durch einen HRTF-Renderer. Die [Sprache](https://github.com/MIT-Assistive-Technology/Project-Daredevil/blob/main/ios/Daredevil/Engine/SpeechAnnouncer.swift) verwendet separat `AVSpeechSynthesizer`.
- Damit sind räumliche Geräusche und gesprochene Zustände belegt, aber keine gemeinsam am Objekt positionierte Wortausgabe.

**Einordnung:** Als möglicher Fork oder als Audio-/Tracking-Grundlage zuerst untersuchen. Ein kleiner semantischer Detektor, räumlich abgespielte deutsche Clips, Android und ein Modus ohne LiDAR bleiben eigene Arbeit.

## 2. Saartheye — lokale Browser-Demo

[Repository](https://github.com/MaybeSomeone-arc18/saartheye-ai) · [MIT-Lizenz](https://github.com/MaybeSomeone-arc18/saartheye-ai/blob/main/LICENSE)

- Browser-Prototyp mit lokaler Objekterkennung, Objektverfolgung, gesprochenen Richtungshinweisen und Stereotönen.
- Der geprüfte [Audio-Code](https://github.com/MaybeSomeone-arc18/saartheye-ai/blob/main/src/utils/spatialAudio.js) enthält vorbereitete englische Sprachsegmente. Die Töne verwenden `StereoPannerNode`; die vorbereiteten Wörter werden direkt an die Audioausgabe angeschlossen.
- Die gesprochene Bezeichnung ist damit im geprüften Code nicht selbst räumlich positioniert. Das wäre gezielt zu ergänzen.
- Die Dokumentation kennzeichnet das Projekt ausdrücklich als nicht mit blinden Menschen validierten Prototyp. Browser-Offlinefähigkeit braucht einen ersten Download und erhaltene lokale Caches.

**Einordnung:** Nahe an der Idee vorbereiteter Sprache und für eine frühe Hördemo interessant. Eine stromsparende native Mobile-App, HRTF, Deutsch und Treppen sind daraus noch nicht nachgewiesen.

## 3. Echora — gezieltes Objektsuchen mit Kopftracking

[Repository](https://github.com/tisya05/Echora)

- iOS-Prototyp zum Suchen eines angefragten Alltagsobjekts mit Sprache, ARKit/LiDAR, räumlichem Ortungssignal und AirPods-Kopftracking.
- Der [Audio-Graph](https://github.com/tisya05/Echora/blob/main/ios/Echora/Audio/SpatialAudioGraph.swift) enthält positionierte Monoquellen mit `.HRTFHQ` und aktualisierte Hörerposition/-orientierung.
- Die reale [Objektortung](https://github.com/tisya05/Echora/blob/main/ios/Echora/Perception/GeminiLocator.swift) sendet Anfragen an Gemini. Das entspricht nicht unserem vollständig lokalen Dauerbetrieb.
- In der geprüften Dateiliste und Repository-Metadaten war keine Projektlizenz ausgewiesen. Öffentliche Lesbarkeit allein ist keine Erlaubnis zur Codeübernahme.

**Einordnung:** Gute Referenz für Bedienung und Kopftracking. Für eine Übernahme sind zuerst Nutzungsrechte und ein lokaler Ersatz der Ortung zu klären.

## 4. NavEye — Android-Referenz für lokale Erkennung

[Repository](https://github.com/Punujalokith/naveye)

- Dokumentiert eine Flutter-Android-App mit rückwärtiger Kamera, lokalem YOLOv8n-ONNX-Modell und englischer Text-to-Speech-Ausgabe.
- Richtungen werden laut README als links/Mitte/rechts aus der Objektbox abgeleitet und angesagt. Eine binaurale Platzierung der gesprochenen Wörter ist damit nicht belegt.
- Für Sprachbefehle nennt das Projekt Cloud-Spracherkennung; die Objekterkennung selbst wird als offline beschrieben.
- Repository-Metadaten weisen keine erkannte Projektlizenz aus. Für diese Recherche wurden README und Metadaten gelesen; der eigentliche Kamera-/Detektorpfad wurde nicht vollständig auditiert.

**Einordnung:** Android-Architektur vergleichen, keine ungeprüfte Übernahme. Die README-Gerätetests sind Angaben des Projekts und keine von uns bestätigten Messungen.

## Weitere Treffer

### Soca / TreeHacks 2024

[Repository](https://github.com/kdrag0n/soca-treehacks24) · [geprüfter AR-/Audio-Code](https://github.com/kdrag0n/soca-treehacks24/blob/main/SpatialDot/AR.swift)

LiDAR, virtuelle Audioquellen, `.HRTFHQ` und Kopfhörerbewegung sind im Swift-Code vorhanden. Daneben gibt es Netzwerk-/Serverbestandteile. Durchgängig lokaler Betrieb ist nicht nachgewiesen. In Dateiliste und Metadaten war keine Projektlizenz ausgewiesen. Als ältere technische Vorarbeit interessant, nicht als fertige plattformübergreifende App bewertet.

### VisionVoice

[Repository](https://github.com/Musharaf-khan/VisionVoice) · [Erkennung](https://github.com/Musharaf-khan/VisionVoice/blob/main/Visionrecognizer.swift) · [Audio](https://github.com/Musharaf-khan/VisionVoice/blob/main/SoundscapeEngine.swift)

iOS-Code mit Apple-Vision-Analyse und räumlichen Tönen. Eine wichtige Einschränkung steht im Erkennungscode: Allgemeine Bildklassifikationen erhalten ein festes Rechteck in der Bildmitte (`CGRect(x: 0.4, y: 0.4, width: 0.2, height: 0.2)`). Diese Ergebnisse liefern also keine tatsächliche Objektposition. Gesichter, Tiere und Text verwenden andere Erkennungen. Eine Projektlizenz war nicht ausgewiesen. Für allgemeine Objektortung daher keine bevorzugte Grundlage.

### Soundscape

[Microsoft-Original](https://github.com/microsoft/soundscape) · [Android-Weiterentwicklung](https://github.com/Scottish-Tech-Army/Soundscape-Android)

Interessante Referenz für räumliche Orientierung und barrierefreie Audiobedienung. Der Schwerpunkt liegt auf geografischer Orientierung und Karteninformationen. Eine Erkennung der Treppe im aktuellen Kamerabild ist dadurch nicht belegt. Die Android-Weiterentwicklung ist ein separates Projekt; Wartung, Lizenz und Audio-Code wären vor einer Übernahme eigens zu prüfen.

## Konsequenz für unser Projekt

1. Die frühe Audioprobe soll ausdrücklich einen **gesprochenen Mono-Clip** räumlich abspielen und dessen Position während des Clips aktualisieren. Ein zusätzliches links/rechts abgespieltes Piepen allein genügt dem Produktziel nicht.
2. Project Daredevil zuerst als iOS-Grundlage bewerten. Saartheye eignet sich als Vergleich für vorbereitete Sprache und die frühe Browser-Demo.
3. Die Android-App braucht weiterhin eine geprüfte lokale Kamera-/Detektorpipeline und einen nativen Audiovergleich. Ein gemeinsamer HRTF-Kern mit Steam Audio oder BRT ist separat zu untersuchen.
4. Treppen und ihre Richtung bleiben ein eigener Trainings- und Validierungsbaustein. Keiner der hier geprüften Codepfade liefert dafür einen ausreichenden Nachweis.
5. Fremdcode bleibt zunächst außerhalb dieses Repositorys. Eine spätere Übernahme erhält nachvollziehbare Herkunft und die erforderlichen Lizenzhinweise.

Der [Entwicklungsplan](PLAN.md) beschreibt den vorgesehenen Umfang, die Audio-Werkzeuge und die Messungen auf realen Geräten.
