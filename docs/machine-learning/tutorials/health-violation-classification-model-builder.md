---
title: 教學課程：使用模型產生器分類健全狀況違規
description: 本教學課程說明如何使用 ML.NET 模型產生器來建立多元分類模型，以分類三藩市中的餐廳健康情況違規嚴重性。
author: luisquintanilla
ms.author: luquinta
ms.date: 10/30/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: cbe20183d317ac6fe39a937e1cfa8a5e3df81b74
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977214"
---
# <a name="tutorial-classify-the-severity-of-restaurant-health-violations-with-model-builder"></a>教學課程：使用模型產生器分類餐廳健康情況違規的嚴重性

瞭解如何使用模型產生器來建立多元分類模型，以將在健康情況檢查期間找到的餐廳違規風險層級分類。

在本教學課程中，您將了解如何：

> [!div class="checklist"]
>
> - 準備並了解資料
> - 選擇案例
> - 從資料庫載入資料
> - 將模型定型
> - 評估模型
> - 使用模型來進行預測

> [!NOTE]
> 模型建立器目前為預覽版。

## <a name="prerequisites"></a>必要條件

如需必要條件和安裝指示的清單，請造訪[模型產生器安裝指南](../how-to-guides/install-model-builder.md)。

## <a name="model-builder-multiclass-classification-overview"></a>模型產生器多元分類總覽

這個範例會建立C# .net Core 主控台應用程式，以使用以模型產生器建立的機器學習模型，將健康情況違規的風險分類。 您可以在[dotnet/machinelearning 範例](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations)GitHub 存放庫中找到本教學課程的原始程式碼。

## <a name="create-a-console-application"></a>建立主控台應用程式

1. 建立名為 "RestaurantViolations" 的 **C# .net Core 主控台應用程式**。

## <a name="prepare-and-understand-the-data"></a>準備並了解資料

> 用來定型和評估機器學習模型的資料集，原本是由[三藩市部門的公用健康餐廳安全分數所組成](https://www.sfdph.org/dph/EH/Food/score/default.asp)。 為了方便起見，資料集已壓縮成隻包含與定型模型和進行預測相關的資料行。 流覽下列網站以深入瞭解[資料集](https://data.sfgov.org/Health-and-Social-Services/Restaurant-Scores-LIVES-Standard/pyih-qa8i?row_index=0)。

[下載餐廳安全分數資料集](https://github.com/luisquintanilla/machinelearning-samples/raw/AB1608219/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantScores.zip)，並將它解壓縮。

Dataset 中的每個資料列都包含在健康情況部門進行檢查時所觀察到之違規的相關資訊，以及對公開健康狀態和安全性的違規威脅的風險評估。

| InspectionType | ViolationDescription | RiskCategory |
| --- | --- | --- |
| 例行排程 | 未充分清除或清理的食物連絡人表面 | 中度風險 |
| 新擁有權 | 高風險 vermin 感染 | 高風險 |
| 例行排程 | 抹除換喪服未清除或正確儲存或 sanitizer 不足 | 低風險 |

- **InspectionType**：檢查的類型。 這可以是新建立的第一次檢查，也就是例行的檢查、抱怨檢查，以及許多其他類型。
- **ViolationDescription**：在檢查期間找到之違規的描述。
- **RiskCategory**：違反的風險嚴重性會造成公用的健全狀況和安全。

`label` 是您希望進行預測的資料行。 執行分類工作時，目標是要指派分類（文字或數位）。 在此分類案例中，違規的嚴重性會指派為 [低]、[中] 或 [高] 風險的值。 因此， **RiskCategory**是標籤。 `features` 是您為模型提供預測 `label`的輸入。 在此情況下， **InspectionType**和**ViolationDescription**會當做功能或輸入來預測**RiskCategory**。

## <a name="choose-a-scenario"></a>選擇案例

![Visual Studio 中的模型產生器 wizard](./media/sentiment-analysis-model-builder/model-builder-screen.png)

若要定型您的模型，請從模型產生器所提供的可用機器學習服務案例清單中選取。 在此情況下，案例是「*問題分類*」。

1. 在**方案總管**中，以滑鼠右鍵按一下*RestaurantViolations*專案，然後選取 [**新增** > **Machine Learning**]。
1. 在此範例中，案例是多元分類。 在模型產生器的*情節*步驟中，選取 [**問題分類**] 案例。

## <a name="load-the-data"></a>載入資料

模型產生器會以 `csv` 或 `tsv` 格式，接受來自 SQL Server 資料庫或本機檔案的資料。

1. 在模型產生器工具的 [資料] 步驟中，從 [資料來源] 下拉式清單中選取 [ **SQL Server** ]。
1. 選取 [**連接到 SQL Server 資料庫**] 文字方塊旁的按鈕。
    1. 在 [**選擇資料**] 對話方塊中，選取 [ **Microsoft SQL Server 資料庫**檔案]。
    1. 取消核取 [**一律使用此選取專案**] 核取方塊，然後選取 [**繼續**]。
    1. 在 [**連接屬性**] 對話方塊中，選取 [**流覽]** ，然後選取已下載的*RestaurantScores .mdf*檔案。
    1. 選取 [確定]。
1. 從 [**資料表名稱**] 下拉式清單中選擇 [**違規**]。
1. 在 [**要預測的資料行（標籤）** ] 下拉式清單中選擇 [ **RiskCategory** ]。
1. 保留 [**輸入資料行（功能）** ] 下拉式清單中選取的預設資料行 [ **InspectionType** ] 和 [ **ViolationDescription**]。
1. 選取 [**定型**] 連結，以移至 [模型產生器] 中的下一個步驟。

## <a name="train-the-model"></a>將模型定型

在本教學課程中用來定型問題分類模型的機器學習工作是多元分類。 在模型定型程式期間，模型產生器會使用不同的多元分類演算法和設定來訓練不同的模型，以尋找資料集最佳的執行模型。

定型模型所需的時間與資料量成正比。 「模型產生器」會根據您的資料來源大小，自動選取要定型的預設值 **（秒）** 。

1. 雖然模型產生器會將 [**要定型的時間] 值（秒）** 設定為10秒，但將它增加為30秒。 定型一段較長的時間，可讓模型產生器在搜尋最佳模型時，探索更多的演算法和參數組合。
1. 選取 [開始定型]。

    在整個定型程序期間，進度資料會顯示在定型步驟的 `Progress` 區段中。

    - **狀態**顯示定型進程的完成狀態。
    - **最佳精確度** 會顯示目前為止模型產生器所找到之最佳執行模型的精確度。 正確性越高，表示模型針對測試資料的預測越正確。
    - **最佳演算法** 會顯示目前為止模型產生器所找到之最佳演算法的名稱。
    - [**上次演算法]**  顯示模型產生器最近用來定型模型的演算法名稱。

1. 定型完成後，請選取 [**評估**] 連結以移至下一個步驟。

## <a name="evaluate-the-model"></a>評估模型

定型步驟的結果是一個具有最佳效能的模型。 在模型產生器的評估步驟中，[輸出] 區段包含最佳**模型**專案中最佳執行模型所使用的演算法，以及最佳**模型精確度**中的計量。 此外，摘要資料表包含最多五個已探索到的模型，而且會顯示其計量。

如果您不滿意精確度計量，嘗試改善模型精確度的一些簡單方法，就是增加定型模型或使用更多資料的時間量。 否則，請選取 [程式**代碼**] 連結，以移至模型產生器中的最後一個步驟。

## <a name="add-the-code-to-make-predictions"></a>新增程式碼來進行預測

定型程式會建立兩個專案。

- RestaurantViolationsML. Consoleapp.exe： C# .Net Core 主控台應用程式，其中包含模型定型和範例耗用量程式碼。
- RestaurantViolationsML： .NET Standard 類別庫，其中包含定義輸入和輸出模型資料之架構的資料模型、定型期間儲存的最佳執行模型版本，以及稱為 `ConsumeModel` 以進行預測的 helper 類別。

1. 在模型產生器的程式碼步驟中，選取 [**加入專案**]，將自動產生的專案加入至方案。
1. 開啟*RestaurantViolations*專案中的*Program.cs*檔案。
1. 新增下列 using 語句，以參考*RestaurantViolationsML 模型*專案：

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L2)]

1. 若要使用模型對新資料進行預測，請在應用程式的 `Main` 方法內，建立 `ModelInput` 類別的新實例。 請注意，[風險] 分類不是輸入的一部分。 這是因為模型會產生它的預測。

    [!code-csharp [TestData](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L11-L15)]

1. 使用來自 `ConsumeModel` 類別的 `Predict` 方法。 `Predict` 方法會載入定型的模型、建立模型的[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) ，並使用它來對新資料進行預測。

    [!code-csharp [Prediction](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L17-L24)]

1. 執行應用程式。

    程式所產生的輸出看起來應該會和以下程式碼片段相似：

    ```bash
    Inspection Type: Complaint
    Violation Description: Inadequate sewage or wastewater disposal
    Risk Category: Moderate Risk
    ```

若您需要於稍後在另外一個解決方案中參考所產生的專案，您可以在 `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` 目錄中找到它們。

恭喜您！ 您已成功建立機器學習模型，以使用模型產生器來分類健康情況違規的風險。 您可以在[dotnet/machinelearning 範例](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations)GitHub 存放庫中找到本教學課程的原始程式碼。

## <a name="additional-resources"></a>其他資源

若要深入了解此教學課程中提及的主題，請瀏覽下列資源：

- [模型建立器案例](../automate-training-with-model-builder.md#scenarios)
- [多元分類](../resources/glossary.md#multiclass-classification)
- [多元分類模型計量](../resources/metrics.md#metrics-for-multi-class-classification)
