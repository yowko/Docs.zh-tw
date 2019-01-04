---
title: 使用叢集學習工具建立鳶尾花叢集 - ML.NET
description: 了解如何在群集案例中使用 ML.NET
author: pkulikov
ms.author: johalex
ms.date: 12/17/2018
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 012cea471c69f66ad9a61db858b4575606b31f74
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/20/2018
ms.locfileid: "53656319"
---
# <a name="tutorial-cluster-iris-flowers-using-a-clustering-learner-with-mlnet"></a>教學課程：ML.NET 的使用叢集學習工具建立鳶尾花叢集

> [!NOTE]
> 本主題涉及 ML.NET，此功能目前為公開預覽版，因此内容可能會有變更。 如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) \(英文)。

本教學課程說明如何使用 ML.NET 為[鳶尾花資料集](https://en.wikipedia.org/wiki/Iris_flower_data_set)建立一個[群集模型](../resources/tasks.md#clustering)。

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> - 了解問題
> - 選取適當的機器學習工作
> - 準備資料
> - 載入並轉換資料
> - 選擇學習演算法
> - 將模型定型
> - 使用模型來進行預測

## <a name="prerequisites"></a>必要條件

- 已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)。

## <a name="understand-the-problem"></a>了解問題

這個問題是關於將一組鳶尾花按照花卉特徵分成不同的群組。 這些特徵是萼片的長度和寬度以及花瓣的長度和寬度。 本教學課程中假設不知道每個花卉的類型。 您想要從特徵了解資料集的結構，還要預測資料執行個體如何符合此結構。

## <a name="select-the-appropriate-machine-learning-task"></a>選取適當的機器學習工作

因為您不知道每個花卉屬於哪個群組，所以您選擇[非監督式機器學習](../resources/glossary.md#unsupervised-machine-learning)工作。 若要按照類似元素歸於同一群組中的方式來分割群組中的資料集，請使用[群集](../resources/tasks.md#clustering)機器學習工作。

## <a name="create-a-console-application"></a>建立主控台應用程式

1. 開啟 Visual Studio 2017。 從功能表列中選取 [檔案]  >  [新增]  >  [專案]。 在 [新增專案] 對話方塊中，選取 [Visual C#] 節點，然後選取 [.NET Core] 節點。 然後選取 [主控台應用程式 (.NET Core)] 專案範本。 在 [名稱] 文字方塊中，鍵入 "IrisFlowerClustering"，然後選取 [確定] 按鈕。

1. 在您的專案中建立一個名為 *Data* 的目錄以儲存資料集和模型檔案：

    在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取 [新增] > [新增資料夾]。 輸入 "Data"，然後按 Enter。

1. 安裝 **Microsoft.ML** NuGet 套件：

    在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取 [管理 NuGet 套件]。 選擇 "nuget.org" 作為 [套件來源]，選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。 在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。

## <a name="prepare-the-data"></a>準備資料

1. 下載 [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) 資料集，並將它儲存到上一個步驟中建立的 *Data* 資料夾。 如需有關鳶尾花資料集的詳細資訊，請參閱[鳶尾花資料集](https://en.wikipedia.org/wiki/Iris_flower_data_set)維基百科頁面和[鳶尾花資料集](http://archive.ics.uci.edu/ml/datasets/Iris)頁面 (也就是資料集的來源)。

1. 以滑鼠右鍵按一下 [方案總管] 中的 *iris.data* 檔案，然後選取 [內容]。 在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。

*Iris.data* 檔案包含五個資料行，分別表示：

- 萼片長度 (以公分為單位)
- 萼片寬度 (以公分為單位)
- 花瓣長度 (以公分為單位)
- 花瓣寬度 (以公分為單位)
- 鳶尾花的類型

為了示範群集方法，本教學課程會略過最後一個資料行。

## <a name="create-data-classes"></a>建立資料類別

為輸入資料和預測建立類別：

1. 在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。
1. 在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *IrisData.cs*。 接著，選取 [新增] 按鈕。
1. 將下列的 `using` 指示詞加入新檔案：

   [!code-csharp[Add necessary usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#Usings)]

移除現有的類別定義，然後將下列程式碼 (定義 `IrisData` 和 `ClusterPrediction` 這兩個類別) 新增至 *IrisData.cs* 檔案：

[!code-csharp[Define data classes](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#ClassDefinitions)]

`IrisData` 是輸入資料類別，它含有資料集中每個特徵的定義。 請使用 [Column](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) 屬性來指定資料集檔案中來源資料行的索引。

`ClusterPrediction` 類別代表套用至 `IrisData` 執行個體的群集模型結果。 使用 [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) 屬性分別將 `PredictedClusterId` 和 `Distances` 欄位繫結至 **PredictedLabel** 和 **Score** 資料行。 群集這些資料行的工作具有下列意義：

- **PredictedLabel** 資料行包含預測群集的 ID。
- **Score** 資料行包含平方歐幾里得距離到群集矩心的陣列。 陣列長度等於群集數目。

> [!NOTE]
> 使用 `float` 型別表示輸入和預測資料類別中的浮點值。

## <a name="define-data-and-model-paths"></a>定義資料和模型路徑

返回 *Program.cs* 檔案並新增兩個欄位，保存資料集檔案的路徑以及儲存模型之檔案的路徑：

- `_dataPath` 會針對具有用來定型模型之資料集的檔案，包含檔案的路徑。
- `_modelPath` 會針對儲存定型模型的檔案，包含檔案的路徑。

將下列程式碼加入 `Main` 方法的緊鄰上方，以指定這些路徑：

[!code-csharp[Initialize paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Paths)]

若要將上述的程式碼進行編譯，請在 *Program.cs* 檔案頂端加入下列 `using` 指示詞：

[!code-csharp[Add usings for paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a>建立 ML 內容

在 *Program.cs* 檔案頂端加入下列額外的 `using` 指示詞：

[!code-csharp[Add Microsoft.ML usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#MLUsings)]

在 `Console.WriteLine("Hello World!");` 方法中，以下列程式碼取代 `Main` 行：

[!code-csharp[Create ML context](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateContext)]

<xref:Microsoft.ML.MLContext?displayProperty=nameWithType> 類別表示機器學習環境，並為資料載入、模型定型、預測和其他工作提供記錄機制和進入點。 這在概念上類似於在 Entity Framework 中使用 `DbContext`。

## <a name="setup-data-loading"></a>設定資料載入

將下列程式碼新增至 `Main` 方法，以設定資料載入方式：

[!code-csharp[Create text loader](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SetupTextLoader)]

請注意，資料行名稱和索引會符合 `IrisData` 類別所定義的結構描述。 <xref:Microsoft.ML.Runtime.Data.DataKind.R4?displayProperty=nameWithType> 值指定 `float` 類型。

使用具現化的 <xref:Microsoft.ML.Runtime.Data.TextLoader> 執行個體來建立 <xref:Microsoft.ML.Runtime.Data.IDataView> 執行個體，以表示定型資料集的資料來源：

[!code-csharp[Create IDataView](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateDataView)]

## <a name="create-a-learning-pipeline"></a>建立學習管線

在本教學課程中，叢集工作的學習管線包含下列兩個步驟：

- 將載入的資料行串連成一個 [特徵] 資料行，以供叢集定型器使用；
- 使用 <xref:Microsoft.ML.Trainers.KMeans.KMeansPlusPlusTrainer> 定型器透過 k-means++ 叢集演算法將模型定型。

將下列程式碼加入 `Main` 方法：

[!code-csharp[Create pipeline](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreatePipeline)]

此程式碼指定應該將資料集分成三個叢集。

## <a name="train-the-model"></a>將模型定型

上述小節中加入的步驟已準備好訓練的管道，不過，還沒有開始執行。 將下列程式碼行新增至 `Main` 方法，以執行資料載入和模型定型：

[!code-csharp[Train the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#TrainModel)]

### <a name="save-the-model"></a>儲存模型

此時，您已有一個可整合至任何現有或新 .NET 應用程式的模型。 若要將您的模型儲存成 .zip 檔案，請將下列程式碼新增至 `Main` 方法：

[!code-csharp[Save the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a>使用模型來進行預測

為了進行預測，請使用 <xref:Microsoft.ML.Runtime.Data.PredictionFunction%602> 類別，其帶領輸入類型的執行個體通過轉換程式管線，並產生輸出類型的執行個體。 將下列程式碼行新增至 `Main` 方法，以建立該類別的執行個體：

[!code-csharp[Create predictor](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Predictor)]

建立 `TestIrisData` 類型以容納測試資料執行個體：

1. 在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。
1. 在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *TestIrisData.cs*。 接著，選取 [新增] 按鈕。
1. 將類別修改成靜態，如以下範例所示：

   [!code-csharp[Make class static](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#Static)]

本教學課程介紹此類別內一個鳶尾花資料執行個體。 您可以新增其他案例來對此模型進行實驗。 將下列程式碼新增至 `TestIrisData` 類別：

[!code-csharp[Test data](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#TestData)]

若要找出指定項目所屬的群集，請返回 *Program.cs* 檔案，然後將下列程式碼加入至 `Main` 方法：

[!code-csharp[Predict and output results](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#PredictionExample)]

執行程式，以查看哪些群集包含指定的資料執行個體以及從該執行個體到群集矩心的平方距離。 您的結果應該與以下類似：

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

恭喜您！ 您現在已成功建置用來群集鳶尾花並進行預測的機器學習模型。 您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub 存放庫中找到本教學課程的原始程式碼。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> - 了解問題
> - 選取適當的機器學習工作
> - 準備資料
> - 載入並轉換資料
> - 選擇學習演算法
> - 將模型定型
> - 使用模型來進行預測

請查看我們的 GitHub 存放庫來繼續學習及尋找更多範例。
> [!div class="nextstepaction"]
> [dotnet/machinelearning GitHub 存放庫](https://github.com/dotnet/machinelearning/)
