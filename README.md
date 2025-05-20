# 🤖 FAQ Smart Assistant

This project is a simple FAQ-based smart assistant built using Python. It allows users to ask questions in natural language and returns the most relevant answer based on a predefined list of Frequently Asked Questions (FAQs).

---

## 📌 Features

- Matches user queries with stored FAQs using **TF-IDF vectorization** and **cosine similarity**
- Returns the most appropriate answer even when the wording differs
- Handles unmatched queries gracefully with a fallback message

---

## 🛠️ Tech Stack

- **Python 3**
- **scikit-learn** – for TF-IDF and similarity computation

---

## 📁 FAQ Knowledge Base

The FAQ data is stored in a dictionary named `faq_data`. Example entries:

```python
faq_data = {
    "Do you offer delivery?": "Yes, we provide delivery service for all orders above 500 BDT.",
    "Where are you located?": "We are located at 123 Main Road, Dhaka.",
    "Can I return a product?": "You can return a product within 7 days of delivery.",
    ...
}
## ⚙️ How It Works
TF-IDF Vectorization: Converts FAQ questions and user query into numerical vectors.

Cosine Similarity: Measures how similar the user query is to each stored FAQ.

Best Match Detection: Finds the most similar question and returns the corresponding answer.

Threshold Filtering: If similarity score is too low (below 0.4), the assistant returns a default message.

##🧪 Sample Usage

print(get_faq_answer("Do you offer delivery?"))
# Output: Yes, we provide delivery service for all orders above 500 BDT.

print(get_faq_answer("Where are you located?"))
# Output: We are located at 123 Main Road, Dhaka.

print(get_faq_answer("Can I return a product?"))
# Output: You can return a product within 7 days of delivery.

print(get_faq_answer("Do you sell mobile phones?"))
# Output: Sorry, I couldn’t find a suitable answer to your question.
## 🧾 Code Explanation

from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.metrics.pairwise import cosine_similarity
Imports TF-IDF and similarity tools from scikit-learn.

faq_data = { ... }
Dictionary mapping FAQ questions to answers.

def get_faq_answer(user_query: str) -> str:
Main function to handle user queries.

    vectorizer = TfidfVectorizer()
    tfidf_matrix = vectorizer.fit_transform(questions + [user_query])
Converts questions and query into TF-IDF vectors.

    similarity_scores = cosine_similarity(tfidf_matrix[-1], tfidf_matrix[:-1])
Computes cosine similarity between the query and each FAQ.

    if best_match_score >= 0.4:
        return faq_data[matched_question]
    else:
        return "Sorry, I couldn’t find a suitable answer to your question."
If similarity is above threshold, return matched answer. Otherwise, show default message.

## ✅ Requirements
Install required libraries using pip:

bash
pip install scikit-learn
## 🚀 How to Run
Clone this repo

Install dependencies

Run the script with your own queries

## 📬 License
This project is open source and available under the MIT License.

Let me know if you'd like the `LICENSE` file or GitHub repo structure suggestion
