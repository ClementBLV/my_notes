__tag__ : #RE 
__publication date__: 5 Apr 2023
__reading date__ : 
__link__ : https://paperswithcode.com/paper/structured-prompt-interrogation-and-recursive
__comments__ : Really recent paper on prompting RE with a [[Zero shot learning]] with a [[GPT-3]] model. It does'nt outperform the existing model and is average, but easy to adapt and few parameters.

---
>__abstract__ : Creating knowledge bases and ontologies is a time consuming task that relies on a manual curation. AI/NLP approaches can assist expert curators in populating these knowledge bases, but current approaches rely on extensive training data, and are not able to populate arbitrary complex nested knowledge schemas. Here we present Structured Prompt Interrogation and Recursive Extraction of Semantics (SPIRES), a Knowledge Extraction approach that relies on the ability of Large Language Models (LLMs) to perform zero-shot learning (ZSL) and general-purpose query answering from flexible prompts and return information conforming to a specified schema. Given a detailed, user-defined knowledge schema and an input text, SPIRES recursively performs prompt interrogation against GPT-3+ to obtain a set of responses matching the provided schema. SPIRES uses existing ontologies and vocabularies to provide identifiers for all matched elements. We present examples of use of SPIRES in different domains, including extraction of food recipes, multi-species cellular signaling pathways, disease treatments, multi-step drug mechanisms, and chemical to disease causation graphs. Current SPIRES accuracy is comparable to the mid-range of existing Relation Extraction (RE) methods, but has the advantage of easy customization, flexibility, and, crucially, the ability to perform new tasks in the absence of any training data. This method supports a general strategy of leveraging the language interpreting capabilities of LLMs to assemble knowledge bases, assisting manual knowledge curation and acquisition while supporting validation with publicly-available databases and ontologies external to the LLM. SPIRES is available as part of the open source OntoGPT package: https://github.com/ monarch-initiative/ontogpt. 

## Goal 
generate RE candidates using prompts in a zero shot learning way. Doesn't outperformed the benchmarks but easy to custom and adapt without any training data. 
Current model use transformer but : subjective to hallucination + insensitive to negation. And they need training data to perform well on specific tasks. 
Model like [[GPT-3]] perform well with zero-shots or few-shots learning on task like : NER, RE.
Automatically complete schemes of ontologies (KB) in any knowledge. 

## Method 

#### Knowledge Scheme generation 

It is a collection of classes (set of attributes + constraints) or templates, it is generated on LinkML. 

#### Model core 

As a core they use a GPT-3 but they make request on it using [[OntoGPT]]. 

#### Steps 

| __inputs__ | __model__ | __outputs__ |
|---|---|---|
| KB schema +raw text containing the info | OntoGPT which request GPT-3 and public data | structure data |


1. Generate the prompt text : ex *“From the text below, extract the following entities in the following format”* is done for all the attribute of the class we are completing 

>ex : 
__Split the following piece of text into fields in the following format: 
	food_item:  _the food item>_
	amount:  _the quantity of the ingredient>_
Text: 
	garlic powder (2 tablespoons) __ 
	===

2. Complete the prompt using OntoGPT, it request the API and complete the prompt like that 

>	__food_item: garlic powder
>	amount: 2 tablespoons

3. Recursive parsing of the output 

## Conclusion 

Extracts info with : no model tuning or training data. The approach is highly customizable, flexible, and can be used to populate knowledge schemas across varied domains.
