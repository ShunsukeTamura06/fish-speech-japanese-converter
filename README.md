# Fish-Speech-1.5 日本語テキスト→音声変換アプリ

[Fish-Speech-1.5](https://huggingface.co/fishaudio/fish-speech-1.5)モデルを使用して、日本語のテキストファイルを高品質な音声に変換するJupyter Notebookアプリケーションです。このアプリケーションは**GitHubへのアクセスなし**で、**Hugging Faceからモデルを直接ダウンロード**して使用します。

## 特徴

- **GitHubアクセス不要**: Hugging Faceからモデルを直接ダウンロード
- **高品質な日本語音声合成**: 100k時間以上の日本語音声データで学習されたモデル
- **複数の話者オプション**: 日本語男性/女性の複数バリエーション
- **テキストファイルのアップロード**: 複数のエンコーディング形式に対応 (UTF-8, Shift-JIS, EUC-JP, ISO-2022-JP)
- **直接テキスト入力機能**: テキストファイルを持たなくても利用可能
- **発話速度の調整**: 0.5倍～2.0倍の範囲で調整可能
- **音声ファイルのブラウザ内再生とダウンロード**

## インストール方法

```bash
# リポジトリをクローン
git clone https://github.com/ShunsukeTamura06/fish-speech-japanese-converter.git
cd fish-speech-japanese-converter

# 必要なライブラリをインストール
pip install -r requirements.txt
```

## 使用方法

1. Jupyter Notebookを起動

```bash
jupyter notebook
```

2. `fish_speech_japanese_converter.ipynb` を開く

3. 初回実行時は、必要なライブラリをインストールするセルを実行（コメントを外して実行）

```python
!pip install torch torchaudio transformers huggingface_hub numpy scipy ipywidgets
```

4. メインのコードセルを実行（初回実行時はモデルのダウンロードに時間がかかります）

5. アプリの使用方法:
   - テキストファイルをアップロード、または直接テキストを入力
   - 話者と発話速度を選択
   - 「テキストを変換」ボタンをクリック
   - 生成された音声を再生、ダウンロード

## モデルについて

Fish-Speech-1.5は、multiple languages（日本語、英語、中国語など）をサポートする最先端の音声合成モデルです。100k時間以上の日本語音声データで学習されており、高品質な日本語音声合成が可能です。

Hugging Faceモデルリポジトリ: [fishaudio/fish-speech-1.5](https://huggingface.co/fishaudio/fish-speech-1.5)

## 注意点

- 初回実行時はモデルのダウンロードに時間がかかります（後続の実行ではキャッシュが使用されます）
- 長いテキストの処理にはより多くの時間がかかります
- GPUがある環境では自動的にGPUが使用され、処理が高速化されます

## ライセンス

MIT License

## 謝辞

このアプリケーションは[Fish Audio](https://huggingface.co/fishaudio)によって開発されたFish-Speech-1.5モデルを使用しています。