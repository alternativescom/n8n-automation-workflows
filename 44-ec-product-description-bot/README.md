# 44. EC Product Description Generator Bot (【EC支援】SEO特化・商品説明の自動生成ボット)

⭐ **If you find this workflow helpful, please give it a Star! (役に立ったらぜひスターをお願いします！)** ⭐

## 🚀 概要 (Overview)
ShopifyやBASEなどのECサイト運営で最も手間のかかる「新商品の登録作業（ライティング）」を、画像1枚から半自動化するワークフローです。

n8nの専用フォームに商品の写真をアップロードするだけで、AI（Gemini Vision）が画像から素材感や特徴を読み取り、「魅力的なキャッチコピー」「SEO対策済みの説明文」「検索用ハッシュタグ」などを自動生成し、**Chatwork（またはLINE等）**に綺麗にフォーマットして通知します。

## 💡 なぜ直接AIを使わず、n8nで自動化するのか？（ベストプラクティス）
「ChatGPTの画面に画像を貼れば同じことができるのでは？」という疑問に対する、業務プロセス改善（DX）としての答えは以下の3点です。

1. **属人化の排除（プロンプトの隠蔽）:** n8nのフォームを使うことで、現場のスタッフは「ただ写真を撮ってアップロードするだけ」になります。AIリテラシーに依存せず、常にプロ級の品質が担保されます。
2. **転記ミスの防止（完全な構造化）:** ECサイトの管理画面にコピペしやすいよう、AIに「商品名」「キャッチコピー」「本文」をJSON形式で強制的に分割出力させています。
3. **将来的な「完全自動化」への布石:** 今回はChatworkへの通知にとどめていますが、n8nをハブにしているため、将来的に「ShopifyやBASEのAPIに直接つなぎ、下書き状態で自動登録させる」という真の自動化へいつでも拡張可能です。

## ✨ 特徴 (Features)
* **画像からの特徴抽出:** テキストの指示がなくても、AIが写真から「シルエット」や「質感」を読み取り、人間が言語化できなかったセールスポイントを引き出します。
* **国内SMB向け（Chatwork連携）:** 実店舗や国内の中小企業で最も導入ハードルの低いChatworkへの通知を前提とした設計（HTTP Request）になっています。

## ⚙️ 使用しているノード (Nodes Used)
1. **n8n Form Trigger:** スタッフがスマホやPCから画像をアップロードするための簡易Webフォームを提供。
2. **Google Gemini:** 画像とメモを解析し、SEOを意識した商品説明をJSONで出力。
3. **Code (JSONパース):** Geminiの出力から純粋なJSONオブジェクトを抽出。
4. **HTTP Request (Chatwork通知):** APIを直接叩き、Chatworkの専用タグ（`[info]`等）を使って見やすく装飾したメッセージを送信。

## 🛠️ 使い方とChatwork APIの設定手順
1. このディレクトリにある `workflow.json` をご自身のn8n環境にインポートします。
2. Geminiの認証情報（Credentials）を設定します。
3. **Chatwork連携のセットアップ:**
   * **APIトークンの取得:** Chatworkの右上のユーザーアイコン ＞「サービス連携」＞「API Token」からご自身のトークンをコピーします。
   * **ルームIDの取得:** 通知を送りたいChatworkのグループチャットを開き、URL（`https://www.chatwork.com/#!rid123456789`）の数字部分（例なら `123456789`）をコピーします。
   * **HTTP Requestノードの設定:** URLの `YOUR_ROOM_ID` の部分を取得したルームIDに書き換え、Headerの `X-ChatWorkToken` のValueにAPIトークンを貼り付けます。
4. ワークフローをテスト状態（Listen for test event）にし、Formの「Test URL」を開いて商品画像をアップロードし、Chatworkに通知が届くか確認してください。

---

## 🏢 自社への導入・カスタマイズをご希望の方へ (Consulting & Support)

「この仕組みをそのまま自社のShopifyとAPI連携させて、完全自動で商品登録させたい」「Chatworkではなく公式LINEに通知を飛ばしたい」といった、実務に直結する高度なカスタマイズのご相談も承っております。

ECサイトの運営効率化や、AIを活用した「一人DX」の実装でお悩みの方は、**有限会社野田収一事務所（Alternative Computers）**へお気軽にご相談ください。

🔗 [Alternative Computers - DX推進サポート](https://alternativecomputers.org/lp/)
