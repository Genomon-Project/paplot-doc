**********************************************
Execution method (signature) |new|
**********************************************

This section explains how to prepare data when using `pmsignature <https://github.com/friend1ws/pmsignature/>`_ .

.. note::

  | Before execution, it is necessary to build R environment and install pmsignature and related packages.
  | Please refer to `pmsignature <https://github.com/friend1ws/pmsignature/>`_ for detailed explanation of installation and execution commands.
  |
  | When signature analysis is performed using another tool, please separately prepare json file conforming to :ref:`specification <json_full>`.

1. run pmsignature
-----------------------------

Run pmsignature with option ``type="full"`` and save parameters to `.Rdata` file.

In this example, sample data of pmsignature is used.

.. code-block:: R

  library(pmsignature)
  
  # use sample data
  inputFile <- system.file("extdata/Nik_Zainal_2012.mutationPositionFormat.txt.gz", package="pmsignature")
  G <- readMPFile(inputFile, numBases = 3, type = "full", trDir = FALSE)
  
  # use background
  BG_prob <- readBGFile(G)
  
  Param <- getPMSignature(G, K = 3, BG = BG_prob)
  Boot <- bootPMSignature(G, Param0 = Param, bootNum = 100, BG = BG_prob)
  
  # save .Rdata
  resultForSave <- list(Param, Boot)
  save(resultForSave, file="pmsignature_full3.Rdata")

2. Convert result file for use with paplot
-----------------------------------------------------

Convert the "pmsignature_full3.Rdata" file created in section 1 to json format so that it can be read by paplot.

We are preparing the conversion script, please download the latest version from the below and unzip it to the appropriate place.
Installation is not necessary.

https://github.com/Genomon-Project/genomon_Rscripts/releases

Pass arguments in order of input file, file name you want to output.

.. code-block:: bash

  R --vanilla --slave --args ./pmsignature_full3.Rdata ./pmsignature_full3.json < {path to genomon_Rscripts}/pmsignature/convert_toJson_full.R


3. Run paplot
-----------------------------

Execute paplot using "pmsignature_full3.json" file created in section 2. If you execute in the above method, you do not need to change the config file.

.. note::

  If you do not use background, please change the background of the config file to False.

`paplot signature pmsignature_full3.Rdata ./temp signature_test`


.. _json_full:

[Supplement] json format
-----------------------------

| Open the sample data `example/signature/Nik_Zainal_2012.full.3.json` with a text editor, it looks as follows.
| (Some are omitted because it is long)
|

.. code-block:: python

  {
    "signature":[
                  [ # signature 1
                    [0.0018,0.0003,0.0002,0.0005,0.0014,0.0008,0.0002,0.0007,0.0012,0.0003,0.0002,0.0004,0.0271,0.0107,0.0016,0.0145],  # C > A
                    [0.0023,0.0007,0.0001,0.002,0.0027,0.0005,0.0004,0.0032,0.0007,0.0004,0.0001,0.0013,0.1546,0.0306,0.0055,0.1931],   # C > G
                    [0.0043,0.0016,0.0027,0.0019,0.0096,0.0026,0.0046,0.0053,0.0045,0.0021,0.0034,0.0028,0.2612,0.0517,0.0284,0.1335],  # C > T
                    [0.0012,0.0007,0.0004,0.0003,0.0003,0.0003,0,0,0.0003,0.0001,0.0003,0,0.0005,0.0001,0.0001,0.0002],                 # T > A
                    [0.0008,0.0003,0.0008,0.0007,0.0002,0.0004,0.0009,0.0005,0.0004,0.0003,0.0006,0.0003,0.0003,0.0004,0.0002,0.0004],  # T > C
                    [0.0001,0.0001,0.0001,0.0001,0,0.0001,0.0001,0,0.0001,0.0001,0.0009,0.0002,0.0001,0,0.0001,0.0005]                  # T > G
                  ],
                  [ # signature 2
                    [0.0266,0.0222,0.0026,0.02,0.0205,0.0145,0.0012,0.0155,0.0155,0.0094,0.0009,0.011,0.0224,0.0177,0.0019,0.0307],
                    [0.0127,0.0079,0.0035,0.0145,0.0058,0.0048,0.0015,0.0115,0.0034,0.0032,0,0.0071,0.0047,0.0145,0.0006,0.0246],
                    [0.0232,0.0099,0.042,0.0184,0.014,0.0108,0.0219,0.02,0.0137,0.0102,0.0264,0.0128,0.0048,0.0186,0.0153,0.0165],
                    [0.0096,0.0084,0.0094,0.0175,0.0075,0.0076,0.0046,0.0123,0.0044,0.0035,0.0028,0.008,0.0176,0.0047,0.0031,0.0139],
                    [0.0245,0.0087,0.0144,0.0235,0.0098,0.0096,0.0051,0.0102,0.0105,0.0053,0.0042,0.0108,0.0114,0.0081,0.0038,0.0098],
                    [0.0046,0.0006,0.0036,0.0035,0.0025,0.0009,0.0028,0.0082,0.0023,0.0005,0.004,0.0048,0.0041,0.0012,0.0056,0.0104]
                  ]
                ],
    "id":["PD3851a","PD3890a","PD3904a"],
    "mutation":[[0,0,0.0594],[0,1,0.7677],[0,2,0.1727],[1,0,0.1474],[1,1,0.4064],[1,2,0.4461]],
    "mutation_count":[4001,7174,5804]
  }

**signature drawing data**

:signature:
  | The value of each bar of the signature.
  | For each signature, describe the value for each change pattern (C> A etc.).
  | The number of change patterns can not be changed.
  | Only one of 3 or 5 can be set as the number of base.

Since base = 3 in this example, write 16 case values in the following order. (R=Reference)

::

  ARA,ARC,ARG,ART,CRA,CRA,CRG,CRT,GRA,GRC,GRG,GRT,TRA,TRA,TRG,TRT

If base = 5, 256 cases of description are required in the following order. (R=Reference) 

::

  AARAA,AARAC,AARAG,AARAT,AARCA,AARCC,AARCG,AARCT,AARGA,AARGC,AARGG,AARGT,AARTA,AARTC,AARTG,AARTT,
  ACRAA,ACRAC,ACRAG,ACRAT,ACRCA,ACRCC,ACRCG,ACRCT,ACRGA,ACRGC,ACRGG,ACRGT,ACRTA,ACRTC,ACRTG,ACRTT,
  AGRAA,AGRAC,AGRAG,AGRAT,AGRCA,AGRCC,AGRCG,AGRCT,AGRGA,AGRGC,AGRGG,AGRGT,AGRTA,AGRTC,AGRTG,AGRTT,
  ATRAA,ATRAC,ATRAG,ATRAT,ATRCA,ATRCC,ATRCG,ATRCT,ATRGA,ATRGC,ATRGG,ATRGT,ATRTA,ATRTC,ATRTG,ATRTT,
  CARAA,CARAC,CARAG,CARAT,CARCA,CARCC,CARCG,CARCT,CARGA,CARGC,CARGG,CARGT,CARTA,CARTC,CARTG,CARTT,
  CCRAA,CCRAC,CCRAG,CCRAT,CCRCA,CCRCC,CCRCG,CCRCT,CCRGA,CCRGC,CCRGG,CCRGT,CCRTA,CCRTC,CCRTG,CCRTT,
  CGRAA,CGRAC,CGRAG,CGRAT,CGRCA,CGRCC,CGRCG,CGRCT,CGRGA,CGRGC,CGRGG,CGRGT,CGRTA,CGRTC,CGRTG,CGRTT,
  CTRAA,CTRAC,CTRAG,CTRAT,CTRCA,CTRCC,CTRCG,CTRCT,CTRGA,CTRGC,CTRGG,CTRGT,CTRTA,CTRTC,CTRTG,CTRTT,
  GARAA,GARAC,GARAG,GARAT,GARCA,GARCC,GARCG,GARCT,GARGA,GARGC,GARGG,GARGT,GARTA,GARTC,GARTG,GARTT,
  GCRAA,GCRAC,GCRAG,GCRAT,GCRCA,GCRCC,GCRCG,GCRCT,GCRGA,GCRGC,GCRGG,GCRGT,GCRTA,GCRTC,GCRTG,GCRTT,
  GGRAA,GGRAC,GGRAG,GGRAT,GGRCA,GGRCC,GGRCG,GGRCT,GGRGA,GGRGC,GGRGG,GGRGT,GGRTA,GGRTC,GGRTG,GGRTT,
  GTRAA,GTRAC,GTRAG,GTRAT,GTRCA,GTRCC,GTRCG,GTRCT,GTRGA,GTRGC,GTRGG,GTRGT,GTRTA,GTRTC,GTRTG,GTRTT,
  TARAA,TARAC,TARAG,TARAT,TARCA,TARCC,TARCG,TARCT,TARGA,TARGC,TARGG,TARGT,TARTA,TARTC,TARTG,TARTT,
  TCRAA,TCRAC,TCRAG,TCRAT,TCRCA,TCRCC,TCRCG,TCRCT,TCRGA,TCRGC,TCRGG,TCRGT,TCRTA,TCRTC,TCRTG,TCRTT,
  TGRAA,TGRAC,TGRAG,TGRAT,TGRCA,TGRCC,TGRCG,TGRCT,TGRGA,TGRGC,TGRGG,TGRGT,TGRTA,TGRTC,TGRTG,TGRTT,
  TTRAA,TTRAC,TTRAG,TTRAT,TTRCA,TTRCC,TTRCG,TTRCT,TTRGA,TTRGC,TTRGG,TTRGT,TTRTA,TTRTC,TTRTG,TTRTT

**Stack graph drawing data**

:id:
  | Sample name list.

:mutation_count:
  | Number of mutations per sample.
  | In the case of the above example, mutation number of PD3851a=4001, mutation number of PD3890a=7174, mutation number of PD3904a=5804.

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

  The key name can be changed. If you change the key name, please change the setting file ([result_format_signature] key_*).

.. note::

  For the strictness of format as json, paplot uses python's json package, so you can read it with the following command.

  File verification example using python json package (When the file name is "Nik_Zainal_2012.full.3.json")

  .. code-block:: shell
  
    $ python
    >>> import json
    >>> json.load(open("Nik_Zainal_2012.full.3.json"))
  

.. |new| image:: image/tab_001.gif
