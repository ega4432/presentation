---
marp: true
theme: base
footer: '2021 ©︎ [ysmtegsr](https://twitter.com/ysmtegsr) - Built with marp.'
---

<style>
section.wrap p {
  font-size: 1.75rem;
  font-weight: bold;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translateY(-50%) translateX(-50%);
  text-align: center;
  width: 75%;
}
</style>

<!-- _class: cover lead invert -->

![bg 100% brightness:0.2 contrast:0.7](./../public/introductory_monitoring.jpg)

## - vol. 2 -
# 監視についてみんなに知って欲しいこと

よっしー(@ysmtegsr)

---

<!--
header: '監視についてみんなに知って欲しいこと'
paginate: true
class: slides
-->

## アジェンダ

1. はじめに
2. 前回のおさらい
3. 監視のデザインパターン
4. ビジネス KPI
5. 各コンポーネントの監視
6. まとめ

---

<!-- _class: invert -->

# はじめに

---

### 今回取り扱う書籍

対象読者
- 監視の基本を理解したい人
- 実践的かつ実用的な例、アドバイスを知りたい人

前回の話

- 導入編：https://speakerdeck.com/ysmtegsr/introductory-monitoring

![bg 90% right:20%](./../public/introductory_monitoring.jpg)

---

<!-- _class: invert -->

# 今日伝えたいこと:point_up:

---

<!-- _class: wrap -->

開発に携わる"全員が"
監視に責任を持ちましょう！

---

<!-- _class: invert -->

# 監視のアンチパターン🙅‍♂️

---

## 監視のアンチパターン

1. ツール依存
2. 役割としての監視
3. チェックボックス監視
4. 監視を頼りにする
5. 手動設定

---

## 1. ツール依存

:x: ツール駆動なチーム

:x: ツールを増やすのを恐れる

:x: 「ツール統合」の名の下に

---

## 1. ツール依存

#### ツールは賢く、注意深く選ぼう

:x: ツール駆動なチーム → :o: ミッション駆動なチーム

:x: ツールを増やすのを恐れる → :o: 複数のツールを組み合わせる

:x: 「ツール統合」の名の下に → :o: 目的に応じた専門家されたツール

---

## 2. 役割としての監視

監視とは

- 役割 → **スキル**
- 独立した仕組み → **サービスのパフォーマンスを知る重要指標**

1 人に監視の全責任を押し付けるチームや会社はアンチパターン:x:

- **全員が監視について責任を持つ！**
- **監視をするまで本番環境とは言えない！**

---

## 3. チェックボックス監視

監視が、「これをチェックしていますよ」と誰かに言うためだけのものになってしまっていること:x:

あるあるな状態

- CPU, メモリなどのメトリクスは記録しているものの、なぜシステムが落ちたのか分からない
- 誤検知が多い
- メトリクスを 5 分ごとあるいはそれ以上の間隔で取得
- メトリクスの履歴を保存していない

---

## 3. チェックボックス監視

#### 解決策

- 「動いている」状態を定義して、それを監視する
- OS のメトリクスでのアラートは行わない
- メトリクスを高頻度で取得する（最低でも 1 分ごと）

---

## 4. 監視を頼りにする

監視項目をどんどん増やす:x:

- 根本的な問題の修正
- サービスをより回復性のあるものに

![bg right:30% 90%](https://1.bp.blogspot.com/-f4cRl6azU08/V9vCGWazNAI/AAAAAAAA97c/x4V132XbBqkKlIgZoRyKZqsRNEVFBGYnwCLcB/s800/company_character2_wakai.png)

---

## 5. 手動設定

- 監視項目の追加、解除は自動化しよう
- 自動化できないなら何か重要なことを見落としている可能性がある

---

<!-- _class: invert -->


# 監視のデザインパターン :building_construction:

---


## 1. 組み合わせ可能

- 専用のツールを複数使って「**監視プラットフォーム**」を作ろう
  - 1 つのツールで賄おうとするのは NG
- 監視サービスそれぞれを疎結合に保つ

（絵を描く）

---

## 2. ユーザ視点での監視

サーバが何台動いているかも大事だけど、「**ユーザにどう影響があるか**」を基準に考える。

---

## 3. 作るのではなく買う

- 結局 SaaS を導入した方が安い
  - エンジニアの賃金 + 機会損失 + 仕組みを作る時間 + メンテナンス > SaaS
- SaaS を導入するメリット
  - プロダクト開発にフォーカスできる。
  - SaaS でできないことはほとんどない。

---

## 4. 継続的な改善

- 一朝一夕にはいかない
  - Google, Facebook, Twitter, Netflix …どこも改善を繰り返し続けて今がある
---

<!-- _class: invert -->

# ビジネス KPI :bar_chart:

---


### 経営者、創業者が知りたいこと


---

### 事業責任者の武器になるメトリクス

- 月次計上収益
- 顧客あたりの収益
- 課金顧客の数
- ネットプロモータスコア
- 顧客生涯価値
- 顧客あたりのコスト
- 顧客獲得単価
- 顧客の解約数
- アクティブユーザ数
- バーンレート
- ランレート
- TAM(total addressable market)
- 粗利

---

### Pinterest の例

The 27 Metrics in Pinterest’s Internal Growth Dashboard：http://jwegan.com/growth-hacking/27-metrics-pinterests-internal-growth-dashboard/

※ 本書では Yelp, Reddit という企業を例に取り扱っていました。

---

### ビジネス KPI を技術指標に結び付ける

---

### 会社のビジネス KPI を見つける


---

## まとめ

- やりたいことベースでツールを選ぶ
- 全員が本番環境に対して責任を持つ
- 「動いている」を定義して、それを監視する
- 監視項目を増やすことよりも問題の修正に時間を使う
- 監視項目の登録・解除を自動化する

---

<!-- _class: invert -->

# ご静聴ありがとうございました🙇‍♂️
