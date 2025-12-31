Sui Foundation Blog の記事を、日本語に自然かつ正確に翻訳するためのプロンプトです。以下の要件に厳密に従ってください。

# 翻訳要件

* 原文のマークダウン構造を保持する（特に、H1 が未指定の場合でも追加しない）

* 指示文などは省略し、翻訳結果のみを出力する

* インラインコードはそのまま保持する
  例:`reduce(callbackFn, initialValue)`

* コードブロックは翻訳をスキップする。例えば、

```move
public entry fun transfer_object(obj: Object, recipient: address, ctx: &mut TxContext) {
    transfer::public_transfer(obj, recipient);
}
```

## 翻訳品質

* 技術的に正確かつ自然な日本語を使用する
* 原文の意図を正確に伝え、日本語として違和感のない表現を選ぶ
* 文体の敬語レベルは文脈に応じて判断し、一貫性を保つ

## 用語の扱い

### 翻訳せず英語のまま記載する用語

#### Sui ネットワーク・プロトコル関連

* Sui, Sui Network, Sui Blockchain, Mainnet, Testnet, Devnet, Narwhal, Bullshark, Mysticeti, Consensus Engine, Epoch, Gas, Transaction Effects Digest, Checkpoint, Validator, Full Node, Light Client

#### Move 言語・オブジェクトモデル関連

* Move, Move VM, Move Bytecode, Move Compiler, Object, Object ID, Shared Object, Owned Object, Immutable Object, Dynamic Field, Hot Potato, Capability, Witness Pattern, One-Time Witness, Programmable Transaction Block (PTB), Transaction Block, Transfer, Freeze, Share, Package, Module, Struct, Entry Function, Public Function

#### Sui 固有機能

* zkLogin, Sui Kiosk, SuiNS, Sui Bridge, DeepBook, Walrus, Sponsored Transaction, Gas Station, GraphQL, RPC, Object Display, Dynamic Fields, Event, Sui Move Analyzer

#### トークン・経済用語

* SUI Token, Staking, Delegation, Validator, Storage Fund, Storage Rebate, Gas Price, Reference Gas Price, Computation Cost, Storage Cost

#### 一般的なブロックチェーン用語

* Proof of Stake, DPoS (Delegated Proof of Stake), Sovereign, Hooks, Upgradeability, Mint, Burn, Vault, Voting Power, Governance, Mempool, Finality, Optimistic, Rollup, Zero-Knowledge Proof, Layer 1, Layer 2, Cross-Chain, Bridge, Oracle, dApp, DeFi, NFT, Smart Contract, Wallet, Account Abstraction, Multisig

### カタカナ表記に置き換える用語

* state → ステート
* transaction → トランザクション（文脈により「取引」も可）
* gas → ガス
* epoch → エポック
* node → ノード
* validator → バリデータ（文脈により「検証者」も可）
* package → パッケージ
* module → モジュール
* products → プロダクト
* consumer → コンシューマー
* treasury → トレジャリー
* client → クライアント
* network → ネットワーク
* throughput → スループット
* latency → レイテンシ

### 指定された訳語を使用する用語

* emit → 発行（イベント発行の文脈）
* mint → 発行（トークン・NFT発行の文脈）
* burn → 焼却、バーン
* stake → ステーキング、預託
* delegate → 委任
* consensus → コンセンサス、合意形成
* finality → ファイナリティ、確定性
* ownership → 所有権
* reference → 参照
* immutable → 不変
* mutable → 可変
* trust minimized → トラスト最小化された

### その他の用語

* 一般的に定訳がない技術用語は、初出時に英語（カッコ内に日本語訳）を併記し、以降は日本語訳を使用
* 必要に応じて簡潔な補足説明を加える

## 文体と読者想定

* 想定読者：Sui や Move 言語、ブロックチェーン技術に関心のある開発者・技術者・研究者
* 文体：専門的かつ読みやすく親しみやすい日本語（「です・ます」調を基本とする）
* 技術概念については、必要に応じて簡潔な補足を加える
* Sui や Move 特有の概念（Objectモデル、Programmable Transaction Blockなど）は、初出時に簡単な説明を加えることが望ましい

## 翻訳前の確認と文脈理解

* 翻訳前に全体を読み、文脈を把握すること

## 文化的配慮

* 日本の読者にとって自然な表現を選び、文化的誤解を避ける
* 必要に応じて補足説明を加える

## SEO 最適化（任意）

* 検索性を意識しつつ、キーワードを自然に埋め込む
* 見出しや構造を明確に保ち、可読性を高める

## 翻訳後の対応

* 翻訳後に全体を見直し、一貫性と品質を確認する
