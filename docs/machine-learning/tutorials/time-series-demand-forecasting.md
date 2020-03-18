---
title: 教程： 預測自行車租賃需求 - 時間系列
description: 本教程介紹如何使用單變數時間序列分析和ML.NET預測自行車租賃服務的需求。
ms.date: 11/07/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: 026421d7b1b2a0e39118ae712780ca7fc8f6e444
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "76921247"
---
# <a name="tutorial-forecast-bike-rental-service-demand-with-time-series-analysis-and-mlnet"></a>教程：通過時間序列分析和ML.NET預測自行車租賃服務需求

瞭解如何使用單變數時間序列分析預測自行車租賃服務的需求，這些分析對存儲在具有ML.NET的 SQL Server 資料庫中的資料進行單變數時間序列分析。

在本教學課程中，您會了解如何：
> [!div class="checklist"]
>
> * 了解問題
> * 從資料庫載入資料
> * 創建預測模型
> * 評估預測模型
> * 保存預測模型
> * 使用預測模型

## <a name="prerequisites"></a>必要條件

- [Visual Studio 2017 版本 15.6 或更高版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)安裝了".NET 核心跨平臺開發"工作負載。

## <a name="time-series-forecasting-sample-overview"></a>時間序列預測示例概述

此示例是**C# .NET Core 主控台應用程式**，該應用程式使用稱為單頻譜分析的單變數時間序列分析演算法預測自行車租賃需求。 此示例的代碼可以在 GitHub 上的[dotnet/機器學習示例](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand)存儲庫中找到。

## <a name="understand-the-problem"></a>了解問題

為了高效運行，庫存管理起著關鍵作用。 庫存的產品過多意味著未售出的產品在貨架上沒有產生任何收入。 產品太少會導致銷售損失和客戶從競爭對手購買。 因此，一個不變的問題是，手頭庫存的最佳數量是多少？ 時間序列分析通過查看歷史資料、識別模式以及使用此資訊預測將來某個時候的值，説明提供這些問題的答案。

分析本教程中使用的資料的技術是一元制時間序列分析。 統一時間序列分析以特定間隔（如月銷售額）查看一段時間內的單數值觀測值。

本教程中使用的演算法是[單頻譜分析（SSA）。](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf) SSA 的工作原理是將時間序列分解為一組主要元件。 這些元件可以解釋為信號的一部分，對應于趨勢、雜訊、季節性和許多其他因素。 然後，這些元件被重建，並用於預測將來某個時候的值。

## <a name="create-console-application"></a>建立主控台應用程式

1. 創建新的**C# .NET 核心主控台應用程式**，稱為"自行車需求預測"。
1. 安裝**Microsoft.ML**版本**1.4.0** NuGet 包
    1. 在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]****。
    1. 選擇"nuget.org"作為"包"源，選擇 **"流覽**"選項卡，搜索**Microsoft.ML**。
    1. 選中"**包含預發佈**"核取方塊。
    1. 選取 [安裝]**** 按鈕。
    1. 在 [預覽變更]**** 對話方塊上，選取 [確定]**** 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]****。
    1. 對**System.Data.SqlClient**版本**4.7.0**和**Microsoft.ML.TimeSeries**版本**1.4.0**重複這些步驟。

### <a name="prepare-and-understand-the-data"></a>準備並了解資料

1. 創建名為*Data*的目錄。
1. 下載[*DailyDemand.mdf*資料庫檔案](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf)並將其保存到*資料*目錄中。

> [!NOTE]
> 本教程中使用的資料來自[UCI 自行車共用資料集](https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset)。 Fanaee-T、Hadi和Gama，Joao，"結合綜合探測器和背景知識的事件標籤"，人工智慧的進步（2013年）：第1-15頁，斯普林格柏林海德堡，[網路連結](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3)。

原始資料集包含與季節性和天氣對應的幾個列。 為簡潔起見，並且本教程中使用的演算法僅需要單個數值列中的值，因此原始資料集已壓縮為僅包含以下列：

- **第二天**：觀察的日期。
- **年份**： 觀測的編碼年份 （0=2011， 1=2012）。
- **cnt**： 當天自行車租賃的總數。

原始資料集映射到 SQL Server 資料庫中具有以下架構的資料庫表。

```SQL
CREATE TABLE [Rentals] (
    [RentalDate] DATE NOT NULL,
    [Year] INT NOT NULL,
    [TotalRentals] INT NOT NULL
);
```

以下是資料的示例：

| 租賃日期 | Year | 總租賃量 |
| --- | --- | --- |
|1/1/2011|0|985|
|1/2/2011|0|801|
|1/3/2011|0|1349|

### <a name="create-input-and-output-classes"></a>創建輸入和輸出類

1. 打開*Program.cs*檔，並將現有`using`語句替換為以下內容：

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L1-L8)]

1. 建立 `ModelInput` 類別。 在類`Program`下方，添加以下代碼。

    [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L120-L127)]

    該`ModelInput`類包含以下列：

    - **租賃日期**：觀察日期。
    - **年份**： 觀測的編碼年份 （0=2011， 1=2012）。
    - **總租金**：當天自行車租賃的總數。

1. 在新`ModelOutput`創建的類下方創建`ModelInput`類。

    [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L129-L136)]

    該`ModelOutput`類包含以下列：

    - **預測租金**：預測期間的預測值。
    - **下邊界租金**：預測期間的預測最小值。
    - **上邊界租金**：預測期間的預測最大值。

### <a name="define-paths-and-initialize-variables"></a>定義路徑並初始化變數

1. 在`Main`方法內，定義變數以存儲資料的位置、連接字串以及保存訓練的模型的位置。

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L16-L19)]

1. 通過向`Main`方法添加以下行，使用`mlContext` [`MLContext`](xref:Microsoft.ML.MLContext)

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L21)]

    該[`MLContext`](xref:Microsoft.ML.MLContext)類是所有ML.NET操作的起點，初始化 mlCoNtext 會創建一個新的ML.NET環境，可以在模型創建工作流物件之間共用。 就概念而言，類似於 Entity Framework 中的 `DBContext`。

## <a name="load-the-data"></a>載入資料

1. 創建`DatabaseLoader`載入類型`ModelInput`的記錄。

    [!code-csharp [CreateDBLoader](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L23)]

1. 定義查詢以從資料庫載入資料。

    [!code-csharp [DefineSQLQuery](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L25)]

    ML.NET演算法期望資料的類型[`Single`](xref:System.Single)。 因此，來自資料庫的數值（單[`Real`](xref:System.Data.SqlDbType)精度浮點值）必須轉換為[`Real`](xref:System.Data.SqlDbType)。

    和`Year``TotalRental`列都是資料庫中的整數類型。 使用`CAST`內建函數，它們都強制轉換為`Real`。

1. 創建`DatabaseSource`以連接到資料庫並執行查詢。

    [!code-csharp [CreateDBSource](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L27-L29)]

1. 將資料載入到 中`IDataView`。

    [!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L31)]

1. 資料集包含兩年的資料。 只有第一年的資料用於培訓，第二年用於將實際值與模型生成的預測進行比較。 使用[`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*)轉換篩選資料。

    [!code-csharp [SplitData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L33-L34)]

    對於第一年，僅通過將`Year``upperBound`參數設置為 1 來選擇列中小於 1 的值。 相反，對於第二年，通過將`lowerBound`參數設置為 1 來選擇大於或等於 1 的值。

## <a name="define-time-series-analysis-pipeline"></a>定義時間序列分析管道

1. 定義使用[Ssa預測器](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator)預測時間序列資料集中的值的管道。

    [!code-csharp [DefinePipeline](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L36-L45)]

    獲取`forecastingPipeline`第一年的 365 個資料點，採樣或拆分時間序列資料集為`seriesLength`參數指定的 30 天（每月）間隔。 每個樣本都通過每週或 7 天的視窗進行分析。 在確定下一個期間的預測值時，使用前七天的值進行預測。 模型設置為預測`horizon`參數定義的未來七個週期。 由於預測是一個知情的猜測，它並不總是 100% 準確。 因此，最好瞭解由上限和下限定義的最佳和最壞情況下的值範圍。 在這種情況下，下限和上限的置信度設置為 95%。 置信度可以相應增加或降低。 值越高，上邊界和下邊界之間的範圍越寬，以實現所需的置信度。

1. 使用[`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*)方法訓練模型並將資料與先前定義的`forecastingPipeline`資料配合。

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L47)]

## <a name="evaluate-the-model"></a>評估模型

通過預測下一年的資料並將其與實際值進行比較，評估模型的性能。

1. 在方法`Main`下方，創建一種稱為`Evaluate`的新實用程式方法。

    ```csharp
    static void Evaluate(IDataView testData, ITransformer model, MLContext mlContext)
    {

    }
    ```

1. 在該方法`Evaluate`內，使用該方法對訓練的模型進行[`Transform`](xref:Microsoft.ML.ITransformer.Transform*)預測第二年的資料。

    [!code-csharp [EvaluateForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L62)]

1. 使用[`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*)方法從資料獲取實際值。

    [!code-csharp [GetActualRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L65-L67)]

1. 使用[`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*)方法獲取預測值。

    [!code-csharp [GetForecastRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L70-L72)]

1. 計算實際值和預測值之間的差異，通常稱為錯誤。

    [!code-csharp [CalculateError](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L75)]

1. 通過計算平均絕對誤差和根均值平方誤差值來衡量性能。

    [!code-csharp [CalculateMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L78-L79)]

    為了評估性能，使用以下指標：

    - **平均絕對誤差**：衡量預測與實際值的接近程度。 此值的範圍介於 0 和無窮大之間。 接近 0，模型的品質越好。
    - **根均值平方錯誤**：匯總模型中的錯誤。 此值的範圍介於 0 和無窮大之間。 接近 0，模型的品質越好。

1. 將指標輸出到主控台。

    [!code-csharp [OutputMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L82-L85)]

1. 在`Evaluate``Main`方法中使用 方法。

    [!code-csharp [EvaluateModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L49)]

## <a name="save-the-model"></a>儲存模型

如果您對模型感到滿意，請將其保存以供以後在其他應用程式中使用。

1. 在`Main`方法中，創建[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602)一個 。 [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602)是進行單一預測的便捷方法。

    [!code-csharp [CreateTimeSeriesEngine](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L51)]

1. 將模型保存到以前定義的`MLModel.zip``modelPath`變數指定的檔中。 使用[`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*)方法保存模型。

    [!code-csharp [SaveModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L52)]

## <a name="use-the-model-to-forecast-demand"></a>使用模型預測需求

1. 在方法`Evaluate`下方，創建一種稱為`Forecast`的新實用程式方法。

    ```csharp
    static void Forecast(IDataView testData, int horizon, TimeSeriesPredictionEngine<ModelInput, ModelOutput> forecaster, MLContext mlContext)
    {

    }
    ```

1. 在該方法`Forecast`內，使用[`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*)方法預測未來七天的租金。

    [!code-csharp [SingleForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L91)]

1. 對齊七個週期的實際值和預測值。

    [!code-csharp [GetForecastOutput](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L93-L108)]

1. 反覆運算預測輸出並將其顯示在主控台上。

    [!code-csharp [DisplayForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L111-L116)]

## <a name="run-the-application"></a>執行應用程式

1. 在`Main`方法內，調用`Forecast`方法。

    [!code-csharp [BuildForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L54)]

1. 執行應用程式。 類似于下面的輸出應出現在主控台上。 為簡潔起見，輸出已壓縮。

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

檢查實際值和預測值將顯示以下關系：

![實際與預測比較](./media/time-series-demand-forecasting/forecast.png)

雖然預測值沒有預測確切的租金數量，但它們提供了更窄的值範圍，使操作能夠優化其資源的使用。

恭喜！ 現在，您已成功構建了時間序列機器學習模型，以預測自行車租賃需求。

您可以在[dotnet/機器學習示例](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand)存儲庫中找到本教程的原始程式碼。

## <a name="next-steps"></a>後續步驟

- [ML.NET 中的機器學習工作](../resources/tasks.md)
- [改善模型精確度](../resources/improve-machine-learning-model-ml-net.md)
