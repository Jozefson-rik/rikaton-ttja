---
layout: page
title: "Digiligipääsetavuse kontrolli aruanne: test.ee"
permalink: /
nav_order: 1
has_toc: true
toc_sticky: true
---

# Digiligipääsetavuse kontrolli aruanne: [test.ee](https://www.test.ee/)

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

# Kokkuvõte

## Aruande lähteandmed

| Väli | Väärtus |
|--------|--------|
| Veebileht | test.ee |
| Standard | EN 301 549 V3.2.1 / WCAG |
| Kontrolli liik | Põhjalik audit |
| Testitud alamlehti | 8 |
| Kasutatud tööriistad | NVDA, WAVE, WebAIM Contrast Checker, Chrome, Firefox, Edge jt |

## Üldtulemus

Veebilehel tuvastati märkimisväärne arv digiligipääsetavuse probleeme, mis mõjutavad klaviatuurikasutajaid, ekraanilugeja kasutajaid, vaegnägijaid ning kasutajaid, kes kasutavad suurendust või kõrgkontrastseid režiime.

---

# Kriitilised probleemid

## WCAG 2.1.1 Keyboard

| Väli | Väärtus |
|---|---|
| EN 310 549 viide | §9.2.1.1 Keyboard |
| WCAG viide | <https://www.w3.org/WAI/WCAG22/quickref/#keyboard> |
| Mõju kasutajale | Kõik kasutajad ei saa veebilehte kasutada ainult klaviatuuriga. |
| Vastutaja | ✅ Arendaja |

### Lühiselgitused
{: .no_toc }

- **Avaleht:** Klaviatuuri fookus ei liigu sisselogimise aknasse, vaid jääb taustal liikuma. Otsingusoovitused avanevad automaatselt ning neid ei ole võimalik vahele jätta. Jaluses jäetakse partnerite logod vahele.
- **Odavad kaubad:** Lisaks sisselogimise akna ja otsingusoovituste probleemile ei liigu fookus sorteerimise valikule.
- **Ostukorv:** Klaviatuuri fookus jääb sisselogimise akna avamisel taustale liikuma ning otsingusoovitusi ei saa vahele jätta.
- **Ostu vormistamine:** Lisaks üldistele klaviatuuriprobleemidele ei liigu fookus aja valiku aknale ning aega ei saa sisestusväljale trükkida.
- **Kontaktid:** Sisselogimise akna ja otsingusoovituste probleem kordub ning jaluses jäetakse partnerite logod vahele.
- **Kinkekaart:** Sisselogimise akna ja otsingusoovituste probleem kordub ning jaluses jäetakse partnerite logod vahele.

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

- Fookus ei liigu sisselogimise dialoogi. CSS selector: `.login-dialog`
- Otsingusoovitused avanevad automaatselt. CSS selector: `.site-search__suggestions`
- Mõned juhtelemendid ei ole klaviatuuriga kasutatavad. CSS selector: `.product-card__quick-action`
- Osa elemente jäetakse vahele. CSS selector: `.main-navigation a, .header-actions button`

---

## WCAG 2.4.1 Bypass Blocks

| Väli | Väärtus |
|---|---|
| EN 310 549 viide | §9.2.4.1 Bypass Blocks |
| WCAG viide | <https://www.w3.org/WAI/WCAG22/quickref/#bypass-blocks> |
| Mõju kasutajale | Klaviatuuri- ja ekraanilugejakasutajad peavad igal lehel läbima kogu päise ja menüü enne põhisisuni jõudmist. |
| Vastutaja | ✅ Arendaja |

### Lühiselgitused
{: .no_toc }

- **Avaleht:** Lehe päist ei ole võimalik vahele jätta.

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

- Puudub ülehüppamislink põhisisu juurde. CSS selector: `.skip-link`

---

## WCAG 1.3.1 Info and Relationships

| Väli | Väärtus |
|---|---|
| EN 310 549 viide | §9.1.3.1 Info and Relationships |
| WCAG viide | <https://www.w3.org/WAI/WCAG22/quickref/#info-and-relationships> |
| Mõju kasutajale | Ekraanilugejad ei saa veebilehe struktuuri korrektselt edasi anda. |
| Vastutaja | ✅ Arendaja |

### Lühiselgitused
{: .no_toc }

- **Avaleht:** Keelevahetuse menüü loetakse ette kui „Button ET“, kuid puudub täpsustus, et tegemist on keelevahetuse menüüga. Lehel on kaks suurt menüüd ilma eristava kirjelduseta ning puudub `h1` pealkiri.
- **Odavad kaubad:** Keelevahetuse menüü ja menüüde eristamise probleem kordub. Toote koguse suurendamisest või ostukorvi lisamisest ei teavitata, lehel puudub `h2` ning paginatsioon ei anna teada, millisel lehel kasutaja asub.
- **Toode:** Keelevahetuse menüü ja menüüde eristamise probleem kordub. Toote koguse suurendamisest või ostukorvi lisamisest ei teavitata.
- **Ostukorv:** Keelevahetuse menüü kirjeldus puudub. Toote eemaldamisest või koguse vähendamisest ostukorvis ei teavitata.
- **Ostu vormistamine:** Keelevahetuse menüü kirjeldus puudub. Vahele on jäänud `h2` ning vormiväljad, raadionupud ja märkeruudud ei ole seotud oma siltidega.
- **Kontaktid:** Keelevahetuse menüü kirjeldus puudub.
- **Juhend:** Keelevahetuse menüü kirjeldus puudub ning alamlehel on tühi `h2` taseme pealkiri.
- **Kinkekaart:** Keelevahetuse menüü kirjeldus puudub.

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

- Puuduvad või vahele jäetud pealkirjatasemed. CSS selector: `main h1, main h2, main h3`
- Vormiväljad ei ole seotud siltidega. CSS selector: `.checkout-form input, .checkout-form select`
- Menüüdel puuduvad eristavad kirjeldused. CSS selector: `nav.main-navigation, nav.footer-navigation`
- Dünaamilistest muudatustest ei teavitata. CSS selector: `.search-results, .cart-status`

---

## WCAG 4.1.2 Name, Role, Value

| Väli | Väärtus |
|---|---|
| EN 310 549 viide | §9.4.1.2 Name, Role, Value |
| WCAG viide | <https://www.w3.org/WAI/WCAG22/quickref/#name-role-value> |
| Mõju kasutajale | Ekraanilugeja kasutajad ei saa kasutajaliidese elementide olekust aru. |
| Vastutaja | ✅ Arendaja |

### Lühiselgitused
{: .no_toc }

- **Avaleht:** Menüüd ei anna olekuteavet: aktiivne menüüpunkt ei ole tuvastatav ning alamenüü avatud või suletud olekut ei edastata.
- **Odavad kaubad:** Menüüd ei anna olekuteavet ning märkeruutude puhul ei loeta ette, kas need on märgistatud või mitte.
- **Toode:** Menüüd ei anna olekuteavet ning akordionide avatud või suletud olekut ei edastata.
- **Ostu vormistamine:** Menüüd ei anna olekuteavet; aktiivne menüüpunkt ja alamenüü avatud või suletud olek ei ole abitehnoloogiale selged.

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

- Aktiivne menüüpunkt ei ole tuvastatav. CSS selector: `.main-navigation__link.is-active`
- Avatud/suletud olek puudub. CSS selector: `.menu-toggle, .filter-toggle`
- Märkeruutude olekut ei edastata. CSS selector: `.filter-panel input[type="checkbox"]`
- Akordionide olekuid ei loeta ette. CSS selector: `.accordion__trigger`

---

# Kõrge prioriteediga probleemid

## WCAG 1.4.3 Contrast (Minimum)

| Väli | Väärtus |
|---|---|
| EN 310 549 viide | §9.1.4.3 Contrast (Minimum) |
| WCAG viide | <https://www.w3.org/WAI/WCAG22/quickref/#contrast-minimum> |
| Mõju kasutajale | Ei ole eraldi välja toodud. |
| Vastutaja | ✅ Arendaja |

### Lühiselgitused
{: .no_toc }

- **Avaleht:** Küpsiste akna sinise nupu ja valge teksti kontrastsus on 1.5:1. Peamenüü aktiivse ja hover-oleku kontrastsus on 4:1, otsinguvälja placeholder'i kontrastsus 3:1 ning ostukorvi halli teksti kontrastsus 2.5:1.
- **Odavad kaubad:** Korduvad küpsiste akna, menüü, otsinguvälja ja ostukorvi kontrastsusprobleemid. Lisaks on leivapuru kontrastsus 3.5:1, toote hinna kontrastsus 3.5:1 ning sildi sinise tausta ja valge teksti kontrastsus 2.5:1.
- **Ostukorv:** Korduvad küpsiste akna, menüü, otsinguvälja ja ostukorvi kontrastsusprobleemid. Lisaks on „Teade“ välja placeholder'i kontrastsus 1.5:1, nuppude sinise teksti kontrastsus 4:1 ning vana läbikriipsutatud hinna kontrastsus 3.5:1.
- **Ostu vormistamine:** Korduvad küpsiste akna, menüü, otsinguvälja ja ostukorvi kontrastsusprobleemid. Tagasi nupu hover-oleku kontrastsus on 4:1 ning ülevaates on halli teksti kontrastsus 3.74:1.
- **Kontaktid:** Korduvad küpsiste akna, menüü, otsinguvälja ja ostukorvi kontrastsusprobleemid. Linkide kontrastsus on 4:1 ning hover-olekus väheneb kontrastsus veelgi.
- **Juhend:** Peamenüü aktiivse ja hover-oleku kontrastsus on 4:1. Linkide kontrastsus on 4:1 ning hover-olekus väheneb kontrastsus veelgi.

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

---

## WCAG 1.4.11 Non-text Contrast

| Väli | Väärtus |
|---|---|
| EN 310 549 viide | §9.1.4.11 Non-text Contrast |
| WCAG viide | <https://www.w3.org/WAI/WCAG22/quickref/#non-text-contrast> |
| Mõju kasutajale | Ei ole eraldi välja toodud. |
| Vastutaja | ✅ Arendaja |

### Lühiselgitused
{: .no_toc }

- **Avaleht:** „Logi sisse“ nupu tausta ja lehe tausta kontrastsus on 2:1. Ostukorvi nupu sinise tausta ja lehe tausta kontrastsus on 1.5:1.
- **Ostukorv:** Korduvad sisselogimise ja ostukorvi nupu kontrastsusprobleemid. Lisaks on sisestusväljade piirjoone ja tausta kontrastsus 1.5:1.
- **Kontaktid:** Korduvad sisselogimise ja ostukorvi nupu kontrastsusprobleemid. Linkide teksti ja tausta kontrastsus on 4.36:1.

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

---

## WCAG 2.4.7 Focus Visible

| Väli | Väärtus |
|---|---|
| EN 310 549 viide | §9.2.4.7 Focus Visible |
| WCAG viide | <https://www.w3.org/WAI/WCAG22/quickref/#focus-visible> |
| Mõju kasutajale | Ei ole eraldi välja toodud. |
| Vastutaja | ✅ Arendaja |

### Lühiselgitused
{: .no_toc }

- **Avaleht:** Keele muutmise menüül, osadel ikoonidel ja osadel reklaamidel puudub nähtav fookus või see on halvasti eristatav.
- **Odavad kaubad:** Keele muutmise menüül ja osadel ikoonidel puudub nähtav fookus. „Lisa ostukorvi“ nupul puudub samuti nähtav fookus.
- **Ostukorv:** Keele muutmise menüül ja osadel ikoonidel puudub nähtav fookus.
- **Ostu vormistamine:** Keele muutmise menüül, osadel ikoonidel, märkeruutudel ja raadionuppudel puudub nähtav fookus.
- **Kontaktid:** Keele muutmise menüül puudub nähtav fookus.

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

---

## WCAG 1.1.1 Non-text Content

| Väli | Väärtus |
|---|---|
| EN 310 549 viide | §9.1.1.1 Non-text Content |
| WCAG viide | <https://www.w3.org/WAI/WCAG22/quickref/#non-text-content> |
| Mõju kasutajale | Ei ole eraldi välja toodud. |
| Vastutaja | ✅ Arendaja<br>✅ Sisutoimetaja |

### Lühiselgitused
{: .no_toc }

- **Avaleht:** Ostukorvi ikooni juures kuvatakse toodete kogus, kuid ekraanilugejale ei täpsustata, et number tähistab ostukorvis olevate toodete kogust. Osadel pakkumistel ei eristata uue ja vana hinna tähendust.
- **Odavad kaubad:** Ostukorvi koguse tähendus ei ole ekraanilugejale selge. Paginatsioon loeb ette ainult numbrid, kuid ei täpsusta, et tegemist on lehtedega.
- **Toode:** Ostukorvi koguse tähendus ei ole ekraanilugejale selge.
- **Ostu vormistamine:** Ostukorvi koguse tähendus ei ole ekraanilugejale selge. Ülevaates oleval pakendi ikoonil puudub ligipääsetav kirjeldus.

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

---

# Keskmise prioriteediga probleemid

## WCAG 3.3.1 Error Identification

| Väli | Väärtus |
|---|---|
| EN 310 549 viide | §9.3.3.1 Error Identification |
| WCAG viide | <https://www.w3.org/WAI/WCAG22/quickref/#error-identification> |
| Mõju kasutajale | Ei ole eraldi välja toodud. |
| Vastutaja | ✅ Arendaja |

### Lühiselgitused
{: .no_toc }

- **Ostu vormistamine:** Vigase välja alla kuvatakse veateade, kuid väli ise ei ole visuaalselt eristatud.

### Esineb alamlehtedel
{: .no_toc }

- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)

### Probleem
{: .no_toc }

Vigane väli ei ole visuaalselt eristatav. Kuigi kuvatakse veateade, ei ole probleemne väli kasutajale piisavalt esile toodud. CSS selector: `.checkout-form .form-field--error input`

---

## WCAG 3.3.2 Labels or Instructions

| Väli | Väärtus |
|---|---|
| EN 310 549 viide | §9.3.3.2 Labels or Instructions |
| WCAG viide | <https://www.w3.org/WAI/WCAG22/quickref/#labels-or-instructions> |
| Mõju kasutajale | Ei ole eraldi välja toodud. |
| Vastutaja | ✅ Arendaja<br>✅ Sisutoimetaja |

### Lühiselgitused
{: .no_toc }

- **Ostu vormistamine:** Kohustuslike väljade ees on tärn (*), kuid puudub selgitus, mida see tähendab. Lehel on palju erineva kujundusega vorme ning osade vormide puhul ei ole aru saada, kas need on kohustuslikud või mitte.

### Esineb alamlehtedel
{: .no_toc }

- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)

### Probleemid
{: .no_toc }

- Kohustuslikud väljad ei ole alati selgelt eristatavad. CSS selector: `.checkout-form [required]`
- Tärni (*) tähendust ei selgitata. CSS selector: `.checkout-form .required-marker`
- Kasutajale ei ole alati selge, millist infot temalt oodatakse.

---

## WCAG 3.3.3 Error Suggestion

| Väli | Väärtus |
|---|---|
| EN 310 549 viide | §9.3.3.3 Error Suggestion |
| WCAG viide | <https://www.w3.org/WAI/WCAG22/quickref/#error-suggestion> |
| Mõju kasutajale | Ei ole eraldi välja toodud. |
| Vastutaja | ✅ Arendaja |

### Lühiselgitused
{: .no_toc }

- **Ostu vormistamine:** Veateadetes puuduvad parandamise soovitused.

### Esineb alamlehtedel
{: .no_toc }

- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)

### Probleem
{: .no_toc }

Veateated ei sisalda kasutajale soovitusi, kuidas sisestatud viga parandada. CSS selector: `.checkout-form .error-message`

---

## WCAG 3.1.1 Language of Page

| Väli | Väärtus |
|---|---|
| EN 310 549 viide | §9.3.1.1 Language of Page |
| WCAG viide | <https://www.w3.org/WAI/WCAG22/quickref/#language-of-page> |
| Mõju kasutajale | Ei ole eraldi välja toodud. |
| Vastutaja | ✅ Sisutoimetaja |

### Lühiselgitused
{: .no_toc }

- **Avaleht:** Vene- ja ingliskeelses vaates on osa tekstidest tõlkimata.

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

---

## WCAG 2.2.2 Pause, Stop, Hide

| Väli | Väärtus |
|---|---|
| EN 310 549 viide | §9.2.2.2 Pause, Stop, Hide |
| WCAG viide | <https://www.w3.org/WAI/WCAG22/quickref/#pause-stop-hide> |
| Mõju kasutajale | Ei ole eraldi välja toodud. |
| Vastutaja | ✅ Arendaja |

### Lühiselgitused
{: .no_toc }

- **Avaleht:** Avalehel on kasutusel karussell, mida ei ole võimalik peatada.

### Esineb alamlehtedel
{: .no_toc }

- [Avaleht](https://www.test.ee/)

### Probleem
{: .no_toc }

Karusselli ei ole võimalik peatada. CSS selector: `.hero-carousel`

---

## WCAG 2.4.2 Page Titled

| Väli | Väärtus |
|---|---|
| EN 310 549 viide | §9.2.4.2 Page Titled |
| WCAG viide | <https://www.w3.org/WAI/WCAG22/quickref/#page-titled> |
| Mõju kasutajale | Ei ole eraldi välja toodud. |
| Vastutaja | ✅ Arendaja |

### Lühiselgitused
{: .no_toc }

- **Ostukorv:** Lehe tiitel on „test.ee“, mis ei anna teada, et tegemist on ostukorvi vaatega.

### Esineb alamlehtedel
{: .no_toc }

- [Ostukorv](https://www.test.ee/ostukorv)

### Probleem
{: .no_toc }

Lehe pealkiri ei kirjelda ostukorvi vaadet.

---

## WCAG 1.3.5 Identify Input Purpose

| Väli | Väärtus |
|---|---|
| EN 310 549 viide | §9.1.3.5 Identify Input Purpose |
| WCAG viide | <https://www.w3.org/WAI/WCAG22/quickref/#identify-input-purpose> |
| Mõju kasutajale | Ei ole eraldi välja toodud. |
| Vastutaja | ✅ Arendaja |

### Lühiselgitused
{: .no_toc }

- **Ostu vormistamine:** Vormidel puudub `autocomplete` atribuut.

### Esineb alamlehtedel
{: .no_toc }

- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine)

### Probleem
{: .no_toc }

Vormiväljadel puuduvad autocomplete atribuudid. CSS selector: `.checkout-form input[name="email"], .checkout-form input[name="phone"], .checkout-form input[name="address"]`

---

## WCAG 4.1.3 Status Messages

| Väli | Väärtus |
|---|---|
| EN 310 549 viide | §9.4.1.3 Status Messages |
| WCAG viide | <https://www.w3.org/WAI/WCAG22/quickref/#status-messages> |
| Mõju kasutajale | Ei ole eraldi välja toodud. |
| Vastutaja | ✅ Arendaja |

### Lühiselgitused
{: .no_toc }

- **Avaleht:** Otsingutulemuste puhul ei anta teada, mitu tulemust otsinguga leiti.
- **Odavad kaubad:** Otsingutulemuste arvu ei teatata. Filtri rakendamisel ei anta automaatselt teada, mitu tulemust valikusse jäi.
- **Ostukorv:** Otsingutulemuste arvu ei teatata. Toote eemaldamisel ostukorvist ei anta teada, et toode eemaldati. Koguse muutmisel ei teatata, et muudatus tehti ega mitu eset ostukorvi jäi.

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

---

## WCAG 2.4.3 Focus Order

| Väli | Väärtus |
|---|---|
| EN 310 549 viide | §9.2.4.3 Focus Order |
| WCAG viide | <https://www.w3.org/WAI/WCAG22/quickref/#focus-order> |
| Mõju kasutajale | Ei ole eraldi välja toodud. |
| Vastutaja | ✅ Arendaja |

### Lühiselgitused
{: .no_toc }

- **Toode:** Pärast sisselogimise nuppu liigub klaviatuuri fookus korraks jalusesse.

### Esineb alamlehtedel
{: .no_toc }

- [Toode](https://www.test.ee/toode)

### Probleem
{: .no_toc }

Klaviatuuri fookus liigub ootamatult jalusesse, mis muudab navigeerimise ebaloogiliseks. CSS selector: `.product-detail .product-gallery button, footer a`

---

# Lisaleiud

## EN 301 549 §11.7 User Preferences

| Väli | Väärtus |
|---|---|
| EN 310 549 viide | §11.7 User Preferences |
| WCAG viide | Ei kohaldu. |
| Mõju kasutajale | Ei ole eraldi välja toodud. |
| Vastutaja | ✅ Arendaja |

### Lühiselgitused
{: .no_toc }

- **Avaleht:** Brauseris suurema teksti valimisel tekst ei suurene. Windowsi kõrgkontrastses vaates ei muutu osa tekste ja ikoone kõrgkontrastseks.
- **Ostukorv:** Brauseris suurema teksti valimisel tekst ei suurene. Windowsi kõrgkontrastses vaates ei muutu osa tekste ja ikoone kõrgkontrastseks ning märkeruutudel kaob oleku eristus.

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