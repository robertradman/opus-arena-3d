# 3D Animacija Opus Arene u Blenderu


## O projektu

Opus Arena u Osijeku novi je stadion nogometnog kluba Osijek i jedan od prepoznatljivih simbola kluba i grada. Svojim izgledom i karakterističnom konstrukcijom predstavlja zanimljiv objekt za izradu 3D modela.

Ovaj projekt prikazuje proces izrade i vizualizacije Opus Arene u programu **Blender**, od prikupljanja referenci i modeliranja, preko izrade materijala i osvjetljenja, do završne animacije prolaska kamere kroz stadion. Posebna pažnja posvećena je optimizaciji modela i samog rendera kako bi rezultat bio što kvalitetniji unutar hardverskih ograničenja dostupnog računala.

## Pregled procesa izrade

### 1. Prikupljanje referenci i planiranje

Prije modeliranja prikupljene su fotografije eksterijera, videozapisi stadiona dostupni na internetu i YouTubeu te standardne dimenzije travnjaka i udaljenosti tribina od terena. Radi lakše izrade, stadion je podijeljen na šest glavnih cjelina:

- Glavna konstrukcija stadiona
- Tribine
- Krovna konstrukcija
- Vanjski betonski stupovi
- Ograda uz teren
- Klupe za rezervne igrače

### 2. Modeliranje

- **Glavna konstrukcija** — izrađena korištenjem visoke simetrije objekta; pomoću `Mirror` modifikatora po X i Y osi izrađena je samo jedna četvrtina konstrukcije, dok se ostatak automatski preslikavao.
- **Krovna konstrukcija** — modelirana ručno, strana po strana, uz pažnju na nagib nadstrešnice; segmenti su spojeni naredbom `Ctrl+J`.
- **Vanjski betonski stupovi** — izrađeni kombinacijom `Mirror` i `Array` modifikatora radi ravnomjernog ponavljanja po cijelom opsegu stadiona.
- **Tribine i stolice** — jedna osnovna stolica umnožena je `Array` modifikatorom po X, Y i Z osi te raspoređena u sektore prema stvarnom izgledu tribina.
- **Ograda uz teren** — nosivi stupići i poprečne šipke izrađeni `Mirror` i `Array` modifikatorima.
- **Klupe za rezervne igrače** — nosači i nadstrešnica izrađeni `Array` modifikatorom.
- **Gotovi modeli** — stolice za klupu i nogometni gol preuzeti su s platforme [BlendKit](https://www.blendkit.com/) i prilagođeni sceni.

### 3. Teksture i materijali

Svi materijali, osim vanjske fasade i igračkog tunela, preuzeti su besplatno s platforme BlendKit:

| Element | Materijal |
|---|---|
| Travnjak | *Green Grass or Lawn* (Steffen), prilagođeno pomoću Wave Texture i Color Ramp čvora |
| Umjetna trava oko terena | *Procedural Turf* (diaverx miky) |
| Glavna konstrukcija i stupovi | *Concrete* (Raymond Gabriel), *Concrete Panels* (ydd 3D) |
| Krovna konstrukcija | *White Painted Metal* (ydd 3D) |
| Tribine | *White Plastic* i dvije nijanse *Blue Plastic* (ydd 3D) |
| Krov klupe za rezerve | *Frosted Acrylic* (Abin Suresh) |
| Ograda uz teren | *Brushed Stainless Steel* (Julix) |

### 4. Osvjetljenje i okruženje

Scena je renderirana pomoću **Cycles** rendering enginea uz dnevni ambijent. Osvjetljenje je podešeno preko `Sky Texture` čvora u World postavkama, s kutom sunčeve visine (Sun Elevation) od 49,1°. Oblaci su generirani proceduralno pomoću `Noise Texture` i `Color Ramp` čvorova, čime je postignut realističan izgled neba bez korištenja HDRI tekstura.

### 5. Animacija

Animacija prikazuje kretanje kamere iz mračnog igračkog tunela prema izvoru svjetlosti, nakon čega kamera izlazi na teren i postupno otkriva tribine i veličinu cijelog stadiona. Animacija je usporena radi boljeg pregleda stadiona u cjelini.

## Izazovi i optimizacija

| Problem | Rješenje |
|---|---|
| Nedostatak preciznih arhitektonskih nacrta stadiona | Kombinacija fotografija, videozapisa i standardnih dimenzija terena |
| Dugo vrijeme renderiranja zbog složenosti scene | `Max Samples` smanjen na 35, `Max Bounces` na 8 |
| Ograničenja računala pri radu s velikim teksturama | Teksture ograničene na rezoluciju do 2K |
| Realistično nebo bez teških HDRI datoteka | Proceduralno generirano nebo i oblaci u Shader Editoru |

Cilj optimizacija nije bio postići maksimalnu tehničku kvalitetu, već pronaći ravnotežu između vizualnog dojma i performansi dostupnog hardvera.

## Alati i tehnologije

- **[Blender](https://www.blender.org/)** — 3D modeliranje, teksturiranje, osvjetljenje i animacija
- **Cycles** — rendering engine
- **[BlendKit](https://www.blendkit.com/)** — biblioteka besplatnih PBR materijala i modela

## Struktura projekta

> Prilagodi ovaj odjeljak stvarnoj strukturi repozitorija.

```
├── assets/                  # Dodatni 3D resursi i materijali
│   ├── materials/           # Prilagođene teksture i materijali
│   └── models/              # Preuzeti i uvezeni 3D modeli
├── rezultat/                # Finalni renderi (slike i animacija)
├── seminar i prezentacija/  # Seminarski rad i prateća prezentacija
├── textures/                # Slikovne teksture korištene u sceni igrača
├── OpusArena.blend          # Glavna Blender projektna datoteka
└── README.md                # Dokumentacija projekta
```

## Reference

- Blender Documentation Team, *Blender 5.0 Reference Manual*, Blender Foundation. https://docs.blender.org/manual/en/5.0/
- BlendKit – 3D Models, PBR Materials & Assets Library for Blender. https://www.blendkit.com/
- NK Osijek, *Stadion „Opus Arena"*. https://nk-osijek.hr/opus-arena/
- Osječka TV, *"Obilazak Opus arene"*, YouTube. https://www.youtube.com/watch?v=DTXgXBjiGis
- NK Osijek, *"Nova era Opus Arena!"*, YouTube. https://www.youtube.com/watch?v=eaqX2emzg2I

---

*Projekt izrađen u sklopu kolegija na Fakultetu primijenjene matematike i informatike u Osijeku.*
