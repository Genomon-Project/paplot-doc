************************
paplot command 
************************

------------------------
1. Basic usage 
------------------------

.. code-block:: bash

  paplot subcommand [--config_file CONFIG_FILE] [--title TITLE]
                    [--ellipsis ELLIPSIS] [--overview OVERVIEW]
                    [--remarks REMARKS]
                    input output_dir project_name

**Required arguments**

:subcommand:
  Select from the followings:
  
  - qc
  - ca
  - mutation
  - signature
  - pmsignature

:input:
  Input files. When you want to use multiple files (usually divided by individual samples), please consult `データファイルが分かれている場合 <./data_common.html#suffix>`.

.. code-block:: bash

  # for single input file
  paplot mutation {unzip_path}/example/mutation_minimal/data.csv ./tmp mutation_minimal \
  --config_file {unzip_path}/example/mutation_minimal/paplot.cfg
  
  # for multiple input files, delimit them by comma
  paplot mutation \
  {unzip_path}/example/mutation_split_file/SAMPLE00.data.csv,{unzip_path}/example/mutation_split_file/SAMPLE01.data.csv \
  ./tmp mutation_split_file1 --config_file {unzip_path}/example/mutation_split_file/paplot.cfg

  # paplot also accept wilde card representation. In this case enclose the input by double quatations
  paplot mutation "{unzip_path}/example/mutation_split_file/*.csv" ./tmp mutation_split_file2 \
  --config_file {unzip_path}/example/mutation_split_file/paplot.cfg

:output_dir:
  Output directory path. See :ref:`2. 出力ディレクトリ <output>` for the detail of directory commponents.

:project_name:
  Project name (used as the title of output files).

.. _output:

---------------------
2. Output directory
---------------------

You will find the following directory structure:

.. code-block:: bash

  {output_dir}
    ├ {project_name}
    │   └ graph_*.html      <--- Each report
    │
    ├ js          <--- The next four directories are necessary to display HTML files, Do not remove them.
    ├ layout
    ├ lib
    ├ style
    │
    └ index.html             <--- Open this file in a web browser.


When you want to move the output, move the entire output directory.
For the usage of each report, please refre `HOW TO USE GRAPHS <./index.html#how-to-toc>`_.


.. _option:

------------------------
3. Options
------------------------

You can change the following items as options.

--config_file        Path to the configuration file. If not specified, then use default file.
--title              Title of the graph.
--ellipsis           Abbreviated name of the graph. It is used for the graph file name. (ex, graph_**ca**.html) It is convenient to set it when outputting multiple files to the same directory.
--overview           Outline of the graph (displayed in the index.html file).
--remarks            Text shown in the remark section of the index.html file (The default value is set at ([style] remarks) in the setting file.

The default values are as follows.

=============== =================== ============ ============================================= ==============
subcommand      title               ellipsis     overview                                      remarks
=============== =================== ============ ============================================= ==============
qc              QC graphs           qc           Quality Control of bam.                       None
ca              CA graphs           ca           Chromosomal Aberration.                       None
mutation        Mutation Matrix     mutation     Gene-sample mutational profiles.              None
signature       Signature           signature    Mutational Signatures.                        None
pmsignature     PMSignature         pmsignature  Express mutational signatures in pmsignature. None
=============== =================== ============ ============================================= ==============

.. |new| image:: image/tab_001.gif
