# Relicensing Combined Datasets (ReCoDa)

- The **article** _Relicensing Combined Datasets_ was presented at the [15th IEEE International Conference on Semantic Computing (ICSC 2021)](https://www.ieee-icsc.org/) resource track.
A draft version is available as [PDF file](https://papers.dice-research.org/2021/ICSC2021_ReCoDa/Relicensing-Combined-Datasets-ReCoDa-public.pdf).
Look up the article at [Google Scholar](https://scholar.google.com/scholar?q=Relicensing+Combined+Datasets).
- The **presentation slides** can be downloaded as [PDF file](https://papers.dice-research.org/2021/ICSC2021_ReCoDa/Relicensing-Combined-Datasets-ReCoDa-slides-public.pdf).
- The **demo** can be accessed at [dice-research.org/ReCoDa](https://dice-research.org/ReCoDa).
- The **code of the demo** is available at [branch demo](https://github.com/adibaba/ReCoDa/tree/demo).


## Repository

This repository contains code to generate a list of compatible licenses based on multiple input licenses to be checked.
The following main steps are executed:

- Creation of a [KnowledgeBase](src/main/java/org/dice_research/opal/licenses/KnowledgeBase.java) which contains the licenses and attributes.
- License [Attribute](src/main/java/org/dice_research/opal/licenses/Attribute.java) values are mapped according to their type.
- The [Operator](src/main/java/org/dice_research/opal/licenses/Operator.java) computes composite attributes of all input licenses.
- Finally, the [BackMapping](src/main/java/org/dice_research/opal/licenses/BackMapping.java) creates a list of compatible licenses.

Knowledge Bases (Knowledge Graphs):

- Knowledge Bases are available in the resource directory [knowledge-bases](src/main/resources/knowledge-bases) as turtle/ccREL files.
- Knowledge Base files can be imported using the [KnowledgeBases](src/main/java/org/dice_research/opal/licenses/KnowledgeBases.java) class.
- To add additional Knowledge Bases, the [AttributeFactory](./src/main/java/org/dice_research/opal/licenses/AttributeFactory.java) can be utilized and afterwards the [Execution](src/main/java/org/dice_research/opal/licenses/Execution.java) methods help to run an experiment.

## Download

Downloads are available at the [releases](../../releases/) page.

## Evaluation and experiments

For the evaluation of the approach, experiments based on two license datasets are provided:
Creative Commons and the European Data Portal (EDP) License Compatibility Matrix.


### Creative Commons experiments

To run the evaluations based on Creative Commons, you first have to download the underlying dataset.
Therefore, download or clone the
[cc.licenserdf](https://github.com/creativecommons/cc.licenserdf)
repository.
For the ReCoDa article, a [cc.licenserdf copy](https://github.com/projekt-opal/cc.licenserdf) was used.
Afterwards, the directory of the repository can be set by the system property ``cc.licenserdf``.
Example commands to run the experiments are listed below.


**Creative Commons License Compatibility Chart**

```
java -Dcc.licenserdf=cc.licenserdf-master/cc/licenserdf/licenses/ -jar ReCoDa.jar cc1
```

This will run the [CcExperiment](src/main/java/org/dice_research/opal/licenses/cc/CcExperiment.java).


**Creative Commons cc.licenserdf with two input licenses**

```
java -Dcc.licenserdf=cc.licenserdf-master/cc/licenserdf/licenses/ -jar ReCoDa.jar cc2
```

This will run the [CcExperimentTuples](src/main/java/org/dice_research/opal/licenses/cc/CcExperimentTuples.java).


**Creative Commons cc.licenserdf with three input licenses**

```
java -Dcc.licenserdf=cc.licenserdf-master/cc/licenserdf/licenses/ -jar ReCoDa.jar cc3
```

This will run the [CcExperimentTriples](src/main/java/org/dice_research/opal/licenses/cc/CcExperimentTriples.java).


### European Data Portal experiments

To run the evaluation of the European Data Portal (EDP) License Compatibility Matrix, run the following maven command:

```
mvn clean test -Dtest=EdpLcmEvaluationTest -Drun.edp.lcm.tests=true
```

This will run the additional [EdpLcmEvaluationTest](src/test/java/org/dice_research/opal/licenses/EdpLcmEvaluationTest.java).


## Credits

[Data Science Group (DICE)](https://dice-research.org/) at [Paderborn University](https://www.uni-paderborn.de/)

This work has been supported by the German Federal Ministry of Transport and Digital Infrastructure (BMVI) within the
project [OPAL](https://dice-research.org/OPAL) under the grant no. 19F2028A and by the EU
H2020 Marie Skłodowska-Curie project [KnowGraphs](https://knowgraphs.eu/) under
the grant agreement no 860801.

