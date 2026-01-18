---
title:  SuiのDeFiの始め方 [Sui Foundation Blog]
tags: SUI Web3 Blockchain Ethereum 仮想通貨
author: nft
slide: false
---
SuiのDeFi（分散型金融）の現状と、DeFiアプリやユーザーがSuiで得られる独自のメリットについて解説します。

![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/1926720/99c3cc43-4735-48b9-b4d9-670497789b05.png)

:::note
元記事: [How to DeFi on Sui](https://blog.sui.io/how-to-defi-on-sui/)
:::

トークンのスワップ、NFTの世界への参入、または単に資産を貸し出して報酬を得たい場合など、SuiのDeFiエコシステムには誰にでも何かがあります。Sui DeFiは、Suiネイティブのプリミティブのおかげで、ユニークで強力なアプリケーションで満たされています。[これらのプリミティブは、DeFiアプリを支援し](https://blog.sui.io/sui-primitives-help-defi-flourish/)、[DeepBook](https://www.deepbook.tech/?ref=blog.sui.io)を介した流動性ブートストラッピングなどの一般的な課題に対処します。

健全なDeFiエコシステムは、借入・貸付プロトコル、分散型取引所(DEX)、NFTマーケットプレイスなど、いくつかの基盤となるアプリタイプで構成されています。Suiの強力なプリミティブ、[Moveプログラミング言語](https://sui.io/move?ref=blog.sui.io)のセキュリティ、そしてSuiビルダーコミュニティの創意工夫により、Sui DeFiはWeb3の他のどこにもない体験を提供します。

[Suiを始める](https://blog.sui.io/how-to-get-started-with-sui/)方法を学び、[DeFiにおけるステーキングの役割](https://blog.sui.io/how-to-stake-on-sui/)について理解した後は、SuiのDeFiランドスケープを理解する時です。

## Sui上のDeFi

他のDeFiエコシステムでは、特にWeb3が初めてのユーザーは、摩擦ポイントに遭遇することがよくあります。例えば、アプリに資産へのアクセスを許可するために別々のトランザクションを送信することは煩雑であり、ガス代がかかります。Suiでは、[オブジェクト指向アーキテクチャ](https://blog.sui.io/all-about-objects/)の結果として承認トランザクションが不要であるため、DeFi活動がよりスムーズでユーザーフレンドリーになります。

ガス代とトランザクション速度は、DeFiにおいて重要な要素です。Suiでは、[ガス代](https://blog.sui.io/gas-fees-explained/)は低いだけでなく、安定しており、各エポックでレートをロックするSuiのガス価格設定メカニズムのおかげで、高需要時でも予測可能性が確保されます。さらに、Suiのコンセンサスメカニズムである[Mysticeti](https://sui.io/mysticeti?ref=blog.sui.io)は、1秒未満でトランザクションをファイナライズし、Web3で最も低いレイテンシを提供してSui DeFiを次のレベルに引き上げます。

## DeFiの使い方

DeFi初心者にとって、アプリとの最初のやり取りは少し馴染みのないものかもしれません。幸いなことに、ほとんどのDeFiアプリには非常に似たステップが必要です。最初のステップは、Suiウォレットを接続することです。通常、ウェブページの中央または右上隅に「Connect Wallet」ボタンがあります。ウォレットを接続する際には、複数のウォレットオプションがあり、[zkLogin](https://sui.io/zklogin?ref=blog.sui.io)を介してGoogleなどのソーシャルアカウントを使用してログインする機能も表示される場合があります。ウォレットアプリと接続する特定のアカウントを選択した後、アプリとのやり取りを開始する準備が整います。

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXddTlSiOVBPWojirll9eGbmmGXvdRycnwcKuEWuyDeUitzkw-GygQzi9puznjb3jXPTkXrkbQproT2iBlLRE9ulnbWV9h1Qt9Tz8s1RpO9_eo-WGQ_-FHnX9XMaFFa6X4DjFo9e67eiE7VHiZOqiMzSsH8?key=GaH0AdJlIeokr9jP1sp83A)

Turbosでは、ユーザーはトレーディングインターフェイスから直接ウォレットに接続できます。

複数のアカウントを持っている場合、アプリとウォレットによってアカウント間の切り替え方法が異なります。シームレスに切り替えられるアプリもあれば、切断、アカウント切り替え、再接続が必要なアプリもあります。ウォレットからも切断する必要がある場合があります。

![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdUiBr6-JaLRoQVoQC_1K9M2qC9oy-CbWEVnU6w-NW29SPXTaFboAU0sFl5q3xKxCbwC-CwW81md6MdHJa2-lI91A2ypeNVob5nJZnI0lOxIi7xVZhwPrCELskYsJbjbojrXk_N0OV_aAmUV7Zl6RKbPEtW?key=GaH0AdJlIeokr9jP1sp83A)

Sui Walletでは、ウィンドウの上部中央に接続されているアプリを確認できます。

次に、考慮すべき様々な要因を理解することが重要です。例えば、スワップを検討する際には、スリッページとガス代が発生する可能性があることを認識しておくと役立ちます。スリッページとは、スワップの予想価格と実際の価格の差であり、ガス代はトランザクションの処理コストです。資産の借入などのオプションを検討している場合、通常は最初に貸付が必要です。これらの基本的な概念を理解することは、より自信を持ってDeFiをナビゲートするのに役立ちますが、どの道を選択する場合でも、独自の調査を行い、アドバイザーに相談することが常に推奨されます。

## SuiのDeFiランドスケープ

### 借入・貸付プロトコル

借入・貸付プロトコルは、ユーザーがデジタル資産を貸し出して他の資産を借り入れる能力を得ることを可能にし、従来の金融システムに代わる低摩擦でアクセス可能な選択肢を提供します。

Smart Contractによって駆動されるこれらのプロトコルは、世界中でアクセス可能な基本的な金融ツールのための公平で透明な手段を提供します。

以下は、Sui上の人気の借入・貸付プロトコルのリストです:

* [Bucket](https://bucketprotocol.io/?ref=blog.sui.io)
* [Navi](https://naviprotocol.io/?ref=blog.sui.io)
* [Scallop](https://scallop.io/?ref=blog.sui.io)
* [SuiLend](https://suilend.fi/?ref=blog.sui.io)

### 分散型取引所

DEXは、ユーザーが安全で機能豊富な方法で互いに資産を直接取引できるようにします。Smart Contractを活用することで、DEXは複雑なピアツーピアトランザクションを自律的な方法で促進できます。

以下は、Sui上の人気のDEXとDEXアグリゲーターのリストです:

* [7k](https://7k.ag/?ref=blog.sui.io)
* [Aftermath](https://aftermath.finance/?ref=blog.sui.io)
* [Cetus](https://www.cetus.zone/?ref=blog.sui.io)
* [FlowX](https://flowx.finance/?ref=blog.sui.io)
* [Hop](https://hop.ag/?ref=blog.sui.io)
* [Kriya](https://kriya.finance/?ref=blog.sui.io)
* [Turbos](https://turbos.finance/?ref=blog.sui.io)

### デリバティブ取引所

デリバティブ取引所は、オプション、先物、パーペチュアル契約などのデリバティブを取引する方法を提供します。これらの取引所により、トレーダーはリスクをヘッジし、レバレッジにアクセスできるほか、高度なトレーディング戦略のための他のツールも利用できます。

以下は、Sui上の人気のデリバティブ取引所のリストです:

* [BlueFin](https://bluefin.io/?ref=blog.sui.io)
* [Typus](https://typus.finance/?ref=blog.sui.io)
* [Sudo](https://www.sudo.finance/?ref=blog.sui.io)

### イールドアグリゲーター

イールドアグリゲーターは、様々なイールド生成プロトコルに資産を自動的に再分配することで、ユーザーが資産の潜在的なリターンを最適化するのを支援します。これらのツールは、ユーザーがSuiのDeFiエコシステムで利用可能な機会を最大限に活用するためのシンプルで効率的な方法を提供します。

以下は、Sui上の人気のイールドアグリゲーターのリストです:

* [Alpha Fi](https://alphafi.xyz/?ref=blog.sui.io)
* [Kai](https://kai.finance/?ref=blog.sui.io)
* [Strater](https://www.strater.xyz/?ref=blog.sui.io)

### NFTマーケットプレイス

NFTマーケットプレイスは、ユーザーがNFTを売買、取引できるプラットフォームです。これらのマーケットプレイスは、アートやコレクティブルから実世界の資産やインフラストラクチャを表すNFTまで、幅広いデジタル資産へのアクセスを提供し、ビルダー、クリエイター、コレクターがSui上でユニークで強力なNFTを取引できるようにします。

以下は、Sui上の人気のNFTマーケットプレイスのリストです:

* [Hyperspace](https://sui.hyperspace.xyz/?ref=blog.sui.io)
* [TradePort](https://www.tradeport.xyz/?ref=blog.sui.io)

### リキッドステーキング

リキッドステーキングプロトコルは、ユーザーがSUIステーキング報酬に比例して増加する資産を取得しながら、流動性と譲渡可能性を維持できるようにします。これらのプラットフォームと資産は、効率的なDeFiエコシステムの基盤となっています。

以下は、Sui上の人気のリキッドステーキングプロトコルとそれに対応するリキッドステーキングトークンのリストです:

* [Aftermath (afSUI)](https://aftermath.finance/?ref=blog.sui.io)
* [Haedal (haSUI)](https://www.haedal.xyz/?ref=blog.sui.io)
* [Volo (vSUI)](https://www.volosui.com/?ref=blog.sui.io)

## DeFiへの第一歩

SuiのDeFiエコシステムは、強力でユーザーフレンドリーな体験を提供することで際立っています。低く安定したガス代、超高速のトランザクション速度、従来の摩擦ポイントの排除の組み合わせにより、Sui DeFiは特に初心者にとってアクセスしやすくなっています。

Sui上でDeFiを行う方法を理解したので、今度はあなたが探索し、最も興味をそそるものを見つける番です!

*注意:このコンテンツは一般的な教育および情報提供を目的としており、資産、投資、または金融商品の購入、売却、または保有を推奨または推奨するものとして解釈または依拠されるべきではなく、金融、法律、または税務上のアドバイスを構成するものではありません。*
