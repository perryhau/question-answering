# SelQA - Answer Sentence Selection

## Introduction

GitHub repository: https://github.com/emorynlp/question-answering/edit/master/data/selqa/ass/  

This repository contains a data set that has been described in:  

```
SelQA: A New Benchmark for Selection-based Question Answering.  
Jurczyk, T.; Zhai, M.; and Choi, J. D.  
In Proceedings of the 28th International Conference on Tools with Artificial Intelligence, of ICTAI'16, San Jose, CA, 2016. 
```


## Data set

Data can be downloaded here: http://www.mathcs.emory.edu/~tjurczy/selqa/selqa_ass.zip


## Description

The package contains three splits: train, development and test sets.
For each `[split]`, the following files can be found:

- *SelQA-ass-[split].txt* - a tab separated text file that contains samples for `[split]` set. Each line can be extracted to three elements:
  * `Question text`
  * `Sentence text`
  * `Label`

 where `Label` denotes whether this `Sentence text` provides the answer for the `Question text` (can be `0` or `1`).
  
- *SelQA-ass-[split]_raw.pickle* - a pickle file that contains raw data based on which the *SelQA-ass-[split].txt* has been created. Each pickle is a list of dictionaries, where each dictionary is a single question entity. In the dictionary, the following elements can be found:
  * `question` - question text
  * `is_paraphrase` - whether the `question` is a paraphrase of other question
  * `type` - genera of the `question` (generas: `set(['MUSIC', 'TV', 'TRAVEL', 'ART', 'SPORT', 'COUNTRY', 'MOVIES', 'HISTORICAL EVENTS', 'SCIENCE', 'FOOD'])`)
  * `article` - name of the Wikipedia article the `question` is about
  * `section` - name of the Wikipedia section the `question` is about
  * `sentences` - set of sentences (simply sentences of the given `section`) for this `question`
  * `candidates` - set of sentence indexes that provide the answer for given `question`.

- *SelQA-ass-[split]_analysis.pickle* - a pickle file contains useful information that might be used for analysis such as question length, section length etc. Each pickle is a list of dictionaries, where each dictionary is a single question entity. In the dictionary, the following elements can be found:
  * `question` - question text
  * `is_paraphrase` - whether the `question` is a paraphrase of other question
  * `genera` - genera of the `question`
  * `q_len` - question length (a number of word tokens in a `question`)
  * `s_len` - section length (a number of `sentences` in a `section`)
  * `q_types` - set of question types (types: `set(['what', 'why', 'when', 'who', 'where', 'how'])`. If empty, none of recognized types are found in the question.)

- *SelQA-ass-[split]_dep.txt* - a text file that contains raw dependency trees of all samples in each `[split]`. __Note__: First question's tree is followed by the trees of its sentences, which is follwed by the second question's tree, which is followed by the trees of its sentences etc...  
 We used [NLP4J](https://github.com/emorynlp/nlp4j) to parse the data.

------------------

## Contact

Should you have any question please contact the author:  
tomasz.jurczyk@emory.edu
