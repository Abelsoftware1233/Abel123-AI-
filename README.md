# 🚀 Abel123 AI — Volledige AI-Suite

![Version](https://img.shields.io/badge/versie-2.0-cyan)
![Status](https://img.shields.io/badge/status-actief-brightgreen)
![License](https://img.shields.io/badge/licentie-MIT-blue)

Een geavanceerde, alles-in-één AI-assistent met **chat**, **beeldgeneratie** en **gezichtsherkenning**. Gebouwd met een prachtige retro-futuristische terminalstijl, volledig mobielvriendelijk.

---

## ✨ Functionaliteiten

| Functie | Beschrijving | API |
|---------|--------------|-----|
| 💬 **Chat** | Intelligent tekstgesprek met Claude | Anthropic |
| 🎨 **Beeldgeneratie** | Maak afbeeldingen op basis van tekst | Google Gemini/Imagen |
| 👤 **Gezichtsherkenning** | Analyseer gezichten op leeftijd, emotie en kenmerken | Anthropic (Claude Vision) |
| 📱 **Mobielvriendelijk** | Volledig responsive design | - |
| 🎯 **Upload functie** | Upload foto's voor analyse | - |
| 🖥️ **Terminal UI** | Retro-futuristische interface | - |

---

## 📋 Vereisten

- Python 3.8 of hoger
- API-keys van:
  - [Anthropic](https://console.anthropic.com/settings/keys) (Claude — chat én gezichtsherkenning)
  - [Google AI Studio](https://aistudio.google.com/apikey) (Gemini/Imagen — beeldgeneratie)

---

## 🛠️ Installatie

### 1. Pak de zip uit en ga naar de projectmap

Ga eerst naar de map waar je de zip hebt staan (bijvoorbeeld je Downloads-map):

```bash
cd storage/downloads
```

Pak de zip uit:

```bash
unzip Abel123-AI--.zip
```

Ga naar de uitgepakte map:

```bash
cd Abel123-AI-
```

### 2. Installeer vereisten

```bash
pip install -r requirements.txt
```

### 3. Configureer API-keys

Maak een `.env` bestand aan en vul je eigen keys in:

```bash
nano .env
```

Voeg toe:

```env
ANTHROPIC_API_KEY=jouw_eigen_key
GOOGLE_API_KEY=jouw_eigen_key
```

Opslaan: `Ctrl+O` → Enter → `Ctrl+X`.

⚠️ **Belangrijk:** `.env` mag nooit gecommit of gedeeld worden. Vul de keys alleen lokaal in.

### 4. Start de server

```bash
python app.py
```

### 5. Open in browser

Ga naar: http://localhost:5000

---

## 📂 Bestandsstructuur

```
Abel123-AI-/
├── app.py                 # Main server met alle API-integraties
├── requirements.txt       # Python dependencies
├── .env.example           # Voorbeeld configuratie (geen echte keys)
├── index.html              # Hoofdinterface
├── style.css               # Mobielvriendelijk design
├── script.js                # Alle client-side logica
├── README.md               # Deze documentatie
└── uploads/                # Tijdelijke uploads (automatisch aangemaakt)
```

---

## 🎨 Interface

### 💬 Chat Tab
- Stel vragen aan Claude
- Typewriter-effect voor antwoorden
- Gespreksgeschiedenis blijft behouden
- Reset-knop om gesprek te wissen

### 🎨 Beeld Tab
- Beschrijf wat je wilt zien
- Genereer afbeeldingen met Gemini/Imagen
- Afbeelding wordt weergegeven in de preview

### 👤 Gezicht Tab
- Upload een gezichtsfoto
- Klik op "Analyseer"
- Ontvang analyse over:
  - Leeftijdsschatting
  - Emotie/expressie
  - Opvallende kenmerken

---

## 🔧 Aanpassingen

### Persoonlijkheid aanpassen

Open `app.py` en wijzig `SYSTEM_PROMPT`:

```python
SYSTEM_PROMPT = (
    "Je bent Abel123 AI, een persoonlijke assistent..."
)
```

### Model wijzigen

In `app.py` bij de chat- en gezichtsherkenningsfunctie:

```python
model="claude-sonnet-4-6"  # Verander naar gewenst model
```

### Styling aanpassen

In `style.css` bovenaan:

```css
:root {
  --cyan: #4de8e0;     /* Primaire kleur */
  --violet: #9d7cff;   /* Secundaire kleur */
  --bg: #060b14;       /* Achtergrond */
}
```

---

## 🚀 Deploy naar Productie

### Optie 1: Render.com (gratis)

1. Push code naar GitHub
2. Ga naar Render.com
3. Kies **New Web Service** → verbind repo
4. Instellingen:
   - Build Command: `pip install -r requirements.txt`
   - Start Command: `gunicorn app:app`
5. Voeg environment variables toe:
   - `ANTHROPIC_API_KEY`
   - `GOOGLE_API_KEY`
6. Klik op Deploy

### Optie 2: Railway.app (gratis)

1. Push code naar GitHub
2. Ga naar Railway.app
3. Kies **Deploy from GitHub**
4. Voeg environment variables toe
5. Klaar! Je krijgt een live URL

### Optie 3: Hugging Face Spaces

1. Maak een Space aan met Docker
2. Upload alle bestanden
3. Voeg secrets toe voor API-keys
4. Deploy automatisch

---

## 📱 Mobiel Gebruik

| Feature | Ondersteuning |
|---------|----------------|
| Responsive design | ✅ Volledig |
| Touch knoppen | ✅ Groot en toegankelijk |
| Camera upload | ✅ Via file input |
| Scrollen | ✅ Vloeiend |
| Dark mode | ✅ Standaard |

---

## 🔒 Veiligheid

- ✅ API-keys via environment variables (niet in code)
- ✅ Geen keys in client-side JavaScript
- ✅ `.env` staat in `.gitignore`, nooit gecommit
- ✅ CORS correct geconfigureerd
- ✅ Input validatie op server
- ✅ Rate limiting mogelijk (optioneel)

---

## ❓ Veelgestelde Vragen

**Q: Werkt dit op GitHub Pages?**
A: Nee, GitHub Pages is statisch. Je moet de server draaien op een platform zoals Render of Railway.

**Q: Kan ik meerdere afbeeldingen genereren?**
A: Ja, pas `number_of_images=1` aan in `app.py`.

**Q: Welke afbeeldingsformaten ondersteunt gezichtsherkenning?**
A: JPG, PNG, WEBP, GIF (statisch).

**Q: Hoe snel is de response?**
A: Chat: 1-3 sec, Beeld: 5-10 sec, Gezicht: 2-4 sec.

---

## 🐛 Probleemoplossing

**Fout: "Geen API-key gevonden"**
- Controleer of `.env` bestaat
- Controleer of de variabelen correct zijn gespeld
- Herstart de server na wijzigingen

**Fout: "CORS" problemen**
- Zorg dat `flask-cors` is geïnstalleerd
- Controleer of `CORS(app)` in `app.py` staat

**Fout: "Geen verbinding"**
- Controleer of de server draait
- Controleer de poort (standaard 5000)
- Controleer firewall-instellingen

**Beeldgeneratie werkt niet**
- Controleer Google API-key
- Zorg dat Imagen beschikbaar is in jouw regio
- Controleer of het model correct is: `imagen-3.0-generate-001`

---

## 📊 API-limieten

| API | Gratis limiet | Betaald |
|-----|----------------|---------|
| Anthropic Claude | 5 requests/min | €0.003/1K tokens |
| Google Gemini | 60 requests/min | €0.001/afbeelding |

---

## 🤝 Bijdragen

Pull requests zijn welkom! Voor grote wijzigingen, open eerst een issue om te bespreken wat je wilt veranderen.

1. Fork de repository
2. Maak een feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit je wijzigingen (`git commit -m 'Add some AmazingFeature'`)
4. Push naar de branch (`git push origin feature/AmazingFeature`)
5. Open een Pull Request

---

## 📜 Licentie

Distributed under the MIT License. Zie LICENSE voor meer informatie.

---

## 📞 Contact

- GitHub: [Abelsoftware1233](https://github.com/Abelsoftware1233)
- Issues: GitHub Issues

---

## 🙏 Credits

- Anthropic — Claude API voor chat en gezichtsherkenning
- Google — Gemini/Imagen voor beeldgeneratie
- Fonts: Orbitron, Inter, JetBrains Mono

---

## 🎯 Roadmap

- [x] Chat functionaliteit
- [x] Beeldgeneratie
- [x] Gezichtsherkenning
- [x] Mobielvriendelijk
- [ ] Voice input
- [ ] Meer AI-modellen
- [ ] Export gesprekken
- [ ] Meertalige ondersteuning

---

Gemaakt met kennis door Abelsoftware123 | © 2026 Alle rechten voorbehouden
