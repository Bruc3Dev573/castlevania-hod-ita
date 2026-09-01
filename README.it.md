# Castlevania: Harmony of Dissonance - traduzione italiana

[English](README.md) | **Italiano**

Patch italiana non ufficiale per la versione USA di *Castlevania: Harmony of
Dissonance* su Game Boy Advance.

La patch è compatibile con **Visual Improvement V1.2.7** e viene distribuita in
quattro varianti. Il gioco originale e la patch Visual Improvement non sono
inclusi.

## Download

Scarica l'ultima versione dalla pagina
[Releases](https://github.com/Bruc3Dev573/castlevania-hod-ita/releases).

## Base richiesta

- ROM: `Castlevania - Harmony of Dissonance (USA)`
- CRC32: `88C1B562`
- SHA-1: `B90DA0D9BE0B3A0893CD9E2C399056BCF9579E21`
- [Visual Improvement V1.2.7](https://www.romhacking.net/hacks/9086/)

## Installazione

1. Parti da una ROM USA pulita con CRC32 `88C1B562`.
2. Applica Visual Improvement V1.2.7 nella variante desiderata.
3. Applica la patch italiana corrispondente alla ROM già modificata.

| Variante Visual Improvement | Patch italiana |
|---|---|
| V1.2.7 originale | `patches/hod-ita-vi-1.2.7.ips` |
| V1.2.7 C-Whip | `patches/hod-ita-vi-1.2.7-cwhip.ips` |
| V1.2.7 RMenu | `patches/hod-ita-vi-1.2.7-rmenu.ips` |
| V1.2.7 C-Whip RMenu | `patches/hod-ita-vi-1.2.7-cwhip-rmenu.ips` |

Le patch italiane non vanno applicate direttamente alla ROM pulita. Usa
[Lunar IPS](https://fusoya.eludevisibility.org/lips/) o un altro patcher IPS
compatibile. Gli hash delle basi e dei risultati sono in `release.json` e
`patches/manifest.json`. Dettagli tecnici sull'approccio di compatibilità:
[docs/how-it-works.md](docs/how-it-works.md) (in inglese).

## Stato della versione 1

La ROM ha 717 voci di testo (dialoghi, menu, nomi di oggetti e nemici). 613
sono tradotte in italiano. Le restanti 104 restano in inglese per scelta
esplicita: 9 sono nomi propri (Maxim, Lydie, Dracula e simili), 72 sono nomi
brevi di oggetti/nemici che non entrano nel budget di byte fisso per ogni
voce, e 23 sono slot placeholder interni mai mostrati in gioco.

Le quattro varianti superano i controlli di integrità, il boot e le verifiche
runtime mirate su menu, dialoghi e progressione avanzata della trama. Il
caricamento e la scrittura di un salvataggio sono stati verificati
manualmente su hardware.

Il gioco è stato provato su hardware reale per alcune ore, raggiungendo il
Castello B, senza crash né blocchi. Il Castello B non è ancora stato
completato. Il glifo `ò`, aggiunto appositamente al font, può risultare
poco leggibile in alcuni testi. La correzione è prevista in una prossima
release.

Per segnalare crash, testo tagliato o altri problemi, usa le
[Issues](https://github.com/Bruc3Dev573/castlevania-hod-ita/issues) indicando
variante, patcher e punto del gioco.

## Screenshot

| Menu equipaggiamento | Prologo |
|:---:|:---:|
| ![Menu equipaggiamento](docs/screenshots/equip-menu.png) | ![Prologo](docs/screenshots/prologue.png) |

## Crediti

- Traduzione italiana, adattamento e patch: **Bruc3Dev573**
- [Visual Improvement V1.2.7](https://www.romhacking.net/hacks/9086/):
  **sorrow, Piggy Chan!, ncoZ, spiffy, LagoLunatic**
- [Traduzione francese v0.7](https://traf.romhack.org/mavabxwa.html?p=patchs&pid=1608)
  di **Brutapode89**, usata come riferimento tecnico per la struttura del
  testo e del font

Il testo italiano è stato tradotto dall'inglese originale. La traduzione
francese non è inclusa né sovrapposta.

Le condizioni di attribuzione e ridistribuzione del materiale originale del progetto sono descritte in [`NOTICE`](NOTICE).

## Avvertenze

Progetto non ufficiale e senza alcuna garanzia. Konami e gli autori citati nei
crediti non sono coinvolti. È necessaria una copia personale del gioco.

Questo repository contiene solo patch, checksum e documentazione. Se detieni i
diritti su materiale presente e vuoi richiederne la rimozione, apri una
segnalazione.
