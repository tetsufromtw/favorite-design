# GitHub Repo Cleaner — Wispr 網站風格設計系統規範

> 本文檔記錄完整的視覺設計規範，支援 Angular+Sass、React+Tailwind、Next.js 等多種技術棧實作。致力於提供優雅、一致、可重用的設計語言。

---

## 📋 目錄

1. [設計理念](#設計理念)
2. [色彩系統](#色彩系統)
3. [字體系統](#字體系統)
4. [間距與佈局](#間距與佈局)
5. [組件規範](#組件規範)
6. [響應式設計](#響應式設計)
7. [技術實作指南](#技術實作指南)
8. [無障礙設計](#無障礙設計)
9. [動畫與互動](#動畫與互動)

---

## 🎨 設計理念

**核心調性**：Wispr 網站風格 — 奶油底色 + 薰衣草主色 + 深墨綠公告區  
**設計原則**：低對比大面積背景、清爽字距、溫潤圓角、優雅極簡

### 關鍵特色

- 🧈 **奶油質感**：`#faf7f2` 作為溫暖基調
- 🌸 **薰衣草紫**：`#9f88c8` 主品牌色，柔和不刺眼
- 🌲 **深墨綠**：`#0e3b2e` 公告與重要資訊背景
- ✨ **低對比美學**：避免強烈黑白對比，營造舒適視覺體驗

---

## 🎨 色彩系統

### 基礎色彩 Token

```css
:root {
  /* === 表面與文字 === */
  --bg: #ffffff; /* 主背景（可切換為奶油模式）*/
  --bg-cream: #faf7f2; /* 奶油色背景，選中狀態/大區塊 */
  --surface: #ffffff; /* 卡片/輸入框背景 */
  --fg: #111418; /* 主要文字色 */
  --muted: #6b7280; /* 次要文字色 */
  --border: #e7e1da; /* 邊框色 */

  /* === 品牌色彩 === */
  --primary: #9f88c8; /* 主按鈕/重點色（薰衣草紫）*/
  --primary-ink: #2a2250; /* 主色上的文字（深紫）*/
  --accent: #d9c2c0; /* 柔霧粉，輔助色 */

  /* === 功能性色彩 === */
  --success: #1f8a70; /* 成功狀態 */
  --warning: #b7791f; /* 警告狀態 */
  --danger: #b42318; /* 危險/錯誤狀態 */

  /* === 公告區域 === */
  --announce-bg: #0e3b2e; /* 深墨綠公告背景 */
  --announce-fg: #ffffff; /* 公告文字色 */

  /* === 熱度梯度（5階） === */
  --heat-1: #d9c2c0; /* 最低（accent）*/
  --heat-2: #cbb0cf;
  --heat-3: #b9a1d6;
  --heat-4: #a58bcf;
  --heat-5: #9f88c8; /* 最高（primary）*/
}

/* 奶油主題模式 */
[data-theme="cream"] {
  --bg: var(--bg-cream);
}
```

### 色彩使用指南

| 使用情境     | 推薦色彩                      | 說明                  |
| ------------ | ----------------------------- | --------------------- |
| 主要操作按鈕 | `primary` + `primary-ink`     | 薰衣草紫底 + 深紫文字 |
| 次要按鈕     | `surface` + `fg` + `border`   | 白底黑字有邊框        |
| 危險操作     | `danger` + `white`            | 紅底白字              |
| 資訊卡片     | `surface` + `border`          | 白底淺色邊框          |
| 選中狀態     | `bg-cream`                    | 奶油色背景            |
| 重要公告     | `announce-bg` + `announce-fg` | 深綠底白字            |

---

## ✍️ 字體系統

### 字體家族

**英文與中文環境**

```css
/* Display 標題字體 */
--font-display: "EB Garamond", serif;
/* UI 介面字體 */
--font-ui: "Figtree", ui-sans-serif, system-ui, -apple-system, "Segoe UI", sans-serif;
```

**日文環境自動切換**

```css
:lang(ja) {
  --font-display: "Noto Serif JP", serif;
  --font-ui: "Noto Sans JP", sans-serif;
}
```

### 字體權重與尺寸

```css
:root {
  /* === 字體尺寸（rem）=== */
  --font-size-display: 3rem; /* 主標題 */
  --font-size-h1: 2.25rem; /* 一級標題 */
  --font-size-h2: 1.75rem; /* 二級標題 */
  --font-size-h3: 1.375rem; /* 三級標題 */
  --font-size-body: 1rem; /* 正文 */
  --font-size-caption: 0.875rem; /* 輔助文字 */

  /* === 行高 === */
  --line-height-heading: 1.15; /* 標題行高 */
  --line-height-body: 1.6; /* 內文行高 */
}
```

### 字體權重規範

| 用途     | 英文/中文   | 日文          | 權重    |
| -------- | ----------- | ------------- | ------- |
| Display  | EB Garamond | Noto Serif JP | 700     |
| H1       | EB Garamond | Noto Serif JP | 700     |
| H2       | EB Garamond | Noto Serif JP | 600     |
| H3       | EB Garamond | Noto Serif JP | 600     |
| Body     | Figtree     | Noto Sans JP  | 400     |
| UI 按鈕  | Figtree     | Noto Sans JP  | 500-600 |
| 強調文字 | Figtree     | Noto Sans JP  | 700     |

---

## 📐 間距與佈局

### 間距系統

```css
:root {
  /* === 間距階層 === */
  --space-xs: 0.25rem; /* 4px - 最小間距 */
  --space-sm: 0.5rem; /* 8px - 小間距 */
  --space-md: 1rem; /* 16px - 標準間距 */
  --space-lg: 1.5rem; /* 24px - 大間距 */
  --space-xl: 2rem; /* 32px - 特大間距 */
  --space-2xl: 3rem; /* 48px - 區塊間距 */
  --space-3xl: 4rem; /* 64px - 頁面級間距 */
}
```

### 圓角與邊框

```css
:root {
  --radius: 12px; /* 全站統一圓角 */
  --ring: 0 0 0 3px rgba(159, 136, 200, 0.35); /* Focus 外環 */
}
```

### 陰影系統

```css
:root {
  /* === 陰影層級 === */
  --shadow-sm: 0 1px 2px 0 rgba(0, 0, 0, 0.05);
  --shadow-md: 0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06);
  --shadow-lg: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
}
```

### 佈局容器

```css
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 var(--space-md);
}

.card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  box-shadow: var(--shadow-sm);
  padding: var(--space-lg);
}
```

---

## 🧩 組件規範

### 按鈕組件

#### 主要按鈕（Primary）

```css
.btn-primary {
  background: var(--primary);
  color: var(--primary-ink);
  border: none;
  border-radius: var(--radius);
  padding: var(--space-sm) var(--space-lg);
  font-weight: 600;
  font-size: var(--font-size-body);
  cursor: pointer;
  transition: all 0.15s ease;
  outline: none;
}

.btn-primary:hover {
  filter: brightness(0.95);
}

.btn-primary:focus-visible {
  box-shadow: var(--ring);
}
```

#### 次要按鈕（Secondary）

```css
.btn-secondary {
  background: var(--surface);
  color: var(--fg);
  border: 1px solid var(--border);
  /* 其他屬性同 primary */
}

.btn-secondary:hover {
  border-color: var(--primary);
  background: var(--bg-cream);
}
```

#### 危險按鈕（Danger）

```css
.btn-danger {
  background: var(--danger);
  color: white;
  border: none;
  /* 其他屬性同 primary */
}
```

### 輸入框組件

```css
.input {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  padding: var(--space-sm) var(--space-md);
  font-size: var(--font-size-body);
  color: var(--fg);
  transition: all 0.15s ease;
  outline: none;
}

.input:hover {
  border-color: var(--primary);
}

.input:focus {
  border-color: var(--primary);
  box-shadow: var(--ring);
}

.input::placeholder {
  color: var(--muted);
}
```

### 卡片組件

```css
.card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  box-shadow: var(--shadow-sm);
  overflow: hidden;
  transition: box-shadow 0.15s ease;
}

.card:hover {
  box-shadow: var(--shadow-md);
}

.card-header {
  padding: var(--space-lg);
  border-bottom: 1px solid var(--border);
  background: var(--bg-cream);
}

.card-body {
  padding: var(--space-lg);
}

.card-footer {
  padding: var(--space-md) var(--space-lg);
  border-top: 1px solid var(--border);
  background: var(--bg-cream);
}
```

### 公告橫幅組件

```css
.banner {
  background: var(--announce-bg);
  color: var(--announce-fg);
  padding: var(--space-md) var(--space-lg);
  border-radius: var(--radius);
  margin-bottom: var(--space-lg);
}

.banner-icon {
  margin-right: var(--space-sm);
  color: var(--announce-fg);
}
```

---

## 📱 響應式設計

### 斷點系統

```css
/* 手機 */
@media (max-width: 767px) {
  /* mobile */
}

/* 平板 */
@media (min-width: 768px) and (max-width: 1023px) {
  /* tablet */
}

/* 桌面 */
@media (min-width: 1024px) {
  /* desktop */
}

/* 大型桌面 */
@media (min-width: 1440px) {
  /* large-desktop */
}
```

### 響應式間距

```css
.container {
  padding: 0 var(--space-md);
}

@media (max-width: 767px) {
  .container {
    padding: 0 var(--space-sm);
  }

  h1 {
    font-size: calc(var(--font-size-h1) * 0.85);
  }
  h2 {
    font-size: calc(var(--font-size-h2) * 0.9);
  }
}
```

---

## 🛠 技術實作指南

### Angular + SCSS 實作

#### 1. 設置 Design Tokens

```scss
// _tokens.scss
:root {
  /* 將上述所有 CSS Variables 定義於此 */
}

// Sass 變數映射
$colors: (
  primary: var(--primary),
  surface: var(--surface),
  // ... 其他色彩
);

$spacing: (
  xs: var(--space-xs),
  sm: var(--space-sm),
  // ... 其他間距
);
```

#### 2. 建立 Mixins

```scss
// _mixins.scss
@mixin font-display() {
  font-family: var(--font-display);
  font-size: var(--font-size-display);
  font-weight: 700;
  line-height: var(--line-height-heading);
}

@mixin btn-base() {
  border-radius: var(--radius);
  padding: var(--space-sm) var(--space-lg);
  font-size: var(--font-size-body);
  font-weight: 600;
  transition: all 0.15s ease;
  cursor: pointer;
  outline: none;

  &:focus-visible {
    box-shadow: var(--ring);
  }
}

@mixin focus-ring() {
  &:focus-visible {
    outline: none;
    box-shadow: var(--ring);
  }
}
```

#### 3. 組件樣式結構

```scss
// component.scss
@use "../../../styles/tokens";
@use "../../../styles/mixins" as mix;

.component {
  @include mix.card();

  &__header {
    @include mix.font-heading(2);
    color: var(--fg);
    margin-bottom: var(--space-md);
  }

  &__button {
    @include mix.btn-base();
    background: var(--primary);
    color: var(--primary-ink);

    &:hover {
      filter: brightness(0.95);
    }
  }
}
```

### React + Tailwind CSS 實作

#### 1. Tailwind 配置

```js
// tailwind.config.js
module.exports = {
  content: ["./src/**/*.{js,ts,jsx,tsx}"],
  theme: {
    extend: {
      colors: {
        bg: "var(--bg)",
        "bg-cream": "var(--bg-cream)",
        surface: "var(--surface)",
        fg: "var(--fg)",
        muted: "var(--muted)",
        border: "var(--border)",
        primary: "var(--primary)",
        "primary-ink": "var(--primary-ink)",
        accent: "var(--accent)",
        success: "var(--success)",
        warning: "var(--warning)",
        danger: "var(--danger)",
        "announce-bg": "var(--announce-bg)",
        "announce-fg": "var(--announce-fg)",
      },
      fontFamily: {
        display: "var(--font-display)",
        ui: "var(--font-ui)",
      },
      fontSize: {
        display: "var(--font-size-display)",
        h1: "var(--font-size-h1)",
        h2: "var(--font-size-h2)",
        h3: "var(--font-size-h3)",
        body: "var(--font-size-body)",
        caption: "var(--font-size-caption)",
      },
      spacing: {
        xs: "var(--space-xs)",
        sm: "var(--space-sm)",
        md: "var(--space-md)",
        lg: "var(--space-lg)",
        xl: "var(--space-xl)",
        "2xl": "var(--space-2xl)",
        "3xl": "var(--space-3xl)",
      },
      borderRadius: {
        DEFAULT: "var(--radius)",
      },
      boxShadow: {
        sm: "var(--shadow-sm)",
        md: "var(--shadow-md)",
        lg: "var(--shadow-lg)",
      },
    },
  },
  plugins: [],
};
```

#### 2. 全域 CSS

```css
/* globals.css */
@import url("https://fonts.googleapis.com/css2?family=EB+Garamond:wght@600;700&family=Figtree:wght@400;500;600&display=swap");

:root {
  /* 在此定義所有 Design Tokens */
}

@layer base {
  body {
    @apply bg-bg text-fg font-ui;
    font-size: var(--font-size-body);
    line-height: var(--line-height-body);
  }

  h1 {
    @apply font-display text-h1 font-bold leading-tight;
  }
  h2 {
    @apply font-display text-h2 font-semibold leading-tight;
  }
  h3 {
    @apply font-display text-h3 font-semibold leading-tight;
  }
}

@layer components {
  .btn-primary {
    @apply bg-primary text-primary-ink px-lg py-sm rounded font-semibold 
           transition-all duration-150 hover:brightness-95 
           focus:outline-none focus-visible:ring-2 focus-visible:ring-primary focus-visible:ring-opacity-35;
  }

  .btn-secondary {
    @apply bg-surface text-fg border border-border px-lg py-sm rounded font-semibold 
           transition-all duration-150 hover:border-primary hover:bg-bg-cream
           focus:outline-none focus-visible:ring-2 focus-visible:ring-primary focus-visible:ring-opacity-35;
  }

  .card {
    @apply bg-surface border border-border rounded shadow-sm 
           transition-shadow duration-150 hover:shadow-md;
  }
}
```

#### 3. React 組件實作

```jsx
// Button.jsx
const Button = ({ variant = "primary", size = "md", children, className = "", ...props }) => {
  const baseClasses = "font-semibold rounded transition-all duration-150 focus:outline-none focus-visible:shadow-[var(--ring)]";

  const variantClasses = {
    primary: "bg-primary text-[color:var(--primary-ink)] hover:brightness-95",
    secondary: "bg-surface text-fg border border-border hover:border-primary hover:bg-[color:var(--bg-cream)]",
    danger: "bg-danger text-white hover:brightness-95",
  };

  const sizeClasses = {
    sm: "px-md py-xs text-caption",
    md: "px-lg py-sm text-body",
    lg: "px-xl py-md text-body",
  };

  return (
    <button className={`${baseClasses} ${variantClasses[variant]} ${sizeClasses[size]} ${className}`} {...props}>
      {children}
    </button>
  );
};
```

---

## ♿ 無障礙設計

### 色彩對比度

- **主文字** (`--fg`) 對 **背景** (`--bg`) ≥ 7:1
- **次要文字** (`--muted`) 對 **背景** ≥ 4.5:1
- **按鈕文字** (`--primary-ink`) 對 **主色** (`--primary`) ≥ 4.5:1

### Focus 管理

```css
/* 全站 Focus 樣式 */
*:focus-visible {
  outline: none;
  box-shadow: var(--ring);
  border-radius: 2px;
}

/* 跳過連結 */
.skip-link {
  position: absolute;
  top: -40px;
  left: 6px;
  background: var(--primary);
  color: var(--primary-ink);
  padding: 8px;
  text-decoration: none;
  border-radius: var(--radius);
  z-index: 1000;
}

.skip-link:focus {
  top: 6px;
}
```

### ARIA 屬性使用

- 所有互動元件必須有適當的 `aria-label` 或 `aria-labelledby`
- 表單錯誤使用 `aria-describedby` 和 `role="alert"`
- 對話框使用 `role="dialog"` 和焦點陷阱
- 表格使用 `scope="col"` 和 `scope="row"`

---

## 🎬 動畫與互動

### 過渡效果

```css
:root {
  /* === 動畫時間 === */
  --transition-fast: 0.15s;
  --transition-normal: 0.3s;
  --transition-slow: 0.5s;

  /* === 緩動函數 === */
  --ease-out: cubic-bezier(0.16, 1, 0.3, 1);
  --ease-in-out: cubic-bezier(0.4, 0, 0.2, 1);
}

/* 基礎過渡 */
.transition {
  transition: all var(--transition-fast) var(--ease-out);
}

/* 懸停效果 */
.hover-lift {
  transition: transform var(--transition-fast) var(--ease-out);
}

.hover-lift:hover {
  transform: translateY(-2px);
}
```

### 載入狀態

```css
/* 骨架屏動畫 */
@keyframes skeleton-pulse {
  0%,
  100% {
    opacity: 1;
  }
  50% {
    opacity: 0.4;
  }
}

.skeleton {
  background: var(--bg-cream);
  animation: skeleton-pulse 2s cubic-bezier(0.4, 0, 0.6, 1) infinite;
}

/* 旋轉載入器 */
@keyframes spin {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

.loading-spinner {
  animation: spin 1s linear infinite;
}
```

---

## 🌍 多語言字體切換

### 自動字體切換邏輯

```css
/* 預設英文/中文字體 */
body {
  font-family: var(--font-ui);
}

h1,
h2,
h3,
.display {
  font-family: var(--font-display);
}

/* 日文環境自動切換 */
:lang(ja) body {
  font-family: "Noto Sans JP", sans-serif;
}

:lang(ja) h1,
:lang(ja) h2,
:lang(ja) h3,
:lang(ja) .display {
  font-family: "Noto Serif JP", serif;
}
```

### JavaScript 動態切換

```javascript
// 語言切換功能
const switchLanguage = (lang) => {
  document.documentElement.lang = lang;

  // 動態載入對應字體
  if (lang === "ja") {
    loadGoogleFonts("Noto+Serif+JP:wght@600;700&family=Noto+Sans+JP:wght@400;500;700");
  } else {
    loadGoogleFonts("EB+Garamond:wght@600;700&family=Figtree:wght@400;500;600");
  }
};

const loadGoogleFonts = (fontQuery) => {
  const link = document.createElement("link");
  link.href = `https://fonts.googleapis.com/css2?family=${fontQuery}&display=swap`;
  link.rel = "stylesheet";
  document.head.appendChild(link);
};
```

---

## 📋 檢核清單

### 🎨 視覺一致性

- [ ] 色彩符合 Wispr 網站調性（奶油+薰衣草+深綠）
- [ ] 圓角統一使用 `--radius: 12px`
- [ ] 間距使用標準階層（xs/sm/md/lg/xl/2xl/3xl）
- [ ] 陰影層級正確（sm/md/lg）

### ✍️ 字體規範

- [ ] 英文使用 EB Garamond + Figtree
- [ ] 日文自動切換至 Noto Serif JP + Noto Sans JP
- [ ] 字重符合規範（標題 700/600，內文 400）
- [ ] 行高合適（標題 1.15，內文 1.6）

### ♿ 無障礙標準

- [ ] 色彩對比度達標（主文 ≥7:1，次要 ≥4.5:1）
- [ ] Focus 狀態可見且一致
- [ ] ARIA 屬性完整
- [ ] 鍵盤導航流暢

### 📱 響應式適配

- [ ] 手機端佈局完整
- [ ] 平板端過渡自然
- [ ] 桌面端充分利用空間
- [ ] 觸控互動友善

### 🎬 互動體驗

- [ ] 過渡動畫流暢（0.15s 標準）
- [ ] 懸停效果適度
- [ ] 載入狀態明確
- [ ] 錯誤提示清晰

---

## 📚 資源與工具

### 字體資源

- [EB Garamond - Google Fonts](https://fonts.google.com/specimen/EB+Garamond)
- [Figtree - Google Fonts](https://fonts.google.com/specimen/Figtree)
- [Noto Serif JP - Google Fonts](https://fonts.google.com/noto/specimen/Noto+Serif+JP)
- [Noto Sans JP - Google Fonts](https://fonts.google.com/noto/specimen/Noto+Sans+JP)

### 色彩工具

- [WebAIM 對比度檢測器](https://webaim.org/resources/contrastchecker/)
- [Coolors 調色盤產生器](https://coolors.co/)

### 設計工具

- [Figma Community - Design System](https://www.figma.com/community/design-systems)
- [Adobe Color](https://color.adobe.com/)

---

_最後更新：2025-09-01_  
_版本：v1.0.0_  
_維護者：GitHub Repo Cleaner Team_
