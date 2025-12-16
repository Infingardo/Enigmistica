# 🔤 Anagrammi Italiano

Web app per trovare anagrammi di parole italiane, utilizzabile da smartphone e desktop.

**👉 [Prova l'app](https://infingardo.github.io/Enigmistica/)**

## Funzionalità

- **Anagrammi perfetti** — tutte le lettere usate una volta
- **Multi-parola** — combinazioni di 2-4 parole che formano l'anagramma
- **Parole incluse** — sub-anagrammi (parole formate con un sottoinsieme delle lettere)
- **Due vocabolari:**
  - 📘 Ridotto (~31k parole) — veloce, solo lemmi principali
  - 📚 Completo (~283k parole) — include forme flesse, plurali, coniugazioni
- **Personalizzazione** — aggiungi o rimuovi parole dal dizionario
- **Offline** — dopo il primo caricamento, il dizionario resta in cache nel browser

## Screenshot

![Screenshot](screenshot.png)

## Uso

1. Apri il [sito](https://infingardo.github.io/Enigmistica/)
2. Seleziona il vocabolario (Ridotto o Completo)
3. Scrivi una parola e premi "Cerca anagrammi"
4. Clicca su un risultato per cercarne gli anagrammi
5. Tieni premuto (mobile) o click destro (desktop) per rimuovere una parola

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

Grazie alla BEI per il lavoro di curatela del vocabolario italiano.

## Licenza

Il codice dell'app è rilasciato sotto licenza MIT.

Il vocabolario Enilab è freeware per uso personale e non commerciale (vedi [licenza Enilab](http://www.enignet.it/software.html)).

## Autore

Filippo Bianchi (kc8)
