# TakeMeter Planning Document

## Community

For this project, I chose Reddit computer science career communities:

* r/cscareerquestions
* r/csMajors
* r/ITCareerQuestions

These communities contain a mix of high-quality career advice, emotional reactions to the job market, and unrelated discussions. This makes them a good fit for a discourse-quality classification task because there are meaningful distinctions between useful guidance, unsupported opinions, and off-topic content.

---

## Labels

### helpful_advice

Posts that provide actionable, constructive, and specific career guidance.

Examples:

* "Tailor your resume to every application."
* "Practice LeetCode consistently and focus on weak topics."

### low_quality_opinion

Posts that express unsupported pessimistic opinions, doomposting, or exaggerated claims without useful guidance.

Examples:

* "CS is dead."
* "Nobody gets hired anymore."

### off_topic

Posts unrelated to computer science careers, internships, job searching, or professional development.

Examples:

* "What's your favorite movie?"
* "What music are you listening to lately?"

---

## Hard Edge Cases

Some posts contain both advice and opinion.

Example:

> "Nobody is hiring right now, but keep building projects and applying."

Possible labels:

* helpful_advice
* low_quality_opinion

Decision rule:

If a post contains actionable guidance that a reader can follow, it will be labeled as helpful_advice even if it contains negative opinions.

Another difficult example:

> "AI is replacing engineers, so learn AI tools."

Decision:

This was labeled as helpful_advice because the post includes a specific recommendation.

---

## Data Collection Plan

Data was collected from:

* Reddit r/cscareerquestions
* Reddit r/csMajors
* Reddit r/ITCareerQuestions

Target distribution:

* helpful_advice: 70 examples
* low_quality_opinion: 70 examples
* off_topic: 60 examples

Actual distribution:

| Label               | Count |
| ------------------- | ----: |
| helpful_advice      |    75 |
| low_quality_opinion |    70 |
| off_topic           |    55 |

Total examples collected: 201

If any label became significantly underrepresented, additional examples would be collected from the same communities until a more balanced distribution was achieved.

---

## Evaluation Metrics

The following metrics will be used:

* Accuracy
* Precision
* Recall
* F1 Score
* Confusion Matrix

Accuracy measures overall performance, but it does not show whether the model performs well on each class individually.

Precision, recall, and F1 score provide class-level performance information, while the confusion matrix helps identify which labels are most frequently confused.

---

## Definition of Success

A successful model should:

* Achieve at least 60% accuracy on the test set
* Correctly identify most helpful_advice examples
* Maintain reasonable precision and recall across all classes
* Demonstrate meaningful learning beyond random guessing

The classifier would be useful if it could reliably surface constructive career advice while filtering low-quality discussion.

---

## AI Tool Plan

### Label Stress Testing

ChatGPT was used to generate borderline examples between helpful_advice and low_quality_opinion. These examples helped refine the label definitions before annotation.

### Annotation Assistance

AI was used to suggest example posts and labeling ideas. Every final label was reviewed manually before inclusion in the dataset.

### Failure Analysis

After evaluation, AI was used to identify recurring patterns among incorrect predictions. These observations were verified against actual model outputs before being included in the report.

---

## Difficult Annotation Examples

### Example 1

Text:

> "Nobody is hiring right now, but keep applying."

Label:

helpful_advice

Reason:

The post contains actionable guidance despite the negative framing.

---

### Example 2

Text:

> "AI is replacing engineers, learn AI tools."

Label:

helpful_advice

Reason:

The recommendation is actionable and useful even though it contains a pessimistic claim.

---

### Example 3

Text:

> "Technical interviews are pointless."

Label:

low_quality_opinion

Reason:

The statement is a negative opinion that does not provide evidence or actionable guidance.

---

## Success Criteria

The project will be considered successful if:

1. The fine-tuning pipeline runs successfully.
2. The model achieves at least 60% test accuracy.
3. The model performs better than random guessing.
4. Failure cases can be analyzed and explained.
5. The evaluation reveals meaningful differences between fine-tuning and zero-shot classification.
