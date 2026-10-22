Release v1.4.11（versionCode 42）

⚠ AI-generated module / 本模块由 AI 生成，代码未经人工长期审计，请自行评估风险。

## 更新内容 / What's new

- ⚠ 本版起改用新的签名证书（旧密钥在本地数据事故中丢失、无法恢复）：从 v1.4.9 及更早版本
  **必须先卸载旧模块再安装本版**，直接覆盖会被系统拒绝；卸载会连勾选状态一起清掉，
  装好后重新设置一次。
  New signing certificate from this version (the old key was lost and is unrecoverable):
  uninstall v1.4.9 or earlier before installing — an in-place update will be rejected.
  Switch states are cleared with the old app, so set them again after installing.
- 适配荣耀应用市场 16.1.10.301：修升级后回潮的开屏广告与搜索框滚动热词，并接住新增的
  「把应用更新卡片添加至桌面」弹窗。开屏回潮的直接原因是参数表漂移——数据入口方法多了
  一个协程续传参数（3 参 → 5 参）、缓存类整体改名，按参数个数过滤的旧钩子在新版永不命中；
  已按新签名重挂，老版本市场的钩子保留。
  Adapted to Honor App Market 16.1.10.301: fixes the returning splash ads and rolling
  hot-words, and blocks the new "add the update widget to desktop" dialog. The splash
  regression was parameter drift — the data entry gained a coroutine parameter (3 → 5) and
  the cached-splash class was renamed, so the argc-filtered hooks never matched.
- 挂钩落空不再静默：目标方法在本版市场不存在时，日志直接输出 `MISSING 类名#方法名`，
  过滤 `HonorMarketTamer` 就能看出是哪个锚点掉了（此前漂移仍会显示"已装配"）。
  A hook matching nothing now logs `MISSING class#method` instead of reporting "armed"
  while the ad keeps showing.

## 本版取证范围 / What this version is verified for

- 搜索框滚动热词：开/关双向真机坐实。
- 开屏广告、小组件弹窗：钩子装配已确认，**实际命中未取证**——验证期间服务端未下发开屏素材、
  设备也没有可更新应用（弹窗没有触发条件）。遇到这两项仍出现，请带着 LSPosed 日志反馈。
  Rolling hot-words verified both ways on device. Splash and the widget dialog are confirmed
  armed only — their live hits could not be captured (no splash material served, no app was
  updatable). If either still shows, please report with your LSPosed log.
