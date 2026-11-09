# Joplo templates

Official project templates for [Joplo](https://github.com/Joplo-app/Joplo). `joplo init` downloads them; you don't need to clone this repository.

```sh
npx joplo@latest init my-demo
cd my-demo
npm install
npx joplo dev --open
```

| Template | What you get |
| --- | --- |
| [`starter/`](starter) | The default project: a sample feature, layout and route, with the ui, diagram, content and alda plugins installed, enabled and pinned to the CLI version. |

Each tag `v<version>` matches a Joplo CLI release exactly. The CLI downloads `github:Joplo-app/joplo-templates/starter#v<its own version>`, so a given CLI always gets the template it was tested with. `main` follows the latest release.

Files contain placeholders that `joplo init` fills in: `__JOPLO_VERSION__` (exact CLI version), `__PACKAGE_NAME__` (npm package name derived from the directory) and `__PROJECT_NAME__` (display name, `--name`). Cloning or copying this repository directly leaves them unfilled — use `joplo init` instead.

## Make your own template

Any GitHub repository or local directory with a `package.json` and `joplo.config.ts` (or `.tsx`) works:

```sh
npx joplo init my-demo --template github:owner/repo/path#ref   # private repos: GITHUB_TOKEN or `gh auth login`
npx joplo init my-demo --template ./my-template                 # offline
```

Start by copying `starter/` from the tag that matches your CLI version.

## Contributing

This repository is generated: every release syncs the `templates/` directory of [Joplo-app/Joplo](https://github.com/Joplo-app/Joplo) here and tags it. Changes made here are overwritten. Report problems with [issues in the main repository](https://github.com/Joplo-app/Joplo/issues); the project accepts issues, not pull requests.

---

# Joplo 模板

[Joplo](https://github.com/Joplo-app/Joplo) 的官方项目模板，由 `joplo init` 下载，不需要克隆本仓库。

- `starter/`：默认项目，包含示例功能、布局和路由；显式安装并启用 ui、diagram、content、alda 四个插件，版本与 CLI 精确一致。
- 每个 `v<版本>` tag 与同版本的 Joplo CLI 一一对应；CLI 默认下载 `github:Joplo-app/joplo-templates/starter#v<CLI版本>`。`main` 跟随最新发布。
- 文件里的 `__JOPLO_VERSION__`、`__PACKAGE_NAME__`、`__PROJECT_NAME__` 由 `joplo init` 替换；直接克隆或复制不会替换，请用 `joplo init`。
- 自定义模板：任何含 `package.json` 和 `joplo.config.ts`（或 `.tsx`）的 GitHub 仓库或本地目录，用 `--template github:owner/repo/path#ref` 或 `--template ./目录`。可以从与 CLI 同版本 tag 的 `starter/` 开始改。
- 本仓库是生成产物：每次发布从主仓库的 `templates/` 同步并打 tag，这里的修改会被覆盖。问题请到[主仓库提 issue](https://github.com/Joplo-app/Joplo/issues)，项目只接受 issue，不接受 PR。
