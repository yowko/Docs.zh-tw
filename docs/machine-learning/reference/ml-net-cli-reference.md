---
title: ML.NET CLI 工具中的 auto-train 命令
description: ML.NET CLI 工具中的 auto-train 命令概觀、範例和參考。
ms.date: 04/16/2019
ms.custom: ''
ms.openlocfilehash: 73bae0165af76226152de322d2951086646a1a1d
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2019
ms.locfileid: "67397667"
---
# <a name="the-auto-train-command-in-mlnet-cli"></a>ML.NET CLI 中的 'auto-train' 命令

> [!NOTE]
> 本主題參考 ML.NET CLI 和 ML.NET AutoML，它們目前為公開預覽版，因此内容可能會有變更。

`auto-train` 命令是 ML.NET CLI 工具所提供的主要命令。 該命令可讓您產生高品質的 ML.NET 模型 (序列化模型 .zip 檔案)，加上執行/評分該模型的範例 C# 程式碼。 此外，也會產生建立/定型該模型的 C# 程式碼，讓您調查其使用哪些演算法和設定來產生「最佳模型」。

您可以從自己的資料集產生這些資產，不用自行撰寫程式碼，因此即使您已熟悉 ML.NET 也能提升生產力。

ML.NET CLI 目前支援的 ML 工作如下：

- `binary-classification`
- `multiclass-classification`
- `regression`

- 未來：其他機器學習工作，例如
  - `recommendation`
  - `anomaly-detection`
  - `clustering`

命令提示字元的使用範例：

```console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name price
```

`mlnet auto-train` 命令會產生下列資產：

- 隨時可用的序列化模型 .zip (「最佳模型」)。
- C# 程式碼，執行/評分產生的模型 (使用該模型以您的終端使用者應用程式建立預測)。
- C# 程式碼和定型程式碼，用來產生該模型 (適用於學習目的)。

前兩項資產可以直接用於終端使用者應用程式 (ASP.NET Core Web 應用程式、服務、傳統型應用程式等)，使用產生的 ML 模型建立預測。

第三項資產，即定型程式碼，會向您顯示 CLI 已使用哪些 ML.NET API 程式碼來定型產生的模型，讓您可以調查 CLI 和 ML.NET AutoML 引擎選取了哪些特定定型器/演算法和超參數。

## <a name="the-auto-train-command-uses-the-automl-engine"></a>'auto-train' 命令使用 AutoML 引擎

CLI 使用 ML.NET AutoML 引擎 (NuGet 套件) 以智慧方式來搜尋最佳品質的模型，如下圖所示：

![圖](./media/ml-net-automl-working-diagram.png "在 ML.NET CLI 內工作的 AutoML 引擎")

使用 'auto-train' 命令執行 ML.NET CLI 工具時，您會看到此工具使用不同演算法和不同組合的設定來嘗試多個反覆運算。

## <a name="reference-for-auto-train-command"></a>'auto-train' 命令參考

## <a name="examples"></a>範例

適用於二元分類問題的最簡單 CLI 命令 (AutoML 必須從提供的資料推斷大部分設定)：

```console
> mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

適用於迴歸問題的另一個簡單 CLI 命令：

``` console
> mlnet auto-train --task regression --dataset "cars.csv" --label-column-name Price
```

使用定型資料集、測試資料集和進一步自訂的明確引數，來建立並定型二元分類模型：

```console
> mlnet auto-train --task binary-classification --dataset "/MyDataSets/Population-Training.csv" --test-dataset "/MyDataSets/Population-Test.csv" --label-column-name "InsuranceRisk" --cache on --max-exploration-time 600
```

## <a name="name"></a>名稱

`mlnet auto-train` - 根據所提供的資料集定型多個模型 ('n' 個反覆運算)，最後選取最佳模型、將它儲存為序列化的 .zip 檔案，並產生用於評分和定型的相關 C# 程式碼。

## <a name="synopsis"></a>概要

```console
> mlnet auto-train

--task | --mltask | -T <value>

--dataset | -d <value>

[
 [--validation-dataset | -v <value>]
  --test-dataset | -t <value>
]

--label-column-name | -n <value>
|
--label-column-index | -i <value>

[--ignore-columns | -I <value>]

[--has-header | -h <value>]

[--max-exploration-time | -x <value>]

[--verbosity | -V <value>]

[--cache | -c <value>]

[--name | -N <value>]

[--output-path | -o <value>]

[--help | -h]

```

無效輸入選項應該會導致 CLI 工具發出有效的輸入清單，以及說明哪些引數遺漏 (若發生此情況) 的錯誤訊息。

## <a name="options"></a>選項

 ----------------------------------------------------------

`--task | --mltask | -T` (string)

單一字串，提供所要解決的 ML 問題。 例如，下列任何工作 (CLI 最終會支援 AutoML 中支援的所有工作)：

- `regression` - 如果使用 ML 模型來預測數值，則選擇此選項
- `binary-classification` - 如果 ML 模型結果有兩個可能的類別布林值 (0 或 1)，則選擇此選項。
- `multiclass-classification` - 如果 ML 模型結果有多個可能的類別值，則選擇此選項。

在未來版本中，將支援其他 ML 工作和案例，例如 `recommendations`、`clustering` 和 `ranking`。

 在這個引數中只應提供一個 ML 工作。

 ----------------------------------------------------------

`--dataset | -d` (string)

這個引數提供下列任一選項的檔案路徑：

- *A：整個資料集檔案：* 如果使用這個選項且使用者沒有提供 `--test-dataset` 和 `--validation-dataset`，則會在內部使用交叉驗證 (k-fold 等) 或自動資料分割方法來驗證模型。 在此情況下，使用者只需提供資料集檔案路徑。

- *B：定型資料集檔案：* 如果使用者同時提供用於模型驗證的資料集 (使用 `--test-dataset` 和選擇性 `--validation-dataset`)，則 `--dataset` 引數表示只會有「定型資料集」。 例如，使用 80% - 20% 方法來驗證模型的品質並取得準確度計量時，「定型資料集」會有 80% 的資料，而「測試資料集」會有 20% 的資料。

----------------------------------------------------------

`--test-dataset | -t` (string)

指向測試資料集檔案的檔案路徑，例如使用 80% - 20% 方法進行一般驗證來取得準確度計量時。

如果使用 `--test-dataset`，則也需要 `--dataset`。

除非使用 --validation-dataset，否則 `--test-dataset` 引數是選擇性的。 在此情況下，使用者必須使用三個引數。

----------------------------------------------------------

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

----------------------------------------------------------

`--label-column-name | -n` (string)

透過這個引數，您可以藉由使用資料集標頭中所設定的資料行名稱，來指定特定目標/目的資料行 (您想要預測的變數)。

這個引數只能用於受監督的 ML 工作，例如「分類問題」  。 不能用於不受監督的 ML 工作，例如「叢集」  。

----------------------------------------------------------

`--label-column-index | -i` (int)

透過這個引數，您可以藉由使用資料集檔案中的資料行數值索引 (資料行索引值以 1 起始)，來指定特定目標/目的資料行 (您想要預測的變數)。

*注意：* 如果使用者同時使用 `--label-column-name`，則會使用 `--label-column-name`。

這個引數只能用於受監督的 ML 工作，例如「分類問題」  。 不能用於不受監督的 ML 工作，例如「叢集」  。

----------------------------------------------------------

`--ignore-columns | -I` (string)

透過這個引數，您可以忽略資料集檔案中的現有資料行，讓定型程序不會載入和使用這些資料行。

指定您要忽略的資料行名稱。 使用 ', ' (逗號與空格) 或 ' ' (空格) 來分隔多個資料行名稱。 您可以使用引號來括住含有空格的資料行名稱 (例如 "logged in")。

範例：

`--ignore-columns email, address, id, logged_in`

----------------------------------------------------------

`--has-header | -h` (bool)

指定資料集檔案是否有標頭資料列。
可能的值為：
- `true`
- `false`

如果使用者未指定這個引數，預設值為 `true`。

為了使用 `--label-column-name` 引數，您的資料集檔案中必須有標頭，且您必須將 `--has-header` 設定為 `true` (預設值)。

----------------------------------------------------------

`--max-exploration-time | -x` (string)

根據預設，最大探索時間為 30 分鐘

這個引數為用於探索多個定型器和設定的程序，設定最大時間 (以秒為單位)。 如果為單一反覆運算所提供的時間太短 (例如 2 秒)，則可能會超過設定的時間。 在此情況下，實際時間是在單一反覆運算中產生一個模型設定所需的時間。

反覆運算所需的時間可能會因資料集大小而有所不同。

----------------------------------------------------------

`--cache | -c` (string)

如果您使用快取，則會將整個定型資料集載入記憶體。

若是小型和中型資料集，使用快取可大幅提升定型效能，這表示定型時間可能會比不使用快取更短。

不過，若是大型資料集，將所有資料載入記憶體可能會造成負面影響，因為記憶體可能會不足。 以大型資料集檔案定型而不使用快取時，ML.NET 會在需要載入更多資料進行定型時從磁碟機串流資料區塊。

您可以指定下列值：

`on`：強制在定型時使用快取。
`off`：強制在定型時不使用快取。
`auto`：快取使用與否會視 AutoML 啟發學習法而定。 通常，如果您使用 `auto` 選項，則小型/中型資料集會使用快取，而大型資料集不會使用快取。

如果您沒有指定 `--cache` 參數，則預設會使用 `auto` 快取設定。

----------------------------------------------------------

`--name | -N` (string)

所建立輸出專案或方案的名稱。 如果未指定名稱，則會使用名稱 `sample-{mltask}`。

ML.NET 模型檔案 (.ZIP 檔案) 也會有相同的名稱。

----------------------------------------------------------

`--output-path | -o` (string)

放置所產生輸出的根位置/資料集。 預設為目前的目錄。

----------------------------------------------------------

`--verbosity | -V` (string)

設定標準輸出的詳細資訊層級。

允許的值如下：

- `q[uiet]`
- `m[inimal]` (預設)
- `diag[nostic]` (記錄資訊層級)

根據預設，CLI 工具在運作時應該至少會顯示一些基本回饋，例如提及它正在運作，以及剩餘時間或完成的時間百分比 (如果可能)。

----------------------------------------------------------

`-h|--help`

印出命令的說明，以及每個命令的參數描述。

----------------------------------------------------------

## <a name="see-also"></a>另請參閱

- [如何安裝 ML.NET CLI 工具](../how-to-guides/install-ml-net-cli.md)
- [使用 ML.NET CLI 自動化模型定型](../automate-training-with-cli.md)
- [教學課程：使用 ML.NET CLI 自動產生二元分類器](../tutorials/mlnet-cli.md)
- [ML.NET CLI 中的遙測](../resources/ml-net-cli-telemetry.md)
