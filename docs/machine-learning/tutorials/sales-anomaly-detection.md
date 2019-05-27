---
title: 在銷售異常偵測案例中使用 ML.NET
description: 探索如何在產品銷售異常偵測案例中使用 ML.NET，以了解如何分析異常暴增及變更點的資料，採取適當的動作。
ms.date: 05/06/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 39e812facccfa75d1643704f8960a387a70c94bc
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641137"
---
# <a name="tutorial-use-mlnet-for-product-sales-anomaly-detection"></a>教學課程：使用 ML.NET 處理產品銷售異常偵測 

此範例教學課程示範使用 ML.NET 偵測產品銷售資料的異常，在 Visual Studio 2019 使用 C#，透過 .NET Core 主控台應用程式採取適當的動作。 

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> * 載入資料
> * 定型尖峰異常偵測的模型
> * 使用定型的模型偵測尖峰異常
> * 定型變更點異常偵測的模型
> * 使用定型的模型偵測變更點異常

您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) 存放庫中找到本教學課程的原始程式碼。

## <a name="prerequisites"></a>必要條件

* 已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。

* [product-sales.csv 資料集](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> `product-sales.csv` 中的資料格式是以 “Shampoo Sales Over a Three Year Period” (洗髮精三年銷售資料) 資料集為基礎，此資料集最初源自 DataMarket，由時間序列資料程式庫 (TSDL) 提供，建立者為 Rob Hyndman。 “Shampoo Sales Over a Three Year Period” (洗髮精三年銷售資料) 資料集已獲 DataMarket 的預設 Open License 授權。

## <a name="create-a-console-application"></a>建立主控台應用程式

1. 建立稱為 "ProductSalesAnomalyDetection" 的 **.NET Core 主控台應用程式**。

2. 在您專案中建立名為 *Data* 的目錄以儲存資料集檔案。

3. 安裝「Microsoft.ML NuGet 套件」：

    在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。 選擇 "nuget.org" 作為 [套件來源]、選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、從清單中選取 **v1.0.0** 套件，然後選取 [安裝] 按鈕。 在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。 為 **Microsoft.ML.TimeSeries v0.12.0** 重複這些步驟。

4. 在您的 *Program.cs* 檔案最上方新增下列 `using` 陳述式：

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a>下載您的資料

1. 下載資料集，並儲存至您先前建立的 *Data* 資料夾：

   * 以滑鼠右鍵按一下 [*product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)，然後選取 [另存連結] 或 [另存目標]

     請務必將 \*.csv 檔案儲存至 *Data* 資料夾，或儲存在其他位置之後將 \*.csv 檔案移至 *Data* 資料夾。

2. 在 [方案總管] 中，以滑鼠右鍵按一下 \*.csv 檔案，並選取 [內容]。 在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。

下表是 \*.csv 檔案的資料預覽：

|月份  |ProductSales |
|-------|-------------|
|1 月 1 日  |    271      |
|1 月 2 日  |    150.9    |
|.....  |    .....    |
|2 月 1 日  |    199.3    |
|.....  |    .....    |

### <a name="create-classes-and-define-paths"></a>建立類別及定義路徑

接下來，定義您的輸入類別資料結構。

將新類別新增至專案：

1. 在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取 [新增] > [新項目]。

2. 在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *ProductSalesData.cs*。 接著，選取 [新增] 按鈕。

隨即在程式碼編輯器中開啟 *ProductSalesData.cs* 檔案。 將下列 `using` 陳述式新增至 *ProductSalesData.cs* 的上方：

```csharp
using Microsoft.ML.Data;
```

移除現有類別定義，然後將下列具有 `ProductSalesData` 和 `ProductSalesPrediction` 兩個類別的程式碼新增至 *ProductSalesData.cs* 檔案：

[!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/ProductSalesData.cs#DeclareTypes "Declare data record types")]

`ProductSalesData` 會指定輸入資料類別。 [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) 屬性會指定應該載入資料集內的哪些資料行 (依資料行索引)。 

在 *Program.cs* 檔案頂端新增下列額外的 `using` 陳述式：

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

您必須建立兩個全域欄位，以保存最近所下載的資料集檔案路徑與儲存的模型檔案路徑：

* `_dataPath` 包含用來將模型定型的資料集路徑。
* `_docsize` 有資料集檔案的記錄數目。 您會用此計算 `pvalueHistoryLength`。

將下列程式碼新增至緊接在 `Main` 方法上方的一行，以指定這些路徑：

[!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DeclareGlobalVariables "Declare global variables")]

[MLContext 類別](xref:Microsoft.ML.MLContext)是所有 ML.NET 作業的起點，且初始化 `mlContext` 會建立新的 ML.NET 環境，其可在模型建立工作流程物件之間共用。 就概念而言，類似於 Entity Framework 中的 `DBContext`。

### <a name="initialize-variables-in-main"></a>在 Main 中初始化變數

將 `Main` 方法中的 `Console.WriteLine("Hello World!")` 程式碼替換成下列程式碼，宣告並初始化 `mlContext` 變數：

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateMLContext "Create the ML Context")]

### <a name="load-the-data"></a>載入資料

ML.NET 中的資料以 [IDataView 類別](xref:Microsoft.ML.IDataView) 表示。 `IDataView` 是彈性且有效率的表格式資料描述方式 (數值和文字)。 資料可以從文字或即時 (例如 SQL 資料庫或記錄檔) 載入至 `IDataView` 物件。 將下列程式碼新增為 `Main()` 方法的下一行：

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#LoadData "loading dataset")]

[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) 會定義資料結構描述並讀入檔案中。 會接受資料路徑變數然後傳回 `IDataView`。

## <a name="ml-task---time-series-anomaly-detection"></a>ML 工作 - 時間序列異常偵測 

異常偵測會標記未預期或不尋常的事件或行為。 它可提供尋找問題的線索，協助您回答「這奇不奇怪？」的問題。

![奇不奇怪](./media/sales-anomaly-detection/anomalydetection.png)

異常偵測是偵測時間序列資料極端值的程序，它們是指定輸入時間序列中非預期或「奇怪」行為的資料點。

這在很多方面都很有用。 若是執行個體：

如果您有一輛汽車，您可能想知道：油量表的讀數是否正常，還是漏油了？
如果您要監視的耗電量，您可能想知道：是否斷電？

可偵測到的時間序列異常有兩種： 

* **尖峰**表示系統中異常行為的暫時高載。 

* **變更點**表示系統開頭的持續性隨著時間變更。 

在 ML.NET 中，IID 尖峰偵測或 IID 變更點偵測演算法都很適合[獨立同分布資料集](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables)。 

您要分析相同的產品銷售資料，偵測尖峰和變更點。 尖峰偵測和變更點偵測的建置與定型模型程序相同，主要差異在於使用的特定偵測演算法。

## <a name="spike-detection"></a>尖峰偵測 

尖峰偵測目標是找出明顯有別於大部分時間序列資料值的突然卻短暫暴增。 請務必及時偵測這些可疑的罕見項目、事件或觀測，將影響降至最低。 下列方法可用來偵測各種異常，例如：中斷、網路攻擊或病毒式 Web 內容。 下圖是時間序列資料集的尖峰範例：

![SpikeDetection](./media/sales-anomaly-detection/SpikeDetection.png)

### <a name="create-the-detectspike-method"></a>建立 DetectSpike() 方法

將下列呼叫新增至 `DetectSpike()` 方法作為 `Main()` 方法中的下一行程式碼：

[!code-csharp[CallDetectSpike](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectSpike)]

`DetectSpike()` 方法會執行下列工作：

* 將模型定型。
* 根據歷史銷售資料偵測尖峰。
* 顯示結果。

請使用下列程式碼，在緊接著 `Main()` 方法之後，建立 `DetectSpike()` 方法：

```csharp
static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

使用 [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) 定型偵測尖峰的模型。 使用下列程式碼將它新增至 `DetectChangepoint()` 方法：

[!code-csharp[AddSpikeTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddSpikeTrainer)]

將下列內容新增為 `DetectSpike()` 方法中的下一行程式碼，調整模型為合適於 `productSales` 資料並傳回已定型模型：

[!code-csharp[TrainModel1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel1)]

[Fit()](xref:Microsoft.ML.Data.TrivialEstimator%601.Fit%2A) 方法透過轉換資料集和套用定型來定型模型。

新增下列程式碼將 `productSales` 資料轉換成 `DetectSpike()` 方法中的下一行程式碼：

[!code-csharp[TransformData1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData1)]

之前的程式碼使用 [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) 方法會對測試資料集多個所提供的輸入資料列進行預測。

將您的 `transformedData` 轉換成強型別 `IEnumerable`，以更容易使用 [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) 方法和下列程式碼顯示：

[!code-csharp[CreateEnumerable1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable1)]

使用下列 <xref:System.Console.WriteLine?displayProperty=nameWithType> 程式碼建立顯示標頭行：

[!code-csharp[DisplayHeader1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader1)]

您會在尖峰偵測結果中顯示下列資訊：

* `Alert` 表示指定資料點的尖峰警示。

* `Score` 是資料集中指定資料點的 `ProductSales` 值。

* `P-Value` "P" 表示機率。 這表示此資料點為異常狀況的可能性。 

使用下列程式碼逐一查看 `predictions` `IEnumerable`，並顯示結果：

[!code-csharp[DisplayResults1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults1)]

## <a name="spike-detection-results"></a>尖峰偵測結果

您的結果應該與以下類似。 處理期間會顯示訊息。 您可能會看到警告或處理訊息。 為了清晰起見，下列結果中已將這些都移除。

```console
Detect temporary changes in pattern
=============== Training the model ===============
=============== End of training process ===============
Alert   Score   P-Value
0       271.00  0.50
0       150.90  0.00
0       188.10  0.41
0       124.30  0.13
0       185.30  0.47
0       173.50  0.47
0       236.80  0.19
0       229.50  0.27
0       197.80  0.48
0       127.90  0.13
1       341.50  0.00 <-- Spike detected
0       190.90  0.48
0       199.30  0.48
0       154.50  0.24
0       215.10  0.42
0       278.30  0.19
0       196.40  0.43
0       292.00  0.17
0       231.00  0.45
0       308.60  0.18
0       294.90  0.19
1       426.60  0.00 <-- Spike detected
0       269.50  0.47
0       347.30  0.21
0       344.70  0.27
0       445.40  0.06
0       320.90  0.49
0       444.30  0.12
0       406.30  0.29
0       442.40  0.21
1       580.50  0.00 <-- Spike detected
0       412.60  0.45
1       687.00  0.01 <-- Spike detected
0       480.30  0.40
0       586.30  0.20
0       651.90  0.14
```

## <a name="change-point-detection"></a>變更點偵測

`Change points` 是值之時間序列事件資料流分佈的持續變更，例如層級變更和趨勢。 這些持續變更延續的時間比 `spikes` 長，可能表示災難性事件。 `Change points` 通常無法為肉眼所見，但可以使用下列方法，在您的資料中偵測到。  下圖是變更點偵測的範例：

![ChangePointDetection](./media/sales-anomaly-detection/ChangePointDetection.png)

### <a name="create-the-detectchangepoint-method"></a>建立 DetectChangepoint() 方法

將下列呼叫新增至 `DetectChangepoint()` 方法作為 `Main()` 方法中的下一行程式碼：

[!code-csharp[CallDetectChangepoint](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectChangepoint)]

`DetectChangepoint()` 方法會執行下列工作：

* 將模型定型。
* 根據歷史銷售資料偵測變更點。
* 顯示結果。

請使用下列程式碼，在緊接著 `Main()` 方法之後，建立 `DetectChangepoint()` 方法：

```csharp
static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
{

}
```

[iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) 用來定型變更點偵測的模型。 使用下列程式碼將它新增至 `DetectChangepoint()` 方法：

[!code-csharp[AddChangepointTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddChangepointTrainer)]

如您之前的操作，將下列內容新增為 `DetectChangePoint()` 方法中的下一行程式碼，調整模型為合適於 `productSales` 資料並傳回已定型模型：

[!code-csharp[TrainModel2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel2)]

將下列程式碼新增至 `DetectChangePoint()`，使用 `Transform()` 方法轉換 `Training` 資料：

[!code-csharp[TransformData2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData2)]

如您之前的操作，將您的 `transformedData` 轉換成強型別 `IEnumerable`，以更容易使用 `CreateEnumerable()` 方法和下列程式碼顯示：

[!code-csharp[CreateEnumerable2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable2)]

下列列程式碼作為 `DetectChangePoint()` 方法中的下一行，建立顯示標頭：

[!code-csharp[DisplayHeader2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader2)]

您會在變更點偵測結果中顯示下列資訊：

* `Alert` 表示指定資料點的變更點警示。
* `Score` 是資料集中指定資料點的 `ProductSales` 值。
* `P-Value` "P" 表示機率。 這表示此資料點為異常狀況的可能性。 
* `Martingale value` 根據一系列的 P 值，用來識別資料點的「怪異」程度。  

使用下列程式碼逐一查看 `predictions` `IEnumerable`，並顯示結果：

[!code-csharp[DisplayResults2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults2)]

## <a name="change-point-detection-results"></a>變更點偵測結果

您的結果應該與以下類似。 處理期間會顯示訊息。 您可能會看到警告或處理訊息。 為了清晰起見，下列結果中已將這些都移除。

```console
Detect Persistent changes in pattern
=============== Training the model Using Change Point Detection Algorithm===============
=============== End of training process ===============
Alert   Score   P-Value Martingale value
0       271.00  0.50    0.00
0       150.90  0.00    2.33
0       188.10  0.41    2.80
0       124.30  0.13    9.16
0       185.30  0.47    9.77
0       173.50  0.47    10.41
0       236.80  0.19    24.46
0       229.50  0.27    42.38
1       197.80  0.48    44.23 <-- alert is on, predicted changepoint
0       127.90  0.13    145.25
0       341.50  0.00    0.01
0       190.90  0.48    0.01
0       199.30  0.48    0.00
0       154.50  0.24    0.00
0       215.10  0.42    0.00
0       278.30  0.19    0.00
0       196.40  0.43    0.00
0       292.00  0.17    0.01
0       231.00  0.45    0.00
0       308.60  0.18    0.00
0       294.90  0.19    0.00
0       426.60  0.00    0.00
0       269.50  0.47    0.00
0       347.30  0.21    0.00
0       344.70  0.27    0.00
0       445.40  0.06    0.02
0       320.90  0.49    0.01
0       444.30  0.12    0.02
0       406.30  0.29    0.01
0       442.40  0.21    0.01
0       580.50  0.00    0.01
0       412.60  0.45    0.01
0       687.00  0.01    0.12
0       480.30  0.40    0.08
0       586.30  0.20    0.03
0       651.90  0.14    0.09
```

恭喜您！ 您現已成功建置偵測銷售資料中尖峰和變更點異常的機器學習模型。

您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) 存放庫中找到本教學課程的原始程式碼。

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> * 載入資料
> * 定型尖峰異常偵測的模型
> * 使用定型的模型偵測尖峰異常
> * 定型變更點異常偵測的模型
> * 使用定型的模式偵測變更點異常

## <a name="next-steps"></a>後續步驟

請查看機器學習範例 GitHub 存放庫，以探索耗電量異常偵測範例。
> [!div class="nextstepaction"]
> [dotnet/machinelearning-samples GitHub 存放庫](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/TimeSeries_PowerAnomalyDetection) \(英文\)
