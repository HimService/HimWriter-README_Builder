# HimWriter-README_Builder

[繁體中文](README.md) | [English](README_EN.md)


<blockquote style="color: lightblue;">
  <p><strong>提示！</strong><br>
  你可以在DOCS網站中查看文檔或繼續閱讀下方文檔:https://himservice-docs.himserver.com/#HimWriter-README_Builder_introduce</p>
</blockquote>


## 專案概述

**HimWriter-README_Builder** 是一個利用 Google Gemini API 自動生成 README.md 的工具。本專案旨在協助開發者快速建立專案文件，使用者可自訂語氣、語言，並選擇欲包含的章節，大幅簡化 README 檔案的撰寫流程。本工具提供圖形化使用者介面 (GUI)，操作簡便直觀，適用於各類軟體專案。

### 主要功能

*   **自動生成 README.md**: 基於專案檔案內容，自動產生結構化的 README.md 檔案。
*   **多種語言與語氣**: 支援多種語言 (如繁體中文、英文等) 及語氣 (如正式、技術性等)，可根據專案需求靈活調整。
*   **Gemini 模型選擇**: 允許使用者選擇不同的 Google Gemini 模型 (如 `gemini-pro`, `gemini-1.5-flash` 等) 以生成內容。
*   **章節自訂**:  使用者可指定 README 檔案中必須包含的章節，例如檔案架構、安裝說明等。
*   **圖形化使用者介面 (GUI)**:  採用 GUI 介面，提供友善的操作體驗。
*   **自動忽略資料夾**:  利用 Gemini API 分析專案目錄結構，自動建議並忽略虛擬環境、編譯輸出等非必要資料夾，提升 README 內容的精確性。
*   **錯誤處理與重試機制**:  針對 Gemini API 的配額限制進行錯誤處理，並具備重試機制，盡力提升工具的穩定性。

## 安裝

### 環境需求

*   **Python 3.7 或更高版本**
*   **pip** (Python 套件管理工具)

### 安裝步驟

1.  **下載專案**:
    ```bash
    cd HimWriter-README_Builder
    ```

2.  **安裝依賴套件**:
    在專案根目錄下，執行以下命令安裝專案所需的 Python 套件：
    ```bash
    pip install -r requirements.txt
    ```

3.  **設定 Gemini API 金鑰**:
    *   前往 [Google AI Studio](https://makersuite.google.com/app/apikey) 獲取 Gemini API 金鑰。
    *   開啟專案目錄下的 `config.py` 檔案。
    *   將 `API_KEY`  替換為您取得的 Gemini API 金鑰：
        ```python
        API_KEY = "YOUR_ACTUAL_API_KEY"
        ```

## 使用方法

1.  **執行應用程式**:
    在專案根目錄下，執行以下命令啟動 GUI 應用程式：
    ```bash
    python main.py
    ```

2.  **設定參數**:
    *   **專案路徑**:  點擊 "瀏覽" 按鈕或直接輸入您的專案根目錄路徑。
    *   **模型**:  從 "模型" 下拉選單中選擇您想要使用的 Gemini 模型。預設提供 `gemini-pro`, `gemini-1.5-pro`, `gemini-1.5-flash`, `gemini-2.0-flash-thinking-exp-01-21` 等選項。
    *   **語調**:  從 "語調" 下拉選單中選擇 README 的語氣，例如 "正式", "輕鬆", "技術性" 等。您也可以選擇 "其他" 並在下方輸入自訂語調。
    *   **語言**:  從 "語言" 下拉選單中選擇 README 的語言，例如 "繁體中文", "English" 等。
    *   **必須包含的內容**:  勾選您希望 README 包含的章節，例如 "檔案架構", "詳細安裝", "介紹", "專案架構" 等。您也可以勾選 "其他" 並輸入額外需要包含的章節名稱。

3.  **生成 README**:
    點擊 "生成" 按鈕，應用程式將開始讀取您的專案檔案，並調用 Gemini API 生成 README 內容。生成過程中，"執行狀態" 區域將顯示進度訊息，"生成結果" 區域將顯示生成的 README 內容 (Markdown 格式)。

4.  **儲存 README**:
    確認 "生成結果" 區域的 README 內容無誤後，點擊 "保存" 按鈕。選擇您想要儲存 README 檔案的路徑及檔名 (預設為 `generated/README.md`)，即可將生成的 README 檔案儲存至本地。

### 配置選項

在 `config.py` 檔案中，您可以修改以下配置選項：

*   **`MODELS`**:  此列表定義了可供選擇的 Gemini 模型。您可以根據需求添加或移除模型名稱。
*   **`SUPPORTED_LANGUAGES`**:  此列表定義了支援的 README 語言。您可以根據需求添加或移除語言名稱。
*   **`TONES`**:  此列表定義了預設的 README 語氣選項。您可以根據需求添加或移除語氣選項。

### 注意事項

*   首次使用前，請務必設定正確的 Gemini API 金鑰。
*   生成 README 內容的品質受 Gemini 模型能力及專案檔案內容影響。建議仔細審閱生成的 README 內容，並進行必要的修改。
*   請確保選擇的模型與API支援的模型類型相符，否則將無法運行
*   若遇到 Gemini API 配額限制錯誤 (HTTP 429)，應用程式會自動進行重試，並在 "執行狀態" 區域顯示相關訊息。請耐心等待或稍後再試。

## 目前問題

### 導出錯誤
- 如果導出的README.md有問題請直接複製GUI內生成的原始內容進行修改,我們已經在修復該問題中。

## 貢獻
如果您有新的功能建議或發現 Bug，請聯繫。
## 許可
請閱讀 `LICENSE` 文件。
