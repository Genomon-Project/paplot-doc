************************
Commands of pa_plot
************************

------------------------
1. Basic usage
------------------------

.. code-block:: bash

  paplot subcommand [--config_file CONFIG_FILE] [--title TITLE]
                    [--ellipsis ELLIPSIS] [--overview OVERVIEW]
                    [--remarks REMARKS]
                    input output_dir project_name

|

**required**

:subcommand:
  Choose from the following: 
  
  - qc
  - ca
  - mutation
  - signature
  - pmsignature

:input:
  Input files. You can specify multiple files with wildcards (``*``, ``?``). Please note that the mark mark ``"``  can be set either at the beginning or the end.

.. code-block:: bash

  # single input file 
  pa_plot qc example/qc/SAMPLE1.qc ./test multi1 --config_file example/example.cfg
  
  # multiple input files (separeted by ,)
  pa_plot qc "example/qc/SAMPLE1.qc.csv,example/qc/SAMPLE2.qc.csv" ./test multi1 --config_file example/example.cfg
  
  # multiple files (using *)
  pa_plot qc "example/qc/*.csv" ./multi multi1 --config_file example/example.cfg


:output_dir:
  Output directory path. See :ref:`3. Output directory <output>` for the detail of directory commponents.
 

:project_name:
  Project name (used as the title of output files).

------------------------
2. Command options
------------------------

You can change the following items as options.

--config_file        Path to the configuration file. If not specified, then use default file.
--title              Title of the graph
--ellipsis           Abbreviated name of the graph. It is used for the graph file name. (ex, graph_**ca**.html) It is convenient to set it when outputting multiple files to the same directory.
--overview           Outline of the graph (displayed in the index.html file).
--remarks            Text shown in the remark section of the index.html file (The default value is set at ([style] remarks) in the setting file.


The default values ​​are as follows.

=============== =================== ============ ============================================= ==============
subcommand      title               ellipsis     overview                                      remarks
=============== =================== ============ ============================================= ==============
qc              QC graphs           qc           Quality Control of bam.                       none
ca              CA graphs           ca           Chromosomal Aberration.                       none
mutation        Mutation matrix     mutation     Gene-sample mutational profiles.              none
signature       Signature           signature    Mutational signatures.                        none
pmsignature     PMSignature         pmsignature  Express mutational signatures in pmsignature. none
=============== =================== ============ ============================================= ==============

.. _output:

---------------------
3. Output directory
---------------------

In the output directory (specified in the ``output_dir`` option),
you can find the output files with the following configuration.

.. code-block:: bash

  {output_dir}
    ├ {project_name}
    │   └ graph_*.html      <--- Graphs.
    │
    ├ js          <--- Don't delete. this 4 directories are required to display the HTML file.
    ├ layout
    ├ lib
    ├ style
    │
    └ index.html             <--- Please open this file in a web browser.

Please movew  whole ``{output_dir}`` when you want to move the result,
so as not to destroy the directory structure.


Please refer to the `how to use graphs <./index.html#how-to-toc>`_  for detailed way of seeing the result.

.. |new| image:: image/tab_001.gif
