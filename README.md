Hittite NLP Pipeline

[[https://www.ukp.tu-darmstadt.de/publications/?no_cache=1&tx_dppublications_pi1%5Bpublication%5D=10481&tx_dppublications_pi1%5Baction%5D=show&tx_dppublications_pi1%5Bcontroller%5D=Publication&cHash=b8407d50f0bf26eb0cdbfd56d71dfc42#dp_publications-single]]

@inproceedings{TUD-CS-2017-0133,
	title = {Distantly Supervised POS Tagging of Low-Resource Languages under Extreme Data Sparsity: The Case of Hittite},
	author = {Sukhareva, Maria and Daxenberger, Johannes and Fuscagni, Francesco and Prechel, Doris and G{\"o}rke, Susanne},
	organization = {tba},
	publisher = {tba},
	volume = {tba},
	booktitle = {LaTeCH '17 Proceedings of the 11th Workshop on Language Technology for Cultural Heritage, Social Sciences, and Humanities},
	pages = {tba},
	number = {tba},
	month = aug,
	year = {2017},
	location = {Vancouver},
	website  = {https://github.com/UKPLab/latech-clfl2017-hittitenlppipeline},
}



The Hittite NLP pipeline has the following parts:

1. Preprocessing
2. Stemming
3. Annotation projection
4. POS tagging

1. Preprocessing
It reads a mysql data base and coverts the data into UIMA format.

2. Stemming
German is stemmed by the off-the-shelf stemmer. The Hittite stemmer is implemented as a part of the pipeline.
It learns the stems from the character-based alignment produced by Phrasal ITG Aligner (pialign).

3. Annotation projection
Is based on the word alignment produced by Giza++.

4. The Hittite pos tagger is trained on the resulting annotation projection. The best results are produced by
hittitestemmed.bin model.

The pipeline needs the following tools installed on your machine:

GIZA++, preferrably with Moses SMT system:
http://www.statmt.org/moses/

pialign - Phrasal ITG Aligner:
http://www.phontron.com/pialign/

Pialign takes a long to time to be trained so you can use our pretrained model in alignment/alignment.palign
If you want to train your own pialign model you need to uncomment this in Pipeline.java

//			 PialignExecutor pe = new PialignExecutor("aligned.punct.1",
//					"clean-corpus.transliteration",
//					"clean-corpus.translation", 100, false);

You also need to change the location of pialign in runperlscript.sh and of moses in
GizaExecutor.java

The Hittite corpus used as input of this pipeline can be provided on request.

