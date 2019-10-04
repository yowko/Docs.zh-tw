---
title: 教學課程：使用迴歸預測價格
description: 本教學課程會示範如何使用 ML.NET 建置迴歸模型，特別針對紐約市的計程車費用預測價格。
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc, seodec18, title-hack-0516
ms.openlocfilehash: 51617d14e84fa46464d7b44dbdb20afaf196924f
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2019
ms.locfileid: "71957374"
---
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a>教學課程：搭配 ML.NET 使用迴歸預測價格

本教學課程會示範如何使用 ML.NET 建置[迴歸模型](../resources/glossary.md#regression)，特別針對紐約市的計程車費用預測價格。

在本教學課程中，您將了解如何：
> [!div class="checklist"]
>
> * 準備並了解資料
> * 載入並轉換資料
> * 選擇學習演算法
> * 將模型定型
> * 評估模型
> * 使用模型來進行預測

## <a name="prerequisites"></a>必要條件

* 已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)。

## <a name="create-a-console-application"></a>建立主控台應用程式

1. 建立稱為 "TaxiFarePrediction" 的 **.NET Core 主控台應用程式**。

1. 在您專案中建立名為 *Data* 的目錄以用來儲存資料集和模型檔案。

1. 安裝 **Microsoft.ML** NuGet 套件：

    在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取 [管理 NuGet 套件]。 選擇 "nuget.org" 作為 [套件來源]、選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。 在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。 針對 **Microsoft.ML.FastTree** Nuget 套件執行相同的動作。

## <a name="prepare-and-understand-the-data"></a>準備並了解資料

1. 下載 [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) 和 [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) 資料集，並將它們儲存至您在上一個步驟所建立的 *Data* 資料夾。 我們可以使用這些資料集將機器學習模型定型，然後評估模型的準確程度。 這些資料集原先來自 [NYC TLC Taxi Trip 資料集](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)。

1. 在 [方案總管] 中，以滑鼠右鍵按一下每個 \*.csv 檔案，然後選取 [屬性]。 在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。

1. 開啟 **taxi-fare-train.csv** 資料集，然後查看第一個資料列中的資料行標頭。 請查看每個資料行。 了解資料，並決定哪些資料行是 **features**，以及哪一個資料行是 **label**。

`label` 是您希望進行預測的資料行。 識別的 `Features` 是您提供模型來預測 `Label` 的輸入。

提供的資料集包含下列資料行：

* **vendor_id：** 計程車廠商的識別碼是一項特徵。
* **rate_code：** 計程車行程的費率類型是一項特徵。
* **passenger_count：** 行程的乘客數目是一項特徵。
* **trip_time_in_secs：** 行程所花費的時間長度。 您想要在行程結束之前預測行程的車資。 那時，您並不知道行程需要多長的時間。 因此，行程時間不是一項特徵，您將從模型中排除這個資料行。
* **trip_distance：** 行程的距離是一項特徵。
* **payment_type：** 付款方式 (現金或信用卡) 是一項特徵。
* **fare_amount：** 計程車車資總計是標籤。

## <a name="create-data-classes"></a>建立資料類別

為輸入資料和預測建立類別：

1. 在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。
1. 在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *TaxiTrip.cs*。 接著，選取 [新增] 按鈕。
1. 將下列的 `using` 指示詞加入新檔案：

   [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

移除現有的類別定義，然後將下列程式碼 (具有 `TaxiTrip` 和 `TaxiTripFarePrediction` 這兩個類別) 新增至 *TaxiTrip.cs* 檔案：

[!code-csharp[DefineTaxiTrip](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip` 是輸入資料類別，並含有每個資料集資料行的定義。 使用 <xref:Microsoft.ML.Data.LoadColumnAttribute> 屬性來指定資料集中來源資料行的索引。

`TaxiTripFarePrediction` 類別代表預測的結果。 包含一個套用 `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> 屬性的單一浮點數欄位 `FareAmount`。 如果是迴歸工作，則**分數**資料行包含預測的標籤值。

> [!NOTE]
> 使用 `float` 型別表示輸入和預測資料類別中的浮點值。

### <a name="define-data-and-model-paths"></a>定義資料和模型路徑

在 *Program.cs* 檔案頂端新增下列額外的 `using` 陳述式：

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

您必須建立三個欄位，保存含有資料集的檔案與用來儲存模型之檔案的檔案路徑：

* `_trainDataPath` 會針對具有用來定型模型之資料集的檔案，包含檔案的路徑。
* `_testDataPath` 會針對具有用來評估模型之資料集的檔案，包含檔案的路徑。
* `_modelPath` 會針對儲存定型模型的檔案，包含檔案的路徑。

將下列程式碼加入至緊接在 `Main` 方法上方，以指定這些路徑和 `_textLoader` 變數：

[!code-csharp[InitializePaths](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

所有 ML.NET 作業都是從 [MLContext 類別](xref:Microsoft.ML.MLContext)開始。 初始化 `mlContext` 會建立新的 ML.NET 環境，可在模型建立工作流程物件間共用。 就概念而言，類似於 Entity Framework 中的 `DBContext`。

### <a name="initialize-variables-in-main"></a>在 Main 中初始化變數

將 `Main` 方法中的 `Console.WriteLine("Hello World!")` 程式碼替換成下列程式碼，宣告並初始化 `mlContext` 變數：

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create the ML Context")]

將下列內容加入為 `Main` 方法中的下一行程式碼，來呼叫 `Train` 方法：

[!code-csharp[Train](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Train your model")]

`Train()` 方法會執行下列工作：

* 載入資料。
* 擷取並轉換資料。
* 將模型定型。
* 傳回模型。

`Train` 方法會將模型定型。 請使用下列程式碼，在緊接著 `Main` 底下建立該方法：

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a>載入並轉換資料

ML.NET 使用 [IDataView 類別](xref:Microsoft.ML.IDataView)作為描述數字或文字表格式資料彈性且有效率的方式。 `IDataView` 可載入文字檔案或即時資料 (例如 SQL 資料庫或記錄檔)。 將下列程式碼新增為 `Train()` 方法的第一行：

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "loading training dataset")]

因為您希望預測計程車的車資，`FareAmount` 資料行便是您將預測的 `Label` (模型的輸出)。請使用 `CopyColumnsEstimator` 轉換類別複製 `FareAmount`，並新增下列程式碼： 

[!code-csharp[CopyColumnsEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Use the CopyColumnsEstimator")]

將模型定型的演算法需要**數值**特徵，因此您需要將類別目錄資料 (`VendorId`、`RateCode` 與 `PaymentType`) 值轉換成數字 (`VendorIdEncoded`、`RateCodeEncoded` 與 `PaymentTypeEncoded`)。 若要進行該操作，請使用 [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) 轉換類別，這會將不同數值索引鍵值指派給每個資料行中的不同值，並新增下列程式碼：

[!code-csharp[OneHotEncodingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Use the OneHotEncodingEstimator")]

資料準備工作的最後一個步驟是使用 `mlContext.Transforms.Concatenate` 轉換類別，將所有特徵資料行合併為 **Features** 資料行。 根據預設，學習演算法只會處理來自 **Features** 資料行的特徵。 加入下列程式碼：

[!code-csharp[ColumnConcatenatingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a>選擇學習演算法

此問題是關於預測紐約市的計程車車資。 乍看之下，這可能看似單純取決於行程遠近。 不過，紐約計程車廠商會針對其他因素 (例如額外的乘客，或使用信用卡而非現金付費) 收取不同的金額。 您希望根據資料集當中的其他因素來預測價格值，這是一個實際值。 為了執行該操作，您選擇[迴歸](../resources/glossary.md#regression)機器學習服務工作。

請將下列內容新增為 `Train()` 中的下一行程式碼，來將 [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) 機器學習服務工作新增到資料轉換定義：

[!code-csharp[FastTreeRegressionTrainer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a>將模型定型

在 `Train()` 方法中新增下列程式碼，調整模型使其符合定型的 `dataview`，並傳回已定型的模型：

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#11 "Train the model")]

[Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) 方法會透過轉換資料集和套用定型來定型模型。

使用 `Train()` 方法中的下列程式碼行，傳回定型的模型：

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a>評估模型

接下來，使用測試資料評估您的模型效能，以進行品質保證和驗證。 在 `Train()` 之後，使用下列程式碼建立 `Evaluate()` 方法：

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

`Evaluate` 方法會執行下列工作：

* 載入測試資料集。
* 建立迴歸評估工具。
* 評估模型並建立計量。
* 顯示計量。

請使用下列程式碼，在緊接著 `Train` 方法呼叫底下，從 `Main` 方法新增對新方法的呼叫：

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Call the Evaluate method")]

使用 [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) 方法載入測試資料集。 透過在 `Evaluate` 方法中新增下列程式碼，使用此資料集作為品質檢查來評估模型：

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Load the test dataset")]

接下來，透過將下列程式碼新增到 `Evaluate()` 來轉換 `Test` 資料：

[!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Predict using the Transformer")]

[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) 方法會針對測試資料集輸入資料列進行預測。

`RegressionContext.Evaluate` 方法會使用指定的資料集來計算 `PredictionModel` 的品質計量。 它傳回的 <xref:Microsoft.ML.Data.RegressionMetrics> 物件包含迴歸評估工具所計算的整體計量。 

若要顯示這些計量以判斷模型的品質，您必須先取得計量。 將下列程式碼加入為 `Evaluate` 方法中的下一行：

[!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Compute Metrics")]

在您設定好預測後，[Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) 方法會評估模型，將預測值與測試資料集中的實際 `Labels` 進行比較，並傳回模型的執行情況。

新增下列程式碼來評估模型並產生評估計量：

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

[RSquared](../resources/glossary.md#coefficient-of-determination) 是迴歸模型的另一個評估計量。 RSquared 接受介於 0 和 1 之間的值。 其值越接近 1，模型就越好。 將下列程式碼新增至 `Evaluate` 方法，以顯示 RSquared 值：

[!code-csharp[DisplayRSquared](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#18 "Display the RSquared metric.")]

[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) 是迴歸模型的評估計量之一。 此計量值越低，模型就越好。 將下列程式碼新增至 `Evaluate` 方法，以顯示 RMS 值：

[!code-csharp[DisplayRMS](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a>使用模型來進行預測

請使用下列程式碼，在緊接著 `Evaluate` 方法之後，建立 `TestSinglePrediction` 方法：

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

`TestSinglePrediction` 方法會執行下列工作：

* 建立測試資料的單一評論。
* 根據測試資料預測費用金額。
* 合併測試資料和預測來進行報告。
* 顯示預測的結果。

請使用下列程式碼，在緊接著 `Evaluate` 方法呼叫底下，從 `Main` 方法新增對新方法的呼叫：

[!code-csharp[CallTestSinglePrediction](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#20 "Call the TestSinglePrediction method")]

將下列程式碼新增到 `TestSinglePrediction()` 來使用 `PredictionEngine` 預測車資：

[!code-csharp[MakePredictionEngine](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#22 "Create the PredictionFunction")]

[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602)是一個方便的 API，可讓您在單一資料實例上執行預測。 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) 不是安全執行緒。 可接受在單一執行緒或原型環境中使用。 為了改善生產環境中的效能和執行緒安全，請使用 `PredictionEnginePool` 服務，這會建立[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)物件的[@no__t 2](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) ，以供整個應用程式使用。 請參閱本指南，以瞭解如何[在 ASP.NET Core WEB API 中使用 `PredictionEnginePool`](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application)

> [!NOTE]
> `PredictionEnginePool` 服務延伸模組目前處於預覽狀態。

本教學課程會使用此類別內的一個測試行程。 您可以稍後新增其他案例來對此方法進行實驗。 透過建立 `TaxiTrip` 的執行個體，在 `TestSinglePrediction()` 方法中新增車程，以測試定型模型的費用預測：

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#23 "Create test data for single prediction")]

接下來，根據計程車車程資料的單一執行個體預測車資，然後透過將下列內容作為 `TestSinglePrediction()` 方法的下一行程式碼，來將它傳遞至 `PredictionEngine`：

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#24 "Create a prediction of taxi fare")]

[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) 函式會在資料的單一執行個體上進行預測。

若要顯示指定之車程的預測費用，請將下列程式碼加入到 `TestSinglePrediction` 方法：

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#25 "Display the prediction.")]

執行程式以查看您測試案例的預測計程車車資。

恭喜您！ 您現在已成功建置可預測計程車車資的機器學習模型、評估了它的準確率，並且也使用它進行了預測。 您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub 存放庫中找到本教學課程的原始程式碼。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您將了解如何：

> [!div class="checklist"]
>
> * 準備並了解資料
> * 建立學習管線
> * 載入並轉換資料
> * 選擇學習演算法
> * 將模型定型
> * 評估模型
> * 使用模型來進行預測

前進到下一個教學課程來深入了解。

> [!div class="nextstepaction"]
> [Iris 叢集](iris-clustering.md)
