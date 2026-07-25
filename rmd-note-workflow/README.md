# RMD Note Workflow

[中文](#中文版本) | [English](#english-version) | [日本語](#日本語版本)

---

## English Version

**A platform-agnostic Rmd writing workflow plugin** that orchestrates collaborative content creation across four concurrent phases: architecture, writing, review, and compilation. Built for teams producing structured technical and academic documents with automated quality gates and environment management.

### Features

- **Interactive Bootstrap** — Zero-to-project setup in one command
- **Concurrent Pipeline** — 4-phase workflow: Architect → Writer → Review → Compile
- **Quality Assurance** — RE:KCTSW narrative framework + structured FAIL thresholds
- **Smart Compilation** — Concurrent builds + automatic retry + format validation
- **Dependency Management** — Auto-detect and lock R, Python, and LaTeX environments

### Quick Start

#### 1. Bootstrap (One-Command Setup)

```bash
python scripts/orchestrator.py bootstrap
```

Answers interactive prompts to auto-generate `config.json` and project structure.

#### 2. Production Pipeline

```bash
# Step 1: Architect (outline generation)
python scripts/orchestrator.py architect --lessons L01-L21

# Step 2: Write (concurrent batch processing)
python scripts/orchestrator.py write --batch B0

# Step 3: Review (5-role concurrent review)
python scripts/orchestrator.py review --batch B0

# Step 4: Compile (with format validation)
python scripts/compiler.py --dir Notes/课程大纲 --format pdf
```

### Project Structure

```
rmd-workflow/
├── core/           Prompts, quality standards, templates
├── scripts/        Orchestration, compilation, validation
├── plugins/        Environment management (extensible)
└── adapters/       Platform adapters (OpenCode/Claude)
```

### Configuration

See `config.json` schema in design documentation.

### Extending

Create a new environment plugin:

1. Add a `.py` file in `plugins/`
2. Implement the `EnvPlugin` interface

---

## 中文版本

**平台无关的 Rmd 写作工作流插件**，支持跨四个并发阶段的协作内容创作：架构、写作、审查和编译。专为生成结构化技术和学术文档的团队设计，具有自动质量检测和环境管理。

### 功能

- **交互式引导** — 一条命令快速搭建项目
- **并发流水线** — 4 阶段工作流：Architect → Writer → Review → Compile
- **质量控制** — RE:KCTSW 叙事框架 + 结构化 FAIL 阈值
- **智能编译** — 并发构建 + 自动重试 + 格式验证
- **依赖管理** — R/Python/LaTeX 环境自动检测和锁定

### 快速开始

#### 1. 从零搭建（一条命令）

```bash
python scripts/orchestrator.py bootstrap
```

按提示回答项目问题，自动生成 `config.json` 和目录结构。

#### 2. 生产流水线

```bash
# 步骤 1：架构师（大纲生成）
python scripts/orchestrator.py architect --lessons L01-L21

# 步骤 2：写手（并发批处理）
python scripts/orchestrator.py write --batch B0

# 步骤 3：审查（5 角色并发）
python scripts/orchestrator.py review --batch B0

# 步骤 4：编译（格式验证）
python scripts/compiler.py --dir Notes/课程大纲 --format pdf
```

### 目录结构

```
rmd-workflow/
├── core/           提示词、质量标准、模板
├── scripts/        编排、编译、验证
├── plugins/        环境管理（可扩展）
└── adapters/       平台适配（OpenCode/Claude）
```

### 配置

详见 `config.json` schema（设计文档）。

### 扩展插件

创建新环境插件：

1. 在 `plugins/` 下创建新 `.py` 文件
2. 实现 `EnvPlugin` 接口

---

## 日本語版本

**プラットフォーム非依存の Rmd ライティングワークフロープラグイン**。4 つの並行フェーズ（アーキテクチャ、ライティング、レビュー、コンパイル）を横断的にサポートします。構造化された技術および学術文書を作成するチーム向けに設計されており、自動品質ゲートと環境管理機能を備えています。

### 機能

- **インタラクティブブートストラップ** — ワンコマンドでプロジェクト生成
- **並行パイプライン** — 4 フェーズワークフロー：Architect → Writer → Review → Compile
- **品質保証** — RE:KCTSW ナラティブフレームワーク + 構造化 FAIL 閾値
- **スマートコンパイル** — 並行ビルド + 自動リトライ + フォーマット検証
- **依存関係管理** — R/Python/LaTeX 環境の自動検出とロック

### クイックスタート

#### 1. ブートストラップ（ワンコマンドセットアップ）

```bash
python scripts/orchestrator.py bootstrap
```

インタラクティブプロンプトに答えると、`config.json` とプロジェクト構造が自動生成されます。

#### 2. 本番パイプライン

```bash
# ステップ 1：アーキテクト（アウトライン生成）
python scripts/orchestrator.py architect --lessons L01-L21

# ステップ 2：ライター（並行バッチ処理）
python scripts/orchestrator.py write --batch B0

# ステップ 3：レビュー（5 ロール並行）
python scripts/orchestrator.py review --batch B0

# ステップ 4：コンパイル（フォーマット検証）
python scripts/compiler.py --dir Notes/課程大綱 --format pdf
```

### プロジェクト構造

```
rmd-workflow/
├── core/           プロンプト、品質基準、テンプレート
├── scripts/        オーケストレーション、コンパイル、検証
├── plugins/        環境管理（拡張可能）
└── adapters/       プラットフォームアダプター（OpenCode/Claude）
```

### 設定

`config.json` スキーマの詳細については、設計ドキュメントを参照してください。

### 拡張

新しい環境プラグインを作成します：

1. `plugins/` に新しい `.py` ファイルを追加
2. `EnvPlugin` インターフェースを実装

---

## License

MIT License - See LICENSE file for details
