---
title: 使用 ML.NET 來預測紐約計程車車資 (迴歸)
description: 了解如何在迴歸案例中使用 ML.NET。
author: aditidugar
ms.author: johalex
ms.date: 06/05/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 048ed1d38408c1ba4901c554cae33d5552c9e303
ms.sourcegitcommit: 5b0802832fb9ad684d34e69b8644a16a5b7c4810
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2018
ms.locfileid: "34860643"
---
# <a name="tutorial-use-mlnet-to-predict-new-york-taxi-fares-regression"></a>教學課程：使用 ML.NET 來預測紐約計程車車資 (迴歸)

> [!NOTE]
> 本主題參考 ML.NET，此功能目前為公開預覽版，而可能會有變更。 如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) \(英文)\。

本教學課程說明如何使用 ML.NET 來建置用於預測紐約市計程車車資的 [迴歸模型](../resources/glossary.md#regression)。

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> * 了解問題
> * 選取適當的機器學習工作
> * 準備並了解您的資料
> * 建立學習管線
> * 載入並轉換您的資料
> * 選擇學習演算法
> * 將模型定型
> * 評估模型
> * 使用模型來進行預測

## <a name="prerequisites"></a>必要條件

* 已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)。

## <a name="understand-the-problem"></a>了解問題

此問題的焦點在於**預測紐約市計程車的車資**。 乍看之下，這可能看似單純取決於行程遠近。 不過，紐約計程車廠商會針對其他因素 (例如額外的乘客，或使用信用卡而非現金付費) 收取不同的金額。

## <a name="select-the-appropriate-machine-learning-task"></a>選取適當的機器學習工作

若要預測計程車車資，您需先選取適當的機器學習工作。 您希望根據資料集內的其他因素來預測實際值 (一個代表價格的雙精度浮點數)。 您需選擇[**迴歸**](../resources/glossary.md#regression)工作。

模型的定型程序會識別資料集內的哪些因素，在預測最終車資價格時最具影響力。

## <a name="create-a-console-application"></a>建立主控台應用程式

1. 開啟 Visual Studio 2017。 從功能表列中選取 [檔案]  >  [新增]  >  [專案]。 在 [新增專案] 對話方塊中，選取 [Visual C#] 節點，然後選取 [.NET Core] 節點。 然後選取 [主控台應用程式 (.NET Core)] 專案範本。 在 [名稱] 文字方塊中，輸入 "TaxiFarePrediction"，然後選取 [確定] 按鈕。

2. 在您的專案中建立一個名為 *Data* 的目錄以儲存資料集檔案：

    在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [新增] > [新增資料夾]。 輸入 "Data"，然後按 Enter。

3. 安裝「Microsoft.ML NuGet 套件」：

    在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。 選擇 "nuget.org" 作為 [套件來源]，選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。 在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。

### <a name="prepare-and-understand-your-data"></a>準備並了解您的資料

1. 下載 [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) 和 [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) 資料集，並將它們儲存至先前建立的 [Data] 資料夾。 Taxi Trip 資料集會將機器學習模型定型，並可用來評估您模型的準確率。 這些資料集原先來自 [NYC TLC Taxi Trip 資料集](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)。

2. 在 [方案總管] 中，於每個 \*.csv 檔案上按一下滑鼠右鍵，然後選取 [屬性]。 在 [進階] 底下，將 [複製到輸出目錄]的值變更為 [永遠]。

3. 在程式碼編輯器中開啟 **taxi-fare-train.csv** 資料集，然後查看第一個資料列中的資料行標頭。 請查看每個資料行。 了解資料並判斷哪些資料行是**特徵**，以及哪個是**標籤**。

**標籤**是您嘗試預測之資料行的識別碼。 所識別的**特徵**會用來預測標籤。

* **vendor_id：** 計程車廠商的識別碼是一項特徵。
* **rate_code：** 計程車行程的費率類型是一項特徵。
* **passenger_count：** 行程的乘客數目是一項特徵。
* **trip_time_in_secs：** 行程所花費的時間長度。 您將必須等到行程完成之後，才能知道行程所花費的時間長度。 您需將此資料行從模型中排除。
* **trip_distance：** 行程的距離是一項特徵。
* **payment_type：** 付款方式 (現金或信用卡) 是一項特徵。
* **fare_amount：** 計程車車資總計是標籤。

### <a name="create-classes-and-define-paths"></a>建立類別及定義路徑

在 *Program.cs* 檔案頂端新增下列額外的 `using` 陳述式：

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

您必須建立三個全域變數，以保存最近所下載檔案及儲存模型的路徑：

* `_datapath` 包含用來將模型定型的資料集路徑。
* `_testdatapath` 包含用來評估模型的資料集路徑。
* `_modelpath` 包含用來儲存定型模型的路徑。

將下列程式碼新增至緊接在 `Main` 上方的一行，以指定最近下載的檔案：

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

接著，為輸入資料和預測建立類別：

1. 在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。
1. 在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *TaxiTrip.cs*。 接著，選取 [新增] 按鈕。
1. 將下列 `using` 陳述式新增至新的檔案：

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

移除現有的類別定義，然後將下列程式碼 (具有 `TaxiTrip` 和 `TaxiTripFarePrediction` 這兩個類別) 新增至 *TaxiTrip.cs* 檔案：

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

`TaxiTrip` 是輸入資料集類別，並含有每個資料集資料行的定義。 `TaxiTripFarePrediction` 類別會在模型定型後，用來進行預測。 它包含一個單一浮點數 (`FareAmount`) 和一個套用的 `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) 屬性。

現在，請返回 **Program.cs** 檔案。 在 `Main` 中，以下列程式碼取代 `Console.WriteLine("Hello World!")`：

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

`Train` 方法會將您的模型定型。 請使用下列程式碼，在緊接著 `Main` 底下，建立該函式：

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

## <a name="create-a-learning-pipeline"></a>建立學習管線

學習管線會載入將模型定型所需的所有資料和演算法。 將下列程式碼新增至 `Train()` 方法：

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-your-data"></a>載入並轉換您的資料

接著，將您的資料載入管線。 指向一開始建立的 `_datapath`，並指定 .csv file 的分隔符號 (,)。 將下列程式碼新增至 `Train()` 方法中、上一個步驟底下：

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(separator:','));
```

您將在要建立的程式碼中，以不使用底線的方式參考資料行。 請使用 `ColumnCopier()` 函式將 `FareAmount` 資料行複製到名為 "Label" 的新資料行中。 此資料行就是**標籤**。

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

請進行一些**特徵工程**來轉換資料，以便能夠有效地使用此資料來進行機器學習。 將模型定型的演算法需要**數值**特徵，您需將類別目錄資料 (`VendorId`、`RateCode` 及 `PaymentType`) 轉換成數字。 `CategoricalOneHotVectorizer()` 函式會將數值索引鍵指派給這每個資料行中的值。 請新增下列程式碼來轉換您的資料：

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

資料準備的最後一個步驟會使用 `ColumnConcatenator()` 函式，將您的所有**特徵**合併成一個向量。 這個必要步驟可協助演算法輕鬆處理您的特徵。 加入下列程式碼：

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

請注意，`trip_time_in_secs` 資料行並未包含在內。 您已經判斷它並非有用的預測特徵。

> [!NOTE]
> 您必須以上述指定的順序將這些步驟新增至管線中，才能成功執行。

## <a name="choose-a-learning-algorithm"></a>選擇學習演算法

將資料新增至管線並將其轉換成正確的輸入格式之後，您需選取學習演算法 (**學習工具**)。 學習演算法會將模型定型。 針對此問題，您需選取**迴歸工作**，因此會將名為 `FastTreeRegressor()` 的學習工具新增至運用**梯度提升** (Gradient Boosting) 的管線。

梯度提升是一種適用於迴歸問題的機器學習技術。 它會以逐步方式建置每個迴歸樹。 它會使用預先定義的損失函式來評估每個步驟中的誤差，然後在下一個步驟中為其進行修正。 結果會產生一個預測模型，這實際上就是較弱預測模型的總體。 如需有關梯度提升的詳細資訊，請參閱[提升的決策樹迴歸](https://docs.microsoft.com/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression) \(英文\)。

將下列程式碼新增至 `Train()` 方法中、上一個步驟中新增的資料處理程式碼之後：

```csharp
pipeline.Add(new FastTreeRegressor());
```

您已將上述所有步驟新增至管線中作為個別的陳述式，但 C# 有個便利的集合初始化語法，可讓您更輕鬆地建立管線並將其初始化。 以下列程式碼取代您到目前為止已新增至 `Train()` 方法中的程式碼：

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a>將模型定型

最後一個步驟是將模型定型。 到目前為止，尚未執行管線中的任何部分。 `pipeline.Train<T_Input, T_Output>()` 函式會採用預先定義的 `TaxiTrip` 類別類型，然後輸出 `TaxiTripFarePrediction` 類型。 將這最後一段程式碼新增至 `Train()` 函式：

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

就是這麼容易！ 您已順利將可預測 NYC 中計程車車資的機器學習模型定型。 現在，請研究一下來了解您模型的準確率，以及模型的使用方式。

## <a name="save-the-model"></a>儲存模型

在您前進到下一個步驟之前，請先在 `Train()` 函式的結尾新增下列程式碼，來將模型儲存成 .zip 檔案：

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

將 `await` 陳述式新增至 `model.WriteAsync()` 呼叫時，意謂著必須將 `Train()` 方法變更為會傳回 `Task` 的非同步方法。 請修改 `Train`，如以下範例所示：

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

變更 `Train` 方法的傳回類型時，意謂著您必須將 `await` 新增至會呼叫 `Main` 方法中 `Train` 的程式碼，如以下程式碼所示：

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

在 `Main` 方法中新增 `await` 時，意謂著 `Main` 方法必須包含 `async` 修飾詞並傳回 `Task`：

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

您還必須在檔案頂端新增下列 using 陳述式：

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

由於 `async Main` 方法是 C# 7.1 中的新功能，而專案的預設語言版本是 C# 7.0，因此您必須將語言版本變更為 C# 7.1 或更新版本。
若要這樣做，請在 [方案總管] 中的專案節點上按一下滑鼠右鍵，然後選取 [屬性]。 選取 [建置] 索引標籤並選取 [進階] 按鈕。 從下拉式清單中，選取 [C# 7.1] (或更新版本)。 選取 [確定] 按鈕。

## <a name="evaluate-the-model"></a>評估模型

評估係指檢查模型運作情況良好程度的程序。 對模型來說，能夠針對在其定型時未使用的資料做出良好的預測，是相當重要的。 若要達到此目的，其中一個做法是將資料分割成定型和測試資料集，就像您在本教學課程中所做的一樣。 既然您已依據定型資料將模型定型，現在即可查看模型對測試資料的表現。

返回您的 `Main` 函式，然後在對 `Train()` 方法的呼叫底下，新增下列程式碼：

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

`Evaluate()` 函式會評估您的模型。 請在 `Train()` 底下建立該函式。 加入下列程式碼：

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

使用 `TextLoader()` 函式來載入測試資料。 將下列程式碼新增至 `Evaluate()` 方法：

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

新增下列程式碼來評估模型並為其產生計量：

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

RMS 是一個用於評估迴歸問題的計量。 此計量值越低，您的模型就越好。 將下列程式碼新增至 `Evaluate()` 函式以顯示模型的 RMS。

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

RSquared 是另一個用於評估迴歸問題的計量。 RSquared 會是介於 0 到 1 之間的值。 越接近 1，您的模型就越好。 將下列程式碼新增至 `Evaluate()` 函式以顯示模型的 RSquared 值。

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a>使用模型來進行預測

接著，建立一個類別來裝載可用來確定模型是否正確運作的測試案例：

1. 在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。
1. 在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *TestTrips.cs*。 接著，選取 [新增] 按鈕。
1. 將類別修改成靜態，如以下範例所示：

[!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

本教學課程會使用此類別內的一個測試行程。 您可以稍後新增其他案例來對此範例進行實驗。 將下列程式碼新增至 `TestTrips` 類別：

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

這個行程的實際車資是 29.5，但使用 0 作為預留位置。 機器學習演算法將會預測車資。

在 `Main` 函式中新增下列程式碼。 它會使用 `TestTrip` 資料來檢驗您的模型：

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

執行程式以查看您測試案例的預測計程車車資。

恭喜您！ 您現在已成功建置可預測計程車車資的機器學習模型、評估了它的準確率，並且也對它進行了測試。 您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) 存放庫中找到本教學課程的原始程式碼。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> * 了解問題
> * 選取適當的機器學習工作
> * 準備並了解您的資料
> * 建立學習管線
> * 載入並轉換您的資料
> * 選擇學習演算法
> * 將模型定型
> * 評估模型
> * 使用模型來進行預測

請查看我們的 GitHub 存放庫來繼續學習及尋找更多範例。
> [!div class="nextstepaction"]
> [dotnet/machinelearning GitHub 存放庫](https://github.com/dotnet/machinelearning/)
