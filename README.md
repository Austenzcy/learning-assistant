# Learning Assistant

## 这个仓库是什么

`learning-assistant` 是一个同时面向 Codex 和 Claude Code 分发的学习助手仓库。当前包含 `learning-assistant-profile-builder`，用于建立个性化学习档案，并在后续学习问答中优先结合用户指定的课本、PPT、讲义、参考习题、往年试卷、答案、老师重点和考试范围。

这个 Skill 的重点不是给一次性通用答案，而是帮助用户长期维护课程资料、学习进度、回答风格、题型库、错题库和复习规则。

## 适用场景

- 第一次建立个性化学习档案。
- 登记课程、当前进度、教材、讲义、PPT、习题册、往年卷和答案。
- 按指定课本或讲义解释概念。
- 按课程资料解析题目。
- 从参考习题或往年试卷中寻找相似题。
- 建立和更新题型库、错题库或复习规则。
- 根据考试范围和老师重点制定复习计划。
- 调整长期回答风格偏好。

## Codex 安装方式

Codex 用户可以通过 `$skill-installer` 从 GitHub 子目录安装：

```text
$skill-installer install https://github.com/Austenzcy/learning-assistant/tree/main/codex/learning-assistant-profile-builder
```

安装后重启 Codex，让新 Skill 生效。

## Claude Code 安装方式

Claude Code 用户可以先添加 marketplace，再安装插件：

```text
/plugin marketplace add Austenzcy/learning-assistant
```

```text
/plugin install learning-assistant-profile-builder@learning-assistant
```

## 手动安装 Fallback

Codex 手动安装时，将 `codex/learning-assistant-profile-builder` 复制到用户级 Codex skills 目录：

```powershell
Copy-Item -Recurse -Force "codex\learning-assistant-profile-builder" "C:\Users\Lenovo\.agents\skills\learning-assistant-profile-builder"
```

安装后，Skill 文件应位于：

```text
C:\Users\Lenovo\.agents\skills\learning-assistant-profile-builder\SKILL.md
```

Claude Code 手动安装时，使用 `plugins/learning-assistant-profile-builder` 作为完整插件目录。该目录内包含独立完整的 Skill 文件，不依赖仓库外部路径。

## 调用方式

Codex 中可以通过 `/skills` 查看是否识别到：

```text
/skills
```

也可以在对话中直接调用：

```text
$learning-assistant-profile-builder
```

Claude Code 中安装插件后，可以使用插件提供的同名 skill 工作流。

## 示例 Prompt

```text
$learning-assistant-profile-builder 帮我第一次建立线性代数的学习档案。
```

```text
我上传了课本和这道题，请优先按课本里的定义和方法讲解。
```

```text
参考习题和往年卷里有没有和这道题类似的题？请按考点和解题方法找。
```

```text
以后回答我请改成通俗入门型，先用直观例子讲，再给公式。
```

```text
把这道题加入我的题型库，记录题型名称、考点、解题思路、详细解析和易错点。
```

## 文件结构说明

```text
learning-assistant/
├─ README.md
├─ LICENSE
├─ .claude-plugin/
│  └─ marketplace.json
├─ codex/
│  └─ learning-assistant-profile-builder/
│     ├─ SKILL.md
│     ├─ assets/
│     │  └─ learner_profile_template.md
│     └─ references/
│        ├─ answer_style_options.md
│        ├─ material_priority_rules.md
│        ├─ question_bank_rules.md
│        └─ task_response_formats.md
├─ plugins/
│  └─ learning-assistant-profile-builder/
│     ├─ .claude-plugin/
│     │  └─ plugin.json
│     └─ skills/
│        └─ learning-assistant-profile-builder/
│           ├─ SKILL.md
│           ├─ assets/
│           │  └─ learner_profile_template.md
│           └─ references/
│              ├─ answer_style_options.md
│              ├─ material_priority_rules.md
│              ├─ question_bank_rules.md
│              └─ task_response_formats.md
└─ shared/
├─ SKILL.md
├─ learner_profile_template.md
├─ answer_style_options.md
├─ material_priority_rules.md
├─ question_bank_rules.md
└─ task_response_formats.md
```

- `codex/learning-assistant-profile-builder/`：Codex skill-installer 使用的 Skill 分发目录。
- `plugins/learning-assistant-profile-builder/`：Claude Code 使用的插件目录。
- `plugins/learning-assistant-profile-builder/skills/learning-assistant-profile-builder/`：Claude Code 插件内置的完整 Skill 副本。
- `.claude-plugin/marketplace.json`：Claude Code marketplace 入口。
- `plugins/learning-assistant-profile-builder/.claude-plugin/plugin.json`：Claude Code 插件 manifest。
- `shared/`：维护用源内容。

## 维护说明

`shared/` 是源内容。更新 Skill 时，先修改 `shared/` 中的文件，再同步到：

- `codex/learning-assistant-profile-builder/`
- `plugins/learning-assistant-profile-builder/skills/learning-assistant-profile-builder/`

Claude Code 插件安装后会被复制到缓存目录，因此 `plugins/learning-assistant-profile-builder/skills/learning-assistant-profile-builder/` 必须包含完整的 `SKILL.md`、`assets/` 和 `references/`，不能依赖 `../shared`。
