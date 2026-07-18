# バイオリンおなやみ相談室

「弓が曲がる」「音程が合わない」「左手が痛い」——生徒が実際に口にする言い回しそのままの悩み113問に、3人の専門家（バイオリニスト・研究マニア・身体専門家）の座談会で答えるLINE風チャットアプリ。

[バイオリンQ&A相談室（violin-qa-chat-v2）](https://github.com/ngmt4amtk-web/violin-qa-chat-v2)の後継。UI・構造は同じで、質問と回答を全面刷新した別アプリ。

## v2との違い

- 質問は書籍『バイオリンQ&A 200』の事例ベース（persona付き）ではなく、レッスン現場の生の悩みベース（persona廃止・一人称の症状描写）
- 回答は全問リサーチし直し（レッスン文字起こし145日分の分析・身体メソッド集・研究論文・学習者フォーラムに接地）
- カテゴリは症状ベースの12章（痛み／構え／弓・右手／音色／左手／音程／ビブラート／ポジション移動／和音・リズム／練習・心／道具／子ども・保護者）

## データの流れ

- 原稿: `chapters/qNNN.json`（フラット構造・これが真実源）
  - スキーマ: `{id, chapter, title, persona: null, question, discussion:[{speaker, text}], prescription:[], sources:[], tier}`
  - 話者は「バイオリニスト」「研究マニア」「身体専門家」の3人のみ
- 質問リストの設計: `research/master_questions.json`（113問・12章・出典refs付き）
- リサーチ素材: `research/sweep_results.json`（学習者の悩み158件・6方向スイープ）ほか `~/qa300-book-2026/research/` を参照

## 更新

原稿JSONを更新したら:

```bash
node scripts/build-data.mjs
```

検証（スキーマ・話者・件数）を通過すると `data/questions.js` が生成される。キャッシュ対策として `index.html` の `?v=` を更新してからコミットする。

## 公開

GitHub Pagesで `main` ブランチのルートを公開する（リモート: violin-nayami-chat）。
