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
   * ウィジェットを使用した対話型インターフェース

4. **シンプル版** - `fish_speech_simple.ipynb`
   * ipywidgetsを使用しないシンプルな実装
   * ウィジェット表示の問題を回避
   * セルごとに個別に実行する手順ベースのアプローチ

5. **超シンプル版** - `fish_speech_ultra_simple.ipynb`
   * ファイルアップロードエラーを修正
   * ファイルパスを直接指定するアプローチ
   * テキストを直接セルに記述する方法
   * 最もトラブルが少ない実装

6. **オフライン版（最新）** - `fish_speech_offline.ipynb` 🆕
   * **Hugging Face APIではなくモデルをダウンロード**
   * **`change.new[0]["content"]`形式のMemoryViewに対応**
   * ウィジェットベースの対話型インターフェース
   * オフライン実行が可能

## 特徴

- **GitHubアクセス不要**: Hugging Faceからモデルを直接利用
- **オフライン実行可能**: モデルとプロセッサをダウンロードして使用
- **高品質な日本語音声合成**: 日本語のテキストに対応
- **発話速度の調整**: 0.5倍～2.0倍の範囲で調整可能
- **複数の言語対応**: 日本語、英語、中国語など

## エラー修正

以下のエラーを修正しました：

- **「KeyError: 'dual_ar'」**: モデルの内部構造に関するエラー → API版、シンプル版、超シンプル版で修正
- **「tuple object has no attribute 'values'」**: ファイルアップロード処理に関するエラー → 超シンプル版で修正
- **「HTML(value=)」表示問題**: Jupyter UIの問題 → シンプル版、超シンプル版で回避
- **MemoryViewアクセス**: `change.new[0]["content"]`形式のMemoryViewアクセス → オフライン版で対応

## インストール方法

```bash
# リポジトリをクローン
git clone https://github.com/ShunsukeTamura06/fish-speech-japanese-converter.git
cd fish-speech-japanese-converter

# 必要なライブラリをインストール（オフライン版用）
pip install torch==2.0.1 torchaudio==2.0.2 numpy scipy ipywidgets
pip install huggingface_hub transformers==4.31.0
pip install onnxruntime soundfile
```

## 使用方法（オフライン版 - 最新版）

1. Jupyter Notebookを起動

```bash
jupyter notebook
```

2. `fish_speech_offline.ipynb` を開く

3. 初回実行時は、必要なライブラリをインストールするセルを実行します

```python
!pip install torch==2.0.1 torchaudio==2.0.2 numpy scipy ipywidgets
!pip install huggingface_hub soundfile
!pip install transformers==4.31.0
!pip install onnxruntime
```

4. モデルをダウンロードするセルを実行します（初回のみ必要）
   - ダウンロードしたモデルは `./models` ディレクトリに保存されます
   - 次回以降の実行ではキャッシュが使用されるため高速です

5. 以下のいずれかの方法でテキストを変換：
   - **ファイルをアップロード**: ファイルアップロードウィジェットを使用
   - **直接テキストを入力**: テキスト入力エリアに直接入力して変換
   - **サンプルテキスト変換**: サンプルテキストを使用したデモ実行

## モデルについて

Fish-Speech-1.5は、multiple languages（日本語、英語、中国語など）をサポートする最先端の音声合成モデルです。100k時間以上の日本語音声データで学習されており、高品質な日本語音声合成が可能です。

Hugging Faceモデルリポジトリ: [fishaudio/fish-speech-1.5](https://huggingface.co/fishaudio/fish-speech-1.5)  
公式デモサイト: [Fish-Speech デモ](https://huggingface.co/spaces/fishaudio/fish-speech-1)

## ライセンス

MIT License

## 謝辞

このアプリケーションは[Fish Audio](https://huggingface.co/fishaudio)によって開発されたFish-Speech-1.5モデルを使用しています。