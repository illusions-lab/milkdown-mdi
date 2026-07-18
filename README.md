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

`milkdown-mdi-support` depends on [`micromark-extension-mdi`](https://github.com/illusions-lab/mdi-js) (once published) for the same validation/disambiguation rules used by the export path (`remark-mdi`), so the editor and exported documents never disagree on how a given piece of MDI syntax should parse.

`milkdown-mdi-support` は（公開後）[`micromark-extension-mdi`](https://github.com/illusions-lab/mdi-js) の検証・曖昧性解決ロジックに依存します。これにより、エディタ側とエクスポート側（`remark-mdi`）の解釈が食い違うことを防ぎます。

---

## Development / 開発

This is a [pnpm](https://pnpm.io) + [Turborepo](https://turbo.build) monorepo.

```bash
pnpm install
pnpm build
pnpm test
```

Versioning and publishing are managed with [Changesets](https://github.com/changesets/changesets):

```bash
pnpm changeset
```

---

## Related projects / 関連プロジェクト

- [illusions-lab/MDI](https://github.com/illusions-lab/MDI) — the MDI specification.
- [illusions-lab/mdi-js](https://github.com/illusions-lab/mdi-js) — Node.js parser and HTML/PDF/EPUB/DOCX converters for MDI.

---

## License

MIT
