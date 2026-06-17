# Abel123 AI

Een chat-terminal in eigen stijl, gekoppeld aan Claude via de Anthropic API.

## ⚠️ Belangrijk: GitHub Pages werkt hier niet voor de chatfunctie

GitHub Pages kan alleen **statische** bestanden (HTML/CSS/JS) tonen — het kan geen Python draaien.
`app.py` is de motor die jouw bericht naar Claude stuurt; zonder die server kan de pagina nooit echt antwoorden.
De pagina zal er nu mooi uitzien op `are1233.github.io`, maar SEND zal een foutmelding geven omdat er geen `/api/chat` bestaat.

Twee opties:

### Optie 1 — Lokaal draaien (makkelijkst, alles werkt direct)
1. `pip install -r requirements.txt`
2. `.env.example` hernoemen naar `.env`, vul je API-key in (console.anthropic.com/settings/keys)
3. `python app.py`
4. Open `http://127.0.0.1:5000` — volledig werkende Abel123 AI, met je eigen huisstijl.

### Optie 2 — Ook online laten werken
Host `app.py` op een gratis Python-host (bijv. Render.com of Railway.app), zet daar je API-key veilig als environment variable, en laat `script.js` naar dat adres wijzen in plaats van `/api/chat`. Dan blijft `are1233.github.io` de "voorkant", en draait de AI-motor ergens anders.
Plaats je API-key **nooit** rechtstreeks in script.js op een publieke GitHub Pages site — die is voor iedereen zichtbaar en kan misbruikt worden.

## Aanpassen

- **Persoonlijkheid** → `SYSTEM_PROMPT` in `app.py`
- **Model** → `ANTHROPIC_MODEL` in `.env` (`claude-opus-4-7` voor meer redeneerkracht, `claude-haiku-4-5-20251001` voor snelheid)
- **Uiterlijk** → kleuren/fonts staan als variabelen boven in `style.css`

## Bestanden

```
abel123-ai/
├── app.py              ← lokale server, praat met Claude
├── requirements.txt
├── .env.example         ← hernoem naar .env + vul key in
├── index.html
├── style.css
└── script.js
```
