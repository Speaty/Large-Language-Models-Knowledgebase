
# Investigating the logical reasoning capability of LLM Multi-agent systems
- Can collaborative multi-agent LLMs out perform their strongest member on logical reasoning tasks? Can we observe the 'Assembly Bonus Effect' in LLM agents?
- Investigating which mechanisms of multi-agent communication show the most promise for the reliability and transparency of logical reasoning.

## Introduction
### Logical Reasoning
In its most general from, logical reasoning can be defined as the process of drawing conclusions from premises using a set of rules or principles. This broad definition is inclusive of both formal and informal modes of reasoning, ranging from rigid logical inference to heuristic-based human cognition.

At the core of formal reasoning is deductive logic, particularly first-order logic (FOL). Deductive reasoning guarantees the truth of a conclusion if the premises are true and the rules of inference are correctly applied. Classic forms of deductive inference include modus ponens (if *p* implies *q*, and *p* is true, then *q* must be true) and modus tollens (if *p* implies *q* and *q* is false, then *p* must be false). Mathematics relies heavily on deductive reasoning, where theorems are proven from axioms through valid inference steps. 

In contrast, non-deductive reasoning includes forms such as inductive, abductive, and analogical reasoning. These do not guarantee their conclusions, but rather support them to varying degrees of plausibility. Inductive reasoning involves generalising from observations (e.g. inferring a law of nature from repeated patterns), while abductive reasoning infers the most likely explaination for an observation (as in medical diagnosis). Analogical reasoning draws parallels between similar domains, enabling inferences by comparison - such as extrapolating from animal models (e.g. the Zucker rat) to human biology (REFERENCE HERE). In this study, we similarly hypothesise that analogies between large language models (LLMs) and human reasoning may provide insight into shared cognitive dynamics. MAYBE MENTION CHOMSKY HERE on LLMs as a tool for linguists. MAY SPARK DEBATE WITH DAVID ALSO

Reasoning may also be non-monotonic, where conclusions are revisable in light of new information. This is an important aspect in dynamic or uncertain environments. Formal systems such as Boolean Satisfiability (SAT) and Satisfiability Modulo Theories (SMT) attempt to capture aspects of logical inference under these conditions. MAYBE REWRITE SOME OF THIS

Finally, arguments that fail to meet logical standards are classified as fallacies. For example, the fallacy of affirming the consequent (*q*; if *p* then *q*; therefore *p*) superficially resembles valid reasoning but lacks deductive soundness. 

(CITATION) defines logical reasoning as a process that involves "selecting and interpreting information from a given context, making connections, and verifying and drawing conclusions based on provided and interpreted information and the associated rules and processes." This functional definition is especially valuable when applied to the evaluation of artificial reasoning systems. It offers a practical set of cognitive operations - selecting, interpreting, connecting, and verifying - that serve as measurable dimensions for assessing reasoning performance across both formal and informal domains. However, operationalising these criteria presents substantial methodological challenges. Unlike symbolic logic systems, which are transparent and fully interpretable, both LLMs and the human brain function as black boxes, making it difficult to observe the internal mechanics of reasoning directly.  

The problem of measuring reasoning is not unique to artificial intelligence; it has long been a point on contention in cognitive psychology. Decades of research on human reasoning have revealed deep disagreements about how reasoning should be tested. Experimental conditions, task framing, prior knowledge, and the validity of test materials all significantly influence observed reasoning behaviour. These same criticisms apply, albeit to a lesser extent, to LLMs. Without carefully controlled inputs and clearly defined success criteria, it is easy to conflate surface-level fluency with genuine reasoning (CITE). Therefore, the challenge lies not only in designing reasoning tasks for AI systems, but also in interpreting their outputs within a meaningful theoretical and empirical framework, one that accounts for both the strengths and limitations of the systems under study. 

- What do we mean by [[logical reasoning]]?  
	- Logical reasoning is a form of thinking that is concerned with arriving at a conclusion in a rigorous way. 
	- deductive/first order logic - the premises ensure the conclusion. Follows a rule of inference. 
		- modus ponens - *P implies Q. P is true. Therefore, Q must also be true.*
		- modus tollens - *not Q; if P then Q; therefore not P*
		- In mathematics, deductive reasoning is used to prove theorems based on a set of premises usually called axioms. 
	- non-deductive - the premises make it more likely that the conclusion is true and strong inferences make it very likely:
		- abductive - Starts from an observation and reasons to the fact explaining it e.g. a doctor diagnosing a condition from symptoms.
		- inductive - Generalisation, inferring a universal law based on patterns found in observation e.g. "all ravens are black."
		- analogical - Comparing similar systems to infer that if one has a feature then the other must also. Often used to transfer insights from animal experiments to humans such as the [[Zucker Rats experiment]]. To some extent, the hypothesis of this experiment aims to transfer insights from humans and LLMs unto one another. 
	- non-monotonic - A conclusion may have to be withdrawn upon learning new information.
		- Boolean Satisfiability problem (SAT) & Satisfiability modulo theories (SMT) - 
	- Arguments that do not meet the standard of logical reasoning are referred to as fallacies. 
		- affirming the consequent - *Q; if P then Q; therefore P* 
	- From "Logical Reasoning in Formal and Everday Reasoning Tasks" - *Selecting and interpreting information from a given context, making connections and verfying and drawing conclusions based on provided and interpreted informaion and the associated rules and processes.* The authors stress that this definition is inclusive of formal and informal strategies of reasoning
	- Arithmetic, commonsense, symbolic
## Motivation
### Logical Reasoning
Logical reasoning is widely recognised as a fundamental component of intelligent decision-making. In formal domains such as mathematics, deductive reasoning provides irrefutable proof. Meanwhile, non-deductive reasoning guides judgement and decision-making under uncertainty, enabling agents to make plausible inferences, generalise patterns, or identify causal explanations. Together, these reasoning forms underpin human cognition in scientific discovery, legal reasoning, and everyday problem-solving. Thus, the capacity to reason logically is not only central to human intelligence but also regarded as a prerequisite for more advanced systems approaching artificial general intelligence (AGI) (CITE DUENAS RUIZ 2024).

Yet, contemporary LLMs, despite their impressive generative and linguistic capabilities, present a challenge in this regard. These models are fundamentally probabilistic systems, trained to predict the next token based on statistical patterns in vast text corpora. As such, they do not "reason" in the way intelligent animals or humans do: their outputs are shaped by distributional patterns, not by a coherent internal process of inference. Although they often appear to produce reasoned responses, closer inspection reveals limitations in consistency, truth-preservation, and explanatory depth, particularly when tasks require explicit logical structure or epistemic confidence. 

This limitation becomes especially salient in domains where transparency, reliability, and interpretability are are essential. In applications such as scientific research, legal advising, or safety-critical decision-making, an illusion of reasoning is not enough, systems must offer not only correct conclusions but also justifications grounded in sound inferential processes.  If LLMs are to be deployed in these settings, it is critical to determine whether they are capable of genuine reasoning, and more importantly, whether such reasoning is observable, measurable, and reproducible. THIS PARA IS WEAK

As such, investigating the logical reasoning capabilities of LLMs, particularly under more structured and interactive conditions such as multi-agent environments, is a necessary step towards both understanding their current capacities and designing systems that can reason more transparently and effectively in the future. 

- Logical reasoning is a pillar of strong decision making, deductive reasoning leaves no doubt about mathematical proofs, and non-deductive reasoning provides guides critical thinking and minimises risk. 
- Language models are fundamentally probabilistic machines and cannot reason as intelligent animals reason. The process of reasoning goes beyond the token-by-token generative nature of auto-regressive LLMs
- While LLMs have impressive generative abilities, many domains desire transparency and confidence (as oppose to the illusion of confidence) before adopting LLMs. 
- If Language models are capable of reasoning, and the reasoning is observable... 
- Logical reasoning widely regarded as a prerequisite for more advanced AI systems approaching AGI (Duenas & Ruiz, 2024).
### why multi agent?
The motivation to study reasoning in multi-agent LLM systems specifically stems from longstanding findings in psychology and cognitive science that suggest reasoning can be socially distributed. Human reasoning, even in simple logical tasks, often improves in collaborative settings. One of the earliest formulation s of this view comes from Collins and Guetzkow (1964), who introduce the concept of the "assembly bonus effect", the idea that effective group interactions can produce outcomes that exceed what would be expected from the mere sum of individual contributions. In this view, reasoning is not solely an internal cognitive process but a social skill that unfolds in communication and coordination. 

Empirical support for this effect can be found in studies such as Moshman and Geil (1998),who demonstrated that groups performed significantly better than individuals on the Wason selection task, a well-known logical reasoning challenge. Their results suggest that collaborative reasoning, rather than imitation or peer pressure, allows groups to overcome individual biases and arrive at more valid conclusions. However, the robustness of the assembly bonus effect remains debated. Some studies support it, while others argue that group performance is often limited to the average ability of its members, or even suffers from process loss due to coordination costs, or conformity pressures (Propp, 2003). 

One key limitation across many of these studies is the lack of precise experimental control when comparing individuals and groups. In human experiments, variables such as communication quality, social dynamics, and prior knowledge are difficult to isolate. However, when working with language models, some of these variables become fully controllable. We can define roles, design communication protocols, and ensure symmetry across experimental conditions, ofering a good opportunity to rigorously test group-level reasoning under controlled circumstances. 

Moreover, multi-agent architectures allow researchers to investigate how communication strategies impact reasoning outcomes. If the assembly bonus effect is observed in LLMs, the question then becomes: what specific communication patterns or coordination mechanisms drive this improvement? HMM

A further benefit of the multi-agent setup is that dialogue itself becomes an observable window into reasoning. One of the challenges in evaluating single LLM outputs is the lack of transparency, although some models output intermediate reasoning steps, these do not necessarily reflect actual inferential processes, and may instead by artifacts of probabilistic sampling. In contrast, when multiple agents engage in dialogue, we can observe coordination and alignment over time - two hallmarks of successful joint reasoning. Coordination referes to the synchronisation of actions and expectations, much like dancers or coordinated physical tasks, while alignment refers to the establishment of shared representations at different linguistic and conceptual levels. Together, these offer concrete, analysable metrics for understanding how, rather than just whether, reasoning occurs in language-based systems. ALSO HMM...

In this context, mutli-agent LLM systems offer a promising testbed for investigating not only the presence of reasoning, but also the structure and dynamics of reasoning as it unfolds through structured, communicative interaction. 


- Assembly Bonus Effect
	- Some literature suggests reasoning to be a social skill. Collins and Guetzkow (1964) coin the 'assembly bonus effect' in which effective interaction is held to allow group members to combine their individual knowledge in a manner that produces higher quality outcomes than would have been attributable to a combination of individual members.
	- Moshman & Geil 1998 - observe that groups perform far better on Wason selection task than individuals due to collaborative reasoning rather than imitation or peer pressure.  
	- Many studies claim to support the 'assembly bonus effect' in humans, and many reject the claim representing a reductionist argument that assumes groups perform at best, only as well as the sum of its parts, and worst the group will create a process loss (Propp 2003). 
	- One flaw of all experiments trying to substantiate or refute this effect is the lack of experimental control between groups and individuals - this is not true of language models and can easily be controlled. 
	- Moreover, the question arises: What communication mechanisms/strategies are responsible in the diversity of results when attempting to observe the assembly bonus effect? and, what communication strategy best enables groups to converge on the correct answer in logical reasoning tasks?
- Dialogue is more observable than internal reasoning of LLMs
	- LLMs and RLMs provide little insight into how they 'think' or arrive at a given answer. Where reasoning models output their reasoning tokens, the tokens themselves don't seem to follow a chain of thought or logic, as a result the success of these models could be down to sampling as oppose to reasoning. 
	- From dialogue we can assert coordination and alignment between LLMs
		- coordination - interlocutors are coordinated in a successful dialogue as in any successful joint activity (dancing, lumberjacks using 2 handed saw etc)
		- alignment - occurs at a particular level when interlocutors have the same representation at that level. 



### Reasoning

#### Reasoning in Humans 


- Moshman & Geil
	- Carried out the Wason selection task on individuals and groups. 
	- Found that groups selected the correct response pattern 75% of the time in comparison to 9% of the time for individuals. 
	- Prior experiments concluded that group performance is typically within the range of individual performance (Gigone & Hastie, 1997) but 3 groups were comprised of individuals that selected incorrect solutions as individuals.
- Socratic Discussion/Dialogue/Questioning - A disciplined method of inquiry that uses open-ended questions to promote critical thinking, uncover assumptions, and evaluate reasoning. 
	- Moshman & Geil transcripts of group discussions function in line with the socratic method. 
- Blinder & Morgan - are two heads better than one? Decision making in humans
	- Two experiments carried out to look at the quality and speed of group decisions over individuals. 
		- First experiment was devoid of any content that required domain knowledge - subjects sample blue or red balls from an urn and estimate its composition. Subjects played as individuals, groups on majority rules and unanimous agreement. Statistically significant results support the hypothesis "Groups make better decisions than individuals"
		- Second, same as above but mimicking macro economic monetary policy. Subjects were required to have taken a introduction to economics class before being eligible for the study. 
	- Simple models of groups do not hold empirically on these experiments.
		- A groups decision is simply the average of the individual decisions
		- A groups decision is the median of individuals
		- A groups decision is that of its strongest member
	- Being an economics paper it rightfully avoids making psychological conclusions about group behaviour and simply concludes that 
- Propp in search of the assembly bonus effect
	- Calls for a revival in trying to observe or disprove the assembly bonus effect. 
	- Highlights the difficulty in setting up these kind of experiments on people.
- Transactive Memory System (TMS) Wegner 1986 definition as "a set of individual memory systems in combination with the communication that takes place between individuals"
	- Propp 1999 expands this definition emphasising "the communication processes that occur within a group as it encodes, stores, and ultimately attempts to retrieve information for use in decision making"
	- In these systems groups assign responsibility to individuals to store knowledge in what is known as differentiated information (Wegner et al 1985). Differentiated information is non-redundant across members and integrated information is redundant across members.
	- Research covers small to large groups, intimate personal relationships to business teams
- In LLMs there is limited research and experiments into TMS, assembly bonus effect, or 
	

- Dialogue as an activity - *Not currently relevant*
	- LLMs are primarily limited to dialogue. Perhaps CoT and hidden reasoning are monologues or perhaps their implementation makes them an internal dialogue.
	- Pickering & Garrod "Towards a mechanistic psychology of dialogue" 


#### Reasoning in LLM/RLMs
Recent years have seen a proliferation of research focused on the reasoning capabilities of LLMs, with numerous studies claiming improvements in various forms of logical or commonsense reasoning. This surge in interest has given rise to a wide array of methodologies designed to enhance or better elicit reasoning behaviour in LLMs. Prompt engineering techniques, such as chain-of-thought (CoT), few-shot learning, and the use of intermediate representations generated by the model itself, have been shown to improve performance on reasoning tasks to various degrees \cite{weiChainofThoughtPromptingElicits, yeUnreliabilityExplanationsFewshot2022a, liuPersonaFlowBoostingResearch2024, yangArithmeticReasoningLLM2024, puertoCodePromptingElicits2024}. Additionally, adaptation of decoding strategies aim to more closely mimic human reasoning by leveraging multiple reasoning paths \cite{wangSelfConsistencyImprovesChain2023}. Some studies investigate augmenting LLMs with external tools, including retrieval-augmented generation (RAG), symbolic solvers (e.g., SMT solvers), and code execution environments, which offload computation-heavy or symbolically rigid components of reasoning \cite{luChameleonPlugandplayCompositional2023a, panLogicLMEmpoweringLarge2023, qianChatDevCommunicativeAgents2024a}. More recently, approaches such as DeepSeek's R1 model introduce the concept of "hidden reasoning," where intermediate reasoning steps are computed internally and not necessarily exposed in the final output. Together these developments reflect an ongoing exploration of how LLMs can engage in reasoning through a combination of architectural design, training paradigms, and inference-time interventions. 

An idea that is not new in machine learning is few-shot learning, wherein a model is provided with a limited number of exemplars within the prompt to guide its behaviour \cite{fewshotSurvey2020}. While this approach predates the rise of large-scale transformer architectures, it has become a standard baseline in the evaluation of LLMs due to its capacity to enable in-context learning - the apparent ability of a model to generalise from examples provided at inference time without updating model weights. In practice, few shot prompting is frequently employed in benchmarking tasks and is often associated with improved quantitative performance \cite{dziriFaithFateLimits2023a, lin2025zebralogic}. The mechanism by which few-shot prompts enhance task completion appears to be through pattern matching rather than structured logical inference, thereby limiting their utility in evaluating true reasoning capabilities. Notably, the ARC (Abstraction and Reasoning Corpus) AGI benchmark \cite{cholletARCPrize20242025} isolates few-shot prompting as its primary interface, deliberately removing external knowledge or pre-training advantages to evaluate core abstraction and generalization skills. Its difficulty lies precisely in the requirement for reasoning beyond memorized patterns, underscoring the limitations of few-shot learning as a measure of genuine reasoning ability.

A more targeted method for inducing reasoning in LLMs is _Chain of Thought_ (CoT) prompting, which encourages models to explicitly decompose complex problems into intermediate steps. The technique is designed to emulate the sequential nature of human reasoning by generating stepwise textual rationales, and has been proposed as a general-purpose strategy applicable to a wide range of tasks solvable via language. Proponents argue that CoT not only improves task performance but also offers interpretability, by making the decision process visible. However, this interpretability is contested. In practice, CoT outputs can contain hallucinated or logically inconsistent reasoning chains that nevertheless conclude with a correct answer, raising questions about whether such reasoning is genuine or post-hoc rationalization. \citeauthor{yeUnreliabilityExplanationsFewshot2022} provide empirical evidence that CoT can, in fact, impair performance relative to standard prompting on certain textual inference tasks \cite{yeUnreliabilityExplanationsFewshot2022}. Using the explainable Stanford Natural Language Inference (e-SNLI) dataset—a benchmark that explicitly requires natural language justifications—they find that CoT sometimes leads to degraded outcomes, suggesting that more text does not necessarily imply better reasoning.

To address some of the limitations of CoT prompting, self-consistency has been proposed as a decoding strategy that samples multiple CoT outputs and selects the most frequent final answer \cite{wangSelfConsistencyImprovesChain2023}. This approach leverages the probabilistic nature of LLM decoding to explore diverse reasoning trajectories, with the assumption that the correct answer will emerge as the most convergent outcome. Unlike greedy decoding, which may commit to a single, potentially suboptimal reasoning path, self-consistency promotes robustness by aggregating across samples. Experimental results show that self-consistency significantly outperforms standard CoT on several reasoning benchmarks and even improves performance on tasks where CoT alone is detrimental \cite{wangSelfConsistencyImprovesChain2023}. The apparent benefit of diversity in generated reasoning paths points to the potential value of ensemble methods or multi-agent settings, where individual agents may contribute distinct "perspectives" or specialized competencies \cite{islam-etal-2024-mapcoder}. This observation motivates further inquiry into whether systems composed of multiple interacting LLMs could more effectively simulate collaborative reasoning processes.



**What is a "Reasoning" Language Model (RLM)?** 
Reasoning language models 
- Chain of thought prompting - A prompt engineering technique used to allow models to decompose multi-step problems into intermediate steps in principle. 
	- Authors claim that CoT provides interpretability, demonstrating how models arrived at their answer; is potentially applicable to any task that humans can solve via language; and can be readily elicited in sufficiently large off-the-shelf language models. 
	- Authors also caveat that while CoT emulates thought process it does not answer whether the network is actually reasoning.
	- Ye & Durrett demonstrate that CoT sometimes hurts performance compared to standard prompting on textual reasoning tasks (e-SNLI) 
- Self-consistency - proposes a new decoding strategy off the back of CoT. The model produces k reasoning path samples, marginalises out the reasoning and chooses the most consistent answer as the final answer. 
	- Shows an impressive improvement over CoT alone on various benchmarks, especially arithmetic reasoning tasks.
	- Self-consistency improves reasoning even where CoT alone hurts performance (Ye & Durrett)
- [Arithmetic Reasoning with LLM: Prolog Generation & Permutation](https://aclanthology.org/2024.naacl-short.61/) NAACL 2024
	- Key Takeaways: 
		- Prolog code generation is consistently better than CoT on [[GSM-8K]] 
		- Another win for intermediate representations for reasoning. Producing code that can be interpreted deterministically to produce an answer as appose to LLM guessing.
	- Novel Ideas:
	- Methods:
		- Converted the GSM8K dataset from CoT to Prolog code
		- Augmented the dataset by reordering Prolog code
		- Finetuned models on the dataset
	- Potential Cheats:
		- Corpus is 8.5k, test set only 1.3k, "Only considered samples with an integer answer" so how big was the test set in the end?
	- Usefulness to me:
		- Indicates that intermediate representations are useful in reasoning
		- First time seeing beam search being used, is this a sensible approach for code generation?
	- Fallout questions:
		- How large was the corpus after removing the non-integer samples?
		- What does permutation ratios refer to? 

### Compositionality
The meaning of the whole is a function of the meaning of the parts (Partee 1995 p.313) -> Lakoff 1977 - The meaning of the whole is greater than the sum of its parts

### Complexity
A recurring theme in the literature is the measurement and effect of complexity on the performance of language models. 
- Faith and Fate - Uses directed acyclic computational graph to measure compositional complexity. Also utilises ZebraLogic bench. **Need to come back to this**
	- Reasoning Depth 
	- Reasoning Width
	- Average Parallelism
- ZebraLogic - Curse of Complexity
- The illusion of reasoning
	- critique







### Learning / Emergent abilities





### Benchmarks & Evaluation Frameworks
As the capabilities of large language models have rapidly advanced, the design of evaluation benchmarks has had to evolve in parallel. Traditional reasoning benchmarks often take the form of multiple-choice question answering tasks \citep{rajpurkar-etal-2016-squad, lee-etal-2020-squad2, talmor-etal-2019-commonsenseqa, liuLogiQAChallengeDataset2020a, liuLogiQA20AnImproved2023, parmarLogicBenchSystematicEvaluation2024a}, which are well-suited to assessing a model’s retention of factual knowledge but are poorly aligned with measuring genuine reasoning ability \citep{dziriFaithFateLimits2023a}. These formats seem to reward pattern recognition and lexical overlap rather than structured inference or abstraction. Moreover, such benchmarks frequently suffer from a lack of robustness and longevity: once released publicly, they are quickly solved by successive state-of-the-art models, often through overfitting or exposure to training data that mirrors the test set. This short lifespan undermines their value as long-term comparison tools . 

To address these limitations, modern reasoning benchmarks must exhibit several key properties. First, they must be _scalable_ in difficulty, allowing for progressive evaluation as models improve—though defining complexity in the context of reasoning remains a challenge. Second, they must be _novel_, both in content and structure, to reduce the likelihood of training data contamination and to avoid eliciting responses through memorized templates or shallow heuristics. In the remainder of this section, we examine how recent benchmark efforts attempt to satisfy these criteria, and what implications they carry for the evaluation of reasoning in LLMs.




#### Question answering / multiple choice benchmarks
- SQuAD & SQuAD 2.0 (Stanford Question and Answering Dataset)
	- Contains 100,000+ questions each based on wikipedia articles where the answer to each is a segment from the given text. Was originally challenging in 2016 when released. Not multiple choice. 
	- SQuAD 2.0 adds 50,000 more adversarial questions with impossible answers - unanswerable questions have no supporting statements in the text. 
	- As of 2021 neural models beat human baseline and have almost perfect scores nearing 95%
- CommonsenseQA: A Qestion Answering Challenge Targeting Commonsense Knowledge
	- 
- LogiQA (Deductive)
	- Tests Natural Language Inference (NLI) and Machine Reading Comprehension (MRC)
	- 8,678 QA instances covering different types of deductive reasoning
	- Found models performed worse than human baseline 
- Logical reasoning benchmarks are numerous and are usually in puzzle format.
- ZebraLogicBench (Deductive, First-order, non-monotonic)
	- constraint satisfaction problem
- Starbattle 
	- more open constraint satisfaction problem
- ARC AGI 
	- no known constraints, model must interpret the rules in order to find the answer. 
	- Smallest puzzle state is enormous with $10^9$ possible solutions if the solution grid size is known. Making the easiest puzzle well past the Zebra logic curse of complexity.
- LogicBench (Deductive, First-order, non-monotonic)
- LogiQA (Deductive)

- Beyond the imitation game
	- Theres a breakthrough 'aha moment' on certain tasks (including those composite in natrue). Observing this depends on task specification, using exact string match vs bleu or rouge turns breakthrough tasks into linear ones.
	- The idea of breakthrough tasks is linked to curse of complexity. Does the models understanding actually scale in ZebraLogic despite a lack of accuracy as we scale the model?
	- Metrics are brittle. Changes in format of prompt can turn a breakthrough task into a linear one. 
- Problem complexity:
	- Search space - all of the above are grid based systems (Zebra) 
	- SAT/SMT solvers - number of backtracks (Zebra)
### How do we measure logical reasoning in language models?
- Benchmarks

	- ZebraLogicBench 
	- ARC AGI 
	- LogicBench 
	- LogiQA (Deductive)
#### Metrics 



### Challenges and Limitations
- The illusion of reasoning & Critique
	- 
- Faith and Fate - Critical of reasoning in LLMs.
	- Transformers solve compositional tasks by reducing multi-step compositional reasoning into linearisd path matching. The correct result my be achieved when patterns are found but does not lead to generalisation on uncommon or complex examples.
	- Errors in language models on compositional tasks propagate and compound in subsequent steps. 

- Scalability Issues
	- Zebralogic bench's findings


- Are LLMs good at structured outputs?
	- MA-LLMs need to be good at structured output for tool use (code execution), summarisation and information sharing between systems which all require some structured output (usually JSON or simple lists in the case of summarisation).  
	- They must also be good at following instruction, this sounds obvious enough but receiving long form NL when expecting a list or key, value pair could be catastrophic for MA-LLM
	- Y Lie et al test various LLMs over various domains and structured output types using their own benchmark SoEval
	- The results show that larger models (GPT series) are better at structured outputs on average. Every model tested were particularly bad at key value pairs and attribute graphs which is perhaps unsurprising given that JSON is a type of key value pairing and possibly a more natural way for an LLM to communicate (assuming training material contains more JSON)
	- Models were asked to produce structured output for a large variety of task subjects, some of which would not organically make sense or be contrived. This may influence the results.









## Background
- **early LLM reasoning** -> Reasoning Language Models (RLMs)
	- Besta et al., 2025
- Chain of Thought
### Single-agent reasoning techniques
- Self Reflexion 
- Reasoning Tokens
-

### Tool use/knowledge integration
- RAG
- SAT/SMT solvers - formal verification tool
- Code execution

### Multi-agent Architectures/Mechanisms
- Ensembles/Majority vote 
- Debate/adversarial agents - LLM-Debate
- role play
	- ChatDEV
	- Shanahan et al., 2023b
- validation/judge - Reflexion
- In context 
	- Dong et al., 2024









- Task complexity for adaptive/dynamic agent allocation


Include a criticism section perhaps?
https://machinelearning.apple.com/research/illusion-of-thinking





- [Are LLMs good at structured outputs? A benchmark for evaluating structured output capabilities in LLMs](https://www.sciencedirect.com/science/article/pii/S0306457324001687?casa_token=bbPRl_8zyDkAAAAA:PNjkDcjOy_XaPQs2FGJkazxAO5axMfmu3qNUkG98uPV3ji_iBFxTOQrvERbbhKbhEDT3H2-F)
	- KT: 
		- Evaluates the structured output capabilities of LLMs by introducing the [[SoEval]] benchmark.
	- Novel Ideas:
	- Methods:
	- Potential Cheats:
		- Uses GPT4 to create dataset, GPT4 achieves the best score across the benchmark
	- Usefulness to me:
	- Fallout Questions:
		- How can a benchmark like this be more fair? 




