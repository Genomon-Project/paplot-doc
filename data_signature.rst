******************************
Mutational Signature Report 
******************************

Here, we show how to generate Mutation Signature Report using sample data [*]_.

 .. [*] Sample data is equipped with the ``example`` directory of ``paplot`` directory.


.. :doc:`exec_signature` に従いデータを準備する場合、設定ファイルの変更は必要ありません。

.. _json:

==========================
1. Input data format
==========================

To generate Mutation Signature Report using paplot, json format input data is necessary.
The example (`example/signature_stack/data2.json`) is as follows:

.. code-block:: python
  :caption: Extracted from the example data (example/signature_stack/data2.json)

  {
    "signature":[
                  [ # signature 1
                    [0.0018,0.0003,0.0002,0.0005,0.0014,0.0008,0.0002,0.0007,0.0012,0.0003,0.0002,0.0004,0.0271,0.0107,0.0016,0.0145],  # C -> A
                    [0.0023,0.0007,0.0001,0.002,0.0027,0.0005,0.0004,0.0032,0.0007,0.0004,0.0001,0.0013,0.1546,0.0306,0.0055,0.1931],   # C -> G
                    [0.0043,0.0016,0.0027,0.0019,0.0096,0.0026,0.0046,0.0053,0.0045,0.0021,0.0034,0.0028,0.2612,0.0517,0.0284,0.1335],  # C -> T
                    [0.0012,0.0007,0.0004,0.0003,0.0003,0.0003,0,0,0.0003,0.0001,0.0003,0,0.0005,0.0001,0.0001,0.0002],                 # T -> A
                    [0.0008,0.0003,0.0008,0.0007,0.0002,0.0004,0.0009,0.0005,0.0004,0.0003,0.0006,0.0003,0.0003,0.0004,0.0002,0.0004],  # T -> C
                    [0.0001,0.0001,0.0001,0.0001,0,0.0001,0.0001,0,0.0001,0.0001,0.0009,0.0002,0.0001,0,0.0001,0.0005]                  # T -> G
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

**Elements of the input data for Mutation Signature Report**

:signature:
  | Probability masses for each mutation pattern.
  | Put the probability value for each mutation signature, substitution pattern (e.g., C > A) and context (e.g., TpCpA > TpApA).
  | The number of bases should be 3 or 5.
  | The number of contexts for each substitution pattern should be the same (16 and 256 when the numbers of bases are 3 and 5, respectively).

Since the number of bases is 3 in the above example data, probabilisty values for 16 contexts should be put down in the following order.

::

  ANA,ANC,ANG,ANT,CNA,CNA,CNG,CNT,GNA,GNC,GNG,GNT,TNA,TNA,TNG,TNT

When `base = 5`, 256 contexts values should be put down in the following order.

::

  AANAA,AANAC,AANAG,AANAT,AANCA,AANCC,AANCG,AANCT,AANGA,AANGC,AANGG,AANGT,AANTA,AANTC,AANTG,AANTT,
  ACNAA,ACNAC,ACNAG,ACNAT,ACNCA,ACNCC,ACNCG,ACNCT,ACNGA,ACNGC,ACNGG,ACNGT,ACNTA,ACNTC,ACNTG,ACNTT,
  AGNAA,AGNAC,AGNAG,AGNAT,AGNCA,AGNCC,AGNCG,AGNCT,AGNGA,AGNGC,AGNGG,AGNGT,AGNTA,AGNTC,AGNTG,AGNTT,
  ATNAA,ATNAC,ATNAG,ATNAT,ATNCA,ATNCC,ATNCG,ATNCT,ATNGA,ATNGC,ATNGG,ATNGT,ATNTA,ATNTC,ATNTG,ATNTT,
  CANAA,CANAC,CANAG,CANAT,CANCA,CANCC,CANCG,CANCT,CANGA,CANGC,CANGG,CANGT,CANTA,CANTC,CANTG,CANTT,
  CCNAA,CCNAC,CCNAG,CCNAT,CCNCA,CCNCC,CCNCG,CCNCT,CCNGA,CCNGC,CCNGG,CCNGT,CCNTA,CCNTC,CCNTG,CCNTT,
  CGNAA,CGNAC,CGNAG,CGNAT,CGNCA,CGNCC,CGNCG,CGNCT,CGNGA,CGNGC,CGNGG,CGNGT,CGNTA,CGNTC,CGNTG,CGNTT,
  CTNAA,CTNAC,CTNAG,CTNAT,CTNCA,CTNCC,CTNCG,CTNCT,CTNGA,CTNGC,CTNGG,CTNGT,CTNTA,CTNTC,CTNTG,CTNTT,
  GANAA,GANAC,GANAG,GANAT,GANCA,GANCC,GANCG,GANCT,GANGA,GANGC,GANGG,GANGT,GANTA,GANTC,GANTG,GANTT,
  GCNAA,GCNAC,GCNAG,GCNAT,GCNCA,GCNCC,GCNCG,GCNCT,GCNGA,GCNGC,GCNGG,GCNGT,GCNTA,GCNTC,GCNTG,GCNTT,
  GGNAA,GGNAC,GGNAG,GGNAT,GGNCA,GGNCC,GGNCG,GGNCT,GGNGA,GGNGC,GGNGG,GGNGT,GGNTA,GGNTC,GGNTG,GGNTT,
  GTNAA,GTNAC,GTNAG,GTNAT,GTNCA,GTNCC,GTNCG,GTNCT,GTNGA,GTNGC,GTNGG,GTNGT,GTNTA,GTNTC,GTNTG,GTNTT,
  TANAA,TANAC,TANAG,TANAT,TANCA,TANCC,TANCG,TANCT,TANGA,TANGC,TANGG,TANGT,TANTA,TANTC,TANTG,TANTT,
  TCNAA,TCNAC,TCNAG,TCNAT,TCNCA,TCNCC,TCNCG,TCNCT,TCNGA,TCNGC,TCNGG,TCNGT,TCNTA,TCNTC,TCNTG,TCNTT,
  TGNAA,TGNAC,TGNAG,TGNAT,TGNCA,TGNCC,TGNCG,TGNCT,TGNGA,TGNGC,TGNGG,TGNGT,TGNTA,TGNTC,TGNTG,TGNTT,
  TTNAA,TTNAC,TTNAG,TTNAT,TTNCA,TTNCC,TTNCG,TTNCT,TTNGA,TTNGC,TTNGG,TTNGT,TTNTA,TTNTC,TTNTG,TTNTT


**Signature contribution graph**

This graph is optional.

Signature contribution graph shows how much amount of mutations are associated with each mutation signature.
When *id*, *mutation* and *mutation_count* are set in the input json file,
then signature contribution graph are generated (`example <http://genomon-project.github.io/paplot/signature_stack/graph_stack2.html>`_).

:id:
  | List of samples. For each sample, sample indices are assigned (in this example, PD3851a=0、PD3890a=1、PD3904a=2 and so on). 

:mutation_count:
  | The number of mutations for each sample
  | In the above example, (the mutation number for PD3851a =4001, the mutation number for PD3890a = 7174 and so on).

:mutation:
  | Contribution ratio of each mutation signature to each sample ([sample index, signature index, value]).
  |
  | The indice for mutation signature (signature index) are assigned in the listed order in the signature key.
  | In the above example, (signature1 = 0, signature2 = 1, signature3 = 2).

.. note::

  The keys in the input json file can be modified by changing contents in the [result_format_signature] section of the configuration file.

  .. code-block:: cfg
    :caption:  paplot/example/signature_stack/paplot.cfg
    
    [result_format_signature]
    # the keys in input json file
    key_signature = signature
    key_id = id
    key_mutation = mutation
    key_mutation_count = mutation_count
            
.. note::

  How to validate json file format
 
  paplot using `json` python package. When loading the input file using load function from json package, then the input file is valid json format.

  Example, when the file fine name is "data2.json".

  .. code-block:: shell
  
    $ python
    >>> import json
    >>> json.load(open("data2.json"))
  
----

.. _sig_minimal:

==========================
2. Minimal dataset  
==========================

| `View the report generated in this section <http://genomon-project.github.io/paplot/signature_minimal/graph_signature_minimal2.html>`_ 
| `View the input data used in this section <https://github.com/Genomon-Project/paplot/blob/master/example/signature_minimal>`_ 
| `Download the input data used in this section <https://github.com/Genomon-Project/paplot/blob/master/example/signature_minimal.zip?raw=true>`_ 

For the format of input data, please refer to :ref:`Here <json>`.

.. :doc:`exec_signature` の手順でデータの準備を行う場合、設定ファイルの変更は必要ありません。

Input data file (the number of mutation signature is 2)

.. code-block:: python
  :caption: example/signature_minimal/data.json
  
  {
    "signature":[
      # signature 1
      [ 
        [0.0021,0.0006,0.0002,0.0007,0.0017,0.001,0.0003,0.0009,0.0014,0.0006,0.0003,0.0006,0.027,0.0108,0.0016,0.0147],
        [0.0025,0.0009,0.0002,0.0022,0.0029,0.0007,0.0005,0.0034,0.0009,0.0006,0.0002,0.0014,0.1504,0.0301,0.0053,0.1884],
        [0.0046,0.0018,0.0031,0.0021,0.0097,0.0029,0.0049,0.0055,0.0047,0.0024,0.0037,0.003,0.2557,0.0513,0.0286,0.1312],
        [0.0014,0.0009,0.0007,0.0006,0.0004,0.0005,0.0003,0.0003,0.0004,0.0003,0.0005,0.0002,0.0008,0.0003,0.0003,0.0005],
        [0.001,0.0004,0.0011,0.001,0.0003,0.0007,0.0012,0.0008,0.0006,0.0004,0.0007,0.0005,0.0005,0.0007,0.0004,0.0007],
        [0.0003,0.0003,0.0003,0.0003,0.0001,0.0003,0.0003,0.0003,0.0002,0.0002,0.0011,0.0004,0.0003,0.0002,0.0003,0.0009]
      ],
      # signature 2
      [ 
        [0.022,0.0183,0.0028,0.0171,0.0192,0.0148,0.0026,0.0157,0.0143,0.0108,0.0018,0.0116,0.0181,0.016,0.0021,0.0246],
        [0.0133,0.0088,0.0037,0.0136,0.0095,0.008,0.003,0.0131,0.0065,0.0063,0.0016,0.0095,0.0044,0.0135,0.0016,0.0171],
        [0.0195,0.0098,0.0283,0.0159,0.0138,0.0112,0.0156,0.0183,0.0128,0.0108,0.0186,0.0127,0,0.0146,0.0095,0.0115],
        [0.0095,0.0085,0.0102,0.0155,0.0077,0.0102,0.0096,0.0135,0.0054,0.0052,0.0058,0.0089,0.0145,0.0076,0.0058,0.016],
        [0.0192,0.0089,0.0135,0.0198,0.0089,0.0113,0.0092,0.0117,0.0092,0.0063,0.0064,0.01,0.0107,0.0096,0.0061,0.0123],
        [0.0059,0.0028,0.0068,0.0063,0.0039,0.0044,0.0076,0.0101,0.004,0.0028,0.007,0.0064,0.006,0.0046,0.008,0.0132]
      ]
    ]
  }

Configuration file

.. code-block:: cfg
  :caption: example/signature_minimal/paplot.cfg
  
  [signature]
  tooltip_format_signature_title = {sig}
  tooltip_format_signature_partial = {route}: {#sum_item_value:6.2}
  
  signature_y_max = -1
  
  alt_color_CtoA = #1BBDEB
  alt_color_CtoG = #211D1E
  alt_color_CtoT = #E62623
  alt_color_TtoA = #CFCFCF
  alt_color_TtoC = #ACD577
  alt_color_TtoG = #EDC7C4
  
  [result_format_signature]
  format = json
  background = False
  key_signature = signature

Execute ``paplot``.

.. code-block:: bash

  paplot signature signature_minimal/data.json ./tmp signature_minimal \
  --config_file ./signature_minimal/paplot.cfg


Then the report is generated in the `tmp` directory.

Here, the file name (`graph_signature2.html`) are determined by the number of mutation signatures (interpreted automatically from the input data).

::

  ./tmp
    ┗ signature_minimal
        ┗ graph_signature2.html

.. _data_signature_multi:

----

.. _sig_mclass:

=================================================================
3. Mutation signature with multiple variosu number of signatures
=================================================================

| View the report generated in this section 

 - `signature 2 <http://genomon-project.github.io/paplot/signature_multi_class/graph_multi_class2.html>`_ 
 - `signature 3 <http://genomon-project.github.io/paplot/signature_multi_class/graph_multi_class3.html>`_ 
 - `signature 4 <http://genomon-project.github.io/paplot/signature_multi_class/graph_multi_class4.html>`_ 
 - `signature 5 <http://genomon-project.github.io/paplot/signature_multi_class/graph_multi_class5.html>`_ 
 - `signature 6 <http://genomon-project.github.io/paplot/signature_multi_class/graph_multi_class6.html>`_ 

| `View the input data used in this section <https://github.com/Genomon-Project/paplot/blob/master/example/signature_multi_class>`_ 
| `Download the input data used in this section <https://github.com/Genomon-Project/paplot/blob/master/example/signature_multi_class.zip?raw=true>`_ 

For the format of input data, please refer to :ref:`Here <json>`.

.. :doc:`exec_signature` の手順でデータの準備を行う場合、設定ファイルの変更は必要ありません。ここでは paplot コマンドを中心に解説します。

When generating Mutation Signature Report with various number of signatures,
the input data for each signature number and configuration file are necessary.

In this example dataset, following files are prepared.

::

  example/signature_multi_class/

     # Input data files
    ┣ data2.json  # signature num = 2
    ┣ data3.json  # signature num = 3
    ┣ data4.json  # signature num = 4
    ┣ data5.json  # signature num = 5
    ┣ data6.json  # signature num = 6

     # Configuration file 
    ┗ paplot.cfg

Execute ``paplot`` for each mutation signature number.

.. code-block:: bash

  paplot signature signature_multi_class/data2.json ./tmp signature_multi_class \
  --config_file ./signature_multi_class/paplot.cfg

  paplot signature signature_multi_class/data3.json ./tmp signature_multi_class \
  --config_file ./signature_multi_class/paplot.cfg

  paplot signature signature_multi_class/data4.json ./tmp signature_multi_class \
  --config_file ./signature_multi_class/paplot.cfg

  paplot signature signature_multi_class/data5.json ./tmp signature_multi_class \
  --config_file ./signature_multi_class/paplot.cfg

  paplot signature signature_multi_class/data6.json ./tmp signature_multi_class \
  --config_file ./signature_multi_class/paplot.cfg

Or execute the following batch command.

.. code-block:: bash

  paplot "signature signature_multi_class/data*.json" ./tmp signature_multi_class \
  --config_file ./signature_multi_class/paplot.cfg

Then the report is generated in the `tmp` directory.

Here, the file name (`graph_signature2.html`) are determined by the number of mutation signatures (interpreted automatically from the input data).

::

  ./tmp
    ┗ signature_multi_class
        ┣ graph_signature2.html
        ┣ graph_signature3.html
        ┣ graph_signature4.html
        ┣ graph_signature5.html
        ┗ graph_signature6.html

----

.. _sig_stack:

================================
4. Signature contribution graph
================================

| View the report generated in this section 

 - `signature 2 <http://genomon-project.github.io/paplot/signature_stack/graph_stack2.html>`_ 
 - `signature 3 <http://genomon-project.github.io/paplot/signature_stack/graph_stack3.html>`_ 
 - `signature 4 <http://genomon-project.github.io/paplot/signature_stack/graph_stack4.html>`_ 
 - `signature 5 <http://genomon-project.github.io/paplot/signature_stack/graph_stack5.html>`_ 
 - `signature 6 <http://genomon-project.github.io/paplot/signature_stack/graph_stack6.html>`_ 

| `View the input data used in this section <https://github.com/Genomon-Project/paplot/blob/master/example/signature_stack>`_ 
| `Download the input data used in this section <https://github.com/Genomon-Project/paplot/blob/master/example/signature_stack.zip?raw=true>`_ 

Here, we add a signature contribution graph.

.. レポートに変異の内訳グラフを追加します。 :ref:`こちら <json_full>` で解説に使用しているデータであり、:doc:`exec_signature` によりデータの準備を行う場合に出力されるデータです。

For the format of input data, please refer to :ref:`here <json>`.

For generating report with various signature numbers, please refer to :ref:`here <sig_mclass>`.

.. |new| image:: image/tab_001.gif
