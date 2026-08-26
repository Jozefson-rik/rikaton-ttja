---
layout: page
title: "Digiligipääsetavuse kontrolli aruanne"
permalink: /
nav_order: 1
has_toc: true
toc_sticky: true
---

# Digiligipääsetavuse kontrolli aruanne

> Käesolev aruanne on koostatud faili „Põhjalik seire_test.xlsx“ hindamistulemuste põhjal. Testitud oli 8 alamlehte ning tuvastati kokku 20 nõuet, mille puhul esines vähemalt üks mittevastavus.

<details class="report-toc" open markdown="1">
<summary>Sisukord</summary>

* TOC
{:toc}

</details>

<style>
	.report-toc {
		margin: 1.5rem 0;
	}

	.report-toc summary {
		display: list-item;
		font-size: 1.5rem;
		font-weight: 600;
		cursor: pointer;
	}

	.report-toc summary:focus-visible {
		outline: 3px solid currentColor;
		outline-offset: 4px;
	}

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

Veebilehel tuvastati märkimisväärne arv digiligipääsetavuse probleeme, mis mõjutavad klaviatuurikasutajaid, ekraanilugeja kasutajaid, vaegnägijaid ning kasutajaid, kes kasutavad suurendust või kõrgkontrastseid režiime.

## Kõige olulisemad probleemid

1. Klaviatuuriga navigeerimine ei ole täielikult kasutatav.
2. Ekraanilugejaga kasutamisel puuduvad oluliste elementide kirjeldused ja olekuteave.
3. Mitmete komponentide kontrastsus ei vasta WCAG nõuetele.
4. Puudub võimalus liikuda otse põhisisu juurde.
5. Vormid ei anna kasutajatele piisavaid juhiseid ja parandamissoovitusi.

---

# Ligipääsetavuse teatise hinnang

Ligipääsetavuse teatist käesoleva auditi raames ei hinnatud. Soovitatav on kontrollida, kas kõik allpool kirjeldatud puudused on ligipääsetavuse teatises korrektselt kajastatud.

---

# Kriitilised probleemid

## WCAG 2.1.1 Keyboard

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#keyboard>

**EN 301 549 viide:**  
§9.2.1.1 Keyboard

### Esineb alamlehtedel
{: .no_toc }

- [Avaleht](https://www.test.ee/)
- [Odavad kaubad](https://www.test.ee/odavad-kaubad)
- [Toode](https://www.test.ee/toode)
- [Ostukorv](https://www.test.ee/ostukorv)
- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)
- [Kontaktid](https://www.test.ee/kontaktid)
- [Juhend](https://www.test.ee/juhend)
- [Kinkekaart](https://www.test.ee/kinkekaart)

### Mõju kasutajale
{: .no_toc }

Kõik kasutajad ei saa veebilehte kasutada ainult klaviatuuriga.

### Probleemid
{: .no_toc }

- Fookus ei liigu sisselogimise dialoogi. CSS selector: `.login-dialog`
- Otsingusoovitused avanevad automaatselt. CSS selector: `.site-search__suggestions`
- Mõned juhtelemendid ei ole klaviatuuriga kasutatavad. CSS selector: `.product-card__quick-action`
- Osa elemente jäetakse vahele. CSS selector: `.main-navigation a, .header-actions button`

### Vastutaja
{: .no_toc }

✅ Arendaja

---

## WCAG 2.4.1 Bypass Blocks

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#bypass-blocks>

**EN 301 549 viide:**  
§9.2.4.1 Bypass Blocks

### Esineb alamlehtedel
{: .no_toc }

- [Avaleht](https://www.test.ee/)
- [Odavad kaubad](https://www.test.ee/odavad-kaubad)
- [Toode](https://www.test.ee/toode)
- [Ostukorv](https://www.test.ee/ostukorv)
- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)
- [Kontaktid](https://www.test.ee/kontaktid)
- [Juhend](https://www.test.ee/juhend)
- [Kinkekaart](https://www.test.ee/kinkekaart)

### Mõju kasutajale
{: .no_toc }

Klaviatuuri- ja ekraanilugejakasutajad peavad igal lehel läbima kogu päise ja menüü enne põhisisuni jõudmist.

### Probleem
{: .no_toc }

- Puudub ülehüppamislink põhisisu juurde. CSS selector: `.skip-link`

### Vastutaja
{: .no_toc }

✅ Arendaja

---

## WCAG 1.3.1 Info and Relationships

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#info-and-relationships>

**EN 301 549 viide:**  
§9.1.3.1 Info and Relationships

### Esineb alamlehtedel
{: .no_toc }

- [Avaleht](https://www.test.ee/)
- [Odavad kaubad](https://www.test.ee/odavad-kaubad)
- [Toode](https://www.test.ee/toode)
- [Ostukorv](https://www.test.ee/ostukorv)
- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)
- [Kontaktid](https://www.test.ee/kontaktid)
- [Juhend](https://www.test.ee/juhend)
- [Kinkekaart](https://www.test.ee/kinkekaart)

### Mõju kasutajale
{: .no_toc }

Ekraanilugejad ei saa veebilehe struktuuri korrektselt edasi anda.

### Probleemid
{: .no_toc }

- Puuduvad või vahele jäetud pealkirjatasemed. CSS selector: `main h1, main h2, main h3`
- Vormiväljad ei ole seotud siltidega. CSS selector: `.checkout-form input, .checkout-form select`
- Menüüdel puuduvad eristavad kirjeldused. CSS selector: `nav.main-navigation, nav.footer-navigation`
- Dünaamilistest muudatustest ei teavitata. CSS selector: `.search-results, .cart-status`

### Vastutaja
{: .no_toc }

✅ Arendaja

---

## WCAG 4.1.2 Name, Role, Value

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#name-role-value>

**EN 301 549 viide:**  
§9.4.1.2 Name, Role, Value

### Esineb alamlehtedel
{: .no_toc }

- [Avaleht](https://www.test.ee/)
- [Odavad kaubad](https://www.test.ee/odavad-kaubad)
- [Toode](https://www.test.ee/toode)
- [Ostukorv](https://www.test.ee/ostukorv)
- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)
- [Kontaktid](https://www.test.ee/kontaktid)
- [Juhend](https://www.test.ee/juhend)
- [Kinkekaart](https://www.test.ee/kinkekaart)

### Mõju kasutajale
{: .no_toc }

Ekraanilugeja kasutajad ei saa kasutajaliidese elementide olekust aru.

### Probleemid
{: .no_toc }

- Aktiivne menüüpunkt ei ole tuvastatav. CSS selector: `.main-navigation__link.is-active`
- Avatud/suletud olek puudub. CSS selector: `.menu-toggle, .filter-toggle`
- Märkeruutude olekut ei edastata. CSS selector: `.filter-panel input[type="checkbox"]`
- Akordionide olekuid ei loeta ette. CSS selector: `.accordion__trigger`

### Vastutaja
{: .no_toc }

✅ Arendaja

---

# Kõrge prioriteediga probleemid

## WCAG 1.4.3 Contrast (Minimum)

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#contrast-minimum>

**EN 301 549 viide:**  
§9.1.4.3 Contrast (Minimum)

### Esineb alamlehtedel
{: .no_toc }

- [Avaleht](https://www.test.ee/)
- [Odavad kaubad](https://www.test.ee/odavad-kaubad)
- [Toode](https://www.test.ee/toode)
- [Ostukorv](https://www.test.ee/ostukorv)
- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)
- [Kontaktid](https://www.test.ee/kontaktid)
- [Juhend](https://www.test.ee/juhend)
- [Kinkekaart](https://www.test.ee/kinkekaart)

### Probleemid
{: .no_toc }

- Küpsiste akna nupud. CSS selector: `.cookie-banner button`
- Placeholder-tekstid. CSS selector: `input::placeholder, textarea::placeholder`
- Hinnad. CSS selector: `.product-card__price, .product-detail__price`
- Leivapurud. CSS selector: `.breadcrumbs a`
- Lingid. CSS selector: `main a`
- Menüüelemendid. CSS selector: `.main-navigation__link`

### Vastutaja
{: .no_toc }

✅ Arendaja

---

## WCAG 1.4.11 Non-text Contrast

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#non-text-contrast>

**EN 301 549 viide:**  
§9.1.4.11 Non-text Contrast

### Esineb alamlehtedel
{: .no_toc }

- [Avaleht](https://www.test.ee/)
- [Odavad kaubad](https://www.test.ee/odavad-kaubad)
- [Toode](https://www.test.ee/toode)
- [Ostukorv](https://www.test.ee/ostukorv)
- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)
- [Kontaktid](https://www.test.ee/kontaktid)
- [Juhend](https://www.test.ee/juhend)
- [Kinkekaart](https://www.test.ee/kinkekaart)

### Probleemid
{: .no_toc }

- Sisestusväljade piirjooned. CSS selector: `input, select, textarea`
- Ostukorvi nupud. CSS selector: `.cart-summary button, .cart-item__action`
- Sisselogimise nupud. CSS selector: `.login-dialog button`
- Muud kasutajaliidese komponendid ei eristu taustast piisavalt. CSS selector: `.button--secondary, .icon-button`

### Vastutaja
{: .no_toc }

✅ Arendaja

---

## WCAG 2.4.7 Focus Visible

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#focus-visible>

**EN 301 549 viide:**  
§9.2.4.7 Focus Visible

### Esineb alamlehtedel
{: .no_toc }

- [Avaleht](https://www.test.ee/)
- [Odavad kaubad](https://www.test.ee/odavad-kaubad)
- [Toode](https://www.test.ee/toode)
- [Ostukorv](https://www.test.ee/ostukorv)
- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)
- [Kontaktid](https://www.test.ee/kontaktid)
- [Juhend](https://www.test.ee/juhend)
- [Kinkekaart](https://www.test.ee/kinkekaart)

### Probleemid
{: .no_toc }

- Keelevahetaja. CSS selector: `.language-switcher a, .language-switcher button`
- Ikoonid. CSS selector: `.icon-button`
- Ostukorvi nupud. CSS selector: `.cart-summary button, .cart-item__action`
- Märkeruudud. CSS selector: `input[type="checkbox"]`
- Raadionupud. CSS selector: `input[type="radio"]`

### Vastutaja
{: .no_toc }

✅ Arendaja

---

## WCAG 1.1.1 Non-text Content

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#non-text-content>

**EN 301 549 viide:**  
§9.1.1.1 Non-text Content

### Esineb alamlehtedel
{: .no_toc }

- [Avaleht](https://www.test.ee/)
- [Odavad kaubad](https://www.test.ee/odavad-kaubad)
- [Toode](https://www.test.ee/toode)
- [Ostukorv](https://www.test.ee/ostukorv)
- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)

### Probleemid
{: .no_toc }

- Reklaambännerid. CSS selector: `.promo-banner img`
- Tootepakendi ikoonid. CSS selector: `.product-badge img, .product-badge svg`
- Ostukorvi ikoon. CSS selector: `.header-cart__icon`
- Visuaalset infot sisaldavad pildid ilma piisava alternatiivkirjelduseta. CSS selector: `img:not([alt]), img[alt=""]`

### Vastutaja
{: .no_toc }

✅ Arendaja  
✅ Sisutoimetaja

---

# Keskmise prioriteediga probleemid

## WCAG 3.3.1 Error Identification

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#error-identification>

**EN 301 549 viide:**  
§9.3.3.1 Error Identification

### Esineb alamlehtedel
{: .no_toc }

- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)

### Probleem
{: .no_toc }

Vigane väli ei ole visuaalselt eristatav. Kuigi kuvatakse veateade, ei ole probleemne väli kasutajale piisavalt esile toodud. CSS selector: `.checkout-form .form-field--error input`

### Vastutaja
{: .no_toc }

✅ Arendaja

---

## WCAG 3.3.2 Labels or Instructions

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#labels-or-instructions>

**EN 301 549 viide:**  
§9.3.3.2 Labels or Instructions

### Esineb alamlehtedel
{: .no_toc }

- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)

### Probleemid
{: .no_toc }

- Kohustuslikud väljad ei ole alati selgelt eristatavad. CSS selector: `.checkout-form [required]`
- Tärni (*) tähendust ei selgitata. CSS selector: `.checkout-form .required-marker`
- Kasutajale ei ole alati selge, millist infot temalt oodatakse.

### Vastutaja
{: .no_toc }

✅ Arendaja  
✅ Sisutoimetaja

---

## WCAG 3.3.3 Error Suggestion

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#error-suggestion>

**EN 301 549 viide:**  
§9.3.3.3 Error Suggestion

### Esineb alamlehtedel
{: .no_toc }

- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)

### Probleem
{: .no_toc }

Veateated ei sisalda kasutajale soovitusi, kuidas sisestatud viga parandada. CSS selector: `.checkout-form .error-message`

### Vastutaja
{: .no_toc }

✅ Arendaja

---

## WCAG 3.1.1 Language of Page

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#language-of-page>

**EN 301 549 viide:**  
§9.3.1.1 Language of Page

### Esineb alamlehtedel
{: .no_toc }

- [Avaleht](https://www.test.ee/)
- [Odavad kaubad](https://www.test.ee/odavad-kaubad)
- [Toode](https://www.test.ee/toode)
- [Ostukorv](https://www.test.ee/ostukorv)
- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)
- [Kontaktid](https://www.test.ee/kontaktid)
- [Juhend](https://www.test.ee/juhend)
- [Kinkekaart](https://www.test.ee/kinkekaart)

### Probleem
{: .no_toc }

Vene- ja ingliskeelsetes vaadetes esineb tõlkimata sisu.

### Vastutaja
{: .no_toc }

✅ Sisutoimetaja

---

## WCAG 2.2.2 Pause, Stop, Hide

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#pause-stop-hide>

**EN 301 549 viide:**  
§9.2.2.2 Pause, Stop, Hide

### Esineb alamlehtedel
{: .no_toc }

- [Avaleht](https://www.test.ee/)

### Probleem
{: .no_toc }

Karusselli ei ole võimalik peatada. CSS selector: `.hero-carousel`

### Vastutaja
{: .no_toc }

✅ Arendaja

---

## WCAG 2.4.2 Page Titled

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#page-titled>

**EN 301 549 viide:**  
§9.2.4.2 Page Titled

### Esineb alamlehtedel
{: .no_toc }

- [Ostukorv](https://www.test.ee/ostukorv)

### Probleem
{: .no_toc }

Lehe pealkiri ei kirjelda ostukorvi vaadet.

### Vastutaja
{: .no_toc }

✅ Arendaja

---

## WCAG 1.3.5 Identify Input Purpose

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#identify-input-purpose>

**EN 301 549 viide:**  
§9.1.3.5 Identify Input Purpose

### Esineb alamlehtedel
{: .no_toc }

- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)

### Probleem
{: .no_toc }

Vormiväljadel puuduvad autocomplete atribuudid. CSS selector: `.checkout-form input[name="email"], .checkout-form input[name="phone"], .checkout-form input[name="address"]`

### Vastutaja
{: .no_toc }

✅ Arendaja

---

## WCAG 4.1.3 Status Messages

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#status-messages>

**EN 301 549 viide:**  
§9.4.1.3 Status Messages

### Esineb alamlehtedel
{: .no_toc }

- [Avaleht](https://www.test.ee/)
- [Odavad kaubad](https://www.test.ee/odavad-kaubad)
- [Toode](https://www.test.ee/toode)
- [Ostukorv](https://www.test.ee/ostukorv)
- [Kinkekaart](https://www.test.ee/kinkekaart)

### Probleemid
{: .no_toc }

- Otsingutulemuste arvust ei teavitata. CSS selector: `.search-results-count`
- Filtri mõjust ei teavitata. CSS selector: `.filter-results-status`
- Toote lisamisest ostukorvi ei teavitata. CSS selector: `.add-to-cart-button`
- Toote eemaldamisest ostukorvist ei teavitata. CSS selector: `.cart-item__remove`

### Vastutaja
{: .no_toc }

✅ Arendaja

---

## WCAG 2.4.3 Focus Order

**WCAG viide:**  
<https://www.w3.org/WAI/WCAG22/quickref/#focus-order>

**EN 301 549 viide:**  
§9.2.4.3 Focus Order

### Esineb alamlehtedel
{: .no_toc }

- [Toode](https://www.test.ee/toode)

### Probleem
{: .no_toc }

Klaviatuuri fookus liigub ootamatult jalusesse, mis muudab navigeerimise ebaloogiliseks. CSS selector: `.product-detail .product-gallery button, footer a`

### Vastutaja
{: .no_toc }

✅ Arendaja

---

# Lisaleiud

## EN 301 549 §11.7 User Preferences

**EN 301 549 viide:**  
§11.7 User Preferences

### Esineb alamlehtedel
{: .no_toc }

- [Avaleht](https://www.test.ee/)
- [Odavad kaubad](https://www.test.ee/odavad-kaubad)
- [Toode](https://www.test.ee/toode)
- [Ostukorv](https://www.test.ee/ostukorv)
- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)
- [Kontaktid](https://www.test.ee/kontaktid)
- [Juhend](https://www.test.ee/juhend)
- [Kinkekaart](https://www.test.ee/kinkekaart)

### Probleemid
{: .no_toc }

- Veebileht ei järgi kasutaja teksti suuruse eelistusi. CSS selector: `html, body, .page-content`
- Kõrgkontrastses vaates ei muutu kõik elemendid piisavalt loetavaks. CSS selector: `.button, .form-control, .product-card`
- Osa ikoone ja kasutajaliidese elemente ei kohandu operatsioonisüsteemi ligipääsetavuse seadistustega. CSS selector: `.icon-button svg, .header-actions svg`

### Vastutaja
{: .no_toc }

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

Audit tuvastas kokku **20 nõuet, mille puhul esines vähemalt üks mittevastavus**. Suurima mõjuga puudused on seotud klaviatuurikasutuse, ekraanilugeja toe, kontrastsuse ning semantilise struktuuriga. Nende parandamine tõstab oluliselt veebilehe vastavust standarditele EN 301 549 ja WCAG 2.2 ning parandab kasutuskogemust kõigile kasutajatele.
``