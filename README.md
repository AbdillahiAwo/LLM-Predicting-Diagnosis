# LLM-Predicting-Diagnosis

This project evaluates the diagnostic accuracy of a LLM in predicting the correct final medical diagnoses from selected House M.D. episodes. The evaluation was performed using two scoring methods: Strict Accuracy (exact matches only) and Lenient Accuracy (partial credit for correct categories or closely related diagnoses). By combining transcript data with LLM-generated predictions, the project investigates how close LLMs can come to making accurate medical diagnoses in a realistic, case-based setting.

### Dataset

* Source: House M.D.
* Focus: Dialogue from the medical team (House, Wilson, Foreman, Cameron, Chase, Cuddy)
* What Did I Evaluate: 8 cases (1 per season)
* Evalution Target: Final confirmed diagnosis for each case

<img width="816" height="202" alt="Screenshot 2025-08-08 at 7 54 55 PM" src="https://github.com/user-attachments/assets/fd65dc8e-25bc-4efc-b44a-4e14fe76a63c" />
 


#### Evaluation Metrics

1. Strict Accuracy:
  * Definition: The percentage of predictions that exactly match the correct final diagnosis.
  * Formula: Strict Accuracy = Correct Match / Amount of cases x 100 
  * Results: 2/8 cases correct 25%
  * Visulization: Each of the 1's represent a correct diagnosis while the 0's represent false diagnosis

<img width="709" height="639" alt="download" src="https://github.com/user-attachments/assets/b28f5c5e-0b59-4958-ad8f-9dab2efb42b6" />

2. Lenient Accuracy:
  * Definition: Gives partial credit if:
    * The predicted diagnosis is in the correct category (e.g., “Cancer” vs. “Lymphoma”)
    * OR the semantic similarity between predicted and true diagnosis ≥ 0.75
  * Formula: Strict Accuracy = Partially Correct Match / Amount of cases x 100 
  * Results: 3/8 cases correct 37.5%
  * Visulization:

<img width="489" height="290" alt="download-1" src="https://github.com/user-attachments/assets/57aee203-7370-40f5-b564-b763710206bd" />


### Strict V. Lenient Accuracy and Why Both Matter
Using both metrics gives a fuller understanding of LLM performance:
* Strict Accuracy: Measures diagnostic precision.
* Lenient Accuracy: Measures clinical usefulness when the LLM is “close enough” to still guide treatment.

This evaluation approach follows the recommendations in Evaluation and mitigation of the limitations of large language models in clinical decision-making (2024), which highlights that category-level scoring and semantic similarity checks can better reflect real-world medical utility.



### Conclusions

* The 12.5% gap between the two metrics shows that while exact matches are limited, the LLM frequently predicted the correct diagnostic domain, which still has clinical relevance.

### Future Work

* Evaluate more cases to improve statistical robustness.
* Incorporate Top-k accuracy to credit correct answers within the model’s top few guesses.
* Use retrieval-augmented generation (RAG) to improve grounding and reduce hallucinations.


## Citations

* [Evaluation and mitigation of the limitations of large language models in clinical decision-making (2024)](https://www.nature.com/articles/s44387-025-00011-z) 
* [Liu et al. (2023) — Automated disease diagnosis evaluation metrics in AI-based systems](https://www.nature.com/articles/s41591-024-03097-1) 
* https://arxiv.org/html/2409.00097v3
