# @kelegele/emoji-picker

[![License](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](LICENSE)
[![OHPM](https://img.shields.io/badge/OHPM-v1.0.1-green.svg)](https://ohpm.openharmony.cn/#/cn/detail/@kelegele%2Femoji-picker)

一个专为 HarmonyOS 设计的 Emoji 选择器组件，支持中文标签、多主题配色和深浅色模式自动适配。

## ✨ 特性

- 🎨 **多主题支持** - 内置 3 种主题，支持完全自定义主题配色
- 🌓 **深浅色适配** - 自动适配系统深浅色模式
- 🇨🇳 **中文标签** - 内置 3000+ Emoji，全部带有中文描述
- 📱 **分组展示** - 按类别分组（笑脸情感、人物身体、动物自然等），支持快速定位
- ✨ **触感反馈** - 选择时提供细腻的震动反馈
- 🔧 **高度可配置** - Emoji 大小、每行数量等均可自定义

## 📦 安装

```bash
ohpm install @kelegele/emoji-picker
```

## 🚀 快速开始

### 基础用法

```typescript
import { Picker } from '@kelegele/emoji-picker'

@Component
struct MyComponent {
  @State emojiText: string = ''

  build() {
    Column() {
      // 显示选中的 Emoji
      Text(this.emojiText)
        .fontSize(48)
      
      // Emoji 选择器
      Picker({ emojiText: $emojiText })
        .height(400)
    }
  }
}
```

### 使用内置主题

```typescript
import { Picker, THEME_DEFAULT, THEME_GRAY, THEME_GREEN } from '@kelegele/emoji-picker'

// 灰色主题
Picker({ 
  emojiText: $emojiText,
  theme: THEME_GRAY
})
```

| 主题 | 常量 | 说明 |
|------|------|------|
| 鸿蒙默认 | `THEME_DEFAULT` | 蓝色系，使用系统强调色 |
| 绿色 | `THEME_GREEN` | 品牌绿色，适合社交类应用 |
| 灰色 | `THEME_GRAY` | 无彩色，适合通用场景 |

### 自定义配置

```typescript
Picker({ 
  emojiText: $emojiText,
  emojiFontSize: 28,  // Emoji 大小，默认 32
  lanes: 8,           // 每行数量，默认 7
  theme: THEME_GRAY   // 主题配置
})
```

### 自定义主题

```typescript
import { Picker, EmojiPickerTheme } from '@kelegele/emoji-picker'

const myTheme: EmojiPickerTheme = {
  name: 'custom',
  selectedTextColor: '#FF6B6B',      // 选中 Tab 文字颜色
  selectedBgColor: '#FFE5E5',        // 选中 Tab 背景颜色
  unselectedTextColor: '#666666',    // 未选中 Tab 文字颜色
  unselectedBgColor: '#F5F5F5',      // 未选中 Tab 背景颜色
  headerColor: '#FF6B6B',            // 分组标题颜色
  headerBgColor: '#FFFFFF'           // 分组标题背景颜色
}

Picker({ 
  emojiText: $emojiText,
  theme: myTheme
})
```

## 📖 API 参考

### Props

| 参数 | 类型 | 必填 | 默认值 | 说明 |
|------|------|:----:|--------|------|
| `emojiText` | `ResourceStr` | ✅ | - | 双向绑定的选中 Emoji |
| `emojiFontSize` | `number` | ❌ | `32` | Emoji 字体大小 |
| `lanes` | `number` | ❌ | `7` | 每行显示数量 |
| `theme` | `EmojiPickerTheme` | ❌ | `THEME_DEFAULT` | 主题配置 |
| `emojiData` | `EmojiGroup[]` | ❌ | 内置数据 | 自定义 Emoji 数据源 |

### 导出内容

```typescript
// 组件
export { Picker } 

// 数据
export { EMOJI_251223 }  // 内置 Emoji 数据（3000+）

// 类型
export { EmojiGroup, EmojiItem, EmojiPickerTheme }

// 内置主题
export { THEME_DEFAULT, THEME_GREEN, THEME_GRAY, BUILT_IN_THEMES }
```

### 类型定义

```typescript
/** Emoji 项 */
interface EmojiItem {
  sub_group: string    // 子分组名称
  emoji_font: string   // Emoji 字符
  emoji_name: string   // 中文名称
  unicode: string      // Unicode 编码
}

/** Emoji 分组 */
interface EmojiGroup {
  group_id: string     // 分组 ID
  group: string        // 分组名称
  items: EmojiItem[]   // Emoji 列表
}

/** 主题配置 */
interface EmojiPickerTheme {
  name: string                     // 主题名称
  selectedTextColor: ResourceStr   // 选中 Tab 文字颜色
  selectedBgColor: ResourceStr     // 选中 Tab 背景颜色
  unselectedTextColor: ResourceStr // 未选中 Tab 文字颜色
  unselectedBgColor: ResourceStr   // 未选中 Tab 背景颜色
  headerColor: ResourceStr         // 分组标题颜色
  headerBgColor: ResourceStr       // 分组标题背景颜色
}
```

## 📱 兼容性

| 项目 | 要求 |
|------|------|
| 最低 SDK | HarmonyOS SDK 5.0.0 (API 12) |
| 目标 SDK | HarmonyOS SDK 6.0.0 (API 20) |
| 运行系统 | HarmonyOS 5.0.0+ |

> ⚠️ **注意**: 部分 Unicode 15.1 新增的 Emoji 可能需要新版系统才能正常显示。

## 📄 许可证

[Apache-2.0](LICENSE)

## 🔗 链接

- [OHPM 中心仓](https://ohpm.openharmony.cn/#/cn/detail/@kelegele%2Femoji-picker)
- [问题反馈](https://github.com/kelegele/OHPM-emoji-picker/issues)