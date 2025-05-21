### What is an 'Agent'?
There isn't a widely accepted definition of agents when referring to LLMs but common agreed upon features include memory, [[Tool Use]], and the use of planning ([Nvidia - Introduction to LLM Agents](https://developer.nvidia.com/blog/introduction-to-llm-agents/)). 

[Russel & Norvig](https://ebookcentral.proquest.com/lib/suss/reader.action?docID=5495854&ppg=23) define an agent as something that acts, but state that a computer agent should operate autonomously, perceive their environment, persist over a prolonged time period, adapt to change, and create and pursue goals. 



# Multi-agent Architectures/Systems
Many different approaches to multi-agent systems have been developed, some like [[CAMEL]], [[ChatDev]] and [[AgentVerse]] use a fixed set of agents and do not adapt based on query or domain. They can be referred to as static agents. Other systems such as [[DyLAN]] select agents based on their relevance to the query, in a dynamic approach to agent selection.

## Dynamic LLM-Powered Agent Network for Task-Oriented Agent Collaboration (DyLAN)
This paper addresses some fundamental issues with Multi-agent systems. Prior frameworks consist of static agents, which struggle to adapt to different tasks. Earlier methods either handcraft teams using human priors or generate agents based off fixed prompts. These systems can also be particularly inefficient with inflated API usage. 


### Team optimisation
- Agent importance score
- Agent Team Reformation
- 