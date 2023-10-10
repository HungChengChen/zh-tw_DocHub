# 用Python 調用 `llama.cpp`

本教程旨在指導讀者通過一個基於Python的封裝，逐步了解如何在本地機器上運行和利用llama.cpp，一個強大的C++庫，用於操作大語言模型。
# 安裝指南

## 使用 Linux 或 Windows WSL
如果您使用的是 `Linux` 或 `Windows 的子系統（WSL）`，可以直接使用 PyPI 進行安裝：
```bash
    pip install llama-cpp-python
```
### 處理安裝問題
如果您在先前的安裝中遇到任何問題，或者想要確保使用最新版本，可以使用下面的命令強制重新安裝、升級，並避免使用快取：
```bash
    pip install llama-cpp-python --force-reinstall --upgrade --no-cache-dir
```
這將確保您安裝或更新到 llama-cpp-python 的最新版本，並且在安裝過程中不會使用可能已經過時的快取版本。

對於 Windows 子系統（WSL）的安裝方法，請[參閱此處](https://learn.microsoft.com/zh-tw/windows/wsl/install)

## Windows 安裝注意事項
在 Windows 下通過 PyPI 安裝會遇到問題。等待官方有釋出新版本。

## 下載模型，=
需要中文模型的資訊，可以參考[這裡](../Windows_Installation/README.md#3-下載模型權重)

## 量化模型
量化模型的詳細資訊，請參考[這裡](../Windows_Installation/README.md#6-量化模型權重)

## High-level API 使用範例
在 model_path 參數中指定模型的位置：
```python
    from llama_cpp import Llama
    llm = Llama(model_path="./zh-models/7B/ggml-model-q4_0.gguf")
    output = llm("Q: Name the planets in the solar system? A: ", max_tokens=32, stop=["Q:", "\n"], echo=True)
```
## Web Server
```bash
    pip install llama-cpp-python[server]
    python3 -m llama_cpp.server --model zh-models/7B/ggml-model-q4_0.gguf
```
導航到 http://localhost:8000/docs 以查看 OpenAPI 文件。