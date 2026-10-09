# Case Study — Sustainability & Data
## "Eco-Friendly Product Classification"

> Take-home case study · Suggested effort ~6–8 hours · Submission window 5 days · **Use of AI is allowed** (how you use it will also be assessed).

---

### Context
**Teknosa** is one of Turkey's large technology/electronics retailers. Erguvan already works with Teknosa: we collect its **carbon and ESG data** on our platform **Azalt**.

**What we have already done.** For a retailer, most of the footprint sits in the products it sells, so we built product-level calculations for three **Scope 3** categories:

| Scope 3 category | What it covers for Teknosa |
|---|---|
| **Cat. 1 — Purchased goods** | Emissions from manufacturing the products Teknosa buys for resale |
| **Cat. 11 — Use of sold products** | Energy the products consume while customers use them |
| **Cat. 12 — End-of-life treatment** | Disposal and recycling of the products at end of life |

To do this, we went to the manufacturers' websites for the brands Teknosa buys and used their APIs to collect every product **EPD** (Environmental Product Declaration) and product carbon footprint we could find. EPDs report impacts by life-cycle stage (manufacturing, use, end of life), so they map naturally onto categories 1, 11 and 12. From these we built a **product pool** and assigned a footprint to each purchased product with a fallback hierarchy:

1. **Exact match:** the product's own EPD (e.g. the specific Dell laptop model).
2. **Brand + category average:** if it has no EPD, the average of comparable models from the same brand (e.g. Dell laptops).
3. **Category average:** if that is also missing, the average across the whole category (e.g. all laptops).

**Where the new request comes from.** With this data in hand, Teknosa now wants to go a step further: highlight the **environmentally better-performing products** in its catalogue with a label on its website and in stores.

Teknosa's firm requirement: do this **not** based on its own subjective opinion, but on **internationally recognized, verifiable sources**, while avoiding **greenwashing** risk. You are the Erguvan consultant leading this project.

Keep in mind that data built for *corporate carbon accounting* is not automatically fit for a *customer-facing product claim*. An average is fine for a Scope 3 inventory, but not as evidence that a specific product is "eco-friendly." Part of the job is deciding which evidence is strong enough for a label.

### Starting point
You will **not** be given a product list. You will **build the portfolio yourself** from Teknosa's publicly available sources (e.g. teknosa.com). While doing so, respect the site's terms of use and `robots.txt`, and keep your request rate reasonable.

### Sources
You decide which sources to use to assess the products' environmental performance and how to access them. Given our existing work, **manufacturer EPDs and product carbon footprints are a natural place to start**. Also look at what other verified sources exist (energy labels, eco-certifications, etc.) and how they complement or conflict with EPD data. **If you cannot access a source, do not fabricate data — document what you tried and why it failed.**

---

### Tasks
1. **Portfolio building.** Assemble a portfolio of ~100+ products from **at least 3 categories** (at least one IT category: laptops or monitors). Document which products you chose and why (sampling logic) and the data-quality issues you ran into.
2. **Data retrieval & matching.** Match the portfolio against the sources. Handle model/GTIN matching, missing or variant codes, and assign **a data-confidence score to each product**. Your code must be **runnable and reproducible**.
3. **Methodology.** For at least **3 product categories**, define criteria + objective thresholds; justify **why you chose each source**.
4. **Classification.** Classify each product (e.g. *eco-friendly / not / insufficient data*) and report coverage & match statistics.
5. **Greenwashing governance.** Describe your approach to the chain of evidence, self-declared vs third-party verification, and avoiding overclaiming.
6. **Phasing.** How would you handle categories with no available data; which category should an MVP start with, and why?
7. **Client email.** A one-page summary to Teknosa explaining your approach and its **limitations honestly**.

### Deliverables
- Runnable **code** (notebook/script) + brief run instructions
- The **portfolio** you collected (CSV, a dated snapshot)
- **Classification output** (CSV)
- A 2–3 page **methodology note**
- **Decision log**: assumptions & trade-offs + "what I would do with more time"
- **Client email**
- **AI-usage note**: which tool, at which step, how you used it

### Evaluation (summary)
We will look at: problem structuring · portfolio collection & data quality · data & matching quality (code, reproducibility) · how you handle real coverage gaps · methodological rigor · ESG/greenwashing judgment · depth of reasoning (decision log) · communication · quality of AI orchestration.

> Hint: The model code on a retailer's site often differs from the code in certification databases, and not every product will exist in every source. **How you handle the ones you cannot find** matters as much as the ones you can. Likewise, not every EPD is equally comparable or equally verified. Think about what makes two footprints comparable before you rank products on them.
