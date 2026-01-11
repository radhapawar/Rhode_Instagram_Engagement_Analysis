# Rhode Instagram Engagement Analysis
Predicting high vs. low Instagram engagement using image-derived labels and caption text, and extracting content themes that correlate with engagement.

**Course:** Analytics for Unstructured Data (MSBA F2025)  
**Project Type:** Group Project (Brand / Instagram)   
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
1. Scrape ~500 posts (image URLs, captions, likes)  
2. Generate **image labels** using Google Vision API
3. Create a binary engagement label (high/low) based on median likes   
4. Train logistic regression classifiers to predict engagement using:
   - image labels only
   - captions only
   - combined labels + captions  
5. Run LDA topic modeling on image labels and compare topic mixes between top vs. bottom engagement quartiles  
6. Provide strategy recommendations to improve engagement  

---
