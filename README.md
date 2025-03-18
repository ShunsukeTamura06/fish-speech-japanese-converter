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

## 特徴

- **GitHubアクセス不要**: Hugging Faceからモデルを直接利用
- **高品質な日本語音声合成**: 100k時間以上の日本語音声データで学習されたモデル
- **テキストファイルのアップロード**: 複数のエンコーディング形式に対応 (UTF-8, Shift-JIS, EUC-JP, ISO-2022-JP)
- **直接テキスト入力機能**: テキストファイルを持たなくても利用可能
- **発話速度の調整**: 0.5倍～2.0倍の範囲で調整可能
- **音声ファイルのブラウザ内再生とダウンロード**

## インストール方法

```bash
# リポジトリをクローン
git clone https://github.com/ShunsukeTamura06/fish-speech-japanese-converter.git
cd fish-speech-japanese-converter

# 必要なライブラリをインストール（API版の場合）
pip install torch torchaudio numpy scipy ipywidgets requests soundfile
```

## 使用方法（API版 - 推奨）

1. Jupyter Notebookを起動

```bash
jupyter notebook
```

2. `fish_speech_space_api.ipynb` を開く

3. 初回実行時は、必要なライブラリをインストールするセルを実行

```python
!pip install torch torchaudio numpy scipy ipywidgets
!pip install requests
!pip install soundfile
```

4. メインのコードセルを実行

5. アプリの使用方法:
   - テキストファイルをアップロード、または直接テキストを入力
   - 言語と発話速度を選択
   - 「テキストを変換」ボタンをクリック
   - 生成された音声を再生、ダウンロード

## 修正点

当初の実装では、Fish-Speech-1.5モデルの使用中に「KeyError: 'dual_ar'」エラーが発生する問題がありました。この問題を解決するため、以下の代替アプローチを用意しました：

1. **ONNX版**: モデルをONNX形式でダウンロードして使用（ローカル実行）
2. **API版**: Hugging Face Spaces APIを使用（推奨）

## モデルについて

Fish-Speech-1.5は、multiple languages（日本語、英語、中国語など）をサポートする最先端の音声合成モデルです。100k時間以上の日本語音声データで学習されており、高品質な日本語音声合成が可能です。

Hugging Faceモデルリポジトリ: [fishaudio/fish-speech-1.5](https://huggingface.co/fishaudio/fish-speech-1.5)  
公式デモサイト: [Fish-Speech デモ](https://huggingface.co/spaces/fishaudio/fish-speech-1)

## 注意点

- API版が最も安定して動作します
- API版は外部サービスに依存するため、インターネット接続が必要です
- 長いテキストの処理にはより多くの時間がかかります

## トラブルシューティング

- **KeyError: 'dual_ar'**: 基本版で発生するエラーです。API版を使用してください。
- **API接続エラー**: インターネット接続を確認し、再試行してください。
- **その他のエラー**: 最新の実装と互換性のある依存関係をインストールしていることを確認してください。

## ライセンス

MIT License

## 謝辞

このアプリケーションは[Fish Audio](https://huggingface.co/fishaudio)によって開発されたFish-Speech-1.5モデルを使用しています。