## Vue3 前端新手營 Vite & Vue - 元件拆分與資料傳遞

此專案為六角學院 2025 Vue3 前端新手營 Vite & Vue 作業

- [GitHub Page Demo](https://rabbitoyo.github.io/hex-vite-vue-components/)
- [Layout CodePen](https://codepen.io/hexschool/pen/EaVwgmK)

### 🛠 使用技術

- Bootstrap 5
- Vite
- Vue 3

### 💻 安裝執行

- 將專案 clone 到本地端

```bash
git clone https://github.com/rabbitoyo/hex-vite-vue-components.git
```

- 安裝執行

```bash
npm install				// 安裝
npm run dev				// 執行
```

- 瀏覽器訪問

```bash
http://localhost:5173/
```

### 🗂 專案設置

```
App					    # 父元件
├── ProductList         # Props: products, Emit: add-cart
├── Cart                # Props: items, Emit: remove-cart
└── Notification        # Inject: notificationState, showNotification
```

### 🌟 未來規劃

- API 開發 & 第三方驗證機制
