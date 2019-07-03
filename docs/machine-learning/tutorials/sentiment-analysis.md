---
title: 教學課程：分析網站評論 - 二元分類
description: 本教學課程示範如何建立 .NET Core 主控台應用程式，來分類網站評論中的情感並採取適當動作。 二元情感分類器在 Visual Studio 中使用 C#。
ms.date: 05/13/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: a766d95c62fd3a89e3291e1ab803f5222fac46ea
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306173"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a>教學課程：在 ML.NET 中使用二元分類來分析網站評論的情感

本教學課程示範如何建立 .NET Core 主控台應用程式，來分類網站評論中的情感並採取適當動作。 二元情感分類器在 Visual Studio 2017 中使用 C#。

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> * 建立主控台應用程式
> * 準備資料
> * 載入資料
> * 建置和定型模型
> * 評估模型
> * 使用模型來進行預測
> * 查看結果

您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) 存放庫中找到本教學課程的原始程式碼。

## <a name="prerequisites"></a>必要條件

* 已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

* [UCI 情感標記句子資料集](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP 檔案)

## <a name="create-a-console-application"></a>建立主控台應用程式

1. 建立稱為 "SentimentAnalysis" 的 **.NET Core 主控台應用程式**。

2. 在專案中建立一個名為 *Data* 的目錄以儲存資料集檔案。

3. 安裝「Microsoft.ML NuGet 套件」  ：

    在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]  。 選擇 "nuget.org" 作為套件來源，然後選取 [瀏覽]  索引標籤。搜尋 **Microsoft.ML**，選取您想要的套件，然後選取 [安裝]  按鈕。 同意您所選套件的授權條款，以繼續進行安裝。 對 **Microsoft.ML.FastTree** NuGet 套件執行相同的動作。

## <a name="prepare-your-data"></a>準備您的資料

> [!NOTE]
> 此教學課程的資料集是來自 'From Group to Individual Labels using Deep Features' (從群組到使用深度特徵的個別標籤) (Kotzias 等人 al， KDD 2015)，而且裝載於「UCI Machine Learning Repository (UCI 機器學習存放庫)」- Dua, D. and Karra Taniskidou, E.(2017)。 「UCI Machine Learning Repository (UCI 機器學習存放庫)」[http://archive.ics.uci.edu/ml ]。 爾灣，加利福尼亞州：加州大學，資訊與電腦科學學院。

1. 下載並解壓縮 [UCI 情感標記句子資料集 ZIP 檔案](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)。

2. 將 `yelp_labelled.txt` 檔案複製到您所建立的 *Data* 目錄。

3. 在 [方案總管] 中，以滑鼠右鍵按一下 `yelp_labeled.txt` 檔案，並選取 [內容]  。 在 [進階]  底下，將 [複製到輸出目錄]  的值變更為 [有更新時才複製]  。

### <a name="create-classes-and-define-paths"></a>建立類別及定義路徑

1. 在 *Program.cs* 檔案頂端新增下列額外的 `using` 陳述式：

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

2. 建立兩個全域欄位，以保存最近所下載資料集檔案路徑與儲存的模型檔案路徑：

    * `_dataPath` 包含用來將模型定型的資料集路徑。
    * `_modelPath` 包含用來儲存定型模型的路徑。

3. 將下列程式碼新增至緊接在 `Main` 方法上方的一行，以指定路徑：

    [!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

4. 接下來，為輸入資料和預測建立類別。 將新類別新增至專案：

    - 在 [方案總管]  中，於專案上按一下滑鼠右鍵，然後選取 [新增]   > [新增項目]  。

    - 在 [新增項目]  對話方塊中，選取 [類別]  ，然後將 [名稱]  欄位變更為 *SentimentData.cs*。 接著，選取 [新增]  按鈕。

5. *SentimentData.cs* 檔案隨即在程式碼編輯器中開啟。 將以下 `using` 陳述式新增至 *SentimentData.cs* 頂端：

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

6. 移除現有的類別定義，然後將下列程式碼 (具有 `SentimentData` 和 `SentimentPrediction` 這兩個類別) 新增至 *SentimentData.cs* 檔案：

    [!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a>如何準備資料
輸入資料集類別 `SentimentData` 具有使用者評論 (`SentimentText`) 的 `string`，以及代表情感的 `bool` (`Sentiment`) 值 1 (正面) 或 0 (負面)。 這兩個欄位都有 [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) 附加屬性，其描述每個欄位的資料檔案順序。  此外，`Sentiment` 屬性具有 [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) 屬性來將它指定為 `Label` 欄位。 下列範例檔案沒有標頭資料列，且看起來像這樣：

|SentimentText                         |情感 (標籤) |
|--------------------------------------|----------|
|女服務生的服務速度有點慢。|    0     |
|不夠酥脆。                    |    0     |
|哇...喜歡這個地方。              |    1     |
|服務很迅速。              |    1     |

`SentimentPrediction` 是在模型定型後所使用的預測類別。 它繼承自 `SentimentData`，用於顯示 `SentimentText` 和預測。 `SentimentPrediction` 包含一個單一布林值 (`Sentiment`) 和一個 `PredictedLabel` `ColumnName` 屬性。 `Label` 會用來建立和定型模型，也會用來搭配分割出來的測試資料集來評估模型。 `PredictedLabel` 的使用時機是在進行預測和評估的期間。 就評估而言，會使用定型資料、預設值及模型。

[MLContext 類別](xref:Microsoft.ML.MLContext)是所有 ML.NET 作業的起點。 將 `mlContext` 初始化會建立新的 ML.NET 環境，可在模型建立工作流程物件間共用。 就概念而言，類似於 Entity Framework 中的 `DBContext`。

## <a name="load-the-data"></a>載入資料
ML.NET 中的資料以 [IDataView 類別](xref:Microsoft.ML.IDataView) 表示。 `IDataView` 是彈性且有效率的表格式資料描述方式 (數值和文字)。 資料可以從文字或即時 (例如 SQL 資料庫或記錄檔) 載入至 `IDataView` 物件。

您可以準備資料，然後載入資料：

1. 將 `Main` 方法中的 `Console.WriteLine("Hello World!")` 程式碼行取代為下列程式碼，以宣告 mlContext 變數並將它初始化：

    [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

2. 將下列程式碼加入為 `Main()` 方法中的下一行程式碼：

    [!code-csharp[CallLoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

3. 請使用下列程式碼，在緊接著 `Main()` 方法之後，建立 `LoadData()` 方法：

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    `LoadData()` 方法會執行下列工作：

    * 載入資料。
    * 將載入的資料集分割為定型與測試資料集。
    * 傳回分割的定型與測試資料集。

4. 將下列程式碼新增為 `LoadData()` 方法的第一行：

    [!code-csharp[LoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

    [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) 會定義資料結構描述並讀入檔案中。 會接受資料路徑變數然後傳回 `IDataView`。

### <a name="split-the-dataset-for-model-training-and-testing"></a>分割資料集以進行模型定型與測試

準備模型時，您可以使用部分資料集來定型它，並使用部分資料集來測試模型的準確度。

1. 若要將載入的資料分割成所需的資料集，請將下列程式碼加入為 `LoadData()` 方法中的下一行：

    [!code-csharp[SplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

    上述程式碼使用 [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) 方法將載入的資料集分割為定型與測試資料集，然後將它們包含在 [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) 類別中並傳回。 您可以使用 `testFraction` 參數來指定資料的測試集百分比。 預設值是 10%，但您在本例中會使用 20% 以評估更多資料。

2. 在 `LoadData()` 方法的結尾傳回 `splitDataView`：

    [!code-csharp[ReturnSplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a>建置和定型模型

1. 將下列呼叫新增至 `BuildAndTrainModel` 方法作為 `Main()` 方法中的下一行程式碼：

    [!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

    `BuildAndTrainModel()` 方法會執行下列工作：

    * 擷取並轉換資料。
    * 將模型定型。
    * 根據測試資料預測情感。
    * 傳回模型。

2. 請使用下列程式碼，在緊接著 `Main()` 方法之後，建立 `BuildAndTrainModel()` 方法：

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a>擷取並轉換資料

1. 呼叫 `FeaturizeText` 作為下一行程式碼：

    [!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

    上述程式碼中的 `FeaturizeText()` 方法會將文字資料行 (`SentimentText`) 轉換成機器學習演算法所使用的數值索引鍵類型 `Features` 資料行，並將它新增為新的資料集資料行：

    |SentimentText                         |情感 |功能              |
    |--------------------------------------|----------|----------------------|
    |女服務生的服務速度有點慢。|    0     |[0.76, 0.65, 0.44, …] |
    |不夠酥脆。                    |    0     |[0.98, 0.43, 0.54, …] |
    |哇...喜歡這個地方。              |    1     |[0.35, 0.73, 0.46, …] |
    |服務很迅速。              |    1     |[0.39, 0, 0.75, …]    |

### <a name="add-a-learning-algorithm"></a>新增學習演算法

此應用程式使用分類演算法來分類多個項目或資料列。 應用程式會將網站評論分類為正面或負面，因此請使用二元分類工作。

透過將下列內容新增為 `BuildAndTrainModel()` 中的下一行程式碼，將機器學習工作附加到資料轉換定義：

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) 是您的分類定型演算法。 這會附加到 `estimator`，並接受特徵化 `SentimentText` (`Features`) 和 `Label` 輸入參數，以從歷史資料學習。

### <a name="train-the-model"></a>將模型定型

將下列內容新增為 `BuildAndTrainModel()` 方法中的下一行程式碼，調整模型為合適於 `splitTrainSet` 資料並傳回已定型模型：

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) 方法會透過轉換資料集和套用定型來定型模型。

### <a name="return-the-model-trained-to-use-for-evaluation"></a>傳回經訓練以供評估使用的模型

 在 `BuildAndTrainModel()` 方法的結尾傳回模型：

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a>評估模型

定型模型之後，使用您的測試資料來驗證模型效能。

1. 在 `BuildAndTrainModel()` 之後，使用下列程式碼建立 `Evaluate()` 方法：

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    `Evaluate()` 方法會執行下列工作：

    * 載入測試資料集。
    * 建立 BinaryClassification 評估工具。
    * 評估模型並建立計量。
    * 顯示計量。

2. 請使用下列程式碼，在緊接著 `BuildAndTrainModel()` 方法呼叫底下，從 `Main()` 方法新增對新方法的呼叫：

    [!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

3. 將下列程式碼新增至 `Evaluate()` 以轉換 `splitTestSet` 資料：

    [!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

    上述程式碼使用 [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) 方法對多個提供的測試資料集輸入資料列進行預測。

4. 將下列內容新增為 `Evaluate()` 方法中的下一行程式碼來評估模型：

    [!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

在您設定好預測 (`predictions`) 後，[Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) 方法會評估模型，將預測值與測試資料集中的實際 `Labels` 進行比較，並傳回與模型執行情況相關的 [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) 物件。

### <a name="displaying-the-metrics-for-model-validation"></a>顯示模型驗證的計量

使用下列程式碼來顯示計量：

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

* `Accuracy` 計量會取得模型的準確度，這是資料集中正確預測的比例。

* `AreaUnderRocCurve` 計量會指出模型正確分類正面和負面類別的自信程度。 您會希望 `AreaUnderRocCurve` 盡可能接近 1。

* `F1Score` 計量會取得模型的 F1 分數，這是[精確度](../resources/glossary.md#precision)與[重新叫用率](../resources/glossary.md#recall)之間的平衡量值。  您會希望 `F1Score` 盡可能接近 1。

### <a name="predict-the-test-data-outcome"></a>預測測試資料結果

1. 請使用下列程式碼，在緊接著 `Evaluate()` 方法之後，建立 `UseModelWithSingleItem()` 方法：

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    `UseModelWithSingleItem()` 方法會執行下列工作：

    * 建立單一評論的測試資料。
    * 根據測試資料預測情感。
    * 合併測試資料和預測來進行報告。
    * 顯示預測的結果。

2. 請使用下列程式碼，在緊接著 `Evaluate()` 方法呼叫底下，從 `Main()` 方法新增對新方法的呼叫：

    [!code-csharp[CallUseModelWithSingleItem](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. 新增下列程式碼，建立作為 `UseModelWithSingleItem()` 方法中的第一行：

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) 是一種便利的 API，可讓您傳遞並在單一資料執行個體上接著執行預測。

4. 透過建立 `SentimentData` 的執行個體，在 `UseModelWithSingleItem()` 方法中新增評論，以測試定型模型的預測：

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. 透過將下列內容新增為 `Prediction Engine` 方法中的後續幾行程式碼，將測試評論資料傳遞到 `UseModelWithSingleItem()`：

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

    [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) 函式會對單一資料列進行預測。

6. 使用下列程式碼來顯示 `SentimentText` 和對應的情感預測：

    [!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a>使用模型來進行預測

### <a name="deploy-and-predict-batch-items"></a>部署並預測批次項目

1. 請使用下列程式碼，在緊接著 `UseModelWithSingleItem()` 方法之後，建立 `UseModelWithBatchItems()` 方法：

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    `UseModelWithBatchItems()` 方法會執行下列工作：

    * 建立批次測試資料。
    * 根據測試資料預測情感。
    * 合併測試資料和預測來進行報告。
    * 顯示預測的結果。

2. 請使用下列程式碼，在緊接著 `UseModelWithSingleItem()` 方法呼叫底下，從 `Main` 方法新增對新方法的呼叫：

    [!code-csharp[CallPredictModelBatchItems](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. 新增一些評論以測試 `UseModelWithBatchItems()` 方法中定型模型的預測：

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a>預測評論情感

利用 [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) 方法，使用該模型來預測評論資料情感：

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a>合併並顯示預測

使用下列程式碼來為預測建立標頭：

[!code-csharp[OutputHeaders](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

因為 `SentimentPrediction` 繼承自 `SentimentData`，所以 `Transform()` 方法會使用預測欄位填入 `SentimentText`。 隨著 ML.NET 處理的進行，每個元件都會新增資料行，使其易於顯示結果：

[!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a>結果

您的結果應該與以下類似。 處理期間會顯示訊息。 您可能會看到警告或處理訊息。 為了清晰起見，下列結果中已將這些都移除。

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 83.96%
Auc: 90.51%
F1Score: 84.04%

=============== End of model evaluation ===============

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This was a very bad steak | Prediction: Negative | Probability: 0.1027377
=============== End of Predictions ===============


=============== Prediction Test of loaded model with a multiple samples ===============

Sentiment: This was a horrible meal | Prediction: Negative | Probability: 0.1369192
Sentiment: I love this spaghetti. | Prediction: Positive | Probability: 0.9960636
=============== End of predictions ===============

=============== End of process ===============
Press any key to continue . . .

```

恭喜您！ 您現在已成功建置可對訊息情感進行分類和預測的機器學習模型。

建立成功的模型是一個需要反覆嘗試的程序。 此模型一開始的品質較低，因為此教學課程是使用小型的資料集來提供快速的模型定型。 如果您對於模型的品質感到不滿意，可以嘗試為它提供較大的定型資料集，或選擇不同的定型演算法，並針對每個演算法搭配不同[超參數](../resources/glossary.md##hyperparameter)來改善它。

您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) 存放庫中找到本教學課程的原始程式碼。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> * 建立主控台應用程式
> * 準備資料
> * 載入資料
> * 建置和定型模型
> * 評估模型
> * 使用模型來進行預測
> * 查看結果

前進到下一個教學課程來深入了解
> [!div class="nextstepaction"]
> [問題分類](github-issue-classification.md)
