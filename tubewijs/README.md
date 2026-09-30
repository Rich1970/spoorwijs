# Tubewijs ▶

Een YouTube-alternatief waarin **jij** bepaalt wat je ziet, niet het algoritme.

1. **Vraag stellen:** typ bovenin wat je wilt leren, bijvoorbeeld *"Hoe haal ik het maximale uit Claude Code met een €20-abonnement zonder door mijn tokens te gaan?"*
2. **AI zoekt slim** *(optioneel)*: Claude Haiku maakt van je vraag een paar goede YouTube-zoekopdrachten (NL + EN), haalt de resultaten op en geeft elke video een relevantiescore. Clickbait en onzin vallen eruit.
3. **Swipen zoals op Tinder:**
   - **← links:** niet interessant, komt nooit meer terug
   - **→ rechts:** al gezien, komt nooit meer terug
   - **↑ omhoog:** bewaren in je kijklijst
   - tik op de kaart of druk op spatie om even te kijken, Backspace maakt ongedaan
   - 🚫 blokkeer een heel kanaal
4. **Kijklijst:** pas als je klaar bent met swipen, kijk je alles achter elkaar ("Alles afspelen"). Na afloop klik je **✓ Gezien**.
5. **Ontdekken:** een homefeed zoals op YouTube (je interesses + trending + categorieën) om je nog te laten verrassen, maar zonder video's die je al zag of wegswipte.

Extra:
- **Google Takeout-import:** laad je echte YouTube-kijkgeschiedenis (`watch-history.json`), zodat Tubewijs vanaf dag 1 weet wat je al hebt gezien.
- Filters: Shorts overslaan, taal, maximale leeftijd van een video.
- Back-up exporteren en importeren, om over te zetten naar je telefoon of een andere computer.

## Kosten

| Onderdeel | Kosten |
|---|---|
| YouTube Data API | **gratis**: 10.000 punten per dag, één zoekvraag met 3 zoekopdrachten ≈ 300 punten, dus ongeveer 30 vragen per dag |
| AI (optioneel) | Claude Haiku via de Anthropic API: ongeveer **€0,002 per vraag**, apart van je Claude-abonnement |

## Starten

Het is één los HTML-bestand, zonder installatie of build. YouTube-video's spelen alleen af als de pagina via `http://` wordt geserveerd (niet als je het bestand dubbelklikt):

```bash
cd tubewijs
npx serve .          # open http://localhost:3000
```

Of zet de map gratis online op Vercel of Netlify (map `tubewijs/` slepen), dan werkt hij ook op je telefoon.

Daarna ⚙️ → vul je **YouTube API-sleutel** in (en eventueel je Anthropic-sleutel) → Opslaan.

**YouTube-sleutel aanmaken (± 3 min):** [console.cloud.google.com](https://console.cloud.google.com) → nieuw project → *APIs & Services → Library* → "YouTube Data API v3" → **Enable** → *Credentials → Create credentials → API key*.
Tip: beperk de sleutel onder *Application restrictions → Websites* tot je eigen domein.

## Privacy

Alles (sleutels, gezien, kijklijst) staat alleen in de `localStorage` van je eigen browser. Er is geen server.
