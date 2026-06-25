# AgentForge · ABAC 权限配置示例

基于属性的访问控制（Attribute-Based Access Control）策略管理静态示例页面。

## 功能特性

- **多资源类型支持**：工作流、智能体、评测集、Skill
- **四维属性配置**：主体属性、资源属性、操作权限、环境属性
- **策略实时预览**：JSON 格式策略定义实时更新
- **权限评估模拟**：基于配置的策略进行权限评估

## 技术栈

- HTML5 + CSS3 + JavaScript
- Remix Icon 图标库
- 响应式设计

## 在线预览

🔗 [GitHub Pages](https://liulzz.github.io/agentforge-abac-demo/)

## 本地运行

直接在浏览器中打开 `index.html` 即可。

## ABAC 概念说明

### 四维属性模型

| 维度 | 说明 | 示例 |
|------|------|------|
| **主体（Subject）** | 发起访问的用户或系统 | 角色、部门、安全等级、组织单元 |
| **资源（Resource）** | 被访问的对象 | 资源类型、状态、安全等级、所属租户 |
| **操作（Operation）** | 执行的动作 | 查看、读取、创建、编辑、删除、执行 |
| **环境（Environment）** | 访问时的上下文 | 时间、来源、设备、认证方式 |

### 策略示例

```json
{
  "policy": {
    "name": "开发者工作流读写权限",
    "effect": "ALLOW",
    "resource": { "type": "workflow" },
    "subject": { "role": "developer" },
    "operations": ["read", "create", "edit"],
    "conditions": {
      "time": "business-hours",
      "source": "internal-network"
    }
  }
}
```

## 与 RBAC 的对比

| 维度 | RBAC | ABAC |
|------|------|------|
| **控制粒度** | 角色级别 | 属性级别 |
| **灵活性** | 较低 | 较高 |
| **复杂度** | 简单 | 复杂 |
| **适用场景** | 权限相对固定 | 权限动态变化 |
| **扩展性** | 有限 | 高度可扩展 |

## AgentForge 应用场景

| 资源类型 | ABAC 应用 |
|----------|----------|
| 工作流 | 基于部门+安全等级控制流程编辑权限 |
| 智能体 | 基于租户+角色控制 Agent 配置权限 |
| 评测集 | 基于项目组+环境控制数据访问权限 |
| Skill | 基于开发者等级控制发布权限 |
