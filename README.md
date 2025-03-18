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

5. **超シンプル版（最新・最も安定）** - `fish_speech_ultra_simple.ipynb` ✨
   * **ファイルアップロードエラーを修正**
   * ファイルパスを直接指定するアプローチ
   * テキストを直接セルに記述する方法
   * 最もトラブルが少ない実装
   * **すべての環境で動作する推奨版**

## 特徴

- **GitHubアクセス不要**: Hugging Faceからモデルを直接利用
- **高品質な日本語音声合成**: 100k時間以上の日本語音声データで学習されたモデル
- **発話速度の調整**: 0.5倍～2.0倍の範囲で調整可能
- **音声ファイルのブラウザ内再生とダウンロード**
- **複数の言語対応**: 日本語、英語、中国語など

## エラー修正

以下のエラーを修正しました：

- **「KeyError: 'dual_ar'」**: モデルの内部構造に関するエラー → API版、シンプル版、超シンプル版で修正
- **「tuple object has no attribute 'values'」**: ファイルアップロード処理に関するエラー → 超シンプル版で修正
- **「HTML(value=)」表示問題**: Jupyter UIの問題 → シンプル版、超シンプル版で回避

## インストール方法

```bash
# リポジトリをクローン
git clone https://github.com/ShunsukeTamura06/fish-speech-japanese-converter.git
cd fish-speech-japanese-converter

# 必要なライブラリをインストール
pip install torch torchaudio numpy scipy requests soundfile
```

## 使用方法（超シンプル版 - 最新の推奨版）

1. Jupyter Notebookを起動

```bash
jupyter notebook
```

2. `fish_speech_ultra_simple.ipynb` を開く

3. 初回実行時は、必要なライブラリをインストールするセルを実行

```python
!pip install torch torchaudio numpy scipy requests soundfile
```

4. 以下のいずれかの方法でテキストを変換：

   - **サンプルテキスト変換**: セル4を実行（リポジトリ内のsample_text.txtを使用）
   - **指定したファイルパスから変換**: セル5を編集して実行（自分のファイルパスを指定）
   - **直接テキストを入力**: セル6を編集して実行（テキストを直接セルに記述）
   - **テキストをファイルに保存してから変換**: セル9を編集して実行（長文処理に便利）

5. その他の機能：
   - 様々な速度でのテスト（セル7）
   - 複数言語のテスト（セル8）

## モデルについて

Fish-Speech-1.5は、multiple languages（日本語、英語、中国語など）をサポートする最先端の音声合成モデルです。100k時間以上の日本語音声データで学習されており、高品質な日本語音声合成が可能です。

Hugging Faceモデルリポジトリ: [fishaudio/fish-speech-1.5](https://huggingface.co/fishaudio/fish-speech-1.5)  
公式デモサイト: [Fish-Speech デモ](https://huggingface.co/spaces/fishaudio/fish-speech-1)

## ライセンス

MIT License

## 謝辞

このアプリケーションは[Fish Audio](https://huggingface.co/fishaudio)によって開発されたFish-Speech-1.5モデルを使用しています。