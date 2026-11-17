# Spatial Vision Assist

Planung einer lokalen Kameraassistenz für blinde und sehbehinderte Menschen auf iOS und Android: schnelle Objekterkennung, kurze Sprachhinweise und eine Tonposition, die dem erkannten Objekt folgt.

**Stand: Planung und Recherche, 17. November 2026.** Dieses Repository enthält noch keine installierbare App. Gerätewerte zu Geschwindigkeit, Erkennungsqualität und Akkuverbrauch sind Entwicklungsziele und noch nicht gemessen.

## Vorgesehenes Nutzererlebnis

App öffnen, Kamera ausrichten und relevante Objekte hören. Befindet sich eine Treppe links im Kamerabild, kommt die entsprechende Ansage von links. Beim Schwenken wandert die Stimme mit dem Objekt. Front- und Rückkamera sind umschaltbar.

Die Grundfunktion soll ohne Internet arbeiten. Häufige Ansagen werden als gespeicherte Mono-Sprachclips räumlich ausgegeben. Geprüft werden Stereo-Panning und binaurales HRTF-Rendering. Phonon ist ein Kandidat für die Herstellung der Sprachpakete und spätere freie Sprachausgabe.

## Dokumente

- [Entwicklungsplan](PLAN.md): Bedienung, Modelle, Treppentraining, Audio, Energiebedarf, Tests und Entwicklungsphasen.
- [Recherche ähnlicher GitHub-Projekte](RECHERCHE.md): vorhandene Ansätze, geprüfte Codepfade, Grenzen und mögliche Grundlagen.
- Der [Audiovergleich im Plan](PLAN.md#71-prüfung-der-vorgeschlagenen-audio-werkzeuge) behandelt unter anderem BRT, Steam Audio, IEM, Binauro, OpenSpatialDelay, Orbit und Binaspect.

## Nächster technischer Schritt

Auf je einem iPhone und Android-Gerät den Weg von Kamera über kleinen Detektor und Objektverfolgung bis zum räumlich bewegten Sprachclip aufbauen. Anschließend Latenz, Richtungserkennung und Energieverbrauch vergleichen. Blinde Testpersonen sollen bereits an der ersten Audioprobe beteiligt werden.

## Einsatzbereich und Daten

Das Vorhaben ist eine ergänzende Orientierungshilfe. Es ersetzt weder Langstock noch Blindenführhund. Fehlende Erkennungen bedeuten keinen freien Weg. Insbesondere Treppen abwärts, einzelne Stufen und Entfernungen benötigen eigene Daten und unabhängige Prüfungen.

Für die Grundfunktion sind keine Aufnahme, Speicherung oder Übertragung von Kamerabildern vorgesehen. Eine spätere Trainingsaufnahme wäre eine getrennte, ausdrücklich aktivierte Funktion.

## Quellen und Lizenzen

Fremdprojekte werden hier beschrieben und verlinkt; ihr Quellcode und ihre Modellgewichte sind nicht enthalten. Vor einer Übernahme werden die konkreten Code-, Modell-, Stimmen- und Datensatzlizenzen geprüft. Für eigenen zukünftigen App-Code ist die Projektlizenz noch festzulegen.

## English overview

Planning and source research for an on-device iOS/Android camera assistant for blind and low-vision users, combining lightweight detection with short spoken cues that follow object direction. No installable application is included yet. The German documents distinguish proposed features, inspected source code, and measurements still required.
