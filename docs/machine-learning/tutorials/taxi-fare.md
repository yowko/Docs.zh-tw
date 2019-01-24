---
title: 透過 ML.NET 使用迴歸學習工具預測紐約計程車費用
description: 透過 ML.NET 使用迴歸學習工具預測費用。
author: aditidugar
ms.author: johalex
ms.date: 01/15/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: b17b4e31a60d6eaf432577281004bcf2c7ca1da2
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333781"
---
# <a name="tutorial-predict-new-york-taxi-fares-using-a-regression-learner-with-mlnet"></a>教學課程：透過 ML.NET 使用迴歸學習工具預測紐約計程車費用

> [!NOTE]
> 本主題涉及 ML.NET，此功能目前為公開預覽版，因此内容可能會有變更。 如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) \(英文)。

本教學課程說明如何使用 ML.NET 來建置用於預測紐約市計程車車資的 [迴歸模型](../resources/glossary.md#regression)。

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> * 了解問題
> * 選取適當的機器學習工作
> * 準備並了解資料
> * 建立學習管線
> * 載入並轉換資料
> * 選擇學習演算法
> * 將模型定型
> * 評估模型
> * 使用模型來進行預測

## <a name="prerequisites"></a>必要條件

* 已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)。

## <a name="understand-the-problem"></a>了解問題

此問題是關於預測紐約市計程車的車資。 乍看之下，這可能看似單純取決於行程遠近。 不過，紐約計程車廠商會針對其他因素 (例如額外的乘客，或使用信用卡而非現金付費) 收取不同的金額。

## <a name="select-the-appropriate-machine-learning-task"></a>選取適當的機器學習工作

您希望根據資料集當中的其他因素來預測價格值，這是一個實際值。 為了這麼做，您選擇[迴歸](../resources/glossary.md#regression)機器學習工作。

## <a name="create-a-console-application"></a>建立主控台應用程式

1. 開啟 Visual Studio 2017。 從功能表列中選取 [檔案]  >  [新增]  >  [專案]。 在 [新增專案] 對話方塊中，選取 [Visual C#] 節點，然後選取 [.NET Core] 節點。 然後選取 [主控台應用程式 (.NET Core)] 專案範本。 在 [名稱] 文字方塊中，輸入 "TaxiFarePrediction"，然後選取 [確定] 按鈕。

1. 在您的專案中建立一個名為 *Data* 的目錄以儲存資料集和模型檔案：

    在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取 [新增] > [新增資料夾]。 輸入 "Data"，然後按 Enter。

1. 安裝 **Microsoft.ML** NuGet 套件：

    在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取 [管理 NuGet 套件]。 選擇 "nuget.org" 作為 [套件來源]，選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。 在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。

## <a name="prepare-and-understand-the-data"></a>準備並了解資料

1. 下載 [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) 和 [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) 資料集，並將它們儲存至您在上一個步驟所建立的 *Data* 資料夾。 我們可以使用這些資料集將機器學習模型定型，然後評估模型的準確程度。 這些資料集原先來自 [NYC TLC Taxi Trip 資料集](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)。

1. 在 [方案總管] 中，以滑鼠右鍵按一下每個 \*.csv 檔案，然後選取 [屬性]。 在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。

1. 開啟 **taxi-fare-train.csv** 資料集，然後查看第一個資料列中的資料行標頭。 請查看每個資料行。 了解資料，並決定哪些資料行是 **features**，以及哪一個資料行是 **label**。

**label** 是您要預測之資料行的識別碼。 所識別的**特徵**會用來預測標籤。

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

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

移除現有的類別定義，然後將下列程式碼 (具有 `TaxiTrip` 和 `TaxiTripFarePrediction` 這兩個類別) 新增至 *TaxiTrip.cs* 檔案：

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip` 是輸入資料類別，並含有每個資料集資料行的定義。 使用 <xref:Microsoft.ML.Data.ColumnAttribute> 屬性來指定資料集中來源資料行的索引。

`TaxiTripFarePrediction` 類別代表預測的結果。 包含一個套用 `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> 屬性的單一浮點數欄位 `FareAmount`。 如果是迴歸工作，則**分數**資料行包含預測的標籤值。

> [!NOTE]
> 使用 `float` 型別表示輸入和預測資料類別中的浮點值。

## <a name="define-data-and-model-paths"></a>定義資料和模型路徑

在 *Program.cs* 檔案頂端新增下列額外的 `using` 陳述式：

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

您必須建立三個欄位，保存含有資料集的檔案與用來儲存模型之檔案的檔案路徑，以及 `TextLoader` 的全域變數：

* `_trainDataPath` 會針對具有用來定型模型之資料集的檔案，包含檔案的路徑。
* `_testDataPath` 會針對具有用來評估模型之資料集的檔案，包含檔案的路徑。
* `_modelPath` 會針對儲存定型模型的檔案，包含檔案的路徑。
* `_textLoader` 是 <xref:Microsoft.ML.Data.TextLoader>，用來載入並轉換資料集。

將下列程式碼加入至緊接在 `Main` 方法上方，以指定這些路徑和 `_textLoader` 變數：

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

使用 ML.NET 建置模型時，您要從建立 ML 內容開始。 這在概念上類似於在 Entity Framework 中使用 `DbContext`。 環境為機器學習作業提供的內容，可用來進行例外狀況追蹤和記錄。

### <a name="initialize-variables-in-main"></a>在 Main 中初始化變數

建立名為 `mlContext` 的變數，並使用 `MLContext` 的新執行個體將它初始化。  在 `Main` 方法中，以下列程式碼取代 `Console.WriteLine("Hello World!")`：

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create the ML Context")]

接下來，為了設定資料載入，將 `_textLoader` 全域變數初始化以重複使用它。  請注意我們使用 `TextReader`。 當您使用 `TextReader` 建立 `TextLoader` 時，您要傳入需要的內容和可自訂的 <xref:Microsoft.ML.Data.TextLoader.Arguments> 類別。 透過將 <xref:Microsoft.ML.Data.TextLoader.Column> 物件的陣列傳遞至包含所有資料行名稱及其類別的 `TextReader`，來指定資料結構描述。 我們已在先前建立 `TaxiTrip` 類別時定義了結構描述。

`TextReader` 類別會傳回完整初始化的 <xref:Microsoft.ML.Data.TextLoader>  

若要初始化 `_textLoader` 全域變數以針對需要的資料集重複使用它，請在 `mlContext` 初始化之後加入下列程式碼：

[!code-csharp[initTextLoader](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Initialize the TextLoader")]

將下列內容加入為 `Main` 方法中的下一行程式碼，來呼叫 `Train` 方法：

[!code-csharp[Train](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Train your model")]

`Train` 方法會執行下列工作：

* 載入資料。
* 擷取並轉換資料。
* 將模型定型。
* 將模型儲存為 .zip 檔案。
* 傳回模型。

`Train` 方法會將模型定型。 請使用下列程式碼，在緊接著 `Main` 底下建立該方法：

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

我們將兩個參數傳遞到 `Train` 方法：內容 (`mlContext`) 的 `MLContext`，和資料集路徑 (`dataPath`) 的字串。 我們將重複使用此方法來載入資料集。

## <a name="load-and-transform-data"></a>載入並轉換資料

我們將使用 `_textLoader` 全域變數搭配 `dataPath` 參數載入資料。 它會傳回 <xref:Microsoft.ML.Data.IDataView>。 作為轉換的輸入和輸出，`DataView` 是基本的資料管線類型，相當於 `LINQ` 的 `IEnumerable`。

在 ML.NET 中，資料相當於 SQL 檢視。 它是延遲評估、結構描述化且異質性的。 物件是管線的第一個部分，並且會載入資料。 在本教學課程中，它會載入具有計程車車程資訊的實用資料集來預測費用。 這會用來建立模型，並將模型定型。

 將下列程式碼新增為 `Train` 方法的第一行：

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "loading training dataset")]

在接下來的步驟中，我們透過 `TaxiTrip` 類別中定義的名稱來參考資料行。

根據預設，在定型和評估模型時，**Label** 資料行中的值會視為要預測的正確值。 因為我們想要預測計程車行程車資，請將 `FareAmount` 資料行複製到 **Label** 資料行。 若要這樣做，請使用 `CopyColumnsEstimator` 轉換類別，並加入下列程式碼：

[!code-csharp[CopyColumnsEstimator](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Use the CopyColumnsEstimator")]

將模型定型的演算法需要**數值**特徵，因此您需要將類別目錄資料 (`VendorId`、`RateCode` 及 `PaymentType`) 值轉換成數字。 若要這樣做，請使用 `OneHotEncodingEstimator` 轉換類別，這會將不同的數值索引鍵值指派給每個資料行中的不同值，並新增下列程式碼：

[!code-csharp[OneHotEncodingEstimator](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Use the OneHotEncodingEstimator")]

資料準備工作的最後一個步驟是使用 `ColumnConcatenatingEstimator` 轉換類別，將所有特徵資料行合併為 **Features** 資料行。 根據預設，學習演算法只會處理來自 **Features** 資料行的特徵。 加入下列程式碼：

[!code-csharp[ColumnConcatenatingEstimator](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a>選擇學習演算法

將資料新增至管線並將其轉換成正確的輸入格式之後，我們需選取學習演算法 (**學習工具**)。 學習工具會將模型定型。 我們為這個問題選擇了**迴歸**工作，因此我們將使用 `FastTreeRegressionTrainer` 學習工具，這是 ML.NET 所提供的其中一個迴歸學習工具。

`FastTreeRegressionTrainer` 學習工具會利用梯度提升。 梯度提升是一種適用於迴歸問題的機器學習技術。 它會以逐步方式建置每個迴歸樹。 它會使用預先定義的損失函式來評估每個步驟中的誤差，然後在下一個步驟中為其進行修正。 結果會產生一個預測模型，這實際上就是較弱預測模型的總體。 如需有關梯度提升的詳細資訊，請參閱[提升的決策樹迴歸](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression) \(英文\)。

將下列程式碼加入至 `Train` 方法中以將 `FastTreeRegressionTrainer` 加入到上一個步驟中加入的資料處理程式碼：

[!code-csharp[FastTreeRegressionTrainer](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a>將模型定型

最後一個步驟是將模型定型。 我們會根據已載入和轉換的資料集將模型 <xref:Microsoft.ML.Data.TransformerChain> 定型。 一旦定義了評估工具之後，我們使用 <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> 定型模型，並提供已載入的定型資料。 這會傳回要用於預測的模型。 `pipeline.Fit()` 會定型管線，並根據傳入的 `DataView` 傳回 `Transformer`。 實驗會等到定型之後才會執行。

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#11 "Train the model")]

就是這麼容易！ 您已順利將可預測 NYC 中計程車車資的機器學習模型定型。 現在，讓我們來了解模型的準確程度，並了解如何使用它來預測計程車車資值。

### <a name="save-the-model"></a>儲存模型

此時，您已有一個可整合至任何現有或新 .NET 應用程式之 <xref:Microsoft.ML.Data.TransformerChain> 類型的模型。 若要將模型儲存至 .zip 檔案，請在 `Train` 方法的結尾新增下列程式碼：

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Save the model as a .zip file and return the model")]

## <a name="save-the-model-as-a-zip-file"></a>將模型儲存為 .zip 檔案

請使用下列程式碼，在緊接著 `Train` 方法之後，建立 `SaveModelAsFile` 方法：

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

`SaveModelAsFile` 方法會執行下列工作：

* 將模型儲存為 .zip 檔案。

我們需要建立儲存模型的方法，以便在其他應用程式中重複使用。 `ITransformer` 具有 <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> 方法，它會採用 `_modelPath` 全域欄位和 <xref:System.IO.Stream>。 因為我們想要將此儲存為 ZIP 檔案，我們將建立 `FileStream`，緊接著呼叫 `SaveTo` 方法。 將下列程式碼加入為 `SaveModelAsFile` 方法中的下一行：

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Add the SaveTo Method")]

我們可以搭配 `_modelPath` 使用下列程式碼撰寫主控台訊息，來顯示檔案寫入的位置：

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="evaluate-the-model"></a>評估模型

評估係指檢查模型預測標籤值之良好程度的程序。 對模型來說，能夠針對其定型時未使用的資料做出良好的預測是相當重要的。 若要達到此目的，其中一個做法是將資料分割成訓練和測試資料集，就像在本教學課程中所做的一樣。 既然您已依據訓練資料來訓練模型，現在即可查看模型對測試資料的表現。

`Evaluate` 方法會評估模型。 若要建立該方法，請在 `Train` 方法底下新增下列程式碼：

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

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Call the Evaluate method")]

我們將使用先前已初始化的 `_textLoader` 全域變數與 `_testDataPath` 全域欄位來載入測試資料集。 您可以使用此資料集來評估模型，以作為品質檢查。 將下列程式碼加入 `Evaluate` 方法：

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Load the test dataset")]

接下來，我們將使用機器學習 `model` 參數 (轉換器) 來輸入特徵並傳回預測。 將下列程式碼加入為 `Evaluate` 方法中的下一行：

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Predict using the Transformer")]

`RegressionContext.Evaluate` 方法會使用指定的資料集來計算 `PredictionModel` 的品質計量。 它傳回的 <xref:Microsoft.ML.Data.RegressionMetrics> 物件包含迴歸評估工具所計算的整體計量。 若要顯示這些計量以判斷模型的品質，您必須先取得計量。 將下列程式碼加入為 `Evaluate` 方法中的下一行：

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Compute Metrics")]

新增下列程式碼來評估模型並產生評估計量：

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

[RSquared](../resources/glossary.md#coefficient-of-determination) 是迴歸模型的另一個評估計量。 RSquared 接受介於 0 和 1 之間的值。 其值越接近 1，模型就越好。 將下列程式碼新增至 `Evaluate` 方法，以顯示 RSquared 值：

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#18 "Display the RSquared metric.")]

[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) 是迴歸模型的評估計量之一。 此計量值越低，模型就越好。 將下列程式碼新增至 `Evaluate` 方法，以顯示 RMS 值：

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a>使用模型來進行預測


## <a name="predict-the-test-data-outcome-with-the-model-and-a-single-comment"></a>使用模型和單一評論來預測測試資料結果

請使用下列程式碼，在緊接著 `Evaluate` 方法之後，建立 `TestSinglePrediction` 方法：

```csharp
private static void TestSinglePrediction(MLContext mlContext)
{

}
```

`TestSinglePrediction` 方法會執行下列工作：

* 建立測試資料的單一評論。
* 根據測試資料預測費用金額。
* 合併測試資料和預測來進行報告。
* 顯示預測的結果。

請使用下列程式碼，在緊接著 `Evaluate` 方法呼叫底下，從 `Main` 方法新增對新方法的呼叫：

[!code-csharp[CallTestSinglePrediction](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#20 "Call the TestSinglePrediction method")]

因為我們想要從已儲存的 ZIP 檔案載入模型，我們要建立 `FileStream`，緊接著呼叫 `Load` 方法。 將下列程式碼加入為 `TestSinglePrediction` 方法中的下一行：

[!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#21 "Load the model")]

雖然 `model` 是可在多個資料列上運作的 `transformer`，但常見的生產環境案例需要根據個別範例進行預測。 <xref:Microsoft.ML.PredictionEngine%602> 是從 `CreatePredictionEngine` 方法傳回的包裝函式。 讓我們在 `Predict` 方法中的第一行加入下列程式碼，來建立 `PredictionEngine`：

[!code-csharp[MakePredictionEngine](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#22 "Create the PredictionFunction")]
  
本教學課程會使用此類別內的一個測試行程。 您可以稍後新增其他案例來對此方法進行實驗。 透過建立 `TaxiTrip` 的執行個體，在 `Predict` 方法中新增車程，以測試定型模型的費用預測：

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#23 "Create test data for single prediction")]

 我們可以使用它來根據計程車車程資料的單一執行個體預測費用。 若要取得預測，請在資料上使用 <xref:Microsoft.ML.PredictionEngine%602.Predict%2A>。 請注意，輸入資料是一個字串，且模型包含特徵化。 在定型和預測期間，您的管線會同步。 您無須特別為預測撰寫前處理/特徵化程式碼，同一個 API 會同時負責批次和單次預測。

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#24 "Create a prediction of taxi fare")]

若要顯示指定之車程的預測費用，請將下列程式碼加入到 `Main` 方法：

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#25 "Display the prediction.")]

執行程式以查看您測試案例的預測計程車車資。

恭喜您！ 您現在已成功建置可預測計程車車資的機器學習模型、評估了它的準確率，並且也使用它進行了預測。 您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub 存放庫中找到本教學課程的原始程式碼。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> * 了解問題
> * 選取適當的機器學習工作
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
