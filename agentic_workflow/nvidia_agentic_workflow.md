
# LLM を使った AI エージェントの構築

## 概要

このワークショップでは、LLM (大規模言語モデル) を利用した AI エージェントの構築を行います。AI エージェントは、チャットの入力を受け付けて、LLM が内容を判断し、出力を生成するという点においては、[基本となるチャットボット](../basic_chatbot/nvidia_chatbot.md)と大枠は同じです。AI エージェントが追加で行えることは、ユーザがツールを複数与えれば、それらのツールを必要に応じて使って出力を生成することです。

もう一つのテンプレートである [RAG のテンプレート](../rag_chatbot/nvidia_rag.md)でみたように、ベクトルデータベースを使った RAG は、チャットボットの出力の精度を高めるうえで有用でした。ベクトルデータベースや、それ以外のデータソースなどをツールとして与えて、AI エージェントが必要に応じて利用することができれば、ユーザがこと細かにツールの指定をしなくとも精度を高めることができる可能性があります。これが AI エージェントを利用する大きなメリットです。

この AI エージェントの基本のテンプレートでは、URL を指定してWebページをダウンロードするツール、電卓のツールを与えます。例えば、URL を含めて質問すれば、AI エージェントは URL からダウンロードするツールを自動的に利用して、回答の生成に役立てるでしょう。

### 事前に準備するもの

- DataStax のアカウント
- NVIDIA の LLM にアクセスするための API キー

## テンプレートを利用したフローの作成


[Workshopの準備](https://github.com/harusametime/langflow-workshop/blob/main/README.md#workshop-%E3%81%AE%E6%BA%96%E5%82%99) に従って、Langflow の画面を開きます。画面の右側に New Flow のボタンがあるのでクリックします。


<p align="center">
<img src="images/create_agent_workflow.png" width="60%" border =1/>
</p>

ボタンをクリックするといくつかのテンプレートが表示されます。今回は LLM を使った AI エージェントのテンプレートとして、Simple Agent を選択します。


## AI エージェントフローの修正

### AI エージェントフローの全体像

概要で説明したように、この AI エージェントフローは、チャットの入力、LLM を利用した Agent、チャットの出力を基本的なフローとして、URL からファイルをダウンロードするツールと、電卓の Calculator ツールを Agent に与えています。以下の図に示すように、URL と Calculator のツールが Agent の Tools に接続されていることがわかります。

<p align="center">
<img src="images/agent_flow.png" width="60%" border =1/>
</p>

### AI エージェントの修正

Agent を修正して NVIDIA のモデルで実行できるようにします。
- Model Provider: `NVIDIA`
- Model Name: `nvidia/nemotron-mini-4b-instruct`
- NVIDIA API KEY: 作成した NVIDIA API Key を指定 ((こちら)[https://github.com/harusametime/langflow-workshop/blob/main/basic_chatbot/nvidia_chatbot.md#nvidia-api-key-%E3%81%AE%E8%A8%AD%E5%AE%9A]を参照)

<p align="center">
<img src="images/agent_config.png" width="30%" border =1/>
</p>

## Playground を使った AI エージェントのテスト
右上の Playground のボタンから Playground を起動してテストしてみましょう。


