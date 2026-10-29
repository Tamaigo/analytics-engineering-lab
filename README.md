# Analytics Engineering Lab

Analytics Engineeringの一連の開発プロセスを実践するためのリポジトリです。

## Purpose

BigQuery上のデータを対象として、以下のプロセスを実践します。

- Source profiling
- Data documentation
- Data modeling with Dataform
- Data quality testing
- Analytics-ready data production
- AI / Analytics Agent向けデータ設計

## Initial Data Source

`bigquery-public-data.bbc_news.fulltext`

BBC News Public Datasetを最初のモデリング対象とします。

## Modeling Layers

```text
Source
  ↓
Staging
  ↓
Intermediate
  ↓
Marts
```

### Source

外部データとの境界およびSource定義を管理します。

### Staging

Sourceの意味を大きく変更せず、命名・型・表記などを標準化します。

### Intermediate

分析に必要な再利用可能な変換・特徴量・ビジネスロジックを構築します。

### Marts

分析者、BI、Analytics Agentなどが利用する分析用モデルを提供します。

## Repository Structure

```text
.
├── definitions/
│   ├── sources/          # Source declarations
│   ├── staging/          # Source normalization
│   ├── intermediate/     # Reusable transformations
│   ├── marts/            # Analytics-ready models
│   └── assertions/       # Data quality assertions
├── analyses/             # Exploratory and profiling SQL
├── docs/
│   ├── architecture/     # Data architecture
│   ├── sources/          # Source documentation
│   ├── models/           # Model documentation
│   └── decisions/        # Architecture Decision Records
└── includes/             # Reusable Dataform code
```

## Development Flow

```text
Profile
  ↓
Document
  ↓
Model
  ↓
Test
  ↓
Review
  ↓
Publish
```

## Modeling Principles

- One model should have one clear responsibility.
- Grain must be explicitly documented.
- Source facts and derived values must be distinguished.
- Business logic should not be introduced unnecessarily in staging.
- Important assumptions should be tested.
- Unknown facts should not be inferred.
- Data semantics should be documented for both humans and AI agents.

## Naming Convention

```text
Staging:
stg_<source>__<entity>

Intermediate:
int_<entity>__<purpose>

Dimension:
dim_<entity>

Fact:
fct_<entity>

Mart:
mart_<domain>__<purpose>
```

Columns use `snake_case`.

### Examples

```text
stg_bbc_news__articles
int_articles__features
dim_categories
fct_articles
mart_news__category_summary
```

## Status

Initial project setup.
