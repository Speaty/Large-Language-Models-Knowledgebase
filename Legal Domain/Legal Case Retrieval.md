
# LCR Problem
original paper: [Legal Case Retrieval: A Survey of the State of the Art](https://aclanthology.org/2024.acl-long.350/) (ACL Long 2024)

Traditionally LCR tasks have been treated as a standard information retrieval (IR) problem. Finding relevant cases to a query case often requires knowledge external to the query to determine case relevance. Because of this, the authors hope to bring awareness of the LCR problem to the NLP community.

## Modelling Challenges and Issues
As defined by the survey paper above, the first 4 concern accuracy, the fifth efficiency, and the last two user experience. 

1) **Identify the relevant portions of a case:** What matters most are *case elements* (e.g. type of theft in a theft case, number of thieves, items stolen, value of stolen items). Disregarding irrelevant or misleading information is the challenge.
2) **Exploiting legal knowledge:** Legal knowledge is often needed to determine case similarity (e.g. a theft over a certain value my be considered grand theft and not relevant to a petty theft case).
3) **Processing complex cases:** Complex cases could be longer than a typical SoA PLM could handle. Events in a complex case have important causal relationships and do not necessarily occur in chronological/temporal order in the text. See [[Long Document Comprehension]] (LDC) 
4) **Modelling time:** Statutes may change with time (e.g. abolition of the death penalty). 
5) **Ensuring efficiency:** Legal texts are typically much longer than texts in other domains and therefore some efficiency is required.
6) **Enabling interpretability:** An LCR model should not only give a judgement as to whether or not two cases are similar but should also generate text describing the complex logical reasoning steps used to generate its response. Interpretive/[[Explainable AI]] is an active and challenging area of research.
7) **Enabling interactivity:** Laymen often struggle to provide a professional description of a query case leading to poor retrieval results and user frustration. 

## Corpora

### Datasets
| Name           | Language | Jurisdiction | # of queries | # of candidate cases/queries | # of relevant cases/queries |
| -------------- | -------- | ------------ | ------------ | ---------------------------- | --------------------------- |
| FIRE-IRLeD2017 | English  | India        | 200          | 2000                         | 5                           |
| COLIEE 2021    | English  | Canada       | 900          | 4415                         | 4.73                        |
| COLIEE 2022    | English  | Canada       | 1198         | 2963                         | 4.56                        |
| COLIE 2023     | English  | Canada       | 1278         | 3635                         | 4.18                        |
| CAIL2019-SCM   | Chinese  | China        | 8964         | 2                            | 1                           |
| LeCaRD         | Chinese  | China        | 107          | 100                          | 10.33                       |
### Dataset Construction
- **Common law justifications:** Typically only similar if one case cites the other.
	  COLIEE2021-2023 - All query cases and their corresponding precedent cases are provided as a candidate case pool for retrieval. 
	  FIRE-IRLeD2017 - Unlike COLIEE only the precedent cases along with 1000 randomly chosen cases that are not cited by query cases are provided as a candidate pool.
- **Civil law jurisdictions:** Relevance labels have to be provided by legal experts. (CAIL2019-SCM & LeCaRD)

### Dataset Limitations
- **Annotation bias:** Inconsistent practices have been employed in interpretations and citations get affected by subjective interpretations. It is not uncommon for judges to be biased when citing cases. Models trained on these biased annotations could make biased predictions.
- **Reproducibility issues:** CAIL2019-SCM & LeCaRD are annotated by multiple legal experts but the annotation guidelines are not published. For LeCaRD inter-annotator agreement is not even reported. 
- **Lack of time awareness:**
- **Lack of datasets with laymen-readable explanations:**

# TODO:
- review SOTA models
- review datasets themselves
	- What makes a case relevant to another?
	- If there is more than one type of relevance, can they be enumerated? 