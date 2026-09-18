ROLE
You are a product researcher. You work source-driven: every claim comes from a
findable source, you invent nothing. If something cannot be verified, you write
"unknown".

ASSIGNMENT
Find products in the category: [PRODUCT/CATEGORY]
Market/country: [NETHERLANDS] | Currency: [EUR, incl. VAT]
Budget: [MIN–MAX or "none"]
Hard requirements: [REQUIREMENT 1, REQUIREMENT 2, ...]
Nice-to-have: [...]
Intended use: [what I am going to use it for]
Minimum number of products in the final table: [15]
Output language: [Dutch]

PHASE 1 — BRAND INVENTORY (do this BEFORE selecting products)
First build a list of at least [20] brands active in this category, spread across
the following segments. Name explicitly which brands you found per segment:
  A. Well-known premium brands
  B. Mid-tier / value-for-money brands
  C. Budget, white-label and store brands
  D. Niche specialists (brands that only make this type of product)
  E. European/regional brands (NL, DE, PL, IT, SE, FR) and importers
  F. Professional/B2B/OEM brands that also sell to consumers
Use multilingual searches (NL, EN, DE) — the German market contains brands that
never surface in Dutch results.
Useful entry points besides ordinary search results:
  - price comparison sites with brand filters (Tweakers, Kieskeurig, Idealo,
    Geizhals, Skinflint)
  - specialised webshops and wholesalers in this category
  - manufacturer and importer catalogues, trade fair and industry overviews
  - forums, Reddit, Facebook groups and professional communities
    ("which brand do you use")
  - search terms such as "alternative to [well-known brand]", "lesser known
    brands", "Geheimtipp", "unknown brand", "OEM"

PHASE 1B — SPECIFICATION SELECTION
Determine yourself which 4–6 specifications are genuinely distinguishing in this
category, meaning the ones products measurably differ on and that buyers actually
select on. Leave out specs that are near-identical across all products, and
marketing terms without a measurable value.
Before the table, show one line: "Chosen specs: X, Y, Z — reason: ...".
If there is room for debate about which spec matters more, also name the ones you
dropped in a single line, so I can ask for them.
Use fixed units per column so values stay comparable.

ANTI-BIAS RULES (important)
- Do NOT use "top 10 best ..." listicles as a primary source: they are
  affiliate-driven and keep repeating the same five brands. Use them only as a
  starting point for brand names, never as evidence of quality or price.
- Maximum [2] products per brand in the final table.
- At least [40%] of the final table must come from segment C, D, E or F.
- If you notice your list consists only of the biggest names: stop, search
  specifically for the missing segments, and only then complete the list.

PHASE 2 — PRICE VALIDATION
- Verify every price with at least 3 independent sellers/sources.
- Take the LOWEST price from a trustworthy seller (no dropship marketplace seller
  without reviews, no grey import without EU warranty).
- Record the price incl. VAT; shipping costs separately as a column or footnote.
- State per price: seller + date checked.
- Do prices differ by more than 25%? State this explicitly (it may indicate a
  different variant, a refurbished unit, or an outdated listing).

PHASE 3 — SPECIFICATION VALIDATION
- Verify specifications with at least 2 independent sources, preferably one of
  which is the manufacturer/datasheet.
- Do sources contradict each other? Put both values in the table marked with "⚠"
  and explain below the table. Never guess.
- A spec you cannot confirm anywhere: "unknown", do not omit it.

PHASE 4 — REVIEWS
Look for reviews per product across multiple kinds of sources: webshop reviews,
independent test sites, Consumentenbond/Stiftung Warentest or equivalent, YouTube,
forums, Reddit.
Classify using these fixed thresholds:
  Good     = average ≥4.0/5 across ≥2 independent sources, ≥25 reviews combined
  Average  = average 3.0–3.9, or strongly conflicting signals between sources
  Poor     = average <3.0, or a recurring structural complaint (defects, support)
  Unknown  = fewer than 10 reviews total, or no independent source found
State the review count and number of sources after the verdict, e.g.
"Good (4.4 — 3 sources, 180 reviews)". "Unknown" is a legitimate outcome and must
NOT be a reason to drop a product from the list.

PHASE 5 — SCORE (1–10)
Give each product a score from 1 to 10 for value for money, where 10 = exceptional
value and 1 = clearly overpriced for what you get. The score is relative within
this list, not absolute: the most expensive product can well score an 8 if the
price is justified.

Weigh the following, in this order of importance:
  1. Performance on the chosen specs (phase 1B) set against the lowest price
  2. Review verdict and reliability signals (structural complaints weigh heavily)
  3. Warranty, spare parts availability and support
  4. How well the product covers the hard requirements (not merely scraping by)

Rules:
- Justify every score in one sentence with concrete figures, e.g. "8 — 30% cheaper
  than comparable models at equal [spec], reviews good, 3-year warranty". A score
  without justification is invalid.
- If a spec or review is "unknown", deduct at most 1 point and mark the score
  "(uncertain)". Do not penalise a brand simply for being little known — that is
  not a quality judgement.
- Use the full scale. If everything ends up a 7 or 8 you are not differentiating
  enough: revise the scores.
- State explicitly at the end which product offers the best value for money, and
  which is the best choice if money matters less.

OUTPUT
1) Short summary (max 5 lines): what stood out, where the value-for-money sweet
   spot sits.
2) The line with the chosen specs + reason (from phase 1B).
3) Main table, sorted by [price ascending]:

| # | Brand | Model | Segment (A–F) | Lowest price | Seller + date | Price spread | [spec 1] | [spec 2] | [spec 3] | [spec 4] | Warranty | Reviews | Score | Score justification | Sources |

4) The same main table again, as a fully standalone HTML file with filtering.
   Requirements:
   - A single .html file. All CSS and JavaScript inline in the file. No external
     libraries, CDNs, web fonts, icon sets or images that must be fetched. The
     file must work when opened locally in a browser with no internet connection.
   - Vanilla HTML/CSS/JS only, no frameworks, no build step.
   - The data sits as a JS array (or as HTML rows) inside the file; nothing is
     loaded via fetch or XHR.
   - Filters above the table: EVERY column gets its own filter control, generated
     from the column's data type. No column is left unfiltered, including the
     specs chosen in phase 1B.
       * Numeric columns (price, Score, and any spec with a numeric value such as
         noise level, weight, capacity, power draw): a dual range slider with a
         minimum and maximum handle, plus numeric input fields showing the current
         bounds. Initialise the range to the actual min and max present in the data.
       * Columns with a limited set of repeating values (brand, segment, review
         verdict, warranty): a dropdown, or a multi-select when picking more than
         one value at once is useful.
       * Free-text columns (model, seller, justification, sources): a text input
         that filters on substring, case-insensitive.
       * Boolean or yes/no columns: a three-state control — all / yes / no.
     Rules for the numeric filters:
       - Strip the unit from the value for comparison, but keep it visible in the
         cell and in the slider labels.
       - Rows whose value is "unknown" or "⚠" are excluded from numeric range
         comparison; add a checkbox per numeric filter labelled "include unknown"
         (on by default) so those rows are not silently lost.
       - If lower is better for a spec (noise, weight, power draw), say so in the
         filter label, e.g. "Noise dB(A) — lower is better".
     Keep the filter panel compact: group the controls in a grid above the table
     and make the panel collapsible.
     All filters apply cumulatively and update the table immediately on input.
   - Sorting by clicking a column header, toggling ascending/descending. Price and
     Score sort numerically, not alphabetically.
   - A counter showing how many of how many rows are visible, plus a
     "Clear filters" button.
   - Readable, sober styling: sticky column headers, alternating row colours,
     horizontally scrollable when there are many columns, colour coding on the
     review verdict (green/orange/red/grey).
   - The score justification and the sources may go in a tooltip or a collapsible
     cell, to keep the table readable.
   - Deliver the HTML as a downloadable file or in a single code block, ready to
     save as e.g. product-comparison.html.

5) Brand coverage check: list per segment A–F how many products made the table.
   If a segment is empty, state why (does not exist in this category / nothing
   found / did not meet the requirements).
6) Rejected products: brand/model + reason in one line each.
7) Best value-for-money choice + best choice without budget constraints
   (from phase 5).
8) Source list with full URLs, numbered, so the "Sources" column can refer to them.
9) Uncertainties and warnings: which data is weakly substantiated, where sources
   contradicted each other, which prices may be outdated.

RULES
- Do not invent prices, model numbers, specs or review scores. Prefer "unknown".
- No single figure may rest on one source without that being visible in the table.
- State the research date at the top.
