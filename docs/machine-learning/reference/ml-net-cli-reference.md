---
title: ML.NET CLI 命令參考
description: ML.NET CLI 工具中的 auto-train 命令概觀、範例和參考。
ms.date: 06/03/2020
ms.custom: mlnet-tooling
ms.openlocfilehash: 397f6fda8554024624b3ef630856dc8eca9696b2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594539"
---
# <a name="the-mlnet-cli-command-reference"></a>ML.NET CLI 命令參考

`classification`、 `regression` 和 `recommendation` 命令是 ML.NET CLI 工具所提供的主要命令。 這些命令可讓您使用自動化機器學習（AutoML），為分類、回歸和建議模型產生良好品質的 ML.NET 模型，以及用來執行/評分該模型的範例 c # 程式碼。 此外，系統會為您產生用來定型模型的 c # 程式碼，以研究模型的演算法和設定。

> [!NOTE]
> 本主題參考 ML.NET CLI 和 ML.NET AutoML，它們目前為公開預覽版，因此内容可能會有變更。

## <a name="overview"></a>概觀

使用範例：

```console
mlnet regression --dataset "cars.csv" --label-col price
```

`mlnet`ML 工作命令（ `classification` 、 `regression` 和）會 `recommendation` 產生下列資產：

- 隨時可用的序列化模型 .zip (「最佳模型」)。
- 用來執行/評分產生之模型的 c # 程式碼。
- C # 程式碼，其中包含用來產生該模型的定型代碼。

前兩個資產可以直接用於您的終端使用者應用程式（ASP.NET Core web 應用程式、服務、傳統型應用程式等），以使用模型進行預測。

第三個資產（訓練程式碼）會顯示 CLI 用來定型所產生模型的 ML.NET API 程式碼，因此您可以調查模型的特定演算法和設定。

## <a name="examples"></a>範例

分類問題最簡單的 CLI 命令（AutoML 會從所提供的資料推斷大部分的設定）：

```console
mlnet classification --dataset "customer-feedback.tsv" --label-col Sentiment
```

適用於迴歸問題的另一個簡單 CLI 命令：

``` console
mlnet regression --dataset "cars.csv" --label-col Price
```

使用訓練資料集、測試資料集和進一步自訂的明確引數來建立和定型分類模型：

```console
mlnet classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-col "InsuranceRisk" --cache on --train-time 600
```

## <a name="command-options"></a>命令選項

`mlnet`ML 工作命令（ `classification` 、 `regression` 和）會 `recommendation` 根據所提供的資料集和 ML.NET CLI 選項來訓練多個模型。 這些命令也會選取最佳的模型、將模型儲存為序列化的 .zip 檔案，並產生相關的 c # 程式碼來進行計分和定型。

### <a name="classification-options"></a>分類選項

`mlnet classification`執行會將分類模型定型。 如果您想要 ML 模型將資料分類成2個或多個類別（例如情感分析），請選擇此命令。

```console
mlnet classification

--dataset <path> (REQUIRED)

--label-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--ignore-cols <cols>

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

### <a name="regression-options"></a>回歸選項

`mlnet regression`執行將會定型回歸模型。 如果您想要 ML 模型預測數值（例如價格預測），請選擇此命令。

```console
mlnet classification

--dataset <path> (REQUIRED)

--label-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--ignore-cols <cols>

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

### <a name="recommendation-options"></a>建議選項

`mlnet recommendation`執行將會定型建議模型。  如果您想要讓 ML 模型根據評等向使用者推薦專案（例如產品建議），請選擇此命令。

```console
mlnet classification

--dataset <path> (REQUIRED)

--item-col <col> (REQUIRED)

--rating-col <col> (REQUIRED)

--user-col <col> (REQUIRED)

--cache <option>

--has-header (Default: true)

--log-file-path <path>

--name <name>

-o, --output <path>

--test-dataset <path>

--train-time <time> (Default: 30 minutes, in seconds)

--validation-dataset <path>

-v, --verbosity <v>

-?, -h, --help

```

不正確輸入選項會導致 CLI 工具發出有效輸入的清單和錯誤訊息。

## <a name="dataset"></a>資料集

`--dataset | -d` (string)

這個引數提供下列任一選項的檔案路徑：

- *答：整個資料集檔案：* 如果使用此選項，且使用者未提供 `--test-dataset` 和 `--validation-dataset` ，則會在內部使用交叉驗證（k-折迭等）或自動化資料分割方法來驗證模型。 在此情況下，使用者只需提供資料集檔案路徑。

- *B：訓練資料集檔案：* 如果使用者也提供模型驗證的資料集（使用 `--test-dataset` 和選擇性 `--validation-dataset` ），則 `--dataset` 引數表示只有「訓練資料集」。 例如，使用 80% - 20% 方法來驗證模型的品質並取得準確度計量時，「定型資料集」會有 80% 的資料，而「測試資料集」會有 20% 的資料。

## <a name="test-dataset"></a>測試資料集

`--test-dataset | -t` (string)

指向測試資料集檔案的檔案路徑，例如使用 80% - 20% 方法進行一般驗證來取得準確度計量時。

如果使用 `--test-dataset`，則也需要 `--dataset`。

除非使用 --validation-dataset，否則 `--test-dataset` 引數是選擇性的。 在此情況下，使用者必須使用三個引數。

## <a name="validation-dataset"></a>驗證資料集

`--validation-dataset | -v` (string)

指向驗證資料集檔案的檔案路徑。 在任何情況下，驗證資料集都是選擇性的。

如果使用 `validation dataset`，行為應該如下：

- 也需要 `test-dataset` 和 `--dataset` 引數。

- `validation-dataset` 資料集是用於評估模型選取的預測誤差。

- `test-dataset` 資料集是用於評定最終選擇模型的概括誤差。 在理想情況下，測試集應該保留在「保存庫」中，且只會在資料分析結束時提出。

基本上，使用 `validation dataset` 加上 `test dataset` 時，驗證階段可分成兩個部分：

1. 在第一個部分中，您只會使用驗證資料來查看模型並選取表現最佳的方法 (=驗證)
2. 然後，您會評估所選方法的準確度 (=測試)。

因此，資料可分成 80/10/10 或 75/15/10。 例如：

- `training-dataset` 檔案應該有 75% 的資料。
- `validation-dataset` 檔案應該有 15% 的資料。
- `test-dataset` 檔案應該有 10% 的資料。

在任何情況下，這些百分比都會由提供已分割檔案的使用者使用 CLI 來決定。

## <a name="label-column"></a>標籤資料行

`--label-col`（int 或 string）

使用這個引數時，您可以使用資料集標頭中所設定的資料行名稱或資料集檔案中的資料行數值索引（從0開始），來指定特定目標/目標資料行（您想要預測的變數）。

這個引數會用於*分類*和*回歸*問題。

## <a name="item-column"></a>專案資料行

`--item-col`（int 或 string）

[專案] 資料行具有 [使用者] 速率的專案清單（建議使用者使用專案）。 您可以使用資料集標頭中所設定的資料行名稱，或是資料集檔案中的資料行數值索引來指定這個資料行（資料行索引值是從0開始）。

這個引數僅用於*建議*工作。

## <a name="rating-column"></a>評等資料行

`--rating-col`（int 或 string）

[評等] 資料行具有使用者所提供專案的評等清單。 您可以使用資料集標頭中所設定的資料行名稱，或是資料集檔案中的資料行數值索引來指定這個資料行（資料行索引值是從0開始）。

這個引數僅用於*建議*工作。

## <a name="user-column"></a>使用者資料行

`--user-col`（int 或 string）

[使用者] 資料行有使用者的清單，可提供專案的評等。 您可以使用資料集標頭中所設定的資料行名稱，或是資料集檔案中的資料行數值索引來指定這個資料行（資料行索引值是從0開始）。

這個引數僅用於*建議*工作。

## <a name="ignore-columns"></a>略過資料行

`--ignore-columns` (string)

透過這個引數，您可以忽略資料集檔案中的現有資料行，讓定型程序不會載入和使用這些資料行。

指定您要忽略的資料行名稱。 使用 ', ' (逗號與空格) 或 ' ' (空格) 來分隔多個資料行名稱。 您可以使用引號來括住含有空格的資料行名稱 (例如 "logged in")。

範例：

`--ignore-columns email, address, id, logged_in`

## <a name="has-header"></a>具有標頭

`--has-header` (bool)

指定資料集檔案是否有標頭資料列。
可能的值包括：

- `true`
- `false`

如果使用者未指定這個引數，ML.NET CLI 會嘗試偵測此屬性。

## <a name="train-time"></a>定型時間

`--train-time` (string)

根據預設，探索/訓練時間上限為30分鐘。

這個引數為用於探索多個定型器和設定的程序，設定最大時間 (以秒為單位)。 如果為單一反覆運算所提供的時間太短 (例如 2 秒)，則可能會超過設定的時間。 在此情況下，實際時間是在單一反覆運算中產生一個模型設定所需的時間。

反覆運算所需的時間可能會因資料集大小而有所不同。

## <a name="cache"></a>快取

`--cache` (string)

如果您使用快取，則會將整個定型資料集載入記憶體。

若是小型和中型資料集，使用快取可大幅提升定型效能，這表示定型時間可能會比不使用快取更短。

不過，若是大型資料集，將所有資料載入記憶體可能會造成負面影響，因為記憶體可能會不足。 以大型資料集檔案定型而不使用快取時，ML.NET 會在需要載入更多資料進行定型時從磁碟機串流資料區塊。

您可以指定下列值：

`on`：強制在定型時使用快取。
`off`：在定型時強制不使用快取。
`auto`：視 AutoML 啟發學習法而定，將會使用快取。 通常，如果您使用 `auto` 選項，則小型/中型資料集會使用快取，而大型資料集不會使用快取。

如果您沒有指定 `--cache` 參數，則預設會使用 `auto` 快取設定。

## <a name="name"></a>名稱

`--name` (string)

所建立輸出專案或方案的名稱。 如果未指定名稱，則會使用名稱 `sample-{mltask}`。

ML.NET 模型檔案 (.ZIP 檔案) 也會有相同的名稱。

## <a name="output-path"></a>輸出路徑

`--output-path | -o` (string)

放置所產生輸出的根位置/資料集。 預設值是目前的目錄。

## <a name="verbosity"></a>詳細程度

`--verbosity | -v` (string)

設定標準輸出的詳細資訊層級。

允許的值包括：

- `q[uiet]`
- `m[inimal]` (預設)
- `diag[nostic]` (記錄資訊層級)

根據預設，CLI 工具應該會在工作時顯示一些最小的意見反應（ `minimal` ），例如，它正在運作，以及可能會有多少時間或已完成的時間。

## <a name="help"></a>[說明]

`-h |--help`

印出命令的說明，以及每個命令的參數描述。

## <a name="see-also"></a>另請參閱

- [如何安裝 ML.NET CLI 工具](../how-to-guides/install-ml-net-cli.md)
- [ML.NET CLI 的總覽](../automate-training-with-cli.md)
- [教學課程：使用 ML.NET CLI 來分析情感](../tutorials/sentiment-analysis-cli.md)
- [ML.NET CLI 中的遙測](../resources/ml-net-cli-telemetry.md)
