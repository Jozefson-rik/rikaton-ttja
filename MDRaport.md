---
layout: page
title: "Digiligipääsetavuse kontrolli aruanne"
permalink: /audit/test-ee/
nav_order: 1
has_toc: true
toc_sticky: true
---

# Digiligipääsetavuse kontrolli aruanne

> Käesolev aruanne on koostatud faili „Põhjalik seire_test.xlsx“ hindamistulemuste põhjal.

## Kokkuvõte

- **Veebileht:** test.ee
- **Standard:** EN 301 549 V3.2.1 / WCAG
- **Kontrolli liik:** Põhjalik audit
- **Testitud alamlehti:** 8
- **Mittevastavaid nõudeid:** 20

{: .warning }
Leitud probleemid mõjutavad oluliselt klaviatuurikasutajaid, ekraanilugeja kasutajaid ning vaegnägijaid.

---

## Sisukord
{: .no_toc }

1. TOC
{:toc}

---

# Ligipääsetavuse teatise hinnang

Ligipääsetavuse teatist ei hinnatud käesoleva auditi raames.

---

# Kriitilised probleemid

## WCAG 2.1.1 Keyboard

**Prioriteet:** 🔴 Kriitiline

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#keyboard>

**Nõude kirjeldus:**  
Kõik veebilehe funktsioonid peavad olema kasutatavad klaviatuuriga.

### Leitud probleemid

- Fookus ei liigu sisselogimise dialoogi.
- Otsingusoovitused avanevad automaatselt.
- Osa funktsioone ei ole klaviatuuriga kasutatavad.

### Mõju kasutajale

Klaviatuurikasutajad ei saa kõiki veebilehe funktsioone kasutada.

### Vastutaja

✅ Arendaja

### Soovitatavad tegevused

- Lisada korrektne fookuse haldus.
- Testida kõik kasutajateekonnad klaviatuuriga.

---

## WCAG 2.4.1 Bypass Blocks

**Prioriteet:** 🔴 Kriitiline

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#bypass-blocks>

### Leitud probleemid

- Puudub ülehüppamislink põhisisu juurde.

### Mõju kasutajale

Igal lehel tuleb läbida kogu navigatsioon enne põhisisuni jõudmist.

### Vastutaja

✅ Arendaja

---

## WCAG 1.3.1 Info and Relationships

**Prioriteet:** 🔴 Kriitiline

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#info-and-relationships>

### Leitud probleemid

- Puuduvad pealkirjatasemed.
- Vormiväljad ei ole seotud siltidega.
- Menüüdel puuduvad kirjeldused.

### Mõju kasutajale

Ekraanilugejad ei saa lehe struktuuri korrektselt edasi anda.

### Vastutaja

✅ Arendaja

---

## WCAG 4.1.2 Name, Role, Value

**Prioriteet:** 🔴 Kriitiline

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#name-role-value>

### Leitud probleemid

- Menüüde aktiivset olekut ei loeta ette.
- Avatud/suletud olekut ei tuvastata.
- Märkeruutude olek puudub.

### Mõju kasutajale

Ekraanilugeja kasutaja ei saa aru liidese seisundist.

### Vastutaja

✅ Arendaja

---

# Kõrge prioriteediga probleemid

## WCAG 1.4.3 Contrast (Minimum)

**Prioriteet:** 🟠 Kõrge

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#contrast-minimum>

### Probleemid

- Küpsiste akna nupud
- Placeholder-tekstid
- Leivapurud
- Hinnad
- Lingid

### Vastutaja

✅ Arendaja

---

## WCAG 1.4.11 Non-text Contrast

**Prioriteet:** 🟠 Kõrge

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#non-text-contrast>

### Probleemid

- Sisestusväljade piirjooned
- Ostukorvi nupud
- Sisselogimise nupud

### Vastutaja

✅ Arendaja

---

## WCAG 2.4.7 Focus Visible

**Prioriteet:** 🟠 Kõrge

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#focus-visible>

### Probleemid

- Keelevahetaja
- Ikoonid
- Ostukorvi nupud
- Märkeruudud

### Vastutaja

✅ Arendaja

---

## WCAG 1.1.1 Non-text Content

**Prioriteet:** 🟠 Kõrge

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#non-text-content>

### Probleemid

- Reklaambännerid
- Tooteikoonid
- Ostukorvi ikoon

### Vastutaja

✅ Sisutoimetaja / Arendaja

---

# Keskmise prioriteediga probleemid

## WCAG 3.3.1 Error Identification

<https://www.w3.org/WAI/WCAG22/quickref/#error-identification>

- Vigased väljad ei ole piisavalt eristatavad.

---

## WCAG 3.3.2 Labels or Instructions

<https://www.w3.org/WAI/WCAG22/quickref/#labels-or-instructions>

- Kohustuslikud väljad ei ole piisavalt selged.
- Tärni tähendus puudub.

---

## WCAG 3.3.3 Error Suggestion

<https://www.w3.org/WAI/WCAG22/quickref/#error-suggestion>

- Veateated ei sisalda parandamissoovitusi.

---

## WCAG 3.1.1 Language of Page

<https://www.w3.org/WAI/WCAG22/quickref/#language-of-page>

- Võõrkeelsetes vaadetes leidub tõlkimata sisu.

---

## WCAG 2.2.2 Pause, Stop, Hide

<https://www.w3.org/WAI/WCAG22/quickref/#pause-stop-hide>

- Avalehe karusselli ei ole võimalik peatada.

---

## WCAG 2.4.2 Page Titled

<https://www.w3.org/WAI/WCAG22/quickref/#page-titled>

- Ostukorvi vaate pealkiri ei kirjelda lehe eesmärki.

---

## WCAG 1.3.5 Identify Input Purpose

<https://www.w3.org/WAI/WCAG22/quickref/#identify-input-purpose>

- Vormidel puuduvad autocomplete atribuudid.

---

## WCAG 4.1.3 Status Messages

<https://www.w3.org/WAI/WCAG22/quickref/#status-messages>

- Otsingutulemuste arvust ei teavitata.
- Filtrite tulemust ei teavitata.
- Ostukorvi muudatustest ei teavitata.

---

# Vastutusalad

## Arendaja

- Keyboard
- Bypass Blocks
- Focus Visible
- Contrast
- ARIA ja semantika
- Status Messages
- Autocomplete

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

1. Lahendada kriitilised WCAG vead.
2. Lisada ülehüppamislink.
3. Parandada fookuse haldus.

## 90 päeva

1. Lahendada kontrastsusprobleemid.
2. Parandada vormid.
3. Täiendada ekraanilugeja tuge.

## 180 päeva

1. Korrastada kogu sisu.
2. Uuendada ligipääsetavuse teatist.
3. Viia läbi kordushindamine.

---

# Kokkuvõte

Veebilehel tuvastati **20 mittevastavat nõuet**, millest suurima mõjuga on klaviatuurikasutuse, semantilise struktuuri, kontrastsuse ja ekraanilugeja toe probleemid. Nende parandamine parandab oluliselt vastavust standarditele EN 301 549 ja WCAG 2.2.
``