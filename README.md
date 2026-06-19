# SmartNews+ パフォーマンスダッシュボード

媒体社向けCV/Impression/CTR パフォーマンス可視化ダッシュボード。

## アクセス方法

### GAS WebApp（メイン — 社内共有用）

smartnews.com ドメインのGoogleアカウントでアクセス:

```
https://script.google.com/a/macros/smartnews.com/s/AKfycbyyHhKHIQB3yBkTh4v-XRZVkxh7z_ABx4UjwW0LWtzm3z2IiD5G7zOOHxQb84ZC8Zm3/exec?id=139
```

パラメータ:
- `?id=139` — media_id で指定
- `?name=Fortune` — 媒体名の部分一致で指定

### GitHub リポジトリ（バックアップ）

このリポジトリの `index.html` は GitHub Actions で毎日 Google Drive から同期されるバックアップです。
GitHub Pages は組織ポリシーにより無効のため、直接配信には使用していません。

## データ更新

- **毎日午前10時（JST）** に自動更新
- パイプライン: GAS → Redash API → Google Drive HTML更新 → GAS WebApp で即時反映

## 媒体社一覧（media_id）

| ID | 媒体社 |
|----|--------|
| 5 | みんかぶプレミアム |
| 139 | マネーポストWEBプレミアム |
| 93 | THE GOLD ONLINE |
| 147 | 週刊文春 電子版 |
| 76 | 現代ビジネスプレミアム |
| 112 | PRESIDENT |
| 84 | 日刊ゲンダイDIGITAL |
| 146 | nobico（のびこ） |
| 39 | Fortune |
| 144 | 集英社オンライン |
| 25 | The New York Times |
| 123 | The Washington Post |

## アーキテクチャ

```
Redash (Trino/Hive)
  ↓ API (毎日10時JST)
GAS (sn-plus-dashboard-updater.js)
  ↓ HTML生成・保存
Google Drive (file ID: 11sRDbOmqlRKRdH70nEM_xvHclXvImn8T)
  ↓ doGet() で読み取り
GAS WebApp (smartnews.com 認証付き)
  ↓ URL共有
媒体社 / 社内チーム

  ※バックアップ:
  Google Drive → GitHub Actions (cron) → このリポジトリ
```

## 管理者

masahiro.matsui@smartnews.com
