# Spelling Bee 訓練器

## 專案概述
單頁式 HTML 應用程式，幫助小朋友準備 Spelling Bee 比賽。包含練習模式、預演模式、錯題集訓營。

## 技術棧
- 純前端：HTML + JavaScript（無框架）
- 樣式：TailwindCSS（CDN）
- 發音：Web Speech API（`speechSynthesis`）
- 字型：Fredoka（Google Fonts）
- 圖示：Font Awesome 6

## 核心功能

### 練習模式
- 顯示大字單字卡（護眼配色）
- 點擊播放發音（自動播放兩次）
- 左右切換瀏覽同組 5 個單字

### 預演模式
- 家長操作：播放單字發音出題
- 小孩口頭拼字後，顯示答案
- 三種評分：不熟（重考）、還可以（保留）、OK（完成）
- 全組完成後可解鎖下一組

### 錯題集訓營 (Error Bank)
- 自動收集被標記為「不熟」或「還可以」的單字
- 集中複習弱點單字，連續 3 次 OK 才能畢業
- 頂部紅色橫幅顯示累積錯題數，點擊進入特訓

### 練習日誌
- 每日足跡：記錄每天練習的單字與次數
- 單字排行榜：依練習次數排序，顯示所屬組別
- 可載入範例資料預覽功能

### 進度管理
- 組別選擇器：下拉選單可跳回已解鎖的組別複習
- 匯出/匯入：Base64 編碼的進度代碼，支援跨裝置同步
- 重置：清除所有進度回到初始狀態

## 資料結構
- `fullWordList`：100 個單字陣列
- `BATCH_SIZE`：每組 5 個
- `STORAGE_KEY`：`spelling_bee_progress_v4`（含舊版自動遷移）
- `state` 物件管理：
  - `currentBatchIndex`：當前檢視的組別
  - `maxUnlockedBatchIndex`：最高解鎖進度
  - `mode`：練習/預演/集訓模式
  - `practiceCardIndex`：練習模式索引
  - `rehearsalQueue`：預演佇列
  - `errorBank`：錯題集（含 streak 連續正確次數）
  - `bootcampQueue`：集訓佇列
  - `practiceLog`：練習日誌（daily/total）

## 部署
- GitHub Pages：https://huansbox.github.io/spelling-bee-trainer/
- 分支：master

## 開發注意事項
- 單字順序固定（已移除 shuffle）
- 預演模式按原始順序出題
- 所有邏輯皆在單一 index.html 內
