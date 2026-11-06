# 其他 Agent 平台

不得假设 Hermes、Gemini CLI、其他 IDE Agent 或自定义 Agent 使用 Claude Code/Codex 的目录结构。

安装前必须核对目标平台的官方文档，确认：
1. 是否支持 Agent Skills 格式和 `SKILL.md`。
2. 是否支持项目/工作区级 Skill 发现。
3. 项目级目录的准确路径和发现深度。
4. 是否会向父目录或用户目录继承 Skill。

只有确认项目级发现目录后才能安装。若平台只支持用户级 Skill，YoYo 不应安装到该平台；可在当前工作区手动提供包并要求执行方读取 `SKILL.md`，但这不是自动发现安装。
