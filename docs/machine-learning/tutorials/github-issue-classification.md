---
title: 教學課程：分類支援問題 - 多類別分類
description: 了解如何在多類別分類案例中使用 ML.NET 來分類 GitHub 問題，以將它們指派至特定區域。
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: a6d158d51e6775feaed669c678bb9a36984f08f3
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698980"
---
# <a name="tutorial-categorize-support-issues-using-multiclass-classification-with-ml-net"></a>教學課程：搭配 ML .NET 使用多類別分類來分類支援問題

此範例教學課程會示範使用 ML.NET，透過使用 Visual Studio 中 C# 的 .NET Core 主控台應用程式，建立 GitHub 問題分類器，來定型分類及預測 GitHub 問題 Area 標籤的模型。

在本教學課程中，您將了解如何：
> [!div class="checklist"]
>
> * 準備您的資料
> * 轉換資料
> * 將模型定型
> * 評估模型
> * 使用訓練過的模型預測
> * 使用已載入的模型部署和預測

您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) 存放庫中找到本教學課程的原始程式碼。

## <a name="prerequisites"></a>必要條件

* 已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)。

* [Github issues tab separated file (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) (Github 問題定位字元分隔檔案 (issues_train.tsv))。
* [Github issues test tab separated file (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) (Github 問題測試定位字元分隔檔案 (issues_test.tsv))。

## <a name="create-a-console-application"></a>建立主控台應用程式

### <a name="create-a-project"></a>建立專案

1. 開啟 Visual Studio 2017。 從功能表列中選取 [檔案]  >  [新增]  >  [專案]。 在 [新增專案] 對話方塊中，選取 [Visual C#] 節點，然後選取 [.NET Core] 節點。 然後選取 [主控台應用程式 (.NET Core)] 專案範本。 在 [名稱] 文字方塊中，鍵入 "GitHubIssueClassification"，然後選取 [確定] 按鈕。

2. 在您的專案中建立一個名為 *Data* 的目錄以儲存資料集檔案：

    在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [新增] > [新增資料夾]。 輸入 "Data"，然後按 Enter。

3. 在您的專案中建立名為 *Models* 的目錄，以儲存您的模型：

    在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [新增] > [新增資料夾]。 鍵入 "Models"，然後按 ENTER。

4. 安裝「Microsoft.ML NuGet 套件」：

    在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。 選擇 "nuget.org" 作為套件來源、選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、在清單中選取 **v 1.0.0** 套件，然後選取 [安裝] 按鈕。 在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。

### <a name="prepare-your-data"></a>準備您的資料

1. 下載 [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) 和 [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) 資料集，並將它們儲存至先前建立的 *Data* 資料夾。 第一個資料集會將機器學習模型定型，第二個資料集則可用來評估您模型的準確率。

2. 在 [方案總管] 中，於每個 \*.tsv 檔案上按一下滑鼠右鍵，然後選取 [屬性]。 在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。

### <a name="create-classes-and-define-paths"></a>建立類別及定義路徑

在 *Program.cs* 檔案頂端新增下列額外的 `using` 陳述式：

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

建立三個全域欄位來保留近期下載檔案的路徑，以及 `MLContext`、`DataView` 和 `PredictionEngine` 的全域變數：

* `_trainDataPath` 包含用來將模型定型的資料集路徑。
* `_testDataPath` 包含用來評估模型的資料集路徑。
* `_modelPath` 包含用來儲存定型模型的路徑。
* `_mlContext` 是提供處理內容的 <xref:Microsoft.ML.MLContext>。
* `_trainingDataView` 是用來處理定型資料集的 <xref:Microsoft.ML.IDataView>。
* `_predEngine` 是用於單一預測的 <xref:Microsoft.ML.PredictionEngine%602>。

將下列程式碼新增至 `Main` 方法正上方的一行，以指定這些路徑和其他變數：

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

為輸入資料和預測建立一些類別。 將新類別新增至專案：

1. 在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。

1. 在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *GitHubIssueData.cs*。 接著，選取 [新增] 按鈕。

    *GitHubIssueData.cs* 檔案隨即在程式碼編輯器中開啟。 將下列 `using` 陳述式新增至 *GitHubIssueData.cs* 最上方：

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

移除現有的類別定義，然後將下列程式碼 (具有 `GitHubIssue` 和 `IssuePrediction` 這兩個類別) 新增至 *GitHubIssueData.cs* 檔案：

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

`label` 是您希望進行預測的資料行。 識別的 `Features` 是您提供模型，以預測標籤 (Label) 的輸入。

請使用 [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) 來指定資料集中來源資料行的索引。

`GitHubIssue` 是輸入資料集類別，並具有下列 <xref:System.String> 欄位：

* 第一個資料行 `ID`(GitHub 問題識別碼)
* 第二個資料行 `Area`(用於定型的預測)
* 第三個資料行 `Title` (GitHub 問題標題) 是第一個用來預測 `Area` 的 `feature`
* 第四個資料行 `Description` 是第二個用來預測 `Area` 的 `feature`

`IssuePrediction` 是在模型定型後，用來進行預測的類別。 它包含單一布林值 `string` (`Area`) 和 `PredictedLabel` `ColumnName` 屬性。  `PredictedLabel` 的使用時機是在進行預測和評估的期間。 就評估而言，會使用含有定型資料、預設值及模型的輸入。

所有 ML.NET 作業都是從 [MLContext](xref:Microsoft.ML.MLContext) 類別開始。 初始化 `mlContext` 會建立新的 ML.NET 環境，可在模型建立工作流程物件間共用。 就概念而言，它與 `Entity Framework` 中的 `DBContext` 相似。

### <a name="initialize-variables-in-main"></a>在 Main 中初始化變數

將具有包含隨機種子 (`seed: 0`) 之新 `MLContext` 執行個體的 `_mlContext` 全域變數初始化，以讓多個定型間的結果可重複/具有確定性。  在 `Main` 方法中，以下列程式碼取代 `Console.WriteLine("Hello World!")`：

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a>載入資料

ML.NET 使用 [IDataView 類別](xref:Microsoft.ML.IDataView)作為描述數字或文字表格式資料彈性且有效率的方式。 `IDataView` 可載入文字檔案或即時進行 (例如 SQL 資料庫或記錄檔)。

若要初始化並載入 `_trainingDataView` 全域變數以將其用於管線，請在 `mlContext` 初始化後，新增下列程式碼：

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]

[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) 會定義資料結構描述並讀入檔案中。 會接受資料路徑變數然後傳回 `IDataView`。

將下列程式碼加入為 `Main` 方法中的下一行程式碼：

[!code-csharp[CallProcessData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

`ProcessData` 方法會執行下列工作：

* 擷取並轉換資料。
* 傳回處理管線。

請使用下列程式碼，在緊接著 `Main` 方法之後，建立 `ProcessData` 方法：

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a>擷取 Features 並傳輸資料

當您想要針對 `GitHubIssue` 預測 Area GitHub 標籤時，請使用 [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) 方法，將 `Area` 資料行轉換成數字索引鍵類型 `Label` 資料行 (分類演算法接受的格式)，並將它新增為新的資料集資料行：

[!code-csharp[MapValueToKey](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

接下來，請呼叫 `mlContext.Transforms.Text.FeaturizeText`，針對每個呼叫的 `TitleFeaturized` 和 `DescriptionFeaturized`，將文字 (`Title` 和 `Description`) 資料行轉換成數值向量。 將這兩個資料行的特徵轉換附加至管線，使用的程式碼如下：

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

資料準備的最後一個步驟是使用 [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) 方法，將所有特徵資料行合併到 **Features** (特徵) 資料行。 根據預設，學習演算法只會處理來自 **Features** 資料行的特徵。 將這此轉換附加至管線，使用的程式碼如下：

[!code-csharp[Concatenate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 接著，附加 <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> 來快取 DataView，以便在您多次逐一查看資料時，使用快取可獲得更高的效能，如下列程式碼所示：

[!code-csharp[AppendCache](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

> [!WARNING]
> 針對小型/中型資料集使用 AppendCacheCheckpoint 以減少訓練時間。 請不要在處理非常大的資料集時使用它 (移除 .AppendCacheCheckpoint())。

在 `ProcessData` 方法的結尾傳回管線。

[!code-csharp[ReturnPipeline](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

這個步驟會處理前置處理/特徵轉換。 使用 ML.NET 中可用的額外元件可讓您的模型產生更佳的結果。

## <a name="build-and-train-the-model"></a>建置和定型模型

將下列呼叫新增至 `BuildAndTrainModel` 方法作為 `Main` 方法中的下一行程式碼：

[!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

`BuildAndTrainModel` 方法會執行下列工作：

* 建立定型演算法類別。
* 將模型定型。
* 根據定型資料預測區域。
* 傳回模型。

請使用下列程式碼，在緊接著 `Main` 方法之後，建立 `BuildAndTrainModel` 方法：

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a>關於分類工作

分類是一項機器學習服務工作，會使用資料來**判斷**項目或資料列的分類、類型或類別，且經常是下列其中一種類型：

* 二元：不是 A 就是 B。
* 多元分類：可使用單一模型來預測的多重分類。

針對此類型的問題，請使用多類別分類學習演算法，因為您的問題類別預測可能是多個類別 (多類別) 的其中之一，而不只是兩個類別 (二元)。

透過將下列內容新增為 `BuildAndTrainModel()` 中的第一行程式碼，將機器學習服務演算法附加到資料轉換定義：

[!code-csharp[AddTrainer](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

[SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) 是您的多類別分類定型演算法。 它會附加到 `pipeline` 並接受特徵化的 `Title` 和 `Description` (`Features`) 及 `Label` 輸入參數，以從歷史資料學習。

### <a name="train-the-model"></a>將模型定型

將下列內容新增為 `BuildAndTrainModel()` 方法中的下一行程式碼，調整模型為合適於 `splitTrainSet` 資料並傳回已定型模型：

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

`Fit()` 方法會透過轉換資料集和套用定型來定型您的模型。

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) 是一種便利的 API，可讓您傳遞並在單一資料執行個體上接著執行預測。 將此新增為 `BuildAndTrainModel()` 方法中的下一行：

[!code-csharp[CreatePredictionEngine1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a>使用訓練過的模型預測

透過建立 `GitHubIssue` 的執行個體，在 `Predict` 方法中新增 GitHub 問題，以測試所定型模型的預測：

[!code-csharp[CreateTestIssue1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

使用 [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) 函式來針對單一資料列進行預測：

[!code-csharp[Predict](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a>使用模型：預測結果

顯示 `GitHubIssue` 和相對應的 `Area` 標籤預測，以共用結果並根據結果相應地採取動作。  請使用下列 <xref:System.Console.WriteLine?displayProperty=nameWithType> 程式碼來為結果建立顯示：

[!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a>傳回經訓練以供評估使用的模型

在 `BuildAndTrainModel` 方法的結尾傳回模型。

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a>評估模型

建立並定型模型之後，現在必須使用不同的資料集來評估它，以確保和驗證品質。 在 `Evaluate` 方法中，會傳入在 `BuildAndTrainModel` 中建立的模型以供評估。 在緊接著 `BuildAndTrainModel` 之後，建立 `Evaluate` 方法，如以下程式碼所示：

```csharp
public static void Evaluate(DataViewSchema trainingDataViewSchema)
{

}
```

`Evaluate` 方法會執行下列工作：

* 載入測試資料集。
* 建立多類別評估工具。
* 評估模型並建立計量。
* 顯示計量。

請使用下列程式碼，在緊接著 `BuildAndTrainModel` 方法呼叫底下，從 `Main` 方法新增對新方法的呼叫：

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

如同您先前針對定型資料集所進行的操作，請透過將下列程式碼新增到 `Evaluate` 方法，來載入測試資料集：

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

[Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) 方法會使用指定的資料集，計算模型的品質計量。 它傳回的 <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> 物件包含多類別分類評估工具所計算的整體計量。
若要顯示計量以判斷模型的品質，您必須先取得計量。
請注意我們在此處使用機器學習服務 `_trainedModel` 全域變數 (一個 [ITransformer](xref:Microsoft.ML.ITransformer)) 的 [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) 方法來輸入特徵並傳回預測。 將下列程式碼加入 `Evaluate` 方法中作為的下一行：

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

針對多類別分類評估的計量如下：

* 微精確度 - 每個範例類別組同樣都會對精確度計量提出貢獻。  建議讓微精確度盡量接近 1。

* 大精確度 - 每個類別同樣都會對精確度計量提出貢獻。 少數類別會加上與較大類別相同的權重。 建議讓大精確度盡量接近 1。

* 記錄檔遺失 - 請參閱[記錄檔遺失](../resources/glossary.md#log-loss)。 建議讓記錄檔遺失盡量接近零。

* 記錄檔遺失減少 - 範圍介於 [-inf, 100]，其中 100 表示完美的預測，而 0 表示平均預測。 建議讓記錄檔遺失減少盡量接近零。

### <a name="displaying-the-metrics-for-model-validation"></a>顯示模型驗證的計量

使用下列程式碼來顯示計量、共用結果，然後依結果採取動作：

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

### <a name="save-the-model-to-a-file"></a>將模型儲存至檔案

滿意您的模型之後，請將它儲存至檔案，以便稍後或在另一個應用程式中進行預測。 將下列程式碼加入至 `Evaluate` 方法。 

[!code-csharp[SnippetCallSaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SnippetCallSaveModel)]

在您的 `Evaluate`方法下方建立 `SaveModelAsFile` 方法。

```csharp
private static void SaveModelAsFile(MLContext mlContext,DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

將下列程式碼新增至 `SaveModelAsFile` 方法。 此程式碼使用 [`Save`](xref:Microsoft.ML.ModelOperationsCatalog.Save*) 方法，將定型的模型序列化並儲存為 ZIP 檔案。

[!code-csharp[SnippetSaveModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SnippetSaveModel)]

## <a name="deploy-and-predict-with-a-model"></a>部署及使用模型進行預測

請使用下列程式碼，在緊接著 `Evaluate` 方法呼叫底下，從 `Main` 方法新增對新方法的呼叫：

[!code-csharp[CallPredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

請使用下列程式碼，緊接在 `Evaluate` 方法之後 (並緊接在 `SaveModelAsFile` 方法之前)，建立 `PredictIssue` 方法：

```csharp
private static void PredictIssue()
{

}
```

`PredictIssue` 方法會執行下列工作：

* 載入已儲存的模型
* 建立測試資料的單一問題。
* 根據測試資料預測區域。
* 合併測試資料和預測來進行報告。
* 顯示預測的結果。

將下列程式碼新增至 `PredictIssue` 方法，以將已儲存模型載入至您的應用程式：

[!code-csharp[SnippetLoadModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#SnippetLoadModel)]

透過建立 `GitHubIssue` 的執行個體，在 `Predict` 方法中新增 GitHub 問題，以測試所定型模型的預測：

[!code-csharp[AddTestIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

如同您先前進行的操作，請使用下列程式碼建立 `PredictionEngine` 執行個體：

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602)是一個方便的 API，可讓您在單一資料實例上執行預測。 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) 不是安全執行緒。 可接受在單一執行緒或原型環境中使用。 為了改善生產環境中的效能和執行緒安全，請使用 `PredictionEnginePool` 服務，這會建立[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)物件的[@no__t 2](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) ，以供整個應用程式使用。 請參閱本指南，以瞭解如何[在 ASP.NET Core WEB API 中使用 `PredictionEnginePool`](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application)

> [!NOTE]
> `PredictionEnginePool` 服務延伸模組目前處於預覽狀態。

使用 `PredictionEngine` 來透過將下列程式碼新增到預測的 `PredictIssue` 方法，來預測 Area GitHub 標籤：

[!code-csharp[PredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a>使用載入的模型來進行預測

顯示 `Area` 以分類問題，並根據該分類採取動作。 請使用下列 <xref:System.Console.WriteLine?displayProperty=nameWithType> 程式碼來為結果建立顯示：

[!code-csharp[DisplayResults](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a>結果

您的結果應該與以下類似。 當管線進行處理時，會顯示訊息。 您可能會看到警告或處理訊息。 為了讓結果變得清楚，這些訊息已從下列結果中移除。

```console
=============== Single Prediction just-trained-model - Result: area-System.Net ===============
*************************************************************************************************************
*       Metrics for Multi-class Classification model - Test Data
*------------------------------------------------------------------------------------------------------------
*       MicroAccuracy:    0.738
*       MacroAccuracy:    0.668
*       LogLoss:          .919
*       LogLossReduction: .643
*************************************************************************************************************
=============== Single Prediction - Result: area-System.Data ===============
```

恭喜您！ 您現在已成功建置可對 GitHub 問題分類和預測 Area 標籤的機器學習模型。 您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) 存放庫中找到本教學課程的原始程式碼。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您將了解如何：
> [!div class="checklist"]
>
> * 準備您的資料
> * 轉換資料
> * 將模型定型
> * 評估模型
> * 使用訓練過的模型預測
> * 使用已載入的模型部署和預測

前進到下一個教學課程來深入了解
> [!div class="nextstepaction"]
> [計程車車資預測工具](taxi-fare.md)
