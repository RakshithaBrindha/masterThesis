# Towards Explainable Creativity: Tackling The Remote Association Test With Knowledge Graphs

Remote Association Test (RAT) is a creativity test that assesses participants' creativity by measuring their associative ability. Various AI frameworks can perform computational creativity tests like the Remote Association Test to measure AI systems' cognitive and problem-solving abilities. However, the state-of-art, CreaCogs cannot propose explanations for these solutions. Thus, my master's thesis's proposed aim is to implement an AI system that can solve RAT computationally by acquiring knowledge from a common-sense knowledge base and word embeddings and constructing explanations for these RAT solutions. The proposed approaches are implemented and evaluated with the state-of-art and the normative data of Bowden and Jung (2013). The study concludes that knowledge from ConceptNet provides a plausible approach to solve RAT computationally and explain "why" an answer is related to the RAT query.

*TimeFrame: 15.02.2021 - 15.09.2021*

The code for this thesis focuses on the following

## ConceptNet search local
Given a triple of concepts e.g., (question, reply, solution) and a ground solution e.g., statement, calculate:

- *solutions*: list of solutions based on conceptnet using [this](https://github.com/ldtoolkit/conceptnet-lite) python library. A solution is a node from three queries that result in the same node for every member of a triple.
- *has_solution*: boolean, whether the triple has a solution or not

- *accuracy*: accuracy calculated against *ground_solution*

For frat: look at non-compound concepts (focus of the thesis)

For rat: look at compound concepts

Moreover, model the explanations (*relation*) according to *templates.txt*

## Embedding search
The Cosine Similarity between two word vectors provides an effective method for reassuring the linguistic or semantic similarity of the correspoinding words. Sometimes, the nearest neighbors according to this metric reveal rare but relevant words that lie outside an average human's vocabulary.

Here all the nodes are checked against the solutions and a cosine distance is noted. Afterwards, solutions are filtered according to a threshold.

### Embedding general search
For every noun in the English language (65k taken from WordNet), get the embedding and thereafter find the cosine similarity with our triples. Finally, perform intersection between triple's solutions.

## Gensim search
Find the intersection of the queries based on [CenceptNet Numberbatch](https://github.com/commonsense/conceptnet-numberbatch). Find top3, top5, top10 solutions.

In order to use the script you must first download the conceptnet-numberbatch model (link in `resources/`), unzip the model and convert it using the `misc/number_batch_converter.py` script.

# Libraries & Tools

1. [conceptnet lite](https://github.com/ldtoolkit/conceptnet-lite): python library for working with conceptnet offline
  - [Conceptnet](https://conceptnet.io/) is a semantic network designed to help computers understand the meaning of words that people use
2. [ConceptNet Numberbatch](https://github.com/commonsense/conceptnet-numberbatch): Set of word embeddings for conceptnet
3. [embeddings](https://github.com/vzhong/embeddings): python package that provides pretrained word embeddings for natural language processing and machine learning
4. [gensim](https://github.com/RaRe-Technologies/gensim): python library for topic modelling, document indexing and similarity retrieval with large corpora. Used in Natural Language Processing and Information Retrieval

