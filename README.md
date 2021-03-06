# SPARQA: question answering over knowledge bases

Code and dataset for paper: "SPARQA: Skeleton-based Semantic Parsing for Complex Questions over Knowledge Bases" (AAAI-2020).

If you meet any questions about SPARQA, please email to him (ywsun@smail.nju.edu.cn).

## Paper Abstract:
> Semantic parsing transforms a natural language question into a formal query over a knowledge base. Many existing methods rely on syntactic parsing like dependencies. However, the accuracy of producing such expressive formalisms is not satisfying on long complex questions. In this paper, we propose a novel skeleton grammar to represent the high-level structure of a complex question. This dedicated coarse-grained formalism with a BERT-based parsing algorithm helps to improve the accuracy of the downstream fine-grained semantic parsing. Besides, to align the structure of a question with the structure of a knowledge base, our multi-strategy method combines sentence-level and word-level semantics. Our approach shows promising performance on several datasets.

Please, read the paper for SPARQA in detail [here](https://www.aaai.org/Papers/AAAI/2020GB/AAAI-SunY.3419.pdf).

## Project Structure:

<table>
    <tr>
        <th>File</th><th>Description</th>
    </tr>
    <tr>
        <td>code</td><td>SPARQA codes</td>
    </tr>
    <tr>
        <td>dataset</td><td>QA datasets and resouces for entity linking</td>
    </tr>
    <tr>
        <td>skeleton</td><td>Skeleton bank of 10K complex questions</td>
    </tr>
    <tr>
        <td>slides</td><td>SPARQA slides and poster</td>
    </tr>
</table>
 
## Skeleton
It is a complex questions skeleton bank by manually annotation. It contains about 10K questions (5,166 questions and 5000 questions from ComplexWebQuestions). We make this resource public to supporch future research (question understanding or semanatic parsing research).

## Requirements
* Python 3.6
* PyTorch 1.3.0+ - [installation](http://pytorch.org/)
* See [requirements.txt](https://github.com/nju-websoft/SPARQA/blob/master/code/requirements.txt) for the full list of packages

## Common Resources
* Root datasets: default value D:/dataset. You can edit it in the configution globals_args.py. 
* GloVe embedding (glove.6B.300d) [download](https://nlp.stanford.edu/projects/glove/)
* Stanford CoreNLP server. The sever version we use is stanford-corenlp-full-2018-10-05. download [here](https://stanfordnlp.github.io/CoreNLP/corenlp-server.html), get started, and replace ip_port address in globals_args.py with URL of your CoreNLP.
* Python wrapper for Stanford CoreNLP's SUTime Java library. download [here](https://github.com/FraBle/python-sutime). SPARQA need to use the Java library. default save in the folder: root/resource_sutime/. if you save other place, remember to replace the address sutime_jar_files in configution with your folder path.
* Four files (stopwords.txt, ordinal_fengli.tsv, unimportantphrase, and unimportantwords) download [here](https://drive.google.com/open?id=1AW5rT5MaZrDkc2rNz0TZhDJaQVQwJgT4). download the file, and saves in the root (default. you can edit these addresses).
* BERT pre-trained Models download [here](https://drive.google.com/drive/folders/1tlUF7ALLLXiHu280gPdlVyQlGvJFklGC) and save the seven files in the default root/pre_train_models address in the configuration bert.args.py (you can edit these addresses).
* Download two version freebases: the latest version for ComplexWebQuestions [here](https://developers.google.com/freebase) and the 2013 version for GraphQuestions [here](https://github.com/ysu1989/GraphQuestions)
* After you download the KBs, you need to run a virtuoso and load the KBs. It costs long time. If you meet questions, the [file](http://ws.nju.edu.cn/blog/2017/03/virtuoso%E5%AE%89%E8%A3%85%E5%92%8C%E5%AF%BC%E5%85%A5%E6%95%B0%E6%8D%AE/) is helpful. 

## Specific CWQ 1.1 Resources
* To access interface virtuoso server, you need configure odbc address (freebase_pyodbc_info) in globals_args.py. 
* To access interface virtuoso html service, you need configure html address (freebase_sparql_html_info) in globals_args.py. 
* CWQ 1.1 five BERT pre-trained Models for Skeleton Parsing. download [here](https://drive.google.com/drive/folders/1t4Rb2feVOSGF_5lRBHwrB_GfxyL2rqby) and save the five files in the default root/dataset_cwq_1_1 address in the configuration bert.args.py (you can edit these addresses).
* Entity-related Lexicons and schema-related lexicons of Freebase latest version. download [here](https://drive.google.com/drive/folders/1t4Rb2feVOSGF_5lRBHwrB_GfxyL2rqby). Specificaly, the files variables in KB_Freebase_Latest class in the configuration kb_name.py.
* ComplexWebQuestions 1.1 dataset. download all files from [here](https://github.com/nju-websoft/SPARQA/tree/master/dataset/dataset_cwq_1_1). It consists of train/dev/test data and pre-processed sparql query bgp files. Note that the data_path_match file is used to save the word-level scoring model and the data_question_match file is used to save the sentence-level scoring model. The oracle_grounded_graph_cwq file used to save the pre-processed query structures to improve the query generation efficiency.

## Specific GraphQuestions Resources
* To access interface virtuoso server, you need configure odbc address (freebase_pyodbc_info) in globals_args.py. 
* To access interface virtuoso html service, you need configure html address (freebase_sparql_html_info) in globals_args.py.
* GraphQuestions five BERT pre-trained Models for Skeleton Parsing. download [here](https://drive.google.com/drive/folders/1Mjpan599INCVRgRQTsirgVdyt29iKblO) and save the five files in the default root/dataset_graphquestions address in the configuration bert.args.py (you can edit these addresses).
* Entity-related Lexicons and schema-related lexicons of Freebase 2013 version. download [here](https://drive.google.com/drive/folders/1Mjpan599INCVRgRQTsirgVdyt29iKblO). Specificaly, the files variables in KB_Freebase_en_2013 class in the configuration kb_name.py.
* GraphQuestions dataset. download all files from [here](https://github.com/nju-websoft/SPARQA/tree/master/dataset/dataset_graphquestions). It consists of train/test data and pre-processed sparql files. Note that the data_path_match file is used to save the word-level scoring model and the data_question_match file is used to save the sentence-level scoring model. The oracle_grounded_graph_graphq file used to save the pre-processed query structures to improve the query generation efficiency. The three files (graph_testing_question_normal.txt, 2019.05.13_test_answers, and 2019.05.13_train_answers) are combined in graphquestions.testing_nju_1209.json and graphquestions.training_nju_1209.json. It should modify the dataset interface of code. Once meet error when runing, please email to ywsun.

## Run SPARQA Pipeline
The pipeline has two steps for answering questions: 

* (1) KB-indenpendent graph-structured ungrounded query generation.
* (2) KB-dependent graph-structure grounded query generation and ranking.

Specifically, see running/freebase/pipeline_cwq.py if you want to run ComplexWebQuestions 1.1. or see running/freebase/pipeline_grapqh.py if you want to run GraphQuestions.
Below, I describe how to run our SPARQA by step-to-steps on GraphQuestions.

### Specific-dataset Configuration

* Datset Selection in the configuration globals_args.py: q_mode = graphq, which means GraphQuestions. q_mode = cwq, which means ComplexWebQuestions 1.1.
* Skeleton Parsing in the configuration globals_args.py: parser_mode = head, which means skeleton parsing. (note that parser_mode=dep, which means dependency parsing).
* Replace the address freebase_pyodbc_info and freebase_sparql_html_info in the globals_args.py with your local information.

### KB-indenpendent query generation
* Variable module = 1.0, which means run KB-indenpendent query generation. The input: graph_questions_filepath. The output: structure_with_1_ungrounded_graphq_file.

### KB-dependent query generation
* Variable module = 2.1, which means to run variant generation. The input: structure_with_1_ungrounded_graphq_file. The output: structure_with_2_1_grounded_graph_file.
* Variable module = 2.2, which means to grounding. The input: structure_with_2_1_grounded_graph_file. The output: structure_with_2_2_grounded_graph_folder.
* Variable module = 2.3_word_match, which means to ranking using word-level scorer. The input: structure_with_2_2_grounded_graph_folder.
* Variable module = 2.3_add_question_match, which means to combine sentence-level scorer and word-level scorer. The input: structure_with_2_2_grounded_graph_folder.
* Variable module = 3_evaluation, which means to run evaluation. The input: structure_with_2_2_grounded_graph_folder. The output: results.

## Instruction of Output File
* It consists of list. The output of every question is dict. Specifically, keys (question, qid, function, compositionality_type, num_node, num_edge, words, gold_graph_query, gold_answer, and gold_sparql_query) is question information.
* Key span_tree represents question skeleton. 
* Key ungrounded_graph_forest represents KB-indenpendent query. It consists of ungrounded_query_id, blag, nodes, edges, important_words_list, abstract_question, sequence_ner_tag_dict, grounded_linking, and grounded_graph_forest.
* Key grounded_graph_forest represents candidate KB-dependent queries. It consists of grounded_query_id, type, nodes, edges, key_path, sparql_query, score, and denotation.

## Train Skeleton Models
* Five models (continue...)

## Train Multi-strategy Scoring Models
* Word-level scorer (continue...)
* Sentence-level scorer (continue...)

## Compare with Baselines
* GraphQuestions: PARA4QA, SCANNER, UDEPLAMBDA
* ComplexWebQuestions: PullNet, SPLITQA, and MHQA-GRN. Note that PullNet used annotated topic entities of questions in its kB only setting. SPARQA, an end-to-end method, do not use annotated topic entities. It is thus not comparable.

## Citation

	@inproceedings{SunZ0Q20,
	  author    = {Yawei Sun and Lingling Zhang and Gong Cheng and Yuzhong Qu},
	  title     = {{SPARQA:} Skeleton-Based Semantic Parsing for Complex Questions over Knowledge Bases},
	  booktitle = {The Thirty-Fourth {AAAI} Conference on Artificial Intelligence, {AAAI} 2020, The Thirty-Second Innovative Applications of Artificial Intelligence Conference, {IAAI} 2020, The Tenth {AAAI} Symposium on Educational Advances in Artificial Intelligence, {EAAI} 2020, New York, NY, USA, February 7-12, 2020},
	  pages     = {8952--8959},
	  publisher = {{AAAI} Press},
	  year      = {2020},
	  url       = {https://aaai.org/ojs/index.php/AAAI/article/view/6426},
	}

## Contacts
If you have any difficulty or questions in running codes, reproducing experimental results, and skeleton parsing, please email to him (ywsun@smail.nju.edu.cn).
