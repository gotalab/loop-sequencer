# 🎵 1分で曲作り - ループ・シーケンサー

16ステップ×4トラックの1小節ループを最短で作って遊べる、Webベースの音楽制作ツールです。

**Gemini 2.5 Pro** による自動パターン生成と、**Tone.js** による高品質なWeb Audio再生を搭載。

## ✨ 特徴

- **AIパターン生成**: Gemini 2.5 ProでDance Music風のパターンを自動生成
- **リアルタイム再生**: Tone.jsによる高精度なシーケンス再生
- **WAV録音**: ブラウザで8秒録音→即ダウンロード
- **プリセット**: House / Boom Bap / Trap の3スタイル搭載
- **完全フロントエンド**: GitHub Pagesで公開可能な静的サイト
- **URL共有**: パターンをURLで簡単にシェア
- **LLMなしモード**: APIキーなしでも手動編集で楽しめる

## 🚀 クイックスタート

### 1. デモサイトで試す

GitHub Pagesで公開されたデモサイトにアクセス:

```
https://[your-username].github.io/loop-sequencer/
```

### 2. ローカルで実行

```bash
# リポジトリをクローン
git clone https://github.com/[your-username]/loop-sequencer.git
cd loop-sequencer

# 静的サーバーで起動（例：Python）
python3 -m http.server 8000

# ブラウザで開く
open http://localhost:8000
```

### 3. Gemini APIキーの取得（オプション）

AIパターン生成を利用する場合は、[Google AI Studio](https://aistudio.google.com/app/apikey) でAPIキーを取得してください。

> ⚠️ **注意**: このアプリはプロトタイプ用途です。APIキーは保存されません（メモリのみ）。

## 📖 使い方

### 基本操作

1. **プリセット選択**: Style ドロップダウンから House / Boom Bap / Trap を選択
2. **パラメータ調整**: BPM（60-200）とSwing（0.50-0.62）を設定
3. **再生**: ▶ボタンで再生、■ボタンで停止
4. **手動編集**: グリッド上のステップをクリックしてON/OFF

### AI生成（Gemini）

1. サイドバーにGemini APIキーを入力
2. 「✨ Geminiで生成」ボタンをクリック
3. 約1-2秒でパターンが生成され、自動的に適用されます

### 録音

1. ●録音ボタンをクリック
2. 8秒間自動録音
3. 完了するとWAVファイルが自動ダウンロードされます

### 共有

1. 「🔗 共有URLを作成」ボタンをクリック
2. 生成されたURLをコピー＆シェア
3. URLを開くと同じパターンが復元されます

### JSON編集

1. サイドバーの「パターンJSON」セクションでJSONを確認
2. 「📥 復元」セクションにJSONをペーストして復元可能

## 🎼 パターン仕様

パターンは `pattern-v1` JSONフォーマットで表現されます:

```json
{
  "version": "pattern-v1",
  "meta": {
    "style": "house",
    "bpm": 124,
    "swing": 0.55,
    "scale": "C minor"
  },
  "tracks": [
    {
      "id": "kick",
      "type": "drum",
      "sound": "kick-01",
      "steps": [1, 5, 9, 13]
    },
    {
      "id": "bass",
      "type": "mono",
      "synth": "square",
      "notes": [
        { "step": 1, "pitch": "C2", "len": "8n" }
      ]
    }
  ]
}
```

詳細は[PRD（要件定義書）](./PRD.md)を参照してください。

## 🛠 技術スタック

- **Tone.js** (v14.8.49) - Web Audio フレームワーク
- **Gemini 2.5 Pro** - AIパターン生成
- **Vanilla JavaScript** - フレームワークなし
- **GitHub Pages** - 静的ホスティング

## 📁 ディレクトリ構成

```
/
├── index.html          # メインアプリケーション（単一ファイル）
├── samples/            # サンプル音源
│   ├── kick-01.wav     # （ユーザーが配置）
│   ├── snare-01.wav    # （ユーザーが配置）
│   ├── hat-closed-01.wav # （ユーザーが配置）
│   └── README.md       # 音源の入手方法
└── README.md           # このファイル
```

## 🔐 セキュリティとプライバシー

- **APIキーは保存されません**: メモリのみで保持され、ページをリロードすると消去されます
- **ローカルストレージは使用しません**: クッキーや永続ストレージにキーは保存されません
- **プロトタイプ用途**: 本番環境ではバックエンドプロキシ経由での利用を推奨

## 📋 受け入れ基準

- [x] サイドバーでキー未入力でも起動可能（LLMなしモード）
- [x] キー入力→[Geminiで生成]実行でpattern-v1 JSONを受け取り、1.5s程度で再生
- [x] ▶再生 / ■停止 / ●録音(8s) が動作し、WAVが保存できる
- [x] プリセット3種が選択できる
- [x] JSON貼付→即反映、?p= 共有で復元できる
- [x] リロードでAPIキーが空に戻る（保存していない）

## 🤝 コントリビューション

プルリクエスト歓迎です！以下のような改善案があります:

- より多くのプリセットスタイル
- 追加のエフェクト（リバーブ、ディレイ等）
- 複数小節対応
- MIDIエクスポート

## 📄 ライセンス

MIT License

## 🙏 謝辞

- [Tone.js](https://tonejs.github.io/) - 素晴らしいWeb Audioフレームワーク
- [Google Gemini](https://ai.google.dev/) - 強力な生成AI
- フリーサンプル提供者の皆様

## 🔗 関連リンク

- [Gemini API ドキュメント](https://ai.google.dev/docs)
- [Tone.js ドキュメント](https://tonejs.github.io/docs/)
- [Web Audio API](https://developer.mozilla.org/en-US/docs/Web/API/Web_Audio_API)

---

**楽しい音楽制作を！** 🎧✨
