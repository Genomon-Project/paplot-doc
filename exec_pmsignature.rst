**********************************************
Execution method (pmsignature) |new|
**********************************************

This section explains how to prepare data when using `pmsignature <https://github.com/friend1ws/pmsignature/>`_ .

.. note::

  | Before execution, it is necessary to build R environment and install pmsignature and related packages.
  | Please refer to `pmsignature <https://github.com/friend1ws/pmsignature/>`_ for detailed explanation of installation and execution commands.
  |
  | When signature analysis is performed using another tool, please separately prepare json file conforming to :ref:`specification <json_ind>`.

1. Run pmsignature
-----------------------------

Run pmsignature with option ``type="independent"`` (default) and save parameters to `.Rdata` file.

In this example, sample data of pmsignature is used.

.. code-block:: R

  library(pmsignature)
  
  # use sample data
  inputFile <- system.file("extdata/Nik_Zainal_2012.mutationPositionFormat.txt.gz", package="pmsignature")
  G <- readMPFile(inputFile, numBases = 5, trDir = TRUE)
  
  # use background
  BG_prob <- readBGFile(G)
  
  Param <- getPMSignature(G, K = 3, BG = BG_prob)
  Boot <- bootPMSignature(G, Param0 = Param, bootNum = 100, BG = BG_prob)
  
  # save .Rdata
  resultForSave <- list(Param, Boot)
  save(resultForSave, file="pmsignature_ind3.Rdata")

2. Convert result file for use with paplot
-----------------------------------------------------

Convert the "pmsignature_ind3.Rdata" file created in section 1 to json format so that it can be read by paplot.

We are preparing the conversion script, please download the latest version from the below and unzip it to the appropriate place.
Installation is not necessary.

https://github.com/Genomon-Project/genomon_Rscripts/releases

Pass arguments in order of input file, file name you want to output.

.. code-block:: bash

  R --vanilla --slave --args ./pmsignature_ind3.Rdata ./pmsignature_ind3.json < {path to genomon_Rscripts}/pmsignature/convert_toJson_ind.R


3. Run paplot
-----------------------------

Execute paplot using "pmsignature_ind3.json" file created in section 2. If you execute in the above method, you do not need to change the config file.

.. note::

  If you do not use background, please change the background of the config file to False.

`paplot signature pmsignature_ind3.Rdata ./temp signature_test`


.. _json_ind:

[Supplement] json format
-----------------------------

| Open the sample data `example/pmsignature/Nik_Zainal_2012.ind.3.json` with a text editor, it looks as follows.
| (Some are omitted because it is long)
|

.. code-block:: python

  {
    "ref":[
            [ # signature 1
              [0.338,0.15,0.183,0.327],  # ref1 (A,C,G,T)
              [0.362,0.191,0.177,0.267], # ref2 (A,C,G,T)
              [0,0.731,0,0.268],         # ref3 (A,C,G,T)
              [0.31,0.165,0.251,0.272],  # ref4 (A,C,G,T)
              [0.295,0.193,0.168,0.341]  # ref5 (A,C,G,T)
            ],
            [ # signature 2
              [0.179,0.414,0.084,0.321],
              [0.007,0.025,0.004,0.962],
              [0,0.999,0,0],
              [0.472,0.104,0.041,0.381],
              [0.277,0.175,0.284,0.262]
            ]
          ],
    "alt":[
            [ # signature 1
              [0,0,0,0],                 # altA (A,C,G,T)
              [0.194,0,0.091,0.445],     # altC (A,C,G,T)
              [0,0,0,0],                 # altG (A,C,G,T)
              [0.093,0.163,0.011,0]      # altT (A,C,G,T)
            ],
            [ # signature 2
              [0,0,0,0],
              [0.059,0,0.437,0.502],
              [0,0,0,0],
              [0,0,0,0]
            ]
          ],
    "strand":[
              [0.461,0.538],  # signature 1
              [0.512,0.487]   # signature 2
             ],
    "id":["PD3851a","PD3890a","PD3904a"],
    "mutation":[[0,0,0.535],[0,1,0.038],[0,2,0.426],[1,0,0.186],[1,1,0.156],[1,2,0.656]],
    "mutation_count":[702,2312,2096]
  }

.. image:: image/exec_pmsig1.PNG

**signature drawing data**

:ref:
  | The value of each reference of signature.
  | Write values ​​in order of signature, A, C, G, T for each reference. Since recalculation is done at drawing time, there is no need to sum up to 1.
  | In the case of the above example, number of base is 5. It can be changed if it is an odd number such as 3 or 7.

:alt:
  | The alt value of the signature.
  | We set 16 values ​​for each signature.
  | The size in the horizontal direction is set to 0 for altA and altG, since it follows the value of ACGT of ref3 (case of base = 5, ref2 if base = 3, ref4 if base = 7).

:strand:
  | The value of strand of signature.
  | For each signature, set plus and minus two values respectively.
  | If there is no strand, enter `[0,0]`.

**signature drawing data**

:id:
  | Sample name list

:mutation_count:
  | Number of mutations per sample.
  | In the case of the above example, mutation number of PD3851a=702, mutation number of PD3890a=2312, mutation number of =PD3904a2096.

:mutation:
  | Set the percentage for each sample and for each signature.
  | Write in order of [sample index, signature index, value].
  |
  | The index of the sample is counted from 0 in the order written in id.
  | In the case of the above example, PD3851a=0, PD3890a=1, PD3904a=2.
  |
  | The signature indexes are also counted from 0 in the order in which they are listed in ref.
  | When using background, count in signature 1, signature 2, ..., background.
  | In the case of the above example, signature1 = 0, signature2 = 1, background = 2.

.. note::

  The key name can be changed. If you change the key name, please change the setting file ([result_format_pmsignature] key_*).

.. note::

  For the strictness of format as json, paplot uses python's json package, so you can read it with the following command.

  File verification example using python json package (When the file name is "Nik_Zainal_2012.ind.3.json")

  .. code-block:: shell
  
    $ python
    >>> import json
    >>> json.load(open("Nik_Zainal_2012.ind.3.json"))
  

.. |new| image:: image/tab_001.gif
