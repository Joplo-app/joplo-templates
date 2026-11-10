# Joplo templates

Starting points for [Joplo](https://github.com/Joplo-app/Joplo) projects. `joplo init` downloads them from this repository's default branch; you don't need to clone it.

```sh
npx joplo@latest init my-demo                    # compare options for a feature
npx joplo@latest init my-show --template work    # a standalone show with two chapters
cd my-demo
npm install
npx joplo dev --open
```

| Template | What you get |
| --- | --- |
| [`starter/`](starter) | The default. One feature with a sample option, cases, a layout and a route — for designing behavior before you build it. Uses the ui, diagram, content and alda plugins. |
| [`work/`](work) | One standalone show: two chapters that continue from each other, an input you can try while paused, and a line of text to edit. Uses the ui plugin. |

`--template <name>` takes any folder name in this repository.

Files contain placeholders that `joplo init` fills in: `__JOPLO_VERSION__` (the version of the CLI you ran), `__PACKAGE_NAME__` (npm package name derived from the directory) and `__PROJECT_NAME__` (display name, `--name`). Cloning or copying this repository directly leaves them unfilled — use `joplo init`.

The plugin skills under each template's `.claude/skills/` are a snapshot so an agent can read them before dependencies are installed. After `npm install`, `npx joplo skill install` brings them in line with the versions you actually installed.

## Make your own template

Any GitHub repository or local directory with a `package.json` and `joplo.config.ts` (or `.tsx`) works:

```sh
npx joplo init my-demo --template github:owner/repo/path#ref   # private repos: GITHUB_TOKEN or `gh auth login`
npx joplo init my-demo --template ./my-template                 # a local directory; keep the ./
```

## Maintenance

This repository is maintained by hand and is independent of Joplo releases: there are no version tags, and the default branch should always work with the latest published CLI. Report problems in the [main repository's issues](https://github.com/Joplo-app/Joplo/issues); the project accepts issues, not pull requests.

---

# Joplo 模板

[Joplo](https://github.com/Joplo-app/Joplo) 项目的起点。`joplo init` 从本仓库的默认分支下载，不需要克隆。

```sh
npx joplo@latest init my-demo                    # 比较一个功能的几种方案
npx joplo@latest init my-show --template work    # 一件两个章节的独立作品
cd my-demo
npm install
npx joplo dev --open
```

| 模板 | 内容 |
| --- | --- |
| [`starter/`](starter) | 默认模板。一个功能、一个示例方案、情况、布局和页面，用来在动手之前把行为设计清楚。使用 ui、diagram、content、alda 四个插件。 |
| [`work/`](work) | 一件独立作品：两个接续的章节，一个暂停后可以上手试的输入框，一行可以直接改的文字。使用 ui 插件。 |

`--template <名字>` 可以是本仓库里任何一个文件夹的名字。

文件里的占位符由 `joplo init` 填入：`__JOPLO_VERSION__`（你运行的 CLI 的版本）、`__PACKAGE_NAME__`（由目录名得到的 npm 包名）、`__PROJECT_NAME__`（显示名，`--name`）。直接克隆或复制本仓库不会替换它们，请用 `joplo init`。

每个模板 `.claude/skills/` 下的插件技能是一份快照，让 Agent 在安装依赖之前就能读到。`npm install` 之后运行 `npx joplo skill install`，它们会与实际安装的版本对齐。

## 自己做模板

任何带 `package.json` 和 `joplo.config.ts`（或 `.tsx`）的 GitHub 仓库或本地目录都可以：

```sh
npx joplo init my-demo --template github:owner/repo/path#ref   # 私有仓库：GITHUB_TOKEN 或 `gh auth login`
npx joplo init my-demo --template ./my-template                 # 本地目录，保留 ./
```

## 维护

本仓库手动维护，与 Joplo 的发版无关：没有版本 tag，默认分支要始终能被最新发布的 CLI 使用。问题请提到[主仓库的 issue](https://github.com/Joplo-app/Joplo/issues)；项目只接受 issue，不接受 PR。
