# Vocabular: cum se numesc aparatele în ce trimit clienții

Id-urile din dreapta sunt cele din `arc_catalog` (modulele configuratorului Vectis). Verifică mereu că id-ul există în
catalogul primit: lista de aici poate rămâne în urmă față de panou.

Unde scrie „întreabă”, pune postul `null` (sau rândul `lipsa`) și întrebarea în `note`.

## Comenzi de lumină

| Ce scrie clientul | Limba / brand | Id ARC |
|---|---|---|
| întrerupător simplu · interruttore · Ausschalter · switch · „1 push-button” pe un post | ro · it · de · en · FEDE | `simplu` |
| întrerupător dublu · interruttore doppio · Serienschalter · „2 push-buttons” pe UN post | ro · it · de · FEDE | `dublu` |
| cap scară · comutator · deviatore · Wechselschalter · 2-way · staircase | ro · it · de · en · FEDE | `cap-scara` |
| dublu cap scară · 2 push-buttons staircase · Doppelwechselschalter | ro · FEDE · de | `dublu-cap-scara` |
| cruce · inversor · invertitore · Kreuzschalter · intermediate | ro · it · de · FEDE | `cruce` |
| 2 butoane intermediate pe un post (dublu cruce) | FEDE | nu există: întreabă (două posturi `cruce`?) |
| buton care revine (sonerie, automatizări) · pulsante · Taster · „momentary” | ro · it · de · en | `buton` |
| variator · dimmer · varialuce · Dimmer | ro · en · it · de | `variator` |
| jaluzele · rulouri · tapparelle · Jalousieschalter · blinds / blinders up-down | ro · it · de · en | `jaluzele` |
| două comenzi de jaluzele pe un singur post (4 butoane) | FEDE | nu există pe un post: propune 2 posturi `jaluzele` |
| termostat · thermostat | toate | `lipsa` (nu e în configurator) |

**Push-button** (FEDE și alții) = întrerupător obișnuit acționat prin apăsare (rămâne aprins), NU butonul care revine.
Îl traduci ca întrerupător (`simplu`, `dublu`, `cap-scara` …); `buton` doar dacă scrie că revine (sonerie, „momentary”,
releu). Vectis are manete: funcția e aceeași, dar întreabă dacă manetele sunt în regulă pentru client.

**Câte butoane ≠ câte posturi.** „2 push-buttons staircase” pe un post = un aparat `dublu-cap-scara`. Cum recunoști
posturile la fiecare fel de document: tipare.md.

## Prize și date

| Ce scrie clientul | Id ARC |
|---|---|
| priză Schuko · shucko / schuko socket · presa schuko · Steckdose | `priza-f` |
| priză cu capac · IP44 · baie / exterior | `priza-f-ip44` |
| priză franceză (cu știft) · type E | `priza-e` |
| priză UK · type G | `priza-g` |
| USB · USB-A + USB-C · încărcător | `usb` |
| RJ45 · internet · rețea · cat 5e / cat 6 | `rj45` |
| TV · antenă · SAT · TV + SAT | `tv-sat` (dacă cere doar TV, spune că avem TV + SAT) |
| HDMI | `hdmi` |
| post gol · blank · cieco · Blindabdeckung | `orb` |

## Rame

- „Frame x3”, „3 posturi”, „triplă”, trei aparate pe aceeași ramă = `gangs: 3`.
- Pe schemele FEDE italiene, fiecare buton ocupă un modul; un modul gol cu săgeată = poziție liberă: întreabă dacă e
  capac orb (`orb`) sau o ramă mai mică.
- Orizontal e implicit; vertical doar dacă schema o arată.

## Finisaje (de confirmat cu omul)

| Ce scrie clientul | Ce avem probabil |
|---|---|
| satin matt gold · auriu satinat · gold matt | `periat-auriu` (auriu periat): **întreabă**, nu e identic |
| brushed gold | `periat-auriu` |
| black matt · negru mat | `negru` |
| white · alb | `alb` |
| brass · alamă | la Vectis: `periat-auriu` sau un efect; la produsele fixe: caută cu `arc_cauta` |
| orice cod RAL / NCS | se face la comandă: notează codul în `note` |
