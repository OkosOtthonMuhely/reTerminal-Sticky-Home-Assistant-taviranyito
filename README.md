# reTerminal Sticky – nappali vezérlő (minta projekt)

E-papíros fali vezérlő a **Seeed reTerminal Sticky**-re, ESPHome-mal és Home Assistanttal.

## Mit tud

- **Menü:** négy csempe (három lámpa + egy tetszőleges kapcsoló), fűtés sáv, hangalapú asszisztens, időjárás
- **Lámpa oldal:** be/ki, fényerő és színhőmérséklet sáv (az 1–3. csempe hosszan nyomva)
- **TV távirányító:** be/ki, egy extra kapcsoló, három forrás / alkalmazás, hangerő (a 4. csempe hosszan nyomva)
- **Fűtés oldal:** cél ±0,5 fok, mód (ki / fűtés / auto), három gyors beállítás, 24 órás grafikon
- **Időjárás:** mai idő és 3 napos előrejelzés – alvás közben is ez látszik
- **Alvás:** használaton kívül mély alvásba megy, gombra ébred, 4 óránként magától frissít

## Telepítés

1. **ESPHome:** a `sticky-nappali.yaml`-t másold az ESPHome mappába. A fájl elején, az
   **„INNEN SZERKESZD”** és **„EDDIG SZERKESZD”** közötti részben írd át az entitásokat,
   feliratokat és ikonokat a sajátjaidra. Ikonnevek: https://pictogrammers.com/library/mdi/
2. **Titkos adatok:** a `secrets.yaml` mintát töltsd ki (Wi-Fi, OTA jelszó, API kulcs).
3. **Home Assistant:** a `home_assistant` mappa két fájlját tedd a `configuration.yaml`-ba
   (vagy a `templates.yaml`-ba, a `template:` sor nélkül). Mindkettőben írd át az entitás nevét
   (`weather.…` illetve `climate.…`), majd töltsd újra a template entitásokat.
4. **Engedély:** a Home Assistant ESPHome integrációjában az eszköznél kapcsold be:
   *„Az eszköz Home Assistant műveleteket hajthat végre”* – enélkül nem tud lámpát kapcsolni.
5. **Fordítás és feltöltés** az ESPHome-ból (az első alkalommal USB-n).

## Gombok

| Hol | OK | FEL / LE |
|---|---|---|
| Menü | asszisztens | lámpa oldalak |
| Lámpa oldal | vissza | előző / következő lámpa |
| TV távirányító | vissza | hangerő |
| Fűtés | vissza | ±0,5 fok |
| Időjárás | vissza | vissza |

## Ha valami nem stimmel

- **Fordítva reagál az érintés:** a Home Assistantban az „Érintés tükrözés X / Y” kapcsolókkal javítható.
- **„Display already in state …” hiba a naplóban:** a `redraw` script végén a `delay: 3s`-t emeld `4s`-ra.
- **Nem látszik az időjárás / a grafikon:** nézd meg a Home Assistantban, van-e értéke a
  `sensor.sticky_idojaras` és a `sensor.sticky_futes_elozmeny` entitásnak.
