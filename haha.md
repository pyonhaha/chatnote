---1
為什麼logging的info輸出是標準錯誤打印？而不是標準輸出


---2
<br>在 Python 的 `logging` 模組中，預設情況下，所有的日誌訊息（包括 `info` 級別）會輸出到標準錯誤流（`stderr`），而不是標準輸出流（`stdout`）。這是設計上的選擇，旨在區分正常的程式輸出與診斷訊息。

### 原因解析：
1. **標準錯誤用於診斷訊息**:
   標準輸出（`stdout`）通常用來顯示程式的主要結果或正常輸出的內容，而標準錯誤（`stderr`）則專門用來顯示錯誤、警告、或診斷訊息。日誌屬於診斷性資料，因此預設發送到 `stderr`.

2. **避免干擾正常輸出**:
   如果日誌訊息被打印到 `stdout`，可能會與程式的主要輸出混合在一起，導致難以解析或處理程式的結果。例如，在命令列工具中，你可能希望程式的主要結果經由管道傳送給其他工具，而將日誌獨立保留在錯誤流中。

3. **可分離性和靈活性**:
   使用 `stderr` 讓日誌與正常輸出分離，使得使用者可以更方便地將兩者重定向到不同的位置。例如，可以將主要結果重定向到檔案，而讓日誌仍然顯示在終端機上。

### 如何修改為使用 `stdout`
如果你希望 `logging.info()` 等級的日誌訊息輸出到標準輸出，你可以透過修改 `logging.StreamHandler()` 的目標流來達成：

```python
import logging
import sys

# 配置 logging
logger = logging.getLogger()
logger.setLevel(logging.INFO)

# 將 StreamHandler 指向 stdout 而非 stderr
handler = logging.StreamHandler(sys.stdout)
handler.setLevel(logging.INFO)

# 設定格式化器 (可選)
formatter = logging.Formatter('%(asctime)s - %(levelname)s - %(message)s')
handler.setFormatter(formatter)

# 加入 handler 到 logger
logger.addHandler(handler)

# 測試 info 輸出的行為
logger.info("This will be printed to standard output (stdout).")
```

透過上述方法，你可以讓所有的資訊級別或其他指定級別的日誌訊息直接打印到標準輸出。

### 結論：
Python 的 `logging` 預設使用 `stderr` 是一種良好的實踐，但根據你的需求，你完全可以自訂它的行為。
<br>--- end ---

---1
在logging以外的地方
我要如何將stderr全部導向stdout

