# Learning Assistant Profile Builder

## Skill 简介

`learning-assistant-profile-builder` 是一个用于 Codex 的个性化学习助手 Skill。它会先帮助用户建立长期学习档案，再在后续讲解概念、解析题目、寻找相似题、维护题型库和制定复习计划时，优先结合用户登记过的课本、PPT、讲义、参考习题、往年试卷、答案和老师重点。

这个 Skill 的重点不是一次性回答问题，而是帮助用户逐步建立可长期更新的学习体系。

## 适用场景

- 第一次建立个性化学习档案。
- 登记课程、当前进度、教材、讲义、PPT、习题册、往年卷和答案。
- 按指定课本或讲义解释概念。
- 按课程资料解析题目。
- 从参考习题或往年试卷中寻找相似题。
- 建立和更新题型库、错题库或复习规则。
- 根据考试范围和老师重点制定复习计划。
- 调整长期回答风格偏好。

## 安装方式

将本仓库复制到用户级 Codex skills 目录：

```powershell
Copy-Item -Recurse -Force . "C:\Users\Lenovo\.agents\skills\learning-assistant-profile-builder"
```

安装后，Skill 文件应位于：

```text
C:\Users\Lenovo\.agents\skills\learning-assistant-profile-builder\SKILL.md
```

## 调用方式

可以通过 Codex 的 `/skills` 查看是否识别到：

```text
/skills
```

也可以在对话中直接调用：

```text
$learning-assistant-profile-builder
```

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
learning-assistant-profile-builder/
├─ SKILL.md
├─ README.md
├─ LICENSE
├─ assets/
│  └─ learner_profile_template.md
└─ references/
   ├─ answer_style_options.md
   ├─ material_priority_rules.md
   ├─ task_response_formats.md
   └─ question_bank_rules.md
```

- `SKILL.md`：Skill 的核心说明、触发场景、工作流和质量标准。
- `assets/learner_profile_template.md`：不支持长期记忆时可使用的学习档案模板。
- `references/answer_style_options.md`：回答风格选项和临时风格调整规则。
- `references/material_priority_rules.md`：学习资料优先级、溯源和长期档案规则。
- `references/task_response_formats.md`：概念讲解、题目解析、相似题检索、复习规划等任务格式。
- `references/question_bank_rules.md`：题型库和错题库维护规则。
