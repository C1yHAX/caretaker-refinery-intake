# Caretaker Refinery Intake

**Version 1.0.0 — Erstrelease für The Last Caretaker.** Diese kleine Mod hebt die Gewichtszulassungsgrenze beim Einfüllen von organischem Material in die beiden Basis-Raffinerien auf. So lässt sich ein größerer Vorrat direkt im Gerät lagern, ohne laufend nachfüllen zu müssen.

[Download auf GitHub](https://github.com/C1yHAX/caretaker-refinery-intake/releases/tag/v1.0.0) · [Download auf GitLab](https://gitlab.com/c0d1ngf1eber/caretaker-refinery-intake/-/releases/v1.0.0)

## Enthaltene Änderungen

- **Dieselraffinerie:** organisches Material über die bisherige Gewichtsgrenze hinaus aufnehmen.
- **Tragbare Benzinraffinerie:** dieselbe Änderung für ihren organischen Eingangsbehälter.
- Strombedarf, Biomasseverbrauch, Produktionsgeschwindigkeit, Ausbeute und Flüssigkeitspuffer bleiben unverändert.
- Die ursprünglichen Geräte, Freischaltungen und gespeicherten Identitäten bleiben erhalten. Es werden keine neuen Gegenstände angelegt.

Technisch wird ausschließlich `bAllowBeyondWeightLimit` der jeweiligen `VoyageInventoryWeightLimited_GEN_VARIABLE` von `false` auf `true` gesetzt. Damit entfällt diese Gewichtsprüfung; die Mod verspricht keinen unbegrenzten Arbeitsspeicher und hebt keine beliebigen anderen Inventarregeln auf. Zwei vorhandene Blueprint-Assets werden überschrieben, ohne zusätzliche Lua-Schleifen.

Die **zusätzliche stationäre Benzinraffinerie** aus [Caretaker Energy](https://github.com/C1yHAX/caretaker-energy) hat diese Anpassung bereits in ihrer eigenen Mod. Refinery Intake ergänzt die beiden Basisgeräte. Die Destillationskolonne verarbeitet Rohöl und hat keinen entsprechenden organischen Einfüllbehälter.

## Voraussetzungen

- Windows-Version von *The Last Caretaker*, **0.10.0.653173 / Steam-Build 25982825**. Andere Spielversionen sind nicht geprüft.
- Für diese reine Asset-Mod sind **UE4SS, AssetBridge und das vollständige Modpack nicht erforderlich**.
- Den Release-Anhang **`Caretaker-Refinery-Intake-1.0.0.zip`** herunterladen. `SHA256SUMS.txt` enthält dessen Prüfsumme.

## Installation

1. Spiel und Modmanager schließen.
2. ZIP vollständig entpacken.
3. Den enthaltenen Ordner **`Voyage`** in den Installationsordner des Spiels kopieren, also in den Ordner, der bereits den Unterordner `Voyage` enthält. Steam: Spiel → Eigenschaften → Installierte Dateien → Durchsuchen.
4. Anschließend müssen diese drei Dateien zusammen unter folgendem Pfad liegen:

   ```text
   <Spielordner>/Voyage/Content/Paks/~mods/CaretakerRefineryIntake/
       CaretakerRefineryIntake_P.pak
       CaretakerRefineryIntake_P.ucas
       CaretakerRefineryIntake_P.utoc
   ```

5. Spiel normal starten. Es ist keine eigene Taste und keine zusätzliche Freischaltung nötig.

Bei einem Update die vorhandenen drei Dateien am selben Ziel ersetzen. Zusätzliche alte Kopien außerhalb des gesamten `Paks`-Ordners archivieren, damit nur eine Version geladen wird. Das **Caretaker-Modpack 1.0.0 enthält diese Mod bereits**; dort ist keine zweite Installation erforderlich.

## Kompatibilität und Entfernen

Mit den im Caretaker-Modpack enthaltenen Assetpaketen wurden keine überlappenden Paketpfade gefunden. Andere Mods, die dieselben zwei Raffinerie-Blueprints verändern, können kollidieren; siehe [ASSET-CHANGES.json](ASSET-CHANGES.json). Mit Caretaker Energy ergänzen sich die Änderungen, da dessen stationäre Benzinraffinerie einen eigenen Blueprint verwendet.

Zum Entfernen das Spiel schließen und den Ordner `CaretakerRefineryIntake` aus `Paks` herausnehmen. Vorher größere eingelagerte Mengen entnehmen und den Spielstand sichern, weil danach wieder die ursprüngliche Aufnahmeprüfung gilt. Die Mod selbst bearbeitet keine Spielstanddateien.

## Prüfung und Grenzen

Die drei Veröffentlichungsdateien wurden mit der installierten Fassung verglichen. Containerprüfung und Rückextraktion wurden erfolgreich durchgeführt; die Exportdaten bleiben beim Packen erhalten. Ein früherer nativer Ladetest bestätigte `bAllowBeyondWeightLimit` an den drei organischen Raffineriebehältern einschließlich Energy. Die Veröffentlichung enthält dieselben beiden Basis-Raffinerieassets.

Ein vollständiger Langzeittest mit großen Vorräten und Speichern/Neuladen steht aus. Für die Vorbereitung dieses Releases wurde das Spiel nicht gestartet. [Prüfbericht](verification/release.json)

## Herkunft

Inoffizielle Community-Mod für das Spiel von Channel37. Die abgeleiteten Spielassets bleiben Eigentum ihrer jeweiligen Rechteinhaber. Die MIT-Lizenz gilt für eigene Dokumentation und Paketierungswerkzeuge, nicht für die Spielinhalte. [Hinweise zu Drittinhalten](THIRD-PARTY-NOTICES.md)

Die fertig gepackten Container und die genaue Änderungsspezifikation sind enthalten. Dieses Repository enthält keinen vollständigen Unreal-Editor- oder Asset-Build. `python tools/package_release.py` prüft die enthaltenen Dateien und erzeugt das Release-ZIP aus dem Repository.

## English

Removes the organic-input weight admission cap from the stock Diesel Refinery and Portable Petrol Refinery. Production rates, resource costs, electricity requirements and liquid buffers stay unchanged. Caretaker Energy already applies the equivalent change to its additional stationary petrol refinery. Requires game build 0.10.0.653173 / 25982825; no UE4SS or AssetBridge required. Close the game and copy the release ZIP's `Voyage` folder into the game installation directory. Already included in the full Caretaker modpack. Conflicts are possible with other mods replacing the same two blueprints. Long-term save/reload behavior with large inventories has not been fully tested.
