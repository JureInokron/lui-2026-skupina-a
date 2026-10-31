# Kontrola jabolčnega čipsa: kosovnica (BOM) in cena

**Glavni koncept: dva traka z obračanjem rezine in dvojnim izmetom.**
Skica: [`skica_cips_obracanje.svg`](skica_cips_obracanje.svg) · 3D (Luka): [`trak-cips-2.png`](trak-cips-2.png) · Navodila: [`NAVODILA.md`](NAVODILA.md).

Cene so nabavne ocene brez DDV. **Vision sistem ima stranka že v celoti: kameri, osvetlitev, obdelava slike in njeno programiranje.** Zato ni v ceni; mi ga vgradimo v ohišje in njegov signal »slaba rezina« povežemo z našima izpihoma.

**Umeritev po prvi nalogi:** pri zapiranju škatlic je bila prava cena izvedenega projekta okoli **26.000 €**, mi smo bili skoraj 2-krat višje. Zato računamo vitko: malo planiranja, standardne komponente, izdelava pri kooperantu. Budget za čips je po besedah predavatelja **večji** kot za škatlice.

![3D koncept (Luka)](trak-cips-2.png)

## Koncept

1. **Vibracijska miza** pod sušilcem (izhod na 1 m) prevzame kup rezin in jih razprši po širini.
2. **Trak 1**, poševen ~15°, 2,2 m × 500 mm, 15 do 20 m/min: rezine se razmaknejo, prekrite na klancu zdrsnejo nazaj.
3. **Kamera 1** (zgoraj, fokus 500 mm) pri 1,7 m vidi **stran A**. Do glave traku je **0,5 m za izračun** (1,5 s pri 20 m/min).
4. **Izmet 1** na glavi traku 1: slabe rezine izpihne v zabojnik izmet 1.
5. **Obračanje:** dobre rezine padejo ~150 mm na trak 2 čez nastavljiv prag in se obrnejo.
6. **Trak 2**, vodoraven, 1,8 m × 500 mm. **Kamera 2** (zgoraj) pri 3,5 m vidi **stran B**, spet 0,5 m pred izpihom.
7. **Izmet 2** na glavi traku 2, dobre rezine po žlebu v **škatlo na tehtnici**.

**Zakaj tako:** obe kameri gledata od zgoraj in obe imata pol metra časa za izračun. Ni špranje v traku, ni kamere pod trakom, drobtine ne padajo na objektiv.

## Kosovnica

**Mehanika**
| # | Pozicija | Kol. | Cena |
|---|---|---|---|
| M0 | Vibracijska miza inox 800 × 500 mm z elektromagnetnim vibratorjem in krmilnikom | 1 | 2.200 € |
| M1 | Trak 1: poševen 2,2 m × 500 mm, živilski PU z rahlo strukturo, inox okvir, valji | 1 | 1.500 € |
| M2 | Trak 2: vodoraven 1,8 m × 500 mm, živilski PU, inox okvir, valji | 1 | 1.300 € |
| M3 | Nastavljiv prag za obračanje rezin, inox | 1 | 150 € |
| M4 | Nosilna konstrukcija in noge, inox | 1 | 600 € |
| M5 | Žleb za dobre rezine do škatle | 1 | 300 € |
| M6 | Žleb in zabojnik za izmet | 2 | 500 € |
| M7 | Ohišje vizije čez oba traka (inox + polikarbonat, zatemnjeno) | 1 | 1.200 € |
| M8 | Nosilci kamer, luči in letev šob | 1 | 300 € |
| | **Skupaj mehanika** | | **8.050 €** |

**Elektro in pnevmatika**
| # | Pozicija | Kol. | Cena |
|---|---|---|---|
| E1 | Mali motor z reduktorjem (trak 1, trak 2) | 2 | 500 € |
| E2 | Frekvenčnik | 2 | 300 € |
| E3 | Enkoder (na vsakem traku, za položaj rezine do izpiha) | 2 | 200 € |
| E4 | Letev hitrih ventilov za izpih, 32 kanalov, z izhodnim modulom | 2 | 5.400 € |
| E5 | Zrak: rezervoar 20 L, filter za zrak brez olja, regulator, tlačno stikalo | 1 | 600 € |
| E6 | Tehtnica pod škatlo (plošča, celica, pretvornik) | 1 | 600 € |
| E7 | Senzorji (škatla na mestu, škatla polna), svetlobni stolpec, gobi, varnostni stikali | 1 | 450 € |
| | **Skupaj elektro** | | **8.050 €** |

**Vizija**
| # | Pozicija | Kol. | Cena |
|---|---|---|---|
| V1 | Kameri, osvetlitev, obdelava slike in programiranje: **dobavi stranka** | 1 | 0 € |

**Elektro omara**
| # | Pozicija | Kol. | Cena |
|---|---|---|---|
| O1 | Omara, PLC S7-1200 z dodatnimi izhodi za 2 letvi, zaslon 4", varnostni rele, napajanje, kabli | 1 | 2.400 € |

**Material skupaj: 18.500 €**

## Delo

| Delo | Ure | Znesek |
|---|---|---|
| Planiranje: konstrukcija, ocena tveganja, CE | 60 h × 55 € | 3.300 € |
| Izdelava in sestava mehanike (kooperant Srbija) | 70 h × 25 € | 1.750 € |
| Ožičenje (kooperant Srbija) | 30 h × 25 € | 750 € |
| Programiranje PLC (2 traka, 2 izpiha, tehtnica) | 30 h × 55 € | 1.650 € |
| Priklop vision sistema stranke: signal slabih rezin → položaj po enkoderju → pravi ventil | 16 h × 55 € | 880 € |
| Preizkus pri nas s pravim čipsom, nastavitev obračanja (FAT) | 24 h × 55 € | 1.320 € |
| Montaža pod sušilec in zagon | 24 h × 55 € | 1.320 € |
| Logistika (prevoz iz Srbije, carinjenje, prevoz do stranke) | | 1.100 € |
| **Skupaj** | | **12.070 €** |

## Razdelitev in prodajna cena

| Sklop | Skupaj |
|---|---|
| Planiranje | 3.300 € |
| Mehanika (vibracijska miza, 2 traka, ohišje + izdelava) | 9.800 € |
| Elektro (pogoni, 2 izpiha, zrak, tehtnica + programiranje) | 9.700 € |
| Priklop vision sistema stranke | 880 € |
| Elektro omara (+ ožičenje) | 3.150 € |
| Preizkus pri nas | 1.320 € |
| Montaža in zagon | 1.320 € |
| Logistika | 1.100 € |
| **Lastna cena** | **30.570 €** |
| Rezerva 10 % | 3.060 € |
| **Lastna cena z rezervo** | **33.630 €** |
| Dodatek 30 % | 10.090 € |
| **Prodajna cena** | **≈ 43.700 € brez DDV** |

Največji posamezni del sta **dve letvi za izpih** (5.400 €). Planiranje je 8 % cene.

**Če je treba ceneje:**
- 16 namesto 32 ventilov na letev: −2.400 € (slabša ločljivost izmeta);
- brez tehtnice, polnjenje po času: −600 €;
- en trak brez obračanja, s kamero spodaj v letu (alternativa spodaj): okoli −8.500 €.

## Povračilo za stranko

Predpostavka: ročno pregleduje in sortira **1 do 2 človeka na izmeno** (30 €/h, 8 h, 230 dni = 55.200 €/leto na osebo). Stroj rabi 1/4 človeka za nadzor in menjavo škatel, obratovalni stroški (zrak, elektrika, vzdrževanje) okoli 3.000 €/leto.

| | 1 človek | 2 človeka |
|---|---|---|
| Neto prihranek na leto (1 izmena) | ~38.400 € | ~93.600 € |
| **Povračilo pri 43.700 €** | **~1,1 leta** | **~0,5 leta** |

## Varnost, HACCP, tveganja

- **HACCP:** neposreden stik z živilom: kontaktne površine inox AISI 304 in živilski PU, brez mrtvih kotov, trakova se snameta brez orodja za pranje, zrak brez olja, maziva H1, nad hrano ni stekla.
- **Varnost pri delu:** zaščite pogonov in vibracijske mize, ohišje vizije z varnostnimi stikali (ob odprtju se ustavita trakova in izpiha), gobi.
- **Tehnična tveganja:**
  1. **ne obrne se vsaka rezina** (ukrivljene, lahke) → nastavljiv prag in višina padca, preizkus s pravim čipsom, cilj ≥ 90 % obrnjenih; to pokaže tudi Lukova simulacija;
  2. dodaten padec poveča lomljenje → padec samo ~150 mm, mehak prehod;
  3. lepljive rezine ne zdrsnejo na klancu → nastavljiva hitrost in naklon, vibracijska miza pred trakom;
  4. vision stranke da signal prepozno ali z napačnim položajem → priklop prek enkoderja, preizkus z označenimi rezinami pri FAT;
  5. izpad zraka (dve letvi rabita več zraka) → rezervoar 20 L, tlačno stikalo, ob alarmu se trakova ustavita.

---

## Alternativa: en poševni trak, kamera spodaj v letu

Skica: [`skica_cips.svg`](skica_cips.svg) · 3D (Luka): [`Trak-za-cips.png`](Trak-za-cips.png).
Vibracijska miza + en trak 4 m. Kamera zgoraj pri 3,5 m, kamera spodaj gleda rezino v letu na glavi traku, en izpih ~150 mm za glavo. Spodaj je za izračun malo časa, zato samo hiter test temnih pik.

| | Glavni (2 traka, obračanje) | Alternativa (1 trak) |
|---|---|---|
| Material | 18.500 € | 14.250 € |
| Lastna cena z rezervo | 33.630 € | 27.060 € |
| **Prodajna cena** | **≈ 43.700 €** | **≈ 35.200 €** |
| Obe strani pregledani | da, če se rezina obrne | da, vedno |
| Čas za izračun | 0,5 m za obe strani | 0,5 m zgoraj, spodaj zelo malo |
| Kamera pod trakom | ne | da (drobtine na objektivu) |
| Izpihi | 2 | 1 |
