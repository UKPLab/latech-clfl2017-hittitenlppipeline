Hittite NLP Pipeline





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

Please cite as:
```
@inproceedings{TUD-CS-2017-0133,
	title = {Distantly Supervised POS Tagging of Low-Resource Languages under Extreme Data Sparsity: The Case of Hittite},
	author = {Sukhareva, Maria and Fuscagni, Francesco and Daxenberger, Johannes and G{\"o}rke, Susanne and Prechel, Doris and Gurevych, Iryna},
	booktitle = {LaTeCH '17 Proceedings of the 11th Workshop on Language Technology for Cultural Heritage, Social Sciences, and Humanities},
	pages = {95--104},
	month = aug,
	year = {2017},
	location = {Vancouver}
}
```


