---
title: '教學: 預測自行車租賃需求 - 時間系列'
description: 本教程介紹如何使用單變數時間序列分析和ML.NET預測自行車租賃服務的需求。
ms.date: 11/07/2019
ms.topic: tutorial
ms.custom: mvc
ms.author: luquinta
author: luisquintanilla
ms.openlocfilehash: 962c40ea0536d6b6057d936cfc4b95a49ddadbf8
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243280"
---
# <a name="tutorial-forecast-bike-rental-service-demand-with-time-series-analysis-and-mlnet"></a><span data-ttu-id="2843e-103">教學:透過時間序列分析和ML.NET預測自行車租賃服務需求</span><span class="sxs-lookup"><span data-stu-id="2843e-103">Tutorial: Forecast bike rental service demand with time series analysis and ML.NET</span></span>

<span data-ttu-id="2843e-104">瞭解如何使用單變數時間序列分析預測自行車租賃服務的需求,這些分析對存儲在具有ML.NET的SQL Server資料庫中的數據進行單變數時間序列分析。</span><span class="sxs-lookup"><span data-stu-id="2843e-104">Learn how to forecast demand for a bike rental service using univariate time series analysis on data stored in a SQL Server database with ML.NET.</span></span>

<span data-ttu-id="2843e-105">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="2843e-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="2843e-106">了解問題</span><span class="sxs-lookup"><span data-stu-id="2843e-106">Understand the problem</span></span>
> * <span data-ttu-id="2843e-107">從資料庫載入資料</span><span class="sxs-lookup"><span data-stu-id="2843e-107">Load data from a database</span></span>
> * <span data-ttu-id="2843e-108">建立預測模型</span><span class="sxs-lookup"><span data-stu-id="2843e-108">Create a forecasting model</span></span>
> * <span data-ttu-id="2843e-109">評估預測模型</span><span class="sxs-lookup"><span data-stu-id="2843e-109">Evaluate forecasting model</span></span>
> * <span data-ttu-id="2843e-110">儲存預測模型</span><span class="sxs-lookup"><span data-stu-id="2843e-110">Save a forecasting model</span></span>
> * <span data-ttu-id="2843e-111">使用預測模型</span><span class="sxs-lookup"><span data-stu-id="2843e-111">Use a forecasting model</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2843e-112">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="2843e-112">Prerequisites</span></span>

- <span data-ttu-id="2843e-113">[Visual Studio 2017 版本 15.6 或更高版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)安裝了".NET 核心跨平台開發"工作負載。</span><span class="sxs-lookup"><span data-stu-id="2843e-113">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="time-series-forecasting-sample-overview"></a><span data-ttu-id="2843e-114">時間序列預測範例概述</span><span class="sxs-lookup"><span data-stu-id="2843e-114">Time series forecasting sample overview</span></span>

<span data-ttu-id="2843e-115">此示例是**C# .NET Core 主控台應用程式**,該應用程式使用稱為單頻譜分析的單變數時間序列分析演算法預測自行車租賃需求。</span><span class="sxs-lookup"><span data-stu-id="2843e-115">This sample is a **C# .NET Core console application** that forecasts demand for bike rentals using a univariate time series analysis algorithm known as Single Spectrum Analysis.</span></span> <span data-ttu-id="2843e-116">此示例的代碼可以在 GitHub 上的[dotnet/機器學習示例](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand)儲存庫中找到。</span><span class="sxs-lookup"><span data-stu-id="2843e-116">The code for this sample can be found on the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) repository on GitHub.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="2843e-117">了解問題</span><span class="sxs-lookup"><span data-stu-id="2843e-117">Understand the problem</span></span>

<span data-ttu-id="2843e-118">為了高效運行,庫存管理起著關鍵作用。</span><span class="sxs-lookup"><span data-stu-id="2843e-118">In order to run an efficient operation, inventory management plays a key role.</span></span> <span data-ttu-id="2843e-119">庫存的產品過多意味著未售出的產品在貨架上沒有產生任何收入。</span><span class="sxs-lookup"><span data-stu-id="2843e-119">Having too much of a product in stock means unsold products sitting on the shelves not generating any revenue.</span></span> <span data-ttu-id="2843e-120">產品太少會導致銷售損失和客戶從競爭對手購買。</span><span class="sxs-lookup"><span data-stu-id="2843e-120">Having too little product leads to lost sales and customers purchasing from competitors.</span></span> <span data-ttu-id="2843e-121">因此,一個不變的問題是,手頭庫存的最佳數量是多少?</span><span class="sxs-lookup"><span data-stu-id="2843e-121">Therefore, the constant question is, what is the optimal amount of inventory to keep on hand?</span></span> <span data-ttu-id="2843e-122">時間序列分析通過查看歷史數據、識別模式以及使用此資訊預測將來某個時候的值,説明提供這些問題的答案。</span><span class="sxs-lookup"><span data-stu-id="2843e-122">Time-series analysis helps provide an answer to these questions by looking at historical data, identifying patterns, and using this information to forecast values some time in the future.</span></span>

<span data-ttu-id="2843e-123">分析本教程中使用的數據的技術是一元制時間序列分析。</span><span class="sxs-lookup"><span data-stu-id="2843e-123">The technique for analyzing data used in this tutorial is univariate time-series analysis.</span></span> <span data-ttu-id="2843e-124">統一時間序列分析以特定間隔(如月銷售額)查看一段時間內的單數值觀測值。</span><span class="sxs-lookup"><span data-stu-id="2843e-124">Univariate time-series analysis takes a look at a single numerical observation over a period of time at specific intervals such as monthly sales.</span></span>

<span data-ttu-id="2843e-125">本教學中使用的演演演算法是[單頻譜分析(SSA)。](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf)</span><span class="sxs-lookup"><span data-stu-id="2843e-125">The algorithm used in this tutorial is [Single Spectrum Analysis(SSA)](http://ssa.cf.ac.uk/zhigljavsky/pdfs/SSA/SSA_encyclopedia.pdf).</span></span> <span data-ttu-id="2843e-126">SSA 的工作原理是將時間序列分解為一組主要元件。</span><span class="sxs-lookup"><span data-stu-id="2843e-126">SSA works by decomposing a time-series into a set of principal components.</span></span> <span data-ttu-id="2843e-127">這些元件可以解釋為信號的一部分,對應於趨勢、雜訊、季節性和許多其他因素。</span><span class="sxs-lookup"><span data-stu-id="2843e-127">These components can be interpreted as the parts of a signal that correspond to trends, noise, seasonality, and many other factors.</span></span> <span data-ttu-id="2843e-128">然後,這些元件被重建,並用於預測將來某個時候的值。</span><span class="sxs-lookup"><span data-stu-id="2843e-128">Then, these components are reconstructed and used to forecast values some time in the future.</span></span>

## <a name="create-console-application"></a><span data-ttu-id="2843e-129">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="2843e-129">Create console application</span></span>

1. <span data-ttu-id="2843e-130">創建新的**C# .NET 核心控制台應用程式**,稱為"自行車需求預測"。</span><span class="sxs-lookup"><span data-stu-id="2843e-130">Create a new **C# .NET Core console application** called "BikeDemandForecasting".</span></span>
1. <span data-ttu-id="2843e-131">安裝**Microsoft.ML**版本**1.4.0** NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="2843e-131">Install **Microsoft.ML** version **1.4.0** NuGet package</span></span>
    1. <span data-ttu-id="2843e-132">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2843e-132">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="2843e-133">選擇「nuget.org」作為「包」源,選擇 **「瀏覽**」選項卡,搜尋**Microsoft.ML**。</span><span class="sxs-lookup"><span data-stu-id="2843e-133">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**.</span></span>
    1. <span data-ttu-id="2843e-134">選中包含**預先發佈**「複選框」。</span><span class="sxs-lookup"><span data-stu-id="2843e-134">Check the **Include prerelease** checkbox.</span></span>
    1. <span data-ttu-id="2843e-135">選取 [安裝]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="2843e-135">Select the **Install** button.</span></span>
    1. <span data-ttu-id="2843e-136">在 [預覽變更]\*\*\*\* 對話方塊上，選取 [確定]\*\*\*\* 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2843e-136">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the License Acceptance dialog if you agree with the license terms for the packages listed.</span></span>
    1. <span data-ttu-id="2843e-137">對**System.Data.SqlClient**版本**4.7.0**和**Microsoft.ML.TimeSeries**版本**1.4.0**重複這些步驟。</span><span class="sxs-lookup"><span data-stu-id="2843e-137">Repeat these steps for **System.Data.SqlClient** version **4.7.0** and **Microsoft.ML.TimeSeries** version **1.4.0**.</span></span>

### <a name="prepare-and-understand-the-data"></a><span data-ttu-id="2843e-138">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="2843e-138">Prepare and understand the data</span></span>

1. <span data-ttu-id="2843e-139">建立名為*Data*的目錄。</span><span class="sxs-lookup"><span data-stu-id="2843e-139">Create a directory called *Data*.</span></span>
1. <span data-ttu-id="2843e-140">下載[*DailyDemand.mdf*資料庫檔案](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf)並將其儲存到*資料*目錄中。</span><span class="sxs-lookup"><span data-stu-id="2843e-140">Download the [*DailyDemand.mdf* database file](https://github.com/dotnet/machinelearning-samples/raw/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Data/DailyDemand.mdf) and save it to the *Data* directory.</span></span>

> [!NOTE]
> <span data-ttu-id="2843e-141">本教學中使用的資料來自[UCI 自行車共享資料集](http://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset)。</span><span class="sxs-lookup"><span data-stu-id="2843e-141">The data used in this tutorial comes from the [UCI Bike Sharing Dataset](http://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset).</span></span> <span data-ttu-id="2843e-142">Fanaee-T、Hadi和Gama,Joao,"結合綜合探測器和背景知識的事件標籤",人工智慧的進步(2013年):第1-15頁,斯普林格柏林海德堡,[網路連結](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3)。</span><span class="sxs-lookup"><span data-stu-id="2843e-142">Fanaee-T, Hadi, and Gama, Joao, 'Event labeling combining ensemble detectors and background knowledge', Progress in Artificial Intelligence (2013): pp. 1-15, Springer Berlin Heidelberg, [Web Link](https://link.springer.com/article/10.1007%2Fs13748-013-0040-3).</span></span>

<span data-ttu-id="2843e-143">原始數據集包含與季節性和天氣對應的幾個列。</span><span class="sxs-lookup"><span data-stu-id="2843e-143">The original dataset contains several columns corresponding to seasonality and weather.</span></span> <span data-ttu-id="2843e-144">為簡潔起見,並且本教程中使用的演演演算法僅需要單個數值列中的值,因此原始數據集已壓縮為僅包含以下列:</span><span class="sxs-lookup"><span data-stu-id="2843e-144">For brevity and because the algorithm used in this tutorial only requires the values from a single numerical column, the original dataset has been condensed to include only the following columns:</span></span>

- <span data-ttu-id="2843e-145">**第二天**:觀察的日期。</span><span class="sxs-lookup"><span data-stu-id="2843e-145">**dteday**: The date of the observation.</span></span>
- <span data-ttu-id="2843e-146">**年份**: 觀測的編碼年份 (0=2011, 1=2012)。</span><span class="sxs-lookup"><span data-stu-id="2843e-146">**year**: The encoded year of the observation (0=2011, 1=2012).</span></span>
- <span data-ttu-id="2843e-147">**cnt**: 當天自行車租賃的總數。</span><span class="sxs-lookup"><span data-stu-id="2843e-147">**cnt**: The total number of bike rentals for that day.</span></span>

<span data-ttu-id="2843e-148">原始資料集映射到 SQL Server 資料庫中具有以下架構的資料庫表。</span><span class="sxs-lookup"><span data-stu-id="2843e-148">The original dataset is mapped to a database table with the following schema in a SQL Server database.</span></span>

```SQL
CREATE TABLE [Rentals] (
    [RentalDate] DATE NOT NULL,
    [Year] INT NOT NULL,
    [TotalRentals] INT NOT NULL
);
```

<span data-ttu-id="2843e-149">以下是資料的範例:</span><span class="sxs-lookup"><span data-stu-id="2843e-149">The following is a sample of the data:</span></span>

| <span data-ttu-id="2843e-150">租賃日期</span><span class="sxs-lookup"><span data-stu-id="2843e-150">RentalDate</span></span> | <span data-ttu-id="2843e-151">Year</span><span class="sxs-lookup"><span data-stu-id="2843e-151">Year</span></span> | <span data-ttu-id="2843e-152">總租賃量</span><span class="sxs-lookup"><span data-stu-id="2843e-152">TotalRentals</span></span> |
| --- | --- | --- |
|<span data-ttu-id="2843e-153">1/1/2011</span><span class="sxs-lookup"><span data-stu-id="2843e-153">1/1/2011</span></span>|<span data-ttu-id="2843e-154">0</span><span class="sxs-lookup"><span data-stu-id="2843e-154">0</span></span>|<span data-ttu-id="2843e-155">985</span><span class="sxs-lookup"><span data-stu-id="2843e-155">985</span></span>|
|<span data-ttu-id="2843e-156">1/2/2011</span><span class="sxs-lookup"><span data-stu-id="2843e-156">1/2/2011</span></span>|<span data-ttu-id="2843e-157">0</span><span class="sxs-lookup"><span data-stu-id="2843e-157">0</span></span>|<span data-ttu-id="2843e-158">801</span><span class="sxs-lookup"><span data-stu-id="2843e-158">801</span></span>|
|<span data-ttu-id="2843e-159">1/3/2011</span><span class="sxs-lookup"><span data-stu-id="2843e-159">1/3/2011</span></span>|<span data-ttu-id="2843e-160">0</span><span class="sxs-lookup"><span data-stu-id="2843e-160">0</span></span>|<span data-ttu-id="2843e-161">1349</span><span class="sxs-lookup"><span data-stu-id="2843e-161">1349</span></span>|

### <a name="create-input-and-output-classes"></a><span data-ttu-id="2843e-162">建立輸入與輸出類別</span><span class="sxs-lookup"><span data-stu-id="2843e-162">Create input and output classes</span></span>

1. <span data-ttu-id="2843e-163">開啟*Program.cs*檔案,`using`並將現有文句取代為以下內容:</span><span class="sxs-lookup"><span data-stu-id="2843e-163">Open *Program.cs* file and replace the existing `using` statements with the following:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L1-L8)]

1. <span data-ttu-id="2843e-164">建立 `ModelInput` 類別。</span><span class="sxs-lookup"><span data-stu-id="2843e-164">Create `ModelInput` class.</span></span> <span data-ttu-id="2843e-165">在類`Program`下方,添加以下代碼。</span><span class="sxs-lookup"><span data-stu-id="2843e-165">Below the `Program` class, add the following code.</span></span>

    [!code-csharp [ModelInputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L120-L127)]

    <span data-ttu-id="2843e-166">該`ModelInput`類別包含以下欄:</span><span class="sxs-lookup"><span data-stu-id="2843e-166">The `ModelInput` class contains the following columns:</span></span>

    - <span data-ttu-id="2843e-167">**租賃日期**:觀察日期。</span><span class="sxs-lookup"><span data-stu-id="2843e-167">**RentalDate**: The date of the observation.</span></span>
    - <span data-ttu-id="2843e-168">**年份**: 觀測的編碼年份 (0=2011, 1=2012)。</span><span class="sxs-lookup"><span data-stu-id="2843e-168">**Year**: The encoded year of the observation (0=2011, 1=2012).</span></span>
    - <span data-ttu-id="2843e-169">**總租金**:當天自行車租賃的總數。</span><span class="sxs-lookup"><span data-stu-id="2843e-169">**TotalRentals**: The total number of bike rentals for that day.</span></span>

1. <span data-ttu-id="2843e-170">在新`ModelOutput`創建的類下方創建`ModelInput`類。</span><span class="sxs-lookup"><span data-stu-id="2843e-170">Create `ModelOutput` class below the newly created `ModelInput` class.</span></span>

    [!code-csharp [ModelOutputClass](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L129-L136)]

    <span data-ttu-id="2843e-171">該`ModelOutput`類別包含以下欄:</span><span class="sxs-lookup"><span data-stu-id="2843e-171">The `ModelOutput` class contains the following columns:</span></span>

    - <span data-ttu-id="2843e-172">**預測租金**:預測期間的預測值。</span><span class="sxs-lookup"><span data-stu-id="2843e-172">**ForecastedRentals**: The predicted values for the forecasted period.</span></span>
    - <span data-ttu-id="2843e-173">**下邊界租金**:預測期間的預測最小值。</span><span class="sxs-lookup"><span data-stu-id="2843e-173">**LowerBoundRentals**: The predicted minimum values for the forecasted period.</span></span>
    - <span data-ttu-id="2843e-174">**上邊界租金**:預測期間的預測最大值。</span><span class="sxs-lookup"><span data-stu-id="2843e-174">**UpperBoundRentals**: The predicted maximum values for the forecasted period.</span></span>

### <a name="define-paths-and-initialize-variables"></a><span data-ttu-id="2843e-175">定義路徑並初始化變數</span><span class="sxs-lookup"><span data-stu-id="2843e-175">Define paths and initialize variables</span></span>

1. <span data-ttu-id="2843e-176">在`Main`方法內,定義變數以存儲數據的位置、連接字串以及保存訓練的模型的位置。</span><span class="sxs-lookup"><span data-stu-id="2843e-176">Inside the `Main` method, define variables to store the location of your data, connection string, and where to save the trained model.</span></span>

    [!code-csharp [DefinePaths](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L16-L19)]

1. <span data-ttu-id="2843e-177">通過向`Main`方法添加以下行,`mlContext`[`MLContext`](xref:Microsoft.ML.MLContext)使用</span><span class="sxs-lookup"><span data-stu-id="2843e-177">Initialize the `mlContext` variable with a new instance of [`MLContext`](xref:Microsoft.ML.MLContext) by adding the following line to the `Main` method.</span></span>

    [!code-csharp [MLContext](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L21)]

    <span data-ttu-id="2843e-178">該[`MLContext`](xref:Microsoft.ML.MLContext)類是所有ML.NET操作的起點,初始化 mlContext 會創建一個新的ML.NET環境,可以在模型創建工作流對象之間共用。</span><span class="sxs-lookup"><span data-stu-id="2843e-178">The [`MLContext`](xref:Microsoft.ML.MLContext) class is a starting point for all ML.NET operations, and initializing mlContext creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="2843e-179">就概念而言，類似於 Entity Framework 中的 `DBContext`。</span><span class="sxs-lookup"><span data-stu-id="2843e-179">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="2843e-180">載入資料</span><span class="sxs-lookup"><span data-stu-id="2843e-180">Load the data</span></span>

1. <span data-ttu-id="2843e-181">建立`DatabaseLoader`載入類型`ModelInput`的記錄。</span><span class="sxs-lookup"><span data-stu-id="2843e-181">Create `DatabaseLoader` that loads records of type `ModelInput`.</span></span>

    [!code-csharp [CreateDBLoader](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L23)]

1. <span data-ttu-id="2843e-182">定義查詢以從資料庫載入數據。</span><span class="sxs-lookup"><span data-stu-id="2843e-182">Define the query to load the data from the database.</span></span>

    [!code-csharp [DefineSQLQuery](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L25)]

    <span data-ttu-id="2843e-183">ML.NET 演算法期望資料[`Single`](xref:System.Single)的類型 。</span><span class="sxs-lookup"><span data-stu-id="2843e-183">ML.NET algorithms expect data to be of type [`Single`](xref:System.Single).</span></span> <span data-ttu-id="2843e-184">因此,來自資料庫的數值(單[`Real`](xref:System.Data.SqlDbType)精度浮點值)必須轉換為[`Real`](xref:System.Data.SqlDbType)。</span><span class="sxs-lookup"><span data-stu-id="2843e-184">Therefore, numerical values coming from the database that are not of type [`Real`](xref:System.Data.SqlDbType), a single-precision floating-point value, have to be converted to [`Real`](xref:System.Data.SqlDbType).</span></span>

    <span data-ttu-id="2843e-185">和`Year``TotalRental`列都是資料庫中的整數類型。</span><span class="sxs-lookup"><span data-stu-id="2843e-185">The `Year` and `TotalRental` columns are both integer types in the database.</span></span> <span data-ttu-id="2843e-186">使用`CAST`內建函數,它們都強制轉換`Real`為 。</span><span class="sxs-lookup"><span data-stu-id="2843e-186">Using the `CAST` built-in function, they are both cast to `Real`.</span></span>

1. <span data-ttu-id="2843e-187">建立`DatabaseSource`以連接到資料庫並執行查詢。</span><span class="sxs-lookup"><span data-stu-id="2843e-187">Create a `DatabaseSource` to connect to the database and execute the query.</span></span>

    [!code-csharp [CreateDBSource](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L27-L29)]

1. <span data-ttu-id="2843e-188">將資料載入到中`IDataView`。</span><span class="sxs-lookup"><span data-stu-id="2843e-188">Load the data into an `IDataView`.</span></span>

    [!code-csharp [LoadData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L31)]

1. <span data-ttu-id="2843e-189">數據集包含兩年的數據。</span><span class="sxs-lookup"><span data-stu-id="2843e-189">The dataset contains two years worth of data.</span></span> <span data-ttu-id="2843e-190">只有第一年的數據用於培訓,第二年用於將實際值與模型生成的預測進行比較。</span><span class="sxs-lookup"><span data-stu-id="2843e-190">Only data from the first year is used for training, the second year is held out to compare the actual values against the forecast produced by the model.</span></span> <span data-ttu-id="2843e-191">使用[`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*)轉換篩選數據。</span><span class="sxs-lookup"><span data-stu-id="2843e-191">Filter the data using the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn*) transform.</span></span>

    [!code-csharp [SplitData](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L33-L34)]

    <span data-ttu-id="2843e-192">對於第一年,僅通過將`Year``upperBound`參數設置為 1 來選擇列中小於 1 的值。</span><span class="sxs-lookup"><span data-stu-id="2843e-192">For the first year, only the values in the `Year` column less than 1 are selected by setting the `upperBound` parameter to 1.</span></span> <span data-ttu-id="2843e-193">相反,對於第二年,通過將`lowerBound`參數設置為 1 來選擇大於或等於 1 的值。</span><span class="sxs-lookup"><span data-stu-id="2843e-193">Conversely, for the second year, values greater than or equal to 1 are selected by setting the `lowerBound` parameter to 1.</span></span>

## <a name="define-time-series-analysis-pipeline"></a><span data-ttu-id="2843e-194">定義時間序列分析導管</span><span class="sxs-lookup"><span data-stu-id="2843e-194">Define time series analysis pipeline</span></span>

1. <span data-ttu-id="2843e-195">定義使用[Ssa 預測器](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator)預測時間序列數據集中的值的管道。</span><span class="sxs-lookup"><span data-stu-id="2843e-195">Define a pipeline that uses the [SsaForecastingEstimator](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator) to forecast values in a time-series dataset.</span></span>

    [!code-csharp [DefinePipeline](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L36-L45)]

    <span data-ttu-id="2843e-196">獲取`forecastingPipeline`第一年的 365 個數據點,採樣或拆分時間序列`seriesLength`數據集為 參數指定的 30 天(每月)間隔。</span><span class="sxs-lookup"><span data-stu-id="2843e-196">The `forecastingPipeline` takes 365 data points for the first year and samples or splits the time-series dataset into 30-day (monthly) intervals as specified by the `seriesLength` parameter.</span></span> <span data-ttu-id="2843e-197">每個樣本都通過每周或 7 天的視窗進行分析。</span><span class="sxs-lookup"><span data-stu-id="2843e-197">Each of these samples is analyzed through weekly or a 7-day window.</span></span> <span data-ttu-id="2843e-198">在確定下一個期間的預測值時,使用前七天的值進行預測。</span><span class="sxs-lookup"><span data-stu-id="2843e-198">When determining what the forecasted value for the next period(s) is, the values from previous seven days are used to make a prediction.</span></span> <span data-ttu-id="2843e-199">模型設置為預測`horizon`參數定義的未來七個週期。</span><span class="sxs-lookup"><span data-stu-id="2843e-199">The model is set to forecast seven periods into the future as defined by the `horizon` parameter.</span></span> <span data-ttu-id="2843e-200">由於預測是一個知情的猜測,它並不總是 100% 準確。</span><span class="sxs-lookup"><span data-stu-id="2843e-200">Because a forecast is an informed guess, it's not always 100% accurate.</span></span> <span data-ttu-id="2843e-201">因此,最好瞭解由上限和下限定義的最佳和最壞情況下的值範圍。</span><span class="sxs-lookup"><span data-stu-id="2843e-201">Therefore, it's good to know the range of values in the best and worst-case scenarios as defined by the upper and lower bounds.</span></span> <span data-ttu-id="2843e-202">在這種情況下,下限和上限的置信度設置為 95%。</span><span class="sxs-lookup"><span data-stu-id="2843e-202">In this case, the level of confidence for the lower and upper bounds is set to 95%.</span></span> <span data-ttu-id="2843e-203">置信度可以相應增加或降低。</span><span class="sxs-lookup"><span data-stu-id="2843e-203">The confidence level can be increased or decreased accordingly.</span></span> <span data-ttu-id="2843e-204">值越高,上邊界和下邊界之間的範圍越寬,以實現所需的置信度。</span><span class="sxs-lookup"><span data-stu-id="2843e-204">The higher the value, the wider the range is between the upper and lower bounds to achieve the desired level of confidence.</span></span>

1. <span data-ttu-id="2843e-205">使用[`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*)方法訓練模型並將數據與先前定義的`forecastingPipeline`數據配合。</span><span class="sxs-lookup"><span data-stu-id="2843e-205">Use the [`Fit`](xref:Microsoft.ML.Transforms.TimeSeries.SsaForecastingEstimator.Fit*) method to train the model and fit the data to the previously defined `forecastingPipeline`.</span></span>

    [!code-csharp [TrainModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L47)]

## <a name="evaluate-the-model"></a><span data-ttu-id="2843e-206">評估模型</span><span class="sxs-lookup"><span data-stu-id="2843e-206">Evaluate the model</span></span>

<span data-ttu-id="2843e-207">通過預測下一年的數據並將其與實際值進行比較,評估模型的性能。</span><span class="sxs-lookup"><span data-stu-id="2843e-207">Evaluate how well the model performs by forecasting next year's data and comparing it against the actual values.</span></span>

1. <span data-ttu-id="2843e-208">在方法`Main`下方,創建一種`Evaluate`稱為 的新實用程式方法。</span><span class="sxs-lookup"><span data-stu-id="2843e-208">Below the `Main` method, create a new utility method called `Evaluate`.</span></span>

    ```csharp
    static void Evaluate(IDataView testData, ITransformer model, MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="2843e-209">在該方法`Evaluate`內,使用該方法對訓練的模型[`Transform`](xref:Microsoft.ML.ITransformer.Transform*)進行 預測第二年的數據。</span><span class="sxs-lookup"><span data-stu-id="2843e-209">Inside the `Evaluate` method, forecast the second year's data by using the [`Transform`](xref:Microsoft.ML.ITransformer.Transform*) method with the trained model.</span></span>

    [!code-csharp [EvaluateForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L62)]

1. <span data-ttu-id="2843e-210">使用[`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*)方法從數據獲取實際值。</span><span class="sxs-lookup"><span data-stu-id="2843e-210">Get the actual values from the data by using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

    [!code-csharp [GetActualRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L65-L67)]

1. <span data-ttu-id="2843e-211">使用[`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*)方法獲取預測值。</span><span class="sxs-lookup"><span data-stu-id="2843e-211">Get the forecast values by using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable*) method.</span></span>

    [!code-csharp [GetForecastRentals](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L70-L72)]

1. <span data-ttu-id="2843e-212">計算實際值和預測值之間的差異,通常稱為錯誤。</span><span class="sxs-lookup"><span data-stu-id="2843e-212">Calculate the difference between the actual and forecast values, commonly referred to as the error.</span></span>

    [!code-csharp [CalculateError](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L75)]

1. <span data-ttu-id="2843e-213">通過計算平均絕對誤差和根均值平方誤差值來衡量性能。</span><span class="sxs-lookup"><span data-stu-id="2843e-213">Measure performance by computing the Mean Absolute Error and Root Mean Squared Error values.</span></span>

    [!code-csharp [CalculateMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L78-L79)]

    <span data-ttu-id="2843e-214">為了評估性能,使用以下指標:</span><span class="sxs-lookup"><span data-stu-id="2843e-214">To evaluate performance, the following metrics are used:</span></span>

    - <span data-ttu-id="2843e-215">**平均絕對誤差**:衡量預測與實際值的接近程度。</span><span class="sxs-lookup"><span data-stu-id="2843e-215">**Mean Absolute Error**: Measures how close predictions are to the actual value.</span></span> <span data-ttu-id="2843e-216">此值的範圍介於 0 和無窮大之間。</span><span class="sxs-lookup"><span data-stu-id="2843e-216">This value ranges between 0 and infinity.</span></span> <span data-ttu-id="2843e-217">接近 0,模型的品質越好。</span><span class="sxs-lookup"><span data-stu-id="2843e-217">The closer to 0, the better the quality of the model.</span></span>
    - <span data-ttu-id="2843e-218">**根均值平方錯誤**:匯總模型中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="2843e-218">**Root Mean Squared Error**: Summarizes the error in the model.</span></span> <span data-ttu-id="2843e-219">此值的範圍介於 0 和無窮大之間。</span><span class="sxs-lookup"><span data-stu-id="2843e-219">This value ranges between 0 and infinity.</span></span> <span data-ttu-id="2843e-220">接近 0,模型的品質越好。</span><span class="sxs-lookup"><span data-stu-id="2843e-220">The closer to 0, the better the quality of the model.</span></span>

1. <span data-ttu-id="2843e-221">將指標輸出到主控台。</span><span class="sxs-lookup"><span data-stu-id="2843e-221">Output the metrics to the console.</span></span>

    [!code-csharp [OutputMetrics](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L82-L85)]

1. <span data-ttu-id="2843e-222">在`Evaluate``Main`方法中使用 方法。</span><span class="sxs-lookup"><span data-stu-id="2843e-222">Use the `Evaluate` method inside the `Main` method.</span></span>

    [!code-csharp [EvaluateModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L49)]

## <a name="save-the-model"></a><span data-ttu-id="2843e-223">儲存模型</span><span class="sxs-lookup"><span data-stu-id="2843e-223">Save the model</span></span>

<span data-ttu-id="2843e-224">如果您對模型感到滿意,請將其保存以供以後在其他應用程式中使用。</span><span class="sxs-lookup"><span data-stu-id="2843e-224">If you're satisfied with your model, save it for later use in other applications.</span></span>

1. <span data-ttu-id="2843e-225">在`Main`方法中,建立[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602)一個 。</span><span class="sxs-lookup"><span data-stu-id="2843e-225">In the `Main` method, create a [`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602).</span></span> <span data-ttu-id="2843e-226">[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602)是進行單一預測的便捷方法。</span><span class="sxs-lookup"><span data-stu-id="2843e-226">[`TimeSeriesPredictionEngine`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602) is a convenience method to make single predictions.</span></span>

    [!code-csharp [CreateTimeSeriesEngine](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L51)]

1. <span data-ttu-id="2843e-227">將模型保存到以前定義的`MLModel.zip``modelPath`變數指定的檔中。</span><span class="sxs-lookup"><span data-stu-id="2843e-227">Save the model to a file called `MLModel.zip` as specified by the previously defined `modelPath` variable.</span></span> <span data-ttu-id="2843e-228">使用[`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*)方法保存模型。</span><span class="sxs-lookup"><span data-stu-id="2843e-228">Use the [`Checkpoint`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.CheckPoint*) method to save the model.</span></span>

    [!code-csharp [SaveModel](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L52)]

## <a name="use-the-model-to-forecast-demand"></a><span data-ttu-id="2843e-229">使用模型預測需求</span><span class="sxs-lookup"><span data-stu-id="2843e-229">Use the model to forecast demand</span></span>

1. <span data-ttu-id="2843e-230">在方法`Evaluate`下方,創建一種`Forecast`稱為 的新實用程式方法。</span><span class="sxs-lookup"><span data-stu-id="2843e-230">Below the `Evaluate` method, create a new utility method called `Forecast`.</span></span>

    ```csharp
    static void Forecast(IDataView testData, int horizon, TimeSeriesPredictionEngine<ModelInput, ModelOutput> forecaster, MLContext mlContext)
    {

    }
    ```

1. <span data-ttu-id="2843e-231">在該方法`Forecast`內,[`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*)使用方法預測未來七天的租金。</span><span class="sxs-lookup"><span data-stu-id="2843e-231">Inside the `Forecast` method, use the [`Predict`](xref:Microsoft.ML.Transforms.TimeSeries.TimeSeriesPredictionEngine%602.Predict*) method to forecast rentals for the next seven days.</span></span>

    [!code-csharp [SingleForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L91)]

1. <span data-ttu-id="2843e-232">對齊七個週期的實際值和預測值。</span><span class="sxs-lookup"><span data-stu-id="2843e-232">Align the actual and forecast values for seven periods.</span></span>

    [!code-csharp [GetForecastOutput](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L93-L108)]

1. <span data-ttu-id="2843e-233">反覆運算預測輸出並將其顯示在控制臺上。</span><span class="sxs-lookup"><span data-stu-id="2843e-233">Iterate through the forecast output and display it on the console.</span></span>

    [!code-csharp [DisplayForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L111-L116)]

## <a name="run-the-application"></a><span data-ttu-id="2843e-234">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="2843e-234">Run the application</span></span>

1. <span data-ttu-id="2843e-235">在`Main`方法內,調`Forecast`用 方法。</span><span class="sxs-lookup"><span data-stu-id="2843e-235">Inside the `Main` method, call the `Forecast` method.</span></span>

    [!code-csharp [BuildForecast](~/machinelearning-samples/samples/csharp/getting-started/Forecasting_BikeSharingDemand/BikeDemandForecasting/Program.cs#L54)]

1. <span data-ttu-id="2843e-236">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="2843e-236">Run the application.</span></span> <span data-ttu-id="2843e-237">類似於下面的輸出應出現在控制臺上。</span><span class="sxs-lookup"><span data-stu-id="2843e-237">Output similar to that below should appear on the console.</span></span> <span data-ttu-id="2843e-238">為簡潔起見,輸出已壓縮。</span><span class="sxs-lookup"><span data-stu-id="2843e-238">For brevity, the output has been condensed.</span></span>

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

<span data-ttu-id="2843e-239">檢查實際值與預測值將顯示以下關係:</span><span class="sxs-lookup"><span data-stu-id="2843e-239">Inspection of the actual and forecasted values shows the following relationships:</span></span>

![實際與預測比較](./media/time-series-demand-forecasting/forecast.png)

<span data-ttu-id="2843e-241">雖然預測值沒有預測確切的租金數量,但它們提供了更窄的值範圍,使操作能夠優化其資源的使用。</span><span class="sxs-lookup"><span data-stu-id="2843e-241">While the forecasted values are not predicting the exact number of rentals, they provide a more narrow range of values that allows an operation to optimize their use of resources.</span></span>

<span data-ttu-id="2843e-242">恭喜！</span><span class="sxs-lookup"><span data-stu-id="2843e-242">Congratulations!</span></span> <span data-ttu-id="2843e-243">現在,您已成功構建了時間序列機器學習模型,以預測自行車租賃需求。</span><span class="sxs-lookup"><span data-stu-id="2843e-243">You've now successfully built a time series machine learning model to forecast bike rental demand.</span></span>

<span data-ttu-id="2843e-244">您可以在[dotnet/機器學習範例](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand)儲存庫中找到本教程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="2843e-244">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/Forecasting_BikeSharingDemand) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2843e-245">後續步驟</span><span class="sxs-lookup"><span data-stu-id="2843e-245">Next steps</span></span>

- [<span data-ttu-id="2843e-246">ML.NET 中的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="2843e-246">Machine learning tasks in ML.NET</span></span>](../resources/tasks.md)
- [<span data-ttu-id="2843e-247">改善模型正確性</span><span class="sxs-lookup"><span data-stu-id="2843e-247">Improve model accuracy</span></span>](../resources/improve-machine-learning-model-ml-net.md)
