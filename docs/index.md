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

<style>
	.audit-finding-toggle {
		width: 100%;
		display: flex;
		justify-content: space-between;
		align-items: center;
		gap: 1rem;
		padding: 0.35rem 0;
		border: 0;
		background: transparent;
		color: inherit;
		font: inherit;
		text-align: left;
		cursor: pointer;
	}

	.audit-finding-toggle:hover span:first-child {
		text-decoration: underline;
	}

	.audit-finding-toggle:focus-visible {
		outline: 3px solid currentColor;
		outline-offset: 4px;
	}

	.audit-finding-toggle__icon {
		flex: 0 0 auto;
		min-width: 1.5rem;
		text-align: center;
		font-weight: 700;
	}

	.audit-finding-panel[hidden] {
		display: none;
	}
</style>

<script>
	const setupAuditFindingToggles = () => {
		const headings = Array.from(document.querySelectorAll(".markdown-body h2, main h2, .main-content h2"));
		const issueHeadingPattern = /^(WCAG|EN 301 549)/;

		headings.forEach((heading, index) => {
			if (heading.querySelector(".audit-finding-toggle")) {
				return;
			}

			const title = heading.textContent.replace(/Anchor\s*$/, "").trim();

			if (!issueHeadingPattern.test(title)) {
				return;
			}

			const panel = document.createElement("div");
			panel.className = "audit-finding-panel";
			panel.id = `audit-finding-panel-${index}`;

			let nextElement = heading.nextElementSibling;

			while (nextElement && !["H1", "H2"].includes(nextElement.tagName)) {
				const elementToMove = nextElement;
				nextElement = nextElement.nextElementSibling;
				panel.appendChild(elementToMove);
			}

			heading.after(panel);

			const button = document.createElement("button");
			button.className = "audit-finding-toggle";
			button.type = "button";
			button.setAttribute("aria-expanded", "true");
			button.setAttribute("aria-controls", panel.id);

			const label = document.createElement("span");
			label.textContent = title;

			const icon = document.createElement("span");
			icon.className = "audit-finding-toggle__icon";
			icon.setAttribute("aria-hidden", "true");
			icon.textContent = "−";

			button.append(label, icon);
			heading.textContent = "";
			heading.appendChild(button);

			button.addEventListener("click", () => {
				const expanded = button.getAttribute("aria-expanded") === "true";
				button.setAttribute("aria-expanded", String(!expanded));
				panel.hidden = expanded;
				icon.textContent = expanded ? "+" : "−";
			});
		});
	};

	if (document.readyState === "loading") {
		document.addEventListener("DOMContentLoaded", setupAuditFindingToggles);
	} else {
		setupAuditFindingToggles();
	}
</script>

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

- [Avaleht](https://www.test.ee/)
- [Odavad kaubad](https://www.test.ee/odavad-kaubad)
- [Toode](https://www.test.ee/toode)
- [Ostukorv](https://www.test.ee/ostukorv)
- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)
- [Kontaktid](https://www.test.ee/kontaktid)
- [Juhend](https://www.test.ee/juhend)
- [Kinkekaart](https://www.test.ee/kinkekaart)

### Mõju kasutajale

Kõik kasutajad ei saa veebilehte kasutada ainult klaviatuuriga. 【1-23880b】

### Probleemid

- Fookus ei liigu sisselogimise dialoogi. CSS selector: `.login-dialog`
- Otsingusoovitused avanevad automaatselt. CSS selector: `.site-search__suggestions`
- Mõned juhtelemendid ei ole klaviatuuriga kasutatavad. CSS selector: `.product-card__quick-action`
- Osa elemente jäetakse vahele. CSS selector: `.main-navigation a, .header-actions button`

### Vastutaja

✅ Arendaja

---

## WCAG 2.4.1 Bypass Blocks

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#bypass-blocks>

### Esineb alamlehtedel

- [Avaleht](https://www.test.ee/)
- [Odavad kaubad](https://www.test.ee/odavad-kaubad)
- [Toode](https://www.test.ee/toode)
- [Ostukorv](https://www.test.ee/ostukorv)
- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)
- [Kontaktid](https://www.test.ee/kontaktid)
- [Juhend](https://www.test.ee/juhend)
- [Kinkekaart](https://www.test.ee/kinkekaart)

### Mõju kasutajale

Klaviatuuri- ja ekraanilugejakasutajad peavad igal lehel läbima kogu päise ja menüü enne põhisisuni jõudmist. 【1-23880b】

### Probleem

- Puudub ülehüppamislink põhisisu juurde. CSS selector: `.skip-link`

### Vastutaja

✅ Arendaja

---

## WCAG 1.3.1 Info and Relationships

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#info-and-relationships>

### Esineb alamlehtedel

- [Avaleht](https://www.test.ee/)
- [Odavad kaubad](https://www.test.ee/odavad-kaubad)
- [Toode](https://www.test.ee/toode)
- [Ostukorv](https://www.test.ee/ostukorv)
- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)
- [Kontaktid](https://www.test.ee/kontaktid)
- [Juhend](https://www.test.ee/juhend)
- [Kinkekaart](https://www.test.ee/kinkekaart)

### Mõju kasutajale

Ekraanilugejad ei saa veebilehe struktuuri korrektselt edasi anda. 【1-23880b】

### Probleemid

- Puuduvad või vahele jäetud pealkirjatasemed. CSS selector: `main h1, main h2, main h3`
- Vormiväljad ei ole seotud siltidega. CSS selector: `.checkout-form input, .checkout-form select`
- Menüüdel puuduvad eristavad kirjeldused. CSS selector: `nav.main-navigation, nav.footer-navigation`
- Dünaamilistest muudatustest ei teavitata. CSS selector: `.search-results, .cart-status`

### Vastutaja

✅ Arendaja

---

## WCAG 4.1.2 Name, Role, Value

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#name-role-value>

### Esineb alamlehtedel

- [Avaleht](https://www.test.ee/)
- [Odavad kaubad](https://www.test.ee/odavad-kaubad)
- [Toode](https://www.test.ee/toode)
- [Ostukorv](https://www.test.ee/ostukorv)
- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)
- [Kontaktid](https://www.test.ee/kontaktid)
- [Juhend](https://www.test.ee/juhend)
- [Kinkekaart](https://www.test.ee/kinkekaart)

### Mõju kasutajale

Ekraanilugeja kasutajad ei saa kasutajaliidese elementide olekust aru. 【1-23880b】

### Probleemid

- Aktiivne menüüpunkt ei ole tuvastatav. CSS selector: `.main-navigation__link.is-active`
- Avatud/suletud olek puudub. CSS selector: `.menu-toggle, .filter-toggle`
- Märkeruutude olekut ei edastata. CSS selector: `.filter-panel input[type="checkbox"]`
- Akordionide olekuid ei loeta ette. CSS selector: `.accordion__trigger`

### Vastutaja

✅ Arendaja

---

# Kõrge prioriteediga probleemid

## WCAG 1.4.3 Contrast (Minimum)

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#contrast-minimum>

### Esineb alamlehtedel

- [Avaleht](https://www.test.ee/)
- [Odavad kaubad](https://www.test.ee/odavad-kaubad)
- [Toode](https://www.test.ee/toode)
- [Ostukorv](https://www.test.ee/ostukorv)
- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)
- [Kontaktid](https://www.test.ee/kontaktid)
- [Juhend](https://www.test.ee/juhend)
- [Kinkekaart](https://www.test.ee/kinkekaart)

### Probleemid

- Küpsiste akna nupud. CSS selector: `.cookie-banner button`
- Placeholder-tekstid. CSS selector: `input::placeholder, textarea::placeholder`
- Hinnad. CSS selector: `.product-card__price, .product-detail__price`
- Leivapurud. CSS selector: `.breadcrumbs a`
- Lingid. CSS selector: `main a`
- Menüüelemendid. CSS selector: `.main-navigation__link`

### Vastutaja

✅ Arendaja

---

## WCAG 1.4.11 Non-text Contrast

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#non-text-contrast>

### Esineb alamlehtedel

- [Avaleht](https://www.test.ee/)
- [Odavad kaubad](https://www.test.ee/odavad-kaubad)
- [Toode](https://www.test.ee/toode)
- [Ostukorv](https://www.test.ee/ostukorv)
- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)
- [Kontaktid](https://www.test.ee/kontaktid)
- [Juhend](https://www.test.ee/juhend)
- [Kinkekaart](https://www.test.ee/kinkekaart)

### Probleemid

- Sisestusväljade piirjooned. CSS selector: `input, select, textarea`
- Ostukorvi nupud. CSS selector: `.cart-summary button, .cart-item__action`
- Sisselogimise nupud. CSS selector: `.login-dialog button`
- Muud kasutajaliidese komponendid ei eristu taustast piisavalt. CSS selector: `.button--secondary, .icon-button`

### Vastutaja

✅ Arendaja

---

## WCAG 2.4.7 Focus Visible

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#focus-visible>

### Esineb alamlehtedel

- [Avaleht](https://www.test.ee/)
- [Odavad kaubad](https://www.test.ee/odavad-kaubad)
- [Toode](https://www.test.ee/toode)
- [Ostukorv](https://www.test.ee/ostukorv)
- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)
- [Kontaktid](https://www.test.ee/kontaktid)
- [Juhend](https://www.test.ee/juhend)
- [Kinkekaart](https://www.test.ee/kinkekaart)

### Probleemid

- Keelevahetaja. CSS selector: `.language-switcher a, .language-switcher button`
- Ikoonid. CSS selector: `.icon-button`
- Ostukorvi nupud. CSS selector: `.cart-summary button, .cart-item__action`
- Märkeruudud. CSS selector: `input[type="checkbox"]`
- Raadionupud. CSS selector: `input[type="radio"]`

### Vastutaja

✅ Arendaja

---

## WCAG 1.1.1 Non-text Content

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#non-text-content>

### Esineb alamlehtedel

- [Avaleht](https://www.test.ee/)
- [Odavad kaubad](https://www.test.ee/odavad-kaubad)
- [Toode](https://www.test.ee/toode)
- [Ostukorv](https://www.test.ee/ostukorv)
- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)

### Probleemid

- Reklaambännerid. CSS selector: `.promo-banner img`
- Tootepakendi ikoonid. CSS selector: `.product-badge img, .product-badge svg`
- Ostukorvi ikoon. CSS selector: `.header-cart__icon`
- Visuaalset infot sisaldavad pildid ilma piisava alternatiivkirjelduseta. CSS selector: `img:not([alt]), img[alt=""]`

### Vastutaja

✅ Arendaja  
✅ Sisutoimetaja

---

# Keskmise prioriteediga probleemid

## WCAG 3.3.1 Error Identification

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#error-identification>

### Esineb alamlehtedel

- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)

### Probleem

Vigane väli ei ole visuaalselt eristatav. Kuigi kuvatakse veateade, ei ole probleemne väli kasutajale piisavalt esile toodud. CSS selector: `.checkout-form .form-field--error input` 【1-23880b】

### Vastutaja

✅ Arendaja

---

## WCAG 3.3.2 Labels or Instructions

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#labels-or-instructions>

### Esineb alamlehtedel

- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)

### Probleemid

- Kohustuslikud väljad ei ole alati selgelt eristatavad. CSS selector: `.checkout-form [required]`
- Tärni (*) tähendust ei selgitata. CSS selector: `.checkout-form .required-marker`
- Kasutajale ei ole alati selge, millist infot temalt oodatakse.

### Vastutaja

✅ Arendaja  
✅ Sisutoimetaja

---

## WCAG 3.3.3 Error Suggestion

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#error-suggestion>

### Esineb alamlehtedel

- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)

### Probleem

Veateated ei sisalda kasutajale soovitusi, kuidas sisestatud viga parandada. CSS selector: `.checkout-form .error-message` 【1-23880b】

### Vastutaja

✅ Arendaja

---

## WCAG 3.1.1 Language of Page

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#language-of-page>

### Esineb alamlehtedel

- [Avaleht](https://www.test.ee/)
- [Odavad kaubad](https://www.test.ee/odavad-kaubad)
- [Toode](https://www.test.ee/toode)
- [Ostukorv](https://www.test.ee/ostukorv)
- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)
- [Kontaktid](https://www.test.ee/kontaktid)
- [Juhend](https://www.test.ee/juhend)
- [Kinkekaart](https://www.test.ee/kinkekaart)

### Probleem

Vene- ja ingliskeelsetes vaadetes esineb tõlkimata sisu. 【1-23880b】

### Vastutaja

✅ Sisutoimetaja

---

## WCAG 2.2.2 Pause, Stop, Hide

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#pause-stop-hide>

### Esineb alamlehtedel

- [Avaleht](https://www.test.ee/)

### Probleem

Karusselli ei ole võimalik peatada. CSS selector: `.hero-carousel` 【1-23880b】

### Vastutaja

✅ Arendaja

---

## WCAG 2.4.2 Page Titled

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#page-titled>

### Esineb alamlehtedel

- [Ostukorv](https://www.test.ee/ostukorv)

### Probleem

Lehe pealkiri ei kirjelda ostukorvi vaadet. 【1-23880b】

### Vastutaja

✅ Arendaja

---

## WCAG 1.3.5 Identify Input Purpose

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#identify-input-purpose>

### Esineb alamlehtedel

- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)

### Probleem

Vormiväljadel puuduvad autocomplete atribuudid. CSS selector: `.checkout-form input[name="email"], .checkout-form input[name="phone"], .checkout-form input[name="address"]` 【1-23880b】

### Vastutaja

✅ Arendaja

---

## WCAG 4.1.3 Status Messages

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#status-messages>

### Esineb alamlehtedel

- [Avaleht](https://www.test.ee/)
- [Odavad kaubad](https://www.test.ee/odavad-kaubad)
- [Toode](https://www.test.ee/toode)
- [Ostukorv](https://www.test.ee/ostukorv)
- [Kinkekaart](https://www.test.ee/kinkekaart)

### Probleemid

- Otsingutulemuste arvust ei teavitata. CSS selector: `.search-results-count`
- Filtri mõjust ei teavitata. CSS selector: `.filter-results-status`
- Toote lisamisest ostukorvi ei teavitata. CSS selector: `.add-to-cart-button`
- Toote eemaldamisest ostukorvist ei teavitata. CSS selector: `.cart-item__remove`

### Vastutaja

✅ Arendaja

---

## WCAG 2.4.3 Focus Order

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#focus-order>

### Esineb alamlehtedel

- [Toode](https://www.test.ee/toode)

### Probleem

Klaviatuuri fookus liigub ootamatult jalusesse, mis muudab navigeerimise ebaloogiliseks. CSS selector: `.product-detail .product-gallery button, footer a` 【1-23880b】

### Vastutaja

✅ Arendaja

---

# Lisaleiud

## EN 301 549 §11.7 User Preferences

### Esineb alamlehtedel

- [Avaleht](https://www.test.ee/)
- [Odavad kaubad](https://www.test.ee/odavad-kaubad)
- [Toode](https://www.test.ee/toode)
- [Ostukorv](https://www.test.ee/ostukorv)
- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)
- [Kontaktid](https://www.test.ee/kontaktid)
- [Juhend](https://www.test.ee/juhend)
- [Kinkekaart](https://www.test.ee/kinkekaart)

### Probleemid

- Veebileht ei järgi kasutaja teksti suuruse eelistusi. CSS selector: `html, body, .page-content`
- Kõrgkontrastses vaates ei muutu kõik elemendid piisavalt loetavaks. CSS selector: `.button, .form-control, .product-card`
- Osa ikoone ja kasutajaliidese elemente ei kohandu operatsioonisüsteemi ligipääsetavuse seadistustega. CSS selector: `.icon-button svg, .header-actions svg` 【1-23880b】

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