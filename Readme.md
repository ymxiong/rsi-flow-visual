# 本地引用打包产物（dist）

## 1. 构建本项目

在本项目根目录执行：

```bash
yarn install
yarn build
```

修改源码后动态调试可运行 `yarn build:lib --watch`，保持该命令运行即可持续更新 `dist`。

## 2. 在使用方项目添加本地依赖

在使用方项目的 `package.json` 中，将依赖路径设为**本项目根目录**（不是 `dist` 目录）：

```json
{
  "dependencies": {
    "@horsecoder/visual-core": "file:../rsi-flow-visual"
  }
}
```

相对路径从使用方项目目录解析，也可改为本机绝对路径；保存后在使用方项目运行 `yarn install`，代码通过 `import VisualDiagram from '@horsecoder/visual-core'` 引用。动态调试希望改动自动同步时，使用 `yarn link`（先在本项目运行 `yarn link`，再在使用方运行 `yarn link @horsecoder/visual-core`）；使用方还需监听链接包的变化，并确保共用同一份 React。
