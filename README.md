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

### Compatibility and bundled guide refresh

The current templates are verified with the published Joplo **0.8.0** CLI. Keep `__JOPLO_VERSION__` in template dependencies: init pins the CLI, kit and selected plugins to the same installed version. This is a compatibility baseline, not a version or tag for this repository.

Only bundle guides for plugins enabled by each template. Neither template currently needs sound-effect, video or Lottie tracks, so neither adds `@joplo-app/plugin-av`. Projects that need those tracks can install that package explicitly; its manifest and guide topic are still named `media` (`joplo skill media`).

To refresh the guide snapshots:

1. Use the published CLI version being verified to init each template into a fresh temporary directory, selecting the local template directory explicitly.
2. Run `npm install`, then `npx joplo skill install` in that generated project. Do not hand-edit version strings or managed hash markers, and do not use `--force` to hide a modified guide.
3. Copy back only the plugin-guide files listed by the generated `.claude/skills/.joplo-plugins.json`, together with that index. Engine skills and the managed AGENTS block are supplied by init; do not copy generated projects, dependencies, caches or build outputs into this repository.
4. Init a second fresh project from each updated template. Verify every bundled guide is byte-identical to the installed guide, a second skill install makes no changes, and `joplo check` / `joplo build` pass. The starter's happy-path info is intentional; these checks do not require voice generation or paid services.

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

### 兼容性与随附指南刷新

当前模板已使用正式发布的 Joplo **0.8.0** CLI 验证。依赖继续保留 `__JOPLO_VERSION__`：init 会把 CLI、kit 与所选插件固定为同一版本。这是兼容性验证基线，不是本仓库的版本号或 tag。

只随附模板实际启用的插件指南。两个模板都不需要独立音效、视频或 Lottie 轨道，因此不新增 `@joplo-app/plugin-av` 依赖；需要这些轨道的项目自行显式安装。该包的 manifest 和指南主题仍叫 `media`，通过 `joplo skill media` 阅读。

刷新指南快照时：

1. 使用待验证的正式 CLI，把每个本地模板初始化到全新临时目录；显式选择本地模板路径。
2. 在生成项目中运行 `npm install`、`npx joplo skill install`。不要手改版本号或托管哈希标记，也不要用 `--force` 掩盖被修改的指南。
3. 只回拷生成的 `.claude/skills/.joplo-plugins.json` 所列插件指南及该索引。引擎技能和 AGENTS 托管段由 init 提供；不要把生成项目、依赖、缓存或构建产物提交进本仓库。
4. 从更新后的每个模板再初始化全新项目，检查随附指南与安装版本逐字节一致，再次安装技能没有改动，且 `joplo check` / `joplo build` 通过。starter 的顺利路径 info 是起步示例的预期提示；验证不需要生成旁白或调用付费服务。

## 自己做模板

任何带 `package.json` 和 `joplo.config.ts`（或 `.tsx`）的 GitHub 仓库或本地目录都可以：

```sh
npx joplo init my-demo --template github:owner/repo/path#ref   # 私有仓库：GITHUB_TOKEN 或 `gh auth login`
npx joplo init my-demo --template ./my-template                 # 本地目录，保留 ./
```

## 维护

本仓库手动维护，与 Joplo 的发版无关：没有版本 tag，默认分支要始终能被最新发布的 CLI 使用。问题请提到[主仓库的 issue](https://github.com/Joplo-app/Joplo/issues)；项目只接受 issue，不接受 PR。
