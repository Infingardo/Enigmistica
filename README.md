# 🔤 Enigmistica

Applicazione web per enigmisti: anagrammi, ricerca parole e giochi linguistici con vocabolario italiano.

## Demo

[**Apri l'applicazione**](https://infingardo.github.io/Enigmistica/)

## Funzionalità

### 🔄 Anagrammi
- **Anagrammi perfetti**: trova tutte le parole con le stesse lettere
- **Multi-parola**: combinazioni di 2-4 parole (es. ASTRONAUTA → TARA + UOSA + N)
- **Parole incluse**: parole più corte contenute nelle lettere date

### 🔍 Cerca parole
Ricerca con pattern flessibili:
- `.` o `?` = una lettera qualsiasi
- `+` = vocale
- `-` = consonante  
- `*` = zero o più lettere

Esempi: `cas+` → casa, case, caso | `*zione` → parole che finiscono in "zione"

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

## Tecnologie

- HTML5 / CSS3 / JavaScript vanilla
- IndexedDB per cache e persistenza
- PWA-ready (funziona offline dopo primo caricamento)
- Zero dipendenze esterne
- Responsive (mobile-friendly)

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
├── dizionario_ridotto.txt  # Vocabolario ridotto
├── dizionario_completo.txt # Vocabolario completo
└── README.md
```

## Note tecniche

- I dizionari vengono scaricati e salvati in IndexedDB al primo utilizzo
- Le modifiche (parole aggiunte/rimosse) sono persistenti nel browser
- La ricerca anagrammi multi-parola è limitata a 500 combinazioni per performance
- La ricerca cambi usa BFS con limite di 10.000 nodi visitati
- La ricerca sciarade nel dizionario analizza max 5.000 parole

## Crediti

- Vocabolario: [Enilab/BEI](http://www.enignet.it) - Biblioteca Enigmistica Italiana
- Sviluppo: Progetto personale per appassionati di enigmistica

## License

MIT License - Uso libero con attribuzione.
