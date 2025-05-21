[TruthfulQA: Measuring How Models Mimic Human Falsehoods](https://arxiv.org/abs/2109.07958)

Claims to measure an LLMs truthfulness in generating answers to questions. Questions contain many common misbeliefs which are found in training data. 

**Task 1** - Generation of full-sentence answer given a prompt and question.
**Task 2** - Multiple-choice variation of the first task.

## Metrics
- Human Evaluation for task 1 measuring truthfulness and informativeness 
	- Truth score is a qualitative label including 'mostly true', 'mixed true/false' etc (13 labels total)
	- >= 0.5 is considered truthful.
	- Same process for informativeness.


## Original Paper Results
More training data does not necessarily improve performance due to the propagation of these misconceptions. 

Larger models were found to be less truthful but more informative, the inverse was observed in smaller QA finetuned model (UnifiedQA).

## Stats
- 817 Questions
- 38 Categories; inc. Health, Law, Finance, & Politics
- 94% Human Baseline
	- Human 'participant' answered 250 randomly sampled questions with a suggested time of 2 minutes per question and access to the internet. 



