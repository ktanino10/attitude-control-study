# 参考文献・出典 / References

> 🇯🇵 日本語 ・ 🇬🇧 [English](#-references-english) ｜ ⬅️ [日本語トップ](./ja/README.md) ・ [English Top](./en/README.md)

このノートは学習目的の二次資料です。図はすべて筆者が描き直したもので、**元記事の写真・図版は転載していません**。
一次情報は必ず下記の出典をご確認ください。

---

## 🇯🇵 参考文献（日本語）

### 一次資料（この学習ノートの元記事）
1. 茂渡 修平（JAXA）, 「第10章 XYZ自由自在！3軸姿勢制御モジュール誕生」,
   特集「宇宙大実験！人工衛星の製作」, **トランジスタ技術 2020年6月号**, CQ出版社, pp.110–114.
   - 雑誌ページ: <https://toragi.cqpub.co.jp/magazine/202006/>
   - 書籍情報: <https://www.cqpub.co.jp/hanbai/books/MTR/MTR202006.htm>
   - PDF版（電子版）: <https://cc.cqpub.co.jp/lib/system/doclib_item/1270/>

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
   （カルマンフィルタの原典。座学2で使用）
9. 角運動量保存則（conservation of angular momentum）・倒立振子（inverted pendulum）
   — 一般的な力学の教科書レベルの概念。参考: <https://ja.wikipedia.org/wiki/角運動量保存の法則> , <https://ja.wikipedia.org/wiki/倒立振子>

### 出典・著作権について
- 本ノートの図（`assets/` 内のSVG・Mermaid）は**すべて筆者が独自に作成**したものです。
- 元記事の写真・図版（図1〜図3など）の**著作権は JAXA／CQ出版社等の各権利者**に帰属し、本ノートには**転載していません**。
- 部品名・型番・商標は各社に帰属します。

---

<a id="-references-english"></a>

## 🇬🇧 References (English)

> 🇬🇧 English ・ 🇯🇵 [日本語](#参考文献出典--references) ｜ ⬅️ [English Top](./en/README.md) ・ [日本語トップ](./ja/README.md)

This is a study note (secondary material) for learning purposes. All figures were redrawn by the author;
**no photographs or figures from the original article are reproduced.** Always consult the primary sources below.

### Primary source (the article this note is based on)
1. Shuhei Motowatari (JAXA), "Chapter 10: XYZ at Will! Birth of a 3-Axis Attitude Control Module,"
   in the special feature "A Grand Space Experiment! Building a Satellite," **Transistor Gijutsu (Transistor Technology), June 2020**, CQ Publishing, pp.110–114. *(Japanese)*
   - Issue page: <https://toragi.cqpub.co.jp/magazine/202006/>
   - Book info: <https://www.cqpub.co.jp/hanbai/books/MTR/MTR202006.htm>
   - PDF (e-edition): <https://cc.cqpub.co.jp/lib/system/doclib_item/1270/>
   - *Author name romanization is approximate.*

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

### Attribution & copyright
- All figures in this repository (SVG/Mermaid under `assets/`) were **created independently by the author**.
- Copyright of the original article's photographs and figures belongs to **JAXA / CQ Publishing and other rights holders**; they are **not reproduced** here.
- Product names, part numbers, and trademarks belong to their respective owners.
