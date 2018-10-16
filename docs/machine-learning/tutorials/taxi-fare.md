---
title: 使用 ML.NET 來預測紐約計程車車資 (迴歸)
description: 了解如何在迴歸案例中使用 ML.NET。
author: aditidugar
ms.author: johalex
ms.date: 07/02/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 133b7ad17a98e4eea510f1704555b690b98e9091
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44252840"
---
# <a name="tutorial-use-mlnet-to-predict-new-york-taxi-fares-regression"></a>教學課程：使用 ML.NET 來預測紐約計程車車資 (迴歸)

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

`TaxiTrip` 是輸入資料類別，並含有每個資料集資料行的定義。 請使用 [Column](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) 屬性來指定資料集中來源資料行的索引。

`TaxiTripFarePrediction` 類別代表預測的結果。 包含一個套用 `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) 屬性的單一浮點數欄位 `FareAmount`。 如果是迴歸工作，則**分數**資料行包含預測的標籤值。

> [!NOTE]
> 使用 `float` 型別表示輸入和預測資料類別中的浮點值。

## <a name="define-data-and-model-paths"></a>定義資料和模型路徑

請返回 *Program.cs* 檔案，並新增三個欄位，針對包含資料集的檔案與用來儲存模型的檔案，以保存這些檔案的路徑：

* `_datapath` 會針對具有用來定型模型之資料集的檔案，包含檔案的路徑。
* `_testdatapath` 會針對具有用來評估模型之資料集的檔案，包含檔案的路徑。
* `_modelpath` 會針對儲存定型模型的檔案，包含檔案的路徑。

將下列程式碼加入 `Main` 方法的緊鄰上方，以指定這些路徑：

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

若要將上述的程式碼進行編譯，請在 *Program.cs* 檔案頂端加入下列 `using` 指示詞：

[!code-csharp[AddUsingsForPaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Using statements for path definitions")]

## <a name="create-a-learning-pipeline"></a>建立學習管線

在 *Program.cs* 檔案頂端加入下列額外的 `using` 指示詞：

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

在 `Main` 方法中，以下列程式碼取代 `Console.WriteLine("Hello World!")`：

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

`Train` 方法會將模型定型。 請使用下列程式碼，在緊接著 `Main` 底下建立該方法：

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

學習管線會載入將模型定型所需的所有資料和演算法。 將下列程式碼新增至 `Train` 方法：

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-data"></a>載入並轉換資料

要執行的第一個步驟是從訓練資料集載入資料。 在我們的案例中，定型資料集儲存在具有 `_datapath` 欄位所定義路徑的文字檔中。 這個檔案具有包含資料行名稱的標頭，因此載入資料時應該忽略第一個資料列。 檔案中的資料行是以逗號 (",") 分隔。 將下列程式碼新增至 `Train` 方法：

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(useHeader: true, separator: ','));
```

在接下來的步驟中，我們透過 `TaxiTrip` 類別中定義的名稱來參考資料行。

根據預設，在定型和評估模型時，**Label** 資料行中的值會視為要預測的正確值。 因為我們想要預測計程車行程車資，請將 `FareAmount` 資料行複製到 **Label** 資料行。 若要這樣做，請使用 <xref:Microsoft.ML.Transforms.ColumnCopier>，並新增下列程式碼：

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

將模型定型的演算法需要**數值**特徵，因此您需要將類別目錄資料 (`VendorId`、`RateCode` 及 `PaymentType`) 值轉換成數字。 若要這樣做，請使用 <xref:Microsoft.ML.Transforms.CategoricalOneHotVectorizer>，這會將不同的數值索引鍵值指派給每個資料行中的不同值，並新增下列程式碼：

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

資料準備工作的最後一個步驟是使用 <xref:Microsoft.ML.Transforms.ColumnConcatenator> 轉換類別，將所有特徵資料行合併為 **Features** 資料行。 根據預設，學習演算法只會處理來自 **Features** 資料行的特徵。 加入下列程式碼：

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

請注意，未包含 `TripTime` 資料行，其對應於資料集檔案中的 `trip_time_in_secs` 資料行。 您已經判斷它並非有用的預測特徵。

> [!NOTE]
> 您必須以上述指定的順序將這些步驟新增至管線中，才能成功執行。

## <a name="choose-a-learning-algorithm"></a>選擇學習演算法

將資料新增至管線並將其轉換成正確的輸入格式之後，您需選取學習演算法 (**學習工具**)。 學習工具會將模型定型。 您為這個問題選擇了**迴歸工作**，因此您將使用 <xref:Microsoft.ML.Trainers.FastTreeRegressor> 學習工具，這是 ML.NET 所提供的其中一個迴歸學習工具。

<xref:Microsoft.ML.Trainers.FastTreeRegressor> 學習工具會利用梯度提升。 梯度提升是一種適用於迴歸問題的機器學習技術。 它會以逐步方式建置每個迴歸樹。 它會使用預先定義的損失函式來評估每個步驟中的誤差，然後在下一個步驟中為其進行修正。 結果會產生一個預測模型，這實際上就是較弱預測模型的總體。 如需有關梯度提升的詳細資訊，請參閱[提升的決策樹迴歸](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression) \(英文\)。

將下列程式碼新增至 `Train` 方法中、上一個步驟中新增的資料處理程式碼之後：

```csharp
pipeline.Add(new FastTreeRegressor());
```

您已將上述所有步驟新增至管線中作為個別的陳述式，但 C# 有個便利的集合初始化語法，可讓您更輕鬆地建立管線並將其初始化。 以下列程式碼取代您到目前為止已新增至 `Train` 方法中的程式碼：

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a>將模型定型

最後一個步驟是將模型定型。 到目前為止，尚未執行管線中的任何部分。 `pipeline.Train<TInput, TOutput>` 方法會產生模型，以接受 `TInput` 類型的執行個體，並輸出`TOutput` 類型的執行個體。 將下列程式碼新增至 `Train` 方法：

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

就是這麼容易！ 您已順利將可預測 NYC 中計程車車資的機器學習模型定型。 現在，讓我們來了解模型的準確程度，並了解如何使用它來預測計程車車資值。

### <a name="save-the-model"></a>儲存模型

此時，您已有一個可整合至任何現有或新 .NET 應用程式的模型。 若要將模型儲存至 .zip 檔案，請在 `Train` 方法的結尾新增下列程式碼：

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

將 `await` 陳述式新增至 `model.WriteAsync` 呼叫時，意謂著必須將 `Train` 方法變更為會傳回 Task 的非同步方法。 請修改 `Train`，如以下範例所示：

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

變更 `Train` 方法的傳回類型時，意謂著您必須將 `await` 新增至會呼叫 `Main` 方法中 `Train` 的程式碼，如以下程式碼所示：

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

在 `Main` 方法中使用 `await` 時，意謂著 `Main` 方法必須包含 `async` 修飾詞並傳回 `Task`：

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

您還必須在檔案頂端新增下列 `using` 指示詞：

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

由於 `async Main` 方法是 C# 7.1 中的新增功能，而專案的預設語言版本是 C# 7.0，因此您必須將語言版本變更為 C# 7.1 或更新版本。 若要這樣做，請以滑鼠右鍵按一下 [方案總管] 中的專案節點，然後選取 [屬性]。 選取 [建置] 索引標籤並選取 [進階] 按鈕。 從下拉式清單中，選取 [C# 7.1] (或更新版本)。 選取 [確定] 按鈕。

## <a name="evaluate-the-model"></a>評估模型

評估係指檢查模型預測標籤值之良好程度的程序。 對模型來說，能夠針對其定型時未使用的資料做出良好的預測是相當重要的。 若要達到此目的，其中一個做法是將資料分割成訓練和測試資料集，就像在本教學課程中所做的一樣。 既然您已依據訓練資料來訓練模型，現在即可查看模型對測試資料的表現。

返回 `Main` 方法，然後在 `Train` 方法的呼叫底下，新增下列程式碼：

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

`Evaluate` 方法會評估模型。 若要建立該方法，請在 `Train` 方法底下新增下列程式碼：

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

將下列程式碼新增至 `Evaluate` 方法，來設定測試資料的載入：

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

新增下列程式碼來評估模型並產生評估計量：

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) 是迴歸模型的評估計量之一。 此計量值越低，模型就越好。 將下列程式碼新增至 `Evaluate` 方法，以顯示 RMS 值：

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

[RSquared](../resources/glossary.md#coefficient-of-determination) 是迴歸模型的另一個評估計量。 RSquared 接受介於 0 和 1 之間的值。 其值越接近 1，模型就越好。 將下列程式碼新增至 `Evaluate` 方法，以顯示 RSquared 值：

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a>使用模型來進行預測

建立類型以容納測試資料執行個體：

1. 在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。
1. 在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *TestTrips.cs*。 接著，選取 [新增] 按鈕。
1. 將類別修改成靜態，如以下範例所示：

   [!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

本教學課程會使用此類別內的一個測試行程。 您可以稍後新增其他案例來對此方法進行實驗。 將下列程式碼新增至 `TestTrips` 類別：

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

這個行程的實際車資是 29.5。 請使用 0 作為預留位置，因為此模型將會預測車資。

若要預測指定行程的車資，請返回 *Program.cs* 檔案，然後將下列程式碼新增至 `Main` 方法：

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

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
