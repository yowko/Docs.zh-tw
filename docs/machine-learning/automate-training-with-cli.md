---
title: 使用 ML.NET CLI 自動化模型定型
description: 探索如何使用 ML.NET CLI 工具，從命令列自動定型最佳模型。
author: CESARDELATORRE
ms.date: 04/17/2019
ms.custom: how-to
ms.openlocfilehash: e5f75dc70ea5a76951d8698ea9c0d07cb2d4ddec
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663930"
---
# <a name="automate-model-training-with-the-mlnet-cli"></a>使用 ML.NET CLI 自動化模型定型

ML.NET CLI 在學習 ML.NET 時，向 .NET 開發人員「推廣」ML.NET。

若要使用 ML.NET API 本身 (不利用 ML.NET AutoML CLI)，您需要選擇定型器 (實作特定工作的機器學習演算法) 以及要套用至資料的一組資料轉換 (特徵工程)。 每個資料集的最佳管道各有不同，而從所有的選項中選取最佳演算法會增加複雜性。 更進一步，每個演算法都有一組要微調的超參數。 因此，您可以花費數週或數月來最佳化機器學習模型，嘗試尋找特徵工程、學習演算法和超參數的最佳組合。

此程序可使用 ML.NET CLI 自動化，這會實作 ML.NET AutoML 的智慧引擎。

> [!NOTE]
> 本主題參考 ML.NET **CLI** 和 ML.NET **AutoML**，它們目前為公開預覽版，因此内容可能會有變更。

## <a name="what-is-the-mlnet-command-line-interface-cli"></a>什麼是 ML.NET 命令列介面 (CLI)？

您可以在任何命令提示字元 (Windows、Mac 或 Linux) 中執行 ML.NET CLI，根據您的定型資料集產生高品質的 ML.NET 模型和原始程式碼。

如下圖所示，產生高品質的 ML.NET 模型 (序列化模型 .zip 檔案) 加上執行/評分數模型的範例 C# 程式碼很容易。 此外，也產生建立/定型模型的 C# 程式碼，以便您可以研究並重覆所產生「最佳模型」使用的演算法和設定。

![圖](media/automate-training-with-cli/cli-high-level-process.png "在 ML.NET CLI 內工作的 AutoML 引擎")

您可以從自己的資料集產生這些資產，不用自行撰寫程式碼，因此即使您已熟悉 ML.NET，也能提升生產力。

ML.NET CLI 目前支援的 ML 工作如下：

- `binary-classification`
- `multiclass-classification`
- `regression`
- 未來：其他機器學習工作，例如 `recommendation`、`ranking`、`anomaly-detection`、`clustering`

使用範例：

```console
> mlnet auto-train --task binary-classification --dataset "customer-feedback.tsv" --label-column-name Sentiment
```

![影像](media/automate-training-with-cli/cli-model-generation.gif)

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

當您使用 CLI 工具產生「最佳模型」後，您會看到適合您目標 ML 工作的品質計量 (例如精確度和 R 平方)。

在此摘要依 ML 工作分組的計量，以便您了解自動產生的「最佳模型」品質。

### <a name="metrics-for-binary-classification-models"></a>二元分類模型的計量

下列顯示 CLI 找到之前五個模型的二元分類 ML 工作計量清單：

![影像](media/automate-training-with-cli/cli-binary-classification-metrics.png)

精確度是分類問題的最熱門計量，但如以下參考所述，精確度不一定一律是選取最佳模型的最佳計量。 在某些情況下，您需要評估模型品質和其他計量。

若要探索及了解 CLI 輸出的計量，請參閱[二元分類計量](resources/metrics.md#metrics-for-binary-classification)。

### <a name="metrics-for-multi-class-classification-models"></a>多元分類模型的計量

下列顯示 CLI 找到之前五個模型的多元分類 ML 工作計量清單：

![影像](media/automate-training-with-cli/cli-multiclass-classification-metrics.png)

若要探索及了解 CLI 輸出的計量，請參閱[多元分類計量](resources/metrics.md#metrics-for-multi-class-classification)。

### <a name="metrics-for-regression-models"></a>迴歸模型的計量

如果觀察到的值和模型預測值之間差異很小且非偏誤，則迴歸模型非常適合這種資料。 可以使用特定計量評估迴歸。

您會看到類似最佳 CLI 找到之前五個品質最佳模型的計量清單。 在這個特例中與迴歸 ML 工作相關：

![影像](media/automate-training-with-cli/cli-regression-metrics.png)

若要探索及了解 CLI 輸出的計量，請參閱[廻歸計量](resources/metrics.md#metrics-for-regression)。

## <a name="see-also"></a>另請參閱

- [如何安裝 ML.NET CLI 工具](how-to-guides/install-ml-net-cli.md)
- [教學課程：使用 ML.NET CLI 自動產生二元分類器](tutorials/mlnet-cli.md)
- [ML.NET CLI 命令參考](reference/ml-net-cli-reference.md)
- [ML.NET CLI 中的遙測](resources/ml-net-cli-telemetry.md)
