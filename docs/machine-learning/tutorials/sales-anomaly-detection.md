---
title: 教學課程：偵測產品銷售中的異常
description: 了解如何建置產品銷售資料的異常偵測應用程式。 此教學課程會示範如何在 Visual Studio 2019 中使用 C# 建立 .NET Core 主控台應用程式。
ms.date: 07/17/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: ed75f1ba0b102ba73eb5671667b5731519c12eb0
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929047"
---
# <a name="tutorial-detect-anomalies-in-product-sales-with-mlnet"></a><span data-ttu-id="4cb59-104">教學課程：使用 ML.NET 偵測產品銷售中的異常</span><span class="sxs-lookup"><span data-stu-id="4cb59-104">Tutorial: Detect anomalies in product sales with ML.NET</span></span>

<span data-ttu-id="4cb59-105">了解如何建置產品銷售資料的異常偵測應用程式。</span><span class="sxs-lookup"><span data-stu-id="4cb59-105">Learn how to build an anomaly detection application for product sales data.</span></span> <span data-ttu-id="4cb59-106">此教學課程會示範如何在 Visual Studio 中使用 C# 建立 .NET Core 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="4cb59-106">This tutorial creates a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="4cb59-107">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="4cb59-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="4cb59-108">載入資料</span><span class="sxs-lookup"><span data-stu-id="4cb59-108">Load the data</span></span>
> * <span data-ttu-id="4cb59-109">建立用於尖峰異常偵測的轉換</span><span class="sxs-lookup"><span data-stu-id="4cb59-109">Create a transform for spike anomaly detection</span></span>
> * <span data-ttu-id="4cb59-110">使用轉換偵測尖峰異常</span><span class="sxs-lookup"><span data-stu-id="4cb59-110">Detect spike anomalies with the transform</span></span>
> * <span data-ttu-id="4cb59-111">建立用於變更點異常偵測的轉換</span><span class="sxs-lookup"><span data-stu-id="4cb59-111">Create a transform for change point anomaly detection</span></span>
> * <span data-ttu-id="4cb59-112">使用轉換偵測變更點異常</span><span class="sxs-lookup"><span data-stu-id="4cb59-112">Detect change point anomalies with the transform</span></span>

<span data-ttu-id="4cb59-113">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="4cb59-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4cb59-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="4cb59-114">Prerequisites</span></span>

* <span data-ttu-id="4cb59-115">已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="4cb59-115">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

* [<span data-ttu-id="4cb59-116">product-sales.csv 資料集</span><span class="sxs-lookup"><span data-stu-id="4cb59-116">The product-sales.csv dataset</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> <span data-ttu-id="4cb59-117">`product-sales.csv` 中的資料格式是以 “Shampoo Sales Over a Three Year Period” (洗髮精三年銷售資料) 資料集為基礎，此資料集最初源自 DataMarket，由時間序列資料程式庫 (TSDL) 提供，建立者為 Rob Hyndman。</span><span class="sxs-lookup"><span data-stu-id="4cb59-117">The data format in `product-sales.csv` is based on the dataset “Shampoo Sales Over a Three Year Period” originally sourced from DataMarket and provided by Time Series Data Library (TSDL), created by Rob Hyndman.</span></span>
> <span data-ttu-id="4cb59-118">“Shampoo Sales Over a Three Year Period” (洗髮精三年銷售資料) 資料集已獲 DataMarket 的預設 Open License 授權。</span><span class="sxs-lookup"><span data-stu-id="4cb59-118">“Shampoo Sales Over a Three Year Period” Dataset Licensed Under the DataMarket Default Open License.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="4cb59-119">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="4cb59-119">Create a console application</span></span>

1. <span data-ttu-id="4cb59-120">建立稱為 "ProductSalesAnomalyDetection" 的 **.NET Core 主控台應用程式**。</span><span class="sxs-lookup"><span data-stu-id="4cb59-120">Create a **.NET Core Console Application** called "ProductSalesAnomalyDetection".</span></span>

2. <span data-ttu-id="4cb59-121">在您專案中建立名為 *Data* 的目錄以儲存資料集檔案。</span><span class="sxs-lookup"><span data-stu-id="4cb59-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="4cb59-122">安裝「Microsoft.ML NuGet 套件」：</span><span class="sxs-lookup"><span data-stu-id="4cb59-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="4cb59-123">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="4cb59-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="4cb59-124">選擇 "nuget.org" 作為 [套件來源]、選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、從清單中選取 **v1.0.0** 套件，然後選取 [安裝] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4cb59-124">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select the **v1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="4cb59-125">在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。</span><span class="sxs-lookup"><span data-stu-id="4cb59-125">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="4cb59-126">為 **Microsoft.ML.TimeSeries v0.12.0** 重複這些步驟。</span><span class="sxs-lookup"><span data-stu-id="4cb59-126">Repeat these steps for **Microsoft.ML.TimeSeries v0.12.0**.</span></span>

4. <span data-ttu-id="4cb59-127">在您的 *Program.cs* 檔案最上方新增下列 `using` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="4cb59-127">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="4cb59-128">下載您的資料</span><span class="sxs-lookup"><span data-stu-id="4cb59-128">Download your data</span></span>

1. <span data-ttu-id="4cb59-129">下載資料集，並儲存至您先前建立的 *Data* 資料夾：</span><span class="sxs-lookup"><span data-stu-id="4cb59-129">Download the dataset and save it to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="4cb59-130">以滑鼠右鍵按一下 [*product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)，然後選取 [另存連結] 或 [另存目標]</span><span class="sxs-lookup"><span data-stu-id="4cb59-130">Right click on [*product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="4cb59-131">請務必將 \*.csv 檔案儲存至 *Data* 資料夾，或儲存在其他位置之後將 \*.csv 檔案移至 *Data* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4cb59-131">Make sure you either save the \*.csv file to the *Data* folder, or after you save it elsewhere, move the \*.csv file to the *Data* folder.</span></span>

2. <span data-ttu-id="4cb59-132">在 [方案總管] 中，以滑鼠右鍵按一下 \*.csv 檔案，並選取 [內容]。</span><span class="sxs-lookup"><span data-stu-id="4cb59-132">In Solution Explorer, right-click the \*.csv file and select **Properties**.</span></span> <span data-ttu-id="4cb59-133">在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。</span><span class="sxs-lookup"><span data-stu-id="4cb59-133">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="4cb59-134">下表是 \*.csv 檔案的資料預覽：</span><span class="sxs-lookup"><span data-stu-id="4cb59-134">The following table is a data preview from your \*.csv file:</span></span>

|<span data-ttu-id="4cb59-135">Month</span><span class="sxs-lookup"><span data-stu-id="4cb59-135">Month</span></span>  |<span data-ttu-id="4cb59-136">ProductSales</span><span class="sxs-lookup"><span data-stu-id="4cb59-136">ProductSales</span></span> |
|-------|-------------|
|<span data-ttu-id="4cb59-137">1 月 1 日</span><span class="sxs-lookup"><span data-stu-id="4cb59-137">1-Jan</span></span>  |    <span data-ttu-id="4cb59-138">271</span><span class="sxs-lookup"><span data-stu-id="4cb59-138">271</span></span>      |
|<span data-ttu-id="4cb59-139">1 月 2 日</span><span class="sxs-lookup"><span data-stu-id="4cb59-139">2-Jan</span></span>  |    <span data-ttu-id="4cb59-140">150.9</span><span class="sxs-lookup"><span data-stu-id="4cb59-140">150.9</span></span>    |
|<span data-ttu-id="4cb59-141">.....</span><span class="sxs-lookup"><span data-stu-id="4cb59-141">.....</span></span>  |    <span data-ttu-id="4cb59-142">.....</span><span class="sxs-lookup"><span data-stu-id="4cb59-142">.....</span></span>    |
|<span data-ttu-id="4cb59-143">2 月 1 日</span><span class="sxs-lookup"><span data-stu-id="4cb59-143">1-Feb</span></span>  |    <span data-ttu-id="4cb59-144">199.3</span><span class="sxs-lookup"><span data-stu-id="4cb59-144">199.3</span></span>    |
|<span data-ttu-id="4cb59-145">.....</span><span class="sxs-lookup"><span data-stu-id="4cb59-145">.....</span></span>  |    <span data-ttu-id="4cb59-146">.....</span><span class="sxs-lookup"><span data-stu-id="4cb59-146">.....</span></span>    |

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="4cb59-147">建立類別及定義路徑</span><span class="sxs-lookup"><span data-stu-id="4cb59-147">Create classes and define paths</span></span>

<span data-ttu-id="4cb59-148">接下來，定義您的輸入和預測類別資料結構。</span><span class="sxs-lookup"><span data-stu-id="4cb59-148">Next, define your input and prediction class data structures.</span></span>

<span data-ttu-id="4cb59-149">將新類別新增至專案：</span><span class="sxs-lookup"><span data-stu-id="4cb59-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="4cb59-150">在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取 [新增] > [新項目]。</span><span class="sxs-lookup"><span data-stu-id="4cb59-150">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="4cb59-151">在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *ProductSalesData.cs*。</span><span class="sxs-lookup"><span data-stu-id="4cb59-151">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *ProductSalesData.cs*.</span></span> <span data-ttu-id="4cb59-152">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4cb59-152">Then, select the **Add** button.</span></span>

   <span data-ttu-id="4cb59-153">隨即在程式碼編輯器中開啟 *ProductSalesData.cs* 檔案。</span><span class="sxs-lookup"><span data-stu-id="4cb59-153">The *ProductSalesData.cs* file opens in the code editor.</span></span>

3. <span data-ttu-id="4cb59-154">將下列 `using` 陳述式新增至 *ProductSalesData.cs* 的上方：</span><span class="sxs-lookup"><span data-stu-id="4cb59-154">Add the following `using` statement to the top of *ProductSalesData.cs*:</span></span>

   ```csharp
   using Microsoft.ML.Data;
   ```

4. <span data-ttu-id="4cb59-155">移除現有類別定義，然後將下列具有 `ProductSalesData` 和 `ProductSalesPrediction` 兩個類別的程式碼新增至 *ProductSalesData.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="4cb59-155">Remove the existing class definition and add the following code, which has two classes `ProductSalesData` and `ProductSalesPrediction`, to the *ProductSalesData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/ProductSalesData.cs#DeclareTypes "Declare data record types")]

    <span data-ttu-id="4cb59-156">`ProductSalesData` 會指定輸入資料類別。</span><span class="sxs-lookup"><span data-stu-id="4cb59-156">`ProductSalesData` specifies an input data class.</span></span> <span data-ttu-id="4cb59-157">[LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) 屬性會指定應該載入資料集內的哪些資料行 (依資料行索引)。</span><span class="sxs-lookup"><span data-stu-id="4cb59-157">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span>

    <span data-ttu-id="4cb59-158">`ProductSalesPrediction` 指定預測資料類別。</span><span class="sxs-lookup"><span data-stu-id="4cb59-158">`ProductSalesPrediction` specifies the prediction data class.</span></span> <span data-ttu-id="4cb59-159">對於異常偵測，預測包含警示，用來指出是否有異常、原始分數及 P 值。</span><span class="sxs-lookup"><span data-stu-id="4cb59-159">For anomaly detection, the prediction consists of an alert to indicate whether there is an anomaly, a raw score, and p-value.</span></span> <span data-ttu-id="4cb59-160">P 值越接近 0，就越可能發生異常。</span><span class="sxs-lookup"><span data-stu-id="4cb59-160">The closer the p-value is to 0, the more likely an anomaly has occurred.</span></span>

5. <span data-ttu-id="4cb59-161">建立兩個全域欄位，以保存最近所下載資料集檔案路徑與儲存的模型檔案路徑：</span><span class="sxs-lookup"><span data-stu-id="4cb59-161">Create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

    * <span data-ttu-id="4cb59-162">`_dataPath` 包含用來將模型定型的資料集路徑。</span><span class="sxs-lookup"><span data-stu-id="4cb59-162">`_dataPath` has the path to the dataset used to train the model.</span></span>
    * <span data-ttu-id="4cb59-163">`_docsize` 有資料集檔案的記錄數目。</span><span class="sxs-lookup"><span data-stu-id="4cb59-163">`_docsize` has the number of records in dataset file.</span></span> <span data-ttu-id="4cb59-164">您會使用 `_docSize` 來計算 `pvalueHistoryLength`。</span><span class="sxs-lookup"><span data-stu-id="4cb59-164">You'll use `_docSize` to calculate `pvalueHistoryLength`.</span></span>

6. <span data-ttu-id="4cb59-165">將下列程式碼新增至緊接在 `Main` 方法上方的一行，以指定這些路徑：</span><span class="sxs-lookup"><span data-stu-id="4cb59-165">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

    [!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DeclareGlobalVariables "Declare global variables")]

### <a name="initialize-variables-in-main"></a><span data-ttu-id="4cb59-166">在 Main 中初始化變數</span><span class="sxs-lookup"><span data-stu-id="4cb59-166">Initialize variables in Main</span></span>

1. <span data-ttu-id="4cb59-167">將 `Main` 方法中的 `Console.WriteLine("Hello World!")` 程式碼替換成下列程式碼，宣告並初始化 `mlContext` 變數：</span><span class="sxs-lookup"><span data-stu-id="4cb59-167">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

    [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateMLContext "Create the ML Context")]

    <span data-ttu-id="4cb59-168">[MLContext 類別](xref:Microsoft.ML.MLContext)是所有 ML.NET 作業的起點，且初始化 `mlContext` 會建立新的 ML.NET 環境，其可在模型建立工作流程物件之間共用。</span><span class="sxs-lookup"><span data-stu-id="4cb59-168">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="4cb59-169">就概念而言，類似於 Entity Framework 中的 `DBContext`。</span><span class="sxs-lookup"><span data-stu-id="4cb59-169">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="load-the-data"></a><span data-ttu-id="4cb59-170">載入資料</span><span class="sxs-lookup"><span data-stu-id="4cb59-170">Load the data</span></span>

<span data-ttu-id="4cb59-171">ML.NET 中的資料以 [IDataView 類別](xref:Microsoft.ML.IDataView) 表示。</span><span class="sxs-lookup"><span data-stu-id="4cb59-171">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="4cb59-172">`IDataView` 是彈性且有效率的表格式資料描述方式 (數值和文字)。</span><span class="sxs-lookup"><span data-stu-id="4cb59-172">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="4cb59-173">資料可以從文字檔或其他來源 (例如 SQL 資料庫或記錄檔) 載入至 `IDataView` 物件。</span><span class="sxs-lookup"><span data-stu-id="4cb59-173">Data can be loaded from a text file or from other sources (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="4cb59-174">將下列程式碼新增為 `Main()` 方法的下一行：</span><span class="sxs-lookup"><span data-stu-id="4cb59-174">Add the following code as the next line of the `Main()` method:</span></span>

    [!code-csharp[LoadData](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="4cb59-175">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) 會定義資料結構描述並讀入檔案中。</span><span class="sxs-lookup"><span data-stu-id="4cb59-175">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="4cb59-176">會接受資料路徑變數然後傳回 `IDataView`。</span><span class="sxs-lookup"><span data-stu-id="4cb59-176">It takes in the data path variables and returns an `IDataView`.</span></span>

## <a name="time-series-anomaly-detection"></a><span data-ttu-id="4cb59-177">時間序列異常偵測</span><span class="sxs-lookup"><span data-stu-id="4cb59-177">Time series anomaly detection</span></span>

<span data-ttu-id="4cb59-178">異常偵測會標記未預期或不尋常的事件或行為。</span><span class="sxs-lookup"><span data-stu-id="4cb59-178">Anomaly detection flags unexpected or unusual events or behaviors.</span></span> <span data-ttu-id="4cb59-179">它可提供尋找問題的線索，協助您回答「這奇不奇怪？」的問題。</span><span class="sxs-lookup"><span data-stu-id="4cb59-179">It gives clues where to look for problems and helps you answer the question "Is this weird?".</span></span>

![奇不奇怪](./media/sales-anomaly-detection/anomalydetection.png)

<span data-ttu-id="4cb59-181">異常偵測是偵測時間序列資料極端值的程序，它們是指定輸入時間序列中非預期或「奇怪」行為的資料點。</span><span class="sxs-lookup"><span data-stu-id="4cb59-181">Anomaly detection is the process of detecting time-series data outliers; points on a given input time-series where the behavior isn't what was expected, or "weird".</span></span>

<span data-ttu-id="4cb59-182">異常偵測適用於許多方面。</span><span class="sxs-lookup"><span data-stu-id="4cb59-182">Anomaly detection can be useful in lots of ways.</span></span> <span data-ttu-id="4cb59-183">若是執行個體：</span><span class="sxs-lookup"><span data-stu-id="4cb59-183">For instance:</span></span>

<span data-ttu-id="4cb59-184">如果您有一輛汽車，您可能想知道：油量表的讀數是否正常，還是漏油了？</span><span class="sxs-lookup"><span data-stu-id="4cb59-184">If you have a car, you might want to know: Is this oil gauge reading normal, or do I have a leak?</span></span>
<span data-ttu-id="4cb59-185">如果您要監視的耗電量，您可能想知道：是否斷電？</span><span class="sxs-lookup"><span data-stu-id="4cb59-185">If you're monitoring power consumption, you’d want to know: Is there an outage?</span></span>

<span data-ttu-id="4cb59-186">可偵測到的時間序列異常有兩種：</span><span class="sxs-lookup"><span data-stu-id="4cb59-186">There are two types of time series anomalies that can be detected:</span></span>

* <span data-ttu-id="4cb59-187">**尖峰**表示系統中異常行為的暫時高載。</span><span class="sxs-lookup"><span data-stu-id="4cb59-187">**Spikes** indicate temporary bursts of anomalous behavior in the system.</span></span>

* <span data-ttu-id="4cb59-188">**變更點**表示系統開頭的持續性隨著時間變更。</span><span class="sxs-lookup"><span data-stu-id="4cb59-188">**Change points** indicate the beginning of persistent changes over time in the system.</span></span>

<span data-ttu-id="4cb59-189">在 ML.NET 中，IID 尖峰偵測或 IID 變更點偵測演算法都很適合[獨立同分布資料集](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables)。</span><span class="sxs-lookup"><span data-stu-id="4cb59-189">In ML.NET, The IID Spike Detection or IID Change point Detection algorithms are suited for [independent and identically distributed datasets](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span></span>

<span data-ttu-id="4cb59-190">不同於其他教學課程中的模型，時間序列異常偵測器轉換會直接對輸入資料進行操作。</span><span class="sxs-lookup"><span data-stu-id="4cb59-190">Unlike the models in the other tutorials, the time series anomaly detector transforms operate directly on input data.</span></span> <span data-ttu-id="4cb59-191">`IEstimator.Fit()` 方法不需要定型資料來產生轉換。</span><span class="sxs-lookup"><span data-stu-id="4cb59-191">The `IEstimator.Fit()` method does not need training data to produce the transform.</span></span> <span data-ttu-id="4cb59-192">不過，它需要資料結構描述，這是由 `ProductSalesData` 空白清單所產生的資料檢視所提供。</span><span class="sxs-lookup"><span data-stu-id="4cb59-192">It does need the data schema though, which is provided by a data view generated from an empty list of `ProductSalesData`.</span></span>

<span data-ttu-id="4cb59-193">您要分析相同的產品銷售資料，偵測尖峰和變更點。</span><span class="sxs-lookup"><span data-stu-id="4cb59-193">You'll analyze the same product sales data to detect spikes and change points.</span></span> <span data-ttu-id="4cb59-194">尖峰偵測和變更點偵測的建置與定型模型程序相同，主要差異在於使用的特定偵測演算法。</span><span class="sxs-lookup"><span data-stu-id="4cb59-194">The building and training model process is the same for spike detection and change point detection; the main difference is the specific detection algorithm used.</span></span>

## <a name="spike-detection"></a><span data-ttu-id="4cb59-195">尖峰偵測</span><span class="sxs-lookup"><span data-stu-id="4cb59-195">Spike detection</span></span>

<span data-ttu-id="4cb59-196">尖峰偵測目標是找出明顯有別於大部分時間序列資料值的突然卻短暫暴增。</span><span class="sxs-lookup"><span data-stu-id="4cb59-196">The goal of spike detection is to identify sudden yet temporary bursts that significantly differ from the majority of the time series data values.</span></span> <span data-ttu-id="4cb59-197">請務必及時偵測這些可疑的罕見項目、事件或觀測，將影響降至最低。</span><span class="sxs-lookup"><span data-stu-id="4cb59-197">It's important to detect these suspicious rare items, events, or observations in a timely manner to be minimized.</span></span> <span data-ttu-id="4cb59-198">下列方法可用來偵測各種異常，例如：中斷、網路攻擊或病毒式 Web 內容。</span><span class="sxs-lookup"><span data-stu-id="4cb59-198">The following approach can be used to detect a variety of anomalies such as: outages, cyber-attacks, or viral web content.</span></span> <span data-ttu-id="4cb59-199">下圖是時間序列資料集的尖峰範例：</span><span class="sxs-lookup"><span data-stu-id="4cb59-199">The following image is an example of spikes in a time series dataset:</span></span>

![SpikeDetection](./media/sales-anomaly-detection/SpikeDetection.png)

### <a name="add-the-createemptydataview-method"></a><span data-ttu-id="4cb59-201">新增 CreateEmptyDataView() 方法</span><span class="sxs-lookup"><span data-stu-id="4cb59-201">Add the CreateEmptyDataView() method</span></span>

<span data-ttu-id="4cb59-202">將下列方法新增至 `Program.cs`：</span><span class="sxs-lookup"><span data-stu-id="4cb59-202">Add the following method to `Program.cs`:</span></span>

[!code-csharp[CreateEmptyDataView](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEmptyDataView)]

<span data-ttu-id="4cb59-203">`CreateEmptyDataView()` 會產生空白資料檢視物件，其包含將作為 `IEstimator.Fit()` 方法輸入的正確結構描述。</span><span class="sxs-lookup"><span data-stu-id="4cb59-203">The `CreateEmptyDataView()` produces an empty data view object with the correct schema to be used as input to the `IEstimator.Fit()` method.</span></span>

### <a name="create-the-detectspike-method"></a><span data-ttu-id="4cb59-204">建立 DetectSpike() 方法</span><span class="sxs-lookup"><span data-stu-id="4cb59-204">Create the DetectSpike() method</span></span>

<span data-ttu-id="4cb59-205">`DetectSpike()` 方法：</span><span class="sxs-lookup"><span data-stu-id="4cb59-205">The `DetectSpike()` method:</span></span>

* <span data-ttu-id="4cb59-206">從估算工具建立轉換。</span><span class="sxs-lookup"><span data-stu-id="4cb59-206">Creates the transform from the estimator.</span></span>
* <span data-ttu-id="4cb59-207">根據歷史銷售資料偵測尖峰。</span><span class="sxs-lookup"><span data-stu-id="4cb59-207">Detects spikes based on historical sales data.</span></span>
* <span data-ttu-id="4cb59-208">顯示結果。</span><span class="sxs-lookup"><span data-stu-id="4cb59-208">Displays the results.</span></span>

1. <span data-ttu-id="4cb59-209">請使用下列程式碼，在緊接著 `Main()` 方法之後，建立 `DetectSpike()` 方法：</span><span class="sxs-lookup"><span data-stu-id="4cb59-209">Create the `DetectSpike()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. <span data-ttu-id="4cb59-210">使用 [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) 定型偵測尖峰的模型。</span><span class="sxs-lookup"><span data-stu-id="4cb59-210">Use the [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) to train the model for spike detection.</span></span> <span data-ttu-id="4cb59-211">使用下列程式碼將它新增至 `DetectSpike()` 方法：</span><span class="sxs-lookup"><span data-stu-id="4cb59-211">Add it to the `DetectSpike()` method with the following code:</span></span>

    [!code-csharp[AddSpikeTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddSpikeTrainer)]

1. <span data-ttu-id="4cb59-212">將下列內容新增為 `DetectSpike()` 方法的下一行程式碼來建立尖峰偵測轉換：</span><span class="sxs-lookup"><span data-stu-id="4cb59-212">Create the spike detection transform by adding the following as the next line of code in the `DetectSpike()` method:</span></span>

    [!code-csharp[TrainModel1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel1)]

1. <span data-ttu-id="4cb59-213">新增下列程式碼將 `productSales` 資料轉換成 `DetectSpike()` 方法中的下一行程式碼：</span><span class="sxs-lookup"><span data-stu-id="4cb59-213">Add the following line of code to transform the `productSales` data as the next line in the `DetectSpike()` method:</span></span>

    [!code-csharp[TransformData1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData1)]

    <span data-ttu-id="4cb59-214">上述程式碼使用 [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) 方法對多個資料集輸入資料列進行預測。</span><span class="sxs-lookup"><span data-stu-id="4cb59-214">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple input rows of a dataset.</span></span>

1. <span data-ttu-id="4cb59-215">將您的 `transformedData` 轉換成強型別 `IEnumerable`，以更容易使用 [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) 方法和下列程式碼顯示：</span><span class="sxs-lookup"><span data-stu-id="4cb59-215">Convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) method with the following code:</span></span>

    [!code-csharp[CreateEnumerable1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable1)]

1. <span data-ttu-id="4cb59-216">使用下列 <xref:System.Console.WriteLine?displayProperty=nameWithType> 程式碼建立顯示標頭行：</span><span class="sxs-lookup"><span data-stu-id="4cb59-216">Create a display header line using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

    [!code-csharp[DisplayHeader1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader1)]

    <span data-ttu-id="4cb59-217">您會在尖峰偵測結果中顯示下列資訊：</span><span class="sxs-lookup"><span data-stu-id="4cb59-217">You'll display the following information in your spike detection results:</span></span>

    * <span data-ttu-id="4cb59-218">`Alert` 表示指定資料點的尖峰警示。</span><span class="sxs-lookup"><span data-stu-id="4cb59-218">`Alert` indicates a spike alert for a given data point.</span></span>
    * <span data-ttu-id="4cb59-219">`Score` 是資料集中指定資料點的 `ProductSales` 值。</span><span class="sxs-lookup"><span data-stu-id="4cb59-219">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>
    * <span data-ttu-id="4cb59-220">`P-Value` "P" 表示機率。</span><span class="sxs-lookup"><span data-stu-id="4cb59-220">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="4cb59-221">P 值越接近 0，資料點就越可能有異常。</span><span class="sxs-lookup"><span data-stu-id="4cb59-221">The closer the p-value is to 0, the more likely the data point is an anomaly.</span></span>

1. <span data-ttu-id="4cb59-222">使用下列程式碼逐一查看 `predictions` `IEnumerable`，並顯示結果：</span><span class="sxs-lookup"><span data-stu-id="4cb59-222">Use the following code to iterate through the `predictions` `IEnumerable` and display the results:</span></span>

    [!code-csharp[DisplayResults1](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults1)]

1. <span data-ttu-id="4cb59-223">在 `Main()` 方法中新增 `DetectSpike()` 方法的呼叫：</span><span class="sxs-lookup"><span data-stu-id="4cb59-223">Add the call to the `DetectSpike()`method in the `Main()` method:</span></span>

    [!code-csharp[CallDetectSpike](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectSpike)]

## <a name="spike-detection-results"></a><span data-ttu-id="4cb59-224">尖峰偵測結果</span><span class="sxs-lookup"><span data-stu-id="4cb59-224">Spike detection results</span></span>

<span data-ttu-id="4cb59-225">您的結果應該與以下類似。</span><span class="sxs-lookup"><span data-stu-id="4cb59-225">Your results should be similar to the following.</span></span> <span data-ttu-id="4cb59-226">處理期間會顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="4cb59-226">During processing, messages are displayed.</span></span> <span data-ttu-id="4cb59-227">您可能會看到警告或處理訊息。</span><span class="sxs-lookup"><span data-stu-id="4cb59-227">You may see warnings, or processing messages.</span></span> <span data-ttu-id="4cb59-228">為了讓結果變得清楚，部分訊息已從下列結果中移除。</span><span class="sxs-lookup"><span data-stu-id="4cb59-228">Some of the messages have been removed from the following results for clarity.</span></span>

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

## <a name="change-point-detection"></a><span data-ttu-id="4cb59-229">變更點偵測</span><span class="sxs-lookup"><span data-stu-id="4cb59-229">Change point detection</span></span>

<span data-ttu-id="4cb59-230">`Change points` 是值之時間序列事件資料流分佈的持續變更，例如層級變更和趨勢。</span><span class="sxs-lookup"><span data-stu-id="4cb59-230">`Change points` are persistent changes in a time series event stream distribution of values, like level changes and trends.</span></span> <span data-ttu-id="4cb59-231">這些持續變更延續的時間比 `spikes` 長，可能表示災難性事件。</span><span class="sxs-lookup"><span data-stu-id="4cb59-231">These persistent changes last much longer than `spikes` and could indicate catastrophic event(s).</span></span> <span data-ttu-id="4cb59-232">`Change points` 通常無法為肉眼所見，但可以使用下列方法，在您的資料中偵測到。</span><span class="sxs-lookup"><span data-stu-id="4cb59-232">`Change points` are not usually visible to the naked eye, but can be detected in your data using approaches such as in the following method.</span></span>  <span data-ttu-id="4cb59-233">下圖是變更點偵測的範例：</span><span class="sxs-lookup"><span data-stu-id="4cb59-233">The following image is an example of a change point detection:</span></span>

![ChangePointDetection](./media/sales-anomaly-detection/ChangePointDetection.png)

### <a name="create-the-detectchangepoint-method"></a><span data-ttu-id="4cb59-235">建立 DetectChangepoint() 方法</span><span class="sxs-lookup"><span data-stu-id="4cb59-235">Create the DetectChangepoint() method</span></span>

<span data-ttu-id="4cb59-236">`DetectChangepoint()` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="4cb59-236">The `DetectChangepoint()` method executes the following tasks:</span></span>

* <span data-ttu-id="4cb59-237">從估算工具建立轉換。</span><span class="sxs-lookup"><span data-stu-id="4cb59-237">Creates the transform from the estimator.</span></span>
* <span data-ttu-id="4cb59-238">根據歷史銷售資料偵測變更點。</span><span class="sxs-lookup"><span data-stu-id="4cb59-238">Detects change points based on historical sales data.</span></span>
* <span data-ttu-id="4cb59-239">顯示結果。</span><span class="sxs-lookup"><span data-stu-id="4cb59-239">Displays the results.</span></span>

1. <span data-ttu-id="4cb59-240">請使用下列程式碼，在緊接著 `Main()` 方法之後，建立 `DetectChangepoint()` 方法：</span><span class="sxs-lookup"><span data-stu-id="4cb59-240">Create the `DetectChangepoint()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. <span data-ttu-id="4cb59-241">使用下列程式碼在 `DetectChangepoint()` 方法中建立 [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator)：</span><span class="sxs-lookup"><span data-stu-id="4cb59-241">Create the [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) in the `DetectChangepoint()` method with the following code:</span></span>

    [!code-csharp[AddChangepointTrainer](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#AddChangepointTrainer)]

1. <span data-ttu-id="4cb59-242">如同您先前進行的操作，請在 `DetectChangePoint()` 方法中新增下列程式碼行，以從估算工具建立轉換：</span><span class="sxs-lookup"><span data-stu-id="4cb59-242">As you did previously, create the transform from the estimator by adding the following line of code in the `DetectChangePoint()` method:</span></span>

    [!code-csharp[TrainModel2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TrainModel2)]

1. <span data-ttu-id="4cb59-243">將下列程式碼新增至 `DetectChangePoint()`，以使用 `Transform()` 方法來轉換資料：</span><span class="sxs-lookup"><span data-stu-id="4cb59-243">Use the `Transform()` method to transform the data by adding the following code to `DetectChangePoint()`:</span></span>

    [!code-csharp[TransformData2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#TransformData2)]

1. <span data-ttu-id="4cb59-244">如您之前的操作，將您的 `transformedData` 轉換成強型別 `IEnumerable`，以更容易使用 `CreateEnumerable()` 方法和下列程式碼顯示：</span><span class="sxs-lookup"><span data-stu-id="4cb59-244">As you did previously, convert your `transformedData` into a strongly-typed `IEnumerable` for easier display using the `CreateEnumerable()`method with the following code:</span></span>

    [!code-csharp[CreateEnumerable2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CreateEnumerable2)]

1. <span data-ttu-id="4cb59-245">下列列程式碼作為 `DetectChangePoint()` 方法中的下一行，建立顯示標頭：</span><span class="sxs-lookup"><span data-stu-id="4cb59-245">Create a display header with the following code as the next line in the `DetectChangePoint()` method:</span></span>

    [!code-csharp[DisplayHeader2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayHeader2)]

    <span data-ttu-id="4cb59-246">您會在變更點偵測結果中顯示下列資訊：</span><span class="sxs-lookup"><span data-stu-id="4cb59-246">You'll display the following information in your change point detection results:</span></span>

    * <span data-ttu-id="4cb59-247">`Alert` 表示指定資料點的變更點警示。</span><span class="sxs-lookup"><span data-stu-id="4cb59-247">`Alert` indicates a change point alert for a given data point.</span></span>
    * <span data-ttu-id="4cb59-248">`Score` 是資料集中指定資料點的 `ProductSales` 值。</span><span class="sxs-lookup"><span data-stu-id="4cb59-248">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>
    * <span data-ttu-id="4cb59-249">`P-Value` "P" 表示機率。</span><span class="sxs-lookup"><span data-stu-id="4cb59-249">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="4cb59-250">P 值越接近 0，資料點就越可能有異常。</span><span class="sxs-lookup"><span data-stu-id="4cb59-250">The closer the P-value is to 0, the more likely the data point is an anomaly.</span></span>
    * <span data-ttu-id="4cb59-251">`Martingale value` 根據一系列的 P 值，用來識別資料點的「怪異」程度。</span><span class="sxs-lookup"><span data-stu-id="4cb59-251">`Martingale value` is used to identify how "weird" a data point is, based on the sequence of P-values.</span></span>

1. <span data-ttu-id="4cb59-252">使用下列程式碼逐一查看 `predictions` `IEnumerable`，並顯示結果：</span><span class="sxs-lookup"><span data-stu-id="4cb59-252">Iterate through the `predictions` `IEnumerable` and display the results with the following code:</span></span>

    [!code-csharp[DisplayResults2](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#DisplayResults2)]

1. <span data-ttu-id="4cb59-253">在 `Main()` 方法中新增 `DetectChangepoint()` 方法的下列呼叫：</span><span class="sxs-lookup"><span data-stu-id="4cb59-253">Add the following call to the `DetectChangepoint()`method in the `Main()` method:</span></span>

    [!code-csharp[CallDetectChangepoint](~/samples/machine-learning/tutorials/ProductSalesAnomalyDetection/Program.cs#CallDetectChangepoint)]

## <a name="change-point-detection-results"></a><span data-ttu-id="4cb59-254">變更點偵測結果</span><span class="sxs-lookup"><span data-stu-id="4cb59-254">Change point detection results</span></span>

<span data-ttu-id="4cb59-255">您的結果應該與以下類似。</span><span class="sxs-lookup"><span data-stu-id="4cb59-255">Your results should be similar to the following.</span></span> <span data-ttu-id="4cb59-256">處理期間會顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="4cb59-256">During processing, messages are displayed.</span></span> <span data-ttu-id="4cb59-257">您可能會看到警告或處理訊息。</span><span class="sxs-lookup"><span data-stu-id="4cb59-257">You may see warnings, or processing messages.</span></span> <span data-ttu-id="4cb59-258">為了讓結果變得清楚，部分訊息已從下列結果中移除。</span><span class="sxs-lookup"><span data-stu-id="4cb59-258">Some messages have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="4cb59-259">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="4cb59-259">Congratulations!</span></span> <span data-ttu-id="4cb59-260">您現已成功建置偵測銷售資料中尖峰和變更點異常的機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="4cb59-260">You've now successfully built machine learning models for detecting spikes and change point anomalies in sales data.</span></span>

<span data-ttu-id="4cb59-261">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="4cb59-261">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

<span data-ttu-id="4cb59-262">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="4cb59-262">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="4cb59-263">載入資料</span><span class="sxs-lookup"><span data-stu-id="4cb59-263">Load the data</span></span>
> * <span data-ttu-id="4cb59-264">定型尖峰異常偵測的模型</span><span class="sxs-lookup"><span data-stu-id="4cb59-264">Train the model for spike anomaly detection</span></span>
> * <span data-ttu-id="4cb59-265">使用定型的模型偵測尖峰異常</span><span class="sxs-lookup"><span data-stu-id="4cb59-265">Detect spike anomalies with the trained model</span></span>
> * <span data-ttu-id="4cb59-266">定型變更點異常偵測的模型</span><span class="sxs-lookup"><span data-stu-id="4cb59-266">Train the model for change point anomaly detection</span></span>
> * <span data-ttu-id="4cb59-267">使用定型的模式偵測變更點異常</span><span class="sxs-lookup"><span data-stu-id="4cb59-267">Detect change point anomalies with the trained mode</span></span>

## <a name="next-steps"></a><span data-ttu-id="4cb59-268">後續步驟</span><span class="sxs-lookup"><span data-stu-id="4cb59-268">Next steps</span></span>

<span data-ttu-id="4cb59-269">請查看機器學習範例 GitHub 存放庫，以探索耗電量異常偵測範例。</span><span class="sxs-lookup"><span data-stu-id="4cb59-269">Check out the Machine Learning samples GitHub repository to explore a Power Consumption Anomaly Detection sample.</span></span>
> [!div class="nextstepaction"]
> <span data-ttu-id="4cb59-270">[dotnet/machinelearning-samples GitHub 存放庫](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="4cb59-270">[dotnet/machinelearning-samples GitHub repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)</span></span>
