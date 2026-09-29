# `CONTRIBUTING.md` — the Georgian section

> **For the PR.** Insert everything below the rule into `CONTRIBUTING.md` **after the
> English → Serbian glossary** (after its closing line *"If you correct or extend this
> table…"* and its `---`), immediately before `## Licence`.
>
> Also add one line to the **Table of contents**, under the two existing glossaries:
>
> ```markdown
>   - [English → Georgian glossary](#english--georgian-glossary)
> ```

---

### English → Georgian glossary

**Status: decided and applied.** This table is not a shortlist to choose from. Unlike the
French table (a researched starting point for the translator to overrule) and the Serbian
one (a stub seeded from the code base), every term here is already used in
`fiberq/i18n/fiberq_ka.ts`. Change a term here and the catalogue changes with it, in the
same pull request.

**Where these terms come from, and where they are weak.** The translator is a GIS and
QGIS-plugin developer, **not a fibre practitioner**. The terms rest on three things: the
maintainer's own `<extracomment>` notes, which define each concept precisely enough to
translate; established Georgian engineering and utility vocabulary — `ტრასა` for an
alignment, `მუფტა` for a joint closure, `ბოძი` for a pole, `მალი` for a span; and the
existing QGIS Georgian UI translation for the GIS half. That is enough for accuracy and
internal consistency. It is **not** the same as a Georgian fibre engineer signing off on the
vocabulary, and a review by one is welcome. One term is left flagged for exactly that
reason (see *Coverage and architecture*).

**The third column is the reasoning, not the definition.** In the French table it carries
the maintainer's domain knowledge. Here the definitions already live in the
`<extracomment>` notes, so this column says *why this Georgian word and not the obvious
one* — which is the part a reviewer needs in order to disagree usefully.

**Acronyms stay in Latin script.** `ODF`, `OTB`, `TO`, `TB`, `PP`, `JC`, `PE`, `OLT`,
`ONT`, `CRS`, `BOM`, `GPON`, `PON`, `FTTH` are not transliterated. Georgian fibre and GIS
practice writes them in Latin, and `ODF` doubles as a layer name in the code. Only the
qualifying word around an acronym is translated: `Indoor OTB` → `შიდა OTB`.

#### Georgian conventions that govern the whole catalogue

These are decided once and applied to every string, so they are not repeated term by term.
A future Georgian translator should read them before touching the `.ts` file.

| Convention | Decision | Why |
|---|---|---|
| **Letter case** | English Title Case is not reproduced. | Georgian has no capital letters. `Place Pole` → `ბოძის განთავსება`. |
| **Imperative menu entries** | Rendered as a verbal noun, not a true imperative. | Georgian UI convention, and what QGIS's own Georgian translation does: `ბოძის განთავსება`, not `განათავსე ბოძი`. |
| **Plural forms** | Georgian has **one** CLDR plural form. All 13 `numerus` messages show a single `<numerusform>` in Qt Linguist. | A noun stays singular after a numeral: `5 შეცდომა`, never `5 შეცდომები`. Translators arriving from the French examples in `docs/TRANSLATING.md` expect two boxes and find one — that is correct, not a bug. |
| **Case endings on placeholders** | The suffix attaches **outside** the braces: `'{layer}'-ში`, `{crs}-სთვის`, `{distance}-ითაა`, `ODF-ის`. | Keeps the placeholder byte-identical, as Rule 2 requires, while letting the sentence decline naturally. This is the most frequent trap in Georgian. |
| **Placeholder order** | Reordered freely where Georgian syntax requires it; never renamed or dropped. | Rule 2 permits moving them; several strings in the catalogue do. |
| **Toolbar-width strings** | Group labels reused 3–4× (`Cable laying`, `Drawings`, `Ducting`, `Routing`, `Selection`, `Drawing object`, `Placing elements`) are kept to one or two words. | One translation serves a menu title, a button caption, a tooltip and a status tip. |
| **GIS vocabulary** | Follows the existing QGIS Georgian UI translation rather than inventing terms. | The user is inside QGIS. Two vocabularies for *layer* would be worse than one imperfect one. |

#### Structures and civil works

| English | Georgian | Note |
|---|---|---|
| manhole / chamber | **საკაბელო ჭა** *(short: **ჭა**)* | **Not** `ლუქი` — that is only the cover. The field also says `კოლოდეცი`, a Russianism; `საკაბელო ჭა` is the written-document term. |
| duct / PE pipe | **მილი** *(menu: **PE მილი**)* | The English says *pipe* in the menu and *duct* everywhere else; the note asks for one word, and Georgian uses `მილი` for both. |
| transition pipe | **გადასასვლელის მილი** | The Ø 110 mm casing at a road/rail/water crossing. `დამცავი მილი` ("protective pipe") was rejected — it loses the *crossing* sense that the legacy Serbian `prelaz` carries. |
| ducting | **მილგაყვანილობა** | The whole duct infrastructure: manholes plus ducts. One word, for toolbar width. |
| trench | **თხრილი** | Not a UI string yet; listed for completeness. |
| pole | **ბოძი** | One word for both `Place Pole` and `Add pole` — the English differs, the object does not. |
| span | **მალი** | The established Georgian engineering term for the run between two supports. Not a bridge span. |
| route | **ტრასა** | **Critically not `მარშრუტი`**, which means a travel route. `ტრასა` is what a Georgian surveyor says for a physical alignment. Not a file or network path either. |
| routing | **ტრასირება** | The engineering act of setting out an alignment; names the tool group. |
| breakpoint | **გაყოფის წერტილი** | Resolved per the note as a **route-geometry split**, not a fault. `წყვეტა` was deliberately avoided so it cannot collide with *fiber break*. |

#### Cables and network segments

| English | Georgian | Note |
|---|---|---|
| cable laying | **კაბელის გაყვანა** | Gerund. Reused 4×, so it must stay this short. |
| underground | **მიწისქვეშა** | |
| aerial | **საჰაერო** | `საჰაერო ხაზი` (overhead line) is the established Georgian collocation. |
| backbone | **მაგისტრალი** *(as a cable class: **მაგისტრალური**)* | The noun names the concept; the menu uses the derived adjective so the three classes read as one parallel set. |
| distribution | **გამანაწილებელი** | The same adjective the Georgian power sector uses for distribution networks. |
| drop | **აბონენტური** | A **noun** in English (drop cable), rendered as an adjective to keep the set parallel: `მაგისტრალური / გამანაწილებელი / აბონენტური`. **Never the verb** — `ჩამოგდება` would be badly wrong. |
| fibre | **ოპტიკური ბოჭკო** *(short: **ბოჭკო**)* | |
| fibre count / capacity | **ტევადობა** | |
| slack | **მარაგი** | The spare coiled length. Matches the field's Russian `запас` (reserve). |
| terminal slack | **საბოლოო მარაგი** | At a cable **end**; drawn as a C coil. |
| mid span slack | **შუალედური მარაგი** | Where the cable passes **through** uncut; an S coil. `საბოლოო` vs `შუალედური` keeps the two unmistakably apart, as the note requires. |
| fiber break | **ბოჭკოს გაწყვეტა** | The **fault**. Kept lexically apart from both `გაყოფა` (breakpoint) and `გაჭრა` (cut infrastructure), which are geometry edits. |
| colour code | **ბოჭკოს ფერთა კოდი** | The TIA-598 / IEC tube-and-fibre sequence. `ფერების კატალოგი` was rejected: in a QGIS context it reads as a symbology palette, which the note explicitly warns against. |

#### Splicing and equipment

| English | Georgian | Note |
|---|---|---|
| splice | **შედუღება** | The fusion weld. Corresponds to the French *soudure*. |
| joint closure | **ოპტიკური მუფტა** *(short: **მუფტა**)* | `მუფტა` is universal in Georgian cable practice, which is why it beats any descriptive alternative. |
| patch panel | **პაჩ-პანელი** | `კომუტაციური პანელი` is more formal but less recognised in the field. Kept clearly distinct from ODF, whose scope overlaps. |
| indoor / outdoor / pole *(qualifiers)* | **შიდა / გარე / ბოძის** | `Pole OTB` → `ბოძის OTB` is **one element**, not a pole plus a box. |
| Joint Closure TO | **TO მუფტაში** | A TO housed inside a closure — one element, not two. Mirrors the Serbian `TO Izvod u nastavku`. |
| latent element | **შუალედური ელემენტი** | Per the note: a passive element recorded *on* a cable's path at a distance along it, between its endpoints — data, not a drawn feature. "Latent" = intermediate/pass-through, **not** faulty or dormant. Deliberately shares `შუალედური` with mid span slack: both are things recorded at an intermediate point along a cable. |

#### Coverage and architecture

| English | Georgian | Note |
|---|---|---|
| service area | **მომსახურების ზონა** | `სერვის-ზონა` is shorter and common in telecom marketing, but less precise. |
| branch | **განშტოება** | A cable junction point (French *dérivation*). Not a company branch, not a git branch. |
| relation *(optical)* | **ოპტიკური კავშირი** ⚠️ **flagged** | A named end-to-end optical link between two sites. **Not** a QGIS layer relation, which Georgian QGIS calls `ურთიერთკავშირი`. **This is the one term awaiting a practitioner's judgement** — a Georgian fibre engineer may prefer `ოპტიკური მიმართულება` ("optical direction"), which is how the trade often speaks of a named end-to-end link. Change it and the catalogue follows. |
| interchange bundle | **გაცვლითი კომპლექტი** | The open `.gpkg` / GeoJSON deliverable added in v1.5.0. `პაკეტი` was rejected: in Georgian it means a *software* package (a pip or deb package), which is the wrong reading for a data deliverable. |

#### Buildings — the trap worth stating twice

| English | Georgian | Note |
|---|---|---|
| Object | **შენობა** | Per the note, FiberQ's `Object` renders the legacy Serbian `objekat` and means a **building** — confirmed by the layer's fields (floors, basement levels, street, house number). |
| Feature | **ობიექტი** | The QGIS sense. |

Georgian QGIS already translates the GIS term *feature* as **`ობიექტი`** — literally
"object". So the obvious translation of FiberQ's `Object` is the one word that must not be
used for it. Without the `<extracomment>` note this would have been wrong in about ten
strings, silently and plausibly.

#### Validation and reporting

| English | Georgian | Note |
|---|---|---|
| validate project | **პროექტის ვალიდაცია** | The 14-rule engine. |
| health check | **მდგომარეობის შემოწმება** | A **different** feature. The two must not collapse into one Georgian word; `Check (health check)` keeps the bracketed term identical, as its note asks. |
| issue *(a finding)* | **ხარვეზი** | Consistent across `ValidationRules`, `ValidationPanel` and `ValidationReport`. |
| severity | **სიმძიმე** | |
| endpoint | **ბოლო წერტილი** | |
| near-miss | **ოდნავ დაცილება** | An endpoint just outside the snapping tolerance — not connected, but clearly meant to be. |
| allowed domain | **დაშვებულ მნიშვნელობათა ნაკრები** *(in messages: **დაშვებულთა შორის**)* | The strict enumeration. |
| plausible range | **გონივრული დიაპაზონი** | Deliberately weaker than `დაშვებული`. The English distinguishes a *plausible* numeric range from an *allowed* value domain, and the two rule names must not sound identical. |
| hand over | **ჩაბარება** | Delivery of the design to the client or authority — the word a Georgian designer uses. |
| BOM report | **მასალების ნუსხა (BOM)** | Bill of Materials. Not `ხარჯთაღრიცხვა`, which is a cost estimate. And, per the note, **not** the Unicode byte-order mark. |

#### Kept in English

**Acronyms:** `ODF` `OTB` `TO` `TB` `PP` `JC` `PE` `OLT` `ONT` `CRS` `BOM` `GPON` `PON` `FTTH`

**Formats and products:** `DWG` `DXF` `GPKG` `GeoPackage` `GeoJSON` `KML` `KMZ` `GPX`
`SHP` `XLSX` `CSV` `JSON` `PostGIS`

**Database columns:** `fiberq_uuid` `duzina_m` `duzina_km` `slack_m` `total_len_m` `duzina`
— including the legacy Serbian ones. Translating them would make the message unmatchable
against the actual schema.

**Layer names in quotes:** `'Poles'` `'Route'` — these are literal layer names the code
looks up, not words. The unquoted *"Route layer"* around them **is** translated.

**Menu paths and keys:** `Project -> Properties -> CRS`, `Ctrl+Shift+Z`, `ESC`, `R`.

If you correct or extend this table, please do it in the same pull request as the `.ts`
file so the two stay consistent.
