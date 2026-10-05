# Tavola – mediterrane Abendessen für zwei

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
