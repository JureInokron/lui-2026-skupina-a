# Kontrola jabolčnega čipsa: kosovnica (BOM) in cena

Skica: [`skica_cips.svg`](skica_cips.svg). Navodila: [`NAVODILA.md`](NAVODILA.md). Cene so nabavne ocene brez DDV.

**Umeritev po prvi nalogi:** pri zapiranju škatlic je bila prava cena izvedenega projekta okoli **26.000 €**, mi smo bili na 46.300 €, torej skoraj 2-krat previsoko. Zato tukaj računamo vitkeje: malo planiranja, standardne komponente, izdelava pri kooperantu. Predavatelj je rekel, da je budget za čips **večji** kot za škatlice.

## Koncept

- Prevzem **pod sušilcem na višini 1 m**, brez vmesnega traku in brez vibracijskega dodajalnika.
- **Poševni trak 4 m, ~15° navzgor** (na koncu ~2 m visoko), teče hitreje od dovoda (15 do 20 m/min). Prekrite rezine na klancu zdrsnejo nazaj, zato se razmaknejo in ne ležijo ena na drugi.
- **En trak brez špranje.** Zgornjo stran slika **kamera nad trakom pri 3,5 m** (fokus 500 mm); do glave traku je **0,5 m za izračun** (pri 20 m/min 1,5 s).
- Spodnjo stran slika **kamera pod glavo traku**, ki gleda rezino **v letu**, ko zleti čez rob (fokus 500 mm). Ker je izpih blizu, za spodnjo stran uporabimo **hiter, preprost test temnih pik** (nekaj milisekund), zahtevnejšo analizo pa naredimo zgoraj, kjer je časa dovolj.
- **Izpih ~150 mm za glavo traku**, v letu: slabe dobijo sunek zraka v žleb za izmet, dobre letijo naprej v žleb, ki jih strese v **škatlo na tehtnici**.

---

## Kosovnica

**Mehanika**
| # | Pozicija | Kol. | Cena |
|---|---|---|---|
| M1 | Poševni trak 4 m × 500 mm v enem kosu, živilski PU z rahlo strukturo, inox okvir, valji | 1 | 2.600 € |
| M3 | Nosilna konstrukcija in noge do višine 2 m, inox | 1 | 600 € |
| M4 | Žleb za dobre rezine do škatle, inox | 1 | 300 € |
| M5 | Žleb in zabojnik za izmet, inox | 1 | 250 € |
| M6 | Ohišje vizije in izpiha (inox + polikarbonat, zatemnjeno) | 1 | 900 € |
| M7 | Nosilci kamer, luči in letve šob | 1 | 250 € |
| | **Skupaj mehanika** | | **4.900 €** |

**Elektro in pnevmatika**
| # | Pozicija | Kol. | Cena |
|---|---|---|---|
| E1 | Mali motor z reduktorjem | 1 | 250 € |
| E2 | Frekvenčnik | 1 | 150 € |
| E3 | Enkoder na traku | 1 | 100 € |
| E4 | Letev hitrih ventilov za izpih, 32 kanalov, z izhodnim modulom | 1 | 2.700 € |
| E5 | Zrak: rezervoar 10 L, filter za zrak brez olja, regulator, tlačno stikalo | 1 | 500 € |
| E6 | Tehtnica pod škatlo (plošča, celica, pretvornik) | 1 | 600 € |
| E7 | Senzorji (škatla na mestu, škatla polna), svetlobni stolpec, gobi, varnostni stikali | 1 | 450 € |
| | **Skupaj elektro** | | **4.750 €** |

**Vizija**
| # | Pozicija | Kol. | Cena |
|---|---|---|---|
| V1 | Linijska barvna kamera z objektivom (zgoraj nad trakom, spodaj pod glavo traku), fokus 500 mm | 2 | 3.000 € |
| V2 | Linijska LED luč (brez bliskanja) | 2 | 1.000 € |
| V3 | Industrijski PC za obdelavo slike | 1 | 1.500 € |
| V4 | Zaščitno okno spodnje kamere, zračna zavesa | 1 | 200 € |
| | **Skupaj vizija** | | **5.700 €** |

**Elektro omara**
| # | Pozicija | Kol. | Cena |
|---|---|---|---|
| O1 | Omara, PLC S7-1200, zaslon 4", varnostni rele, napajanje, sponke, kabli | 1 | 2.200 € |

**Material skupaj: 17.550 €**

## Delo

| Delo | Ure | Znesek |
|---|---|---|
| Planiranje: konstrukcija, ocena tveganja, CE | 50 h × 55 € | 2.750 € |
| Izdelava in sestava mehanike (kooperant Srbija) | 60 h × 25 € | 1.500 € |
| Ožičenje (kooperant Srbija) | 24 h × 25 € | 600 € |
| Programiranje PLC (trakovi, tehtnica, menjava škatle) | 24 h × 55 € | 1.320 € |
| Vizija: slike pravega čipsa, učenje napak, pragovi, sinhronizacija izpiha | 60 h × 55 € | 3.300 € |
| Preizkus pri nas s pravim čipsom (FAT) | 16 h × 55 € | 880 € |
| Montaža pod sušilec in zagon | 24 h × 55 € | 1.320 € |
| Logistika (prevoz iz Srbije, carinjenje, prevoz do stranke) | | 1.100 € |
| **Skupaj** | | **12.770 €** |

## Razdelitev in prodajna cena

| Sklop | Skupaj |
|---|---|
| Planiranje | 2.750 € |
| Mehanika (material + izdelava) | 6.400 € |
| Elektro (stroj + programiranje PLC) | 6.070 € |
| Vizija (kamere, luči, PC + učenje) | 9.000 € |
| Elektro omara (+ ožičenje) | 2.800 € |
| Preizkus pri nas | 880 € |
| Montaža in zagon | 1.320 € |
| Logistika | 1.100 € |
| **Lastna cena** | **30.320 €** |
| Rezerva 10 % | 3.030 € |
| **Lastna cena z rezervo** | **33.350 €** |
| Dodatek 30 % | 10.010 € |
| **Prodajna cena** | **≈ 43.400 € brez DDV** |

Največji del je **vizija** (20 % cene) in **izpih**, kar je pri optičnem sortirniku pričakovano. En poševni trak brez reže je prihranil vibracijski dodajalnik, odvodni trak in drugi pogon.

**Če je treba ceneje:** 16 namesto 32 ventilov (−1.200 €, slabša ločljivost izmeta), brez tehtnice, polnjenje škatle po času (−600 €), kameri z navadnim (ne linijskim) senzorjem (−1.400 €, manj ostra slika pri gibanju).

## Povračilo za stranko

Predpostavka: ročno pregleduje in sortira **1 do 2 človeka na izmeno** (30 €/h, 8 h, 230 dni = 55.200 €/leto na osebo). Stroj rabi 1/4 človeka za nadzor in menjavo škatel, obratovalni stroški (zrak, elektrika, vzdrževanje) okoli 3.000 €/leto.

| | 1 človek | 2 človeka |
|---|---|---|
| Neto prihranek na leto (1 izmena) | ~38.400 € | ~93.600 € |
| **Povračilo pri 43.400 €** | **~1,1 leta** | **~0,5 leta** |

Zraven: enaka presoja napak ves dan, sledljivost (vsaka izločena rezina je posneta), manj plesnivih rezin pri kupcu.

## Varnost, HACCP, tveganja

- **HACCP:** tu je **neposreden stik z živilom**, zato: kontaktne površine inox AISI 304 ali živilski PU, brez rež in mrtvih kotov, trakovi se snamejo brez orodja za pranje, zrak za izpih brez olja (filter), maziva H1, nad hrano ni stekla (zgornja kamera ima polikarbonatno okno).
- **Varnost pri delu:** glava traku je na 2 m, zato dostop za čiščenje s stopnico ali podestom; zaščite na pogonih, varnostni stikali na ohišju vizije (ob odprtju ugasne izpih in trakovi), gobi.
- **Tehnična tveganja:**
  1. rezine na klancu ne zdrsnejo dovolj (lepljive) → nastavljiv naklon in hitrost, trak z ustrezno strukturo; preizkus s pravim čipsom;
  2. rezina se v letu obrne, preden jo vidi spodnja kamera → kamera čisto ob glavi traku, kratek čas osvetlitve, položaj iz zgornje slike + enkoderja;
  3. lažni izmet (dobre izpihne) → učenje na pravih vzorcih, nastavljiv prag na zaslonu;
  4. drobtine na spodnji kameri → zračna zavesa, čiščenje okna v urniku;
  5. izpad zraka → rezervoar, tlačno stikalo, ob alarmu se trak ustavi.
