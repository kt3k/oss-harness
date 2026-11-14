# ライブラリの LP（ランディングページ）の見せ方

OSS ライブラリの LP、特にファーストビュー（ヒーロー）に何を置くかについて、調査と実践から分かったことのまとめ。2026-11 時点。

事例として [gawa](https://github.com/kt3k/gawa)（WebView 内のページとネイティブアプリをつなぐ型付きブリッジ）の LP を作り直した経緯を末尾に記録する。

## 結論

1. **ライブラリのヒーローにはコードを置く。** 抽象的な図やロゴの大写しではなく、「使うとこう書ける」を見せる。
2. **見出しは名前ではなく「何をするツールか」を言う。** 名前とロゴは小さなワードマークで足りる。
3. **コードはファーストビューに収める。** 一般的なノート PC の画面（1280×800 程度）で、スクロールせずにコードの要点が全部見えることを目安にする。
4. **2 つの側をつなぐツールは、両端のコードを対にして見せる。** 同じ名前で呼ぶ側と受ける側が一致することを、一目で分かるようにする。

## ツールの種類ごとのヒーロー

| 種類 | ヒーローに置くもの | 例 |
|---|---|---|
| ライブラリ・SDK | 使い方のコード | tRPC、Hono、Tailwind |
| ランタイム・CLI | インストールコマンド、ベンチマーク | Vite、Bun、Biome、Effect |
| 大きなフレームワーク・製品 | ロゴ、アニメーション、製品 UI | Tauri、Electron、Astro |

- ヒーローに抽象的な層の図（「Page / ライブラリ / WebView」のような積み重ね）を置いている事例は見つからなかった。
- ロゴを大きく見せているのは、大きなフレームワークか、ヒーローに何も置かない LP（htmx、Zod）だった。小さなライブラリが真似る理由は薄い。
- Tailwind や Biome は「入力 → 出力」を並べる。「呼ぶ → 結果が返る」の視覚化として使える。

## 2 つの側をつなぐツールの見せ方

クライアントとサーバー、ページとネイティブ、メインスレッドとワーカーのように、両端を持つツールの事例。

- **tRPC**: ヒーローには呼ぶ側のコードだけを置き、「型はサーバーから来る」と一行添える。直後の「How it works」で両側を左右に並べる。
- **Comlink**: main 側と worker 側のコードを対にして載せる。
- **Capacitor**: Web 側の TypeScript とネイティブ側の Swift を同じタブ群に並べる。

推奨する形:

- 左に呼ぶ側、右に受ける側を置く。受ける側が複数言語なら（Swift / Kotlin など）タブで切り替える。
- 間に矢印を置き、どちらが呼んでどちらが受けるかを示す（例: `call →`、`← emit`）。
- 両端で同じメソッド名を使い、対応が目で追えるようにする。
- 狭い画面では縦に積み、矢印も上下向きにする。または tRPC のように呼ぶ側だけ見せ、受ける側へリンクする。

## ヒーロー以降の並び

ヒーローの直後は、利用企業ロゴか機能カード、次に 3 ステップの「How it works」がほぼ定番。続いて機能、社会的証明、最終 CTA の順。

ただし、機能カードが既に 3 項目で同じ役割を果たしているなら、「How it works」を重ねて足す必要はない。

## 根拠

- **[Evil Martians: We studied 100 dev tool landing pages](https://evilmartians.com/chronicles/we-studied-100-devtool-landing-pages-here-is-what-actually-works-in-2025)**: 中央寄せのヒーローが主流。大きな見出しの下にビジュアルを 1 つ置く。UI の少ないライブラリ・SDK はコードスニペットを置くのが一般的。主張より動くコードと具体的な数字、派手な演出より簡潔さ。
- **[DEV: Landing pages that convert for developer tools](https://dev.to/whoffagents/landing-pages-that-convert-for-developer-tools-patterns-that-actually-work-3c8k)**: ファーストビューのコードやデモは、長い説明文より早く中身が伝わる。
- **閲覧時間の偏り**: Nielsen Norman Group の調査として「閲覧時間の 57% が最初の画面」という数字がよく引かれる（[二次情報](https://mixpanel.com/blog/optimizing-above-the-fold)。原典は未確認）。
- **見出しの重要性**: 訪問者の多くは見出しとサブ見出しの冒頭だけで読み進めるか判断すると言われる（[参考](https://www.flint.com/blog/landing-page-headline-testing-statistics)。ベンダーのブログで、数字は割り引いて読む）。

ロゴの大きさを直接比べた研究は見つからなかった。上の結論は、エージェンシーやベンダーの記事と、各 LP の実例からの判断。

### 調べた LP

GitHub 上のサイトのソースで確認した: tRPC、Hono、Zod、Valibot、Vite、Tauri、Capacitor、htmx、Astro、Tailwind、Biome、Effect、Electron、Comlink。

Bun と Hotwire は記憶ベースで未検証。Deno、Expo、Alpine は取得できなかった。各公式サイトには調査環境のネットワークから接続できなかったため、本番の表示とは差がありうる。

## 事例: gawa の LP

1. **最初の状態**: ヒーロー右に「Page: `call` / `on`」「gawa: typed RPC and events」「WebView」の 3 段の層リスト。段名と API 名が同じ行に並び「page call on」と読めてしまう、呼び先のネイティブ側が図にない、という問題があった。
2. **1 回目の修正**: 層リストをやめ、ページ側の `bridge.call("kv.get", …)` / `bridge.on("back", …)` と、アプリ側の `router.register("kv.get")` / `emit("back")`（Swift / Kotlin のタブ）を左右に並べた。間に `call →` と `← emit` の矢印。
3. **2 回目の修正**: 上部の大きな漢字「側」が最初の画面の高さを約 170px 使い、1280×900 でもコードの上の数行しか見えなかった。側をワードマーク横の小さな印にし、h1 を名前の「gawa」から「A thin, typed bridge between a web page and the app that hosts it.」に変えた。1280×800 でコードの組が最後まで見えるようになった。

学び:

- ブランド要素（漢字の名前など）は残してよいが、ファーストビューの面積を使わせない。
- 見た目の確認は、デスクトップ（1280×800）、スマホ幅（390px）、ダークモードのスクリーンショットで行い、コードの組の下端の位置を数値で測る。
