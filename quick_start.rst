========================================
paplotによるグラフ作成
========================================

#. paplotのインストール
#. コマンドの実行
#. 結果ファイルの表示

1. paplotのインストール
^^^^^^^^
| HGCスパコンで使用される場合、事前に`qlogin`してください。
|

.. code-block:: bash
git clone https://github.com/Genomon-Project/paplot.git
cd paplot

python setup.py build install --user

| installの確認
| 以下を入力してください。
| 

.. code-block:: bash
pa_plot conf

| 以下が表示されればインストール成功です。
| 

.. code-block:: bash
******************************
hello genomon post analysis!!!
******************************
(そのあとにデフォルト設定の内容)


2. コマンドの実行
^^^^^^^^

テストサンプルが用意されていますので実行してみます．

.. code-block:: bash
cd {paplotをインストールしたディレクトリ}
pa_plot

# output_directoryには出力したいディレクトリを指定してください

3. 結果ファイルを見てみましょう
^^^^^^^^
