# 参考文献・出典 / References

> 🇯🇵 日本語 ・ 🇬🇧 [English](#-references-english) ｜ ⬅️ [日本語トップ](./ja/README.md) ・ [English Top](./en/README.md)

このノートは学習目的の二次資料です。図はすべて筆者が描き直したもので、**元記事の写真・図版は転載していません**。
一次情報は必ず下記の出典をご確認ください。

---

## 🇯🇵 参考文献（日本語）

### 一次資料（この学習ノートの元記事）
巳谷 真司（JAXA）, 短期連載「XYZ 3軸姿勢制御モジュールの運動方程式とマイコン制御」（全3回）, CQ出版社.
1. 【第1回】1次元倒立振子のメカニズム（副題：自立で起き上がって静かに倒立する立方体）,
   **トランジスタ技術 2020年6月号**, pp.121–127.
   - 雑誌ページ: <https://toragi.cqpub.co.jp/magazine/202006/>
   - 書籍情報: <https://www.cqpub.co.jp/hanbai/books/MTR/MTR202006.htm>
   - PDF版（電子版, 号まるごと）: <https://cc.cqpub.co.jp/lib/system/doclib_item/1270/>
2. 【第2回】1次元倒立振子の運動方程式とマイコン制御,
   **トランジスタ技術 2020年7月号**, pp.131–136.
   - 雑誌ページ: <https://toragi.cqpub.co.jp/magazine/202007/>
   - 書籍情報: <https://www.cqpub.co.jp/hanbai/books/MTR/MTR202007.htm>
   - PDF版（電子版, 号まるごと）: <https://cc.cqpub.co.jp/lib/system/doclib_item/1273/>
3. 【第3回】3次元の姿勢制御,
   **トランジスタ技術 2020年8月号**, pp.140–149.
   - 雑誌ページ: <https://toragi.cqpub.co.jp/magazine/202008/>
   - 書籍情報: <https://www.cqpub.co.jp/hanbai/books/MTR/MTR202008.htm>
   - PDF版（電子版, 号まるごと）: <https://cc.cqpub.co.jp/lib/system/doclib_item/1277/>

   - 著者情報（KAKEN 研究者DB）: <https://nrid.nii.ac.jp/ja/nrid/1000000747446/>

### 元記事が引用している一次文献（The Cubli）
- M. Gajamohan, M. Merz, I. Thommen, R. D'Andrea, "The Cubli: A Cube that can Jump Up and Balance,"
  *2012 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS)*, 2012年10月7–12日, Vilamoura, ポルトガル.
- M. Gajamohan, M. Muehlebach, T. Widmer, R. D'Andrea, "The Cubli: A Reaction Wheel Based 3D Inverted Pendulum,"
  *European Control Conference (ECC)*, pp.268–274, 2013.

### 関連するJAXAの宇宙機・ロボット
2. JAXA「Int-Ball（JEM自律移動型船内カメラ）」
   - 英語: <https://iss.jaxa.jp/en/kiboexp/news/170714_int_ball_en.html>
   - Int-Ball2（有人宇宙技術部門）: <https://humans-in-space.jaxa.jp/>
3. JAXA「宇宙ステーション補給機『こうのとり』（HTV）」
   - 日本語: <https://iss.jaxa.jp/htv/> ／ <https://www.jaxa.jp/projects/rockets/htv/>
   - 英語: <https://global.jaxa.jp/projects/rockets/htv/index.html>

### 主要部品（データシート・製品ページ）
4. **TDK InvenSense MPU-6050** — 6軸（3軸加速度＋3軸ジャイロ）MEMSセンサ。I²Cアドレスは AD0 ピンで 0x68／0x69。
   - <https://invensense.tdk.com/products/motion-tracking/6-axis/mpu-6050/>
5. **maxon EC 45 flat**（Ø42.9 mm, ブラシレス, 30 W, ホールセンサ付, 型番 200142）— トルク定数 ≈ 25.5 mNm/A。
   - <https://www.maxongroup.com/maxon/view/product/motor/ecmotor/ecflat/ecflat45/200142>
   - ※ 記事が引用する一次文献（maxonモータのデータシート）に相当。
6. **Infineon（旧Cypress）PSoC 5LP**（CY8C58 ファミリ, ARM **Cortex-M3** コア＋UDB）。
   - 製品ページ: <https://www.infineon.com/cms/en/product/microcontroller/psoc/psoc-5lp-arm-cortex-m3/psoc-5lp-cy8c58lp-family/>
7. **FreeRTOS**（リアルタイムOS, 現在は Amazon Web Services 管理）。
   - <https://www.freertos.org/>

### 概念・理論の参考
8. R. E. Kálmán, "A New Approach to Linear Filtering and Prediction Problems,"
   *Transactions of the ASME – Journal of Basic Engineering*, Vol.82, No.1, pp.35–45, 1960. DOI: 10.1115/1.3662552.
   （カルマン・フィルタの原典。カルマン正準分解も同氏の名にちなむ→座学3）
9. 角運動量保存則（conservation of angular momentum）・倒立振子（inverted pendulum）
   — 一般的な力学の教科書レベルの概念。参考: <https://ja.wikipedia.org/wiki/角運動量保存の法則> , <https://ja.wikipedia.org/wiki/倒立振子>

### 関連プロジェクト（手を動かす例）
- **実機の倒立振子を作った例（筆者の別プロジェクト）**: `ktanino10/copilot-cli-inverted-pendulum-m5stick`
  - リポジトリ: <https://github.com/ktanino10/copilot-cli-inverted-pendulum-m5stick>
  - M5StickC Plus で自立バランスする1次元倒立振子。**PID制御＋カルマンフィルタ＋WebUI** を、GitHub Copilot CLI との対話でファーム開発・書き込み・デバッグまで行った実践記録。
  - ブラウザ・デモ（実機不要）: <https://ktanino10.github.io/copilot-cli-inverted-pendulum-m5stick/>
  - ※ この学習ノートとは独立した趣味プロジェクトで、上記トランジスタ技術の連載とは直接の関係はありません。座学1〜2の「1次元倒立振子」を手を動かして体験する際の参考としてどうぞ。

### 出典・著作権について
- 本ノートの図（`assets/` 内のSVG・Mermaid）は**すべて筆者が独自に作成**したものです。
- 元記事の写真・図版の**著作権は、個別に記載のある場合を除き JAXA**（一部は CQ出版社等の各権利者）に帰属し、本ノートには**転載していません**。
- 部品名・型番・商標は各社に帰属します。

---

<a id="-references-english"></a>

## 🇬🇧 References (English)

> 🇬🇧 English ・ 🇯🇵 [日本語](#参考文献出典--references) ｜ ⬅️ [English Top](./en/README.md) ・ [日本語トップ](./ja/README.md)

This is a study note (secondary material) for learning purposes. All figures were redrawn by the author;
**no photographs or figures from the original article are reproduced.** Always consult the primary sources below.

### Primary source (the article this note is based on)
Shinji Mitani (巳谷 真司, JAXA), short serial "Equations of Motion and Microcontroller Control of an XYZ 3-Axis Attitude Control Module" (3 parts), CQ Publishing. *(Japanese)*
1. **Part 1: Mechanism of a 1-D Inverted Pendulum** (subtitle: "A cube that stands itself up and balances quietly"),
   **Transistor Gijutsu (Transistor Technology), June 2020**, pp.121–127.
   - Issue page: <https://toragi.cqpub.co.jp/magazine/202006/>
   - Book info: <https://www.cqpub.co.jp/hanbai/books/MTR/MTR202006.htm>
   - PDF (e-edition, full issue): <https://cc.cqpub.co.jp/lib/system/doclib_item/1270/>
2. **Part 2: Equations of Motion and Microcontroller Control of the 1-D Inverted Pendulum**,
   **Transistor Gijutsu, July 2020**, pp.131–136.
   - Issue page: <https://toragi.cqpub.co.jp/magazine/202007/>
   - Book info: <https://www.cqpub.co.jp/hanbai/books/MTR/MTR202007.htm>
   - PDF (e-edition, full issue): <https://cc.cqpub.co.jp/lib/system/doclib_item/1273/>
3. **Part 3: 3-D Attitude Control**,
   **Transistor Gijutsu, August 2020**, pp.140–149.
   - Issue page: <https://toragi.cqpub.co.jp/magazine/202008/>
   - Book info: <https://www.cqpub.co.jp/hanbai/books/MTR/MTR202008.htm>
   - PDF (e-edition, full issue): <https://cc.cqpub.co.jp/lib/system/doclib_item/1277/>

   - Author profile (KAKEN researcher DB): <https://nrid.nii.ac.jp/nrid/1000000747446/>

### Primary references cited by the article (The Cubli)
- M. Gajamohan, M. Merz, I. Thommen, R. D'Andrea, "The Cubli: A Cube that can Jump Up and Balance,"
  *2012 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS)*, Oct 7–12, 2012, Vilamoura, Portugal.
- M. Gajamohan, M. Muehlebach, T. Widmer, R. D'Andrea, "The Cubli: A Reaction Wheel Based 3D Inverted Pendulum,"
  *European Control Conference (ECC)*, pp.268–274, 2013.

### Related JAXA spacecraft / robots
2. JAXA "Int-Ball (JEM Internal Ball Camera)"
   - <https://iss.jaxa.jp/en/kiboexp/news/170714_int_ball_en.html>
   - Int-Ball2: <https://humans-in-space.jaxa.jp/>
3. JAXA "H-II Transfer Vehicle KOUNOTORI (HTV)"
   - <https://global.jaxa.jp/projects/rockets/htv/index.html>

### Key components (datasheets / product pages)
4. **TDK InvenSense MPU-6050** — 6-axis (3-axis accel + 3-axis gyro) MEMS. I²C address 0x68/0x69 via AD0 pin.
   - <https://invensense.tdk.com/products/motion-tracking/6-axis/mpu-6050/>
5. **maxon EC 45 flat** (Ø42.9 mm, brushless, 30 W, with Hall sensors, part 200142) — torque constant ≈ 25.5 mNm/A.
   - <https://www.maxongroup.com/maxon/view/product/motor/ecmotor/ecflat/ecflat45/200142>
6. **Infineon (formerly Cypress) PSoC 5LP** (CY8C58 family, ARM **Cortex-M3** core + UDB).
   - <https://www.infineon.com/cms/en/product/microcontroller/psoc/psoc-5lp-arm-cortex-m3/psoc-5lp-cy8c58lp-family/>
7. **FreeRTOS** (real-time OS, maintained by Amazon Web Services).
   - <https://www.freertos.org/>

### Concept / theory references
8. R. E. Kálmán, "A New Approach to Linear Filtering and Prediction Problems,"
   *Transactions of the ASME – Journal of Basic Engineering*, 82(1):35–45, 1960. DOI: 10.1115/1.3662552.
9. Conservation of angular momentum; inverted pendulum — standard mechanics topics.
   Ref: <https://en.wikipedia.org/wiki/Angular_momentum> , <https://en.wikipedia.org/wiki/Inverted_pendulum>

### Related project (hands-on example)
- **A working inverted pendulum the author built (separate personal project)**: `ktanino10/copilot-cli-inverted-pendulum-m5stick`
  - Repository: <https://github.com/ktanino10/copilot-cli-inverted-pendulum-m5stick>
  - A 1-D self-balancing inverted pendulum on the M5StickC Plus. **PID control + Kalman filter + a web UI**, with firmware development, flashing, and debugging all carried out through GitHub Copilot CLI.
  - Browser demo (no hardware needed): <https://ktanino10.github.io/copilot-cli-inverted-pendulum-m5stick/>
  - Note: this is an independent hobby project, not affiliated with the Transistor Technology serial above. Offered as a hands-on companion for the "1-D inverted pendulum" covered in Sessions 1–2.

### Attribution & copyright
- All figures in this repository (SVG/Mermaid under `assets/`) were **created independently by the author**.
- Copyright of the original article's photographs and figures belongs to **JAXA** (except where individually noted; some rights held by CQ Publishing and others); they are **not reproduced** here.
- Product names, part numbers, and trademarks belong to their respective owners.
