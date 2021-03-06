---

copyright:
  years: 2016

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# {{site.data.keyword.iot_short_notm}} Starter 概説
{: #gettingstartedtemplate}
<!-- Provide and appropriate ID above -->
*最終更新日: 2016 年 6 月 27 日*
{: .last-updated}

{{site.data.keyword.iot_short_notm}} Starter ボイラープレートを使用して、{{site.data.keyword.iot_full}} を開始します。スターターを使用すると、デバイスのシミュレート、カードの作成、およびデータの生成を迅速に実行することができ、{{site.data.keyword.iot_short_notm}} ダッシュボードでデータの分析や表示をすぐに開始できます。
{: shortdesc}

スターターは、以下のサービスのデプロイおよび接続を自動的に行います。

{{site.data.keyword.iot_short_notm}} - このプラットフォームは、ゲートウェイ・デバイス、デバイス管理、および強力なアプリケーション・アクセスを含む、用途の広い IoT ツールキットを提供します。{{site.data.keyword.iot_short_notm}} を使用して、接続されたデバイスのデータを収集し、組織からのリアルタイムのデータに基づいて分析を実行できます。

{{site.data.keyword.sdk4nodefull}} - Node-RED を実行するランタイム環境を作成します。

{{site.data.keyword.cloudantfull}} - Node-RED がメタデータを保管するデータベース。

## {{site.data.keyword.iot_short_notm}} の概要
{: #about_iotplatform}
{{site.data.keyword.iot_short_notm}} には、IoT デバイスおよびデータへの強力なアプリケーション・アクセス機能があり、分析アプリケーション、可視化ダッシュボード、およびモバイル IoT アプリを素早く作成できます。
{{site.data.keyword.iot_short_notm}} を使用すると、強力なデバイス管理操作の実行、デバイス・データの保管とアクセス、および各種のデバイスおよびゲートウェイ・デバイスの接続が可能になります。{{site.data.keyword.iot_short_notm}} は、MQTT および TLS を使用して、ご使用のデバイスとの間のセキュア通信を実現します。

## Node-RED の概要
{: #about_nodered}
Node-RED は、ハードウェア・デバイス、API、およびオンライン・サービスを、新しい興味深い方法で接続するツールです。Node-RED を使用して、シミュレートされたサーモスタットを作成し、シミュレートされたデータを {{site.data.keyword.iot_short_notm}} サービスに送信することができます。また、{{site.data.keyword.iot_short_notm}} ダッシュボードにリアルタイムでデータを表示するためのカードを作成できます。詳細については、[Node-RED の資料](https://console.ng.bluemix.net/docs/starters/Node-RED/nodered.html#nodered)を参照してください。

## ナビゲート
{: #gettingaround}
以下のステップを実行する際に、ブラウザーで 3 つの異なるタブを使用します。
  1. *{{site.data.keyword.Bluemix_notm}} ダッシュボード* - {{site.data.keyword.Bluemix_notm}} ダッシュボードを使用して、デプロイメントの状態の確認、資料の参照、およびダッシュボードの起動を行います。
  2. *{{site.data.keyword.iot_short_notm}} ダッシュボード* - このダッシュボードは、このサービスの処理に使用します。このダッシュボードを使用して、デバイス・タイプの定義、デバイスの登録、着信するセンサー・データのモニター、データ可視化カードの作成、およびライブ・データ可視化の確認を行います。
  3. *Node-RED* - node.js Web アプリケーションとして実行して、デバイス・シミュレーター・フローの構成と実行、および {{site.data.keyword.iot_short_notm}} からのデータを処理するためのその他のフローの処理を行います。

## {{site.data.keyword.iot_short_notm}} でのシミュレートされたデバイスの定義
{: #definingsimdev}
次の手順で、デバイスを {{site.data.keyword.iot_short_notm}} に登録します。
  1.	{{site.data.keyword.Bluemix_notm}} で、デプロイされたアプリケーションの概要タブに移動します。
  2.	「接続」セクションまたはタブで、「{{site.data.keyword.iot_short_notm}}」ボックスをクリックします。
  3.	「ダッシュボードを起動」をクリックして、新しいブラウザー・ウィンドウで {{site.data.keyword.iot_short_notm}} ダッシュボードを開きます。
  4.	「デバイス」を選択します。
  5.	「デバイスの追加」をクリックします。
  6.	「デバイスの追加」ダイアログで、「デバイス・タイプの作成」をクリックします。
  7.	「デバイス・タイプの作成」ダイアログで、「デバイス・タイプの作成」をクリックします。
  8. デバイス・タイプの記述名と説明 (例えば、サーモスタット) を入力します。
  9.	「テンプレートの定義」はスキップします。
  10.	「メタデータ」はスキップします。
  11.	「作成」をクリックして、新しいデバイス・タイプを追加します。
  12.	「次へ」をクリックして、デバイスを追加します (「デバイス・タイプの選択」が事前選択されています)。
  13.	デバイス ID (例えば、LivingRoomThermo1) を入力します。
  14.	デバイス・メタデータの入力はスキップします。
  15.	「次へ」をクリックして、自動生成された認証トークンとともにデバイス接続を追加します。
  16.	サマリー情報が正しいことを確認し、「追加」をクリックして接続を追加します。
  17.	開いたデバイス情報ページで、以下のデバイス情報をコピーして保存します。
      -	組織 ID
      -	デバイス・タイプ
      -	デバイス ID
      - 認証方式
      - 認証トークン

**ヒント**: 組織 ID、デバイス・タイプ、およびデバイス ID は、Node-RED アプリケーションの構成を終了して接続を完成させるために、次のいくつかのステップで必要になります。

## Node-RED デバイス・シミュレーターの構成および実行
{: #confignodered}
Node-RED デバイス・シミュレーターを構成します。デバイス・シミュレーターを使用して、MQTT デバイス・メッセージを {{site.data.keyword.iot_short_notm}} に送信します。このデバイス・シミュレーターは、温度と湿度の情報を {{site.data.keyword.iot_short_notm}} に送信します。

1. Bluemix ダッシュボードで、**「アプリの表示」**を選択するか、リンク (例えば、http://myIoTApp.mybluemix.net) をクリックして、Node-RED を開きます。
2.	**「Node-RED フロー・エディターに移動 (Go to your Node-RED flow editor)」**をクリックして、エディターを開きます。
3.	「デバイス・シミュレーター」フロー内の {{site.data.keyword.iot_short_notm}} ノードへの青色の **「送信」**をダブルクリックします。
  1.	「認証 = Bluemix サービス」であることを確認します。
  2.	登録したデバイスから「デバイス・タイプ」を貼り付けます。
  3.	登録したデバイスから「デバイス ID」を貼り付けます。
  4.	「OK」をクリックします。
4.	Node-RED フロー・エディターの右上隅で、**「デプロイ」**をクリックします。
5.	「Node-RED 温度モニター」フローを構成します。
  1.	「デバイス・シミュレーター」フロー内の青色の「IBM IoT App In」ノードをダブルクリックします。
  2.	「認証」を「Bluemix サービス」に変更します。
  3.	「デバイス・タイプ」、「デバイス ID」、「イベント」、および「フォーマット」には「すべて」を選択します。
  4.	「OK」をクリックします。
6.	Node-RED フロー・エディターの右上隅で、**「デプロイ」**をクリックします。
7.	デバイス接続を検証します。
  1.	ブラウザーの別のタブまたはウィンドウで、{{site.data.keyword.iot_short_notm}} ダッシュボードに戻ります。
  2.	「デバイス」を選択して「LivingRoomThermo1」をクリックするか、これと異なる場合は、追加したデバイスの名前をクリックします。デバイス情報ページが開きます。このビューでは、デバイスの接続状況を確認できます。デバイスの状況は「切断済み」になっています。
  3.	Node-RED フロー・エディターに戻り、グレー表示の「送信データ」ノード上のボタンをクリックして、アセット・ペイロードを生成します。ペイロードには、以下のデータ・ポイントが含まれています。
  ```
  {"d":{"temp":15,"humidity":50,"location":{"longitude":-98.49,"latitude":29.42}}}
  ```
  4.	右側のペインのデバッグ・タブで、メッセージが作成されていることを確認します。
  5.	{{site.data.keyword.iot_short_notm}} デバイス情報ページで、デバイスから受信したのと同じデータ・ポイントが「センサー情報」セクションに表示されていることを確認します。

8.	サンプル IoT デバイスを {{site.data.keyword.iot_short_notm}} に接続して、デバイス・データを表示します。

## {{site.data.keyword.iot_short_notm}} でのライブ・データを表示するためのカードの作成
{: #createcards}
カードを作成するには、以下のタスクを実行します。

### 3 秒ごとにデータを自動生成
1. Node-RED タブで、「送信データ」ノードをダブルクリックします。
2.	「繰り返し間隔 (Repeat to Interval)」を「3 秒ごと (Every 3 seconds)」に設定します。
3.	デプロイします。

### ダッシュボードでの新規カードの作成
1. {{site.data.keyword.iot_short_notm}} ダッシュボードのブラウザー・タブに移動します。
2. 「ボード」を選択します。
3. 「新規ボードの作成 (Create New Board)」をクリックします。
4. ボードに名前 (「ホーム環境」など) を付けます。
5. 作成します。
6. 「新しいカードの追加」をクリックします (温度用)。
   1.	「デバイス」の下で、「リアルタイム・グラフ」を選択します。
   2.	カードのソース・データとして、デバイス「LivingRoomThermo1」にチェック・マークを付けて、「次へ」をクリックします。
   3. 新規データ・セットを接続します。
       - 名前: 温度
       - イベント: 更新
       - プロパティー: temp
       - タイプ: 浮動小数点
       - 単位: °C
       - 精度: 2
       - 最小: 0
       - 最大: 50
       - 次へ
  4. カードのプレビュー。
       - L を選択
       - 次へ
  5. カード情報。
       - タイトル: 温度
  6.	送信します。
  7.	温度カードがダッシュボードに表示され、ライブ温度データのグラフが示されます。
7.	「新しいカードの追加」をクリックします (湿度用)。
  1.	「デバイス」の下で、「詳細表示」を選択します。
  2.	「ゲージ」を選択します。
  3.	カードのソース・データとして、ご使用のデバイスにチェック・マークを付けて、「次へ」をクリックします。
  4.	新規データ・セットを接続します。
       -	名前: 湿度
       -	イベント: 更新
       -	プロパティー: humidity
       -	タイプ: 浮動小数点
       -	単位: 「% 相対湿度」
       -	精度: 1
       -	最小: 10
       -	最大: 95
       -	次へ
  5.	カードのプレビュー。
       -	設定
          -	下限しきい値: 40%、普通
          -	中間: 良好
          -	上限しきい値: 50% 、普通
       -	M を選択
       -	次へ
  6.	カード情報。
       -	タイトル: 湿度
  7.	送信します。
  8.	湿度カードがダッシュボードに表示され、ライブ湿度データを示すゲージが示されます。
8.	「新しいカードの追加」をクリックします (位置用)。
  1.	「デバイス」の下で、「詳細表示」を選択します。
  2.	「値」を選択します。
  3.	カードのソース・データとして、デバイス「LivingRoomThermo1」にチェック・マークを付けて、「次へ」をクリックします。
  4.	新規データ・セットを接続します。
       -	名前: 緯度
       -	イベント: 更新
       -	プロパティー: location.latitude
       -	タイプ: 浮動小数点
       -	単位: 「°N」
       -	精度: 2
       -	最小: -180
       -	最大: 180
  5. 新規データ・セットを接続します。
       -	名前: 経度
       -	イベント: 更新
       -	プロパティー: location.longitude
       -	タイプ: 浮動小数点
       -	単位: 「°E」
       -	精度: 2
       -	最小: -180
       -	最大: 180
       -  次へ
  6.	カードのプレビュー。
       -	L を選択
       -	次へ
  7.	カード情報。
       -	タイトル: 位置
  8.	送信します。
9.	Node-RED フローによって生成されるシミュレーター・データを使用したリアルタイムでの新規カードの更新を監視します。
**注**: Node-RED は、ユーザーが停止するまでデータの送信を続けます。
10.	Node-RED フロー・エディターで、「送信データ」ノードを「繰り返し: なし」に更新します。
11.	デプロイします。

## 次に行うこと
{: #whatsnext}
シミュレートされたデバイスが {{site.data.keyword.iot_short_notm}} にデータを送信するようになりましたので、引き続き IoT プロジェクト上で操作を繰り返すことができます。

1. [IoT レシピの検索](https://developer.ibm.com/recipes/?post_type=tutorials&s=watson+iot)を行って、 Raspberry Pi などの物理デバイスに接続し、データを {{site.data.keyword.iot_short_notm}} に送信します。
2. [サンプル node.js アプリケーションをデプロイして、デバイス・データを視覚化します。](https://www.bluemix.net/docs/services/IoT/visualizingdata_sample.html)
3.	Node-RED フロー・エディターをパスワード保護します。デフォルトでは、エディターは、任意のユーザーがアクセスしてフローを変更できる状態で開きます。エディターをパスワード保護するには、以下のタスクを実行します。
  1.	Bluemix ダッシュボードで、アプリケーションの「環境変数」ページを選択します。
  2.	次のユーザー定義の変数を追加します。
       -	NODE_RED_USERNAME - エディターを保護するためのユーザー名
       -	NODE_RED_PASSWORD - エディターを保護するためのパスワード
  3.	「保存」をクリックします。


# 関連リンク
{: #rellinks}

## チュートリアルおよびサンプル
{: #samples}
* [デバイスを接続するためのレシピ](https://developer.ibm.com/recipes/?post_type=tutorials&s=iot){:new_window}
* [{{site.data.keyword.iot_short}} Play 組織](https://play.internetofthings.ibmcloud.com/){:new_window}
* [Intel Galileo の {{site.data.keyword.iot_short}} への接続](https://developer.ibm.com/recipes/tutorials/connect-an-intel-galileo-to-the-internet-of-things-foundation-connect/){:new_window}
* [ARM&reg; mbed&trade; IoT Starter Kit の接続](https://developer.ibm.com/recipes/tutorials/arm-mbed-iot-starter-kit-part-1/){:new_window}
* [Raspberry Pi の {{site.data.keyword.iot_short}} への接続](https://developer.ibm.com/recipes/tutorials/raspberry-pi-4/){:new_window}

## API リファレンス
{: #api}
* [{{site.data.keyword.iot_short}} API の資料](https://docs.internetofthings.ibmcloud.com/swagger/v0002.html#/){:new_window}


## 関連リンク
{: #general}
* [{{site.data.keyword.iot_short_notm}} の資料](https://www.bluemix.net/docs/services/IoT/iotplatform_overview.html){:new_window}
* [{{site.data.keyword.sdk4nodefull}} スターターの資料](https://console.ng.bluemix.net/docs/starters/Node-RED/nodered.html){:new_window}
