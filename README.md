# SmartNews+ パフォーマンスダッシュボード

媒体社向けCV/Impression/CTR パフォーマンス可視化ダッシュボード。

## アクセス方法

GitHub Pages URL にパラメータを付けてアクセス:

```
https://smartnews.github.io/sn-plus-dashboard/?id=139
https://smartnews.github.io/sn-plus-dashboard/?name=Fortune
```

## データ更新

- **毎日午前10時（JST）** に自動更新
- GAS → Redash API → Google Drive HTML更新 → GitHub Actions → GitHub Pages

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
  ↓ HTML更新
Google Drive (file ID: 11sRDbOmqlRKRdH70nEM_xvHclXvImn8T)
  ↓ curl download (GitHub Actions cron)
GitHub Pages (このリポジトリ)
  ↓ URL共有
媒体社 / 社内チーム
```

## 管理者

masahiro.matsui@smartnews.com
