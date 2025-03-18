# Fish-Speech-1.5 日本語テキスト→音声変換アプリ

[Fish-Speech-1.5](https://huggingface.co/fishaudio/fish-speech-1.5)モデルを使用して、日本語のテキストファイルを高品質な音声に変換するJupyter Notebookアプリケーションです。このアプリケーションは**GitHubへのアクセスなし**で、**Hugging Faceからモデルを直接利用**します。

## 実装方法

このリポジトリには、複数の実装アプローチが含まれています：

1. **基本版（現在非推奨）** - `fish_speech_japanese_converter.ipynb`
   * transformersライブラリを使用してモデルを直接ロード
   * 現在「KeyError: 'dual_ar'」エラーが発生する問題があります

2. **修正版（ローカル実行）** - `fish_speech_japanese_converter_fixed.ipynb`
   * ONNXモデルを使用してロード
   * シンプルな代替音声生成機能を実装

3. **API版（推奨）** - `fish_speech_space_api.ipynb`
   * Hugging Face Spaces APIを使用
   * 公式デモサイトのバックエンドAPIを呼び出し
   * **最も安定した実装方法**

4. **シンプル版（NEW!）** - `fish_speech_simple.ipynb`
   * **ipywidgetsを使用しない**シンプルな実装
   * ウィジェット表示の問題を回避
   * セルごとに個別に実行する手順ベースのアプローチ
   * API版と同様の安定性

## 特徴

- **GitHubアクセス不要**: Hugging Faceからモデルを直接利用
- **高品質な日本語音声合成**: 100k時間以上の日本語音声データで学習されたモデル
- **発話速度の調整**: 0.5倍～2.0倍の範囲で調整可能
- **音声ファイルのブラウザ内再生とダウンロード**
- **複数の言語対応**: 日本語、英語、中国語など

## ウィジェット表示問題について

Jupyter Notebookで「HTML(value=)」といった形でウィジェットが表示されない問題が発生することがあります。この問題の対処法：

1. **ipywidgets拡張機能のインストール**:
   ```bash
   # JupyterLabの場合
   jupyter labextension install @jupyter-widgets/jupyterlab-manager
   
   # Jupyter Notebookの場合
   jupyter nbextension enable --py widgetsnbextension
   ```

2. **ブラウザキャッシュのクリア**: ブラウザのキャッシュをクリアして再起動

3. **シンプル版を使用**: ウィジェットを使用しない `fish_speech_simple.ipynb` を使用

## インストール方法

```bash
# リポジトリをクローン
git clone https://github.com/ShunsukeTamura06/fish-speech-japanese-converter.git
cd fish-speech-japanese-converter

# 必要なライブラリをインストール（API版の場合）
pip install torch torchaudio numpy scipy requests soundfile
```

## 使用方法（シンプル版 - 最新）

1. Jupyter Notebookを起動

```bash
jupyter notebook
```

2. `fish_speech_simple.ipynb` を開く

3. 初回実行時は、必要なライブラリをインストールするセルを実行

```python
!pip install torch torchaudio numpy scipy requests soundfile
```

4. ファイル処理または直接入力のセルを実行

5. サンプルファイル `sample_text.txt` を使用するか、直接テキストを入力して音声に変換できます

## 修正点

当初の実装では、Fish-Speech-1.5モデルの使用中に「KeyError: 'dual_ar'」エラーが発生する問題がありました。この問題を解決するため、以下の代替アプローチを用意しました：

1. **ONNX版**: モデルをONNX形式でダウンロードして使用（ローカル実行）
2. **API版**: Hugging Face Spaces APIを使用（推奨）
3. **シンプル版**: ウィジェットを使わないAPI版（Jupyter環境に依存しない実装）

## モデルについて

Fish-Speech-1.5は、multiple languages（日本語、英語、中国語など）をサポートする最先端の音声合成モデルです。100k時間以上の日本語音声データで学習されており、高品質な日本語音声合成が可能です。

Hugging Faceモデルリポジトリ: [fishaudio/fish-speech-1.5](https://huggingface.co/fishaudio/fish-speech-1.5)  
公式デモサイト: [Fish-Speech デモ](https://huggingface.co/spaces/fishaudio/fish-speech-1)

## ライセンス

MIT License

## 謝辞

このアプリケーションは[Fish Audio](https://huggingface.co/fishaudio)によって開発されたFish-Speech-1.5モデルを使用しています。