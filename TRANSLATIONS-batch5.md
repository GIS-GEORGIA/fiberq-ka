# Batch 5 — the interchange bundle (20)

The 20 strings added to `FiberQPlugin` in v1.5.0, for the **interchange bundle** export and
import. They are the difference between the 306 strings drafted against `fiberq_fr.ts` in
batches 1–4 and the **326** in the seeded `fiberq/i18n/fiberq_ka.ts`
([PR #47](https://github.com/vukovicvl/fiberq/pull/47)).

Verified by diffing the seeded catalogue against batches 1–4: **325 of 326 source strings
already had a Georgian draft; exactly these 20 did not.** All of them are in
`FiberQPlugin`, exactly as the maintainer said.

!!! note "No translator notes on these"
    The catalogue carries 95 `<extracomment>` notes, but **none of them are on these 20** —
    they are new in v1.5.0 and have not been annotated. Where the English was ambiguous I
    say so below rather than guessing silently.

---

## The term: `interchange bundle`

**Georgian: `გაცვლითი კომპლექტი`**

An *interchange bundle* is an open, tool-neutral package of the design — either a single
`.gpkg` file or a folder of GeoJSON files — meant for handing the project to software that
is not FiberQ.

- `interchange` → **გაცვლითი** (for exchange between tools)
- `bundle` → **კომპლექტი** (a package of several parts)

`კომპლექტი` is the same word used for FiberQ Designer's `.fqz` portable bundle, which is a
different feature of a different product but the same underlying idea — several things
packed into one deliverable. Keeping one word for both keeps the two products readable
side by side.

!!! tip "Why not `პაკეტი`"
    `პაკეტი` is the everyday Georgian word for a software package (a pip package, a deb).
    Using it here would invite exactly the wrong reading — this is a data deliverable, not
    an installable.

---

## Menu entries and actions (7)

| English | ქართული | Note |
|---|---|---|
| Export interchange bundle… | გაცვლითი კომპლექტის ექსპორტი… | **U+2026** — Qt's "opens a dialog" convention. |
| Import interchange bundle… | გაცვლითი კომპლექტის იმპორტი… | Same. |
| Export interchange bundle | გაცვლითი კომპლექტის ექსპორტი | **A separate string from the one above**, without the ellipsis — kept distinct. |
| Import FiberQ interchange bundle | FiberQ-ის გაცვლითი კომპლექტის იმპორტი | Dialog title. |
| Export FiberQ interchange bundle | FiberQ-ის გაცვლითი კომპლექტის ექსპორტი | Dialog title. **Also distinct from the plain "Export interchange bundle"** — the English carries the product name here. |
| Write the design as an open FiberQ interchange bundle (.gpkg) | პროექტის ჩაწერა FiberQ-ის ღია გაცვლითი კომპლექტის სახით (.gpkg) | Tooltip. `open` = **ღია** in the open-format sense, not "opened". |
| Read an open FiberQ interchange bundle into this project | FiberQ-ის ღია გაცვლითი კომპლექტის წაკითხვა ამ პროექტში | Tooltip. |

!!! warning "Four near-identical strings"
    `Export interchange bundle`, `Export interchange bundle…`, `Export FiberQ interchange
    bundle` — three separate catalogue entries that differ only by an ellipsis and the
    product name. Qt treats them as three unrelated strings. **Each keeps its own exact
    form in Georgian**; do not collapse them.

## File filters (2)

| English | ქართული | Note |
|---|---|---|
| GeoPackage bundle (*.gpkg) | GeoPackage კომპლექტი (*.gpkg) | Qt file filter — the glob pattern is untouched. |
| GeoJSON bundle — a folder, no relations (*) | GeoJSON კომპლექტი — საქაღალდე, კავშირების გარეშე (*) | The `(*)` pattern is untouched. "no relations" = the GeoJSON form cannot carry the relational tables a GeoPackage can. |

## Confirmation prompts (2)

| English | ქართული | Note |
|---|---|---|
| The folder {name} already exists. Write the bundle into it? | საქაღალდე {name} უკვე არსებობს. ჩაიწეროს კომპლექტი მასში? | |
| Replace the bundle {name}? | ჩანაცვლდეს კომპლექტი {name}? | |

## Explanatory text under the prompts (2)

These two are the long lines that tell the user what is and is not destroyed. They matter
more than their length suggests.

| English | ქართული |
|---|---|
| Existing GeoJSON files for the same element types are replaced. Other files in the folder are left alone. | იმავე ტიპის ელემენტების არსებული GeoJSON ფაილები ჩანაცვლდება. საქაღალდის სხვა ფაილებს არაფერი ემართება. |
| Its FiberQ layers are rewritten from this project. Anything another tool stored in the file -- its own metadata keys and relational tables -- is kept, not discarded. | მისი FiberQ-ის შრეები ამ პროექტიდან თავიდან ჩაიწერება. ყველაფერი, რაც ფაილში სხვა პროგრამამ შეინახა — მისი საკუთარი მეტამონაცემების გასაღებები და რელაციური ცხრილები — შენარჩუნდება და არ წაიშლება. |

The `--` in the second string is a double hyphen in the source; Georgian uses an em dash.
That is punctuation, not a placeholder, so adapting it is allowed.

!!! abstract "The reassurance is the point"
    Both strings exist to say *what survives*. A user about to overwrite a GeoPackage that
    another tool also writes to needs to read "kept, not discarded" and believe it. The
    Georgian keeps that emphasis at the end of the sentence, where Georgian puts it.

## Results (3)

| English | ქართული | Note |
|---|---|---|
| Wrote {path} — {summary} | ჩაიწერა {path} — {summary} | |
| Imported {path} — {summary} | იმპორტირებულია {path} — {summary} | |
| Carried through unchanged, with no FiberQ layer to draw them in: {kinds}. They survive the next export. | უცვლელად გადმოტანილია, რადგან FiberQ-ის შრე, რომელშიც დაიხატებოდა, არ არსებობს: {kinds}. შემდეგ ექსპორტში ისინი შენარჩუნდება. | Things the bundle carried that FiberQ has no layer for. Georgian makes the causal link explicit (`რადგან …`), which English leaves to apposition. |

## Errors (4)

| English | ქართული |
|---|---|
| Could not write the bundle: {details} | კომპლექტის ჩაწერა ვერ მოხერხდა: {details} |
| Could not read the bundle: {details} | კომპლექტის წაკითხვა ვერ მოხერხდა: {details} |
| Bundle export failed: {details} | კომპლექტის ექსპორტი ვერ შესრულდა: {details} |
| Import failed: {details} | იმპორტი ვერ შესრულდა: {details} |

*(`Export failed: {details}` looks like it belongs here but is not new — it already existed
and was translated in batch 4.)*

---

## Self-check against the three rules

- **Rule 1** — no `<source>` touched.
- **Rule 2** — placeholders in this batch: `{details}` ×4, `{path}` ×2, `{summary}` ×2,
  `{name}` ×2, `{kinds}` ×1. All reproduced exactly, lowercase, both braces. None
  reordered — the English order suits Georgian here. Two Qt file filters keep their glob
  patterns. One ellipsis pair (`…`, U+2026) preserved on the two menu entries that carry it
  and **not** added to the two that do not.
- **Rule 3** — nothing compiled.

## Terms added to the glossary

`interchange bundle` → **გაცვლითი კომპლექტი** · `bundle` → **კომპლექტი** ·
`folder` → **საქაღალდე** · `relations` *(in the GeoJSON sense)* → **კავშირები** ·
`metadata keys` → **მეტამონაცემების გასაღებები** ·
`relational tables` → **რელაციური ცხრილები**

---

## Progress against the real catalogue

| Batch | Context(s) | Strings | Status |
|---|---|---:|---|
| 1 | toolbar, menus, element names (11 contexts) | 76 | drafted |
| 2 | `ValidationRules` | 45 | drafted |
| 3 | `ValidationReport` + `ValidationPanel` | 53 | drafted |
| 4 | `FiberQPlugin` (v1.4.0) | 132 | drafted |
| 5 | `FiberQPlugin` — interchange bundle (v1.5.0) | 20 | drafted |
| | **Total** | **326** | **326 (100%)** |

The seeded catalogue has **326 `type="unfinished"` slots**, and every one now has a
Georgian draft waiting for it.
