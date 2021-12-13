---
title: "環境変数"
sidebar_position: 4
---

import { WebVarExample as Example } from '../../../src/components/WebVarExample';

## NEXT_PUBLIC_API_HTTP（必須）{#NEXT_PUBLIC_API_HTTP}

APIサーバーのHTTPのアドレスを入力します。通常は `https://` もしくは `http://` で始まります。

### 入力例

<Example
keyName='NEXT_PUBLIC_API_HTTP'
value='https://example.com' />

## NEXT_PUBLIC_API_WS（必須）

APIサーバーのWebSocketのアドレスを入力します。通常は、(NEXT_PUBLIC_API_HTTP)[#NEXT_PUBLIC_API_HTTP] の `https://` もしくは `http://` の部分をそれぞれ `wss://` と `ws://` に置き換えたものになります。

### 入力例

<Example
keyName='NEXT_PUBLIC_API_WS'
value='wss://example.com' />

## NEXT_PUBLIC_AUTH_PROVIDERS（必須）

Firebase Authenticationで有効化したログイン方法を入力します。複数ある場合は`,`で区切ります。

現時点で利用可能な値は、`email`、`google`、`facebook`、`github`、`twitter`、`phone` です。

### 入力例

<Example
keyName='NEXT_PUBLIC_AUTH_PROVIDERS'
value='email,google' />

この例ではメールパスワードとGoogleの2つのログイン方法を入力しています。

## NEXT_PUBLIC_FIREBASE_CONFIG（必須）

[APIサーバーのNEXT_PUBLIC_FIREBASE_CONFIG](/docs/server/api-server/vars#NEXT_PUBLIC_FIREBASE_CONFIG)と同じ値を入力します。

### 入力例

<Example
keyName='NEXT_PUBLIC_FIREBASE_CONFIG'
value='{"apiKey":"****************","authDomain":"***-*****.firebaseapp.com","databaseURL":"https://***-*****.firebaseio.com","projectId":"***-*****","storageBucket":"***-*****.appspot.com","messagingSenderId":"**********","appId":"****************"}' />

## NEXT_PUBLIC_FIREBASE_STORAGE_ENABLED（省略可）

Firebase Storage 版アップローダーを有効化する場合は `true` を入力します。

:::info
有効化する場合は、あわせて Firebase 管理ページから Firebase Storage サービスを有効化する必要があります。
:::

### 入力例

<Example
keyName='NEXT_PUBLIC_FIREBASE_STORAGE_ENABLED'
value='true' />