************************
Introduction
************************

| paplot is graph generater from analysis results of genome.
|
| For example, you have such a text file by analyzing the genome.
|

.. image:: image/mutation_list.PNG
  :scale: 100%

| What do you want to after this?
| Do you want to create a graph?
| Do you create charts manually each time?
| Do you write scripts such as wrote previously?
| Do you create a graph in time to change the extraction conditions and sort conditions of the data?
|
| paplot is to automate this task, and to ease the genome analysis of everyone just a little bit, may be.
|

Graphs can be created
--------------------------

1. QC (Quality Control) graph

| QC graph reports each bam's quality.
|

.. image:: image/qc_dummy.png
  :scale: 100%

2. CA (Chromosomal Aberration) graph

| Circos like plot views inter chromosomal aberration, for example Structural Variation (SV).
| Bar plot views these distribution.
|

.. image:: image/sv_dummy.png
  :scale: 100%

3. mutation-matrix graph

| Plot mutation number.
| Virtical axis is gene and Horizontal axis is sample.
|

.. image:: image/mut_dummy.png
  :scale: 100%

