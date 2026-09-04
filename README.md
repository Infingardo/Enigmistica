# 🔤 Enigmistica

Applicazione web per enigmisti: anagrammi, ricerca parole e giochi linguistici con vocabolario italiano.

## Demo

[**Apri l'applicazione**](https://infingardo.github.io/Enigmistica/)

## Funzionalità

### 🔄 Anagrammi

- **Anagrammi perfetti**: trova tutte le parole con le stesse lettere
- **Multi-parola**: combinazioni di 2-4 parole (es. ASTRONAUTA → TARA + UOSA + N)
- **Parole incluse**: parole più corte contenute nelle lettere date
- **Tooltip live**: traduzione del pattern in tempo reale con stima combinazioni

#### Pattern per anagrammi estesi

Aggiungi caratteri speciali alla fine della parola per cercare anagrammi con lettere aggiuntive:

| Pattern | Significato | Esempio |
|---------|-------------|---------|
| `+` | Aggiungi una vocale | `roma+` → anagrammi di ROMA + A/E/I/O/U |
| `-` | Aggiungi una consonante | `roma-` → anagrammi di ROMA + B/C/D/... |
| `?` | Aggiungi una lettera qualsiasi | `roma?` → anagrammi di ROMA + qualsiasi lettera |
| `*` | Superanagrammi | `roma*` → parole che contengono tutte le lettere di ROMA |

**Combinazioni**: puoi combinare liberamente i pattern (escluso `*`):
- `roma++` → ROMA + due vocali
- `roma--` → ROMA + due consonanti  
- `roma+-` → ROMA + una vocale + una consonante
- `roma???` → ROMA + tre lettere qualsiasi
- `casa++-` → CASA + due vocali + una consonante

### 🔍 Cerca parole

Ricerca con pattern flessibili:

| Pattern | Significato | Esempio |
|---------|-------------|---------|
| `.` o `?` | Una lettera qualsiasi | `cas?` → casa, case, caso |
| `+` | Una vocale | `c+sa` → casa, cosa |
| `-` | Una consonante | `ca-a` → cala, cama, cana... |
| `*` | Zero o più lettere | `*zione` → parole che finiscono in "zione" |

I filtri lunghezza min/max appaiono solo quando il pattern contiene `*` (altrimenti la lunghezza è determinata).

### 🎯 Quiz

Allenamento interattivo sugli anagrammi:
- Parola mostrata, trova tutti gli anagrammi
- Timer 60 secondi con bonus tempo
- Punteggio e serie (streak)
- Supporto anagrammi multi-parola per parole lunghe
- Filtri per lunghezza e numero minimo di anagrammi

### 🎮 Giochi

| Gioco | Descrizione | Esempio |
|-------|-------------|---------|
| **🔀 Cambi** | Catena di parole cambiando una lettera | MANO → MONO → MOTO |
| **🪞 Palindromi** | Parole speculari | OTTO, RADAR, ANNA |
| **↔️ Bifronti** | Coppie di parole una il rovescio dell'altra | ENOTECA ↔ ACETONE |
| **✂️ Scarti** | Togli una lettera | CAMINO → CAINO |
| **🔧 Zeppe** | Aggiungi lettera interna | CANTO → CANATO |
| **➕ Aggiunte** | Lettera a inizio/fine | CARPA → SCARPA, CHE → CHEF |
| **🧩 Sciarade** | Scomponi in parole | CANICOLA = CANI + COLA |

## Vocabolario

Due dizionari disponibili (fonte: [Enilab/BEI](http://www.enignet.it)):

- **📘 Ridotto**: ~31.000 parole, caricamento veloce
- **📚 Completo**: ~283.000 parole, esaustivo

### Personalizzazione

- ➕ Aggiungi parole personalizzate
- 🗑️ Rimuovi parole indesiderate
- ♻️ Ripristina parole rimosse
- 📥 Esporta dizionario modificato
- ✉️ Suggerisci parole al curatore
- 📋 Copia risultati negli appunti

## Tecnologie

- HTML5 / CSS3 / JavaScript vanilla
- IndexedDB per cache e persistenza
- **PWA installabile** (funziona offline, si installa come app)
- Zero dipendenze esterne
- Responsive (mobile-friendly)

## Installazione come App (PWA)

### Su smartphone (Android/iOS)
1. Apri [l'applicazione](https://infingardo.github.io/Enigmistica/) nel browser
2. **Android (Chrome)**: Menu ⋮ → "Aggiungi a schermata Home"
3. **iOS (Safari)**: Condividi ↑ → "Aggiungi a Home"

### Su desktop (Chrome/Edge)
1. Apri l'applicazione
2. Clicca l'icona di installazione nella barra degli indirizzi (➕ o 📥)
3. Oppure: Menu → "Installa Enigmistica"

Una volta installata, funziona **completamente offline** dopo il primo caricamento del dizionario.

## Installazione locale

1. Clona il repository:
```bash
git clone https://github.com/infingardo/Enigmistica.git
```

2. Apri `index.html` nel browser

Oppure servilo con un server locale:
```bash
python -m http.server 8000
# Apri http://localhost:8000
```

## Struttura file

```
Enigmistica/
├── index.html              # Applicazione completa
├── manifest.json           # Manifest PWA
├── sw.js                   # Service Worker
├── icons/
│   ├── icon-192.png        # Icona 192x192
│   └── icon-512.png        # Icona 512x512
├── dizionario_ridotto.txt  # Vocabolario ridotto
├── dizionario_completo.txt # Vocabolario completo
└── README.md
```

## Note tecniche

### Limiti configurabili

I limiti di ricerca sono centralizzati in `CONFIG`:

| Parametro | Valore | Descrizione |
|-----------|--------|-------------|
| `maxPatternResults` | 1000 | Risultati max per ricerca pattern |
| `maxMultiWordResults` | 500 | Anagrammi multi-parola max |
| `maxPatternCombinations` | 50000 | Combinazioni max per pattern anagrammi |
| `maxCambiNodes` | 10000 | Nodi BFS max per catena cambi |
| `maxSciaradeInverseCheck` | 5000 | Parole analizzate per sciarade inverse |
| `maxSuperanagramsPerGroup` | 200 | Superanagrammi visualizzati per gruppo |

Quando un limite viene raggiunto, appare un warning giallo.

### Apostrofi e trattini

Le parole con apostrofo o trattino sono trattate come forme unite:
- `dell'arte` → `dellarte`
- `week-end` → `weekend`

Scelta necessaria per gli anagrammi, ma può influire semanticamente su alcuni giochi (sciarade, bifronti).

### Ottimizzazioni

- **Pre-indice `wordsByLength`**: accelera la ricerca Cambi
- **Pruning in multi-parola**: taglia rami morti quando `remaining < minLen * wordsNeeded`
- **IndexedDB**: dizionario scaricato una volta e cachato nel browser

## Crediti

- Vocabolario: [Enilab/BEI](http://www.enignet.it) - Biblioteca Enigmistica Italiana
- Sviluppo: [infingardo](https://github.com/infingardo)

## License

MIT License - Uso libero con attribuzione.
