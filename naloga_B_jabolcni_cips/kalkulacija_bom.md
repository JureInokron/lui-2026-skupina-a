# Kontrola jabolčnega čipsa: kosovnica in cena

Skica: [`skica_cips.svg`](skica_cips.svg). Navodila: [`NAVODILA.md`](NAVODILA.md). Cene so nabavne ocene brez DDV.

**Umeritev po prvi nalogi:** pri zapiranju škatlic je bila prava cena izvedenega projekta okoli **26.000 €**, mi smo bili na 46.300 €, torej skoraj 2-krat previsoko. Zato tukaj računamo vitkeje: manj ur planiranja, cenejše standardne komponente, izdelava pri kooperantu. Predavatelj je rekel, da je budget za čips **večji** kot za škatlice.

---

## Kosovnica

**Mehanika**
| Pozicija | Kol. | Cena |
|---|---|---|
| Vibracijski dodajalnik inox 800 × 500 mm z elektromagnetnim vibratorjem in krmilnikom | 1 | 2.200 € |
| Pospeševalni trak 1,6 m × 500 mm: živilski PU trak, inox okvir, valji | 1 | 1.500 € |
| Odvodni trak 1,2 m × 400 mm | 1 | 1.000 € |
| Žleb za izmet in zabojnik, inox | 1 | 250 € |
| Ohišje vizije (inox + polikarbonat, zatemnjeno) | 1 | 900 € |
| Noge, nosilci kamer | 1 | 250 € |
| **Skupaj** | | **6.100 €** |

**Elektro in pnevmatika**
| Pozicija | Kol. | Cena |
|---|---|---|
| Mali motor z reduktorjem | 2 | 500 € |
| Frekvenčnik | 2 | 300 € |
| Enkoder na pospeševalnem traku | 1 | 100 € |
| Letev hitrih ventilov za izpih, 32 kanalov, z izhodnim modulom | 1 | 2.700 € |
| Zrak: rezervoar 10 L, filter za zrak brez olja, regulator, tlačno stikalo | 1 | 500 € |
| Tehtnica pod škatlo (plošča, celica, pretvornik) | 1 | 600 € |
| Senzorji (škatla na mestu, škatla polna), svetlobni stolpec, gobi, varnostni stikali | 1 | 450 € |
| **Skupaj** | | **5.150 €** |

**Vizija**
| Pozicija | Kol. | Cena |
|---|---|---|
| Industrijska barvna kamera z objektivom (zgoraj, spodaj), fokus 500 mm | 2 | 1.600 € |
| LED luč (linijska, brez bliskanja) | 2 | 600 € |
| Industrijski PC za obdelavo slike | 1 | 1.500 € |
| Zaščitno steklo spodnje kamere, zračna zavesa | 1 | 200 € |
| **Skupaj** | | **3.900 €** |

**Elektro omara**
| Pozicija | Kol. | Cena |
|---|---|---|
| Omara, PLC S7-1200, zaslon 4", varnostni rele, napajanje, sponke, kabli | 1 | 2.200 € |

**Material skupaj: 17.350 €**

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
| Mehanika (material + izdelava) | 7.600 € |
| Elektro (stroj + programiranje PLC) | 6.470 € |
| Vizija (kamere, luči, PC + učenje) | 7.200 € |
| Elektro omara (+ ožičenje) | 2.800 € |
| Preizkus pri nas | 880 € |
| Montaža in zagon | 1.320 € |
| Logistika | 1.100 € |
| **Lastna cena** | **30.120 €** |
| Rezerva 10 % | 3.010 € |
| **Lastna cena z rezervo** | **33.130 €** |
| Dodatek 30 % | 9.940 € |
| **Prodajna cena** | **≈ 43.100 € brez DDV** |

Največji del je **vizija** (17 %) in **izpih** (letev ventilov), kar je pri optičnem sortirniku pričakovano.

**Če je treba ceneje:** ena kamera zgoraj in obračanje rezin namesto dveh kamer (−1.100 €, a slabše zaznavanje), 16 namesto 32 ventilov (−1.200 €, slabša ločljivost izmeta), brez tehtnice, polnjenje škatle po času (−600 €).

## Povračilo za stranko

Predpostavka: ročno pregleduje in sortira **1 do 2 človeka na izmeno** (30 €/h, 8 h, 230 dni = 55.200 €/leto na osebo). Stroj rabi 1/4 človeka za nadzor in menjavo škatel, obratovalni stroški (zrak, elektrika, vzdrževanje) okoli 3.000 €/leto.

| | 1 človek | 2 človeka |
|---|---|---|
| Neto prihranek na leto (1 izmena) | ~38.400 € | ~93.600 € |
| **Povračilo pri 43.100 €** | **~1,1 leta** | **~0,5 leta** |

Zraven: enaka presoja napak ves dan, sledljivost (vsaka izločena rezina je posneta), manj plesnivih rezin pri kupcu.

## Varnost, HACCP, tveganja

- **HACCP:** tu je **neposreden stik z živilom**, zato: vse kontaktne površine inox AISI 304 ali živilski PU, brez rež in mrtvih kotov, trakovi se snamejo brez orodja za pranje, zrak za izpih brez olja (filter), maziva H1, steklo nad hrano ni dovoljeno (spodnja kamera ima polikarbonat ali steklo z zaščitno folijo in je pod tokom, ne nad njim).
- **Varnost pri delu:** zaščite na pogonih, varnostni stikali na ohišju vizije (ob odprtju ugasne izpih in trakovi), gobi, luč v ohišju ne slepi (zatemnjeno).
- **Tehnična tveganja:**
  1. rezine se lepijo ali prekrivajo → vibracijski dodajalnik + pospešek; če ne zadošča, širši trak;
  2. lažni izmet (dobre rezine izpihne) → učenje na pravih vzorcih, nastavljiv prag na zaslonu, merimo pri preizkusu;
  3. drobtine in prah na kamerah → zračna zavesa, čiščenje stekla v urniku;
  4. izpad zraka → rezervoar, tlačno stikalo, ob alarmu se trak ustavi.
