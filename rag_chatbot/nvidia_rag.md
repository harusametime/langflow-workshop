# LLM を使った RAG チャットボットの構築

## 概要

このワークショップでは、LLM (大規模言語モデル) とベクトルデータベースを利用して RAG (検索拡張生成; Retrieval Augmented Generation) のチャットボットの構築を行います。LLM は NVIDIA NIM、ベクトルデータベースは DataStax Astra Vector DB を利用します。

RAG は、生成 AI による回答の精度を向上させる一つの手段です。具体的には、ユーザーのクエリに対して関連するデータを検索し、そのデータを元にAIが回答を生成します。これにより、AIが最新の情報を利用して回答を生成するため、誤った情報を提供するリスクが減少します。

### 事前に準備するもの

- DataStax のアカウント
- NVIDIA の LLM にアクセスするための API キー

## テンプレートを利用したフローの作成

[Workshopの準備](https://github.com/harusametime/langflow-workshop/blob/main/README.md#workshop-%E3%81%AE%E6%BA%96%E5%82%99) に従って、Langflow の画面を開きます。画面の右側に New Flow のボタンがあるのでクリックします。

<p align="center">
<img src="./images/create_new_flow.png" width="70%" border =1/>
</p>

ボタンをクリックするといくつかのテンプレートが表示されます。今回は LLM を使った RAG チャットボットのテンプレートとして、Vector Store RAG を選択します。

<p align="center">
<img src="./images/create_new_rag_flow.png" width="70%" border =1/>
</p>

RAG チャットボットのテンプレートのフローが表示されます。チャットボットのフローは以下の2つのフローで構成されます。
- 関連するデータをあらかじめベクトルデータベースに保存するフロー
- ベクトルデータベースから検索して LLM で回答を生成するフロー

## データをあらかじめデータベースに登録

### Langflow から Astra Vector DB を作成

![alt text](./images/create_new_db.png)

![alt text](./images/input_db_info.png)
