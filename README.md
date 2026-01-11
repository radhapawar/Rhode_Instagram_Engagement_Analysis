# Rhode Instagram Engagement Analysis
Predicting high vs. low Instagram engagement using image-derived labels and caption text, and extracting content themes that correlate with engagement.

**Course:** Analytics for Unstructured Data (MSBA F2025)  
**Project Type:** Group Project (Alternative 1 — Brand / Instagram) :contentReference[oaicite:1]{index=1}  
**Brand:** Rhode — https://www.instagram.com/rhode/

## Contributors
- Carol Le
- Niladri Nath
- Gabriel Kinshuk
- Radha Pawar
- Vyshnavi Maringanti

---

## Project Objective
We act as analytics consultants to Rhode with the objective of **increasing Instagram engagement**.  
Objective:
1. Scrape ~500 posts (image URLs, captions, likes) :contentReference[oaicite:2]{index=2}  
2. Generate **image labels** using Google Vision API :contentReference[oaicite:3]{index=3}  
3. Create a binary engagement label (high/low) based on median likes :contentReference[oaicite:4]{index=4}  
4. Train logistic regression classifiers to predict engagement using:
   - image labels only
   - captions only
   - combined labels + captions :contentReference[oaicite:5]{index=5}  
5. Run LDA topic modeling on image labels and compare topic mixes between top vs. bottom engagement quartiles :contentReference[oaicite:6]{index=6}  
6. Provide strategy recommendations to improve engagement:contentReference[oaicite:7]{index=7}  

---
