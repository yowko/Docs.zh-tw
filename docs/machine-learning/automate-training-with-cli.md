---
title: 使用 ML.NET CLI 自動化模型定型
description: 探索如何使用 ML.NET CLI 工具，從命令列自動定型最佳模型。
ms.date: 12/17/2019
ms.custom: how-to, mlnet-tooling
ms.openlocfilehash: 3344ed15266503d4d5c7cd9db0a0596f58a904fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185888"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a>使用 ML.NET CLI 自動化模型定型

ML.NET CLI 可自動為 .NET 開發人員生成模型。

若要使用 ML.NET API 本身 (不利用 ML.NET AutoML CLI)，您需要選擇定型器 (實作特定工作的機器學習演算法) 以及要套用至資料的一組資料轉換 (特徵工程)。 每個資料集的最佳管道各有不同，而從所有的選項中選取最佳演算法會增加複雜性。 更進一步，每個演算法都有一組要微調的超參數。 因此，您可以花費數週或數月來最佳化機器學習模型，嘗試尋找特徵工程、學習演算法和超參數的最佳組合。

ML.NET CLI 使用自動機器學習 （AutoML） 簡化了此過程。

> [!NOTE]
> 本主題是指當前處於預覽版中的ML.NET **CLI**和 ML.NET **AutoML，** 材料可能會有所更改。

## <a name="what-is-the-mlnet-command-line-interface-cli"></a>什麼是ML.NET命令列介面 （CLI）？

cLIML.NET是[.NET 核心工具](../core/tools/global-tools.md)。 安裝後，您將給它一個機器學習任務和培訓資料集，並生成一個ML.NET模型，以及運行以在應用程式中使用模型的 C# 代碼。

如下圖所示，生成高品質ML.NET模型（序列化模型 .ZIP 檔案）加上示例 C# 代碼以運行/評分該模型非常簡單。 此外，也產生建立/定型模型的 C# 程式碼，以便您可以研究並重覆所產生「最佳模型」使用的演算法和設定。

![圖像](media/automate-training-with-cli/cli-high-level-process.png "自動ML發動機在ML.NET CLI 內工作")

您可以從自己的資料集產生這些資產，不用自行撰寫程式碼，因此即使您已熟悉 ML.NET，也能提升生產力。

ML.NET CLI 目前支援的 ML 工作如下：

- `binary-classification`
- `multiclass-classification`
- `regression`
- 未來：其他機器學習工作，例如 `recommendation`、`ranking`、`anomaly-detection`、`clustering`

使用範例：

```console
mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

![image](media/automate-training-with-cli/cli-model-generation.gif)

您可以用在 *Windows PowerShell*、*macOS/Linux bash 或 *Windows CMD* 執行的方式執行它。 不過，表格式自動完成 (參數建議) 不適用於 *Windows CMD*。

## <a name="output-assets-generated"></a>產生的輸出資產

CLI `auto-train` 命令會在輸出資料夾中產生下列資產：

- 序列化模型 .zip (「最佳模型」) 準備好用於執行預測。
- C# 解決方案具有：
  - C# 程式碼，執行/評分產生的模型 (使用該模型以您的終端使用者應用程式建立預測)。
  - C# 程式碼和定型程式碼，用來產生該模型 (適用於學習目的或重新定型模型)。
- 記錄檔，具有多個已評估之演算法所有反覆項目/清除的資訊，包括其詳細的組態/管線。

前兩項資產可以直接用於終端使用者應用程式 (ASP.NET Core Web 應用程式、服務、桌面應用程式等)，使用已產生的 ML 模型建立預測。

第三項資產，即定型程式碼，會向您顯示 CLI 已使用哪些 ML.NET API 程式碼來定型產生的模型，讓您可以重新定型模型，以及調查和逐一查看 CLI 和 AutoML 在幕後選取了哪些特定的定型器/演算法和超參數。

## <a name="understanding-the-quality-of-the-model"></a>了解模型的品質

當您使用 CLI 工具生成"最佳模型"時，您將看到針對要定位的 ML 任務所需的品質指標（如準確性和 R-平方度）。

在這裡，這些指標按 ML 任務進行分組，以便您可以瞭解自動生成的"最佳模型"的品質。

### <a name="metrics-for-binary-classification-models"></a>二元分類模型的計量

下列顯示 CLI 找到之前五個模型的二元分類 ML 工作計量清單：

![image](media/automate-training-with-cli/cli-binary-classification-metrics.png)

準確性是分類問題的熱門指標，但準確性並不總是從以下引用中解釋的最佳指標來選擇最佳模型。 在某些情況下，您需要評估模型品質和其他計量。

要探索和瞭解由 CLI 輸出的指標，請參閱[二進位分類的評估指標](resources/metrics.md#evaluation-metrics-for-binary-classification)。

### <a name="metrics-for-multi-class-classification-models"></a>多元分類模型的計量

下列顯示 CLI 找到之前五個模型的多元分類 ML 工作計量清單：

![image](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

要流覽和瞭解由 CLI 輸出的指標，請參閱[多類分類的評估指標](resources/metrics.md#evaluation-metrics-for-multi-class-classification)。

### <a name="metrics-for-regression-and-recommendation-models"></a>回歸和推薦模型的指標

如果觀察到的值和模型預測值之間差異很小且非偏誤，則迴歸模型非常適合這種資料。 可以使用特定計量評估迴歸。

您將看到 CLI 找到的最佳五大品質模型的類似指標清單。 在這個特例中與迴歸 ML 工作相關：

![image](media/automate-training-with-cli/cli-regression-metrics.png)

要流覽和瞭解 CLI 輸出的指標，請參閱[回歸的評估指標](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation)。

## <a name="see-also"></a>另請參閱

- [如何安裝 ML.NET CLI 工具](how-to-guides/install-ml-net-cli.md)
- [教程：使用 cLI ML.NET分析情緒](tutorials/sentiment-analysis-cli.md)
- [ML.NET CLI 命令參考](reference/ml-net-cli-reference.md)
- [ML.NET CLI 中的遙測](resources/ml-net-cli-telemetry.md)
