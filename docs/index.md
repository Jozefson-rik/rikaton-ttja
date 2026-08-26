---
layout: page
title: "Digiligipääsetavuse kontrolli aruanne"
permalink: /
nav_order: 1
has_toc: true
toc_sticky: true
---

# Digiligipääsetavuse kontrolli aruanne

> Käesolev aruanne on koostatud faili „Põhjalik seire_test.xlsx“ hindamistulemuste põhjal. Testitud oli 8 alamlehte ning tuvastati kokku 20 nõuet, mille puhul esines vähemalt üks mittevastavus. 【1-23880b】

## Sisukord
{: .no_toc }

* TOC
{:toc}

---

# Juhtkokkuvõte

## Kontrolli andmed

| Väli | Väärtus |
|--------|--------|
| Veebileht | test.ee |
| Standard | EN 301 549 V3.2.1 / WCAG |
| Kontrolli liik | Põhjalik audit |
| Testitud alamlehti | 8 |
| Kasutatud tööriistad | NVDA, WAVE, WebAIM Contrast Checker, Chrome, Firefox, Edge jt |

## Üldtulemus

Veebilehel tuvastati märkimisväärne arv digiligipääsetavuse probleeme, mis mõjutavad klaviatuurikasutajaid, ekraanilugeja kasutajaid, vaegnägijaid ning kasutajaid, kes kasutavad suurendust või kõrgkontrastseid režiime. 【1-23880b】

## Kõige olulisemad probleemid

1. Klaviatuuriga navigeerimine ei ole täielikult kasutatav. 【1-23880b】
2. Ekraanilugejaga kasutamisel puuduvad oluliste elementide kirjeldused ja olekuteave. 【1-23880b】
3. Mitmete komponentide kontrastsus ei vasta WCAG nõuetele. 【1-23880b】
4. Puudub võimalus liikuda otse põhisisu juurde. 【1-23880b】
5. Vormid ei anna kasutajatele piisavaid juhiseid ja parandamissoovitusi. 【1-23880b】

---

# Ligipääsetavuse teatise hinnang

Ligipääsetavuse teatist käesoleva auditi raames ei hinnatud. Soovitatav on kontrollida, kas kõik allpool kirjeldatud puudused on ligipääsetavuse teatises korrektselt kajastatud. 【1-23880b】

---

# Kriitilised probleemid

## WCAG 2.1.1 Keyboard

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#keyboard>

### Esineb alamlehtedel

- Avaleht
- Odavad kaubad
- Toode
- Ostukorv
- Ostu vormistamine
- Kontaktid
- Juhend
- Kinkekaart

### Mõju kasutajale

Kõik kasutajad ei saa veebilehte kasutada ainult klaviatuuriga. 【1-23880b】

### Probleemid

- Fookus ei liigu sisselogimise dialoogi.
- Otsingusoovitused avanevad automaatselt.
- Mõned juhtelemendid ei ole klaviatuuriga kasutatavad.
- Osa elemente jäetakse vahele.

### Vastutaja

✅ Arendaja

---

## WCAG 2.4.1 Bypass Blocks

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#bypass-blocks>

### Esineb alamlehtedel

- Avaleht
- Odavad kaubad
- Toode
- Ostukorv
- Ostu vormistamine
- Kontaktid
- Juhend
- Kinkekaart

### Mõju kasutajale

Klaviatuuri- ja ekraanilugejakasutajad peavad igal lehel läbima kogu päise ja menüü enne põhisisuni jõudmist. 【1-23880b】

### Probleem

- Puudub ülehüppamislink põhisisu juurde.

### Vastutaja

✅ Arendaja

---

## WCAG 1.3.1 Info and Relationships

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#info-and-relationships>

### Esineb alamlehtedel

- Avaleht
- Odavad kaubad
- Toode
- Ostukorv
- Ostu vormistamine
- Kontaktid
- Juhend
- Kinkekaart

### Mõju kasutajale

Ekraanilugejad ei saa veebilehe struktuuri korrektselt edasi anda. 【1-23880b】

### Probleemid

- Puuduvad või vahele jäetud pealkirjatasemed.
- Vormiväljad ei ole seotud siltidega.
- Menüüdel puuduvad eristavad kirjeldused.
- Dünaamilistest muudatustest ei teavitata.

### Vastutaja

✅ Arendaja

---

## WCAG 4.1.2 Name, Role, Value

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#name-role-value>

### Esineb alamlehtedel

- Avaleht
- Odavad kaubad
- Toode
- Ostukorv
- Ostu vormistamine
- Kontaktid
- Juhend
- Kinkekaart

### Mõju kasutajale

Ekraanilugeja kasutajad ei saa kasutajaliidese elementide olekust aru. 【1-23880b】

### Probleemid

- Aktiivne menüüpunkt ei ole tuvastatav.
- Avatud/suletud olek puudub.
- Märkeruutude olekut ei edastata.
- Akordionide olekuid ei loeta ette.

### Vastutaja

✅ Arendaja

---

# Kõrge prioriteediga probleemid

## WCAG 1.4.3 Contrast (Minimum)

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#contrast-minimum>

### Esineb alamlehtedel

- Avaleht
- Odavad kaubad
- Toode
- Ostukorv
- Ostu vormistamine
- Kontaktid
- Juhend
- Kinkekaart

### Probleemid

- Küpsiste akna nupud
- Placeholder-tekstid
- Hinnad
- Leivapurud
- Lingid
- Menüüelemendid

### Vastutaja

✅ Arendaja

---

## WCAG 1.4.11 Non-text Contrast

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#non-text-contrast>

### Esineb alamlehtedel

- Avaleht
- Odavad kaubad
- Toode
- Ostukorv
- Ostu vormistamine
- Kontaktid
- Juhend
- Kinkekaart

### Probleemid

- Sisestusväljade piirjooned
- Ostukorvi nupud
- Sisselogimise nupud
- Muud kasutajaliidese komponendid ei eristu taustast piisavalt

### Vastutaja

✅ Arendaja

---

## WCAG 2.4.7 Focus Visible

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#focus-visible>

### Esineb alamlehtedel

- Avaleht
- Odavad kaubad
- Toode
- Ostukorv
- Ostu vormistamine
- Kontaktid
- Juhend
- Kinkekaart

### Probleemid

- Keelevahetaja
- Ikoonid
- Ostukorvi nupud
- Märkeruudud
- Raadionupud

### Vastutaja

✅ Arendaja

---

## WCAG 1.1.1 Non-text Content

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#non-text-content>

### Esineb alamlehtedel

- Avaleht
- Odavad kaubad
- Toode
- Ostukorv
- Ostu vormistamine

### Probleemid

- Reklaambännerid
- Tootepakendi ikoonid
- Ostukorvi ikoon
- Visuaalset infot sisaldavad pildid ilma piisava alternatiivkirjelduseta

### Vastutaja

✅ Arendaja  
✅ Sisutoimetaja

---

# Keskmise prioriteediga probleemid

## WCAG 3.3.1 Error Identification

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#error-identification>

### Esineb alamlehtedel

- Ostu vormistamine

### Probleem

Vigane väli ei ole visuaalselt eristatav. Kuigi kuvatakse veateade, ei ole probleemne väli kasutajale piisavalt esile toodud. 【1-23880b】

### Vastutaja

✅ Arendaja

---

## WCAG 3.3.2 Labels or Instructions

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#labels-or-instructions>

### Esineb alamlehtedel

- Ostu vormistamine

### Probleemid

- Kohustuslikud väljad ei ole alati selgelt eristatavad.
- Tärni (*) tähendust ei selgitata.
- Kasutajale ei ole alati selge, millist infot temalt oodatakse.

### Vastutaja

✅ Arendaja  
✅ Sisutoimetaja

---

## WCAG 3.3.3 Error Suggestion

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#error-suggestion>

### Esineb alamlehtedel

- Ostu vormistamine

### Probleem

Veateated ei sisalda kasutajale soovitusi, kuidas sisestatud viga parandada. 【1-23880b】

### Vastutaja

✅ Arendaja

---

## WCAG 3.1.1 Language of Page

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#language-of-page>

### Esineb alamlehtedel

- Avaleht
- Odavad kaubad
- Toode
- Ostukorv
- Ostu vormistamine
- Kontaktid
- Juhend
- Kinkekaart

### Probleem

Vene- ja ingliskeelsetes vaadetes esineb tõlkimata sisu. 【1-23880b】

### Vastutaja

✅ Sisutoimetaja

---

## WCAG 2.2.2 Pause, Stop, Hide

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#pause-stop-hide>

### Esineb alamlehtedel

- Avaleht

### Probleem

Karusselli ei ole võimalik peatada. 【1-23880b】

### Vastutaja

✅ Arendaja

---

## WCAG 2.4.2 Page Titled

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#page-titled>

### Esineb alamlehtedel

- Ostukorv

### Probleem

Lehe pealkiri ei kirjelda ostukorvi vaadet. 【1-23880b】

### Vastutaja

✅ Arendaja

---

## WCAG 1.3.5 Identify Input Purpose

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#identify-input-purpose>

### Esineb alamlehtedel

- Ostu vormistamine

### Probleem

Vormiväljadel puuduvad autocomplete atribuudid. 【1-23880b】

### Vastutaja

✅ Arendaja

---

## WCAG 4.1.3 Status Messages

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#status-messages>

### Esineb alamlehtedel

- Avaleht
- Odavad kaubad
- Toode
- Ostukorv
- Kinkekaart

### Probleemid

- Otsingutulemuste arvust ei teavitata.
- Filtri mõjust ei teavitata.
- Toote lisamisest ostukorvi ei teavitata.
- Toote eemaldamisest ostukorvist ei teavitata.

### Vastutaja

✅ Arendaja

---

## WCAG 2.4.3 Focus Order

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#focus-order>

### Esineb alamlehtedel

- Toode

### Probleem

Klaviatuuri fookus liigub ootamatult jalusesse, mis muudab navigeerimise ebaloogiliseks. 【1-23880b】

### Vastutaja

✅ Arendaja

---

# Lisaleiud

## EN 301 549 §11.7 User Preferences

### Esineb alamlehtedel

- Avaleht
- Odavad kaubad
- Toode
- Ostukorv
- Ostu vormistamine
- Kontaktid
- Juhend
- Kinkekaart

### Probleemid

- Veebileht ei järgi kasutaja teksti suuruse eelistusi.
- Kõrgkontrastses vaates ei muutu kõik elemendid piisavalt loetavaks.
- Osa ikoone ja kasutajaliidese elemente ei kohandu operatsioonisüsteemi ligipääsetavuse seadistustega. 【1-23880b】

### Vastutaja

✅ Arendaja

---

# Vastutusalad

## Arendaja

- Klaviatuurikasutus
- Kontrastsus
- Fookuse haldus
- ARIA atribuudid
- Semantiline HTML
- Olekuteated
- Ülehüppamislink
- Autocomplete atribuudid

## Sisutoimetaja

- Alternatiivtekstid
- Tõlked
- Veatekstid
- Lehtede pealkirjad

## Jagatud vastutus

- Ligipääsetavuse teatis
- Karussellid
- Vormide kasutusloogika

---

# Soovitatud tegevuskava

## 30 päeva

1. Parandada WCAG 2.1.1 Keyboard puudused.
2. Lisada ülehüppamislink.
3. Lahendada kriitilised ekraanilugeja probleemid.
4. Parandada kontrastsusvead.

## 90 päeva

1. Parandada vormide kasutatavus.
2. Lisada puuduvad alternatiivtekstid.
3. Täiendada olekuteadete tuge.
4. Lahendada keele- ja tõlkeprobleemid.

## 180 päeva

1. Uuendada ligipääsetavuse teatis.
2. Teostada kordusaudit.
3. Parandada ülejäänud keskmise prioriteediga puudused.

---

# Kokkuvõte

Audit tuvastas kokku **20 nõuet, mille puhul esines vähemalt üks mittevastavus**. Suurima mõjuga puudused on seotud klaviatuurikasutuse, ekraanilugeja toe, kontrastsuse ning semantilise struktuuriga. Nende parandamine tõstab oluliselt veebilehe vastavust standarditele EN 301 549 ja WCAG 2.2 ning parandab kasutuskogemust kõigile kasutajatele. 【1-23880b】
``