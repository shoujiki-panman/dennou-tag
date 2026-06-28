# 電脳タグ — Kickoff（現実に"正直なタグ"を貼る）

Date: 2026-06-28 / 探索・学習プロジェクト（締切なし。Catalyst応募とは別、応募後の本命の一つ）
このファイル＝別スレの頭で読ませる仕様書。開始手順は `START-HERE.md`。

## ゴール
「**現実の場所に"正直なタグ"を貼って、あとで同じ場所で見られる**」を、**自分で理解しながら段階的に**作る。
最終ビジョン＝電脳コイル的な共有AR（場所・モノ・人に情報が貼り付く）。社会レイヤー（3役・信頼）は後半。

## 最優先（Twitterクローンの教訓）
**理解 > 完成。各フェーズで「動いた」を自分の目で確認してから次へ。** AIにコードを全部書かせない（私が手を動かす／なぜを説明できる）。
作り直しでなく、**簡単な所から1機能ずつ確認**して積む（＝Taste Glassで欠けていた"各機能の確認"を最初からやる）。

## 電脳タグの分解（3層）
1. **場所に貼る（アンカー技術）** — GPS/緯度経度 or VPSで現実座標に固定
2. **保存・共有（バックエンド）** — タグ(場所＋本文＋持ち主)を保存し、再表示・他端末で見る
3. **社会レイヤー（信頼/3役）** — 書く/残す/消す。**Twitterクローンの RLS・所有がそのまま効く**（[[project-electronic-tag-social-layer]]）

## フェーズ計画（各フェーズ "✅できたら次"）
| Phase | 内容 | 確認(✅) | 難度 |
|---|---|---|---|
| P0 | 準備・方針：学習目的の確認、参考リポを1つ読む、まずWeb位置ARで始めると決める | 何をどう真似るか言語化できた | 易 |
| P1 | **最速で"動く"**：Web位置AR(AR.js/LocAR.js)で、自分のいる緯度経度にタグ1個を表示 | スマホのブラウザで自分の場所にタグが見える | 易 |
| P2 | **保存・再表示**：タグ(緯度経度＋本文)をSupabaseに保存→リロード/別端末でも同じ場所に出る | DB保存したタグが再表示される | 中 |
| P3 | **【最重要】所有と権限**：user_id＋RLSで「自分のタグだけ編集/削除、他人のは読めるが消せない」 | 他人のタグを消そうとして弾かれる/自分のは消せる | 中 |
| P4 | （任意・難）**精度↑/Android化**：ARCore Geospatialで粗いGPS→高精度。実機必要 | 看板付近にタグが安定して出る | 難 |
| P5 | **社会レイヤー構想**：3役(書く/残す/消す)・信頼の浮き沈みを設計文書化（実装は段階） | 設計が1枚にまとまる | 設計 |

- **メインゴール**：P1〜P3（Webで"貼る→保存→所有"）。ここまでで電脳タグの本質は検証できる。
- P4(高精度AR/実機)・P5(社会レイヤー)は余力・別日。最初から1億人/cm精度を狙わない（早すぎる最適化を避ける＝Twitter第12章の学び）。

## 参考リポジトリ（GitHub調べ済み 2026-06-28）
### まさに電脳タグ（空間にメモを貼る）
- jparismorgan/AzureSpatialAnchors-NotesAR ★27 — 現実に永続メモ（コンセプト直撃）
- zikriharis/MarkerlessARStickyNotes — Lightship VPSで永続付箋
- Sunidhishree/ARspacesharee — WebXRでリンクを開くだけで3Dメモを落とす
### 場所に固定（Android本命）
- morhenny/ar-navigation ★33 **Kotlin** — ARCore Cloud Anchors + Geospatial（スタック最近接）
- google-ar/arcore-unity-extensions ★394 — Geospatial Creator（公式）
- anujdutt9/ARCore-CloudAnchors ★13 — アンカーをFirebaseに保存/取得（②の型）
### Webで最速プロトタイプ（P1で使う）
- AR-js-org/AR.js ★5955 / AR-js-org/locar.js / nicolocarpignoli/GeoAR.js — 緯度経度にARを置く、インストール不要
### 共有AR・標準（社会レイヤー/構想の裏付け）
- OpenArCloud/sparcl ・ oscp-spatial-content-discovery ・ oscp-geopose-protocol
### Android XR 直系
- drumath2237/AndroidXR-BookOfFoods-Sample（Kotlin/Jetpack XR）

## 正直な難所（先に知る）
- **精度の段階**：GPSだけ＝数m、看板にピタッ＝VPS必要（ARCore GeospatialはStreet Viewのある場所のみ高精度）。
- **共有・永続・複数人同期**は本質的に難しい（ドリフト/カバレッジ）。**P1は"粗い位置でまず貼れる"から**。
- だからWeb位置ARで本質（貼る→保存→所有）を先に検証し、高精度・実機は後。

## 進め方ルール（厳守）
- コードを全部書かない。私が書くのを手伝い、間違い・ハマりどころを指摘。AI作でも「なぜ」を説明できる状態に。
- 1フェーズずつ。各フェーズ終了で「今日の学び」を `LEARNING-LOG.md` に1〜2行。
- 既存の学び（Twitterクローンの Supabase/RLS/所有）を積極的に再利用する。
