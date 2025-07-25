From the paper: [LLMs for CSS](https://aclanthology.org/2024.cl-1.8.pdf)

| Effective Prompt Guideline                                                                                                                                                                                                  | Reference               | Guideline Example                                                                                                                                    |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| When the answer is categorical, enumerate options as alphabetical mltiple-choice so that the output is simply the highest-probability token ('A', 'B').                                                                     | Hendrycks et al. (2021) | {\$CONTEXT}<br><br>Which of the following describes the above news headline?<br>A: Misinformation<br>B: Trustworthy<br><br>{\$CONSTRAINT}            |
| Each option should be separated by a new line to resemble the natural format of online multiple choice questions. More natural prompts will elicit more regular behaviour.                                                  | Inverse Scaling Prize   | see above.                                                                                                                                           |
| To promote instruction-following, give instructions after the context is provided; then explicitly state and constraints. Recent and repeated text has a greater effect on LLM generations due to common attention patterns | Child et al. (2019)     | {\$CONTEXT}<br>{\$QUESTION}<br><br>Constraint: Even if you are uncertain, you **must pick either "True", or "False"** without using any other words. |
| Clarify the expected output in the case of uncertainty. Uncertain models may use default phrases like "I don't know," and clarifying contraints force the model to answer.                                                  | No reference            | see above.                                                                                                                                           |
| When the answer should contain multiple pieces of information, request responses in JSON format. This leverages LLM's familiarity with code to provide an output structure that is more easily parsed                       | MiniChain Library       | {\$CONTEXT}<br>{\$QUESTION}<br><br>JSON Output:                                                                                                      |
MiniChain is a library for LLM augmented programming. [A paper by the same name](https://aclanthology.org/2023.emnlp-demo.27.pdf) exists from the 2023 Conference on Empirical Methods in NLP: System Demos. Both the paper and the library's documentation do not mention JSON as an effective prompting method from what I could find. 

From the [Prompt Report](https://arxiv.org/pdf/2406.06608)
> Styling Formatting the LLM’s response using XML or JSON styling has also been shown to improve the accuracy of the judgment generated by the evaluator ([Hada et al., 2024](https://aclanthology.org/2024.findings-eacl.71/); [Lin and Chen, 2023](https://arxiv.org/abs/2305.13711); [Dubois et al., 2023](https://proceedings.neurips.cc/paper_files/paper/2023/hash/5fc47800ee5b30b8777fdd30abcaaf3b-Abstract-Conference.html)).

According to this report the above papers claim that enforcing JSON/XML styling improves accuracy in LLMs. 


#### Are Large Language Model-based Evaluators the Solution to Scaling Up Multilingual Evaluation? (Hada et al., 2024)
Claims that adding styling and formatting in the form of a JSON schema helped combat errors in formatting in the output. No metrics as to how much this improved the output. 
- *Does this improve accuracy like the survey stated? Or does it just make it easier to parse.*

#### LLM-Eval: Unified Multi-Dimensional Automatic Evaluation for Open-Domain Conversations with Large Language Models
Has an LLM review a response to a conversation, since it asks for scores across Appropriateness, Content, Grammar, and Relevance it gives these metrics as a JSON template in the prompt.  No reason expressed as to why JSON was used explicitly but seems obvious given the nature of the output.

#### AlpacaFarm (Dubois et al., 2023)
Used JSON output as a 'trick' to force ChatGPT to give a preference in a pairwise preference simulation. 
- *I don't think this adds to the claim that formatting an LLMs response to JSON improves accuracy. Does this not just improve accuracy based on 50/50 chance of selecting the response that most aligns with humans?*


