# 36. Daily Report AI Analyzer (日報AI集計＆アクション提案ボット)

⭐ **If you find this workflow helpful, please give it a Star! (役に立ったらぜひスターをお願いします！)** ⭐

## 🚀 概要 (Overview)
形骸化しがちな「日報」を、マネジメントの強力な武器に変えるワークフローです。
毎日指定した時間（例：19時）に、チャットツール上の「日報チャンネル」からその日の投稿をすべて自動取得し、AI（Gemini）がマネージャー向けに分析レポートを作成します。

単なる要約ではなく、「チームのコンディション」「クレームやモチベーション低下などの要注意サイン」「明日マネージャーが誰にどんな声かけをすべきかのアクション提案」を抽出してリーダーのDMに直接届けます。

## ✨ 特徴 (Features)
* **LLMによる高度な文脈理解:** 日々の業務報告から「感情」や「隠れたリスク」をGeminiが読み取ります。
* **行動直結型のアウトプット:** 「〇〇さんに明日の朝、タスク過多ではないかヒアリングしてください」など、明日すぐに行動できる具体的なアクションを提案します。
* **Slack / Microsoft Teams 両対応:** 企業のセキュリティ要件や導入ツールに合わせて柔軟にカスタマイズ可能です。（デフォルトはSlack版の構成になっています）

## ⚙️ 使用しているノード (Nodes Used - Slack版)
1. **Schedule Trigger:** 平日の19時に定期実行。
2. **Slack (日報取得):** 指定した日報チャンネルから本日のメッセージを一括取得。
3. **Code (日報テキスト結合):** 取得した複数のメッセージを1つのテキストデータに整形。
4. **Google Gemini:** 結合された日報を読み込み、マネージャー向けのアクション提案レポートを生成。
5. **Slack (通知):** 生成されたレポートをマネージャーのDM（または専用チャンネル）に送信。

---

## 🔄 Microsoft Teams版への切り替え手順 (How to adapt for MS Teams)

多くの企業で導入されている Microsoft Teams でも動作させることが可能です。以下の手順でノードを差し替えてください。

1. **取得ノードの変更:** `Slack (日報取得)` を削除し、`Microsoft Teams` ノードを追加（Operation: `Get Many`, Resource: `Chat Message` 等を設定）。
2. **通知ノードの変更:** `Slack (マネージャーへ通知)` を削除し、`Microsoft Teams` ノードを追加（Operation: `Create`, Resource: `Message` を設定）。
3. **Codeノードの修正:** Teamsから取得するメッセージはHTMLタグが含まれることが多いため、`Code` ノードのコードを以下のように書き換えてHTMLタグをプレーンテキストにクリーニングしてください。

```javascript
const messages = $input.all();
if (messages.length === 0) {
  return [{ json: { compiledReports: "本日の日報はありませんでした。" } }];
}

let compiledText = "";
messages.forEach((msg, index) => {
  let text = (msg.json.body && msg.json.body.content) ? msg.json.body.content : "";
  text = text.replace(/<[^>]*>?/gm, '').trim();
  
  if (text !== "") {
    compiledText += `【報告 ${index + 1}】\n${text}\n\n`;
  }
});

if (compiledText === "") {
  return [{ json: { compiledReports: "本日の日報はありませんでした。" } }];
}

return [{ json: { compiledReports: compiledText } }];
```

---

## 🏢 自社への導入・カスタマイズをご希望の方へ (Consulting & Support)

「このワークフローを自社のTeams環境に導入してほしい」「形骸化した日報文化をAIで改善し、マネジメントの質を向上させたい」といったご依頼も承っております。

経営課題を解決する「生きた業務自動化（DX推進）」でお悩みの方は、**有限会社野田収一事務所（Alternative Computers）**へお気軽にご相談ください。

🔗 [Alternative Computers - DX推進サポート](https://alternativecomputers.org/lp/)
