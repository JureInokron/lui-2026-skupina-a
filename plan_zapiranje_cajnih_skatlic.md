# LUI Scaleup Journey 2026 · Skupina A · Avtomatsko zapiranje čajnih škatlic (LUI-RFQ-01)

Plan za delo skupine in za 8-minutno predstavitev. Sestavljeno 31. 10. 2026 iz povpraševanja (PDF LEOSS), večernega pogovora 30. 10. in jutranjih navodil 31. 10. Internet je dovoljen (včerajšnja prepoved je bila šala).

---

## 1. Zahteve naročnika (vse, kar je predavatelj povedal)

| Zahteva | Vrednost | Vir |
|---|---|---|
| Kapaciteta | **7 do 10 škatlic/min** (pravi projekt: 8, nato 17) | jutro / večer |
| Dolžina našega sistema | **največ 2 m**, vgrajen v linijo med dovod in odvod | jutro |
| Vhod in izhod | s transportnega traku na naš del, naprej na trak proti pakiranju | jutro |
| Lega škatlice | **vedno kratka stranica naprej** (short side leading), vedno enako | jutro |
| Formati | **dolžina enaka, širina in višina različni** | jutro |
| Serija | en šiht = ena serija (8 ur), tipi se ne mešajo | jutro |
| Menjava formata | **3 minute, en operater** | jutro |
| Lepilo | hot melt; **linija po celi dolžini** na pripravljenem pasu, **stransko samo pike** (da ne prideš s prstom vmes); odmik od roba vedno enak → parametrizirano | jutro |
| Škatlica | pride zaprta, odprt je samo zgornji pokrov; mala stranska krilca so »vedno največji problem« | večer |
| Kaj hoče videti | koncept, blokovna shema, risba (2D/3D, na roke ali z AI), izbira sistemov, izračun hitrosti in dolžine transporta, **kalkulacija** | jutro |
| Kaj hoče slišati | kateri PLC, kako poganjamo (elektromotorji ali pnevmatika), kako zagotovimo varnost, ocena tveganja, cena razbita na: **mehanika, elektro, elektro omara, stroj za lepljenje, montaža** | jutro (Jure) |
| Predstavitev | 8 min + 4 min vprašanj | PDF |
| Vprašanja | predavatelj ali Nejc | jutro |

Škatlica iz posnetka: Everton »La Tisana di Natale«, 20 vrečk, približno **L 130 × Š 75 × V 60 mm** (odokativno). Pokrov s tečajem na zadnjem dolgem robu in jezičkom spredaj, dve mali prašni krilci na kratkih stranicah. Zunaj lakirano; pas za lepilo je »pripravljen« (verjetno nelakiran).

## 2. Lekcije predavatelja, ki jih vrnemo v rešitvi (točke)

- izpih z zrakom je odpovedal (vrtna cev, kompresor, premalo zraka, škatlica se obrne in zatakne) → **potiskač za izmet, lasten zračni rezervoar, tlačno stikalo, alarm**;
- cilinder prepočasen, »giljotina«, roka vmes → **zaprta postaja s stikali na vratih, brez prostih gibov**;
- slabo zalepljene škatlice in »tampon« (nitka) → zastoj kot slap nazaj po liniji → **senzor nabiranja na izhodu, stop dovoda, šoba brez nitkanja**;
- leseni rob, kamor se zatika → **gladka vodila brez robov**;
- fleksibilni verižni transporter, ki ga režeš na mestu → **enako za naš vhod/izhod**.

## 3. Izračun (hitrost, dolžina, takt)

Takt pri 10/min = **6 s na škatlico** (pri 7/min 8,6 s). Načrtujemo na 10/min z rezervo do 12/min.

**Različica A, taktna postaja (škatlica se ustavi):**
stop in fiksiranje 0,3 s + zapogib krilc 0,5 s + nanos lepila 1,0 s + zapogib pokrova 0,8 s + stisk 1,0 s + sprostitev 0,3 s = **okoli 4 s** → 10/min gre z 2 s rezerve. V teh 2 s se škatlica premakne za korak 0,6 m → trak med postajami **18 m/min**. Pritisk se nadaljuje na izhodu pod pritisnim trakom (izhodni trak 6 m/min, 0,7 m = 7 s pritiska).

**Različica B, kontinuirni tok (škatlica se ne ustavi):**
razmak med škatlicami p = 0,3 m → hitrost traku v = 10/min × 0,3 m = **3 m/min**. Škatlica je v 2 m sistemu 40 s. Tudi če je v sistemu samo ena škatlica naenkrat: 2 m v 6 s = **20 m/min**. Hitrost traku je torej med 3 in 20 m/min, kar je zelo udobno; pri **6 m/min** je linija lepila (130 mm) nanesena v 1,3 s, pritisni trak dolžine 0,7 m drži 7 s (hot melt se prime v 1 do 3 s). Za primerjavo: linija v Đurđevcu teče 200 škatel/min, torej okoli 60 m/min.

**Razporeditev 2 m (obe različici):** vhod in poravnava 0,4 m · zapogib krilc in nanos lepila 0,6 m · zapiranje pokrova 0,3 m · pritisni trak in kontrola 0,7 m = 2,0 m.

## 4. Koncept (blokovna shema)

VHOD (trak linije) → poravnava ob desno vodilo, senzor prisotnosti → ZAPOGIB MALIH KRILC (prvo in zadnje krilce, prsti ali vodila) → NANOS LEPILA (pike na krilci od zgoraj, linija po celi dolžini na pripravljen pas; proženje po enkoderju, odmik od roba iz recepta) → ZAPIRANJE POKROVA (vrtljiva lopatica ali kriv vodilo) → PRITISK (pritisni trak nad škatlico, čas iz recepta) → KONTROLA (senzor ravnosti pokrova + senzor prisotnosti lepila) → IZMET (potiskač v zabojnik) → IZHOD (trak proti pakiranju).

**Odločitev skupine (pogovor 31. 10. ob 10:23): trak teče ves čas, pogon samo od spodaj**, brez jermena, ki bi škatlico držal 2 m (»to je zelo zahtevno, zmečka«). Škatlice pridejo naključno (potrdil Jang), zato je prvi stage zadrževalnik. Razmak 20 do 30 cm, okno za stiskanje do 60 cm. Zaporedje (najprej zgoraj, sicer se škatla odpre):

1. **Zadrževalnik** (stop in spust na enak razmak, škatlice pridejo naključno)
2. **Poravnava**: potisk ob desni rob (flat board)
3. **Lepilo na zgornji pas** (linija po celi dolžini)
4. **Zapiranje pokrova** in tiščanje od zgoraj
5. **Odpiranje/stiskanje stranskih krilc**
6. **Nozli od strani**: pike lepila
7. **Stiskanje** do konca (sekunda ali več na traku, ne prej, da se ne odlepi)
8. **Fotosenzor nad pokrovom** (ne kamera): ali je ostal odprt; napako zapiše in označi, **linije ne ustavi** in nima kretnice (cenejše; izmet kasneje na pakiranju). Primer Volkswagen: linija teče naprej, manjkajoče se dopolni potem.

Odprto: lopatke za siguren poriv (gladek trak ne vleče zanesljivo) ali dovolj zadrževalnik + trenje.

**Prejšnji predlog: A, taktna postaja + pritisk med izhodom.** Zakaj: natančna lega pri nanosu lepila na mala krilca (največji problem), neodvisno od točnosti dovoda, lahko preizkusimo na vsakem formatu posebej; pri 6 s na škatlico je časa dovolj. Pritisk opravimo med vožnjo ven, da 2 m dobro izkoristimo.

**Alternativa: B, kontinuirni tok** s krivimi vodili za zapogib in nanosom med vožnjo. Prednosti: manj gibljivih delov, višja kapaciteta (do faze 2 na 17/min brez predelav). Slabosti: nanos lepila med vožnjo je občutljiv na lego in hitrost, mala krilca pri različnih širinah rabijo prilagoditev vodil, težja menjava v 3 minutah. Zato jo ponudimo kot pot za fazo 2 ali kot cenejšo osnovno različico, če naročnik sprejme tveganje.

## 5. Izbira sistemov (odgovori na njegova vprašanja)

| Vprašanje | Naša izbira | Zakaj |
|---|---|---|
| PLC | Siemens S7-1200 + zaslon KTP700 (Beckhoff, če servo osi) | standard v slovenski industriji, servis, recepti, enkoder vhod |
| Pogon transporta | elektromotor z reduktorjem in frekvenčnikom (SEW ali Nord), enkoder na traku | hitrost nastavljiva, trak kot v liniji, enkoder za proženje lepila |
| Zapogib krilc in pokrova, pritisk | pnevmatski cilindri z regulacijo hitrosti in senzorji končne lege | poceni, hitro, dovolj pri 10/min |
| Zrak | lasten rezervoar, filter-regulator, tlačno stikalo, alarm pod 5 bar | lekcija iz Đurđevca |
| Različica brez pnevmatike (če naročnik noče zraka) | električni cilindri ali servo osi (+ 8 do 12 k€) | brez kompresorja, več nastavljivosti, dražje |
| Stroj za lepljenje | hot melt enota (Nordson ProBlue ali Robatech), 2 greti cevi, 1 modul za linijo + 1 modul za pike, senzor lepila | serijsko preizkušeno, proženje po enkoderju, temperatura v receptu |
| Menjava formata v 3 min | ročne ročice s števci položaja (širina in višina), vrednosti iz recepta na zaslonu; dolžina enaka, zato lepilo ostane | en operater, brez orodja; premium: servo osi, menjava s pritiskom na gumb |
| Kontrola | optični senzor ravnosti pokrova + senzor lepila (ali UV-dodatek) | vsaka škatlica dobi DA/NE, števec izmeta |
| Izmet | mehanski potiskač | zanesljivejši od izpiha |

## 6. Varnost in ocena tveganja

- Postaja zaprta s polikarbonatnimi pokrovi, vrata z varnostnim stikalom (Schmersal/Pilz), zaustavitev v izklopu (STO na frekvenčniku, odzračenje pnevmatike), gobasti izklop, dvoročni zagon ni potreben.
- Varnostni rele ali varnostni PLC (S7-1200F) po EN ISO 13849-1, zahtevana raven PLd za vrata pri gibajočih delih in vročem lepilu.
- Nevarnosti po ISO 12100: vroče lepilo 160 do 180 °C (opekline, hlapi → lokalni odses), stisk med cilindri, ujetje pri pritisnem traku, poseg ob zastoju. Ukrepi: zaščite, prekinitev gibanja ob odprtju, varen način za čiščenje šobe (stroj ustavljen, lepilo na čakanju).
- CE: nepopoln stroj v liniji ali samostojen stroj; Direktiva o strojih 2006/42/ES, od januarja 2027 Uredba (EU) 2023/1230. Priložimo oceno tveganja, izjavo in navodila.
- Hrana: lepilo s potrdilom za posredni stik z živili, deli brez odprtih maziv.

## 7. Podatki, ki jih rabimo za potrditev (RFQ to zahteva)

1. mere vseh formatov (širina, višina) in geometrija zavihkov, koliko formatov;
2. hitrost in razmak škatlic na dovodnem traku, kako jih stroj pred nami oddaja;
3. kje točno je pas za lepilo, ali je nelakiran; dovoljeno lepilo (stik z živili), ali ga že uporabljajo;
4. zrak (tlak, pretok) in elektrika na mestu, prostor okoli 2 m (širina, višina, dostop);
5. merila kakovosti: kaj je »pravilno zaprto«, dovoljen izmet, kam z izmetom;
6. signali linije: start/stop, zastoj za nami, zastoj pred nami.

## 8. Tveganja (3 največja + 2)

1. **oprijem lepila na lakiranem kartonu** → test lepljenja na vzorcih v tednu 1, izbira lepila z dobaviteljem;
2. **mala krilca** (odskok, različne širine) → prsti z nastavljivim hodom, test vseh formatov pri FAT;
3. **lega na vhodu** (stroj pred nami ni naš) → poravnava ob desno vodilo, senzor prisotnosti, čakanje na prazno postajo;
4. nitkanje lepila in zastoji → šoba z rezom, senzor nabiranja, stop dovoda;
5. menjava v 3 min → merjena pri FAT z operaterjem naročnika.

## 9. Kalkulacija (razbita, kot jo hoče)

**Zamenjano s podrobno kalkulacijo v `kalkulacija_bom.md` (≈ 66.300 € prodajna cena).** Spodnja tabela je bila prva groba ocena.

| Sklop | Vsebina | Okvirno |
|---|---|---|
| Mehanika | okvir, transporter 2 m, vodila, zapogibala, pritisni trak, formatni deli z ročicami, zaščite | 25 do 35 k€ |
| Elektro | motor z reduktorjem, frekvenčnik, enkoder, senzorji, pnevmatski ventili in cilindri, kabli, rezervoar | 8 do 12 k€ |
| Elektro omara | PLC, zaslon, varnostni rele, napajanje, ožičenje, program in recepti | 12 do 18 k€ |
| Stroj za lepljenje | hot melt enota, 2 cevi, 2 modula, senzor lepila, prvi nasip lepila | 10 do 18 k€ |
| Montaža | sestava, FAT pri nas, SAT v liniji, šolanje, dokumentacija, CE | 8 do 12 k€ |
| Inženiring | koncept, konstrukcija, test lepljenja (če ni že v sklopih) | 12 do 20 k€ |
| **Skupaj** | | **okoli 75 do 115 k€** |

Pripravi **osnovno in polno različico**: osnovna brez senzorja lepila, ročna menjava formata, pnevmatika (okoli 75 k€); polna s servo menjavo formata in električnimi osmi (okoli 110 k€). Ko pride »kregánje«, imaš odgovor takoj.

## 9a. Povračilo investicije (ROI)

Predpostavke (povej jih na glas, naročnik jih popravi): zdaj ročno zapiranje, 1 operater na izmeno, strošek delodajalca okoli 30 €/h; 1 izmena/dan, 230 dni/leto → **okoli 55.000 €/leto** samo za ena izmena (2 izmeni okoli 110.000 €). Stroški stroja na leto: lepilo, elektrika in zrak 3 do 5 k€, vzdrževanje 2 do 3 k€.

| | Osnovna (~75 k€) | Polna (~110 k€) |
|---|---|---|
| Prihranek 1 izmena | ~48 k€/leto neto | ~48 k€/leto neto |
| Povračilo 1 izmena | **~1,6 leta** | **~2,3 leta** |
| Povračilo 2 izmeni | **~0,8 leta** | **~1,1 leta** |

Plus, ki ga ne štejemo v evrih: manj reklamacij zaradi odprtih škatlic, stalna kakovost, operater gre na drugo delo. Tipična meja za odobritev v industriji je 2 do 3 leta, torej smo notri.

## 10. Faze in merila uspešnosti

Faze: (1) vzorci vseh formatov in test lepljenja, 1 do 2 tedna · (2) koncept in postavitev, potrditev · (3) konstrukcija in nabava, 4 do 6 tednov · (4) izdelava in program, 4 do 6 tednov · (5) FAT: 500 škatlic na format + merjena menjava formata · (6) montaža v linijo, SAT, šolanje · (7) spremljanje prvi mesec, nato faza 2 (17/min).

Merila: pravilno zaprtih ≥ 99,5 %, napačen izmet ≤ 0,5 % · 10/min 8 ur brez zastoja po naši krivdi, razpoložljivost ≥ 95 % · menjava formata ≤ 3 min, en operater, brez orodja · spoj: pokrov se trga po kartonu, ne po lepilu · čiščenje šobe ≤ 10 min.

## 11. Delo skupine (90 minut)

| Čas | Kaj | Kdo |
|---|---|---|
| 0 do 10 | Odločite: A (taktno) kot glavno, B alternativa; zaporedje zapiranja; kje linija in kje pike; izmet s potiskačem. Dve vprašanji Nejcu ali predavatelju (pas za lepilo, dovod). | vsi |
| 10 do 40 | Risar: blokovna shema + skica 2 m postaje z merami zon. Kalkulant: tabela iz točke 9, osnovna/polna. Tehnik: izbira sistemov (točka 5), varnost (6), izračun (3). Četrti: podatki, tveganja, faze, merila. | vzporedno |
| 40 do 55 | Sestavite zgodbo v 8 minut, kdo pove kaj. | vsi |
| 55 do 70 | Vaja s štoparico na glas. | vsi |
| 70 do 90 | Odgovori na pričakovana vprašanja, rezerva. | vsi |

## 12. Predstavitev (8 minut)

1. (0:30) Kaj smo razumeli: 7 do 10/min, 2 m v liniji, kratka stranica naprej, dolžina enaka, širina in višina različni, menjava 3 min, linija + pike hot melta.
2. (1:00) Blokovna shema in razporeditev 2 m.
3. (2:00) Glavni koncept A po korakih na skici, izračun takta in hitrosti.
4. (1:30) Izbira sistemov: PLC, pogoni (elektro + pnevmatika z lastnim zrakom), hot melt, kontrola, menjava formata v 3 min.
5. (0:45) Varnost in ocena tveganja v treh stavkih.
6. (0:45) Alternativa B in zakaj ni prva.
7. (1:00) Kalkulacija po sklopih, osnovna/polna, faze, merila.
8. (0:30) Kaj rabimo od naročnika (vzorci, lepilo, mere, signali).

## 13. Pričakovana vprašanja

- Zakaj taktno in ne kontinuirno? (natančnost na malih krilcih, test po formatih, časa je dovolj; B ostane za fazo 2)
- Kako v 3 minutah? (dve ročici s števci + recept; dolžina enaka, zato lepilo ne spreminjamo; servo kot opcija)
- Zakaj pnevmatika, če je zrak težava? (lasten rezervoar in nadzor; brez zraka za +8 do 12 k€)
- Kaj če lak odbija lepilo? (test v fazi 1, pas za lepilo, drugo lepilo)
- Kako veste, da je zaprta prav? (senzor ravnosti + senzor lepila, DA/NE na vsako)
- Kaj ob zastoju? (senzor nabiranja, stop dovoda, dostop z vrati, varen način)
- Kaj odvzamete pri nižjem budgetu? (osnovna različica)
- Kako do 17/min? (B ali dvojna postaja, mehanika že dimenzionirana)
