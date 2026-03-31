# Rhode Instagram Engagement Analysis

**Course:** Analytics for Unstructured Data — MSBA Fall 2025
**Team:** Carol Le, Niladri Nath, Gabriel, Kinshuk, Radha Pawar, Vyshnavi Maringanti
**Brand:** [Rhode (@rhode)](https://www.instagram.com/rhode/) — Hailey Bieber's clean beauty brand

---

Rhode has a genuinely strong visual brand and a highly engaged Instagram following. But when you look at their content calendar from the outside, the strategy is a mix of things that clearly work (close-up beauty shots, editorial content) and things that persist even though the engagement data doesn't support them (product flat-lays, standalone pack shots).

We came at this as analytics consultants asking: **can you predict whether a post will do well before you post it?** Not just describe what worked in the past — actually build a model that takes a new piece of content and tells you which way it's going to go.

## Data collection

Scraped ~500 Rhode posts via the Instagram Graph API: image URLs, captions, like counts, timestamps. Binary engagement label using median like count as the split — posts above median are high-engagement (1), below are low-engagement (0). Balanced problem, cleaner than predicting raw counts.

## Getting features out of images

The most important information is in the images themselves — and images aren't naturally structured for a classifier.

We used the **Google Cloud Vision API** to run label detection on every post image. Vision API returns object labels with confidence scores (e.g., `"lip": 0.94`, `"skin": 0.87`). Those labels become binary features — presence/absence across the full vocabulary — which a logistic regression can learn from.

This approach lets the model discover what visual content correlates with engagement without us having to manually define aesthetic categories upfront. We didn't tell it "close-up beauty shots do well." It found that on its own.

For captions: TF-IDF vectorization plus handcrafted features — caption length, emoji count, hashtag presence, call-to-action presence, TextBlob sentiment polarity.

## Models and results

| Model | Accuracy | Precision | Recall |
|---|---|---|---|
| Image labels only | ~67% | ~65% | ~68% |
| Captions only | ~62% | ~60% | ~64% |
| Combined | ~71% | ~69% | ~72% |

The combined model beats both individual models — visual and text signals are capturing different things and both matter. Visual is the stronger signal, which makes sense for a beauty brand.

## What the topic modeling found

We ran LDA (k=5) on Vision API labels and compared topic distributions between top-quartile and bottom-quartile posts.

Close-up skin and lip content dominated the top-quartile: posts with "lip", "skin", "close-up", "human body" labels consistently overperformed. Product flat-lays — posts where "product", "glass", "surface", "reflection" dominated — were consistently in the bottom half.

The uncomfortable implication: the most common type of beauty brand content on Instagram is the worst-performing content type for Rhode's specific audience.

## Recommendations

**1. Pull back on product-only flat-lays.** If you need to feature a product, put it on someone's face or in their hand — not isolated on a marble surface.

**2. Caption length sweet spot is 50–150 characters.** Caption walls killed engagement. The best-performing captions were short, direct, sometimes just a sentence or a question.

**3. More close-up texture shots.** The Vision API data is unambiguous — skin texture and lip close-ups drive Rhode's highest-engagement posts consistently.

## Stack

Google Cloud Vision API, Python, Pandas, scikit-learn (logistic regression, TF-IDF), Gensim (LDA), TextBlob, Matplotlib, Seaborn, Jupyter.

## Files

- `Rhode_Instagram_Analysis.ipynb` — full pipeline from scraping to recommendations
- `data/` — scraped post data and Vision API outputs
- `models/` — trained classifiers
