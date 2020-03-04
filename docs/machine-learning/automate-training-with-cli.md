---
title: 使用 ML.NET CLI 自動化模型定型
description: 探索如何使用 ML.NET CLI 工具，從命令列自動定型最佳模型。
ms.date: 12/17/2019
ms.custom: how-to
ms.openlocfilehash: 9c493b1df0dd326ad2f0a5d1cac0fc11d7cf37e2
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240619"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a>使用 ML.NET CLI 自動化模型定型

ML.NET CLI 會自動產生適用于 .NET 開發人員的模型。

若要使用 ML.NET API 本身 (不利用 ML.NET AutoML CLI)，您需要選擇定型器 (實作特定工作的機器學習演算法) 以及要套用至資料的一組資料轉換 (特徵工程)。 每個資料集的最佳管道各有不同，而從所有的選項中選取最佳演算法會增加複雜性。 更進一步，每個演算法都有一組要微調的超參數。 因此，您可以花費數週或數月來最佳化機器學習模型，嘗試尋找特徵工程、學習演算法和超參數的最佳組合。

ML.NET CLI 會使用自動化機器學習（AutoML）來簡化此程式。 

> [!NOTE]
> 本主題參考 ML.NET **CLI** 和 ML.NET **AutoML**，它們目前為公開預覽版，因此内容可能會有變更。

## <a name="what-is-the-mlnet-command-line-interface-cli"></a>什麼是 ML.NET 命令列介面（CLI）？

ML.NET CLI 是一種[.Net Core 工具](../core/tools/global-tools.md)。 安裝之後，您可以為它提供機器學習工作和訓練資料集，並產生 ML.NET 模型，以及要在應用程式C#中使用模型所執行的程式碼。

如下圖所示，您可以輕鬆地產生高品質的 ML.NET 模型（序列化模型 .zip 檔案），再加上執行/ C#評分該模型的範例程式碼。 此外，也產生建立/定型模型的 C# 程式碼，以便您可以研究並重覆所產生「最佳模型」使用的演算法和設定。

![image](media/automate-training-with-cli/cli-high-level-process.png "在 ML.NET CLI 內運作的 AutoML 引擎")

您可以從自己的資料集產生這些資產，不用自行撰寫程式碼，因此即使您已熟悉 ML.NET 也能提升生產力。

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

前兩項資產可以直接用於終端使用者應用程式 (ASP.NET Core Web 應用程式、服務、傳統型應用程式等)，使用產生的 ML 模型建立預測。

第三項資產，即定型程式碼，會向您顯示 CLI 已使用哪些 ML.NET API 程式碼來定型產生的模型，讓您可以重新定型模型，以及調查和逐一查看 CLI 和 AutoML 在幕後選取了哪些特定的定型器/演算法和超參數。

## <a name="understanding-the-quality-of-the-model"></a>了解模型的品質

當您使用 CLI 工具產生「最佳模型」時，您會看到適用于您的目標 ML 工作的品質度量（例如精確度和右平方）。

這裡的計量是依 ML 工作分組，因此您可以瞭解自動產生的「最佳模型」的品質。

### <a name="metrics-for-binary-classification-models"></a>二元分類模型的計量

下列顯示 CLI 找到之前五個模型的二元分類 ML 工作計量清單：

![image](media/automate-training-with-cli/cli-binary-classification-metrics.png)

精確度是分類問題的熱門計量，不過，精確度不一定是最佳的計量，可以從中選取最佳的模型，如下列參考中所述。 在某些情況下，您需要評估模型品質和其他計量。

若要探索及瞭解 CLI 所輸出的計量，請參閱[二元分類的評估度量](resources/metrics.md#evaluation-metrics-for-binary-classification)。

### <a name="metrics-for-multi-class-classification-models"></a>多元分類模型的計量

下列顯示 CLI 找到之前五個模型的多元分類 ML 工作計量清單：

![image](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

若要探索及瞭解 CLI 所輸出的計量，請參閱[多元分類的評估度量](resources/metrics.md#evaluation-metrics-for-multi-class-classification)。

### <a name="metrics-for-regression-and-recommendation-models"></a>回歸和建議模型的計量

如果觀察到的值和模型預測值之間差異很小且非偏誤，則迴歸模型非常適合這種資料。 可以使用特定計量評估迴歸。

您會看到一份類似的計量清單，適用于 CLI 找到的最佳前五個品質模型。 在這個特例中與迴歸 ML 工作相關：

![image](media/automate-training-with-cli/cli-regression-metrics.png)

若要探索及瞭解 CLI 所輸出的計量，請參閱[回歸的評估計量](resources/metrics.md#evaluation-metrics-for-regression-and-recommendation)。

## <a name="see-also"></a>另請參閱

- [如何安裝 ML.NET CLI 工具](how-to-guides/install-ml-net-cli.md)
- [教學課程：使用 ML.NET CLI 來分析情感](tutorials/sentiment-analysis-cli.md)
- [ML.NET CLI 命令參考](reference/ml-net-cli-reference.md)
- [ML.NET CLI 中的遙測](resources/ml-net-cli-telemetry.md)
