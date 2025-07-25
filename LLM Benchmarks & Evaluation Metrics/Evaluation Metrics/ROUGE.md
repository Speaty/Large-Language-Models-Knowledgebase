Original paper: [ROUGE: A Package for Automatic Evaluation of Summaries](https://aclanthology.org/W04-1013.pdf)
# Recall-Oriented Understudy for Gisting Evaluation
Metric to compare automatically generated text with a reference text based on [[BLEU]]. 

## ROUGE-N (N-gram Overlap)
- Measures the overlap of n-grams between candidate and reference summaries. N refers to the sequence length. $$ \text{ROUGE-N} = \frac{\text{Number of overlapping n-grams}}{\text{Total n-grams in the reference summary}} $$
## ROUGE-L (Longest Common Subsequence -LCS)
- Focuses on the longest common subsequence between the candidate and reference summaries. 
- Takes into account sentence structure and word order.
- Reflects precision, recall, and F1 measures.

## ROUGE-W (Weighted LCS)
- A weighted version of ROUGE-L that assigns higher importance to longer contiguous matches in the LCS.

## ROUGE-S (Skip-Bigram with Co-occurrence)
- Measures skip-bigram overlap, where skip-bigrams are pairs of words in the candidate and reference that maintain the same order but may have gaps in between.
- Captures non-contiguous word matches.

## ROUGE-SU (Skip-Bigram with Unigram)
- An extension of ROUGE-S that includes unigram matches along with skip-bigrams

## ROUGE-K (Keywords)
Original paper: [ROUGE-K: Do Your Summaries Have Keywords](https://aclanthology.org/2024.starsem-1.6/) \*SEM 2024

**Key Takeaways:**
- ROUGE-K is a metric based on ROUGE which takes only keywords into account. Which measures how well a candidate summary recalls predefined keywords.$$
  \text{ROUGE-K} = \frac{\text{Count}(\text{keywords } \cap \text{ n-grams})}{\text{Count(keywords)}} 
   $$


**Novel Ideas:**
- 4 proposed interventions to guide models for better keyword inclusion.

**Methods:**
- Keywords are generated by extracting n-grams, removing stop words, and comparing n-grams from multiple references or the corresponding title where there is only one reference text. This seems to be significantly more effective than TF-IDF and TextRank.
- Evaluations performed on:
	- **XSum:** News summarisation dataset
	- **SciTLDR & ScisummNet:** Scientific document summarisation datasets
- Human Judgement analysis
- Model Interventions: To improve keyword inclusion, four strategies were developed:
	- **Re-weighted Encoding (RwEnc)**
		- Adjusts attention layer in encoder to include TF-IDF scores
	- **Re-weighted Generation (RwGen)**
	- **Multi-task Learning with TF-IDF (TDMTL)**
	- **TF-IDF-guided Decoder (TDSum)**
- **Model Evaluation and Metrics:** Models BART, GSum, MTL, PreSumm were evaluated for traditional ROUGE Scores and ROUGE-K
- 
**Potential Cheats:**
- 
**Usefulness to me:**
- JSON task -> it will be interesting to see how this metric compares to others on JSON vs NL task performances in summarisation
- Multiagents -> summarisation is a key task in multiagent architectures 
- RAG -> the keyword generation might be useful elsewhere for retrieval of legal documents, I imagine legal keywords are significant and are repeated across legal texts quite frequently
**Fall out questions:**
- What is TextRank for keyword extraction?
- Come back to the results and analyse with model knowledge