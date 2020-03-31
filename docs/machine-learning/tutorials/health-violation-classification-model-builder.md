---
title: 教學:使用模型產生器對執行狀況違規進行分類
description: 本教程演示如何使用ML.NET模型生成器構建多類分類模型,對三藩市的餐廳健康違規嚴重性進行分類。
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.topic: tutorial
ms.custom: mvc,mlnet-tooling
ms.openlocfilehash: 6a36989f9453208e436ef8a4db2d4440aa0a1382
ms.sourcegitcommit: 2ff49dcf9ddf107d139b4055534681052febad62
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/31/2020
ms.locfileid: "80438194"
---
# <a name="tutorial-classify-the-severity-of-restaurant-health-violations-with-model-builder"></a>教程:使用模型生成器對餐廳健康違規的嚴重程度進行分類

瞭解如何使用模型生成器構建多類分類模型,以對運行狀況檢查中發現的餐館違規行為的風險級別進行分類。

在本教學課程中，您會了解如何：

> [!div class="checklist"]
>
> - 準備並了解資料
> - 選擇案例
> - 從資料庫載入資料
> - 將模型定型
> - 評估模型
> - 使用模型來進行預測

> [!NOTE]
> 模型產生器目前為預覽版。

## <a name="prerequisites"></a>Prerequisites

有關先決條件和安裝說明的清單,請造[訪模型產生器安裝指南](../how-to-guides/install-model-builder.md)。

## <a name="model-builder-multiclass-classification-overview"></a>模型產生器多類別概述

此示例創建一個 C# .NET Core 主控台應用程式,該應用程式使用使用模型生成器建構的機器學習模型對運行狀況衝突的風險進行分類。 您可以在[dotnet/機器學習範例](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations)GitHub 儲存庫中找到本教學的原始程式碼。

## <a name="create-a-console-application"></a>建立主控台應用程式

1. 建立名為「餐廳違規」的**C# .NET 核心主控台應用程式**。 確保**未選取****同一目錄中的放置解決方案和專案**(VS 2019),或**選中****「創建解決方案目錄**」(VS 2017)。

## <a name="prepare-and-understand-the-data"></a>準備並了解資料

> 用於培訓和評估機器學習模型的數據集最初來自[三藩市公共衛生部餐廳安全評分](https://www.sfdph.org/dph/EH/Food/score/default.asp)。 為方便起見,數據集已壓縮為僅包括與訓練模型和進行預測相關的列。 請造訪以下網站,瞭解有關[資料集](https://data.sfgov.org/Health-and-Social-Services/Restaurant-Scores-LIVES-Standard/pyih-qa8i?row_index=0)的資訊。

[下載餐廳安全分數數據集](https://github.com/luisquintanilla/machinelearning-samples/raw/AB1608219/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantScores.zip)並解壓縮。

數據集中的每一行都包含有關在衛生部檢查期間觀察到的違規行為的資訊,以及對這些違規行為對公眾健康和安全構成的威脅的風險評估。

| 偵測類型 | 違規描述 | 風險類別 |
| --- | --- | --- |
| 例程 ─ 排程 | 未充分清潔或消毒食品接觸表面 | 中等風險 |
| 新擁有權 | 高風險害蟲侵擾 | 高風險 |
| 例程 ─ 排程 | 擦拭未清潔或未正確存放或消毒器不足的布 | 低風險 |

- **檢驗類型**:檢驗類型。 這可以是新機構的首次檢查、例行檢查、投訴檢查和許多其他類型。
- **違規說明**:檢查中發現的違規行為的描述。
- **風險類別**:違規行為對公眾健康和安全構成的風險嚴重性。

`label` 是您希望進行預測的資料行。 執行分類任務時,目標是分配類別(文本或數位)。 在此分類方案中,將指定衝突的嚴重性為低、中或高風險的值。 因此,**風險類別**是標籤。 是`features`您為模型提供用於預測`label`的輸入。 在這種情況下,**檢查類型**和**違規描述**用作用於預測**風險類別**的功能或輸入。

## <a name="choose-a-scenario"></a>選擇案例

![視覺化工作室中的模型產生器精靈](./media/sentiment-analysis-model-builder/model-builder-screen.png)

要訓練模型,請從模型生成器提供的可用機器學習方案清單中選擇。 在這種情況下,方案是*問題分類*。

1. 在**解決方案資源管理器中**,右鍵按*下 「餐廳違規」* 項目,然後選擇「**添加** > **機器學習**」。
1. 對於此示例,方案是多類分類。 在模型生成器*的方案*步驟中,選擇**問題分類**方案。

## <a name="load-the-data"></a>載入資料

模型生成器接受來自 SQL Server 資料庫或`csv`本地`tsv`檔案的數據, 其格式或格式。

1. 在模型生成器工具的資料步驟中,從資料源下拉清單中選擇**SQL Server。**
1. 選擇"連接到 SQL **Server 資料庫"文字**框旁邊的按鈕。
    1. 在**選擇資料「** 對話框中,選擇**Microsoft SQL 伺服器資料庫檔案**。
    1. 取消選中 **「始終使用此選擇**」複選框,然後選擇"**繼續**"。
    1. 在 **'連接屬性**'對話框中,選擇 **'瀏覽**』並選擇下載的*餐館分數.mdf*檔案。
    1. 選取 [確定]  。
1. 從**表格名稱**下拉清單中選擇 **「衝突**」。
1. 在「列」中選擇 **「風險類別****」以預測(標籤)** 下拉清單。
1. 輸入**欄(功能)** 下拉下下下下下,保留預設欄選擇、**檢查類型**與**違規描述**。
1. 選擇 **「訓練」** 連結以移動到模型生成器中的下一步。

## <a name="train-the-model"></a>將模型定型

本教學中用於訓練問題分類模型的機器學習任務是多類分類。 在模型培訓過程中,模型生成器使用不同的多類分類演演演算法和設置訓練單獨的模型,以查找數據集的最佳模型。

模型訓練所需的時間與數據量成正比。 模型生成器根據資料來源的大小自動選擇**時間訓練時間(秒)** 的預設值。

1. 儘管模型生成器將**訓練時間(秒)** 的值設置為 10 秒,但將其增加到 30 秒。 經過更長時間的培訓,模型構建器可以探索更多演演演算法和參數組合,以查找最佳模型。
1. 選取 [開始定型]****。

    在整個定型程序期間，進度資料會顯示在定型步驟的 `Progress` 區段中。

    - **狀態**顯示培訓過程的完成狀態。
    - **最佳精度** 顯示模型生成器迄今找到的最佳模型的準確性。 正確性越高，表示模型針對測試資料的預測越正確。
    - **最佳演算法** 顯示模型生成器迄今找到的表現最好的演演演算法的名稱。
    - **最後一個演算法** 顯示模型生成器最近用於訓練模型的演演演算法的名稱。

1. 培訓完成後,選擇 **「評估**」連結以轉到下一步。

## <a name="evaluate-the-model"></a>評估模型

訓練步驟的結果是性能最好的模型。 在模型生成器的計算步驟中,輸出部分包含**最佳模型**條目中性能最佳的模型使用的演演演算法以及**最佳模型精度**中的指標。 此外,還會顯示一個摘要表,其中包含最多五個已流覽的模型及其指標。

如果您對準確性指標不滿意,則嘗試提高模型準確性的一些簡單方法是增加訓練模型或使用更多數據的時間。 否則,選擇要移動到模型生成器中的最後一步**的代碼**連結。

## <a name="add-the-code-to-make-predictions"></a>新增程式碼來進行預測

培訓過程的結果創建了兩個專案。

- 餐廳違規ML.ConsoleApp:包含模型培訓和示例消耗代碼的C#.NET核心控制台應用程式。
- 餐廳違規ML.Model:一個.NET標準類庫,其中包含定義輸入和輸出模型數據架構的數據模型、培訓期間最佳性能模型的保存版本以及調用`ConsumeModel`用於進行預測的幫助器類。

1. 在模型生成器的代碼步驟中,選擇 **「添加專案」** 以將自動生成的專案添加到解決方案中。
1. 打開 *「餐廳違規」* 專案中*的 Program.cs*檔。
1. 新增以下使用敘述以引用*餐廳違規ML.模型*專案:

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L2)]

1. 要使用模型對新數據進行預測,請在應用程式`ModelInput``Main`的方法內創建類的新實例。 請注意,風險類別不是輸入的一部分。 這是因為模型為其生成預測。

    [!code-csharp [TestData](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L11-L15)]

1. 使用`Predict`類中`ConsumeModel`的方法。 該方法`Predict`載入訓練的模型,為模型[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)建立 。

    [!code-csharp [Prediction](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L17-L24)]

1. 執行應用程式。

    程式所產生的輸出看起來應該會和以下程式碼片段相似：

    ```bash
    Inspection Type: Complaint
    Violation Description: Inadequate sewage or wastewater disposal
    Risk Category: Moderate Risk
    ```

若您需要於稍後在另外一個解決方案中參考所產生的專案，您可以在 `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` 目錄中找到它們。

恭喜！ 您已成功建構機器學習模型,以便使用模型生成器對健康違規的風險進行分類。 您可以在[dotnet/機器學習範例](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations)GitHub 儲存庫中找到本教學的原始程式碼。

## <a name="additional-resources"></a>其他資源

若要深入了解此教學課程中提及的主題，請瀏覽下列資源：

- [模型建立器案例](../automate-training-with-model-builder.md#scenario)
- [多類類別](../resources/glossary.md#multiclass-classification)
- [多類類別模型指標](../resources/metrics.md#evaluation-metrics-for-multi-class-classification)
