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
  These are sub-commands of paplot. Choose any one from among these.
  
  - qc
  - ca
  - mutation
  - signature
  - pmsignature

:input:
  Input files. Multiple files can be specified with wild-card (``*``, ``?``) . In this case, mark ``"``  at the beginning and end.

.. code-block:: bash

  # Only 1 file
  pa_plot qc example/qc/SAMPLE1.qc ./test multi1 --config_file example/example.cfg
  
  # Multiple files (separeted by , )
  pa_plot qc "example/qc/SAMPLE1.qc.csv,example/qc/SAMPLE2.qc.csv" ./test multi1 --config_file example/example.cfg
  
  # Multiple files (use * )
  pa_plot qc "example/qc/*.csv" ./multi multi1 --config_file example/example.cfg


:output_dir:
  Output directory path. See :ref:`2. Output Directory <output>`, for explain of directory components.

:project_name:
  Project name. For use title of output files.




**optional**

--config_file        Path of configuration file. If not specified, then use default file.
--remarks            The text to be output to the remarks column of index.html. If not specified, use the value of a configuration file.
-h                   Displays the help.
--version            Displays the version.

.. _output:

------------------------
2. Command options
------------------------

You can change the following items as options.

--config_file        Path of configuration file. If not specified, then use default file.
--remarks            The text to be output to the remarks column of index.html. If not specified, use the value of a configuration file.
-h                   Displays the help.
--version            Displays the version.

The default values ​​are as follows.

=============== =================== ============ ============================================= ==============
subcommand      title               ellipsis     overview                                      remarks
=============== =================== ============ ============================================= ==============
qc              QC graphs           qc           Quality Control of bam.                       なし
ca              CA graphs           ca           Chromosomal Aberration.                       なし
mutation        Mutation matrix     mutation     Gene-sample mutational profiles.              なし
signature       Signature           signature    Mutational signatures.                        なし
pmsignature     PMSignature         pmsignature  Express mutational signatures in pmsignature. なし
=============== =================== ============ ============================================= ==============

.. _output:

---------------------
3. Output directory
---------------------

In the location specified in the ``output_dir`` option to output the file with the following configuration.

.. code-block:: bash

  {output_dir}
    ├ {project_name}
    │   └ graph_*.html      <--- Graphs.
    │
    ├ js          <--- Don't delete. this 4 directories are required to display the HTML file.
    ├ layout
    ├ lib
    ├ style
    |
    └ index.html             <--- Please open the file in a web browser.


If you want to move the output files, please move each `` {output_dir} ``.

Method of operation of the output file, please refer to the `how to use graphs <./index.html#how-to-toc>`_ .

.. |new| image:: image/tab_001.gif