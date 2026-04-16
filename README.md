# rei-zenn

**Rei-AIOS の Zenn 投稿用リポジトリ** (auto-deployed via Zenn GitHub 連携)

- Author: 藤本 伸樹 (Nobuki Fujimoto, [@fc0web](https://github.com/fc0web))
- Zenn: https://zenn.dev/fc0web
- License: [CC-BY-4.0](LICENSE)
- Source project: [Rei-AIOS](https://github.com/fc0web/rei-aios) (Private)

## 構成

```
articles/   ← 各 Paper を 1 ファイル / 1 記事として配置
books/      ← 連載本 (将来用)
LICENSE     ← CC-BY-4.0
.gitignore  ← node_modules, .DS_Store
```

## ワークフロー

1. ローカルで `articles/paper-NNN-...md` を作成 (frontmatter 付き)
2. `git push origin main`
3. Zenn が自動で公開 (or 更新)

## ローカルプレビュー

```bash
npx zenn preview
```

http://localhost:8000 で記事プレビュー。

## 新規記事

```bash
npx zenn new:article --slug paper-NNN-shortname
```

## 引用

各記事は CC-BY-4.0 です。利用時は著者名 (藤本 伸樹 / Nobuki Fujimoto) を明記してください。
原典の DOI (Zenodo) と Internet Archive URL が記事内に併記されています。
