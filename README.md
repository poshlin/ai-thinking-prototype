# 《AI 思維：實戰問題解決課》課程著陸頁 Prototype

橘子蘋果程式學苑全新 AI 課程的著陸頁設計稿，**單檔 HTML + 靜態素材** 即可預覽。

## 🔗 線上預覽

- **預覽（GitHub Pages）**：<https://poshlin.github.io/ai-thinking-prototype/>
- 直接打開 `index.html` 也可以本機觀看（不需要起 server）

---

## 📁 檔案結構

```
ai-thinking-prototype/
├─ index.html              # 全部頁面（單一 HTML 檔，含 inline CSS 與 JS）
├─ README.md               # 本檔
└─ assets/
   ├─ logo-2023-color.svg          # 主品牌 Logo（彩色，導覽列用）
   ├─ logo-2023-white.svg          # Logo 白色版（深色 footer 用）
   ├─ hero-ai-thinking.png         # Hero 主視覺（孩子 + AI 創作）
   ├─ topic-1-main.jpg             # 主題 1：綠色小怪獸三視圖
   ├─ topic-1-sub1.jpg             # 主題 1 副圖：3D 玩具模型
   ├─ topic-1-sub2.jpg             # 主題 1 副圖:名畫風格創作
   ├─ topic-2-main.jpg             # 主題 2：太空人電影海報
   ├─ topic-2-sub1.jpg             # 主題 2 副圖：太空繪本
   ├─ topic-3-main.jpg             # 主題 3：卡牌對戰遊戲
   ├─ topic-3-sub1.jpg             # 主題 3 副圖：戰鬥卡牌（反擊）
   ├─ topic-4-main.jpg             # 主題 4：個人作品集網頁
   ├─ topic-4-sub1.jpg             # 主題 4 副圖：Devil Tea 品牌應用
   └─ topic-4-sub2.jpg             # 主題 4 副圖：簡易網頁設計
```

---

## 🎨 設計依據

- **品牌規範**：依《橘子蘋果_品牌設計規範 v2.0（官方 CIS 版）》三主色（橘 `#FFA300` / 紅 `#FF5859` / 藍綠 `#00C4B3`）+ Noto Sans TC
- **視覺風格**：軟性、幾何、簡潔（避免過於童趣，符合 CIS 視覺定位）
- **靈感參考**：[atelier-null.com](https://atelier-null.com/) 的圓形蒙版、波浪過場、手繪虛線框設計手法

---

## 🛠 技術棧

| 類別 | 內容 |
|---|---|
| 框架 | Bootstrap 5.3（CDN） |
| 動畫 | AOS 2.3.4（CDN，scroll-trigger 進場動畫） |
| 字體 | Google Fonts — Noto Sans TC（300 / 400 / 500 / 700 / 900） |
| 影片 | YouTube 縮圖 + 連結（避開 embed 限制） |
| JS | 純原生（滑鼠跟隨、滾動進度條、漢堡選單、FAQ／Unit 摺疊、數字計數動畫、視差） |

**沒有任何 build process** — 開啟 `index.html` 即可看到完整效果。

---

## 📑 頁面區塊一覽（共 14 段）

1. 導覽列（Logo + 5 大選單 + 取得免費試聽 + 登入）
2. **Hero**：金句副標、3 個信任數字、3 個對話泡泡、CTA
3. 為什麼孩子不能只學「使用 AI」？（3 大論點）
4. 課程定位（大引號）+ **完整課程資訊表（8 項）**
5. **十多年累積的程式教育信任**（3 大數據 + 3 個課程獨家亮點）
6. **AI 時代孩子需要的五大關鍵能力**
7. **🔥 表面 vs 實際**（6 列對照 + 黑底結尾金句）
8. **每堂課怎麼上**（Phase 01 表達練習 5 步 + Phase 02 主題任務 5 步）
9. **四大實戰主題**（圓形蒙版 + 浮動副圖縮圖 + 手繪虛線框）
10. 看見 AI 創作的無限可能（YouTube 縮圖連結）
11. 完整 15 堂課表（4 個 Unit 摺疊式）
12. **🔥 AI 思維課 vs AI 實作營對照** + 金句
13. **🔥 適合 / 不適合自我檢查**
14. **FAQ 13 題**
15. Footer CTA + 完整 Footer（4 欄連結 + 聯絡資訊）

---

## ⚠️ 已知待處理項目

| 項目 | 狀態 | 說明 |
|---|---|---|
| YouTube 影片 Error 153 | 暫用 thumbnail + 連結 | 需到 YouTube Studio 開啟「允許嵌入」後可改回 iframe embed |
| Hero 圖片大小 | 1.7 MB | 上線前建議壓縮為 WebP，預期可降到 200–400 KB |

---

## 👨‍💻 給工程師：上線到 Rails 官網的轉換建議

橘蘋官網是 **Rails 7 + SASS + Bootstrap 5.3**，這份設計稿可參考以下建議拆解：

### A. HTML 拆解
- 整份 `index.html` 拆為 ERB partials：
  - `_nav.html.erb`、`_hero.html.erb`、`_reasons.html.erb`、`_overview.html.erb`、`_trust.html.erb`、`_skills.html.erb`、`_vs_surface.html.erb`、`_flow.html.erb`、`_curriculum.html.erb`、`_video.html.erb`、`_syllabus.html.erb`、`_vs_camp.html.erb`、`_suitable.html.erb`、`_faq.html.erb`、`_footer_cta.html.erb`、`_footer.html.erb`
- 主視圖：`app/views/courses/ai_thinking.html.erb`，依序 render 上述 partials

### B. CSS / SCSS
- 整段 `<style>` 內的 CSS 抽出為 `app/assets/stylesheets/courses/ai_thinking.scss`
- 三主色變數已在 `:root`，可改為 SCSS 變數：
  ```scss
  $orange: #FFA300;
  $red:    #FF5859;
  $teal:   #00C4B3;
  ```
- 與全站既有的 SCSS partials（如 `_brand.scss`）整合，避免變數重複定義

### C. 圖片資源
- 所有 `assets/*` 內的圖移到 `app/assets/images/courses/ai_thinking/`
- HTML 內 `<img src="assets/...">` 改為 `<%= image_tag "courses/ai_thinking/..." %>`

### D. 字體與外部 CDN
- Bootstrap 5.3 / AOS / Google Fonts 使用 CDN 引入；如官網已有引入這些資源，**請複用、不要重複載入**
- AOS 初始化 JS 段已寫在頁尾 `<script>`，整合到全站 JS 載入流程即可

### E. YouTube 影片區
- 目前是 `<a>` 連結到 YouTube 觀看頁（避開 Error 153）
- YouTube 影片擁有者若已開啟「允許嵌入」，可改回 iframe：
  ```html
  <iframe src="https://www.youtube.com/embed/irlNGTb-ypc" ...></iframe>
  ```

### F. 表單／CTA 串接
- 所有「取得免費試聽」「立即報名」按鈕目前指向 `#cta` 或 `https://orangeapple.co/free-trial`
- 上線時改為實際的試聽預約表單路由

### G. RWD 已處理
- 設計稿已測試桌面 / 平板 / 手機三種斷點
- 1100px 以下導覽列收合為漢堡選單
- 768px 以下多數 grid 改單欄

---

## 📞 聯絡

- **設計／企劃**：林保旭（線上事業部 × 行銷部 總監）— [claude.003@orangeapple.co](mailto:claude.003@orangeapple.co)
- **品牌規範參考**：`橘子蘋果_品牌設計規範_v2.0.md`
- **課程素材參考**：教學部《AI 思維：實戰問題解決課》PDF 簡報

---

© 2026 橘子蘋果程式學苑｜OrangeApple Programming Academy
