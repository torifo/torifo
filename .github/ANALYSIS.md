# 取り組みの言語化 / Repository Analysis

> `@torifo` の公開・非公開を含む全 120+ リポジトリから、技術スタック・関心領域・成果の傾向を整理したドキュメント。プロフィール README が「ハブ」であるのに対し、本ドキュメントは「中身を体系的に振り返るログ」として配置している。
>
> *更新日: 2026-06-03*

---

## 1. 技術スタック分析

実際に手を動かしたリポジトリから抽出した使用技術。頻度ベース／規模ベースで「主軸」「準主軸」「実験段階」に分類。

### 1.1 言語

|タイプ|言語|主な用途|代表リポジトリ|
|:---|:---|:---|:---|
|**主軸**|TypeScript / JavaScript|フロントエンド、Astro/Next/SvelteKit、ブラウザ拡張|`design-*`, `animation-*`, `portfolio-astro`, `business-card`, `fade-ticae`, `bookmarklet-kit`, `llm-google-calendar-browser-extension`|
|**主軸**|Python|Discord Bot、AI/OCR、CLI、卒研周辺|`genshin-site-mediator.discord-bot`, `senior-thesis-develop`, `yarikuri.discord-bot`(private)|
|**主軸**|Go|VPS Bot、API、CLI、Tauri バックエンド|`claude-usage-bot`(private), `yarikuri.discord-bot`(private 旧実装), `cmd-mock-cli`, `snaptick-desktop-app`(Tauri 部分)|
|**準主軸**|Rust|高速ツール、Tauri、学習中|`snaptick-desktop-app`, 一部 CLI 群|
|**準主軸**|Ruby (Rails)|Web アプリ習作|`recommendation-system` 周辺|
|**実験**|Java|ゲーム実装習作|`java-game-RetroShootingGame.Genshin_Impact-Style`|
|**実験**|PHP / Laravel|Web フレームワーク学習|(skillicons に表示)|

### 1.2 フレームワーク / ランタイム

|カテゴリ|採用技術|備考|
|:---|:---|:---|
|フロントエンド|Astro 5, Next.js, React, SvelteKit, Tailwind 4|ポートフォリオ・デザイン習作・小品で使い分け|
|バックエンド|FastAPI, Flask, Express, Laravel, Rails, Gin (Go)|目的別に試行|
|デスクトップ|Tauri (Rust + Web)|`snaptick-desktop-app` で常駐型タイマーを実装|
|Bot 基盤|discord.py, discordgo (Go)|Python / Go の両方で実装経験|
|ブラウザ拡張|Chrome Extension Manifest V3|`llm-google-calendar-browser-extension`|

### 1.3 データ / インフラ

|カテゴリ|採用技術|備考|
|:---|:---|:---|
|RDB|PostgreSQL + PostGIS|地理系（旅・位置情報）で本命|
|SQLite|中間バッファ・組み込み用途|VPS ↔ PC 同期の中間ストレージ|
|NoSQL|MongoDB|（一部実験）|
|コンテナ / オーケストレ|Docker|個人開発でも常用|
|CI/CD|GitHub Actions|自動テスト・公開・Homebrew tap 更新|
|配信|Homebrew (`homebrew-snaptick` tap)|`brew install` で本人プロダクトを配布する独自パイプライン|
|サーバー|Ubuntu (VPS), Nginx|常駐 Bot / API 配信|

### 1.4 AI / LLM ツール組み込み

- **Claude Code skill 22+ 件を自作公開**（`skills-*`）：自分の開発フロー（コミット作成、テスト生成、依存監査、SQL 解析、SDD 等）を再利用可能な skill に変換
- **Claude API / Vision API**：`claude-usage-bot` で API 使用量を 5 時間ブロック単位で監視、`yarikuri.discord-bot` でレシート画像から OCR
- **Gemini Vision API**：レシート OCR の初期実装で採用、複数 AI API を目的別に比較・切替できる構成

---

## 2. 取り組み領域の分類

リポジトリを「目的別」「アウトプット型別」で分類。`@torifo` の活動は単発の試作から **シリーズ化** に明確にシフトしている。

### 2.1 🪛 Claude Code Skills シリーズ（22+ 件）

自身の開発作業を再利用可能な単位に切り出し公開している群。マーケットプレイス的にも機能。

- 開発フロー系: `skills-commit`, `skills-safe-commit`, `skills-changelog`, `skills-branch-cleanup`, `skills-refactor-safe`
- 品質系: `skills-test-gen`, `skills-secret-scan`, `skills-dep-audit`, `skills-error-trace`, `skills-mypy-fix`
- 設計系: `skills-sdd`, `skills-create-spec`, `skills-mongo-pattern`, `skills-mock-design`, `skills-react-state-review`
- 運用系: `skills-run-tests`, `skills-time-estimate`, `skills-context-snapshot-clear`, `skills-todo-aggregate`, `skills-plan-before-action`, `skills-sql-explain`
- メタ: `skills`（マスタ）, `skills-dead-code`

**意味**: AI コーディング時代における「自分の手癖を skill 化して横展開できる開発者」というポジション。

### 2.2 🎨 Brand Design Studies シリーズ（30+ 件）

フィクショナルブランド向け Web デザイン習作。`design-<業種>-<persona>` の命名規則で persona ベースで設計。

|業種|persona の例|
|:---|:---|
|アパレル|`design-apparel-minimal` / `street` / `vintage` / `trend`|
|ビューティーサロン|`design-beauty-salon-noir` / `rouge` / `wabi` / `ivoire`|
|家具|`design-furniture-luxury` / `nordic` / `urban` / `artisan`|
|アートギャラリー|`design-art-gallery-bluechip` / `emerging` / `institutional` / `digital`|
|文房具|`design-stationery-blueprint` / `character` / `mono` / `notebook`|
|ヴィンテージ雑貨|`design-vintage-sundries-kottou` / `mingei` / `showa-retro` / `zakka`|
|フィットネスジム|`design-fitness-gym-salon` / `studio` / `totonoi` / `reshape`|
|海辺の本屋|`design-seasidebookshop-fuyunagi` / `minato` / `sangosho` / `shiosai`|

**意味**: 単なる UI 模写ではなく「業種 × persona × ビジュアル言語」をパラメトリックに設計する力。エンジニアでありデザイナー的視点も持つ証拠。

### 2.3 🌀 Animation Studies シリーズ（16+ 件）

Pure HTML/CSS/JS（WebGL なし）でのインタラクションアニメーション習作。1 件 = 1 技法。

- 物理表現: `animation-blob-morph`, `animation-fluid-mask`, `animation-liquid-cursor`
- スクロール駆動: `animation-scroll-type`, `animation-layered-parallax`, `animation-wave-parallax`
- カメラ表現: `animation-iris-shutter`, `animation-camera-dive`
- 文字・図形: `animation-letter-split`, `animation-text-shuffle`, `animation-line-draw`, `animation-grid-reveal`, `animation-rect-ripple`
- カード操作: `animation-tilt-card`, `animation-card-rotate`, `animation-page-swipe`

**意味**: 「美しい挙動を最小 stack で再現する」アプローチ。WebGL に逃げず CSS/JS 基礎を磨いている。

### 2.4 ⏱ パーソナルプロダクト（リリース済 / 開発中）

実用ツール群。**Homebrew tap までセットで配信パイプラインを自前で組んでいる**のが特徴。

|プロダクト|概要|主要技術|
|:---|:---|:---|
|`snaptick-desktop-app`|常駐型メニューバータイマー（即フォーカスセッション）|Tauri (Rust + Web)|
|`homebrew-snaptick`|SnapTick の Homebrew tap|Ruby (Formula)|
|`hostra-pwa`|PWA プロダクト|TS, Service Worker|
|`wanderpath-journey`|旅の記録を地図に重ねるアプリ|PostGIS, Web|
|`business-card`|物理カード不要のデジタル名刺サイト（日没連動テーマ）|Astro 5 + Tailwind 4 (SSG)|
|`fade-ticae`|最新3手だけが残る引き分けのない三目並べ|SvelteKit|
|`bookmarklet-kit`|D&D で即インストールできるブックマークレット集|GitHub Pages|
|`nexus-sticky`|デスクトップ常駐の付箋アプリ|Tauri|
|`fudagit-web`|読み札方式で Git コマンドを覚える|Web|
|`slate-errors`|放課後の黒板で HTTP エラーを学び直す|Web|
|`meme-fortress-www`|インターネットのくだらなさを展示する Web|Web|
|`matter-reson`|問いと共鳴のテキスト系プロダクト|Web|

### 2.5 🤖 Bots & Automation

|Bot|可視性|目的|スタック|
|:---|:---|:---|:---|
|`slack-times-butler-bot`|public|times に流した発言を資産化する執事|—|
|`discord-vc-watcher-bot`|public|Discord VC 監視|—|
|`genshin-site-mediator.discord-bot`|public|原神関連サイト情報の集約|Python|
|`llm-google-calendar-browser-extension`|public|LLM 経由で Google Calendar 操作|Chrome Extension|
|`claude-usage-bot`|**private**|Claude AI 使用量を Discord に統計表示。Win/Linux/VPS の `/root/.claude/projects` 全環境対応、5 時間 API リミットを色分け監視、Cron 自動レポート|Go + discordgo|
|`yarikuri.discord-bot`|**private**|家計管理 Bot。レシート画像を Discord に投稿 → AI OCR で支出データ化 → VPS Gin API（SQLite 中間バッファ） → PC の PostgreSQL に最終書き込み、という 3 段アーキテクチャ|Python (Bot) + Go (Gin API) + PostgreSQL|
|`Bot_revise`|**private**|過去の Discord Bot 実装の改訂版（草稿段階）|—|

**意味**: Bot を単一スクリプトではなく **VPS / PC / API / DB を含む分散アーキテクチャ**として設計できる。`yarikuri.discord-bot` の構成判断（VPS 側 API を中間バッファに置く理由を表で整理）は特に練度が高い。

### 2.6 🎓 学術・卒研系

|リポジトリ|概要|
|:---|:---|
|`senior-thesis-develop`|卒業研究|
|`university-credit-checker`|単位確認ツール|
|`recommendation-system`|推薦システム実験|
|`lab-marp-decks`|研究室発表用 Marp スライド集|

### 2.7 🎮 ゲーム・原神系

|リポジトリ|概要|
|:---|:---|
|`java-game-RetroShootingGame.Genshin_Impact-Style`|Java 製レトロシューティング（原神スタイル）|
|`TravelerA-Genshin-DB-Manager-WebApp`|原神 DB 管理 Web アプリ|
|`genshin-site-mediator.discord-bot`|原神情報集約 Bot|

### 2.8 🌐 地理 / ポートフォリオ系

|リポジトリ|概要|
|:---|:---|
|`portfolio-astro`, `Portfolio`|ポートフォリオサイト本体|
|`jgeo`|地理系（推定）|
|`prism-flags`|国旗系（推定）|
|`anchor-ports`|港・拠点系|
|`tailwind-jp-blueprint`|日本語向け Tailwind ボイラープレート|

### 2.9 🧪 その他の習作 / 単発実験

`shikuty`, `wording-stock`, `portion-flow`, `room-design`, `echo-news`, `freeslot-allocator-app`, `reachtrail-app`, `gahama`, `cataloger-shelf` / `cataloger-shelf.dev`, `cmd-mock-cli`, `welfare-optimizer-tool`, `serendipity-encount`, `astral-drive`, `webgl-design`, `discord-vc-watcher-bot` … 名前から「思いついたら即コード化」のスタンスが見える。

---

## 3. 時系列の進化

| 期間 | 主な動き |
|:---|:---|
| 2022.04 – 2022.08 | 大学入学 → 個人開発スタート |
| 2023 | Python 天気 CLI、初期スクリプト |
| 2024 | Discord Bot 群、Java ゲーム、Bot_revise 草稿 |
| 2025 | Web Application 公開、claude-usage-bot 開発、wanderpath-journey 着手 |
| 2026.03 | 卒業 |
| **2026.04 – 06** | **加速期**: `skills-*` 大量公開、`design-*` シリーズ化、`animation-*` シリーズ化、SnapTick 本体 + Homebrew tap、Astro 名刺サイト、Discord×Slack の役割分担、3 段アーキテクチャの Bot 設計 |

**変化のポイント**:
1. 単発スクリプト → **シリーズ化（命名規則・persona・カタログ化）**
2. ローカルツール → **OSS 配信パイプライン（GitHub Actions → Homebrew tap）**
3. 単一言語 → **目的別の多言語使い分け（Go × Python × Web × Rust）**
4. AI を「使う」 → **AI ツール（Claude Code skill）を「作って横展開」**

---

## 4. 強み・成果の結晶

|観点|具体的根拠|
|:---|:---|
|**量と継続性**|Public 100+ / Total 120+ リポジトリ、日次レベルの push（streak）|
|**横断的なスタック**|TS / Python / Go / Rust / Ruby / Java を目的別に使い分け、PostgreSQL + PostGIS で地理データ、Tauri でデスクトップ|
|**シリーズ化思考**|`skills-*` 22+, `design-*` 30+, `animation-*` 16+ — 単発で終わらず体系化する設計判断|
|**OSS 配信力**|GitHub Pages / Homebrew tap / Astro SSG など、配布手段を自前で組める|
|**AI 開発の前線**|Claude Code 用 skill を 22+ 自作・公開、AI OCR を本番アーキに組み込み、Claude API 使用量を独自 Bot で監視|
|**デザイン感覚**|30+ ブランド design 習作 + 16+ animation 習作。エンジニア × デザイナー視点|
|**分散アーキ設計**|`yarikuri.discord-bot` の VPS Bot × Gin 中間 API × PC PostgreSQL の 3 段構成、`claude-usage-bot` の Win/Linux/VPS マルチ環境統合|
|**学術 → 実務の橋渡し**|東京都立大 情報科学科卒、卒研系リポジトリと実務系リポジトリが地続き|

---

## 5. 補足

- **Private 3 件の本質**: 個人運用に紐づくシークレットや家計データを含むため private 維持（コードベース自体は十分にプロダクションレベル）
- **公開判断の傾向**: 「再利用可能なツール」「ライブラリ」「習作」は public、「個人運用 Bot」「家計データ」は private
- **次の関心領域（README より）**: Rust 深化 / WebAssembly / 分散システム
- **連絡先**: `progbot.clover@gmail.com` (開発) / `occupation.clover@gmail.com` (採用)

---

> 📌 本ドキュメントは「リポジトリの中身を体系的に振り返るログ」として `.github/` 配下に配置。  
> プロフィール README（リンクハブ）と [ポートフォリオ](https://portorifo.riumu.net)（採用・成果プレゼン）と本ドキュメント（内省・体系化）の **3 層構成** で `@torifo` を表現する。
