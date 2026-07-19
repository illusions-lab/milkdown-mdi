# milkdown-mdi

**[Milkdown](https://milkdown.dev) editor plugins for [illusion Markdown (MDI)](https://github.com/illusions-lab/MDI)** — MDI syntax support and vertical writing (縦書き) display for the ProseMirror-based Milkdown editor.

**illusion Markdown (MDI)** のための [Milkdown](https://milkdown.dev) エディタプラグイン群です。MDI 構文サポートと縦書き表示を提供します。

This repository was split out of the `illusions` project's original `milkdown-plugin-japanese-novel` plugin.  
本リポジトリは `illusions` プロジェクトの `milkdown-plugin-japanese-novel` から独立したものです。

---

## Packages / パッケージ構成

| Package | Description |
|---------|-------------|
| [`milkdown-mdi-support`](./packages/milkdown-mdi-support) | Milkdown plugin adding MDI 2.0 syntax (ruby, tate-chu-yoko, boten, kerning, warichu, block alignment, page breaks, etc.) as input rules, schema nodes/marks, and a remark integration. |
| [`milkdown-plugin-tategaki`](./packages/milkdown-plugin-tategaki) | Milkdown plugin for vertical writing mode (縦書き) display — independent of MDI syntax, usable for any vertical Japanese editing surface. |

### Relationship to mdi-js / mdi-js との関係

`milkdown-mdi-support` depends on [`micromark-extension-mdi`](https://github.com/illusions-lab/mdi-js) (once published) for the same validation/disambiguation rules used by the export path (`@illusions-lab/mdi-remark`), so the editor and exported documents never disagree on how a given piece of MDI syntax should parse.

`milkdown-mdi-support` は（公開後）[`micromark-extension-mdi`](https://github.com/illusions-lab/mdi-js) の検証・曖昧性解決ロジックに依存します。これにより、エディタ側とエクスポート側（`@illusions-lab/mdi-remark`）の解釈が食い違うことを防ぎます。

---

## Development / 開発

This is a [pnpm](https://pnpm.io) + [Turborepo](https://turbo.build) monorepo.

```bash
pnpm install
pnpm build
pnpm test
```

### Versioning / バージョニング

Every package's version is `<MDI spec version>.<package release number>` — the major.minor pair always equals the MDI spec version this repo targets (currently `2.0`), and the patch number is each package's own independent release count, **starting at `.1`** (never `.0`) for the first release under a given spec version. Patch numbers are independent per package; only major.minor is shared.

すべてのパッケージのバージョンは `<MDI 仕様バージョン>.<パッケージ自身のリリース回数>` です。major.minor はこのリポジトリが対応する MDI 仕様バージョン（現在 `2.0`）に常に一致し、patch は各パッケージが独自にカウントするリリース回数で、そのバージョンで最初のリリースは `.0` ではなく **`.1` から始まります**。patch は各パッケージ独立で、major.minor のみ共有します。

- **Ordinary releases** (same spec version): use Changesets as normal — always choose a **patch** bump, never minor/major.  
  **通常のリリース**（同じ仕様バージョン内）: 通常どおり Changesets を使い、常に **patch** bump のみを選びます（minor/major は使いません）。

  ```bash
  pnpm changeset       # record what changed; always pick "patch"
  pnpm version         # apply pending changesets
  pnpm release         # build + publish
  ```

- **Spec version bump** (e.g. MDI 2.0 → 2.1): Changesets has no concept of "MDI spec version," so this is a separate, explicit step — it rewrites every package's version to `<new spec version>.1` regardless of each package's prior patch count.  
  **仕様バージョンの引き上げ**（例: MDI 2.0 → 2.1）: Changesets は「MDI 仕様バージョン」という概念を知らないため、これは別の明示的な手順です。各パッケージの直前の patch 数に関係なく、全パッケージのバージョンを `<新しい仕様バージョン>.1` へ書き換えます。

  ```bash
  pnpm bump-spec-version 2.1
  ```

---

## Related projects / 関連プロジェクト

- [illusions-lab/MDI](https://github.com/illusions-lab/MDI) — the MDI specification.
- [illusions-lab/mdi-js](https://github.com/illusions-lab/mdi-js) — Node.js parser and HTML/PDF/EPUB/DOCX converters for MDI.

---

## License

MIT
