Release v1.4.9（versionCode 40）

⚠ AI-generated module / 本模块由 AI 生成，代码未经人工长期审计，请自行评估风险。

## 更新内容 / What's new

- 新增「指纹解锁成功震动」：挂在 SystemUI 的 `KeyguardUpdateMonitor` 成功回调上，
  20 ms 短震，设置页可关；需为本模块勾选「System UI / 系统用户界面」作用域，
  不需要系统框架作用域。
  New: haptic feedback on successful fingerprint unlock, hooked inside SystemUI
  (20 ms one-shot, toggle in settings). Needs the System UI scope only, not the
  Android System (framework) scope.
- 修复推荐作用域从未显示：`xposedscope` 元数据此前用逗号拼接，而 LSPosed 按 `;`
  切分，整串被当成一个不存在的包名，模块详情页一条「推荐应用」都没有。
  Fixed the recommended-scope list never appearing: the `xposedscope` meta-data was
  comma-joined while LSPosed splits on `;`, so the whole string parsed as one
  non-existent package name.
- 市场 16.1.8.305 适配沿用 v1.4.6/1.4.7，本次未改动任何拦截钩子逻辑。
  Market 16.1.8.305 adaptation carried over from v1.4.6/1.4.7; no hook changes here.
- 与 v1.3.3+ 同签名密钥，可直接覆盖安装，无需卸载。
  Same signing key as v1.3.3+ — install over the old one directly.
