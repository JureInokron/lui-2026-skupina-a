# Naloga 2: avtomatska kontrola jabolčnega čipsa (LUI-RFQ-02)

Osnova: povpraševanje (PDF, stran 2) in ustna navodila naročnika 31. 10. ob 11:28. Enako kot pri prvi nalogi: **konstrukcija in cena**.

## Kaj je povedal naročnik

| Zahteva | Vrednost |
|---|---|
| Od kod pridejo | iz sušilca, krhlji padejo na trak v razsutem toku |
| Kaj naredimo | razporedimo, pregledamo **zgoraj in spodaj** s kamerami, izločimo slabe |
| Kaj je slabo | črne pike (plesen), druge napake na rezini |
| Dobri | v **eno škatlo na koncu, pod škatlo je tehtnica** (škatla se polni po masi, ne po kosih) |
| Slabi | v drug zabojnik (ne na tla) |
| Dolžina | **največ 4 m** |
| Vhod | modri trak naročnika odstranimo, **naš trak se priklopi direktno pod sušilec** |
| Hitrost | dovod **okoli 5 m/min**; požreti moramo vse, kar pride (količina kot na videu) |
| Pogoj | **rezine se ne smejo prekrivati**, sicer jih kamera ne vidi |
| Iz PDF | nežno ravnanje, stik z živili, higiensko čiščenje, čim manj lomljenja, sledljivost, enostavne nastavitve in obravnava napak |

## Predlog poteka (4 m)

```mermaid
flowchart LR
    A[Sušilec] --> B[1 Vibracijski dodajalnik<br/>razprši po širini]
    B --> C[2 Pospeševalni trak<br/>5 → 20+ m/min<br/>rezine se razmaknejo]
    C --> D[3 Met čez rob traku<br/>kamera zgoraj + kamera spodaj<br/>v letu]
    D -->|dobra| E[4 Odvodni trak<br/>v škatlo na tehtnici]
    D -->|slaba: zračni izpih| F[Zabojnik za izmet]
```

| Odsek | Dolžina | Kaj |
|---|---|---|
| 1 Vibracijski dodajalnik | ~0,8 m | prevzame kup iz sušilca, razprši rezine po širini |
| 2 Pospeševalni trak | ~1,6 m | teče 4 do 5-krat hitreje od dovoda, zato se rezine razmaknejo in ne prekrivajo |
| 3 Pregled in izmet | ~0,4 m | rezine letijo čez konec traku; dve linijski kameri (zgoraj, spodaj) ju vidita v letu z obeh strani, šobe za zrak izpihnejo slabe |
| 4 Odvod v škatlo | ~1,2 m | dobre na kratek trak, ki jih strese v škatlo na tehtnici; ob polni masi menjava škatle |

## Izmet: kako

**Zračni izpih v letu (tako delajo optični sortirniki za suho sadje):**
- rezine zletijo z roba pospeševalnega traku v loku; točno tam sta obe kameri, ena od zgoraj in ena od spodaj, zato vidimo **obe strani brez obračanja rezine**;
- čez celo širino je **letev s hitrimi ventili** (npr. 32 do 64 šob, vsaka pokriva 10 do 20 mm širine, odziv 1 do 3 ms);
- računalnik ve, kje je slaba rezina (položaj iz slike + enkoder), in odpre samo šobo na njeni širini za nekaj milisekund;
- slaba rezina dobi kratek sunek zraka in pade v **ločen žleb za izmet**, dobre letijo naprej na odvodni trak;
- rezina tehta 1 do 3 g, zato je izpih idealen: ne dotakne se je nič, ni lomljenja, ni gibljivih delov v stiku z živilom.

**Kar se je naročnik naučil pri škatlah (izpih je odpovedal), tukaj rešimo:** lasten zračni rezervoar ob letvi, tlačno stikalo z alarmom, filter za živilski zrak (brez olja), ob padcu tlaka se dovod ustavi.

**Alternativi:**
- **mehanska loputa** pod koncem traku: deluje samo, če so rezine daleč narazen, sicer vrže ven tudi dobre; počasnejša;
- **robot z vakuumskim prijemalom (delta)**: pobere slabe s traka, nežno, a drago in pri večji gostoti ne dohaja.

## Kaj še odpreti z naročnikom
1. koliko rezin na minuto oziroma kg/h (iz videa ocenimo, potem potrdimo);
2. velikost in debelina rezin, kako so krhke in lepljive;
3. katere napake točno (črne pike, temne rezine, lomljene, tujki) in koliko lažnega izmeta je sprejemljivo;
4. masa škatle, ki jo polnimo, in kako se škatla menja;
5. prostor pod sušilcem (višina za vibracijski dodajalnik in met).

## Naslednji koraki
- [ ] iz videa oceniti, koliko rezin na minuto pride
- [ ] skica (tloris + stranski pogled)
- [ ] kosovnica in kalkulacija po sklopih (planiranje, mehanika, elektro, omara, vizija, montaža, zagon) + 30 %
- [ ] povračilo za stranko (koliko ljudi danes ročno pregleduje)
- [ ] varnost, HACCP (tu je **neposreden stik z živilom**, zato inox, živilski trakovi, čiščenje), tveganja
