# 元記事（写真）との対応表 🗂️

**🌐 言語 / Language:** 日本語（現在） ・ [English](../en/coverage-map.md) ｜ [🏠 トップ](../README.md)

送っていただいた写真＝**トランジスタ技術 2020年6月号 短期連載「XYZ 3軸姿勢制御モジュールの運動方程式とマイコン制御」【第1回】1次元倒立振子のメカニズム（巳谷 真司／JAXA, pp.121–127）** の内容を、
このノートの**どこで・どのレベルで解説したか**を一覧にしました。写真そのものは載せず、図は**すべて自分で描き直し**ています（→ [出典・参考文献](../REFERENCES.md)）。

> レベルの見方：🟢＝中学生向け（やさしく） ／ 🔵＝もう少し知りたい人向け（くわしく・数式あり）

---

## 記事の流れ順の対応表

| # | 元記事の項目・図 | 内容 | 解説した場所 | レベル |
|---|---|---|---|---|
| 1 | リード文／モジュールの狙い | 1辺10cmに全部入れ、小型・軽量・高密度・低コストで**地上実演** | [`session-1-overview/04-jaxa-module.md`](./session-1-overview/04-jaxa-module.md)、[`README.md`](./README.md) | 🟢 |
| 2 | Int-Ball との関係 | 宇宙ステーション内の撮影ロボの姿勢制御を地上で見せる教材 | [`session-1-overview/02-why-needed.md`](./session-1-overview/02-why-needed.md) | 🟢 |
| 3 | こうのとり（HTV）などの実例 | 正しい向きが必要な宇宙機の例 | [`session-1-overview/02-why-needed.md`](./session-1-overview/02-why-needed.md) | 🟢 |
| 4 | 写真2・写真3：起き上がり〜倒立のシーケンス | 寝た状態→辺で倒立→頂点で倒立 | [`session-1-overview/04-jaxa-module.md`](./session-1-overview/04-jaxa-module.md)（図 `standup-sequence.svg`） | 🟢 |
| 5 | 3つの機能 | 辺による倒立／起き上がり／頂点による倒立 | [`session-1-overview/04-jaxa-module.md`](./session-1-overview/04-jaxa-module.md) | 🟢🔵 |
| 6 | 姿勢制御の基礎（3軸・RPY） | 姿勢とは・XYZ軸・ロール/ピッチ/ヨー | [`session-1-overview/01-what-is-attitude.md`](./session-1-overview/01-what-is-attitude.md) | 🟢🔵 |
| 7 | リアクションホイールの原理 | 角運動量保存則・作用反作用・回転いす | [`session-1-overview/03-how-to-turn-in-space.md`](./session-1-overview/03-how-to-turn-in-space.md)（図 `reaction-wheel-principle.svg`） | 🟢🔵 |
| 8 | 電磁ブレーキ／起き上がり | 高速回転を急停止して瞬間大トルク | [`session-1-overview/03-how-to-turn-in-space.md`](./session-1-overview/03-how-to-turn-in-space.md)、[`04-jaxa-module.md`](./session-1-overview/04-jaxa-module.md) | 🟢🔵 |
| 9 | アンローディング | 回しすぎたホイールを戻す操作 | [`session-1-overview/03-how-to-turn-in-space.md`](./session-1-overview/03-how-to-turn-in-space.md) | 🟢🔵 |
| 10 | 図5：制御システム（システム・ブロック図） | PSoC中心の全体配線・信号の流れ | [`reference/system-block.md`](./reference/system-block.md) | 🟢🔵 |
| 11 | 各インターフェース | I²C・UART・D-A・パルスカウント・MOSFET・GPIO の役割 | [`reference/interfaces.md`](./reference/interfaces.md) | 🟢🔵 |
| 12 | I²Cが3系統ある理由 | MPU-6050のアドレスが2個→1本に2個まで→6個で3本 | [`reference/interfaces.md`](./reference/interfaces.md)、[`system-block.md`](./reference/system-block.md) | 🔵 |
| 13 | 写真1：モジュールの外観／内部 | ホイールの直交配置・IMU分散・電池と基板の詰め方 | [`reference/mechanical.md`](./reference/mechanical.md)（図 `module-cube.svg`） | 🟢🔵 |
| 14 | センサ（IMU 6個） | 加速度センサ＋ジャイロ、MPU-6050、6軸×6 | [`session-1-overview/05-parts-overview.md`](./session-1-overview/05-parts-overview.md)、[`reference/parts-list.md`](./reference/parts-list.md) | 🟢 |
| 15 | 姿勢推定（カルマン等） | 2つのセンサの合体（センサフュージョン） | [`GLOSSARY.md`](./GLOSSARY.md)、[`session-3-3d/`](./session-3-3d/README.md)（座学3で解説） | 🟢🔵 |
| 16 | アクチュエータ | モータ（maxon EC 45 flat 30W）・ドライバ・電磁ブレーキ | [`session-1-overview/05-parts-overview.md`](./session-1-overview/05-parts-overview.md)、[`reference/parts-list.md`](./reference/parts-list.md) | 🟢 |
| 17 | マイコン | PSoC 5LP・ARM Cortex-M3・FreeRTOS・UDB | [`reference/system-block.md`](./reference/system-block.md)、[`GLOSSARY.md`](./GLOSSARY.md) | 🟢🔵 |
| 18 | 電源 | リチウムポリマ電池 7.4V×2 | [`session-1-overview/05-parts-overview.md`](./session-1-overview/05-parts-overview.md)、[`reference/parts-list.md`](./reference/parts-list.md) | 🟢 |
| 19 | トルク計算 | 重力トルク $`T=mgl\sin\theta`$、モータ定格の約8倍 | [`session-1-overview/04-jaxa-module.md`](./session-1-overview/04-jaxa-module.md)（🔵） | 🔵 |
| 20 | 参考文献（maxonデータシート等） | 記事が引用する部品資料 | [`REFERENCES.md`](../REFERENCES.md) | — |

---

## 補足：3回の座学への割りふり

- 元記事の第1回（写真の内容）は概要中心なので、運動方程式とマイコン制御は**第2回**、3次元への拡張と姿勢推定は**第3回**で扱います。
- 第1回は、全体像と基本用語を中心にまとめています。各項目の解説場所は上の表のとおりです。

📎 用語の意味は [`GLOSSARY.md`](./GLOSSARY.md)、出典は [`REFERENCES.md`](../REFERENCES.md) を参照してください。
