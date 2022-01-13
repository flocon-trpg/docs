---
title: "ログイン機能のセットアップ"
sidebar_position: 2
---

export const Space = () => (<div style={{ height: 12 }} />);

## 概要

Flocon では、ログイン機能などに[Firebase](https://firebase.google.com/?hl=ja)という Google が運用しているサービスを利用しています。これにより、安全に利用できるログイン機能と、アップローダー[^1]が Flocon で簡単に使えるようになります。

少なくとも Flocon の身内サーバー程度の用途であれば、Firebase は無料枠の範囲内で利用できるかと思います。

## プロジェクトの作成

[Firebase 公式ページ]にアクセスして、「使ってみる」から Firebase プロジェクトを作成します。

サイトの説明に従って、新しいプロジェクトを作るか、既存のプロジェクトを選択して続行を押します。

![1.png](/img/docs/firebase-auth/1.png)

:::danger

Firebase のプランには、無料の Spark プランと従量課金制の Blaze プランの 2 種類がありますが、Blaze プランは Google Cloud と同じく課金額の上限を直接的に制限できないため、多額の料金を請求される可能性があります。また、プロジェクトに対して Google Cloud の請求先アカウントの設定などを行った場合は、[Spark プランから Blaze プランに自動的にアップグレードされる](https://firebase.google.com/docs/projects/billing/firebase-pricing-plans#upgrade-spark-to-blaze)ことがあります。<br />
確実に Spark プランに固定したい場合は、請求先アカウントが設定されていないプロジェクトを使用し、そのプロジェクトに請求先アカウントを今後設定しないようにしてください。もし Blaze プランを利用する場合は、課金アラートの設定などを行うことを強く推奨します。<br />
Flocon の作者は、Flocon の利用により生じた損害等について一切の責任を負いません。

よくわからない場合は、以下の点を守ることを推奨します。

- Spark プランを利用する。
- Firebase や Google Cloud などで、請求先（クレジットカードの登録など）を設定しない。
- もし既存の Google Cloud プロジェクトがある、もしくは請求先アカウントを設定した状態の Google Cloud プロジェクトを後で使用したくなった場合は、そのプロジェクトと Flocon 用のプロジェクトは分けたほうが無難（Flocon で Blaze プランを利用することを考えていて、請求先アカウントを一元的に管理したい場合などはこの限りではありません）。

:::

<Space />

Google アナリティクスを有効にするかどうかを選択します。特にデータが必要でない限りは基本的には無効でいいと思います。

![2.png](/img/docs/firebase-auth/2.png)

<Space />

プロジェクトの作成が完了したら、Firebase 設定画面のトップページに自動的に移動します。

## Firebase Authentication の設定

Firebase Authentication は、Firebase のうちログイン機能の部分を担うサービスです。Firebase Authentication の設定を行っていきます。

左上にある「Authentication」を選択して、「始める」ボタンを押します。

![3.png](/img/docs/firebase-auth/3.png)

<Space />

「Sign-in method」を選択して、「ログインプロバイダ」から希望するログイン方法を追加します。最低でも 1 つのログイン方法を追加しないと利用者がログインできないので、少なくとも 1 つは追加する必要があります。

2021/12/26 現在、Flocon が対応しているのは「メール/パスワード」「電話番号」「匿名」「Google」「Facebook」「Twitter」「GitHub」です。このうち簡単にセットアップできるものでおすすめなのは、「メール/パスワード」と「Google」です。サーバーの用途によっては「匿名」も有効化してもいいかもしれません。

ログイン方法は後からでも追加および削除が可能です。

![4.png](/img/docs/firebase-auth/4.png)

### 自動的に送信されるメールのタイトルと本文を変更 (任意)

:::info
この項目の作業は任意です。
:::

ユーザーがパスワード再発行などを希望したときは Firebase からそのユーザーに対して自動的にメールが配信されます。このメールのタイトルと本文はデフォルトでは英語ですが、左下にある「テンプレート言語」などからこれらを変更することもできます。

デフォルトの文章は Flocon に関するメールだということが少し分かりにくいですし、英語のメールだとユーザーに迷惑メールなどと誤解される可能性があるため、公開サーバーの場合は変更したほうがいいかもしれません。

![6.png](/img/docs/firebase-auth/6.png)

## セットアップ完了

これでログイン機能のセットアップは完了です。次は[APIサーバーを設置する](./api_server)のページをご覧ください。

[firebase公式ページ]: https://firebase.google.com/?hl=ja

[^1]: Flocon は、[Firebase を用いないアップローダーも作成可能](/docs/server/details/uploader/embedded)です。ただし、このチュートリアルの方法で設置した場合はこのアップローダーは実用的でないため、解説していません。