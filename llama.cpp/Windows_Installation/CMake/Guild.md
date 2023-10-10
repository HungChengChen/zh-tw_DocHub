# 在 Windows 上安裝 C 語言編譯器和 CMake

## 安裝 C 語言編譯器
詳細的 C 語言編譯器安裝指南可參見[此處](../Windows_Installation/README.md#windows下c語言編譯器的安裝)。

## 安裝 CMake
- 訪問 [CMake 官方網站](https://cmake.org/download/) 下載頁。
- 選擇 `Windows x64 Installer` 並下載。
- 在安裝過程中，請確保選中 `Add CMake to the system PATH for all users` 選項。

### 驗證CMake安裝成功：

在終端機中輸入以下命令並確認輸出與下方範例相符：
```bash
    cmake --version
```
預期輸出：
```bash
    cmake version 3.27.6

    CMake suite maintained and supported by Kitware (kitware.com/cmake).
```
### 設定 CMake 預設的 C 編譯器
在 Windows 中使用 CMake 時，可以通過 -G 選項指定生成器（generator）。例如，若要使用 "MinGW Makefiles" 生成器，輸入：
```bash
    cmake -G "MinGW Makefiles" [path to source]
```
但由於在使用 PyPI 進行安裝時無法指定生成器，我們需要將 `MinGW Makefiles` 設定為默認選項。這可以通過將 `CMAKE_GENERATOR` 環境變數加入系統環境變數來完成。

### 如何設定環境變數

1. 右鍵點選 `此電腦` 或 `電腦`，選擇 `屬性`。
2. 點擊 `進階系統設定`。
3. 在系統屬性視窗中，點擊 `環境變數`。
4. 在環境變數視窗中，點擊 `新建`，在系統變數區塊新增一個變數。
   - 變數名稱：`CMAKE_GENERATOR`
   - 變數值：`MinGW Makefiles`
5. 點擊 `確定` 儲存設定。

以下是設定的示意圖：

![環境變數示例圖](./Images/image_0.png)