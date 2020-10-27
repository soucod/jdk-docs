JDK 1.1 Beta のインストールディレクトリ docs/guide/rmi/examples/stock 
にアプレットの作り方を示す例題があります。このアプレットはリモートオブ
ジェクトをエクスポートしてストックサーバーからの変動する株価を受け取り
ます。アプレットはサーバーからの通知を受け取るたびに株価を動的に表示し
ます。この例題で使うインタフェース/クラスは次の通りです。 

   - StockWatch はストックサーバーのためのリモートインタフェースです。 

   - StockNotify はストックオブザーバーのためのリモートインタフェースです。 

   - Stock は株価データを保持する直列化可能なオブジェクトです。 

   - StockServer (StockWatchを実装) は値を受け取るように設定されたリモー
     トオブジェクトに株価変動を通知します。 

   - StockApplet (StockNotifyを実装) はリモートオブジェクト（自分自身）
     をエクスポートし、StockServer へ株価変動の通知を登録し、株価変動
     通知を受け取るとそれを表示します。 

Solaris の場合：JDK 1.1 Beta リリースをダウンロードし、
docs/guide/rmi/examples/stock ディレクトリにある run スクリプトを実行
します。 このスクリプトは例題実行中にその実行内容をプリントします。ス
トックサーバーは自分のレジストリを作成しますから "rmiregistry" をスター
トさせる必要はありません。 run スクリプトは基本的に次のステップを実行
します。 

setenv CLASSPATH ../..:$CLASSPATH
javac -d ../.. *.java
rmic -d ../.. examples.stock.StockServer examples.stock.StockApplet
java examples.stock.StockServer &
appletviewer index.html 

注意: Appletviewer を実行する前に CLASSPATH を元の内容に（../..を含め
ずに）戻してかまいません。こうしておくとクラスは CLASSPATH からではな
くネットワークからダウンロードされます。 

Windows システムの場合：JDK 1.1 Beta リリースをダウンロードし,
docs/guide/rmi/examples/stock ディレクトリに移動して run.bat を実行し
ます。例題のビルドと実行中は各ステップの説明が表示されます。終了しまし
たらサーバープロセスのために作られたウィンドウを消してください。 
