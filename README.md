# 🔤 Enigmistica

Web app per anagrammi e ricerca parole italiane, utilizzabile da smartphone e desktop.

**👉 [Prova l'app](https://infingardo.github.io/Enigmistica/)**

## Funzionalità

### 🔄 Anagrammi
- **Anagrammi perfetti** — tutte le lettere usate una volta
- **Multi-parola** — combinazioni di 2-4 parole che formano l'anagramma
- **Parole incluse** — sub-anagrammi (parole formate con un sottoinsieme delle lettere)

### 🔍 Ricerca parole
Cerca parole usando pattern con caratteri speciali:

| Carattere | Significato |
|-----------|-------------|
| `.` o `?` | una lettera qualsiasi |
| `+` | una vocale (a, e, i, o, u) |
| `-` | una consonante |
| `*` | zero o più lettere |

**Esempi:**
- `cas+` → casa, case, caso, casi
- `*zione` → parole che finiscono in "-zione"
- `p-+ma` → prima, piuma...
- `..ntro` → centro, contro, dentro...
- `a*z*a` → inizia con "a", contiene "z", finisce con "a"

### 📚 Vocabolari
- 📘 **Ridotto** (~31k parole) — veloce, solo lemmi principali
- 📚 **Completo** (~283k parole) — include forme flesse, plurali, coniugazioni

### ⚙️ Altre funzionalità
- **Personalizzazione** — aggiungi o rimuovi parole dal dizionario
- **Offline** — dopo il primo caricamento, il dizionario resta in cache
- **Esportazione** — scarica il dizionario personalizzato

## Uso

1. Apri il [sito](https://infingardo.github.io/Enigmistica/)
2. Seleziona il vocabolario (Ridotto o Completo)
3. Scegli la tab **Anagrammi** o **Cerca parole**
4. Scrivi una parola o un pattern e premi Cerca
5. Clicca su un risultato per cercarne gli anagrammi
6. Tieni premuto (mobile) o click destro (desktop) per altre opzioni

## Installazione locale

```bash
git clone https://github.com/Infingardo/Enigmistica.git
cd Enigmistica
# Apri index.html nel browser
```

## File

| File | Descrizione |
|------|-------------|
| `index.html` | App completa (HTML + CSS + JS) |
| `dizionario_ridotto.txt` | ~31k parole |
| `dizionario_completo.txt` | ~283k parole |

## Crediti

Il vocabolario proviene da **[Enilab](http://www.enignet.it/software.html)**, software gratuito per l'enigmistica sviluppato da Giulio Ferrari e distribuito dalla **[Biblioteca Enigmistica Italiana (BEI)](http://www.enignet.it/)**.

## Licenza

Il codice dell'app è rilasciato sotto licenza MIT.

Il vocabolario Enilab è freeware per uso personale e non commerciale (vedi [licenza Enilab](http://www.enignet.it/software.html)).

## Autore

Filippo Bianchi (kc8)
