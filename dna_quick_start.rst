========================================
Quick Start DNA解析
========================================

#. Genomonのインストール
#. コマンドの実行
#. 結果ファイルを見てみましょう

1. Genomonのインストール
^^^^^^^^
| HGCスパコンには、Genomonで使用する解析ソフトウェア(BWA,Samtools等)が既にインストールされています(ANNOVARは別途インストールが必要です)。そのためご自身のユーザディレクトリにGenomonをインストールするだけで、解析をはじめることができます．
|
| → :doc:`install` にインストール方法を記載しました．
|

2. コマンドの実行
^^^^^^^^

テストサンプルを実行してインストールが正しくされたか確かめましょう．テストサンプルは用意されていますので、それを使用して実行してみましょう．

.. code-block:: bash
  
  # qloginする
  $qlogin
  # GenomonPipelineに移動
  $cd GenomonPipeline-v{バージョン}
  # 実行
  $./genomon_pipeline dna /home/w3varann/testdata/sample.csv {output_directory} genomon.cfg dna_task_param.cfg 
  # output_directoryには出力したいディレクトリを指定してください

3. 結果ファイルを見てみましょう
^^^^^^^^
