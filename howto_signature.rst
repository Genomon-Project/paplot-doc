=============================
Mutational Signature Report
=============================

Mutational Signature Report displays the "mutation signature" (see e.g., Alexandrov et al., Nature, 2013) as bargraphs and the estimated "contributions" of each signature to the mutations per samples as stacked bar graphs.

:Upper panel (mutation signature graph):
  | Mutation signatures are displayed (typically by barplots with 96 elements).

:Lower panel (signature contribution graph):
  | For each sample, the ratios of contributions of mutation signatures to the mutations are displayed.

.. image:: image/sig_dummy.PNG
  :scale: 100%

In addition, you can change the display mode using the list box below the stacked graph.

:View mode:
  :Rate: The percentage (%) of signature contribution normalized by sum-to-one constraint.
  :Count: It displays the ratio by the actual number of mutations.

:Sort by:
  :Sample ID: Sort by sample ID.
  :Mutation count: Descending order of the number of mutations (applicable only when the view mode is Count).


Display example when the view mode is [Count] and sorting is by [Mutation count].

.. image:: image/sig_operation1.PNG
  :scale: 100%


A similar representation is adopted for the case with pmsignature.

.. image:: image/pmsig_dummy.PNG
  :scale: 100%

.. |new| image:: image/tab_001.gif
