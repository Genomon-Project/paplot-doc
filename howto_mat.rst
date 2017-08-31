===========================
Mutation Matrix Report
===========================

Mutation Matrix Report displayes a landscape of mutation status across genes (Gene, vertical axis) and samples (Sample, horizontal axis).


:Horizontal bar chart (Sample):
  | Displays the total number of mutations detected for each sample.

:Vertical bar chart (Gene):
  | Displays the number of mutations and fractions of mutation types (e.g., nonsynonymous, stopgain and so on) for each gene.
  |
  | - If the same sample has multiple mutations at the same gene, this is counted as 1.
  | - If the same sample has multiple mutation with different mutation types at the same gene, just a mutation type with "the higher priority" is counted. For example, in the default setting, the priority of stopgain is higher than that of nonsynonymous mutations. The order of priority can be modified by the configuration file. 

.. Please see (XXX) for the default settings of the priority and (XXX) for modifying them.

:Mutation type:
  | Mutation type is displayed with a distinct color. If you want to hide a specific type of mutations, uncheck them in this section.

:Subplot:
  | If there is meta infromation for the samples (e.g., clinical information), it can be displayed as a subplot. This file must be entered in the configuration file before executing the ``paplot`` command.

.. image:: image/mut_operation1.PNG
  :scale: 100%

**How to view**

.. image:: image/mut_operation2.PNG
  :scale: 100%

.. image:: image/mut_operation2_2.PNG
  :scale: 100%

1. Axis-X sort 
---------------

Change the order of the horizontal axis.

 - None ... Default ordering
 - ASC ... Ascending ordering 
 - DESC ... Descending ordering

It can sort by the following elements (allowing for multiple key ordering):

:Sample ID:
  | Sort by the name of samples 

:Mutation number:
  | Sort by the number of mutations per sample

:Genes:
  | Sort by the mutation states of the selected genes. After selecting either ASC/DESC, select the gene to add from the list box next and click the [add sort key] button.

:Automatic Gantt-chart:
  | We will create a Gantt chart automatically. Enter the number of genes to display [*]_ in the horizontal edit box and click the [Gantt-chart] button.

**How Gantt-chart works**

 1. First sort the genes according to the descending number of mutations.
 2. Then divide the samples into two groups according the mutation status of the first gene, and place the group with the mutation to the left and the other group to the right.
    Repeat this procedure for the second one, third one, ...

.. [*]
   It is ideal to display all the detected genes, but as processing becomes heavier, narrowing down to the gene list will be practical in many case.

.. image:: image/mut_operation3.PNG
  :scale: 100%

2. Axis-Y sort
----------------

Change the order of the vertical axis.

 - None ... Default ordering 
 - ASC ... Ascending ordering 
 - DESC ... Descending ordering 

It can sort by the following elements (allowing for multiple key ordering):

:Mutation number: Number of mutations per gene 
:Gene name: Sorted by gene name 


3. Sample filter
------------------

Sets the maximum value of the vertical axis of the horizontal bar chart (Sample).


| In some cases, only a few samples have extremely large numbers of mutations compared to others.
| In those cases, setting the threshould for the maximum number of mutations will make the graph a lot easier to see.
| Enter the threshould value in the horizontal edit box, then click the [update filter] button.
| In the default setting ("blank"), the maximum of the horizontal axis is set to the maximum number of mutations among the samples in the cohort automatically.


**Before and after filter application**

| Example of display when maximum value is set to 200. 
| 

.. image:: image/mut_operation4.PNG
  :scale: 100%


4. Genes filter
-----------------

Set the filter for the gene displayed on the vertical axis.

:Rate:
  | Frequency of the samples with mutations at each gene (%). The initial value is 0% (no filtering)

:Display maximum:
  | Maximum number of genes to display.

After setting the above items, please click the [update filter] button.

