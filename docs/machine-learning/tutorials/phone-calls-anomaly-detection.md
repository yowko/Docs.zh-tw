---
title: 教學課程：偵測來電中的異常狀況
description: 瞭解如何建立時間序列資料的異常偵測應用程式。 此教學課程會示範如何在 Visual Studio 2019 中使用 C# 建立 .NET Core 主控台應用程式。
ms.date: 12/04/2020
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: f001cb912bb695a7edb0917f3306ca9bfbe311ac
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98187778"
---
# <a name="tutorial-detect-anomalies-in-time-series-with-mlnet"></a><span data-ttu-id="9c905-104">教學課程：使用 ML.NET 偵測時間序列中的異常</span><span class="sxs-lookup"><span data-stu-id="9c905-104">Tutorial: Detect anomalies in time series with ML.NET</span></span>

<span data-ttu-id="9c905-105">瞭解如何建立時間序列資料的異常偵測應用程式。</span><span class="sxs-lookup"><span data-stu-id="9c905-105">Learn how to build an anomaly detection application for time series data.</span></span> <span data-ttu-id="9c905-106">此教學課程會示範如何在 Visual Studio 2019 中使用 C# 建立 .NET Core 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="9c905-106">This tutorial creates a .NET Core console application using C# in Visual Studio 2019.</span></span>

<span data-ttu-id="9c905-107">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="9c905-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="9c905-108">載入資料</span><span class="sxs-lookup"><span data-stu-id="9c905-108">Load the data</span></span>
> * <span data-ttu-id="9c905-109">偵測時間序列的期間</span><span class="sxs-lookup"><span data-stu-id="9c905-109">Detect period for a time series</span></span>
> * <span data-ttu-id="9c905-110">偵測定期時間序列的異常狀況</span><span class="sxs-lookup"><span data-stu-id="9c905-110">Detect anomaly for a periodical time series</span></span>

<span data-ttu-id="9c905-111">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/PhoneCallsAnomalyDetection) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="9c905-111">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/PhoneCallsAnomalyDetection) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9c905-112">先決條件</span><span class="sxs-lookup"><span data-stu-id="9c905-112">Prerequisites</span></span>

* <span data-ttu-id="9c905-113">已安裝「.NET Core 跨平臺開發」工作負載[Visual Studio 2019 16.7.8 版或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="9c905-113">[Visual Studio 2019 version 16.7.8 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="9c905-114">[phone-calls.csv 資料集](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_PhoneCalls/SrEntireDetection/Data/phone-calls.csv)。</span><span class="sxs-lookup"><span data-stu-id="9c905-114">[The phone-calls.csv dataset](https://github.com/dotnet/machinelearning-samples/blob/master/samples/csharp/getting-started/AnomalyDetection_PhoneCalls/SrEntireDetection/Data/phone-calls.csv).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="9c905-115">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="9c905-115">Create a console application</span></span>

1. <span data-ttu-id="9c905-116">建立名為 "ProductSalesAnomalyDetection" 的 **c # .Net Core 主控台應用程式** 。</span><span class="sxs-lookup"><span data-stu-id="9c905-116">Create a **C# .NET Core Console Application** called "ProductSalesAnomalyDetection".</span></span>

2. <span data-ttu-id="9c905-117">在您的專案中建立名為 *data* 的目錄，以儲存資料集檔案。</span><span class="sxs-lookup"><span data-stu-id="9c905-117">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="9c905-118">安裝「Microsoft.ML NuGet 套件」：</span><span class="sxs-lookup"><span data-stu-id="9c905-118">Install the **Microsoft.ML NuGet Package**:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    <span data-ttu-id="9c905-119">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="9c905-119">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="9c905-120">選擇 "nuget.org" 作為 [套件來源]，選取 [流覽] 索引標籤，搜尋 **Microsoft.ML** ，然後選取 [ **安裝** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="9c905-120">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="9c905-121">在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。</span><span class="sxs-lookup"><span data-stu-id="9c905-121">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="9c905-122">針對 **時間序列** 重複上述步驟。</span><span class="sxs-lookup"><span data-stu-id="9c905-122">Repeat these steps for **Microsoft.ML.TimeSeries**.</span></span>

4. <span data-ttu-id="9c905-123">在您的 *Program.cs* 檔案最上方新增下列 `using` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="9c905-123">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="9c905-124">下載您的資料</span><span class="sxs-lookup"><span data-stu-id="9c905-124">Download your data</span></span>

1. <span data-ttu-id="9c905-125">下載資料集，並儲存至您先前建立的 *Data* 資料夾：</span><span class="sxs-lookup"><span data-stu-id="9c905-125">Download the dataset and save it to the *Data* folder you previously created:</span></span>

    <span data-ttu-id="9c905-126">以滑鼠右鍵按一下 [*phone-calls.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_PhoneCalls/SrEntireDetection/Data/phone-calls.csv) ，然後選取 [儲存連結 (或目標) 為 ...]</span><span class="sxs-lookup"><span data-stu-id="9c905-126">Right click on [*phone-calls.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_PhoneCalls/SrEntireDetection/Data/phone-calls.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="9c905-127">請務必將 \*.csv 檔案儲存至 *Data* 資料夾，或儲存在其他位置之後將 \*.csv 檔案移至 *Data* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="9c905-127">Make sure you either save the \*.csv file to the *Data* folder, or after you save it elsewhere, move the \*.csv file to the *Data* folder.</span></span>

2. <span data-ttu-id="9c905-128">在 [方案總管] 中，以滑鼠右鍵按一下 \*.csv 檔案，並選取 [內容]。</span><span class="sxs-lookup"><span data-stu-id="9c905-128">In Solution Explorer, right-click the \*.csv file and select **Properties**.</span></span> <span data-ttu-id="9c905-129">在 [ **Advanced**] 底下，將 [ **複製到輸出目錄** ] 的值變更為 [ **更新時複製**]。</span><span class="sxs-lookup"><span data-stu-id="9c905-129">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="9c905-130">下表是 \*.csv 檔案的資料預覽：</span><span class="sxs-lookup"><span data-stu-id="9c905-130">The following table is a data preview from your \*.csv file:</span></span>

| <span data-ttu-id="9c905-131">timestamp</span><span class="sxs-lookup"><span data-stu-id="9c905-131">timestamp</span></span>  | <span data-ttu-id="9c905-132">value</span><span class="sxs-lookup"><span data-stu-id="9c905-132">value</span></span> |
|--------|--------------|
| <span data-ttu-id="9c905-133">2018/9/3</span><span class="sxs-lookup"><span data-stu-id="9c905-133">2018/9/3</span></span>  | <span data-ttu-id="9c905-134">36.69670857</span><span class="sxs-lookup"><span data-stu-id="9c905-134">36.69670857</span></span>  |
| <span data-ttu-id="9c905-135">2018/9/4</span><span class="sxs-lookup"><span data-stu-id="9c905-135">2018/9/4</span></span>  | <span data-ttu-id="9c905-136">35.74160571</span><span class="sxs-lookup"><span data-stu-id="9c905-136">35.74160571</span></span>  |
| <span data-ttu-id="9c905-137">.....</span><span class="sxs-lookup"><span data-stu-id="9c905-137">.....</span></span>  | <span data-ttu-id="9c905-138">.....</span><span class="sxs-lookup"><span data-stu-id="9c905-138">.....</span></span>  |
| <span data-ttu-id="9c905-139">2018/10/3</span><span class="sxs-lookup"><span data-stu-id="9c905-139">2018/10/3</span></span>  | <span data-ttu-id="9c905-140">34.49893429</span><span class="sxs-lookup"><span data-stu-id="9c905-140">34.49893429</span></span>  |
| <span data-ttu-id="9c905-141">...</span><span class="sxs-lookup"><span data-stu-id="9c905-141">...</span></span>    | <span data-ttu-id="9c905-142">....</span><span class="sxs-lookup"><span data-stu-id="9c905-142">....</span></span>   |

<span data-ttu-id="9c905-143">此檔案代表時間序列。</span><span class="sxs-lookup"><span data-stu-id="9c905-143">This file represents a time-series.</span></span> <span data-ttu-id="9c905-144">檔案中的每個資料列都是一個資料點。</span><span class="sxs-lookup"><span data-stu-id="9c905-144">Each row in the file is a data point.</span></span> <span data-ttu-id="9c905-145">每個資料點都有兩個屬性， `timestamp` 也就 `value` 是和，代表每天通話的次數。</span><span class="sxs-lookup"><span data-stu-id="9c905-145">Each data point has two attributes, namely, `timestamp` and `value`, to represent the number of phone calls at each day.</span></span> <span data-ttu-id="9c905-146">通話的數目會轉換成不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="9c905-146">The number of phone calls is transformed to de-sensitivity.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="9c905-147">建立類別及定義路徑</span><span class="sxs-lookup"><span data-stu-id="9c905-147">Create classes and define paths</span></span>

<span data-ttu-id="9c905-148">接下來，定義您的輸入和預測類別資料結構。</span><span class="sxs-lookup"><span data-stu-id="9c905-148">Next, define your input and prediction class data structures.</span></span>

<span data-ttu-id="9c905-149">將新類別新增至專案：</span><span class="sxs-lookup"><span data-stu-id="9c905-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="9c905-150">在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取 [新增] > [新項目]。</span><span class="sxs-lookup"><span data-stu-id="9c905-150">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="9c905-151">在 [ **加入新專案] 對話方塊** 中，選取 [ **類別** ]，然後將 [ **名稱** ] 欄位變更為 *PhoneCallsData.cs*。</span><span class="sxs-lookup"><span data-stu-id="9c905-151">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *PhoneCallsData.cs*.</span></span> <span data-ttu-id="9c905-152">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="9c905-152">Then, select the **Add** button.</span></span>

   <span data-ttu-id="9c905-153">*PhoneCallsData.cs* 檔案隨即在 [程式碼編輯器] 中開啟。</span><span class="sxs-lookup"><span data-stu-id="9c905-153">The *PhoneCallsData.cs* file opens in the code editor.</span></span>

3. <span data-ttu-id="9c905-154">將下列 `using` 語句新增至 *PhoneCallsData.cs* 的頂端：</span><span class="sxs-lookup"><span data-stu-id="9c905-154">Add the following `using` statement to the top of *PhoneCallsData.cs*:</span></span>

   ```csharp
   using Microsoft.ML.Data;
   ```

4. <span data-ttu-id="9c905-155">移除現有的類別定義，然後將下列程式碼加入至 PhoneCallsData.cs 檔案，其中包含兩個類別 `PhoneCallsData` 和 `PhoneCallsPrediction` ： </span><span class="sxs-lookup"><span data-stu-id="9c905-155">Remove the existing class definition and add the following code, which has two classes `PhoneCallsData` and `PhoneCallsPrediction`, to the *PhoneCallsData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](./snippets/phone-calls-anomaly-detection/csharp/PhoneCallsData.cs#DeclareTypes "Declare data record types")]

    <span data-ttu-id="9c905-156">`PhoneCallsData` 會指定輸入資料類別。</span><span class="sxs-lookup"><span data-stu-id="9c905-156">`PhoneCallsData` specifies an input data class.</span></span> <span data-ttu-id="9c905-157">[LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) 屬性會指定應該載入資料集內的哪些資料行 (依資料行索引)。</span><span class="sxs-lookup"><span data-stu-id="9c905-157">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> <span data-ttu-id="9c905-158">它有兩個屬性 `timestamp` ，而且 `value` 對應到資料檔案中的相同屬性。</span><span class="sxs-lookup"><span data-stu-id="9c905-158">It has two attributes `timestamp` and `value` that correspond to the same attributes in the data file.</span></span>

    <span data-ttu-id="9c905-159">`PhoneCallsPrediction` 指定預測資料類別。</span><span class="sxs-lookup"><span data-stu-id="9c905-159">`PhoneCallsPrediction` specifies the prediction data class.</span></span> <span data-ttu-id="9c905-160">針對 SR-IOV CNN 偵測器，預測取決於指定的偵測 [模式](xref:Microsoft.ML.TimeSeries.SrCnnDetectMode) 。</span><span class="sxs-lookup"><span data-stu-id="9c905-160">For SR-CNN detector, the prediction depends on the [detect mode](xref:Microsoft.ML.TimeSeries.SrCnnDetectMode) specified.</span></span> <span data-ttu-id="9c905-161">在此範例中，我們會選取 `AnomalyAndMargin` 模式。</span><span class="sxs-lookup"><span data-stu-id="9c905-161">In this sample, we select the `AnomalyAndMargin` mode.</span></span> <span data-ttu-id="9c905-162">輸出包含七個數據行。</span><span class="sxs-lookup"><span data-stu-id="9c905-162">The output contains seven columns.</span></span> <span data-ttu-id="9c905-163">在大部分的情況下，、、 `IsAnomaly` `ExpectedValue` `UpperBoundary` 和 `LowerBoundary` 都有足夠的資訊。</span><span class="sxs-lookup"><span data-stu-id="9c905-163">In most cases, `IsAnomaly`, `ExpectedValue`, `UpperBoundary`, and `LowerBoundary` are informative enough.</span></span> <span data-ttu-id="9c905-164">它們會告訴您某個點是否為異常，這是點的預期值和點的下限/上限區域。</span><span class="sxs-lookup"><span data-stu-id="9c905-164">They tell you if a point is an anomaly, the expected value of the point and the lower / upper boundary region of the point.</span></span>

5. <span data-ttu-id="9c905-165">將下列程式碼新增至方法上方的行， `Main` 以指定資料檔案的路徑：</span><span class="sxs-lookup"><span data-stu-id="9c905-165">Add the following code to the line right above the `Main` method to specify the path to your data file:</span></span>

    [!code-csharp[Declare global variables](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

### <a name="initialize-variables-in-main"></a><span data-ttu-id="9c905-166">在 Main 中初始化變數</span><span class="sxs-lookup"><span data-stu-id="9c905-166">Initialize variables in Main</span></span>

1. <span data-ttu-id="9c905-167">將 `Main` 方法中的 `Console.WriteLine("Hello World!")` 程式碼替換成下列程式碼，宣告並初始化 `mlContext` 變數：</span><span class="sxs-lookup"><span data-stu-id="9c905-167">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

    [!code-csharp[CreateMLContext](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CreateMLContext "Create the ML Context")]

    <span data-ttu-id="9c905-168">[MLContext 類別](xref:Microsoft.ML.MLContext)是所有 ML.NET 作業的起點，且初始化 `mlContext` 會建立新的 ML.NET 環境，其可在模型建立工作流程物件之間共用。</span><span class="sxs-lookup"><span data-stu-id="9c905-168">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="9c905-169">就概念而言，類似於 Entity Framework 中的 `DBContext`。</span><span class="sxs-lookup"><span data-stu-id="9c905-169">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="load-the-data"></a><span data-ttu-id="9c905-170">載入資料</span><span class="sxs-lookup"><span data-stu-id="9c905-170">Load the data</span></span>

<span data-ttu-id="9c905-171">ML.NET 中的資料以 [IDataView 類別](xref:Microsoft.ML.IDataView) 表示。</span><span class="sxs-lookup"><span data-stu-id="9c905-171">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="9c905-172">`IDataView` 是彈性且有效率的表格式資料描述方式 (數值和文字)。</span><span class="sxs-lookup"><span data-stu-id="9c905-172">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="9c905-173">資料可以從文字檔或其他來源 (例如 SQL 資料庫或記錄檔) 載入至 `IDataView` 物件。</span><span class="sxs-lookup"><span data-stu-id="9c905-173">Data can be loaded from a text file or from other sources (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="9c905-174">將下列程式碼新增為 `Main` 方法的下一行：</span><span class="sxs-lookup"><span data-stu-id="9c905-174">Add the following code as the next line of the `Main` method:</span></span>

    [!code-csharp[LoadData](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="9c905-175">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) 會定義資料結構描述並讀入檔案中。</span><span class="sxs-lookup"><span data-stu-id="9c905-175">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="9c905-176">會接受資料路徑變數然後傳回 `IDataView`。</span><span class="sxs-lookup"><span data-stu-id="9c905-176">It takes in the data path variables and returns an `IDataView`.</span></span>

## <a name="time-series-anomaly-detection"></a><span data-ttu-id="9c905-177">時間序列異常偵測</span><span class="sxs-lookup"><span data-stu-id="9c905-177">Time series anomaly detection</span></span>

<span data-ttu-id="9c905-178">時間序列異常偵測是偵測時間序列資料極端值的過程;指向指定的輸入時間序列，其中行為不是預期的行為，或「奇怪」。</span><span class="sxs-lookup"><span data-stu-id="9c905-178">Time series anomaly detection is the process of detecting time-series data outliers; points on a given input time-series where the behavior isn't what was expected, or "weird".</span></span> <span data-ttu-id="9c905-179">這些異常通常代表問題領域的一些感興趣事件：使用者帳戶的網路攻擊、電源中斷、伺服器上的高載 RPS、記憶體流失等。</span><span class="sxs-lookup"><span data-stu-id="9c905-179">These anomalies are typically indicative of some events of interest in the problem domain: a cyber-attack on user accounts, power outage, bursting RPS on a server, memory leak, etc.</span></span>

<span data-ttu-id="9c905-180">若要在時間序列上尋找異常狀況，您應該先決定數列的期間。</span><span class="sxs-lookup"><span data-stu-id="9c905-180">To find anomaly on time series, you should first determine the period of the series.</span></span> <span data-ttu-id="9c905-181">然後，時間序列可以分解成數個元件，例如 `Y = T + S + R` ， `Y` 原始數列 `T` 是趨勢元件、 `S` 是季節性元件，而 `R` 是數列的剩餘元件。</span><span class="sxs-lookup"><span data-stu-id="9c905-181">Then, the time series can be decomposed into several components as `Y = T + S + R`, where `Y` is the original series, `T` is the trend component, `S` is the seasonal component, and `R` is the residual component of the series.</span></span> <span data-ttu-id="9c905-182">此步驟稱為 [分解](https://en.wikipedia.org/wiki/Decomposition_of_time_series)。</span><span class="sxs-lookup"><span data-stu-id="9c905-182">This step is called [decomposition](https://en.wikipedia.org/wiki/Decomposition_of_time_series).</span></span> <span data-ttu-id="9c905-183">最後，會在剩餘的元件上執行偵測，以找出異常狀況。</span><span class="sxs-lookup"><span data-stu-id="9c905-183">Finally, detection is performed on the residual component to find the anomalies.</span></span> <span data-ttu-id="9c905-184">在 ML.NET 中，CNN 演算法是先進的新穎演算法，以光譜殘留 (SR) 和卷積類神經網路 (CNN) 偵測時間序列上的異常狀況。</span><span class="sxs-lookup"><span data-stu-id="9c905-184">In ML.NET, The SR-CNN algorithm is an advanced and novel algorithm that is based on Spectral Residual (SR) and Convolutional Neural Network(CNN) to detect anomaly on time-series.</span></span> <span data-ttu-id="9c905-185">如需此演算法的詳細資訊，請參閱 [Microsoft 的時間序列異常偵測服務](https://arxiv.org/pdf/1906.03821.pdf)。</span><span class="sxs-lookup"><span data-stu-id="9c905-185">For more information on this algorithm, see [Time-Series Anomaly Detection Service at Microsoft](https://arxiv.org/pdf/1906.03821.pdf).</span></span>

<span data-ttu-id="9c905-186">在本教學課程中，您會看到可以使用兩個函數來完成這些程式。</span><span class="sxs-lookup"><span data-stu-id="9c905-186">In this tutorial, you will see that these procedures can be completed using two functions.</span></span>

## <a name="detect-period"></a><span data-ttu-id="9c905-187">偵測期間</span><span class="sxs-lookup"><span data-stu-id="9c905-187">Detect Period</span></span>

<span data-ttu-id="9c905-188">在第一個步驟中，我們叫用 `DetectSeasonality` 函數來判斷數列的期間。</span><span class="sxs-lookup"><span data-stu-id="9c905-188">In the first step, we invoke the `DetectSeasonality` function to determine the period of the series.</span></span>

### <a name="create-the-detectperiod-method"></a><span data-ttu-id="9c905-189">建立 DetectPeriod 方法</span><span class="sxs-lookup"><span data-stu-id="9c905-189">Create the DetectPeriod method</span></span>

1. <span data-ttu-id="9c905-190">`DetectPeriod`使用下列程式碼，在方法正下方建立方法 `Main` ：</span><span class="sxs-lookup"><span data-stu-id="9c905-190">Create the `DetectPeriod` method, just below the `Main` method, using the following code:</span></span>

    ```csharp
    static void DetectPeriod(MLContext mlContext, IDataView phoneCalls)
    {

    }
    ```

2. <span data-ttu-id="9c905-191">使用 <xref:Microsoft.ML.TimeSeriesCatalog.DetectSeasonality%2A> 函數來偵測期間。</span><span class="sxs-lookup"><span data-stu-id="9c905-191">Use the <xref:Microsoft.ML.TimeSeriesCatalog.DetectSeasonality%2A> function to detect period.</span></span> <span data-ttu-id="9c905-192">使用下列程式碼將它新增至 `DetectPeriod` 方法：</span><span class="sxs-lookup"><span data-stu-id="9c905-192">Add it to the `DetectPeriod` method with the following code:</span></span>

    [!code-csharp[DetectSeasonality](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DetectSeasonality)]

3. <span data-ttu-id="9c905-193">將下列內容新增為方法中的下一行程式碼，以顯示期間值 `DetectPeriod` ：</span><span class="sxs-lookup"><span data-stu-id="9c905-193">Display the period value by adding the following as the next line of code in the `DetectPeriod` method:</span></span>

    [!code-csharp[DisplayPeriod](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DisplayPeriod)]

4. <span data-ttu-id="9c905-194">將下列呼叫新增至 `DetectPeriod` 方法中的方法 `Main` ：</span><span class="sxs-lookup"><span data-stu-id="9c905-194">Add the following call to the `DetectPeriod` method in the `Main` method:</span></span>

    [!code-csharp[CallDetectPeriod](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CallDetectPeriod)]

### <a name="period-detection-results"></a><span data-ttu-id="9c905-195">期間偵測結果</span><span class="sxs-lookup"><span data-stu-id="9c905-195">Period detection results</span></span>

<span data-ttu-id="9c905-196">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="9c905-196">Run the application.</span></span> <span data-ttu-id="9c905-197">您的結果應該與以下類似。</span><span class="sxs-lookup"><span data-stu-id="9c905-197">Your results should be similar to the following.</span></span>

```console
Period of the series is: 7.
```

## <a name="detect-anomaly"></a><span data-ttu-id="9c905-198">偵測異常</span><span class="sxs-lookup"><span data-stu-id="9c905-198">Detect Anomaly</span></span>

<span data-ttu-id="9c905-199">在此步驟中，您會使用 <xref:Microsoft.ML.TimeSeriesCatalog.DetectEntireAnomalyBySrCnn%2A> 方法來尋找異常。</span><span class="sxs-lookup"><span data-stu-id="9c905-199">In this step, you use the <xref:Microsoft.ML.TimeSeriesCatalog.DetectEntireAnomalyBySrCnn%2A> method to find anomalies.</span></span>

### <a name="create-the-detectanomaly-method"></a><span data-ttu-id="9c905-200">建立 DetectAnomaly 方法</span><span class="sxs-lookup"><span data-stu-id="9c905-200">Create the DetectAnomaly method</span></span>

1. <span data-ttu-id="9c905-201">`DetectAnomaly`使用下列程式碼，在方法正下方建立方法 `DetectPeriod` ：</span><span class="sxs-lookup"><span data-stu-id="9c905-201">Create the `DetectAnomaly` method, just below the `DetectPeriod` method, using the following code:</span></span>

    ```csharp
    static void DetectAnomaly(MLContext mlContext, IDataView phoneCalls, int period)
    {

    }
    ```

2. <span data-ttu-id="9c905-202"><xref:Microsoft.ML.TimeSeries.SrCnnEntireAnomalyDetectorOptions> `DetectAnomaly` 使用下列程式碼在方法中設定：</span><span class="sxs-lookup"><span data-stu-id="9c905-202">Set up <xref:Microsoft.ML.TimeSeries.SrCnnEntireAnomalyDetectorOptions> in the `DetectAnomaly` method with the following code:</span></span>

    [!code-csharp[SetupSrCnnParameters](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#SetupSrCnnParameters)]

3. <span data-ttu-id="9c905-203">藉由在方法中新增下列程式碼，偵測 CNN 演算法的異常狀況 `DetectAnomaly` ：</span><span class="sxs-lookup"><span data-stu-id="9c905-203">Detect anomaly by SR-CNN algorithm by adding the following line of code in the `DetectAnomaly` method:</span></span>

    [!code-csharp[DetectAnomaly](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DetectAnomaly)]

4. <span data-ttu-id="9c905-204">使用方法搭配下列程式碼，將輸出資料檢視轉換成強型別 `IEnumerable` ，以便更輕鬆地顯示 [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) ：</span><span class="sxs-lookup"><span data-stu-id="9c905-204">Convert the output data view into a strongly typed `IEnumerable` for easier display using the [`CreateEnumerable`](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) method with the following code:</span></span>

    [!code-csharp[CreateEnumerableForResult](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CreateEnumerableForResult)]

5. <span data-ttu-id="9c905-205">下列列程式碼作為 `DetectAnomaly` 方法中的下一行，建立顯示標頭：</span><span class="sxs-lookup"><span data-stu-id="9c905-205">Create a display header with the following code as the next line in the `DetectAnomaly` method:</span></span>

    [!code-csharp[DisplayHeader](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DisplayHeader)]

    <span data-ttu-id="9c905-206">您會在變更點偵測結果中顯示下列資訊：</span><span class="sxs-lookup"><span data-stu-id="9c905-206">You'll display the following information in your change point detection results:</span></span>

    * <span data-ttu-id="9c905-207">`Index` 這是每個點的索引。</span><span class="sxs-lookup"><span data-stu-id="9c905-207">`Index` is the index of each point.</span></span>
    * <span data-ttu-id="9c905-208">`Anomaly` 這是是否偵測到每個點是否為異常的指標。</span><span class="sxs-lookup"><span data-stu-id="9c905-208">`Anomaly` is the indicator of whether each point is detected as anomaly.</span></span>
    * <span data-ttu-id="9c905-209">`ExpectedValue` 這是每個點的估計值。</span><span class="sxs-lookup"><span data-stu-id="9c905-209">`ExpectedValue` is the estimated value of each point.</span></span>
    * <span data-ttu-id="9c905-210">`LowerBoundary` 是每個點都不是異常的最小值。</span><span class="sxs-lookup"><span data-stu-id="9c905-210">`LowerBoundary` is the lowest value each point can be to be not anomaly.</span></span>
    * <span data-ttu-id="9c905-211">`UpperBoundary` 這是最大值，每個點都不是異常。</span><span class="sxs-lookup"><span data-stu-id="9c905-211">`UpperBoundary` is the highest value each point can be to be not anomaly.</span></span>

6. <span data-ttu-id="9c905-212">逐一查看 `predictions` `IEnumerable` ，並以下列程式碼顯示結果：</span><span class="sxs-lookup"><span data-stu-id="9c905-212">Iterate through the `predictions` `IEnumerable` and display the results with the following code:</span></span>

    [!code-csharp[DisplayAnomalyDetectionResults](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#DisplayAnomalyDetectionResults)]

7. <span data-ttu-id="9c905-213">將下列呼叫新增至 `DetectAnomaly` 方法中的方法 `Main` ：</span><span class="sxs-lookup"><span data-stu-id="9c905-213">Add the following call to the `DetectAnomaly` method in the `Main` method:</span></span>

    [!code-csharp[CallDetectAnomaly](./snippets/phone-calls-anomaly-detection/csharp/Program.cs#CallDetectAnomaly)]

## <a name="anomaly-detection-results"></a><span data-ttu-id="9c905-214">異常偵測結果</span><span class="sxs-lookup"><span data-stu-id="9c905-214">Anomaly detection results</span></span>

<span data-ttu-id="9c905-215">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="9c905-215">Run the application.</span></span> <span data-ttu-id="9c905-216">您的結果應該與以下類似。</span><span class="sxs-lookup"><span data-stu-id="9c905-216">Your results should be similar to the following.</span></span> <span data-ttu-id="9c905-217">處理期間會顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="9c905-217">During processing, messages are displayed.</span></span> <span data-ttu-id="9c905-218">您可能會看到警告或處理訊息。</span><span class="sxs-lookup"><span data-stu-id="9c905-218">You may see warnings or processing messages.</span></span> <span data-ttu-id="9c905-219">為了讓結果變得清楚，部分訊息已從下列結果中移除。</span><span class="sxs-lookup"><span data-stu-id="9c905-219">Some messages have been removed from the following results for clarity.</span></span>

```console
Detect period of the series
Period of the series is: 7.
Detect anomaly points in the series
Index   Data    Anomaly AnomalyScore    Mag     ExpectedValue   BoundaryUnit    UpperBoundary   LowerBoundary
0,0,36.841787256739266,41.14206982401966,32.541504689458876
1,0,35.67303618137362,39.97331874865401,31.372753614093227
2,0,34.710132999891826,39.029491313022824,30.390774686760828
3,0,33.44765248883495,37.786086547816545,29.10921842985335
4,0,28.937110922276364,33.25646923540736,24.61775260914537
5,0,5.143895892785781,9.444178460066171,0.843613325505391
6,0,5.163325228419392,9.463607795699783,0.8630426611390014
7,0,36.76414836240396,41.06443092968435,32.46386579512357
8,0,35.77908590657007,40.07936847385046,31.478803339289676
9,0,34.547259536635245,38.847542103915636,30.246976969354854
10,0,33.55193524820608,37.871293561337076,29.23257693507508
11,0,29.091800129624648,33.392082696905035,24.79151756234426
12,0,5.154836630338823,9.455119197619213,0.8545540630584334
13,0,5.234332502492464,9.534615069772855,0.934049935212073
14,0,36.54992549471526,40.85020806199565,32.24964292743487
15,0,35.79526470980883,40.095547277089224,31.494982142528443
16,0,34.34099013096804,38.64127269824843,30.040707563687647
17,0,33.61201516582131,37.9122977331017,29.31173259854092
18,0,29.223563320561812,33.5238458878422,24.923280753281425
19,0,5.170512168851533,9.470794736131923,0.8702296015711433
20,0,5.2614938889462834,9.561776456226674,0.9612113216658926
21,0,36.37103858487317,40.67132115215356,32.07075601759278
22,0,35.813544599026855,40.113827166307246,31.513262031746464
23,0,34.05600492733225,38.356287494612644,29.755722360051863
24,0,33.65828319077884,37.95856575805923,29.358000623498448
25,0,29.381125690882463,33.681408258162854,25.080843123602072
26,0,5.261543539820418,9.561826107100808,0.9612609725400283
27,0,5.4873712582971805,9.787653825577571,1.1870886910167897
28,1,36.504694001629254,40.804976568909645,32.20441143434886  <-- alert is on, detected anomaly
...
```

<span data-ttu-id="9c905-220">恭喜！</span><span class="sxs-lookup"><span data-stu-id="9c905-220">Congratulations!</span></span> <span data-ttu-id="9c905-221">您現在已成功建立機器學習模型，以偵測定期系列的期間和異常。</span><span class="sxs-lookup"><span data-stu-id="9c905-221">You've now successfully built machine learning models for detecting period and anomaly on a periodical series.</span></span>

<span data-ttu-id="9c905-222">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/PhoneCallsAnomalyDetection) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="9c905-222">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/PhoneCallsAnomalyDetection) repository.</span></span>

<span data-ttu-id="9c905-223">在本教學課程中，您已了解如何：</span><span class="sxs-lookup"><span data-stu-id="9c905-223">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="9c905-224">載入資料</span><span class="sxs-lookup"><span data-stu-id="9c905-224">Load the data</span></span>
> * <span data-ttu-id="9c905-225">偵測時間序列資料的期間</span><span class="sxs-lookup"><span data-stu-id="9c905-225">Detect period on the time series data</span></span>
> * <span data-ttu-id="9c905-226">偵測時間序列資料的異常狀況</span><span class="sxs-lookup"><span data-stu-id="9c905-226">Detect anomaly on the time series data</span></span>

## <a name="next-steps"></a><span data-ttu-id="9c905-227">後續步驟</span><span class="sxs-lookup"><span data-stu-id="9c905-227">Next steps</span></span>

<span data-ttu-id="9c905-228">請查看機器學習範例 GitHub 存放庫，以探索耗電量異常偵測範例。</span><span class="sxs-lookup"><span data-stu-id="9c905-228">Check out the Machine Learning samples GitHub repository to explore a Power Consumption Anomaly Detection sample.</span></span>
> [!div class="nextstepaction"]
> <span data-ttu-id="9c905-229">[dotnet/machinelearning-samples GitHub 存放庫](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="9c905-229">[dotnet/machinelearning-samples GitHub repository](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)</span></span>
