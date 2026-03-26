# Cron Manager Master - OpenClaw 定时任务管理技能

[![OpenClaw Skill](https://img.shields.io/badge/OpenClaw-Skill-blue)](https://clawhub.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 📋 项目简介

Cron Manager Master 是一个专为 OpenClaw 设计的定时任务创建和管理技能。它提供了标准化、自动化的定时任务创建流程，并包含智能上下文提取功能，极大地简化了定时任务的配置和管理。

## ✨ 核心特性

### 🎯 智能上下文提取
- **零配置创建**：自动从当前会话中提取通道（channel）和用户ID（to）
- **无缝集成**：无需手动配置参数，直接使用当前会话上下文
- **跨平台支持**：支持飞书、企业微信等多种通道

### 📝 标准化工作流
- **参数规范检查**：创建前自动验证参数完整性
- **创建后验证**：任务创建后立即执行系统验证
- **错误处理**：完善的错误处理和监控机制

### 🔧 自动化规范检查
- 强制使用 `--session isolated` 参数
- 强制使用 `--announce` 模式
- 自动验证时间格式和用户ID格式
- 任务名称清晰明确检查

## 🚀 快速开始

### 安装方法
```bash
# 使用 skills 工具安装
npx skills add <your-username>/cron-manager-master -g -y
```

### 使用方法
1. **触发技能**：在 OpenClaw 会话中提及"创建定时任务"、"设置cron任务"等关键词
2. **自动提取**：技能会自动提取当前会话的通道和用户ID
3. **创建任务**：按照提示输入任务名称、时间和消息内容
4. **系统验证**：任务创建后自动执行规范检查

## 📁 项目结构

```
cron-manager-master/
├── README.md                 # 项目说明文档
├── SKILL.md                  # 技能主文件
├── references/
│   └── cron-examples.md      # Cron表达式示例参考
└── scripts/
    ├── create-cron.sh        # 创建定时任务脚本
    └── validate-cron.sh      # 验证定时任务脚本
```

## 📖 详细文档

请查看 [SKILL.md](SKILL.md) 文件获取完整的使用说明、参数规范和示例。

### 核心功能
- **自动上下文提取**：从会话中智能提取 channel 和 user_id
- **参数规范化**：确保所有定时任务符合 OpenClaw 最佳实践
- **创建后验证**：立即检查任务配置的正确性
- **错误处理**：完善的监控和告警机制

### 使用示例

#### 创建一次性任务
```bash
openclaw cron add \
  --name "会议提醒" \
  --at "2026-03-26T14:30:00+08:00" \
  --session isolated \
  --message "下午2:30有团队会议" \
  --announce \
  --channel feishu \
  --to "ou_xxxxx"
```

#### 创建周期性任务
```bash
openclaw cron add \
  --name "每日AI新闻日报" \
  --cron "0 10 * * *" \
  --session isolated \
  --message "正在生成今日AI新闻日报..." \
  --announce \
  --channel feishu \
  --to "ou_xxxxx"
```

## 🔧 开发指南

### 技能结构
- **SKILL.md**：技能定义文件，包含触发条件、工作流和规范
- **scripts/**：辅助脚本目录，包含创建和验证脚本
- **references/**：参考文档目录，包含Cron表达式示例

### 扩展功能
1. 添加更多通道支持
2. 增加任务模板功能
3. 集成任务监控和告警
4. 添加批量任务管理功能

## 📄 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情。

## 🤝 贡献

欢迎提交 Issue 和 Pull Request 来改进这个技能！

## 📞 支持

如有问题或建议，请：
1. 提交 GitHub Issue
2. 联系作者
3. 查看 OpenClaw 官方文档

---

**让定时任务管理变得简单而高效！** 🚀
