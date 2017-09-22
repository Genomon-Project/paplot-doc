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
  The type of report to generate. Select from the following:
  
  - qc
  - ca
  - mutation
  - signature
  - pmsignature

:input:
  Input files. If you wish to process multiple files (usually divided by individual samples), please refer to `Processing multiple input files <./data_common.html#suffix>`_.

.. code-block:: bash

  # for single input file
  paplot mutation {unzip_path}/example/mutation_minimal/data.csv ./tmp mutation_minimal \
  --config_file {unzip_path}/example/mutation_minimal/paplot.cfg
  
  # for multiple input files, delimit them by comma
  paplot mutation \
  {unzip_path}/example/mutation_split_file/SAMPLE00.data.csv,{unzip_path}/example/mutation_split_file/SAMPLE01.data.csv \
  ./tmp mutation_split_file1 --config_file {unzip_path}/example/mutation_split_file/paplot.cfg

  # paplot also accept wild card representation. In this case enclose the input by double quotations
  paplot mutation "{unzip_path}/example/mutation_split_file/*.csv" ./tmp mutation_split_file2 \
  --config_file {unzip_path}/example/mutation_split_file/paplot.cfg

:output_dir:
  Output directory path. Refer :ref:`Output directory <output>` for the details of the directory components.

:project_name:
  Project name (used as the title of the output files).

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


If you wish to move the output, move the entire output directory.
For the usage of each report, please refer to `HOW TO USE GRAPHS <./index.html#how-to-toc>`_.


.. _option:

------------------------
3. Options
------------------------

You can add the following optional arguments:

--config_file        Path to the configuration file. If it is not specified, the default file is used.
--title              Title of the graph.
--ellipsis           Abbreviated name of the graph used for file names (e.g., graph_**ca**.html). It may be convenient when outputting multiple files to the same directory.
--overview           Outline of the graph (displayed in the index.html file).
--remarks            Text displayed in the remark section of the index.html file (the default value is set at ( ``[style]`` section's ``remarks`` option) in the configuration file.

The default values are as follows:

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
