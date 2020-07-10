---
title: 教學課程：預測自行車出租需求-時間序列
description: 本教學課程說明如何使用單一變數時間序列分析和 ML.NET，預測自行車出租服務的需求。
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: d93bdee8d5a057be0f405fe4334d7edbdc0649ec
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174402"
---
# <a name="tutorial-forecast-bike-rental-service-demand-with-time-series-analysis-and-mlnet"></a>教學課程：使用時間序列分析和 ML.NET 預測自行車出租服務需求

瞭解如何使用單一變數時間序列分析，針對儲存在含有 ML.NET 之 SQL Server 資料庫中的資料，預測自行車出租服務的需求。

在本教學課程中，您會了解如何：
> [!div class="checklist"]
>
> * 了解問題
> * 從資料庫載入資料
> * 建立預測模型
> * 評估預測模型
> * 儲存預測模型
> * 使用預測模型

## <a name="prerequisites"></a>先決條件

- [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)或更新版本，或是已安裝「.net Core 跨平臺開發」工作負載的 Visual Studio 2017 15.6 或更新版本。

## <a name="time-series-forecasting-sample-overview"></a>時間序列預測範例總覽

這個範例是**c # .Net Core 主控台應用程式**，使用單一變數時間序列分析演算法（稱為單一頻譜分析）來預測自行車租用的需求。 此範例的程式碼可在 GitHub 上的[dotnet/machinelearning 範例](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand)存放庫中找到。

## <a name="understand-the-problem"></a>了解問題

為了執行有效率的作業，清查管理扮演重要的角色。 存貨中有太多產品，表示坐在貨架上的 unsold 產品不會產生任何收益。 產品過少會導致銷售和客戶從競爭者購買。 因此，常數的問題是，最適合的清查數量為何？ 時間序列分析會查看歷程記錄資料、識別模式，並使用此資訊來預測未來一些時間的值，以協助提供這些問題的答案。

分析本教學課程中使用的資料的技術是單一變數時間序列分析。 單一變數時間序列分析會以特定間隔（例如每月銷售），查看一段時間內的單一數值觀察。

本教學課程中使用的演算法是[ (SSA) 的單一頻譜分析](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf)。 SSA 的運作方式是將時間序列分解成一組主要元件。 這些元件可以解讀為與趨勢、雜訊、季節性和許多其他因素相對應的信號部分。 然後，系統會重建這些元件，並用來預測未來一些時間的值。

## <a name="create-console-application"></a>建立主控台應用程式

1. 建立名為 "BikeDemandForecasting" 的新**c # .Net Core 主控台應用程式**。
1. 安裝**Microsoft.ML**版本 NuGet 套件

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    1. 在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]****。
    1. 選擇 [nuget.org] 作為 [套件來源]，選取 [**流覽**] 索引標籤，搜尋**Microsoft.ML**。
    1. 勾選 [**包含發行**前版本] 核取方塊。
    1. 選取 [安裝]**** 按鈕。
    1. 在 [預覽變更]**** 對話方塊上，選取 [確定]**** 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]****。
    1. 針對**SqlClient**和**時間序列**重複執行這些步驟。

### <a name="prepare-and-understand-the-data"></a>準備並了解資料

1. 建立名為*Data*的目錄。
1. 下載[ *DailyDemand .mdf*資料庫](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf)檔案，並將它儲存至*資料*目錄。

> [!NOTE]
> 本教學課程中使用的資料來自[UCI 自行車共用資料集](http://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset)。 Fanaee-T、Hadi 和 Gama、Joao、「結合集團偵測器和背景知識的事件標記」、人工智慧 (2013) ： pp 1-15、Springer link 柏林 Heidelberg、 [Web 連結](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3)。

原始資料集包含數個對應至季節性和氣象的資料行。 為了簡潔起見，因為本教學課程中使用的演算法只需要單一數值資料行中的值，所以原始資料集已壓縮成隻包含下列資料行：

- **dteday**：觀察的日期。
- **year**：觀察 (0 = 2011，1 = 2012) 的編碼年份。
- **cnt**：當天的自行車租用總數。

原始資料集會對應到在 SQL Server 資料庫中具有下列架構的資料庫資料表。

```SQL
CREATE TABLE [Rentals] (
    [RentalDate] DATE NOT NULL,
    [Year] INT NOT NULL,
    [TotalRentals] INT NOT NULL
);
```

以下是資料的範例：

| RentalDate | 年 | TotalRentals |
| --- | --- | --- |
|1/1/2011|0|985|
|1/2/2011|0|801|
|1/3/2011|0|1349|

### <a name="create-input-and-output-classes"></a>建立輸入和輸出類別

1. 開啟*Program.cs*檔案，並 `using` 以下列內容取代現有的語句：

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L1-L8)]

1. 建立 `ModelInput` 類別。 在 `Program` 類別底下，新增下列程式碼。

    [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L120-L127)]

    `ModelInput`類別包含下列資料行：

    - **RentalDate**：觀察的日期。
    - **Year**：觀察 (0 = 2011，1 = 2012) 的編碼年份。
    - **TotalRentals**：當天的自行車租金總數。

1. `ModelOutput`在新建立的類別底下建立類別 `ModelInput` 。

    [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L129-L136)]

    `ModelOutput`類別包含下列資料行：

    - **ForecastedRentals**：預測週期的預測值。
    - **LowerBoundRentals**：預測週期的預測最小值。
    - **UpperBoundRentals**：預測週期的預測最大值。

### <a name="define-paths-and-initialize-variables"></a>定義路徑和初始化變數

1. 在 `Main` 方法內，定義變數以儲存資料的位置、連接字串，以及要在何處儲存定型的模型。

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L16-L19)]

1. `mlContext` [`MLContext`](xref:Microsoft.ML.MLContext) 將下列程式程式碼新增至方法，以將變數初始化為的新實例 `Main` 。

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L21)]

    [`MLContext`](xref:Microsoft.ML.MLContext)類別是所有 ML.NET 作業的起點，而初始化 mlCoNtext 會建立可在模型建立工作流程物件之間共用的新 ML.NET 環境。 就概念而言，類似於 Entity Framework 中的 `DBContext`。

## <a name="load-the-data"></a>載入資料

1. 建立 `DatabaseLoader` ，它會載入類型的記錄 `ModelInput` 。

    [!code-csharp [CreateDBLoader](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L23)]

1. 定義要從資料庫載入資料的查詢。

    [!code-csharp [DefineSQLQuery](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L25)]

    ML.NET 演算法預期資料的類型為 [`Single`](xref:System.Single) 。 因此，來自不屬於類型之資料庫的數值（ [`Real`](xref:System.Data.SqlDbType) 單精確度浮點數）必須轉換成 [`Real`](xref:System.Data.SqlDbType) 。

    `Year`和 `TotalRental` 資料行都是資料庫中的兩個整數類型。 使用 `CAST` 內建函數時，它們會轉換成 `Real` 。

1. 建立 `DatabaseSource` 以連接到資料庫並執行查詢。

    [!code-csharp [CreateDBSource](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L27-L29)]

1. 將資料載入 `IDataView` 。

    [!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L31)]

1. 此資料集包含兩年的資料。 只有第一年的資料會用於定型，第二年則是用來比較實際值與模型產生的預測。 使用轉換來篩選資料 [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) 。

    [!code-csharp [SplitData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L33-L34)]

    在第一年中，只有小於1的資料行中的值 `Year` 會藉由將 `upperBound` 參數設定為1來選取。 相反地，針對第二個年份，會將參數設定為1，以選取大於或等於1的值 `lowerBound` 。

## <a name="define-time-series-analysis-pipeline"></a>定義時間序列分析管線

1. 定義管線，以使用[SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator)來預測時間序列資料集中的值。

    [!code-csharp [DefinePipeline](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L36-L45)]

    `forecastingPipeline`第一年會採用365資料點並取樣，或將時間序列資料集分割為30天 (每月) 間隔，如參數所指定 `seriesLength` 。 每個範例都是透過每週或7天的時段進行分析。 在決定下一個期間的預測值 (s) 為時，會使用過去七天的值進行預測。 此模型設定為以參數所定義，預測未來七個週期 `horizon` 。 由於預測是一種明智的猜測，因此不一定總是100% 精確。 因此，最好能在最佳和最糟的案例中，根據上限和下限所定義的值範圍來瞭解。 在此情況下，較低和上限的信心層級會設定為95%。 信賴等級可以相應增加或減少。 值愈高，範圍的寬度就會介於上限和下限之間，以達到所需的信心層級。

1. 使用 [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) 方法來定型模型，並將資料符合先前定義的 `forecastingPipeline` 。

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L47)]

## <a name="evaluate-the-model"></a>評估模型

藉由預測下一年的資料，並將其與實際值進行比較，來評估模型的執行程度。

1. 在 `Main` 方法下方，建立名為的新公用程式方法 `Evaluate` 。

    ```csharp
    static void Evaluate(IDataView testData, ITransformer model, MLContext mlContext)
    {

    }
    ```

1. 在 `Evaluate` 方法內，使用方法搭配定型模型來預測第二年的資料 [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) 。

    [!code-csharp [EvaluateForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L62)]

1. 使用方法，從資料取得實際的值 [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) 。

    [!code-csharp [GetActualRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L65-L67)]

1. 使用方法取得預測值 [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) 。

    [!code-csharp [GetForecastRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L70-L72)]

1. 計算實際和預測值之間的差異，通常稱為「錯誤」。

    [!code-csharp [CalculateError](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L75)]

1. 藉由計算平均絕對錯誤和根 Mean 平方誤差值來測量效能。

    [!code-csharp [CalculateMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L78-L79)]

    若要評估效能，會使用下列計量：

    - **平均絕對錯誤**：測量接近預測與實際值的方式。 這個值的範圍介於0與無限大之間。 愈接近0，模型的品質愈好。
    - **根平均平方誤差**：摘要說明模型中的錯誤。 這個值的範圍介於0與無限大之間。 愈接近0，模型的品質愈好。

1. 將計量輸出至主控台。

    [!code-csharp [OutputMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L82-L85)]

1. 在 `Evaluate` 方法內使用方法 `Main` 。

    [!code-csharp [EvaluateModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L49)]

## <a name="save-the-model"></a>儲存模型

如果您對模型感到滿意，請儲存以供稍後在其他應用程式中使用。

1. 在 `Main` 方法中，建立 [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) 。 [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602)是進行單一預測的便利方法。

    [!code-csharp [CreateTimeSeriesEngine](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L51)]

1. 將模型儲存至名為的檔案， `MLModel.zip` 如先前定義的 `modelPath` 變數所指定。 使用 [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) 方法來儲存模型。

    [!code-csharp [SaveModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L52)]

## <a name="use-the-model-to-forecast-demand"></a>使用模型來預測需求

1. 在 `Evaluate` 方法下方，建立名為的新公用程式方法 `Forecast` 。

    ```csharp
    static void Forecast(IDataView testData, int horizon, TimeSeriesPredictionEngine<ModelInput, ModelOutput> forecaster, MLContext mlContext)
    {

    }
    ```

1. 在 `Forecast` 方法內，使用 [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) 方法來預測接下來七天的租用。

    [!code-csharp [SingleForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L91)]

1. 將 [實際] 和 [預測] 值對齊七個期間。

    [!code-csharp [GetForecastOutput](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L93-L108)]

1. 逐一查看預測輸出，並將它顯示在主控台上。

    [!code-csharp [DisplayForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L111-L116)]

## <a name="run-the-application"></a>執行應用程式

1. 在 `Main` 方法內，呼叫 `Forecast` 方法。

    [!code-csharp [BuildForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L54)]

1. 執行應用程式。 與下面類似的輸出應該會出現在主控台上。 為求簡潔，輸出已壓縮。

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

檢查實際和預測的值，會顯示下列關聯性：

![實際與預測比較](./media/time-series-demand-forecasting/forecast.png)

雖然預測的值不會預測確切的租用數目，但它們提供的值範圍較窄，可讓作業優化資源的使用。

恭喜！ 您現在已成功建立時間序列機器學習模型來預測自行車出租需求。

您可以在[dotnet/machinelearning 範例](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand)存放庫中找到本教學課程的原始程式碼。

## <a name="next-steps"></a>後續步驟

- [ML.NET 中的機器學習工作](../resources/tasks.md)
- [改善模型正確性](../resources/improve-machine-learning-model-ml-net.md)
