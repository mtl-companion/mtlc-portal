# Media Technology Learning Companion カリキュラム

Media Technology Learning Companion (mtlc) は、非ITネイティブな放送技術者の学びを支えるコンパニオン（伴走者）です。このカリキュラムは、放送技術のIT化について、皆さん自身が手を動かしながら理解を深めていくための道しるべとして用意しています。

ここに並べたコースは、皆さん自身の学習テーマに合わせて参照するためのものです。GStreamerやDockerに慣れていない方は準備シリーズから、既に経験がある方は関心のあるプレーンから、自分のペースで進めてください。

各コースの状態は、次のとおりです。

- 【公開中】参加を受け付けています
- 【作成中】教材を作成中です
- 【構想中】今後の計画です

各コースの教材リポジトリは参加者限定（非公開）です。参加希望の方はメール（mtlc.project@gmail.com）でお申し込みください。

## IP化

放送設備をIPネットワーク上に構成する技術について、理解を深めるためのコース群です。IP化は、単にSDIなどの専用インターフェースをIPに置き換えるだけではありません。メディア、制御、同期をネットワーク上で扱うことで、設備設計や運用ワークフローそのものが変化します。

IP化の学びを進める手がかりとして、以下の観点に分けて構成しています。

- 準備シリーズ：PC上で映像処理やコンテナ技術を扱うための足場
- メディアプレーンシリーズ：映像、音声、補助データの伝送を確かめる入口
- 制御プレーンシリーズ：NMOSによる発見、登録、接続管理を理解する手がかり
- 同期プレーンシリーズ：PTPによる時刻同期の動きを見るための入口
- Test & Measurementシリーズ：パケット解析、信号解析、規格適合性確認に触れるための手がかり

### 準備シリーズ

各ハンズオンで共通して使う基礎技術への入口です。既にGStreamerやDockerに慣れている方はスキップして構いません。

- 【公開中】[GStreamer イントロ](https://github.com/mtl-companion/mtlc-gstreamer-introduction)
  - GStreamerは、マルチメディア処理のためのオープンソースのパイプラインフレームワークです。
  - PC上で映像信号を扱いながら、メディアパイプラインの基本的な動きを確認します。

- 【作成中】[Docker イントロ](https://github.com/mtl-companion/mtlc-docker-introduction)
  - Dockerは、アプリケーションをコンテナとして実行するためのオープンソースプラットフォームです。
  - NMOS RegistryやGStreamerなどのツールを、再現性のある環境で動かすための足場を作ります。

### メディアプレーンシリーズ

メディアプレーンでは、映像、音声、補助データなどのメディア信号を扱います。プロ用設備では10G/25G/100G/400G Ethernetを備えた機器が使われますが、このカリキュラムではPC上で体験できる範囲を大切にし、1G Ethernet環境でも扱いやすい内容から始めます。

- 【作成中】[OSSRF ハンズオン](https://github.com/mtl-companion/mtlc-ossrf-hands-on)
  - OSSRFは、AMWAが提供するOpen Source Sender Receiver Frameworkです。
  - NMOS制御に対応したSender/Receiverを動かし、映像・音声の送受信と制御の関係を確認します。

### 制御プレーンシリーズ

制御プレーンでは、機器やソフトウェアが互いを発見し、登録し、接続を制御する仕組みに触れます。IP化における制御の主要な標準としてAMWA NMOSが使われており、特にIS-04 Discovery & RegistrationとIS-05 Connection Managementが基本になります。

- 【作成中】[easy NMOS ハンズオン](https://github.com/mtl-companion/mtlc-easy-nmos-hands-on)
  - easy NMOSは、NMOS Registry、Node、Controllerなどをコンテナで手軽に起動できる学習・検証用の環境です。
  - NMOS APIやログを確認しながら、IS-04による登録・発見と、IS-05による接続制御の動きを追います。

### 同期プレーンシリーズ

同期プレーンでは、IP化された放送設備で時刻をそろえる仕組みに触れます。放送IPシステムではPTP (Precision Time Protocol) が重要な役割を持ちます。このシリーズでは、LinuxのPTP関連ツールを使い、PC上でGrandmasterとFollowerの動作を確認します。

- 【作成中】[Sync Plane ハンズオン](https://github.com/mtl-companion/mtlc-syncplane-hands-on)
  - PC上でlinuxptpを使い、PTPの基本動作を確認します。
  - Grandmaster/Followerの構成、時刻同期の確認、SMPTE ST 2059-2プロファイル適用の流れに触れます。

### Test & Measurementシリーズ

Test & Measurement (T&M) は、IP化された放送システムを観測し、問題を切り分けるための重要な観点です。ライブ信号を直接解析するにはPCの処理性能が必要ですが、パケットキャプチャを使えば非ライブでの分析も可能です。

- 【構想中】Wireshark ハンズオン
  - ST 2110、PTP、NMOSなど、放送で使うIPパケットをWiresharkで観察します。
  - パケットを見ることに慣れ、信号や制御がネットワーク上でどう表れるかを確認します。

- 【構想中】NMOS Testing ハンズオン
  - AMWAが提供するNMOS Testingツールを使い、NMOS実装の動作確認に触れます。
  - テスト項目を見ることで、NMOS仕様が実装に何を求めているかを読み解く手がかりにします。

- 【構想中】EBU LIST ハンズオン
  - EBUが提供するLive IP Software Toolkit (LIST) を使い、ST 2110ストリームの解析に触れます。
  - PCAPをもとに、メディアストリームの状態やタイミングを確認する流れを見ていきます。

- 【構想中】JT-NM Tested ハンズオン
  - JT-NM Testedの結果の読み方や、評価項目の考え方を扱う予定です。

## ソフト化

メディア信号をソフトウェアで処理する技術について、理解を深めるためのコース群です。ソフト化は、IP化されたネットワークの上で、信号処理や設備構成をソフトウェアとして動的に組み替える方向へ進むものです。単にハードウェア処理をソフトウェアに置き換えるだけでなく、設備の構成を短時間で変更できることが重要になります。

ここでは、Dynamic Media Facility (DMF) と、その中心的な構成要素であるMedia eXchange Layer (MXL) を、手を動かしながら確認する入口として扱います。

### DMF MXLシリーズ

- 【構想中】MXL CBC/Radio-Canada ハンズオン
  - CBC/Radio-Canadaが提供するmxl-hands-onプログラムを体験するコースです。
  - コンテナ間でMXLを使ってメディアフローを扱い、DMF/MXLの基本的な考え方に触れます。

[Portalへ](README.md)
