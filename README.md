# 东海往事 · 数字世界引擎

为《东海往事》角色卡开发的独立弹窗小手机（应用：微信 + 备忘录）。移植自蒋默单人卡同款引擎，详见 [设计文档.md](设计文档.md)。

## 目录

```
loader/dhwj-loader.js   装载器（粘贴到卡片，经酒馆助手运行）
src/                       引擎源码（按模块分文件）
build/build.js             构建：node build/build.js → dist/engine.js
dist/engine.js             发布产物（jsDelivr 分发的就是它）
test/smoke.js              离线冒烟测试：node test/smoke.js
设计文档.md                 唯一设计依据
```

## 发布流程

1. 改 `src/` 里的代码
2. `node test/smoke.js`（离线回归，全绿再构建）
3. `node build/build.js`
4. 提交推送 GitHub（dist 一起推）
5. 玩家下次进卡自动拿到新版（装载器取 main 最新提交号）

## 使用前必改（世界书约定）

卡的世界书已带引擎约定条目，零配置即可用：

- `东海往事::通讯录` —— 联系人/群/朋友圈数据（JSON）
- `东海往事::表情包` —— 表情名→catbox 文件名（JSON）
- `角色档案：周霓` / `角色档案：郑书宁` / `角色档案：NPCs` —— 引擎的人设源（单人条目全文即档案；NPCs 合集按 `### 数字. 名字` 小节拆）

可选：`东海往事::NSFW`（亲密文风指引，有则注入所有叙事类生成）。

装载器已指向 `haodayizhiyu404/donghai_wangshi`；改名仓库需同步改 `loader/dhwj-loader.js` 顶部常量。
