---
title: 教學課程：預測自行車出租需求時間序列
description: 本教學課程說明如何使用單變數時間序列分析和 ML.NET，預測自行車出租服務的需求。
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: 51041f5a9076ad360a84cc39704aedb50b77d40a
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679386"
---
# <a name="tutorial-forecast-bike-rental-service-demand-with-time-series-analysis-and-mlnet"></a>教學課程：使用時間序列分析和 ML.NET 預測自行車出租服務需求

瞭解如何針對使用 ML.NET 儲存在 SQL Server 資料庫中的資料，使用單變數時間序列分析來預測自行車租用服務的需求。

在本教學課程中，您會了解如何：
> [!div class="checklist"]
>
> * 了解問題
> * 從資料庫載入資料
> * 建立預測模型
> * 評估預測模型
> * 儲存預測模型
> * 使用預測模型

## <a name="prerequisites"></a>必要條件

- 已安裝「.NET Core 跨平臺開發」工作負載， [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)或更新版本或 Visual Studio 2017 15.6 版或更新版本。

## <a name="time-series-forecasting-sample-overview"></a>時間序列預測範例總覽

此範例是 **c # .Net Core 主控台應用程式** ，它會使用稱為單數頻譜分析的單變數時間序列分析演算法，預測自行車租用的需求。 您可以在 GitHub 上的 [dotnet/machinelearning 範例](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) 存放庫中找到此範例的程式碼。

## <a name="understand-the-problem"></a>了解問題

為了執行有效率的作業，清查管理扮演重要角色。 股票內有太多的產品，表示坐在貨架的 unsold 產品不會產生任何收益。 產品太少導致銷售中斷，以及從競爭者購買的客戶。 因此，常數的問題是，要保留的最佳清查數量為何？ 時間序列分析藉由查看歷程記錄資料、識別模式，以及使用這項資訊來預測未來的價值，來協助提供這些問題的答案。

分析本教學課程中所使用之資料的技術是單變數時間序列分析。 單變數時間序列分析會以特定間隔（例如每月銷售額），查看一段時間內的單一數值觀察。

本教學課程中使用的演算法是 [ (SSA) 的單一頻譜分析 ](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf)。 SSA 的運作方式是將時間序列分解為一組主體元件。 這些元件可以被解釋為與趨勢、雜訊、季節性和許多其他因素對應的信號部分。 然後，這些元件會重建，並用來預測未來一些時間的值。

## <a name="create-console-application"></a>建立主控台應用程式

1. 建立名為 "BikeDemandForecasting" 的新 **c # .Net Core 主控台應用程式** 。
1. 安裝 **Microsoft.ML** NuGet 套件版本

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    1. 在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]****。
    1. 選擇 "nuget.org" 作為 [套件來源]，選取 [ **流覽** ] 索引標籤，並搜尋 **Microsoft.ML**。
    1. 核取 [ **包含發行** 前版本] 核取方塊。
    1. 選取 [安裝]**** 按鈕。
    1. 在 [預覽變更]**** 對話方塊上，選取 [確定]**** 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]****。
    1. 針對 **SqlClient** 和 **時間序列**重複執行這些步驟。

### <a name="prepare-and-understand-the-data"></a>準備並了解資料

1. 建立名為 *Data*的目錄。
1. 下載[ *DailyDemand .mdf*資料庫](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf)檔案，並將它儲存到*資料*目錄。

> [!NOTE]
> 本教學課程中使用的資料來自 [UCI 自行車共用資料集](http://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset)。 Fanaee-T、Hadi 和 Gama、Joao、「結合集團偵測器和背景知識的事件標籤」、人工智慧 (2013) ： pp 1-15、Springer link 柏林 Heidelberg、 [Web 連結](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3)。

原始資料集包含數個對應至季節性和氣象的資料行。 為了簡潔起見，在本教學課程中使用的演算法只需要單一數值資料行的值，原始資料集已壓縮成隻包含下列資料行：

- **dteday**：觀察日期。
- **year**：觀察 (0 = 2011，1 = 2012) 的編碼年份。
- **cnt**：當天的自行車租金總數。

原始資料集會對應到 SQL Server 資料庫中具有下列架構的資料庫資料表。

```sql
CREATE TABLE [Rentals] (
    [RentalDate] DATE NOT NULL,
    [Year] INT NOT NULL,
    [TotalRentals] INT NOT NULL
);
```

以下是資料的範例：

| RentalDate | Year | TotalRentals |
| --- | --- | --- |
|1/1/2011|0|985|
|1/2/2011|0|801|
|1/3/2011|0|1349|

### <a name="create-input-and-output-classes"></a>建立輸入和輸出類別

1. 開啟 *Program.cs* 檔案，並將現有的語句取代為 `using` 下列內容：

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L1-L8)]

1. 建立 `ModelInput` 類別。 在 `Program` 類別底下，加入下列程式碼。

    [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L120-L127)]

    `ModelInput`類別包含下列資料行：

    - **RentalDate**：觀察日期。
    - **Year**：觀察 (0 = 2011，1 = 2012) 的編碼年份。
    - **TotalRentals**：當天的自行車租金總數。

1. `ModelOutput`在新建立的類別底下建立類別 `ModelInput` 。

    [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L129-L136)]

    `ModelOutput`類別包含下列資料行：

    - **ForecastedRentals**：預測期間的預測值。
    - **LowerBoundRentals**：預測期間的預測最小值。
    - **UpperBoundRentals**：預測期間的預測最大值。

### <a name="define-paths-and-initialize-variables"></a>定義路徑及初始化變數

1. 在 `Main` 方法內部，定義變數來儲存資料的位置、連接字串，以及要儲存定型模型的位置。

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L16-L19)]

1. `mlContext` [`MLContext`](xref:Microsoft.ML.MLContext) 將下列程式程式碼加入至方法，以將變數初始化為的新實例 `Main` 。

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L21)]

    [`MLContext`](xref:Microsoft.ML.MLContext)類別是所有 ML.NET 作業的起點，而初始化 mlCoNtext 會建立新的 ML.NET 環境，可在模型建立工作流程物件間共用。 就概念而言，類似於 Entity Framework 中的 `DBContext`。

## <a name="load-the-data"></a>載入資料

1. 建立 `DatabaseLoader` ，它會載入類型的記錄 `ModelInput` 。

    [!code-csharp [CreateDBLoader](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L23)]

1. 定義從資料庫載入資料的查詢。

    [!code-csharp [DefineSQLQuery](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L25)]

    ML.NET 演算法預期資料的類型是 [`Single`](xref:System.Single) 。 因此，來自不屬於型別之資料庫的數值 [`Real`](xref:System.Data.SqlDbType) （單精確度浮點數）必須轉換成 [`Real`](xref:System.Data.SqlDbType) 。

    `Year`和 `TotalRental` 資料行都是資料庫中的整數類型。 使用 `CAST` 內建函數，兩者都會轉換成 `Real` 。

1. 建立 `DatabaseSource` 以連接到資料庫並執行查詢。

    [!code-csharp [CreateDBSource](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L27-L29)]

1. 將資料載入至 `IDataView` 。

    [!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L31)]

1. 資料集包含兩年的資料。 只有第一年的資料會用於定型，第二年則是為了比較實際值與模型所產生的預測。 使用轉換來篩選資料 [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) 。

    [!code-csharp [SplitData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L33-L34)]

    在第一年，只要將 `Year` 參數設定為1，就只會選取小於1的資料行中的值 `upperBound` 。 相反地，在第二個年份中，將參數設定為1，即可選取大於或等於1的值 `lowerBound` 。

## <a name="define-time-series-analysis-pipeline"></a>定義時間序列分析管線

1. 定義使用 [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) 來預測時間序列資料集中值的管線。

    [!code-csharp [DefinePipeline](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L36-L45)]

    `forecastingPipeline`第一年採用365個資料點，並取樣或將時間序列資料集分割為30天 (每月) 間隔，如參數所指定 `seriesLength` 。 每個範例都是在每週或7天的時間範圍內進行分析。 判斷下一個期間的預測值 (s) 是時，前七天的值會用來進行預測。 模型會設定為根據參數所定義，在未來預測七個週期 `horizon` 。 因為預測是明智的猜測，所以其精確度不一定是100%。 因此，在最大和最糟的情況下，最好是以上限和下限來瞭解值的範圍。 在此情況下，下限和上限的信賴等級會設定為95%。 信賴等級可以據此增加或減少。 值愈高，範圍的範圍越多，就能達到所需的信賴程度。

1. 您 [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit%2A) 可以使用方法來定型模型，並將資料與先前定義的資料放在一起 `forecastingPipeline` 。

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L47)]

## <a name="evaluate-the-model"></a>評估模型

藉由預測下一年的資料，並將它與實際值進行比較，來評估模型的執行效果。

1. 在 `Main` 方法底下，建立名為的新公用程式方法 `Evaluate` 。

    ```csharp
    static void Evaluate(IDataView testData, ITransformer model, MLContext mlContext)
    {

    }
    ```

1. 在 `Evaluate` 方法中，使用方法搭配定型的模型來預測第二年的資料 [`Transform`](xref:Microsoft.ML.ITransformer.Transform%2A) 。

    [!code-csharp [EvaluateForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L62)]

1. 使用方法從資料取得實際的值 [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) 。

    [!code-csharp [GetActualRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L65-L67)]

1. 使用方法取得預測值 [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) 。

    [!code-csharp [GetForecastRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L70-L72)]

1. 計算實際值與預測值之間的差異，通常稱為「錯誤」。

    [!code-csharp [CalculateError](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L75)]

1. 藉由計算平均絕對誤差和根 Mean 平方誤差值來測量效能。

    [!code-csharp [CalculateMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L78-L79)]

    若要評估效能，請使用下列計量：

    - **平均絕對錯誤**：測量預測對實際值的接近程度。 此值的範圍介於0和無限大之間。 越接近0，模型的品質就越好。
    - **根 Mean 平方誤差**：摘要說明模型中的錯誤。 此值的範圍介於0和無限大之間。 越接近0，模型的品質就越好。

1. 將計量輸出到主控台。

    [!code-csharp [OutputMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L82-L85)]

1. 使用 `Evaluate` 方法內的方法 `Main` 。

    [!code-csharp [EvaluateModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L49)]

## <a name="save-the-model"></a>儲存模型

如果您對模型感到滿意，請加以儲存，以供稍後在其他應用程式中使用。

1. 在 `Main` 方法中，建立 [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) 。 [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) 是進行單一預測的便利方法。

    [!code-csharp [CreateTimeSeriesEngine](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L51)]

1. 將模型儲存至 `MLModel.zip` 先前定義之變數所指定的檔案 `modelPath` 。 使用 [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint%2A) 方法來儲存模型。

    [!code-csharp [SaveModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L52)]

## <a name="use-the-model-to-forecast-demand"></a>使用模型來預測需求

1. 在 `Evaluate` 方法底下，建立名為的新公用程式方法 `Forecast` 。

    ```csharp
    static void Forecast(IDataView testData, int horizon, TimeSeriesPredictionEngine<ModelInput, ModelOutput> forecaster, MLContext mlContext)
    {

    }
    ```

1. 在 `Forecast` 方法中，使用 [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict%2A) 方法來預測接下來七天的租用。

    [!code-csharp [SingleForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L91)]

1. 將實際值與預測值對齊七個週期。

    [!code-csharp [GetForecastOutput](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L93-L108)]

1. 逐一查看預測輸出，並將它顯示在主控台上。

    [!code-csharp [DisplayForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L111-L116)]

## <a name="run-the-application"></a>執行應用程式

1. 在 `Main` 方法中，呼叫 `Forecast` 方法。

    [!code-csharp [BuildForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L54)]

1. 執行應用程式。 類似下面的輸出應該會出現在主控台上。 為了簡潔起見，已壓縮輸出。

    ```text
    Evaluation Metrics
    ---------------------
    Mean Absolute Error: 726.416
    Root Mean Squared Error: 987.658

    Rental Forecast
    ---------------------
    Date: 1/1/2012
    Actual Rentals: 2294
    Lower Estimate: 1197.842
    Forecast: 2334.443
    Upper Estimate: 3471.044

    Date: 1/2/2012
    Actual Rentals: 1951
    Lower Estimate: 1148.412
    Forecast: 2360.861
    Upper Estimate: 3573.309
    ```

實際和預測值的檢查會顯示下列關聯性：

![實際與預測比較](./media/time-series-demand-forecasting/forecast.png)

雖然預測的值不會預測確切的租用數量，但會提供更窄的值範圍，讓作業優化資源的使用。

恭喜！ 您現在已成功建立時間序列機器學習模型來預測自行車出租需求。

您可以在 [dotnet/machinelearning 範例](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) 存放庫中找到本教學課程的原始程式碼。

## <a name="next-steps"></a>後續步驟

- [ML.NET 中的機器學習工作](../resources/tasks.md)
- [改善模型正確性](../resources/improve-machine-learning-model-ml-net.md)
