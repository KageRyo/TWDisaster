# TWDisaster 臺灣歷史災害資料集

TWDisaster 是獨立、採用 UTF-8 CSV 的臺灣歷史天氣災害與有來源支持之應變事實資料集。0.1.1 版包含 **76 個事件、395 筆觀察、88 個來源及 89 筆事件—來源關聯**；來源所載的事件期間涵蓋 2001-06-22 至 2025-08-11。下載後即可用試算表或任何支援 CSV 的工具使用，不必安裝本專案的軟體。

首版收錄官方公開來源中的應變事實，屬於只記錄有證據的正向資料，並非臺灣所有災害或應變行動的完整清單。沒有觀察列不表示行動未發生。資料集不包含預報、建議、優先順序、候選排序、訓練標籤，也沒有將史料硬配到 20 公尺格網。

## 檔案

| 路徑 | 內容 |
| --- | --- |
| `data/events.csv` | 穩定事件識別碼及來源所載日期範圍 |
| `data/observations.csv` | 應變事實、時間、地點、來源與原文定位 |
| `data/sources.csv` | 出版機關、原始網址、取得時間、完整性及權利依據 |
| `data/event_sources.csv` | 明確的事件—來源關聯 |
| `schema/*.schema.json` | 四份 CSV 的列資料 JSON Schema |
| `metadata/dataset.json` | 範圍、筆數及版本 |
| `metadata/manifest.json`、`metadata/checksums.sha256` | 正式資料檔筆數與 SHA-256 |

用 UTF-8 及第一列欄名讀取 CSV。試算表可直接開啟；R 可使用 `read.csv("data/events.csv", fileEncoding = "UTF-8")`，Python 標準函式庫的 `csv.DictReader` 也能讀取，皆不需安裝本專案套件。欄名以 `_json` 結尾的儲存格包含一般 JSON 陣列或物件。觀察表以 `event_id` 與 `source_id` 分別連到事件表與來源表；`event_sources.csv` 列出所有不重複的事件—來源關聯。

空白儲存格表示未知、無證據或無資料，依欄位定義解讀；絕不自動當作零或否定。`attributes_json` 裡的 `0` 才是明確記錄的零，`[]` 表示已記錄的空清單。只有日期精度的行動以 `YYYY-MM-DD` 表示；有時間證據的值保留 ISO 8601 時區。事件日期是收錄來源的報告期間，不等於精確氣象起訖。地理範圍保持來源支持的尺度。

詳見[資料模型](docs/data-model.md)、[方法](docs/methodology.md)、[來源脈絡](docs/provenance.md)與[來源及權利](docs/sources.md)。本庫不包含原始文件。部分網址日後可能變更，另有 11 個來源缺少已驗證的原件雜湊；其餘缺口列於來源脈絡文件。

## 授權與引用

本庫原創說明、結構定義及資料集的選取與編排採用 [CC BY 4.0](LICENSE)。個別來源事實及來源素材仍受 [DATA_LICENSE.md](DATA_LICENSE.md)、`sources.csv` 與各機關公開再利用聲明所述權利限制；引用來源事實時請標示原始出版機關。本庫授權不取代上游權利，也不授權未收錄的 PDF、HTML 封存、圖片或標誌。

引用本版請使用 [CITATION.cff](CITATION.cff)；引用特定觀察時也請註明對應的原始機關及網址。
