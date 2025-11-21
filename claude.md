# Spelling Bee 訓練器

## 專案概述
單頁式 HTML 應用程式，幫助小朋友準備 Spelling Bee 比賽。包含練習模式和預演模式。

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

## 資料結構
- `fullWordList`：100 個單字陣列
- `BATCH_SIZE`：每組 5 個
- `state` 物件管理：當前組別、模式、練習索引、預演佇列

## 部署
- GitHub Pages：https://huansbox.github.io/spelling-bee-trainer/
- 分支：master

## 開發注意事項
- 單字順序固定（已移除 shuffle）
- 預演模式按原始順序出題
- 所有邏輯皆在單一 index.html 內

## 待新增功能

### 錯題集訓營 (Error Bank)
**痛點**：Spelling Bee 的勝負關鍵在於「不熟的字」。目前的機制是「當下練熟就過關」，但人類大腦會遺忘。

**功能**：增加一個「複習弱點」按鈕。系統會將所有曾經被標記為 Retry（不熟）或 Hard（還可以）的單字收集起來。

**效益**：在考前衝刺時，不需重跑所有簡單字（如 ace），只專攻那些曾經卡住的單字（如 checkers, know-how）。符合 80/20 法則。
