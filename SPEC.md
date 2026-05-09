# 麻酱 (MahJiang Score) - 麻将积分记录 App

## 1. Concept & Vision

一款极简的麻将战绩记录工具，专为微信内使用设计。没有花哨的动画，没有多余的功能——就是快速记录、轻松查看。界面风格参考日式麻将的沉稳感，配合暖色调，让人想起茶馆里搓麻的悠闲下午。

## 2. Design Language

**Aesthetic**: 温暖的麻将馆风格，深色背景配合暖金色点缀
**Color Palette**:
- Primary: `#2D5016` (深绿，麻将桌面感)
- Secondary: `#D4A843` (暖金色，胡牌色)
- Accent: `#C73E3A` (红色，点缀)
- Background: `#1A1A1A` (深夜黑)
- Surface: `#2A2A2A` (卡片背景)
- Text: `#F5F5F5` (主文字), `#999` (次要文字)

**Typography**: 
- 主字体: "PingFang SC", "Hiragino Sans GB", "Microsoft YaHei", sans-serif
- 数字: "DIN Alternate", "Roboto Mono", monospace

**Motion**: 极简，无动画，确保微信内流畅

**Icons**: 使用 Emoji (🀄🀁🀓🀅🀆)，不引入外部库

## 3. Layout & Structure

单页应用，三个 Tab 切换：
1. **记录** - 记录当日战绩
2. **历史** - 查看历史战绩列表
3. **玩家** - 管理玩家列表

底部固定 Tab 栏，每个 Tab 清晰图标 + 文字。

## 4. Features & Interactions

### 4.1 玩家管理
- 添加玩家：输入姓名，选择预设标签（运气好/技术好/会算牌/新手，可多选）
- 删除玩家：滑动或长按删除（确认提示）
- 预设标签：运气好 🌟、技术好 🧠、会算牌 📊、新手 🌱
- 数据持久化到 localStorage

### 4.2 战绩记录
- 选择当日参与的玩家（多选）
- 为每位玩家输入本场积分（数字输入，可正可负）
- 自动记录日期和时间
- 保存到 localStorage

### 4.3 历史战绩
- 按日期倒序展示所有记录
- 每条记录显示：日期、时间、参与玩家、各自积分
- 可下拉删除单条记录

## 5. Component Inventory

### TabBar
- 三个 Tab：📝记录 / 📜历史 / 👥玩家
- 当前 Tab 高亮（暖金色下划线）
- 固定底部

### PlayerCard
- 姓名 + 标签徽章
- 删除按钮（红色 ×）
- 点击无操作（仅展示）

### ScoreInputRow
- 玩家姓名 + 积分输入框
- 积分可为负数（支持 - 号输入）

### RecordCard (历史页)
- 日期 + 时间
- 玩家列表及各自积分
- 红色删除按钮

### AddPlayerModal
- 姓名输入框
- 标签多选按钮组
- 确认/取消按钮

## 6. Technical Approach

- **单文件**: `index.html` 包含所有 HTML/CSS/JS
- **存储**: localStorage，key: `mahjong_players`, `mahjong_records`
- **无框架**: 原生 JavaScript，轻量优先
- **部署**: GitHub Pages (用户名 wrd200300，仓库 mahjong-score)

## 7. Data Model

```js
// 玩家
{
  id: string,        // UUID
  name: string,
  tags: string[]     // ['lucky', 'skillful', 'counter', 'newbie']
}

// 战绩记录
{
  id: string,        // UUID
  date: string,      // '2026-05-09'
  time: string,      // '16:30'
  players: [
    { playerId: string, score: number }
  ]
}
```
