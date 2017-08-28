==========================================
Chromosomal Aberration Report
==========================================

| CA (Chromosomal Aberration) Report displays a landscape of chromosomal aberrations such as structural variations (typically identified by genome sequence data) and gene fusions (by transcriptome sequence data).

* Barplot at the top panel shows the total number of breakpoints of CAs in the cohort.
* The circular plots below shows the [CIRCOS-like](http://circos.ca) profile of CAs for each sample, where two edges of a curved line represent breakpoints of each CA.

| When you select a region in the barplot at the top, samples having any of the breakpoints in the selected region are highlighted (when Stype of selected graphs are set to "Highligh selected graphs") or samples without any of the breakpoints in the region dissapears ("Hide non-selected graphs).

.. image:: image/sv_operation1.PNG
  :scale: 100%


| There are two stacks in the bar chart, and the color is separated depending on whether two break points are beyond the chromosome (Inter Chromosome) or within the same chromosome (Intra Chromosome). [*]_
| If unchecked, that element is not displayed.

.. [*] About categorization

  Categorization by inter or intra chromosome is the default setting.
  By using the configuration file, categorization can be changed. 
  Please refer `変異のグルーピング <./data_ca.html#ca-group>`_.

  
.. image:: image/sv_operation2.PNG
  :scale: 100%

| Click the circle graph for each sample to enlarge it.
| Show the details by hovering the mouse over the line connecting the breakpoints.

.. image:: image/sv_operation3.PNG
  :scale: 100%
