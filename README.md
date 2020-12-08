# OracleのSequence相当の機能を実装するサンプル

連番を生成する関数（$Increment）を使用して連番を自動生成する

## ファイル一覧
- SampleSequencer.xml	実行に必要なクラス、ルーチンを含むプロジェクトファイル。
- readme.md		このファイル

## セットアップ

### プロジェクトファイルのインポート

スタジオで適当なネームスペースにSampleSequencer.xmlをインポート・コンパイルします。

## サンプルの実行

### 実行内容

Init()メソッドで初期化を実行し、SQLのSelect文でNextValue及びCurrValueを選択します。

## ターミナルでの実行例

```
USER>do ##class(Sample.Sequencer).Init()
 
12/26/2013 12:29:38 に修飾子 'ck' でコンパイルを開始しました。
クラスのコンパイル中 Sample.Sequencer
テーブルのコンパイル中 Sample.Sequencer
ルーチンのコンパイル中 Sample.Sequencer.1
コンパイルが正常に終了しました (所要時間: 0.106秒)。
 
USER>do $SYSTEM.SQL.Shell()
SQL Command Line Shell
----------------------------------------------------
 
The command prefix is currently set to: <<nothing>>.
Enter q to quit, ? for help.
USER>>select NextValue from Sample.Sequencer
1.      select NextValue from Sample.Sequencer
 
NextValue
1
 
1 Rows(s) Affected
statement prepare time: 0.0855s, elapsed execute time: 0.0003s.
---------------------------------------------------------------------------
USER>>select NextValue from Sample.Sequencer
2.      select NextValue from Sample.Sequencer
 
NextValue
2
 
1 Rows(s) Affected
statement prepare time: 0.0002s, elapsed execute time: 0.0002s.
---------------------------------------------------------------------------
USER>>select CurrValue from Sample.Sequencer
3.      select CurrValue from Sample.Sequencer
 
CurrValue
2
 
1 Rows(s) Affected
statement prepare time: 0.0828s, elapsed execute time: 0.0002s.
---------------------------------------------------------------------------
USER>>select * from Sample.Sequencer
4.      select * from Sample.Sequencer
 
ID      CurrValue       NextValue
1       2       3
 
1 Rows(s) Affected
statement prepare time: 0.0879s, elapsed execute time: 0.0002s.
---------------------------------------------------------------------------
USER>>q
 
USER>
```
