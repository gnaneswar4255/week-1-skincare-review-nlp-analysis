# Dataset Source Comparison — Skincare Review Analysis

**Prepared for:** Week 2, Data Identification, Sourcing Strategy & Initial Analysis Planning  
**Project:** Review-Informed Skincare Product Discovery Using NLP and Data Analytics  
**Status:** Desk research only; no dataset has yet been downloaded or analysed for this project.

## 1. Candidate sources

### Source A — Amazon Reviews'23, All_Beauty category

- Overview: https://amazon-reviews-2023.github.io/main.html
- Dataset card: https://huggingface.co/datasets/McAuley-Lab/Amazon-Reviews-2023
- Publisher page: https://mcauleylab.ucsd.edu/public_datasets/amazon_demo/

**Published source statistics:** The dataset documentation reports about 701.5K ratings/reviews, 112.6K items and 632.0K users for `All_Beauty`. The overall Amazon Reviews'23 collection is much larger: 571.54 million reviews across 33 categories, with interactions spanning May 1996 to September 2023.

**Strengths**
- Includes review text and ratings, with item metadata available.
- Has a documented beauty category and enough volume to support sampling.
- Useful for EDA, review-theme exploration, and possible text analysis.

**Limitations / checks**
- `All_Beauty` is broader than skincare and may include makeup, haircare, fragrance, and other beauty products.
- Dataset size is large; use a documented subset and inspect actual files/fields.
- Some products may lack metadata.
- The current licence/terms and permitted redistribution must be verified before use; do not assume availability means unrestricted reuse.
- Platform, language, reviewer self-selection, and time-period biases may limit generalization.

**Fit:** Best current candidate, conditional on metadata review and terms-of-use verification.

### Source B — Amazon Reviews (2018/older category data)

- Dataset page: https://cseweb.ucsd.edu/~jmcauley/datasets/amazon_v2/

**Strengths**
- Well-documented historical review data, including text, ratings, timestamps, and product metadata in category-specific files.
- May be useful if a smaller historical subset better fits the computing environment.

**Limitations**
- Older collection ending in October 2018, so it is less recent than the 2023 collection.
- Category files can still be large.
- Older field definitions and terms must be reviewed separately.
- Beauty category is not automatically synonymous with skincare.

**Fit:** Backup source if a suitable, manageable category subset is available and terms are acceptable.

### Source C — A mentor-approved or clearly licensed skincare-specific dataset

**Search route:** Kaggle or another data repository may host skincare product reviews, but individual dataset quality, licence, provenance, and freshness vary. No specific Kaggle dataset is recommended here until its exact page and terms have been inspected.

**Strengths**
- May be smaller and easier to work with.
- Could contain cleaner product categories that map directly to skincare.

**Limitations**
- Some uploads do not document original collection methods or provide a clear licence.
- Fields may be missing, synthetic, scraped without clear permission, or too narrow for comparisons.
- A dataset title alone is not evidence of authenticity or suitability.

**Fit:** Potentially useful if provenance, actual schema, licence, and sample data can be verified.

## 2. Comparison matrix

| Criterion | Amazon Reviews'23 All_Beauty | Amazon Reviews 2018/older | Unverified skincare-specific upload |
|---|---|---|---|
| Review text and ratings | Documented at collection level; inspect selected files | Documented in legacy schema; inspect chosen file | Unknown until checked |
| Product metadata | Available; some items may lack metadata | Available in separate metadata files | Varies |
| Skincare specificity | Medium: broad beauty category requires filtering | Medium: broad category requires filtering | Potentially high, but unverified |
| Volume | Very large; published All_Beauty stats ~701.5K ratings/reviews | Large; category subset required | Varies |
| Ease for beginner | Medium-low for full data; manageable with sampling | Medium-low | Could be high if compact and well-structured |
| Recency | Collected through Sep 2023 | Older, through Oct 2018 | Unknown |
| Licence / reuse | Must verify current terms and use conditions | Must verify source terms | Must verify; do not assume |
| Current recommendation | Preferred candidate pending checks | Backup | Consider only after verification |

## 3. Recommended sourcing decision

Start with Amazon Reviews'23 `All_Beauty`, but do not immediately download the full category. First:

1. Read the dataset documentation and check the current terms and attribution requirements.
2. Inspect the available item metadata schema and review schema.
3. Confirm whether category/product titles allow a defensible skincare subset to be created.
4. Download or load a small sample for a schema and data-quality check.
5. Record the sample method, row count, fields, date coverage, missingness, and duplicates.
6. Keep raw data unchanged; create a separate cleaned working dataset.
7. Do not commit raw reviews to a public GitHub repository unless redistribution is explicitly permitted.

If the metadata does not support reliable skincare identification, ask the mentor to approve a more targeted dataset rather than forcing an uncertain category filter.

## 4. Proposed minimum fields

| Field | Why needed | Required? |
|---|---|---|
| Product identifier | link reviews to product metadata | strongly preferred |
| Product title/name | interpret product and filter category | strongly preferred |
| Product category/metadata | define skincare subset | strongly preferred |
| Review text | topic and sentiment exploration | required |
| Rating | compare feedback with rating groups | required |
| Review timestamp/date | time coverage, if available | optional |
| Verified purchase flag | optional context only | optional |
| Price | optional product context | optional |

Reviewer names, account IDs, and other personal identifiers are not needed for the initial research question and should not be included in the analysis dataset unless there is a justified requirement.

## 5. Data-quality checks after access

- Record number of rows and columns.
- Inspect data types and missingness for every required field.
- Check rating values and review-text length.
- Count duplicate review IDs and exact/near-duplicate text.
- Inspect product/category coverage and examples from each included category.
- Check review language and date range.
- Compare raw and cleaned row counts and document every exclusion.
- Verify that the sample is not dominated by only a few products.

## 6. References

- McAuley Lab. *Amazon Reviews'23 overview*: https://amazon-reviews-2023.github.io/main.html
- McAuley-Lab. *Amazon-Reviews-2023 dataset card*: https://huggingface.co/datasets/McAuley-Lab/Amazon-Reviews-2023
- McAuley Lab. *Amazon Product Reviews*: https://mcauleylab.ucsd.edu/public_datasets/amazon_demo/
- McAuley Lab. *Amazon Reviews 2018 dataset*: https://cseweb.ucsd.edu/~jmcauley/datasets/amazon_v2/
