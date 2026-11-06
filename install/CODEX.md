# Codex｜当前工作区安装

Codex 项目级 Skill 目录为仓库内 `.agents/skills/`。将整个 `yoyo` Skill 文件夹放到：

```text
<项目根目录>/.agents/skills/yoyo/SKILL.md
```

不要安装到用户目录 `~/.agents/skills/`、系统目录或管理员目录。Codex 会从当前工作目录向仓库根目录扫描 `.agents/skills`，因此应确认实际仓库根目录，避免意外扩大到其他项目。

如果项目根目录已有同名 Skill，先比较和备份，不覆盖用户改动。项目档案放在 `<项目根目录>/.yoyo/`。

参考：OpenAI Codex Skills 文档 https://learn.chatgpt.com/docs/build-skills
