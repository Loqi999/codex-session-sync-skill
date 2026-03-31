# Overview | 总览

`codex-session-sync` helps users move an in-progress Codex conversation between devices with as little friction as possible.

`codex-session-sync` 的目标，是让用户以尽可能低的成本，把一段正在进行中的 Codex 对话带到另一台设备上继续。

## User Goal | 用户目标

The user should feel like they are doing something close to syncing code:

- choose the work they want
- choose how much fidelity they need
- choose where it should go
- restore it on another machine with as little manual cleanup as possible

用户的感受应该更接近“同步代码”，而不是“搬运聊天记录”：

- 选择自己要继续的工作
- 选择保留多少上下文
- 选择发送到哪里
- 在另一台设备上尽量无感恢复

## Export Flow | 导出流程

1. Choose a conversation or thread.
2. Choose one of three modes:
   - `快速发送`
   - `继续工作（推荐）`
   - `完整迁移`
3. Choose a destination:
   - GitHub
   - Local zip bundle
4. Export and show a clear result:
   - repo destination
   - local bundle path
   - next step for restore

1. 选择一个对话或线程。
2. 选择三种模式之一：
   - `快速发送`
   - `继续工作（推荐）`
   - `完整迁移`
3. 选择导出去向：
   - GitHub
   - 本地 zip 包
4. 导出完成后，明确告诉用户结果：
   - 仓库位置
   - 本地包路径
   - 下一步恢复方式

## Import Flow | 导入流程

1. Choose a source:
   - GitHub
   - Local zip bundle
2. Choose the session to restore.
3. Let the importer decide the safest restore strategy:
   - summary reference
   - continuation context
   - raw local session merge
4. Tell the user exactly what happened.

1. 选择导入来源：
   - GitHub
   - 本地 zip 包
2. 选择要恢复的会话。
3. 让导入器自动判断最安全的恢复策略：
   - 摘要参考
   - 续写上下文
   - raw 本地会话合并
4. 明确告诉用户实际发生了什么。

## Merge Strategy | 合并策略

The skill avoids aggressive merges.

- If a raw session exists and the same session id already exists locally, it treats it as the same session and avoids duplicating it.
- If only lightweight artifacts exist, it restores context rather than forcing a native local-session merge.
- If title, first message, project, and time suggest a likely match, that match is reported as a hint rather than silently overwriting local state.

这个 skill 会尽量避免激进合并：

- 如果存在 raw 会话，且本地已经有相同 session id，则视为同一条会话，避免重复导入
- 如果只有轻量导出内容，则恢复为上下文，而不是强行并入本地原生会话
- 如果标题、第一句消息、项目和时间高度接近，则把它作为“可能匹配”的提示，而不是静默覆盖本地内容

## Privacy Model | 隐私模型

- Lightweight exports still preserve the conversation title and first user message.
- Sensitive-looking strings are redacted from previews.
- Raw session export is available, but it is intentionally not the default.

即便是轻量导出，也会保留对话标题和第一句用户消息，方便后续匹配。

- 预览中疑似敏感字符串会被自动脱敏
- raw 会话导出仍然可用，但它不是默认选项

## Recommended Product Positioning | 推荐产品定位

- `快速发送`: quick backup or lightweight sharing
- `继续工作（推荐）`: best cross-device continuation path
- `完整迁移`: closest to local session restoration

- `快速发送`：适合快速备份或轻量分享
- `继续工作（推荐）`：最适合跨设备续写
- `完整迁移`：最接近本地原生会话恢复

Repository owner note: maintained under the Loqi999 GitHub account.
