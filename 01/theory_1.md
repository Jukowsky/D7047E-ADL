# Task 1.1 Ethics

First, we used ChatGPT model GPT-4 to generate sentences involving various professions. We then translated these sentences from a neutral language (English) into languages with grammatical gender (e.g., Spanish and French) to observe if stereotypes emerged based on the profession.

## Observations

Below are the generated sentences along with gender identifications and professions:

### Spanish Sentences

- **El científico está trabajando en un nuevo experimento.**  
  _Male_ (scientist / **científico**)

- **El maestro explica la lección con mucha paciencia.**  
  _Male_ (teacher / **maestro**)

- **El médico revisó a su paciente y le recetó un medicamento.**  
  _Male_ (doctor / **médico**)

- **El director tomó una decisión importante para la empresa.**  
  _Male_ (director / **director**)

- **El ingeniero diseñó un puente resistente y seguro.**  
  _Male_ (engineer / **ingeniero**)

- **La actriz ganó un premio por su increíble actuación.**  
  _Female_ (actress / **actriz**)

### French Sentences

- **Le scientifique travaille sur une nouvelle expérience.**  
  _Male_ (scientist / **scientifique**)

- **Le maître explique la leçon avec beaucoup de patience.**  
  _Male_ (teacher / **maître**)

- **Le médecin a examiné son patient et lui a prescrit un médicament.**  
  _Male_ (doctor / **médecin**)

- **Le directeur a pris une décision importante pour l’entreprise.**  
  _Male_ (director / **directeur**)

- **L’ingénieur a conçu un pont solide et sécurisé.**  
  _Male_ (engineer / **ingénieur**)

- **L’actrice a gagné un prix pour son incroyable performance.**  
  _Female_ (actress / **actrice**)

## Conclusion

The translations defaulted to masculine forms for roles like scientist, teacher, doctor, engineer, and director, and only used a feminine form for the profession "actress." This demonstrates how LLMs, even when neutral in English, can replicate or reinforce gender stereotypes in gendered languages.

## Task 1.2 Metrics
## Confusion Matrix Values

- **True Negatives (TN)**: 990  
- **False Positives (FP)**: 10  
- **False Negatives (FN)**: 20  
- **True Positives (TP)**: 30  

---

## Evaluation Metrics

**Precision** = TP / (TP + FP) = 30 / (30 + 10) = **0.75**  
*Of all the predicted positives, how many were actually positive?*

**Recall** = TP / (TP + FN) = 30 / (30 + 20) = **0.60**  
*Of all the actual positives, how many did we correctly predict?*

**Accuracy** = (TP + TN) / (TP + TN + FP + FN) = (30 + 990) / (30 + 990 + 10 + 20) = **0.97**  
*Overall, how many predictions were correct?*

**F1 Score** = 2 × (Precision × Recall) / (Precision + Recall) = 2 × (0.75 × 0.60) / (0.75 + 0.60) = **0.67**  
*Harmonic mean of Precision and Recall*



