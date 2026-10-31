# Stroj za zapiranje čajnih škatlic: rešitve, kosovnica in kalkulacija

Skupina A, LUI 2026, 31. 10. 2026. Podlaga je debata skupine (`zapiski/2026-10-31_debata_sestava_masine.md`), skica je v `skica_sistema.svg`.
Cene so **nabavne, brez DDV**. Kjer imamo Inokronove podatke, so označene z **[INO]** (dejanski računi in kalkulacije), ostale so tržne ocene **[ocena]**.

---

## 1. Transporter in hitrost

- Dolžina 2.000 mm, širina traku 300 mm (dovolj za vse formate), živilski PU/PVC trak, okvir inox.
- **Hitrost: »6 s na 2 m« = 2 m / 6 s = 0,33 m/s = 20 m/min.**
- **Pozor, protislovje, ki ga je treba razčistiti z naročnikom:**
  - če je kapaciteta 7 do 10 škatel/min in je razmak med njimi okoli 25 cm (7 do 10 na 2 m), mora trak teči **1,75 do 2,5 m/min**;
  - če trak teče 20 m/min in je na njem 7 do 10 škatel, gre skozi **70 do 100 škatel/min**, kar je 10-krat več od zahteve;
  - pri 20 m/min in 7 do 10 škatlah/min je na 2 m naenkrat samo **ena škatla** (razmak 2 do 3 m).
- **Naša rešitev:** frekvenčnik in nastavljiva hitrost **2 do 20 m/min**, usklajena z obstoječim dovodom (signal hitrosti ali enkoder z linije). Vsi stagi so narejeni tako, da delujejo v celem območju (stisk ≥ 1 s je pri 20 m/min 0,33 m jermena, mi imamo 0,4 m).
- Kapaciteta, ki jo zagotavljamo: **do 12 škatel/min** pri razmaku ≥ 20 cm. Omejitev je hitrost hot melt nanosa na majhnih krilcih, ne trak.

## 2. Tri rešitve za stisk in lepljenje na premikajočem se traku

| | A. Fiksne šobe + pritisni jermeni (PRIPOROČENO) | B. Leteča linearna os (manipulator vzporedno s trakom) | C. Robotska roka / gimbal |
|---|---|---|---|
| Kako | Šobe so pritrjene, enkoder jih proži točno, ko gre škatla mimo (začetek in konec po S2). Pokrov zapre inox vodilo (plug), drži ga zgornji pritisni jermen, krilca stranska jermena; vsi jermeni tečejo z isto hitrostjo kot trak. | Voziček na linearni osi se spusti, prime škatlo, pelje z njo 1 s (pri 3 m/min samo 5 cm, pri 20 m/min 33 cm), nanese/stisne, dvigne, vrne. | Robot z orodjem sledi škatli, nanaša lepilo in stiska. |
| Prednosti | Standard pri zapiralnikih kartonov. Lepilne cevi so fiksne. En pogon za vse (jermeni prek jermenic z glavnega traku). Najceneje, najbolj zanesljivo. | Natančen stisk z nadzorom sile. Ena os za več formatov. | Najbolj prilagodljivo. |
| Slabosti | Za vsak format nastavitev višine in širine (ročica s števcem, v 3 min gre). | Servo os + krmiljenje, vrnitev v izhodišče omeji kapaciteto, gibljiva cev za lepilo. | Drago (25 do 40 k€ samo robot), počasno, nenatančno sledenje, zahtevna varnost. |
| Cena dodatno | izhodišče | **+ 6.000 do 9.000 €** | **+ 30.000 do 45.000 €** |

Rešitev z jermenom z več nastavki in šobami, ki se vozijo s trakom, smo zavrnili: 6 premičnih šob, lepila ne spraviš okoli.

## 3. Potek (stagi) in kosovnica

| # | Stage | Kaj se zgodi | Glavni elementi |
|---|---|---|---|
| 1 | Vhod, zadrževalnik | S1 zazna škatlo, C1 jo zadrži in spusti na enakomeren razmak po enkoderju | S1, C1, enkoder RLS |
| 2 | Poravnava | Levo nastavljivo vodilo potisne škatlo ob desno fiksno vodilo (flat board) | vodili, ročica + števec |
| 3 | Lepilo zgoraj | S2 zazna začetek in konec, G1 nariše linijo po celi dolžini | S2, G1 |
| 4 | Zapiranje pokrova | Inox vodilo (plug) zapre pokrov, zgornji jermen ga drži | plug, zgornji jermen |
| 5 | Stranska krilca | Vodila zapreta krilca, G2 in G3 naneseta pike; S3 med tem preveri, ali je pokrov zaprt | G2, G3, S3 |
| 6 | Stisk | Zgornji in stranska jermena stisnejo škatlo ≥ 1 s | jermeni |
| 7 | Izhod | Slaba škatla (iz S3) gre s potiskačem P v zabojnik, ostale na obstoječi odvod | P, zabojnik |

### Kosovnica (BOM), nabavne cene

**A. Mehanika (material)**
| Pozicija | Kol. | Cena | Vir |
|---|---|---|---|
| Trak živilski PU/PVC 2.000 × 300 mm, brezkončni | 1 | 180 € | [INO] po naših nabavnih cenah |
| Okvir in stranice inox AISI 304, 3 mm, laser + krivljenje | 1 | 950 € | [ocena] |
| Pogonski in obračalni valj, gredi, ležaji UCF (4) | 1 | 380 € | [ocena] |
| Nastavljive noge inox | 4 | 160 € | [ocena] |
| Vodili (desno fiksno, levo nastavljivo), vreteno, linearna vodila, 2 ročici s števcem položaja | 1 | 540 € | [ocena] |
| Inox vodilo za zapiranje pokrova (plug) | 1 | 450 € | [ocena] |
| Zgornji pritisni jermen 0,4 m z nastavitvijo višine, jermenice | 1 | 1.400 € | [ocena] |
| Stranska pritisna jermena 0,4 m z vodili za krilca | 2 | 1.600 € | [ocena] |
| Vodila za zapiranje stranskih krilc | 1 | 400 € | [ocena] |
| Zaščitni pokrovi polikarbonat + inox okvir, vrata | 1 | 900 € | [ocena] |
| **Skupaj mehanika** | | **6.960 €** | |

**B. Elektro in pnevmatika na stroju**
| Pozicija | Kol. | Cena | Vir |
|---|---|---|---|
| Motor z reduktorjem 0,37 kW | 1 | 650 € | [ocena] |
| Enkoder RLS Orbis 16 + magnet + kabel 3 m | 1 | 135 € | [INO] po naših nabavnih cenah |
| Cilinder zadrževalnika Ø16 | 1 | 120 € | [ocena] |
| Fotosenzorji S1, S2 (začetek/konec) | 3 | 270 € | [ocena] |
| Senzor zaprtosti pokrova S3 (laserski, razdalja) | 1 | 350 € | [ocena] |
| Potiskač izmeta: cilinder Ø25 + ventil + zabojnik | 1 | 350 € | [ocena] |
| Pnevmatika: pripravna skupina, varnostni odzračevalni ventil, tlačno stikalo, ventilski otok, cevi, rezervoar 5 L | 1 | 980 € | [ocena] |
| Varnostna stikala na vratih (2), gobasta izklopa (2), svetlobni stolpec | 1 | 510 € | [ocena] |
| **Skupaj elektro** | | **3.365 €** | |

**C. Elektro omara**
| Pozicija | Kol. | Cena | Vir |
|---|---|---|---|
| Omara 600 × 600 | 1 | 450 € | [ocena] |
| PLC Siemens S7-1200 (1214C) + I/O modul | 1 | 650 € | [ocena] |
| HMI Siemens KTP700 (recepti formatov) | 1 | 750 € | [ocena] |
| Frekvenčnik 0,37 kW | 1 | 220 € | [ocena] |
| Varnostni rele (Pilz PNOZ) | 1 | 250 € | [ocena] |
| Napajalnik 24 V, glavno stikalo, varovalke, sponke, kabli | 1 | 600 € | [ocena] |
| Kabli do senzorjev, police | 1 | 300 € | [ocena] |
| Vmesnik do obstoječe linije (start/stop, zastoj, hitrost) | 1 | 150 € | [ocena] |
| **Skupaj omara** | | **3.370 €** | |

**D. Stroj za lepljenje (hot melt)**
| Pozicija | Kol. | Cena | Vir |
|---|---|---|---|
| Hot melt enota 4 kanali, tank 4 L (Robatech / Nordson) | 1 | 7.000 € | [ocena] |
| Grete cevi 1,2 m | 3 | 1.350 € | [ocena] |
| Nanosni moduli (G1 linija, G2 in G3 pike) | 3 | 1.950 € | [ocena] |
| Krmilnik vzorca nanosa (po enkoderju) | 1 | 1.200 € | [ocena] |
| **Skupaj lepljenje** | | **11.500 €** | |

**Material skupaj: 25.195 €**

## 4. Delo

Strošek ure **55 €/h** (z režijo, predpostavka).

| Delo | Ure | Znesek |
|---|---|---|
| Planiranje: konstrukcija, risbe, ocena tveganja, CE dokumentacija | 140 | 7.700 € |
| Izdelava in sestava mehanike | 100 | 5.500 € |
| Elektro: ožičenje omare in stroja | 40 | 2.200 € |
| Programiranje PLC + HMI, recepti formatov | 50 | 2.750 € |
| Preizkus v delavnici (FAT, 500 škatel na format) | 16 | 880 € |
| Montaža v linijo (2 osebi) | 16 | 880 € |
| Zagon, šolanje operaterjev | 16 | 880 € |
| **Delo skupaj** | **378 h** | **20.790 €** |

## 5. Razdelitev in prodajna cena

| Sklop | Material | Delo | Skupaj |
|---|---|---|---|
| Planiranje | | 7.700 € | 7.700 € |
| Mehanika | 6.960 € | 5.500 € | 12.460 € |
| Elektro (stroj + programiranje) | 3.365 € | 2.750 € | 6.115 € |
| Elektro omara | 3.370 € | 2.200 € | 5.570 € |
| Stroj za lepljenje | 11.500 € | | 11.500 € |
| Montaža | 400 € prevoz | 880 € | 1.280 € |
| Zagon (FAT + zagon pri stranki) | | 1.760 € | 1.760 € |
| **Lastna cena** | | | **46.385 €** |
| Rezerva za nepredvideno 10 % | | | 4.640 € |
| **Lastna cena z rezervo** | | | **51.025 €** |
| **Dodatek 30 % (marža)** | | | **15.310 €** |
| **Prodajna cena** | | | **≈ 66.300 € brez DDV** |

Preverba po pravilu, ki ga je dal predavatelj (od prodajne cene **15 % planiranje, 20 % elektro**):
- planiranje 15 % = 9.950 €, mi imamo 7.700 € (12 %) → ali dodamo 40 ur konstrukcije ali argumentiramo, da je stroj enostaven;
- elektro 20 % = 13.260 €, mi imamo elektro + omara = 11.685 € (18 %) → v okviru.

**Opcije za ceno:**
- svetlobna zavesa na vhodu in izhodu namesto zaprtih tunelov: + 1.500 €;
- servo nastavitev formata s pritiskom na gumb namesto ročic: + 6.000 €;
- leteča linearna os (rešitev B): + 6.000 do 9.000 €.

## 6. Kaj dobi stranka (povračilo investicije)

Predpostavke (stranka jih popravi):
- ročno zapiranje in lepljenje z ročno pištolo traja **6 do 9 s na škatlo**, za 7 do 10 škatel/min je torej potreben **1 človek ves čas na izmeno**;
- strošek delavca **30 €/h**, izmena 8 h, 230 dni na leto → **55.200 €/leto na izmeno**;
- stroj še vedno rabi nekaj nadzora (polnjenje lepila, menjava formata, izmet): 1/4 človeka → ostane **41.400 €/leto prihranka na izmeno**;
- obratovalni stroški stroja: lepilo ~0,3 g/škatlo, 4.800 škatel na izmeno → ~1.400 €/leto; elektrika ~3 kW × 8 h → ~1.100 €/leto; vzdrževanje ~1.500 €/leto → **~4.000 €/leto**.

| | 1 izmena | 2 izmeni | 3 izmene |
|---|---|---|---|
| Neto prihranek na leto | ~37.400 € | ~74.800 € | ~112.000 € |
| **Povračilo pri 66.300 €** | **~1,8 leta** | **~0,9 leta** | **~0,6 leta** |

Zraven, a brez evrov: stalna kakovost zapiranja, manj reklamacij, sledljivost izmeta, delavec gre na drugo delo.

## 7. Tveganja, HACCP, varnost pri delu

**HACCP:** čaj je v vrečkah in škatli, stroj ni v neposrednem stiku z živilom, zato **HACCP certifikacija stroja ni potrebna**. Ker je škatla zgoraj odprta, kljub temu upoštevamo higiensko izvedbo: inox AISI 304, brez odprtih maziv nad škatlo (maziva H1), lepilo s potrdilom za posredni stik z živili, gladke površine za čiščenje.

**Varnost pri delu (ocena tveganja po ISO 12100):**
| Nevarnost | Ukrep |
|---|---|
| Vroče lepilo 160 do 180 °C, opekline, hlapi | zaprta zaščita, opozorilne oznake, rokavice pri polnjenju, po potrebi lokalni odsesovalnik |
| Stisk in ujetje med jermeni in valji | fiksni pokrovi, vrata z varnostnimi stikali (ob odprtju se ustavi pogon, odzrači pnevmatika, šobe se zaprejo) |
| Poseg v stroj na vhodu ali izhodu | odprtini tunela samo za višino škatle, varnostne razdalje po ISO 13857; opcija: svetlobna zavesa |
| Zastoj, operater sega po škatlo | gobasta izklopa na obeh straneh, ponovni zagon samo s tipko |
| Izpad zraka (lekcija iz Đurđevca) | tlačno stikalo, alarm pod 5 bar, lasten rezervoar |
| Varnostna funkcija | varnostni rele, raven PLd po ISO 13849-1 |

**Tehnična tveganja:**
1. lepilo se ne prime laka → test lepljenja na vzorcih pred konstrukcijo;
2. mala krilca odskočijo → stranska jermena in vodila z nastavitvijo, test vseh formatov pri FAT;
3. škatle prihajajo naključno → zadrževalnik C1 in enkoder;
4. zastoj za nami (slap nazaj) → senzor nabiranja na izhodu ustavi zadrževalnik, trak se izprazni;
5. menjava formata v 3 min → dve ročici s števcem in tabela formatov na zaslonu, preverjeno pri FAT s štoparico.

**CE:** stroj se vgradi v linijo; izjava o skladnosti, ocena tveganja in navodila so v ceni (planiranje). Od 20. 1. 2027 velja Uredba o strojih (EU) 2023/1230.

---

## 8. Varianta 2: optimizirani stroški (izdelava in montaža pri kooperantu v Srbiji)

Kaj spremenimo glede na varianto 1:

| Sprememba | Prej | Zdaj | Razlika |
|---|---|---|---|
| Stroj za lepljenje (enota, cevi, šobe), proženje šob kar iz PLC po enkoderju, brez posebnega krmilnika vzorca | 11.500 € | 6.000 € | −5.500 € |
| Mali motor z reduktorjem (trak je lahek, škatle ~100 g) | 650 € | 250 € | −400 € |
| Manjši frekvenčnik | 220 € | 150 € | −70 € |
| Stranska pritisna jermena → vzmetna inox vodila (krilca so majhna, jermen ni nujen) | 1.600 € | 600 € | −1.000 € |
| Laserski senzor pokrova S3 → navaden fotosenzor | 350 € | 120 € | −230 € |
| HMI 7" → 4" (recepti formatov gredo tudi na manjšem) | 750 € | 450 € | −300 € |
| Izdelava in sestava mehanike, ožičenje, montaža (156 h) v Srbiji: 25 €/h namesto 55 €/h | 8.580 € | 3.900 € | −4.680 € |
| Dodatno: koordinacija in kontrola kakovosti pri kooperantu (16 h, naši) | | 880 € | +880 € |
| Dodatno: programiranje proženja šob v PLC (8 h) | | 440 € | +440 € |
| Dodatno: prevoz iz Srbije + carinjenje (z EUR.1 je carina 0 %) | | 720 € | +720 € |

Planiranje, programiranje, preizkus (FAT) in zagon pri stranki ostanejo pri nas, ker je tam znanje.

### Razdelitev variante 2

| Sklop | Material | Delo | Skupaj |
|---|---|---|---|
| Planiranje (140 h, naši) | | 7.700 € | 7.700 € |
| Mehanika | 5.960 € | 2.500 € (Srbija) | 8.460 € |
| Elektro (stroj + programiranje) | 2.735 € | 3.190 € | 5.925 € |
| Elektro omara | 3.000 € | 1.000 € (Srbija) | 4.000 € |
| Stroj za lepljenje | 6.000 € | | 6.000 € |
| Montaža | 400 € prevoz | 400 € (Srbija) | 800 € |
| Zagon (FAT + zagon pri stranki) | | 1.760 € | 1.760 € |
| Logistika in kontrola pri kooperantu | 720 € | 880 € | 1.600 € |
| **Lastna cena** | | | **36.245 €** |
| Rezerva 10 % | | | 3.625 € |
| **Lastna cena z rezervo** | | | **39.870 €** |
| Dodatek 30 % | | | 11.960 € |
| **Prodajna cena** | | | **≈ 51.800 € brez DDV** |

**Prihranek proti varianti 1: okoli 14.500 € (−22 %).**

Preverba po pravilu: planiranje 7.700 € = **15 %**, elektro + omara 9.925 € = **19 %**. Zdaj se oboje ujema s 15 % in 20 %.

Povračilo za stranko pri 51.800 €: **~1,4 leta** pri eni izmeni, **~0,7 leta** pri dveh.

### Na kaj paziti pri varianti 2
- **Kakovost varjenja inoxa** pri kooperantu: zahtevamo vzorčni zvar in fotografije pred odpremo, prevzem pri njih (zato 16 h koordinacije).
- **EUR.1** (potrdilo o poreklu) mora kooperant izdati, sicer se plača carina.
- **Popravki po montaži so dlje**: zato FAT pri nas, preden gre stroj k stranki.
- **Cenejši hot melt**: preveriti rezervne dele in servis v regiji stranke.
- Druga možnost: prodajna cena ostane okoli 66.300 €, razlika gre v maržo (dodatek okoli 66 % namesto 30 %, zaslužek okoli 26.400 € namesto 11.960 €).
