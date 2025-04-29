# 日本語感情分析テスト (Japanese Sentiment Analysis Test)

## 概要

このリポジトリには、[Hugging FaceのTransformersライブラリ](https://huggingface.co/transformers/) と事前学習済みモデル `cl-tohoku/bert-base-japanese-whole-word-masking` を使用して、日本語テキストの感情分析を行うGoogle Colaboratoryノートブック (`sentiment_analysis_test.ipynb`) が含まれています。

`pipeline` を利用することで、比較的簡単なコードでテキストがポジティブかネガティブかを判定できます。

## 背景

Hugging FaceのTransformersライブラリを用いた自然言語処理の実装方法を学ぶため。特に、事前学習済みモデルを利用した感情分析パイプラインの構築を試すことを目的としました。

## 使い方

1.  **Google Colabで開く:**
    下のバッジをクリックすると、Google Colaboratoryで直接ノートブックを開いて実行できます。
    [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/kognavi/sentiment-analysis-test/blob/main/sentiment_analysis_test.ipynb)

2.  **ライブラリのインストール:**
    ノートブックの最初のコードセルを実行して、必要なライブラリをインストールします。
    ```python
    !pip install transformers[ja] fugashi ipadic
    ```

3.  **実行:**
    ノートブック内のセルを上から順に実行してください。サンプルテキストに対する感情分析の結果が出力されます。
    分析したいテキストを変更する場合は、ノートブック内の該当するコード部分を編集してください。

## 実行結果の例

ノートブック内のサンプルコードを実行すると、以下のような結果が得られます。

**入力テキスト:** `"この映画はとても面白かった。"`
**分析結果:**
```
[{'label': 'positive', 'score': 0.998417317867279}]
```
(このテキストは「ポジティブ」である可能性が非常に高いと判定されました。)

**入力テキスト:** `"期待していたほどではなかった。"`
**分析結果:**
```
[{'label': 'negative', 'score': 0.9988049864768982}]
```
(このテキストは「ネガティブ」である可能性が非常に高いと判定されました。)

*スコア (score) は、そのラベルである確信度を示します。*

## 今後の改善点

今回は事前学習済みモデルをそのまま利用しましたが、今後は特定のドメイン（例: 商品レビューデータなど）に合わせてモデルをファインチューニングし、精度を向上させることも考えられます。（GPU環境があれば、より効率的に試行できます。）

## 使用モデル

*   **モデル:** `cl-tohoku/bert-base-japanese-whole-word-masking`
    *   東北大学 乾・鈴木研究室によって公開されている日本語BERTモデルです。
    *   Hugging Face Model Hub: [https://huggingface.co/cl-tohoku/bert-base-japanese-whole-word-masking](https://huggingface.co/cl-tohoku/bert-base-japanese-whole-word-masking)

## 技術スタック

*   Python
*   Google Colaboratory
*   Hugging Face Transformers
*   Fugashi (日本語形態素解析器)
*   IPAdic (Fugashi用辞書)
*   PyTorch (Transformersのバックエンドとして)


