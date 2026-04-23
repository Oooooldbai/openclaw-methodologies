# 锚定机制 · 快速启动卡

> 新Agent先读这个，需要时再深入其他4个文件

---

## 一句话

**用检查点和自动化取代记忆和自觉。**

## 四大支柱

| 支柱 | 一句话 | 文件 |
|------|--------|------|
| 图书馆记忆法 | 存什么、怎么存、怎么找 | LIBRARY-MEMORY-TEMPLATE.md |
| 消防队模式 | 怎么拆、怎么并行 | FIREFIGHTER-MODE-TEMPLATE.md |
| 任务闭环 | 变更怎么固化、怎么验证 | TASK-COMPLETION-WORKFLOW.md |
| 自动检查 | 不依赖"记得" | AUTO-CHECKS.md |

## 5条铁律

1. **检查点是硬证据** — 不创建 = 任务未完成
2. **配置单一来源** — 只存 config.md + config.local.md
3. **模板轻量** — 每个文件<200行，业务规则独立存放
4. **日志有生命周期** — 7天蒸馏，30天清理
5. **HEARTBEAT强制检查** — 不依赖自觉性

## 三层记忆

```
raw/（原始来源，只读）→ wiki/（编译产物，LLM写入）→ SCHEMA.md（规则，共管）
```

## 任务执行流程

```
拆解为<5分钟子任务 → 批量触发 → 检查点驱动 → 异步确认
```

## 变更闭环

```
确认 → 固化（更新配置+记忆）→ 验证（立即测试）→ 归档
```

触发：用户说"确认/就这么定了" / 同话题>3轮 / 涉及配置变更

## 自动检查（HEARTBEAT每次必执行）

1. **检查点完整性** — synced_to全true，有false立即修复
2. **日志生命周期** — 7天蒸馏，30天清理
3. **仓库同步** — 未push的commit立即push
4. **HEARTBEAT有效性** — 过期任务清理

**熔断机制**：连续3次同一问题未修复 → 升级到人工（发消息通知用户）

## 检查点格式

```json
{
  "task_id": "唯一标识",
  "status": "completed|failed|pending",
  "output_files": [],
  "synced_to": { "MEMORY.md": true, "index.md": true },
  "timestamp": "ISO"
}
```

## 启动检查清单

```
SOUL.md → USER.md → memory/index.md → MEMORY.md → config.md → config.local.md
```

---

*锚定机制 · 快速启动卡 v1.0 | 详细版见4个支柱文件*
