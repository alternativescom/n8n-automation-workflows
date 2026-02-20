# 📊 Telework Task Inventory Bot

チャットツール（Microsoft TeamsやSlackなど）に投稿された自然言語の「業務報告」をGeminiが解析し、タスク名・所要時間・カテゴリを自動抽出してGoogleスプレッドシートに追記していくワークフローです。
チームメンバーの入力負担を増やさずに、テレワーク下の業務の棚卸しと可視化を実現します。

## ✨ 特徴 (Features)
- **🧠 Natural Language Processing:** 「A社の提案書を2時間作成」といった自然言語から、AIが厳密なJSONデータを抽出。
- **🧹 Auto-Formatting:** AIの出力ブレ（マークダウンの付着など）をCodeノードで自動サニタイズ。
- **📈 Direct Sheets Integration:** 抽出したタスクを分割し、スプレッドシートの指定フォーマット（日付/担当者/タスク名/時間/カテゴリ）に合わせて自動追記（Append）。

## 🛠️ 必須要件 (Prerequisites)
- **n8n** (v1.0+)
- **Google Gemini API Key**
- **Google Account (Google Sheets API)**

## 🚀 セットアップ手順 (Setup Instructions)

1. **インポート:**
   `workflow.json` をn8nにインポートします。
2. **スプレッドシートの準備:**
   Googleスプレッドシートを作成し、1行目（ヘッダー）に左から `日付`, `担当者`, `タスク名`, `所要時間(分)`, `カテゴリ` と入力します。
3. **認証とIDの設定:**
   - **Gemini: Extract Tasks:** あなたのGemini APIクレデンシャルを選択します。
   - **Google Sheets:** Googleアカウントを連携し、上記で作成したスプレッドシートのIDを指定します。`Mapping Column Mode` は `Auto-Map Input Data to Columns` に設定してください。
4. **テスト実行:**
   画面下の「Execute Workflow」をクリックすると、Mockデータ（山田太郎さんの業務報告）が処理され、スプレッドシートに3行のデータが書き込まれます。

※実運用時は、`Manual Trigger` と `Mock Teams Message` ノードを、連携させたいチャットツールのTriggerノード（Webhookなど）に置き換えてご使用ください。
