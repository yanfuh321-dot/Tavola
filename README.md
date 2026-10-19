# Tavola – Frühstück und mediterrane Abendessen für zwei

Tavola ist eine kleine Web-App für gesunde mediterrane Rezepte: Jeden Tag ein Rezeptvorschlag, Favoriten und Bewertungen, Timer in jedem Schritt, Umrechnung metrisch/imperial, Englisch/Deutsch/Chinesisch und Dark Mode. Alle Rezepte sind für zwei Personen und kommen ohne Backofen aus (Air Fryer und Herd).

## Was in diesem Ordner liegt

| Datei | Wofür |
|---|---|
| `index.html` | Die komplette App |
| `manifest.webmanifest` | Damit du Tavola wie eine App auf den Startbildschirm legen kannst |
| `icon-192.png`, `icon-512.png`, `icon-maskable-512.png`, `apple-touch-icon.png` | App-Symbole |
| `README.md` | Diese Anleitung |

---

## 1. Auf GitHub veröffentlichen (ca. 10 Minuten)

1. **Konto anlegen:** Auf [github.com](https://github.com) kostenlos registrieren, falls du noch kein Konto hast.
2. **Repository erstellen:** Oben rechts auf **+** → **New repository**.
   - Name: zum Beispiel `tavola` (der Name wird Teil der Adresse)
   - Sichtbarkeit: **Public**. Im kostenlosen GitHub-Plan funktioniert GitHub Pages nur mit öffentlichen Repositories.
   - Kein Häkchen bei „Add a README file“ (eine README ist schon dabei).
   - **Create repository** klicken.
3. **Dateien hochladen:** Auf der neuen, leeren Seite auf den Link **uploading an existing file** klicken.
   - Die ZIP-Datei vorher entpacken.
   - **Alle Dateien aus dem entpackten Ordner** markieren und ins Browserfenster ziehen, nicht den Ordner selbst. `index.html` muss ganz oben im Repository liegen, nicht in einem Unterordner.
   - Unten auf **Commit changes** klicken.
4. **GitHub Pages einschalten:** Im Repository auf **Settings** → links **Pages**.
   - Unter **Build and deployment** → **Source**: **Deploy from a branch**
   - **Branch**: `main`, Ordner `/ (root)` → **Save**
5. **Kurz warten:** Nach 1–2 Minuten die Pages-Seite neu laden. Oben steht dann deine Adresse, etwa
   `https://DEIN-BENUTZERNAME.github.io/tavola/`

Hinweis: Weil das Repository öffentlich ist, kann jeder den Code und die Seite sehen. Deine persönlichen Daten (Favoriten, Notizen, API-Schlüssel) liegen aber nur in deinem Browser und landen nie auf GitHub.

---

## 2. Tavola als App aufs Handy legen

- **iPhone (Safari):** Seite öffnen → Teilen-Symbol → **Zum Home-Bildschirm**
- **Android (Chrome):** Menü ⋮ → **Zum Startbildschirm hinzufügen** oder **App installieren**

Tavola öffnet sich dann ohne Browserleiste, wie eine normale App.

---

## 3. Neue Rezepte per KI (optional): Claude oder Gemini

In claude.ai erstellt Claude die neuen Rezepte direkt. Auf GitHub gibt es diese Verbindung nicht. Damit Tavola dort trotzdem täglich neue Rezepte erstellen kann, trägst du einen **eigenen API-Schlüssel** ein. Du kannst wählen, ob Claude oder Gemini die Rezepte schreibt.

Ohne Schlüssel funktioniert alles andere ganz normal: Sammlung, Favoriten, Bewertungen, Timer und Umrechnung. Nur „Neues Rezept erstellen“ und das tägliche neue Rezept sind dann ausgeblendet.

**In Tavola einstellen:** Zahnrad → **Rezept-KI** → **Claude** oder **Gemini** wählen → Schlüssel einfügen → **Schlüssel speichern**.
Für jeden Anbieter wird ein eigener Schlüssel gespeichert. Du kannst also jederzeit umschalten, ohne neu einzugeben. Unter jedem neuen Rezept steht, wer es erstellt hat.

### Variante A: Claude-Schlüssel

1. Auf [platform.claude.com](https://platform.claude.com) (Claude Console) anmelden.
   Wichtig: Die API wird **getrennt** von claude.ai abgerechnet. Ein Claude-Pro- oder Max-Abo enthält kein API-Guthaben.
2. Unter **Billing** Guthaben aufladen.
3. Unter **API Keys** auf **Create Key** klicken und den Schlüssel kopieren. Er beginnt mit `sk-ant-`.
4. Empfehlung: In der Console ein **Ausgabenlimit** einstellen.

### Variante B: Gemini-Schlüssel

1. Auf [aistudio.google.com](https://aistudio.google.com) (Google AI Studio) mit deinem Google-Konto anmelden.
2. Dort einen **API-Schlüssel** erstellen und kopieren. Er beginnt mit `AIza`.
3. Kosten, kostenlose Kontingente und Limits legt Google fest. Die aktuellen Bedingungen findest du in Google AI Studio. Prüf dort auch, wie Google die Eingaben bei kostenlosen Kontingenten verwenden darf. Tavola schickt nur die Rezeptanfrage mit, also deine Wünsche und die Titel deiner Lieblingsrezepte.

**Kosten:** Jedes neue Rezept ist eine Anfrage an den jeweiligen Anbieter. Wenn „Jeden Tag ein neues Rezept“ eingeschaltet ist, entsteht höchstens ein automatisches Rezept pro Tag, plus die Rezepte, die du selbst unter „Entdecken“ erstellst.

**Sicherheit:**

- Schlüssel werden **nur im Browser des jeweiligen Geräts** gespeichert. Trag sie niemals in `index.html` ein und lade sie nie auf GitHub hoch, denn das Repository ist öffentlich.
- Auf jedem Gerät musst du den Schlüssel einmal eintragen.
- Wer Zugriff auf dein entsperrtes Gerät hat, könnte einen Schlüssel auslesen. Wenn du unsicher bist, lösch den Schlüssel beim Anbieter und erstelle einen neuen.

**Modelle:** Mit Claude nutzt Tavola Claude Sonnet und weicht bei Bedarf automatisch auf ein anderes verfügbares Modell aus (in `index.html`: `API_MODELS`). Mit Gemini wählt Tavola automatisch das neueste stabile Gemini-Flash-Modell, das dein Schlüssel nutzen darf. Ein festes Modell kannst du in `index.html` bei `GEMINI_MODEL` eintragen.

---

## 4. Wo deine Daten liegen

- Favoriten, Bewertungen, Notizen, „Heute gekocht“ und neue Rezepte werden **im Browser des jeweiligen Geräts** gespeichert.
- Sie werden **nicht automatisch** zwischen Handy und Laptop abgeglichen. Dafür gibt es die Sicherung: **Zahnrad → Sicherung → Exportieren**, die Datei aufs andere Gerät schicken und dort **Importieren**. Der Import führt die Daten zusammen und überschreibt nichts.
- Wenn du die Browserdaten löschst, sind auch die Tavola-Daten weg. Ab und zu exportieren lohnt sich.
- Die Version in claude.ai speichert getrennt in deinem Claude-Konto. Beide Versionen teilen keine Daten.

---

## 5. Eine neue Version einspielen

1. Im Repository auf **Add file** → **Upload files**.
2. Die neue `index.html` hineinziehen. Eine Datei mit gleichem Namen wird ersetzt.
3. **Commit changes**. Nach 1–2 Minuten ist die neue Version online.

Deine Daten bleiben dabei erhalten, weil sie im Browser liegen und nicht in der Datei.

---

## 6. Startrezepte selbst ergänzen

Die Startrezepte stehen in `index.html` im Abschnitt `const SEEDS = [`. Jede Zutat und jeder Schritt hat die Form:

```js
I(200, 'g', 'wholewheat spaghetti', 'Vollkornspaghetti', '全麦意大利面')   // Menge, Einheit, Englisch, Deutsch, Chinesisch
P(600, 'English step…', 'Deutscher Schritt…', '中文步骤…')                 // Timer in Sekunden (0 = kein Timer), Text
```

- Einheiten: `g`, `ml`, `tbsp` (EL), `tsp` (TL), `pinch` (Prise), `handful` (Handvoll), `pc` (Stück). Menge `0` bedeutet „nach Geschmack“.
- Temperaturen als `{T200}` schreiben. Tavola zeigt sie automatisch in °C oder °F an.

Einfacher geht es, wenn du Claude das Rezept schickst und es einbauen lässt.

---

## Wenn etwas nicht klappt

- **Die Seite zeigt „404“:** 2–3 Minuten warten. Prüfen, ob `index.html` direkt im Repository liegt (nicht in einem Unterordner) und ob Pages auf `main` / `/ (root)` steht.
- **„Der API-Schlüssel wurde abgelehnt“:** Schlüssel neu kopieren, ohne Leerzeichen am Anfang oder Ende. Bei Gemini prüfen, ob der Schlüssel in Google AI Studio aktiv ist.
- **„Kein Guthaben“:** In der Claude Console unter Billing aufladen.
- **„Gemini-Kontingent aufgebraucht“:** Das Tageslimit bei Google ist erreicht. Später erneut versuchen oder die Limits in Google AI Studio prüfen.
- **Ein falscher Schlüssel im falschen Feld:** Claude-Schlüssel beginnen mit `sk-ant-`, Gemini-Schlüssel mit `AIza`. Prüf unter „Rezept-KI“, welcher Anbieter ausgewählt ist.
- **Kein Timer-Ton:** Prüfen, ob das Handy stumm geschaltet ist. Wenn sich der Bildschirm sperrt, pausieren manche Browser den Ton. Die Zeit läuft trotzdem korrekt weiter. Beim Kochen den Bildschirm am besten anlassen.


## 7. Externe Rezepte importieren (neu)

Unter **Entdecken → Rezept importieren** den vollständigen Rezepttext (Zutaten, Mengen, Zubereitung und ursprüngliche Portionszahl) einfügen. Eine Quelle oder URL kannst du separat speichern. **Mit KI umwandeln** verwendet den unter Einstellungen hinterlegten Claude- oder Gemini-Schlüssel. Der eingegebene Rezepttext wird an diesen Anbieter gesendet; dafür gelten dessen API-Kosten.

Die KI rechnet auf zwei Personen um, übersetzt in Deutsch, Englisch und Chinesisch und ergänzt Timer und Temperatur-Tokens. Standardmäßig bleiben Zutaten und Geräte erhalten. Optional kann die Zubereitung an deine Geräteeinstellung angepasst werden. Änderungen und Annahmen erscheinen in der Vorschau. Dort alle Mengen und Garzeiten prüfen; Kalorien sind Schätzwerte. Erst **In Sammlung speichern** übernimmt das Rezept. Zum Korrigieren den Ausgangstext ändern und erneut umwandeln.

Importiert wird kopierter Text, keine Webseite hinter einem Link und kein PDF-/Foto-Anhang. Bei PDF-Rezepten zunächst den Text kopieren. Die Quellenangabe bleibt am gespeicherten Rezept erhalten und wird mit der bestehenden Sicherungsfunktion exportiert. Wie bisher werden Rezepte lokal auf dem jeweiligen Gerät gespeichert.

Zum Aktualisieren zuerst in Tavola eine Sicherung exportieren, dann die neue index.html im bisherigen GitHub-Repository ersetzen. Die Browser-Speicherschlüssel bleiben gleich. Die Online-Version wird durch diese ZIP-Datei nicht automatisch aktualisiert.


## 8. Bestehende Rezepte mit KI anpassen (neu)

Ein Rezept öffnen und **Mit KI anpassen** auswählen. Beschreibe deinen Wunsch, zum Beispiel: „Meine Frau mag keine Petersilie. Bitte durch ein passendes Kraut ersetzen.“ Der Schnellvorschlag **Ohne Petersilie ausprobieren** füllt dieses Anliegen für dich aus; erst **Variante vorschlagen** sendet die Anfrage.

Tavola nutzt deinen eingestellten Claude- oder Gemini-Anbieter und API-Schlüssel. Das Rezept und der Änderungswunsch werden an diesen Anbieter gesendet. Die KI soll passende Ersatzmengen wählen, Zutaten und Zubereitung konsistent aktualisieren und die Änderungen erläutern. Die Ausgabe umfasst wie bisher Deutsch, Englisch und Chinesisch, Timer und Temperaturen.

Prüfe die vollständige Vorschau für zwei Personen und wähle **Als neue Variante speichern**. Das Original samt Bewertungen und Notizen bleibt unverändert. Die neue Variante erhält einen eigenen Eintrag in deiner Sammlung und einen Verweis auf den Originaltitel sowie den umgesetzten Wunsch. Ihre Bewertungen und Notizen beginnen leer. Um den Wunsch zu überarbeiten, zuerst den Vorschlag verwerfen und eine neue Anfrage stellen. **Stoppen** bricht eine laufende Anfrage ab.

Die Portionsauswahl im Rezept dient der Anzeige; die KI arbeitet immer mit den hinterlegten zwei Basisportionen. Der Petersilienwunsch gilt jeweils für dieses Rezept und wird nicht automatisch als allgemeine Vorliebe gespeichert. Varianten sind Teil der bestehenden Export-/Import-Sicherung. Nicht gespeicherte Vorschläge gehen beim Neuladen verloren. Geräteübergreifender Sync ist in dieser Version weiterhin nicht eingerichtet.

Update: zuerst in Tavola eine Sicherung exportieren, dann die index.html aus dieser ZIP im bisherigen GitHub-Repository ersetzen. Deine lokal gespeicherten Rezepte bleiben unter demselben Speicherschlüssel erhalten.


## 9. Frühstück und Dinner (neu)

Über **Frühstück / Dinner** oberhalb des Inhalts wählst du die Mahlzeit. Die Auswahl gilt für **Heute**, **Entdecken** und **Sammlung**. Vier Frühstücksrezepte sind ohne API-Schlüssel enthalten: Apfel-Walnuss-Porridge, Beeren-Joghurt-Bowl, Spinat-Rührei auf Vollkorntoast und Hummus-Gurken-Brot. Die angegebenen Kalorien sind Schätzwerte pro Person.

Frühstück unterstützt dieselben Funktionen: KI-Rezepte, Textimport, KI-Anpassungen, Favoriten, Bewertungen, Notizen, Kochhistorie, Portionen, Timer, Einheiten und drei Sprachen. Unter Entdecken gibt es zusätzlich den Zeitfilter **Bis 15 Min.**. Beim Textimport wird die ausgewählte Mahlzeit zugeordnet; Varianten behalten die Kategorie des Ausgangsrezepts.

Bestehende Rezepte ohne Mahlzeit-Feld werden weiterhin als Dinner behandelt. Für jede Kategorie wird ein eigener Tagesvorschlag gespeichert. Ist die automatische KI-Erstellung aktiviert, wird pro geöffneter Kategorie höchstens ein neues Rezept täglich angefragt, also insgesamt bis zu zwei. Dafür können entsprechend zusätzliche API-Kosten entstehen.

Die Mahlzeit-Kategorie ist in der bestehenden Datensicherung enthalten. Geräteübergreifender Sync ist weiterhin nicht eingerichtet. Zum Update wie bisher zuerst die Daten exportieren und anschließend die index.html ersetzen.


## 10. Individuelle Refluxwünsche (neu)

Unter dem Mahlzeit-Umschalter **Reflux berücksichtigen** öffnen, aktivieren, Ausschlüsse anpassen und **Einstellungen speichern** wählen. Gilt für neue KI-Rezepte (auch automatische Tagesrezepte) und KI-Anpassungen bei Frühstück und Dinner. Die Grundeinstellung berücksichtigt häufig genannte Auslöser: Zitrusfrüchte, Tomaten, scharfe Gewürze, Minze, Kakao/Schokolade, Kaffee/Koffein und Alkohol. Jede Gruppe lässt sich abwählen; weitere persönliche Auslöser können durch Kommas getrennt ergänzt werden. Zusätzlich wird die KI um milde Zubereitung, mäßige Fettmengen und moderate Portionen gebeten.

Bestehende Rezepte, Tagesvorschläge aus der Sammlung und reine Textimporte werden nicht automatisch verändert oder als verträglich eingestuft. Öffne ein solches Rezept, wähle **Mit KI anpassen → Refluxwünsche anwenden → Variante vorschlagen** und prüfe das Ergebnis. Für ein neues Rezept: **Entdecken → Neues Rezept erstellen**. Bereits heute erzeugte Tagesrezepte werden durch Einschalten nicht erneut automatisch erzeugt.

Die Einstellungen werden auf diesem Gerät gespeichert. Sie werden bei KI-Anfragen an deinen ausgewählten Anbieter gesendet; Rezepte behalten eine Kopie der bei der Anfrage verwendeten Einstellungen. Exporte enthalten diese Daten. Der bestehende Sicherungsimport übernimmt die gespeicherten Rezepte, jedoch nicht die globalen Geräteeinstellungen; den Modus auf einem neuen Gerät bitte separat konfigurieren. Die Kennzeichnung bedeutet nur „mit diesen Wünschen angefragt“, nicht medizinisch geprüft. Die KI kann Fehler machen; Zutaten und Varianten vor Verwendung prüfen.

Auslöser und Verträglichkeit sind individuell. Eine bestimmte Ernährung verhindert Beschwerden nicht garantiert; unnötig umfassende Lebensmittelverbote sind nicht das Ziel. Anhaltende Rachenbeschwerden sollten ärztlich abgeklärt werden. Diese Funktion diagnostiziert oder behandelt weder GERD noch LPR.

Grundlagen (abgerufen 10.10.2026):
- NIDDK: https://www.niddk.nih.gov/health-information/digestive-diseases/acid-reflux-ger-gerd-adults/eating-diet-nutrition
- American Academy of Otolaryngology–Head and Neck Surgery: https://www.enthealth.org/conditions/gerd-and-lpr/


## 11. OpenRouter als Rezept-KI (neu)

1. Zahnrad → **Rezept-KI → OpenRouter**.
2. Auf https://openrouter.ai/models ein Text-/Chatmodell wählen und dessen genaue ID in **Modell-ID** einfügen (anbieter/modell).
3. Den persönlichen OpenRouter-Schlüssel eintragen und speichern. Das Modell wird dabei ebenfalls gespeichert. Alternativ die Modell-ID separat mit **Modell speichern** ändern.
4. Unter **Entdecken** ein Rezept erstellen oder ein vorhandenes Rezept importieren/anpassen. Frühstück, Dinner und Refluxwünsche verwenden denselben ausgewählten Anbieter.

OpenRouter erhält die Rezeptanfragen und leitet sie an einen Modellanbieter weiter. Preise, Limits, Modellverfügbarkeit und Datenregeln gelten entsprechend. Ein ChatGPT-/Claude-Abonnement ist dafür kein API-Guthaben. Es wird nicht automatisch auf ein anderes Modell gewechselt. Die App wartet auf eine vollständige Antwort; bei langen Anfragen erscheint bis dahin die laufende Ladeanzeige. Stoppen bleibt verfügbar; Abbruch bedeutet nicht zwingend, dass beim Anbieter keine Kosten entstehen. Nach zwei Minuten wird die Anfrage beendet.

**Schlüsselspeicherung:** Der neue OpenRouter-Key bleibt standardmäßig nur im Arbeitsspeicher des Tabs und muss nach dem Neuladen erneut eingegeben werden. **Schlüssel auf diesem Gerät merken** ist eine optionale dauerhafte Speicherung im Browser. Zum Wechseln dieser Einstellung den Key entfernen und neu eintragen. Der Key wird nie in Rezept-Backups oder in diese ZIP geschrieben. Bestehende Claude-/Gemini-Schlüssel behalten ihr bisheriges Speicherverhalten. Browserseitige Schlüssel sind kein Ersatz für eine abgesicherte Serverlösung; nutze einen separaten Schlüssel mit Ausgabenlimit. Das Speichern des OpenRouter-Schlüssels allein startet keine kostenpflichtige Rezeptanfrage. Die bestehende Option für tägliche automatische Rezepte gilt beim späteren Öffnen und Kategorien-/Anbieterwechsel weiterhin.

**Sicherheitskorrektur:** Rezept-IDs und relevante Importfelder werden strenger geprüft; IDs und Kategorien werden bei der HTML-Ausgabe maskiert. Fehlerhafte Sicherungen werden vor dem Zusammenführen abgewiesen. Die konkret gefundene HTML-Attribut-Injektion über Backup-Rezept-IDs ist damit geschlossen. Dies ist kein vollständiges Sicherheitszertifikat.

API-Dokumentation: https://openrouter.ai/docs/api/api-reference/chat/create-a-chat-completion (abgerufen 19.10.2026).
