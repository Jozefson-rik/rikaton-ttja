---
layout: page
title: "Digiligipääsetavuse kontrolli aruanne: test.ee"
permalink: /
nav_order: 1
has_toc: true
toc_sticky: true
---

# Digiligipääsetavuse põhjaliku seire aruanne
{: .no_toc }

<div class="report-actions">
	<a class="download-button" href="https://raw.githubusercontent.com/Jozefson-rik/rikaton-ttja/main/docs/index.md" download>Laadi aruanne alla Markdown-failina</a>
	<button class="fold-all-button" type="button" id="fold-all-button" aria-expanded="true">Ava/Sulge kõik</button>
</div>

<button class="move-to-top-button" type="button" id="move-to-top-button" aria-label="Liigu lehe algusesse">↑</button>

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

	.markdown-body a {
		color: #003087;
	}

	.markdown-body a:hover {
		color: #2d5196;
	}

	.download-button {
		display: inline-block;
		margin: 1rem 0;
		padding: 0.6rem 0.9rem;
		border: 1px solid currentColor;
		border-radius: 4px;
		font-weight: 600;
		text-decoration: none;
	}

	.download-button:hover {
		text-decoration: underline;
	}

	.download-button:focus-visible {
		outline: 3px solid currentColor;
		outline-offset: 4px;
	}

	.report-actions {
		display: flex;
		flex-wrap: wrap;
		align-items: center;
		gap: 0.75rem;
		margin: 1rem 0;
	}

	.report-actions .download-button {
		margin: 0;
	}

	.fold-all-button {
		padding: 0.6rem 0.9rem;
		border: 1px solid currentColor;
		border-radius: 4px;
		background: transparent;
		color: inherit;
		font: inherit;
		font-weight: 600;
		cursor: pointer;
	}

	.fold-all-button:hover {
		text-decoration: underline;
	}

	.fold-all-button:focus-visible {
		outline: 3px solid currentColor;
		outline-offset: 4px;
	}

	.move-to-top-button {
		position: fixed;
		right: 1.5rem;
		bottom: 1.5rem;
		z-index: 10;
		width: 2.75rem;
		height: 2.75rem;
		border: 1px solid #003087;
		border-radius: 50%;
		background: #ffffff;
		color: #003087;
		font-size: 1.5rem;
		font-weight: 700;
		line-height: 1;
		cursor: pointer;
	}

	.move-to-top-button:hover {
		background: #003087;
		color: #ffffff;
	}

	.move-to-top-button:focus-visible {
		outline: 3px solid currentColor;
		outline-offset: 4px;
	}

	.copy-statement-button {
		margin: 0.5rem 0 1rem;
		padding: 0.6rem 0.9rem;
		border: 1px solid currentColor;
		border-radius: 4px;
		background: transparent;
		color: inherit;
		font: inherit;
		font-weight: 600;
		cursor: pointer;
	}

	.copy-statement-button:hover {
		text-decoration: underline;
	}

	.copy-statement-button:focus-visible {
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

	.report-section-toggle {
		width: 100%;
		display: flex;
		justify-content: space-between;
		align-items: center;
		gap: 1rem;
		padding: 0;
		border: 0;
		background: transparent;
		color: inherit;
		font: inherit;
		text-align: left;
		cursor: pointer;
	}

	.report-section-toggle:hover {
		text-decoration: underline;
	}

	.report-section-toggle:focus-visible {
		outline: 3px solid currentColor;
		outline-offset: 4px;
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
	const addAccessibleLinkLabels = () => {
		const pageNames = new Set([
			"Avaleht",
			"Odavad kaubad",
			"Toode",
			"Ostukorv",
			"Ostu vormistamine",
			"Kontaktid",
			"Juhend",
			"Kinkekaart",
		]);

		document.querySelectorAll(".markdown-body a").forEach((link) => {
			const linkText = link.textContent.trim();

			if (link.closest(".report-toc") || link.getAttribute("href")?.startsWith("#")) {
				return;
			}

			link.setAttribute("target", "_blank");
			link.setAttribute("rel", "noopener noreferrer");

			if (!link.getAttribute("aria-label") && pageNames.has(linkText)) {
				link.setAttribute("aria-label", `${linkText}, mõjutatud alamleht`);
			}
		});
	};

	const setupAuditFindingToggles = () => {
		const headings = Array.from(document.querySelectorAll(".markdown-body h1, .markdown-body h2, main h1, main h2, .main-content h1, .main-content h2"));
		const issueHeadingPattern = /^(WCAG|EN 301 549)/;
		const foldableSectionPattern = /^(Lähteandmed|Kokkuvõte)$/;

		headings.forEach((heading, index) => {
			if (heading.querySelector(".audit-finding-toggle")) {
				return;
			}

			const title = heading.textContent.replace(/Anchor\s*$/, "").trim();

			const isFinding = heading.tagName === "H2" && issueHeadingPattern.test(title);
			const isFoldableSection = heading.tagName === "H1" && foldableSectionPattern.test(title);

			if (!isFinding && !isFoldableSection) {
				return;
			}

			const panel = document.createElement("div");
			panel.className = "audit-finding-panel";
			panel.id = `audit-finding-panel-${index}`;

			let nextElement = heading.nextElementSibling;

			const boundaryTags = heading.tagName === "H1" ? ["H1"] : ["H1", "H2"];

			while (nextElement && !boundaryTags.includes(nextElement.tagName)) {
				const elementToMove = nextElement;
				nextElement = nextElement.nextElementSibling;
				panel.appendChild(elementToMove);
			}

			heading.after(panel);

			const button = document.createElement("button");
			button.className = isFinding ? "audit-finding-toggle" : "report-section-toggle";
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

		const foldAllButton = document.querySelector("#fold-all-button");
		const reportToc = document.querySelector(".report-toc");
		if (foldAllButton) {
			foldAllButton.addEventListener("click", () => {
				const panels = Array.from(document.querySelectorAll(".audit-finding-panel"));
				const shouldExpand = panels.some((panel) => panel.hidden) || (reportToc && !reportToc.open);

				panels.forEach((panel) => {
					panel.hidden = !shouldExpand;
				});

				if (reportToc) {
					reportToc.open = shouldExpand;
				}

				document.querySelectorAll(".audit-finding-toggle").forEach((toggle) => {
					toggle.setAttribute("aria-expanded", String(shouldExpand));
					const icon = toggle.querySelector(".audit-finding-toggle__icon");
					if (icon) {
						icon.textContent = shouldExpand ? "−" : "+";
					}
				});

				foldAllButton.setAttribute("aria-expanded", String(shouldExpand));
				foldAllButton.textContent = shouldExpand ? "Sulge kõik" : "Ava kõik";
			});
		}

		const moveToTopButton = document.querySelector("#move-to-top-button");
		if (moveToTopButton) {
			moveToTopButton.addEventListener("click", () => {
				window.scrollTo({ top: 0, behavior: "smooth" });
			});
		}

		const copyStatementButton = document.querySelector("#copy-statement-button");
		const statementHeading = copyStatementButton?.closest(".markdown-body")?.querySelector("h1:last-of-type")
			|| copyStatementButton?.previousElementSibling;

		if (copyStatementButton && statementHeading?.tagName === "H1") {
			copyStatementButton.addEventListener("click", async () => {
				const content = document.createElement("div");
				content.appendChild(statementHeading.cloneNode(true));
				let nextElement = statementHeading.nextElementSibling;

				while (nextElement && nextElement.tagName !== "H1") {
					if (nextElement !== copyStatementButton && nextElement.innerText.trim()) {
						content.appendChild(nextElement.cloneNode(true));
					}
					nextElement = nextElement.nextElementSibling;
				}

				const htmlToCopy = content.innerHTML;

				try {
					if (!navigator.clipboard?.writeText) {
						throw new Error("Clipboard API unavailable");
					}
					await navigator.clipboard.writeText(htmlToCopy);
				} catch {
					const textArea = document.createElement("textarea");
					textArea.value = htmlToCopy;
					textArea.setAttribute("readonly", "");
					textArea.style.position = "fixed";
					textArea.style.opacity = "0";
					document.body.appendChild(textArea);
					textArea.select();
					document.execCommand("copy");
					textArea.remove();
				}

				copyStatementButton.textContent = "Teatis kopeeritud";
				setTimeout(() => {
					copyStatementButton.textContent = "Kopeeri teatis";
				}, 2000);
			});
		}
	};

	if (document.readyState === "loading") {
		document.addEventListener("DOMContentLoaded", () => {
			addAccessibleLinkLabels();
			setupAuditFindingToggles();
		});
	} else {
		addAccessibleLinkLabels();
		setupAuditFindingToggles();
	}
</script>

---

# Lähteandmed

| Hindamise viis | käsitsi |
| Veebileht | [test.ee](https://www.test.ee/) |
| Hindamise läbiviija | Toomas ja pojad OÜ |
| Hindamise kuupäev | 26.08.2026 |
| Tagasiside tähtaeg | 30.12.2026 |
| Kontakt | [mingiemail@ttja.ee](mailto:mingiemail@ttja.ee) |
| Standard | EN 301 549 V3.2.1 / WCAG |
| Kontrolli liik | Põhjalik audit |
| Testitud alamlehti | 8 lehte<br>[Avaleht](https://www.test.ee/)<br>[Odavad kaubad](https://www.test.ee/odavad-kaubad)<br>[Toode](https://www.test.ee/toode)<br>[Ostukorv](https://www.test.ee/ostukorv)<br>[Ostu vormistamine](https://www.test.ee/ostu-vormistamine)<br>[Kontaktid](https://www.test.ee/kontaktid)<br>[Juhend](https://www.test.ee/juhend)<br>[Kinkekaart](https://www.test.ee/kinkekaart) |
| Kasutatud tööriistad | NVDA, WAVE, WebAIM Contrast Checker, Chrome, Firefox, Edge jt |

# Kokkuvõte

Auditi käigus kontrolliti veebilehe [test.ee](https://www.test.ee/) 8 alamlehte standardi EN 301 549 V3.2.1 ja WCAG nõuete alusel. Tuvastati **20 nõuet, mille puhul esines vähemalt üks mittevastavus**.

Tööde järjekord peaks olema järgmine: esmalt kõrvaldada põhifunktsioone takistavad kriitilised vead, seejärel parandada kontrastsuse ja fookuse probleemid ning lõpuks viimistleda sisu, tõlked ja teatis. Allolev nimekiri on mõeldud otse tööülesannete jagamiseks.

**Kui dokumendis pole alamlehti või WCAG nõudeid välja toodud, siis nende osas vigu ei tuvastatud.**

## TODO tööde jagamiseks

Iga ülesande lõpetamisel tuleks kontrollida nii hiire, klaviatuuri kui ka ekraanilugejaga ning märkida tulemus tööde nimekirjas. Aruande leiuplokid sisaldavad konkreetseid standardiviiteid, mõjutatud alamlehti ja CSS-valijaid, mida saab kasutada arenduspiletite koostamisel.

| Prioriteet | Raportiviide | Tegevus | Oodatav tulemus |
|---|---|---|---|
| 1 | [WCAG 2.1.1](#bug-wcag-211) | Parandada klaviatuurifookus, sisselogimise dialoog, otsingusoovitused ja vahelejäävad elemendid. | Kõiki põhifunktsioone saab kasutada ainult klaviatuuriga. |
| 2 | [WCAG 2.4.1](#bug-wcag-241) | Lisada põhisisuni viiv ülehüppamislink. | Kasutaja saab päisest ja menüüst otse põhisisuni liikuda. |
| 3 | [WCAG 1.3.1](#bug-wcag-131) | Parandada semantiline HTML, pealkirjatasemed, vormisildid ja dünaamiliste muudatuste semantika. | Ekraanilugeja saab lehe struktuurist ja seostest aru. |
| 4 | [WCAG 4.1.2](#bug-wcag-412) | Lisada menüüde, märkeruutude ja akordionide olekuteave. | Kasutajaliidese nimi, roll ja olek on abitehnoloogiale selged. |
| 5 | [WCAG 1.4.3](#bug-wcag-143) | Parandada teksti, linkide, hindade, placeholder'ite ja menüüelementide kontrastsus. | Tekst vastab kontrastsusnõuetele ja on loetav. |
| 6 | [WCAG 1.4.11](#bug-wcag-1411) | Parandada nuppude, sisestusväljade ja muude kasutajaliidese komponentide kontrastsus. | Komponendid eristuvad taustast piisavalt. |
| 7 | [WCAG 2.4.7](#bug-wcag-247) | Lisada nähtav fookus keelevahetajale, ikoonidele, nuppudele, märkeruutudele ja raadionuppudele. | Klaviatuuri fookus on alati nähtav. |
| 8 | [WCAG 1.1.1](#bug-wcag-111) | Lisada puuduvad alternatiivtekstid ja kirjeldused ikoonidele ning visuaalset infot sisaldavatele piltidele. | Informatiivne sisu on kättesaadav ka ilma visuaalse tajuta. |
| 9 | [WCAG 3.3.1](#bug-wcag-331) | Tähistada vigased vormiväljad visuaalselt. | Kasutaja tuvastab vigase välja kiiresti. |
| 10 | [WCAG 3.3.2](#bug-wcag-332) | Lisada vormidele selged juhised ja selgitada kohustuslike väljade tähistust. | Kasutaja teab, millist infot ja millises vormingus sisestada. |
| 11 | [WCAG 3.3.3](#bug-wcag-333) | Lisada veateadetele konkreetsed parandamise soovitused. | Kasutaja saab vea iseseisvalt parandada. |
| 12 | [WCAG 3.1.1](#bug-wcag-311) | Tõlkida vene- ja ingliskeelsetes vaadetes puuduv sisu. | Kõik avalikud vaated sisaldavad täielikku ja ühtset sisu. |
| 13 | [WCAG 2.2.2](#bug-wcag-222) | Lisada karussellile peatamise võimalus. | Liikuvat sisu saab kasutaja peatada. |
| 14 | [WCAG 2.4.2](#bug-wcag-242) | Määrata ostukorvi vaatele kirjeldav lehe pealkiri. | Lehe eesmärk on brauseris ja abitehnoloogias arusaadav. |
| 15 | [WCAG 1.3.5](#bug-wcag-135) | Lisada vormiväljadele sobivad `autocomplete` atribuudid. | Isikuandmete sisestamine on lihtsam ja täpsem. |
| 16 | [WCAG 4.1.3](#bug-wcag-413) | Lisada olekuteated otsingule, filtritele ja ostukorvi tegevustele. | Kasutaja saab teada dünaamiliste tegevuste tulemusest. |
| 17 | [WCAG 2.4.3](#bug-wcag-243) | Korrastada tootelehel klaviatuuri fookuse järjekord. | Fookus liigub kasutaja jaoks loogilises järjestuses. |
| 18 | [EN 301 549 §11.7](#bug-en-301-549-117) | Tagada teksti suuruse, kontrastsuse ja kasutajaliidese kohandumine kasutaja eelistustega. | Veebileht toimib paremini kasutaja ligipääsetavusseadetega. |

## Vastutusalad

| Vastutusala | Ülesanded |
|---|---|
| Arendaja | Klaviatuurikasutus<br>Kontrastsus<br>Fookuse haldus<br>ARIA atribuudid<br>Semantiline HTML<br>Olekuteated<br>Ülehüppamislink<br>Autocomplete atribuudid |
| Sisutoimetaja | Alternatiivtekstid<br>Tõlked<br>Veatekstid<br>Lehtede pealkirjad |
| Jagatud vastutus | Ligipääsetavuse teatis<br>Karussellid<br>Vormide kasutusloogika |

---

# Kriitilised probleemid

<a id="bug-wcag-211"></a>

## WCAG 2.1.1 Keyboard

| Hindamise viis | automaatne |
| EN 301 549 viide | §9.2.1.1 Keyboard |
| WCAG viide | [WCAG 2.1.1](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=2.1.1&id=wcag-2.1.1-2.1.1-success-criterion-3496a62ea785) |
| Vastutaja | ✅ Arendaja |

### Esineb alamlehtedel
{: .no_toc }

- [Avaleht](https://www.test.ee/): Klaviatuuri fookus ei liigu sisselogimise aknasse, vaid jääb taustal liikuma. Otsingusoovitused avanevad automaatselt ning neid ei ole võimalik vahele jätta. Jaluses jäetakse partnerite logod vahele.
- [Odavad kaubad](https://www.test.ee/odavad-kaubad): Lisaks sisselogimise akna ja otsingusoovituste probleemile ei liigu fookus sorteerimise valikule.
- [Toode](https://www.test.ee/toode): vt. eelmist kirjeldust
- [Ostukorv](https://www.test.ee/ostukorv): Klaviatuuri fookus jääb sisselogimise akna avamisel taustale liikuma ning otsingusoovitusi ei saa vahele jätta.
- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine): Lisaks üldistele klaviatuuriprobleemidele ei liigu fookus aja valiku aknale ning aega ei saa sisestusväljale trükkida.
- [Kontaktid](https://www.test.ee/kontaktid): Sisselogimise akna ja otsingusoovituste probleem kordub ning jaluses jäetakse partnerite logod vahele.
- [Juhend](https://www.test.ee/juhend): vt. eelmist kirjeldust
- [Kinkekaart](https://www.test.ee/kinkekaart): Sisselogimise akna ja otsingusoovituste probleem kordub ning jaluses jäetakse partnerite logod vahele.

### Tehniline viide
{: .no_toc }

- Fookus ei liigu sisselogimise dialoogi. CSS selector: `.login-dialog`
- Otsingusoovitused avanevad automaatselt. CSS selector: `.site-search__suggestions`
- Mõned juhtelemendid ei ole klaviatuuriga kasutatavad. CSS selector: `.product-card__quick-action`
- Osa elemente jäetakse vahele. CSS selector: `.main-navigation a, .header-actions button`

---

<a id="bug-wcag-241"></a>

## WCAG 2.4.1 Bypass Blocks

| Hindamise viis | automaatne |
| EN 301 549 viide | §9.2.4.1 Bypass Blocks |
| WCAG viide | [WCAG 2.4.1](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=2.4.1&id=wcag-2.4.1-2.4.1-success-criterion-03fff1a1bbfe) |
| Vastutaja | ✅ Arendaja |

### Esineb alamlehtedel
{: .no_toc }

- [Avaleht](https://www.test.ee/): Lehe päist ei ole võimalik vahele jätta.
- [Odavad kaubad](https://www.test.ee/odavad-kaubad): vt. eelmist kirjeldust
- [Toode](https://www.test.ee/toode): vt. eelmist kirjeldust
- [Ostukorv](https://www.test.ee/ostukorv): vt. eelmist kirjeldust
- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine): vt. eelmist kirjeldust
- [Kontaktid](https://www.test.ee/kontaktid): vt. eelmist kirjeldust
- [Juhend](https://www.test.ee/juhend): vt. eelmist kirjeldust
- [Kinkekaart](https://www.test.ee/kinkekaart): vt. eelmist kirjeldust

### Probleem
{: .no_toc }

- Puudub ülehüppamislink põhisisu juurde. CSS selector: `.skip-link`

---

<a id="bug-wcag-131"></a>

## WCAG 1.3.1 Info and Relationships

| Hindamise viis | automaatne |
| EN 301 549 viide | §9.1.3.1 Info and Relationships |
| WCAG viide | [WCAG 1.3.1](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=1.3.1&id=wcag-1.3.1-1.3.1-success-criterion-4f68d524e4c2) |
| Vastutaja | ✅ Arendaja |

### Esineb alamlehtedel
{: .no_toc }

- [Avaleht](https://www.test.ee/): Keelevahetuse menüü loetakse ette kui „Button ET“, kuid puudub täpsustus, et tegemist on keelevahetuse menüüga. Lehel on kaks suurt menüüd ilma eristava kirjelduseta ning puudub `h1` pealkiri.
- [Odavad kaubad](https://www.test.ee/odavad-kaubad): Keelevahetuse menüü ja menüüde eristamise probleem kordub. Toote koguse suurendamisest või ostukorvi lisamisest ei teavitata, lehel puudub `h2` ning paginatsioon ei anna teada, millisel lehel kasutaja asub.
- [Toode](https://www.test.ee/toode): Keelevahetuse menüü ja menüüde eristamise probleem kordub. Toote koguse suurendamisest või ostukorvi lisamisest ei teavitata.
- [Ostukorv](https://www.test.ee/ostukorv): Keelevahetuse menüü kirjeldus puudub. Toote eemaldamisest või koguse vähendamisest ostukorvis ei teavitata.
- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine): Keelevahetuse menüü kirjeldus puudub. Vahele on jäänud `h2` ning vormiväljad, raadionupud ja märkeruudud ei ole seotud oma siltidega.
- [Kontaktid](https://www.test.ee/kontaktid): Keelevahetuse menüü kirjeldus puudub.
- [Juhend](https://www.test.ee/juhend): Keelevahetuse menüü kirjeldus puudub ning alamlehel on tühi `h2` taseme pealkiri.
- [Kinkekaart](https://www.test.ee/kinkekaart): Keelevahetuse menüü kirjeldus puudub.

### Tehniline viide
{: .no_toc }

- Puuduvad või vahele jäetud pealkirjatasemed. CSS selector: `main h1, main h2, main h3`
- Vormiväljad ei ole seotud siltidega. CSS selector: `.checkout-form input, .checkout-form select`
- Menüüdel puuduvad eristavad kirjeldused. CSS selector: `nav.main-navigation, nav.footer-navigation`
- Dünaamilistest muudatustest ei teavitata. CSS selector: `.search-results, .cart-status`

---

<a id="bug-wcag-412"></a>

## WCAG 4.1.2 Name, Role, Value

| Hindamise viis | käsitsi |
| EN 301 549 viide | §9.4.1.2 Name, Role, Value |
| WCAG viide | [WCAG 4.1.2](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=4.1.2&id=wcag-4.1.2-4.1.2-success-criterion-260b752b491b) |
| Vastutaja | ✅ Arendaja |

### Esineb alamlehtedel
{: .no_toc }

- [Avaleht](https://www.test.ee/): Menüüd ei anna olekuteavet: aktiivne menüüpunkt ei ole tuvastatav ning alamenüü avatud või suletud olekut ei edastata.
- [Odavad kaubad](https://www.test.ee/odavad-kaubad): Menüüd ei anna olekuteavet ning märkeruutude puhul ei loeta ette, kas need on märgistatud või mitte.
- [Toode](https://www.test.ee/toode): Menüüd ei anna olekuteavet ning akordionide avatud või suletud olekut ei edastata.
- [Ostukorv](https://www.test.ee/ostukorv): vt. eelmist kirjeldust
- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine): Menüüd ei anna olekuteavet; aktiivne menüüpunkt ja alamenüü avatud või suletud olek ei ole abitehnoloogiale selged.
- [Kontaktid](https://www.test.ee/kontaktid): vt. eelmist kirjeldust
- [Juhend](https://www.test.ee/juhend): vt. eelmist kirjeldust
- [Kinkekaart](https://www.test.ee/kinkekaart): vt. eelmist kirjeldust

### Tehniline viide
{: .no_toc }

- Aktiivne menüüpunkt ei ole tuvastatav. CSS selector: `.main-navigation__link.is-active`
- Avatud/suletud olek puudub. CSS selector: `.menu-toggle, .filter-toggle`
- Märkeruutude olekut ei edastata. CSS selector: `.filter-panel input[type="checkbox"]`
- Akordionide olekuid ei loeta ette. CSS selector: `.accordion__trigger`

---

# Kõrge prioriteediga probleemid

<a id="bug-wcag-143"></a>

## WCAG 1.4.3 Contrast (Minimum)

| Hindamise viis | käsitsi |
| EN 301 549 viide | §9.1.4.3 Contrast (Minimum) |
| WCAG viide | [WCAG 1.4.3](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=1.4.3&id=wcag-1.4.3-1.4.3-success-criterion-06c311b42c2d) |
| Vastutaja | ✅ Arendaja |

### Esineb alamlehtedel
{: .no_toc }

- [Avaleht](https://www.test.ee/): Küpsiste akna sinise nupu ja valge teksti kontrastsus on 1.5:1. Peamenüü aktiivse ja hover-oleku kontrastsus on 4:1, otsinguvälja placeholder'i kontrastsus 3:1 ning ostukorvi halli teksti kontrastsus 2.5:1.
- [Odavad kaubad](https://www.test.ee/odavad-kaubad): Korduvad küpsiste akna, menüü, otsinguvälja ja ostukorvi kontrastsusprobleemid. Lisaks on leivapuru kontrastsus 3.5:1, toote hinna kontrastsus 3.5:1 ning sildi sinise tausta ja valge teksti kontrastsus 2.5:1.
- [Toode](https://www.test.ee/toode): vt. eelmist kirjeldust
- [Ostukorv](https://www.test.ee/ostukorv): Korduvad küpsiste akna, menüü, otsinguvälja ja ostukorvi kontrastsusprobleemid. Lisaks on „Teade“ välja placeholder'i kontrastsus 1.5:1, nuppude sinise teksti kontrastsus 4:1 ning vana läbikriipsutatud hinna kontrastsus 3.5:1.
- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine): Korduvad küpsiste akna, menüü, otsinguvälja ja ostukorvi kontrastsusprobleemid. Tagasi nupu hover-oleku kontrastsus on 4:1 ning ülevaates on halli teksti kontrastsus 3.74:1.
- [Kontaktid](https://www.test.ee/kontaktid): Korduvad küpsiste akna, menüü, otsinguvälja ja ostukorvi kontrastsusprobleemid. Linkide kontrastsus on 4:1 ning hover-olekus väheneb kontrastsus veelgi.
- [Juhend](https://www.test.ee/juhend): Peamenüü aktiivse ja hover-oleku kontrastsus on 4:1. Linkide kontrastsus on 4:1 ning hover-olekus väheneb kontrastsus veelgi.
- [Kinkekaart](https://www.test.ee/kinkekaart): vt. eelmist kirjeldust

### Tehniline viide
{: .no_toc }

- Küpsiste akna nupud. CSS selector: `.cookie-banner button`
- Placeholder-tekstid. CSS selector: `input::placeholder, textarea::placeholder`
- Hinnad. CSS selector: `.product-card__price, .product-detail__price`
- Leivapurud. CSS selector: `.breadcrumbs a`
- Lingid. CSS selector: `main a`
- Menüüelemendid. CSS selector: `.main-navigation__link`

---

<a id="bug-wcag-1411"></a>

## WCAG 1.4.11 Non-text Contrast

| Hindamise viis | automaatne |
| EN 301 549 viide | §9.1.4.11 Non-text Contrast |
| WCAG viide | [WCAG 1.4.11](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=1.4.11&id=wcag-1.4.11-1.4.11-success-criterion-7d1acb39f7f0) |
| Vastutaja | ✅ Arendaja |

### Esineb alamlehtedel
{: .no_toc }

- [Avaleht](https://www.test.ee/): „Logi sisse“ nupu tausta ja lehe tausta kontrastsus on 2:1. Ostukorvi nupu sinise tausta ja lehe tausta kontrastsus on 1.5:1.
- [Odavad kaubad](https://www.test.ee/odavad-kaubad): vt. eelmist kirjeldust
- [Toode](https://www.test.ee/toode): vt. eelmist kirjeldust
- [Ostukorv](https://www.test.ee/ostukorv): Korduvad sisselogimise ja ostukorvi nupu kontrastsusprobleemid. Lisaks on sisestusväljade piirjoone ja tausta kontrastsus 1.5:1.
- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine): vt. eelmist kirjeldust
- [Kontaktid](https://www.test.ee/kontaktid): Korduvad sisselogimise ja ostukorvi nupu kontrastsusprobleemid. Linkide teksti ja tausta kontrastsus on 4.36:1.
- [Juhend](https://www.test.ee/juhend): vt. eelmist kirjeldust
- [Kinkekaart](https://www.test.ee/kinkekaart): vt. eelmist kirjeldust

### Tehniline viide
{: .no_toc }

- Sisestusväljade piirjooned. CSS selector: `input, select, textarea`
- Ostukorvi nupud. CSS selector: `.cart-summary button, .cart-item__action`
- Sisselogimise nupud. CSS selector: `.login-dialog button`
- Muud kasutajaliidese komponendid ei eristu taustast piisavalt. CSS selector: `.button--secondary, .icon-button`

---

<a id="bug-wcag-247"></a>

## WCAG 2.4.7 Focus Visible

| Hindamise viis | käsitsi |
| EN 301 549 viide | §9.2.4.7 Focus Visible |
| WCAG viide | [WCAG 2.4.7](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=2.4.7&id=wcag-2.4.7-2.4.7-success-criterion-74ab3972e1d1) |
| Vastutaja | ✅ Arendaja |

### Esineb alamlehtedel
{: .no_toc }

- [Avaleht](https://www.test.ee/): Keele muutmise menüül, osadel ikoonidel ja osadel reklaamidel puudub nähtav fookus või see on halvasti eristatav.
- [Odavad kaubad](https://www.test.ee/odavad-kaubad): Keele muutmise menüül ja osadel ikoonidel puudub nähtav fookus. „Lisa ostukorvi“ nupul puudub samuti nähtav fookus.
- [Toode](https://www.test.ee/toode): vt. eelmist kirjeldust
- [Ostukorv](https://www.test.ee/ostukorv): Keele muutmise menüül ja osadel ikoonidel puudub nähtav fookus.
- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine): Keele muutmise menüül, osadel ikoonidel, märkeruutudel ja raadionuppudel puudub nähtav fookus.
- [Kontaktid](https://www.test.ee/kontaktid): Keele muutmise menüül puudub nähtav fookus.
- [Juhend](https://www.test.ee/juhend): vt. eelmist kirjeldust
- [Kinkekaart](https://www.test.ee/kinkekaart): vt. eelmist kirjeldust

### Tehniline viide
{: .no_toc }

- Keelevahetaja. CSS selector: `.language-switcher a, .language-switcher button`
- Ikoonid. CSS selector: `.icon-button`
- Ostukorvi nupud. CSS selector: `.cart-summary button, .cart-item__action`
- Märkeruudud. CSS selector: `input[type="checkbox"]`
- Raadionupud. CSS selector: `input[type="radio"]`

---

<a id="bug-wcag-111"></a>

## WCAG 1.1.1 Non-text Content

| Hindamise viis | käsitsi |
| EN 301 549 viide | §9.1.1.1 Non-text Content |
| WCAG viide | [WCAG 1.1.1](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=1.1.1&id=wcag-1.1.1-1.1.1-success-criterion-18548a3b09d7) |
| Vastutaja | ✅ Arendaja<br>✅ Sisutoimetaja |

### Esineb alamlehtedel
{: .no_toc }

- [Avaleht](https://www.test.ee/): Ostukorvi ikooni juures kuvatakse toodete kogus, kuid ekraanilugejale ei täpsustata, et number tähistab ostukorvis olevate toodete kogust. Osadel pakkumistel ei eristata uue ja vana hinna tähendust.
- [Odavad kaubad](https://www.test.ee/odavad-kaubad): Ostukorvi koguse tähendus ei ole ekraanilugejale selge. Paginatsioon loeb ette ainult numbrid, kuid ei täpsusta, et tegemist on lehtedega.
- [Toode](https://www.test.ee/toode): Ostukorvi koguse tähendus ei ole ekraanilugejale selge.
- [Ostukorv](https://www.test.ee/ostukorv): vt. eelmist kirjeldust
- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine): Ostukorvi koguse tähendus ei ole ekraanilugejale selge. Ülevaates oleval pakendi ikoonil puudub ligipääsetav kirjeldus.

### Tehniline viide
{: .no_toc }

- Reklaambännerid. CSS selector: `.promo-banner img`
- Tootepakendi ikoonid. CSS selector: `.product-badge img, .product-badge svg`
- Ostukorvi ikoon. CSS selector: `.header-cart__icon`
- Visuaalset infot sisaldavad pildid ilma piisava alternatiivkirjelduseta. CSS selector: `img:not([alt]), img[alt=""]`

---

# Keskmise prioriteediga probleemid

<a id="bug-wcag-331"></a>

## WCAG 3.3.1 Error Identification

| Hindamise viis | automaatne |
| EN 301 549 viide | §9.3.3.1 Error Identification |
| WCAG viide | [WCAG 3.3.1](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=3.3.1&id=wcag-3.3.1-3.3.1-success-criterion-cb1a373df5d2) |
| Vastutaja | ✅ Arendaja |

### Esineb alamlehtedel
{: .no_toc }

- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine): Vigase välja alla kuvatakse veateade, kuid väli ise ei ole visuaalselt eristatud.

### Probleem
{: .no_toc }

Vigane väli ei ole visuaalselt eristatav. Kuigi kuvatakse veateade, ei ole probleemne väli kasutajale piisavalt esile toodud. CSS selector: `.checkout-form .form-field--error input`

---

<a id="bug-wcag-332"></a>

## WCAG 3.3.2 Labels or Instructions

| Hindamise viis | käsitsi |
| EN 301 549 viide | §9.3.3.2 Labels or Instructions |
| WCAG viide | [WCAG 3.3.2](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=3.3.2&id=wcag-3.3.2-3.3.2-success-criterion-e66da61d25f3) |
| Vastutaja | ✅ Arendaja<br>✅ Sisutoimetaja |

### Esineb alamlehtedel
{: .no_toc }

- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine): Kohustuslike väljade ees on tärn (*), kuid puudub selgitus, mida see tähendab. Lehel on palju erineva kujundusega vorme ning osade vormide puhul ei ole aru saada, kas need on kohustuslikud või mitte.

### Tehniline viide
{: .no_toc }

- Kohustuslikud väljad ei ole alati selgelt eristatavad. CSS selector: `.checkout-form [required]`
- Tärni (*) tähendust ei selgitata. CSS selector: `.checkout-form .required-marker`
- Kasutajale ei ole alati selge, millist infot temalt oodatakse.

---

<a id="bug-wcag-333"></a>

## WCAG 3.3.3 Error Suggestion

| Hindamise viis | automaatne |
| EN 301 549 viide | §9.3.3.3 Error Suggestion |
| WCAG viide | [WCAG 3.3.3](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=3.3.3&id=wcag-3.3.3-3.3.3-success-criterion-cb5084410615) |
| Vastutaja | ✅ Arendaja |

### Esineb alamlehtedel
{: .no_toc }

- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine): Veateadetes puuduvad parandamise soovitused.

### Probleem
{: .no_toc }

Veateated ei sisalda kasutajale soovitusi, kuidas sisestatud viga parandada. CSS selector: `.checkout-form .error-message`

---

<a id="bug-wcag-311"></a>

## WCAG 3.1.1 Language of Page

| Hindamise viis | käsitsi |
| EN 301 549 viide | §9.3.1.1 Language of Page |
| WCAG viide | [WCAG 3.1.1](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=3.1.1&id=wcag-3.1.1-3.1.1-success-criterion-1fcbac084231) |
| Vastutaja | ✅ Sisutoimetaja |

### Esineb alamlehtedel
{: .no_toc }

- [Avaleht](https://www.test.ee/): Vene- ja ingliskeelses vaates on osa tekstidest tõlkimata.
- [Odavad kaubad](https://www.test.ee/odavad-kaubad): vt. eelmist kirjeldust
- [Toode](https://www.test.ee/toode): vt. eelmist kirjeldust
- [Ostukorv](https://www.test.ee/ostukorv): vt. eelmist kirjeldust
- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine): vt. eelmist kirjeldust
- [Kontaktid](https://www.test.ee/kontaktid): vt. eelmist kirjeldust
- [Juhend](https://www.test.ee/juhend): vt. eelmist kirjeldust
- [Kinkekaart](https://www.test.ee/kinkekaart): vt. eelmist kirjeldust

### Probleem
{: .no_toc }

Vene- ja ingliskeelsetes vaadetes esineb tõlkimata sisu.

---

<a id="bug-wcag-222"></a>

## WCAG 2.2.2 Pause, Stop, Hide

| Hindamise viis | automaatne |
| EN 301 549 viide | §9.2.2.2 Pause, Stop, Hide |
| WCAG viide | [WCAG 2.2.2](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=2.2.2&id=wcag-2.2.2-2.2.2-success-criterion-f1204e1d633d) |
| Vastutaja | ✅ Arendaja |

### Esineb alamlehtedel
{: .no_toc }

- [Avaleht](https://www.test.ee/): Avalehel on kasutusel karussell, mida ei ole võimalik peatada.

### Probleem
{: .no_toc }

Karusselli ei ole võimalik peatada. CSS selector: `.hero-carousel`

---

<a id="bug-wcag-242"></a>

## WCAG 2.4.2 Page Titled

| Hindamise viis | automaatne |
| EN 301 549 viide | §9.2.4.2 Page Titled |
| WCAG viide | [WCAG 2.4.2](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=2.4.2&id=wcag-2.4.2-2.4.2-success-criterion-029376ef6914) |
| Vastutaja | ✅ Arendaja |

### Esineb alamlehtedel
{: .no_toc }

- [Ostukorv](https://www.test.ee/ostukorv): Lehe tiitel on „test.ee“, mis ei anna teada, et tegemist on ostukorvi vaatega.

### Probleem
{: .no_toc }

Lehe pealkiri ei kirjelda ostukorvi vaadet.

---

<a id="bug-wcag-135"></a>

## WCAG 1.3.5 Identify Input Purpose

| Hindamise viis | käsitsi |
| EN 301 549 viide | §9.1.3.5 Identify Input Purpose |
| WCAG viide | [WCAG 1.3.5](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=1.3.5&id=wcag-1.3.5-1.3.5-success-criterion-fb80b741698f) |
| Vastutaja | ✅ Arendaja |

### Esineb alamlehtedel
{: .no_toc }

- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine): Vormidel puudub `autocomplete` atribuut.

### Probleem
{: .no_toc }

Vormiväljadel puuduvad autocomplete atribuudid. CSS selector: `.checkout-form input[name="email"], .checkout-form input[name="phone"], .checkout-form input[name="address"]`

---

<a id="bug-wcag-413"></a>

## WCAG 4.1.3 Status Messages

| Hindamise viis | käsitsi |
| EN 301 549 viide | §9.4.1.3 Status Messages |
| WCAG viide | [WCAG 4.1.3](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=4.1.3&id=wcag-4.1.3-4.1.3-success-criterion-bc7dc23b0a4f) |
| Vastutaja | ✅ Arendaja |

### Esineb alamlehtedel
{: .no_toc }

- [Avaleht](https://www.test.ee/): Otsingutulemuste puhul ei anta teada, mitu tulemust otsinguga leiti.
- [Odavad kaubad](https://www.test.ee/odavad-kaubad): Otsingutulemuste arvu ei teatata. Filtri rakendamisel ei anta automaatselt teada, mitu tulemust valikusse jäi.
- [Toode](https://www.test.ee/toode): vt. eelmist kirjeldust
- [Ostukorv](https://www.test.ee/ostukorv): Otsingutulemuste arvu ei teatata. Toote eemaldamisel ostukorvist ei anta teada, et toode eemaldati. Koguse muutmisel ei teatata, et muudatus tehti ega mitu eset ostukorvi jäi.
- [Kinkekaart](https://www.test.ee/kinkekaart): vt. eelmist kirjeldust

### Tehniline viide
{: .no_toc }

- Otsingutulemuste arvust ei teavitata. CSS selector: `.search-results-count`
- Filtri mõjust ei teavitata. CSS selector: `.filter-results-status`
- Toote lisamisest ostukorvi ei teavitata. CSS selector: `.add-to-cart-button`
- Toote eemaldamisest ostukorvist ei teavitata. CSS selector: `.cart-item__remove`

---

<a id="bug-wcag-243"></a>

## WCAG 2.4.3 Focus Order

| Hindamise viis | automaatne |
| EN 301 549 viide | §9.2.4.3 Focus Order |
| WCAG viide | [WCAG 2.4.3](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=2.4.3&id=wcag-2.4.3-2.4.3-success-criterion-9415829080b3) |
| Vastutaja | ✅ Arendaja |

### Esineb alamlehtedel
{: .no_toc }

- [Toode](https://www.test.ee/toode): Pärast sisselogimise nuppu liigub klaviatuuri fookus korraks jalusesse.

### Probleem
{: .no_toc }

Klaviatuuri fookus liigub ootamatult jalusesse, mis muudab navigeerimise ebaloogiliseks. CSS selector: `.product-detail .product-gallery button, footer a`

<a id="bug-en-301-549-117"></a>

## EN 301 549 §11.7 User Preferences

| Hindamise viis | käsitsi |
| EN 301 549 viide | §11.7 User Preferences |
| WCAG viide | Ei kohaldu. |
| Vastutaja | ✅ Arendaja |

### Esineb alamlehtedel
{: .no_toc }

- [Avaleht](https://www.test.ee/): Brauseris suurema teksti valimisel tekst ei suurene. Windowsi kõrgkontrastses vaates ei muutu osa tekste ja ikoone kõrgkontrastseks.
- [Odavad kaubad](https://www.test.ee/odavad-kaubad): vt. eelmist kirjeldust
- [Toode](https://www.test.ee/toode): vt. eelmist kirjeldust
- [Ostukorv](https://www.test.ee/ostukorv): Brauseris suurema teksti valimisel tekst ei suurene. Windowsi kõrgkontrastses vaates ei muutu osa tekste ja ikoone kõrgkontrastseks ning märkeruutudel kaob oleku eristus.
- [Ostu vormistamine](https://www.test.ee/ostu-vormistamine): vt. eelmist kirjeldust
- [Kontaktid](https://www.test.ee/kontaktid): vt. eelmist kirjeldust
- [Juhend](https://www.test.ee/juhend): vt. eelmist kirjeldust
- [Kinkekaart](https://www.test.ee/kinkekaart): vt. eelmist kirjeldust

### Tehniline viide
{: .no_toc }

- Veebileht ei järgi kasutaja teksti suuruse eelistusi. CSS selector: `html, body, .page-content`
- Kõrgkontrastses vaates ei muutu kõik elemendid piisavalt loetavaks. CSS selector: `.button, .form-control, .product-card`
- Osa ikoone ja kasutajaliidese elemente ei kohandu operatsioonisüsteemi ligipääsetavuse seadistustega. CSS selector: `.icon-button svg, .header-actions svg`

---

# Eeltäidetud teatis

<button class="copy-statement-button" type="button" id="copy-statement-button">Kopeeri teatis</button>

**Ligipääsetavuse teatis**

Alljärgnevalt kirjeldame vastavust ligipääsetavusnõuetele.

EL kehtib digiteenuste osutamisel ligipääsetavuse nõue, mis eeldab, et kõik avalikud teenused peavad olema ligipääsetavad. See tähendab et, see vastaks avaliku [teabe seaduse § 32](https://www.riigiteataja.ee/akt/AvTS#para32) alusel kehtestatud ligipääsetavusnõuetega (need on kehtestatud standardiga [EN 301 549 V.3.2.1](https://www.etsi.org/deliver/etsi_en/301500_301599/301549/03.02.01_60/en_301549v030201p.pdf)).

Käesolev avaldus kehtib Justiits- ja Digiministeeriumi hallatavale veebilehe test [test.ee](http://etoimik.rik.ee/) kohta.

**Töötame pidevalt ligipääsetavuse parandamiseks**

Selle süsteemi ligipääsetavust on hinnanud TTJA tellimusel ligipääsetavuse spetsialist: 13.08.2026.

**Digiteenuste ligipääsetavuse vastavus**

See veebisait vastab osaliselt avaliku teabe seaduse §32 nõuetele allpool loetletud põhjuste tõttu.

**Sisu ja funktsioonid, mis ei ole ligipääsetavad**

| Nr | Nõude tähistus standardis | Nõude nimi | Alamlehe/dokumendi/ekraanikuva nimi, kus mittevastavus esineb | Mittevastavuse lühiselgitus | Selgitus:<br>lahendus mittevastavuse kõrvaldamiseks - alternatiiv. Kõrvaldamise plaan. |
|---|---|---|---|---|---|
| 1 | EN 301 549 §9.2.1.1 Keyboard<br>[WCAG 2.1.1](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=2.1.1&id=wcag-2.1.1-2.1.1-success-criterion-3496a62ea785) | Keyboard | [Avaleht](https://www.test.ee/)<br>[Odavad kaubad](https://www.test.ee/odavad-kaubad)<br>[Ostukorv](https://www.test.ee/ostukorv)<br>[Ostu vormistamine](https://www.test.ee/ostu-vormistamine)<br>[Kontaktid](https://www.test.ee/kontaktid)<br>[Kinkekaart](https://www.test.ee/kinkekaart) | [Avaleht](https://www.test.ee/): Klaviatuuri fookus ei liigu sisselogimise aknasse, vaid jääb taustal liikuma. Otsingusoovitused avanevad automaatselt ning neid ei ole võimalik vahele jätta. Jaluses jäetakse partnerite logod vahele.<br>[Odavad kaubad](https://www.test.ee/odavad-kaubad): Lisaks sisselogimise akna ja otsingusoovituste probleemile ei liigu fookus sorteerimise valikule.<br>[Ostukorv](https://www.test.ee/ostukorv): Klaviatuuri fookus jääb sisselogimise akna avamisel taustale liikuma ning otsingusoovitusi ei saa vahele jätta.<br>[Ostu vormistamine](https://www.test.ee/ostu-vormistamine): Lisaks üldistele klaviatuuriprobleemidele ei liigu fookus aja valiku aknale ning aega ei saa sisestusväljale trükkida.<br>[Kontaktid](https://www.test.ee/kontaktid): Sisselogimise akna ja otsingusoovituste probleem kordub ning jaluses jäetakse partnerite logod vahele.<br>[Kinkekaart](https://www.test.ee/kinkekaart): Sisselogimise akna ja otsingusoovituste probleem kordub ning jaluses jäetakse partnerite logod vahele. | Tugineb eelmiste punktide kordategemisel. |
| 2 | EN 301 549 §9.2.4.1 Bypass Blocks<br>[WCAG 2.4.1](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=2.4.1&id=wcag-2.4.1-2.4.1-success-criterion-03fff1a1bbfe) | Bypass Blocks | [Avaleht](https://www.test.ee/) | [Avaleht](https://www.test.ee/): Lehe päist ei ole võimalik vahele jätta. | Voiceover on tasuline tarkvara |
| 3 | EN 301 549 §9.1.3.1 Info and Relationships<br>[WCAG 1.3.1](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=1.3.1&id=wcag-1.3.1-1.3.1-success-criterion-4f68d524e4c2) | Info and Relationships | [Avaleht](https://www.test.ee/)<br>[Odavad kaubad](https://www.test.ee/odavad-kaubad)<br>[Toode](https://www.test.ee/toode)<br>[Ostukorv](https://www.test.ee/ostukorv)<br>[Ostu vormistamine](https://www.test.ee/ostu-vormistamine)<br>[Kontaktid](https://www.test.ee/kontaktid)<br>[Juhend](https://www.test.ee/juhend)<br>[Kinkekaart](https://www.test.ee/kinkekaart) | [Avaleht](https://www.test.ee/): Keelevahetuse menüü loetakse ette kui „Button ET“, kuid puudub täpsustus, et tegemist on keelevahetuse menüüga. Lehel on kaks suurt menüüd ilma eristava kirjelduseta ning puudub `h1` pealkiri.<br>[Odavad kaubad](https://www.test.ee/odavad-kaubad): Keelevahetuse menüü ja menüüde eristamise probleem kordub. Toote koguse suurendamisest või ostukorvi lisamisest ei teavitata, lehel puudub `h2` ning paginatsioon ei anna teada, millisel lehel kasutaja asub.<br>[Toode](https://www.test.ee/toode): Keelevahetuse menüü ja menüüde eristamise probleem kordub. Toote koguse suurendamisest või ostukorvi lisamisest ei teavitata.<br>[Ostukorv](https://www.test.ee/ostukorv): Keelevahetuse menüü kirjeldus puudub. Toote eemaldamisest või koguse vähendamisest ostukorvis ei teavitata.<br>[Ostu vormistamine](https://www.test.ee/ostu-vormistamine): Keelevahetuse menüü kirjeldus puudub. Vahele on jäänud `h2` ning vormiväljad, raadionupud ja märkeruudud ei ole seotud oma siltidega.<br>[Kontaktid](https://www.test.ee/kontaktid): Keelevahetuse menüü kirjeldus puudub.<br>[Juhend](https://www.test.ee/juhend): Keelevahetuse menüü kirjeldus puudub ning alamlehel on tühi `h2` taseme pealkiri.<br>[Kinkekaart](https://www.test.ee/kinkekaart): Keelevahetuse menüü kirjeldus puudub. | Uue projekti raames. |
| 4 | EN 301 549 §9.4.1.2 Name, Role, Value<br>[WCAG 4.1.2](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=4.1.2&id=wcag-4.1.2-4.1.2-success-criterion-260b752b491b) | Name, Role, Value | [Avaleht](https://www.test.ee/)<br>[Odavad kaubad](https://www.test.ee/odavad-kaubad)<br>[Toode](https://www.test.ee/toode)<br>[Ostu vormistamine](https://www.test.ee/ostu-vormistamine) | [Avaleht](https://www.test.ee/): Menüüd ei anna olekuteavet: aktiivne menüüpunkt ei ole tuvastatav ning alamenüü avatud või suletud olekut ei edastata.<br>[Odavad kaubad](https://www.test.ee/odavad-kaubad): Menüüd ei anna olekuteavet ning märkeruutude puhul ei loeta ette, kas need on märgistatud või mitte.<br>[Toode](https://www.test.ee/toode): Menüüd ei anna olekuteavet ning akordionide avatud või suletud olekut ei edastata.<br>[Ostu vormistamine](https://www.test.ee/ostu-vormistamine): Menüüd ei anna olekuteavet; aktiivne menüüpunkt ja alamenüü avatud või suletud olek ei ole abitehnoloogiale selged. | Uue projekti raames. |
| 5 | EN 301 549 §9.1.4.3 Contrast (Minimum)<br>[WCAG 1.4.3](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=1.4.3&id=wcag-1.4.3-1.4.3-success-criterion-06c311b42c2d) | Contrast (Minimum) | [Avaleht](https://www.test.ee/)<br>[Odavad kaubad](https://www.test.ee/odavad-kaubad)<br>[Ostukorv](https://www.test.ee/ostukorv)<br>[Ostu vormistamine](https://www.test.ee/ostu-vormistamine)<br>[Kontaktid](https://www.test.ee/kontaktid)<br>[Juhend](https://www.test.ee/juhend) | [Avaleht](https://www.test.ee/): Küpsiste akna sinise nupu ja valge teksti kontrastsus on 1.5:1. Peamenüü aktiivse ja hover-oleku kontrastsus on 4:1, otsinguvälja placeholder'i kontrastsus 3:1 ning ostukorvi halli teksti kontrastsus 2.5:1.<br>[Odavad kaubad](https://www.test.ee/odavad-kaubad): Korduvad küpsiste akna, menüü, otsinguvälja ja ostukorvi kontrastsusprobleemid. Lisaks on leivapuru kontrastsus 3.5:1, toote hinna kontrastsus 3.5:1 ning sildi sinise tausta ja valge teksti kontrastsus 2.5:1.<br>[Ostukorv](https://www.test.ee/ostukorv): Korduvad küpsiste akna, menüü, otsinguvälja ja ostukorvi kontrastsusprobleemid. Lisaks on „Teade“ välja placeholder'i kontrastsus 1.5:1, nuppude sinise teksti kontrastsus 4:1 ning vana läbikriipsutatud hinna kontrastsus 3.5:1.<br>[Ostu vormistamine](https://www.test.ee/ostu-vormistamine): Korduvad küpsiste akna, menüü, otsinguvälja ja ostukorvi kontrastsusprobleemid. Tagasi nupu hover-oleku kontrastsus on 4:1 ning ülevaates on halli teksti kontrastsus 3.74:1.<br>[Kontaktid](https://www.test.ee/kontaktid): Korduvad küpsiste akna, menüü, otsinguvälja ja ostukorvi kontrastsusprobleemid. Linkide kontrastsus on 4:1 ning hover-olekus väheneb kontrastsus veelgi.<br>[Juhend](https://www.test.ee/juhend): Peamenüü aktiivse ja hover-oleku kontrastsus on 4:1. Linkide kontrastsus on 4:1 ning hover-olekus väheneb kontrastsus veelgi. | Voiceover on tasuline tarkvara |
| 6 | EN 301 549 §9.1.4.11 Non-text Contrast<br>[WCAG 1.4.11](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=1.4.11&id=wcag-1.4.11-1.4.11-success-criterion-7d1acb39f7f0) | Non-text Contrast | [Avaleht](https://www.test.ee/)<br>[Ostukorv](https://www.test.ee/ostukorv)<br>[Kontaktid](https://www.test.ee/kontaktid) | [Avaleht](https://www.test.ee/): „Logi sisse“ nupu tausta ja lehe tausta kontrastsus on 2:1. Ostukorvi nupu sinise tausta ja lehe tausta kontrastsus on 1.5:1.<br>[Ostukorv](https://www.test.ee/ostukorv): Korduvad sisselogimise ja ostukorvi nupu kontrastsusprobleemid. Lisaks on sisestusväljade piirjoone ja tausta kontrastsus 1.5:1.<br>[Kontaktid](https://www.test.ee/kontaktid): Korduvad sisselogimise ja ostukorvi nupu kontrastsusprobleemid. Linkide teksti ja tausta kontrastsus on 4.36:1. | Voiceover on tasuline tarkvara |
| 7 | EN 301 549 §9.2.4.7 Focus Visible<br>[WCAG 2.4.7](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=2.4.7&id=wcag-2.4.7-2.4.7-success-criterion-74ab3972e1d1) | Focus Visible | [Avaleht](https://www.test.ee/)<br>[Odavad kaubad](https://www.test.ee/odavad-kaubad)<br>[Ostukorv](https://www.test.ee/ostukorv)<br>[Ostu vormistamine](https://www.test.ee/ostu-vormistamine)<br>[Kontaktid](https://www.test.ee/kontaktid) | [Avaleht](https://www.test.ee/): Keele muutmise menüül, osadel ikoonidel ja osadel reklaamidel puudub nähtav fookus või see on halvasti eristatav.<br>[Odavad kaubad](https://www.test.ee/odavad-kaubad): Keele muutmise menüül ja osadel ikoonidel puudub nähtav fookus. „Lisa ostukorvi“ nupul puudub samuti nähtav fookus.<br>[Ostukorv](https://www.test.ee/ostukorv): Keele muutmise menüül ja osadel ikoonidel puudub nähtav fookus.<br>[Ostu vormistamine](https://www.test.ee/ostu-vormistamine): Keele muutmise menüül, osadel ikoonidel, märkeruutudel ja raadionuppudel puudub nähtav fookus.<br>[Kontaktid](https://www.test.ee/kontaktid): Keele muutmise menüül puudub nähtav fookus. | Tugineb eelmiste punktide kordategemisel. |
| 8 | EN 301 549 §9.1.1.1 Non-text Content<br>[WCAG 1.1.1](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=1.1.1&id=wcag-1.1.1-1.1.1-success-criterion-18548a3b09d7) | Non-text Content | [Avaleht](https://www.test.ee/)<br>[Odavad kaubad](https://www.test.ee/odavad-kaubad)<br>[Toode](https://www.test.ee/toode)<br>[Ostu vormistamine](https://www.test.ee/ostu-vormistamine) | [Avaleht](https://www.test.ee/): Ostukorvi ikooni juures kuvatakse toodete kogus, kuid ekraanilugejale ei täpsustata, et number tähistab ostukorvis olevate toodete kogust. Osadel pakkumistel ei eristata uue ja vana hinna tähendust.<br>[Odavad kaubad](https://www.test.ee/odavad-kaubad): Ostukorvi koguse tähendus ei ole ekraanilugejale selge. Paginatsioon loeb ette ainult numbrid, kuid ei täpsusta, et tegemist on lehtedega.<br>[Toode](https://www.test.ee/toode): Ostukorvi koguse tähendus ei ole ekraanilugejale selge.<br>[Ostu vormistamine](https://www.test.ee/ostu-vormistamine): Ostukorvi koguse tähendus ei ole ekraanilugejale selge. Ülevaates oleval pakendi ikoonil puudub ligipääsetav kirjeldus. | Uue projekti raames. |
| 9 | EN 301 549 §9.3.3.1 Error Identification<br>[WCAG 3.3.1](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=3.3.1&id=wcag-3.3.1-3.3.1-success-criterion-cb1a373df5d2) | Error Identification | [Ostu vormistamine](https://www.test.ee/ostu-vormistamine) | [Ostu vormistamine](https://www.test.ee/ostu-vormistamine): Vigase välja alla kuvatakse veateade, kuid väli ise ei ole visuaalselt eristatud. | Tugineb eelmiste punktide kordategemisel. |
| 10 | EN 301 549 §9.3.3.2 Labels or Instructions<br>[WCAG 3.3.2](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=3.3.2&id=wcag-3.3.2-3.3.2-success-criterion-e66da61d25f3) | Labels or Instructions | [Ostu vormistamine](https://www.test.ee/ostu-vormistamine) | [Ostu vormistamine](https://www.test.ee/ostu-vormistamine): Kohustuslike väljade ees on tärn (*), kuid puudub selgitus, mida see tähendab. Lehel on palju erineva kujundusega vorme ning osade vormide puhul ei ole aru saada, kas need on kohustuslikud või mitte. | Uue projekti raames. |
| 11 | EN 301 549 §9.3.3.3 Error Suggestion<br>[WCAG 3.3.3](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=3.3.3&id=wcag-3.3.3-3.3.3-success-criterion-cb5084410615) | Error Suggestion | [Ostu vormistamine](https://www.test.ee/ostu-vormistamine) | [Ostu vormistamine](https://www.test.ee/ostu-vormistamine): Veateadetes puuduvad parandamise soovitused. | Voiceover on tasuline tarkvara |
| 12 | EN 301 549 §9.3.1.1 Language of Page<br>[WCAG 3.1.1](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=3.1.1&id=wcag-3.1.1-3.1.1-success-criterion-1fcbac084231) | Language of Page | [Avaleht](https://www.test.ee/) | [Avaleht](https://www.test.ee/): Vene- ja ingliskeelses vaates on osa tekstidest tõlkimata. | Uue projekti raames. |
| 13 | EN 301 549 §9.2.2.2 Pause, Stop, Hide<br>[WCAG 2.2.2](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=2.2.2&id=wcag-2.2.2-2.2.2-success-criterion-f1204e1d633d) | Pause, Stop, Hide | [Avaleht](https://www.test.ee/) | [Avaleht](https://www.test.ee/): Avalehel on kasutusel karussell, mida ei ole võimalik peatada. | Uue projekti raames. |
| 14 | EN 301 549 §9.2.4.2 Page Titled<br>[WCAG 2.4.2](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=2.4.2&id=wcag-2.4.2-2.4.2-success-criterion-029376ef6914) | Page Titled | [Ostukorv](https://www.test.ee/ostukorv) | [Ostukorv](https://www.test.ee/ostukorv): Lehe tiitel on „test.ee“, mis ei anna teada, et tegemist on ostukorvi vaatega. | Voiceover on tasuline tarkvara |
| 15 | EN 301 549 §9.1.3.5 Identify Input Purpose<br>[WCAG 1.3.5](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=1.3.5&id=wcag-1.3.5-1.3.5-success-criterion-fb80b741698f) | Identify Input Purpose | [Ostu vormistamine](https://www.test.ee/ostu-vormistamine) | [Ostu vormistamine](https://www.test.ee/ostu-vormistamine): Vormidel puudub `autocomplete` atribuut. | Voiceover on tasuline tarkvara |
| 16 | EN 301 549 §9.4.1.3 Status Messages<br>[WCAG 4.1.3](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=4.1.3&id=wcag-4.1.3-4.1.3-success-criterion-bc7dc23b0a4f) | Status Messages | [Avaleht](https://www.test.ee/)<br>[Odavad kaubad](https://www.test.ee/odavad-kaubad)<br>[Ostukorv](https://www.test.ee/ostukorv) | [Avaleht](https://www.test.ee/): Otsingutulemuste puhul ei anta teada, mitu tulemust otsinguga leiti.<br>[Odavad kaubad](https://www.test.ee/odavad-kaubad): Otsingutulemuste arvu ei teatata. Filtri rakendamisel ei anta automaatselt teada, mitu tulemust valikusse jäi.<br>[Ostukorv](https://www.test.ee/ostukorv): Otsingutulemuste arvu ei teatata. Toote eemaldamisel ostukorvist ei anta teada, et toode eemaldati. Koguse muutmisel ei teatata, et muudatus tehti ega mitu eset ostukorvi jäi. | Tugineb eelmiste punktide kordategemisel. |
| 17 | EN 301 549 §9.2.4.3 Focus Order<br>[WCAG 2.4.3](https://mariakesa.github.io/rikaton/wcag_kb/?lang=et&wcag=2.4.3&id=wcag-2.4.3-2.4.3-success-criterion-9415829080b3) | Focus Order | [Toode](https://www.test.ee/toode) | [Toode](https://www.test.ee/toode): Pärast sisselogimise nuppu liigub klaviatuuri fookus korraks jalusesse. | Voiceover on tasuline tarkvara |
| 18 | EN 301 549 §11.7 User Preferences<br>WCAG: ei kohaldu | User Preferences | [Avaleht](https://www.test.ee/)<br>[Ostukorv](https://www.test.ee/ostukorv) | [Avaleht](https://www.test.ee/): Brauseris suurema teksti valimisel tekst ei suurene. Windowsi kõrgkontrastses vaates ei muutu osa tekste ja ikoone kõrgkontrastseks.<br>[Ostukorv](https://www.test.ee/ostukorv): Brauseris suurema teksti valimisel tekst ei suurene. Windowsi kõrgkontrastses vaates ei muutu osa tekste ja ikoone kõrgkontrastseks ning märkeruutudel kaob oleku eristus. | Tugineb eelmiste punktide kordategemisel. |

***Allpool loetletud sisule rakendub ebaproportsionaalne koormuse erand.***

Puudub.

***Allpool loetletud sisu ei kuulu kohaldatavate õigusnormide kohaldamisalasse***

Puudub.

**Tagasiside**

Andke ligipääsetavuse kohta tagasisidet kirjutades kasutajatoele.

E-post: [info@pelmeen.ee](mailto:info@pelmeen.ee)

Telefon: +372 680 3160

Vastame teile tavaliselt E-N 9.00-17.00, R 9.00-14.00.

**Ligipääsetavuse järelevalve asutus**

Avalike teenuste veebide ja rakenduste ligipääsetavuse osas teostab järelevalvet Tarbijakaitse ja Tehnilise Järelevalve Amet.

Veebileht: [www.ttja.ee](http://www.ttja.ee/)

E-post: [info@ttja.ee](mailto:info@ttja.ee)

Telefon: 667 2000

**Veebilehe testimine**

Käesolev avaldus on koostatud 23.01.2024.