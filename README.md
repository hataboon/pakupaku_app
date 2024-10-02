# パクラク（Pakuraku）
# 家庭用献立提案サービス

## 画面遷移図
- [Figma 画面遷移図](https://www.figma.com/design/0cojSDS4xJ1ybwfGGIWLzH/%E3%83%91%E3%82%AF%E3%83%A9%E3%82%AF?node-id=8-2743&node-type=frame&t=21CuoaJOQqYR9uaC-0)

## サービス概要
家庭にある食材をもとに、生成AIが栄養を考えた子供と大人向けの食べやすい献立を提案します。また、摂取した栄養の可視化機能も提供します。

## このサービスへの思い・作りたい理由
毎日の献立を考えるのは忙しい中で大きな負担です。特に、家族の栄養バランスや子供の好みにも配慮しながら献立を決めるのは難しく、頻繁に悩みます。このアプリがあれば、忙しい家庭の献立作りがもっと簡単で健康的になると思いました。

## ユーザー層について
主婦・共働きの家庭・料理初心者など、忙しい中で毎日料理をする方や家族の健康に配慮したい方をターゲットにしています。

## サービスの利用イメージ
ユーザーが家庭にある食材を入力すると、1日～1週間分の献立が自動生成されます。献立のレシピを確認しながら調理ができます。これにより、時短・食材の無駄削減・栄養管理が実現します。

## ユーザーの獲得について
SNS（InstagramやX（旧twitter））で生成した献立の画像をシェアし、注目を集めます。また、パパママ向けのコミュニティにて口コミでの広がりも狙います。

## サービスの差別化ポイント・推しポイント
1週間分のプランを作ることにより、買い物や調理の計画が簡単に作れます。
また、摂取した栄養を可視化できることにより、より健康的な身体を維持・活性化することを実現します。

## 機能候補

### MVPリリース時に作りたい機能
- 食材入力に基づく献立生成
- 新規登録・ログイン機能

### 本リリースまでに作りたい機能
- 献立の保存とシェア機能
- 栄養の可視化機能（栄養グラフ）

## 機能の実装方針予定

### 1. 一週間の献立を考える機能
- **目的**: ユーザーが家庭にある食材を入力し、それをもとにAIが1日〜1週間分の献立を提案する。
- **実装方法**:
  1. **ユーザー入力部分（Rails View）**:
     - 食材情報を入力するフォームをRailsのViewで提供し、シンプルに食材情報を送信します。
  2. **AIを用いた献立生成（Rails API）**:
     - Rails側で食材情報を受け取り、OpenAIのAPIを使用して献立を生成します。
     - 実際の保育園等の給食のデータを抽出し、openAIへ活用します。
  3. **献立の表示部分（Rails）**:
     - 献立の表示もRailsのViewで行い、サーバーサイドで生成したHTMLをレンダリングして表示します。

### 2. 新規登録・ログイン機能
- **目的**: ユーザーがアカウントを作成・ログイン・ログアウトする機能。
- **実装方法**:
  1. **ユーザー登録・ログイン画面（Rails View）**:
     - 登録・ログイン画面はRailsのViewで作成し、`Devise`を使ってユーザー認証を行います。

### 3. 栄養の可視化機能（栄養グラフ）
- **目的**: 献立の栄養情報を可視化。
- **実装方法**:
  1. **栄養データの生成（Rails）**:
     - 献立の栄養データはRails側で計算し、その結果をRailsのViewで表示します。
  2. **グラフの表示（Rails + JavaScript）**:
     - グラフはRailsのView内でJavaScriptを使って表示します。Reactを使わずに表示を実現します。

### 4. シェア機能
- **目的**: ユーザーが作成した献立をSNSへ投稿し、他のユーザーと共有。
- **実装方法**:
  1. **シェア機能（Rails View）**:
     - 献立をシェアする機能には、SNS（例えばInstagramやTwitter）との連携を行うためのボタンを追加します。シェアボタンを押すことで、献立をSNSに投稿できるリンクを生成します。

## 機能チェックリスト
- [ ] ユーザー登録機能
- [ ] ログイン機能
- [ ] パスワード変更機能
- [ ] メールアドレス変更機能
- [ ] 献立の生成・編集・削除機能
- [ ] 栄養の可視化機能
- [ ] シェア機能
- [ ] その他の基本機能


---
