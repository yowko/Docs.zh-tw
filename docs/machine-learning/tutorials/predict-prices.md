---
title: 教學課程：使用迴歸預測價格
description: 本教學課程會示範如何使用 ML.NET 建置迴歸模型，特別針對紐約市的計程車費用預測價格。
ms.date: 05/09/2019
ms.topic: tutorial
ms.custom: mvc, seodec18, title-hack-0516
ms.openlocfilehash: fe3afab4cbd3f77ed4498cc5081180910d7d0b9e
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666616"
---
# <a name="tutorial-predict-prices-using-regression-with-mlnet"></a><span data-ttu-id="6ef13-103">教學課程：搭配 ML.NET 使用迴歸預測價格</span><span class="sxs-lookup"><span data-stu-id="6ef13-103">Tutorial: Predict prices using regression with ML.NET</span></span>

<span data-ttu-id="6ef13-104">本教學課程會示範如何使用 ML.NET 建置[迴歸模型](../resources/glossary.md#regression)，特別針對紐約市的計程車費用預測價格。</span><span class="sxs-lookup"><span data-stu-id="6ef13-104">This tutorial illustrates how to build a [regression model](../resources/glossary.md#regression) using ML.NET to predict prices, specifically, New York City taxi fares.</span></span>

<span data-ttu-id="6ef13-105">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="6ef13-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="6ef13-106">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="6ef13-106">Prepare and understand the data</span></span>
> * <span data-ttu-id="6ef13-107">載入並轉換資料</span><span class="sxs-lookup"><span data-stu-id="6ef13-107">Load and transform the data</span></span>
> * <span data-ttu-id="6ef13-108">選擇學習演算法</span><span class="sxs-lookup"><span data-stu-id="6ef13-108">Choose a learning algorithm</span></span>
> * <span data-ttu-id="6ef13-109">將模型定型</span><span class="sxs-lookup"><span data-stu-id="6ef13-109">Train the model</span></span>
> * <span data-ttu-id="6ef13-110">評估模型</span><span class="sxs-lookup"><span data-stu-id="6ef13-110">Evaluate the model</span></span>
> * <span data-ttu-id="6ef13-111">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="6ef13-111">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6ef13-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="6ef13-112">Prerequisites</span></span>

* <span data-ttu-id="6ef13-113">已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)。</span><span class="sxs-lookup"><span data-stu-id="6ef13-113">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="6ef13-114">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="6ef13-114">Create a console application</span></span>

1. <span data-ttu-id="6ef13-115">建立稱為 "TaxiFarePrediction" 的 **.NET Core 主控台應用程式**。</span><span class="sxs-lookup"><span data-stu-id="6ef13-115">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

1. <span data-ttu-id="6ef13-116">在您專案中建立名為 *Data* 的目錄以用來儲存資料集和模型檔案。</span><span class="sxs-lookup"><span data-stu-id="6ef13-116">Create a directory named *Data* in your project to store the data set and model files.</span></span>

1. <span data-ttu-id="6ef13-117">安裝 **Microsoft.ML** NuGet 套件：</span><span class="sxs-lookup"><span data-stu-id="6ef13-117">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="6ef13-118">在 [方案總管]  中，以滑鼠右鍵按一下專案，然後選取 [管理 NuGet 套件]  。</span><span class="sxs-lookup"><span data-stu-id="6ef13-118">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="6ef13-119">選擇 "nuget.org" 作為 [套件來源]、選取 [瀏覽]  索引標籤、搜尋 **Microsoft.ML**、從清單中選取該套件，然後選取 [安裝]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="6ef13-119">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="6ef13-120">在 [預覽變更]  對話方塊上，選取 [確定]  按鈕，然後在 [授權接受]  對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]  。</span><span class="sxs-lookup"><span data-stu-id="6ef13-120">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="6ef13-121">針對 **Microsoft.ML.FastTree** Nuget 套件執行相同的動作。</span><span class="sxs-lookup"><span data-stu-id="6ef13-121">Do the same for the **Microsoft.ML.FastTree** Nuget package.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="6ef13-122">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="6ef13-122">Prepare and understand the data</span></span>

1. <span data-ttu-id="6ef13-123">下載 [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) 和 [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) 資料集，並將它們儲存至您在上一個步驟所建立的 *Data* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="6ef13-123">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="6ef13-124">我們可以使用這些資料集將機器學習模型定型，然後評估模型的準確程度。</span><span class="sxs-lookup"><span data-stu-id="6ef13-124">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="6ef13-125">這些資料集原先來自 [NYC TLC Taxi Trip 資料集](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)。</span><span class="sxs-lookup"><span data-stu-id="6ef13-125">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

1. <span data-ttu-id="6ef13-126">在 [方案總管]  中，以滑鼠右鍵按一下每個 \*.csv 檔案，然後選取 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="6ef13-126">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="6ef13-127">在 [進階]  底下，將 [複製到輸出目錄]  的值變更為 [有更新時才複製]  。</span><span class="sxs-lookup"><span data-stu-id="6ef13-127">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

1. <span data-ttu-id="6ef13-128">開啟 **taxi-fare-train.csv** 資料集，然後查看第一個資料列中的資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="6ef13-128">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="6ef13-129">請查看每個資料行。</span><span class="sxs-lookup"><span data-stu-id="6ef13-129">Take a look at each of the columns.</span></span> <span data-ttu-id="6ef13-130">了解資料，並決定哪些資料行是 **features**，以及哪一個資料行是 **label**。</span><span class="sxs-lookup"><span data-stu-id="6ef13-130">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="6ef13-131">`label` 是您希望進行預測的資料行。</span><span class="sxs-lookup"><span data-stu-id="6ef13-131">The `label` is the column you want to predict.</span></span> <span data-ttu-id="6ef13-132">識別的 `Features` 是您提供模型來預測 `Label` 的輸入。</span><span class="sxs-lookup"><span data-stu-id="6ef13-132">The identified `Features`are the inputs you give the model to predict the `Label`.</span></span>

<span data-ttu-id="6ef13-133">提供的資料集包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="6ef13-133">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="6ef13-134">**vendor_id：** 計程車廠商的識別碼是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="6ef13-134">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="6ef13-135">**rate_code：** 計程車行程的費率類型是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="6ef13-135">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="6ef13-136">**passenger_count：** 行程的乘客數目是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="6ef13-136">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="6ef13-137">**trip_time_in_secs：** 行程所花費的時間長度。</span><span class="sxs-lookup"><span data-stu-id="6ef13-137">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="6ef13-138">您想要在行程結束之前預測行程的車資。</span><span class="sxs-lookup"><span data-stu-id="6ef13-138">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="6ef13-139">那時，您並不知道行程需要多長的時間。</span><span class="sxs-lookup"><span data-stu-id="6ef13-139">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="6ef13-140">因此，行程時間不是一項特徵，您將從模型中排除這個資料行。</span><span class="sxs-lookup"><span data-stu-id="6ef13-140">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="6ef13-141">**trip_distance：** 行程的距離是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="6ef13-141">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="6ef13-142">**payment_type：** 付款方式 (現金或信用卡) 是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="6ef13-142">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="6ef13-143">**fare_amount：** 計程車車資總計是標籤。</span><span class="sxs-lookup"><span data-stu-id="6ef13-143">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="6ef13-144">建立資料類別</span><span class="sxs-lookup"><span data-stu-id="6ef13-144">Create data classes</span></span>

<span data-ttu-id="6ef13-145">為輸入資料和預測建立類別：</span><span class="sxs-lookup"><span data-stu-id="6ef13-145">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="6ef13-146">在 [方案總管]  中，於專案上按一下滑鼠右鍵，然後選取 [新增]   > [新增項目]  。</span><span class="sxs-lookup"><span data-stu-id="6ef13-146">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="6ef13-147">在 [新增項目]  對話方塊中，選取 [類別]  ，然後將 [名稱]  欄位變更為 *TaxiTrip.cs*。</span><span class="sxs-lookup"><span data-stu-id="6ef13-147">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="6ef13-148">接著，選取 [新增]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="6ef13-148">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="6ef13-149">將下列的 `using` 指示詞加入新檔案：</span><span class="sxs-lookup"><span data-stu-id="6ef13-149">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="6ef13-150">移除現有的類別定義，然後將下列程式碼 (具有 `TaxiTrip` 和 `TaxiTripFarePrediction` 這兩個類別) 新增至 *TaxiTrip.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="6ef13-150">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](~/samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="6ef13-151">`TaxiTrip` 是輸入資料類別，並含有每個資料集資料行的定義。</span><span class="sxs-lookup"><span data-stu-id="6ef13-151">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="6ef13-152">使用 <xref:Microsoft.ML.Data.LoadColumnAttribute> 屬性來指定資料集中來源資料行的索引。</span><span class="sxs-lookup"><span data-stu-id="6ef13-152">Use the <xref:Microsoft.ML.Data.LoadColumnAttribute> attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="6ef13-153">`TaxiTripFarePrediction` 類別代表預測的結果。</span><span class="sxs-lookup"><span data-stu-id="6ef13-153">The `TaxiTripFarePrediction` class represents predicted results.</span></span> <span data-ttu-id="6ef13-154">包含一個套用 `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> 屬性的單一浮點數欄位 `FareAmount`。</span><span class="sxs-lookup"><span data-stu-id="6ef13-154">It has a single float field, `FareAmount`, with a `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> attribute applied.</span></span> <span data-ttu-id="6ef13-155">如果是迴歸工作，則**分數**資料行包含預測的標籤值。</span><span class="sxs-lookup"><span data-stu-id="6ef13-155">In case of the regression task the **Score** column contains predicted label values.</span></span>

> [!NOTE]
> <span data-ttu-id="6ef13-156">使用 `float` 型別表示輸入和預測資料類別中的浮點值。</span><span class="sxs-lookup"><span data-stu-id="6ef13-156">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

### <a name="define-data-and-model-paths"></a><span data-ttu-id="6ef13-157">定義資料和模型路徑</span><span class="sxs-lookup"><span data-stu-id="6ef13-157">Define data and model paths</span></span>

<span data-ttu-id="6ef13-158">在 *Program.cs* 檔案頂端新增下列額外的 `using` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="6ef13-158">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="6ef13-159">您必須建立三個欄位，保存含有資料集的檔案與用來儲存模型之檔案的檔案路徑：</span><span class="sxs-lookup"><span data-stu-id="6ef13-159">You need to create three fields to hold the paths to the files with data sets and the file to save the model:</span></span>

* <span data-ttu-id="6ef13-160">`_trainDataPath` 會針對具有用來定型模型之資料集的檔案，包含檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="6ef13-160">`_trainDataPath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="6ef13-161">`_testDataPath` 會針對具有用來評估模型之資料集的檔案，包含檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="6ef13-161">`_testDataPath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="6ef13-162">`_modelPath` 會針對儲存定型模型的檔案，包含檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="6ef13-162">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="6ef13-163">將下列程式碼加入至緊接在 `Main` 方法上方，以指定這些路徑和 `_textLoader` 變數：</span><span class="sxs-lookup"><span data-stu-id="6ef13-163">Add the following code right above the `Main` method to specify those paths and for the `_textLoader` variable:</span></span>

[!code-csharp[InitializePaths](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="6ef13-164">所有 ML.NET 作業都是從 [MLContext 類別](xref:Microsoft.ML.MLContext)開始。</span><span class="sxs-lookup"><span data-stu-id="6ef13-164">All ML.NET operations start in the [MLContext class](xref:Microsoft.ML.MLContext).</span></span> <span data-ttu-id="6ef13-165">初始化 `mlContext` 會建立新的 ML.NET 環境，可在模型建立工作流程物件間共用。</span><span class="sxs-lookup"><span data-stu-id="6ef13-165">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="6ef13-166">就概念而言，類似於 Entity Framework 中的 `DBContext`。</span><span class="sxs-lookup"><span data-stu-id="6ef13-166">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="6ef13-167">在 Main 中初始化變數</span><span class="sxs-lookup"><span data-stu-id="6ef13-167">Initialize variables in Main</span></span>

<span data-ttu-id="6ef13-168">將 `Main` 方法中的 `Console.WriteLine("Hello World!")` 程式碼替換成下列程式碼，宣告並初始化 `mlContext` 變數：</span><span class="sxs-lookup"><span data-stu-id="6ef13-168">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="6ef13-169">將下列內容加入為 `Main` 方法中的下一行程式碼，來呼叫 `Train` 方法：</span><span class="sxs-lookup"><span data-stu-id="6ef13-169">Add the following as the next line of code in the `Main` method to call the `Train` method:</span></span>

[!code-csharp[Train](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Train your model")]

<span data-ttu-id="6ef13-170">`Train()` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="6ef13-170">The `Train()` method executes the following tasks:</span></span>

* <span data-ttu-id="6ef13-171">載入資料。</span><span class="sxs-lookup"><span data-stu-id="6ef13-171">Loads the data.</span></span>
* <span data-ttu-id="6ef13-172">擷取並轉換資料。</span><span class="sxs-lookup"><span data-stu-id="6ef13-172">Extracts and transforms the data.</span></span>
* <span data-ttu-id="6ef13-173">將模型定型。</span><span class="sxs-lookup"><span data-stu-id="6ef13-173">Trains the model.</span></span>
* <span data-ttu-id="6ef13-174">傳回模型。</span><span class="sxs-lookup"><span data-stu-id="6ef13-174">Returns the model.</span></span>

<span data-ttu-id="6ef13-175">`Train` 方法會將模型定型。</span><span class="sxs-lookup"><span data-stu-id="6ef13-175">The `Train` method trains the model.</span></span> <span data-ttu-id="6ef13-176">請使用下列程式碼，在緊接著 `Main` 底下建立該方法：</span><span class="sxs-lookup"><span data-stu-id="6ef13-176">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

## <a name="load-and-transform-data"></a><span data-ttu-id="6ef13-177">載入並轉換資料</span><span class="sxs-lookup"><span data-stu-id="6ef13-177">Load and transform data</span></span>

<span data-ttu-id="6ef13-178">ML.NET 使用 [IDataView 類別](xref:Microsoft.ML.IDataView)作為描述數字或文字表格式資料彈性且有效率的方式。</span><span class="sxs-lookup"><span data-stu-id="6ef13-178">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="6ef13-179">`IDataView` 可載入文字檔案或即時資料 (例如 SQL 資料庫或記錄檔)。</span><span class="sxs-lookup"><span data-stu-id="6ef13-179">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span> <span data-ttu-id="6ef13-180">將下列程式碼新增為 `Train()` 方法的第一行：</span><span class="sxs-lookup"><span data-stu-id="6ef13-180">Add the following code as the first line of the `Train()` method:</span></span>

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "loading training dataset")]

<span data-ttu-id="6ef13-181">因為您希望預測計程車的車資，`FareAmount` 資料行便是您將預測的 `Label` (模型的輸出)。請使用 `CopyColumnsEstimator` 轉換類別複製 `FareAmount`，並新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="6ef13-181">As you want to predict the taxi trip fare, the `FareAmount` column is the `Label` that you will predict (the output of the model)Use the `CopyColumnsEstimator` transformation class to copy `FareAmount`, and add the following code:</span></span> 

[!code-csharp[CopyColumnsEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Use the CopyColumnsEstimator")]

<span data-ttu-id="6ef13-182">將模型定型的演算法需要**數值**特徵，因此您需要將類別目錄資料 (`VendorId`、`RateCode` 與 `PaymentType`) 值轉換成數字 (`VendorIdEncoded`、`RateCodeEncoded` 與 `PaymentTypeEncoded`)。</span><span class="sxs-lookup"><span data-stu-id="6ef13-182">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers (`VendorIdEncoded`, `RateCodeEncoded`, and `PaymentTypeEncoded`).</span></span> <span data-ttu-id="6ef13-183">若要進行該操作，請使用 [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) 轉換類別，這會將不同數值索引鍵值指派給每個資料行中的不同值，並新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="6ef13-183">To do that, use the [OneHotEncodingTransformer](xref:Microsoft.ML.Transforms.OneHotEncodingTransformer) transformation class, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

[!code-csharp[OneHotEncodingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Use the OneHotEncodingEstimator")]

<span data-ttu-id="6ef13-184">資料準備工作的最後一個步驟是使用 `mlContext.Transforms.Concatenate` 轉換類別，將所有特徵資料行合併為 **Features** 資料行。</span><span class="sxs-lookup"><span data-stu-id="6ef13-184">The last step in data preparation combines all of the feature columns into the **Features** column using the `mlContext.Transforms.Concatenate` transformation class.</span></span> <span data-ttu-id="6ef13-185">根據預設，學習演算法只會處理來自 **Features** 資料行的特徵。</span><span class="sxs-lookup"><span data-stu-id="6ef13-185">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="6ef13-186">加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="6ef13-186">Add the following code:</span></span>

[!code-csharp[ColumnConcatenatingEstimator](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="6ef13-187">選擇學習演算法</span><span class="sxs-lookup"><span data-stu-id="6ef13-187">Choose a learning algorithm</span></span>

<span data-ttu-id="6ef13-188">此問題是關於預測紐約市的計程車車資。</span><span class="sxs-lookup"><span data-stu-id="6ef13-188">This problem is about predicting a taxi trip fare in New York City.</span></span> <span data-ttu-id="6ef13-189">乍看之下，這可能看似單純取決於行程遠近。</span><span class="sxs-lookup"><span data-stu-id="6ef13-189">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="6ef13-190">不過，紐約計程車廠商會針對其他因素 (例如額外的乘客，或使用信用卡而非現金付費) 收取不同的金額。</span><span class="sxs-lookup"><span data-stu-id="6ef13-190">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span> <span data-ttu-id="6ef13-191">您希望根據資料集當中的其他因素來預測價格值，這是一個實際值。</span><span class="sxs-lookup"><span data-stu-id="6ef13-191">You want to predict the price value, which is a real value, based on the other factors in the dataset.</span></span> <span data-ttu-id="6ef13-192">為了執行該操作，您選擇[迴歸](../resources/glossary.md#regression)機器學習服務工作。</span><span class="sxs-lookup"><span data-stu-id="6ef13-192">To do that, you choose a [regression](../resources/glossary.md#regression) machine learning task.</span></span>

<span data-ttu-id="6ef13-193">請將下列內容新增為 `Train()` 中的下一行程式碼，來將 [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) 機器學習服務工作新增到資料轉換定義：</span><span class="sxs-lookup"><span data-stu-id="6ef13-193">Append the [FastTreeRegressionTrainer](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer) machine learning task to the data transformation definitions by adding the following as the next line of code in `Train()`:</span></span>

[!code-csharp[FastTreeRegressionTrainer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="6ef13-194">將模型定型</span><span class="sxs-lookup"><span data-stu-id="6ef13-194">Train the model</span></span>

<span data-ttu-id="6ef13-195">在 `Train()` 方法中新增下列程式碼，調整模型使其符合定型的 `dataview`，並傳回已定型的模型：</span><span class="sxs-lookup"><span data-stu-id="6ef13-195">Fit the model to the training `dataview` and return the trained model by adding the following line of code in the `Train()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#11 "Train the model")]

<span data-ttu-id="6ef13-196">[Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) 方法會透過轉換資料集和套用定型來定型模型。</span><span class="sxs-lookup"><span data-stu-id="6ef13-196">The [Fit()](xref:Microsoft.ML.Trainers.FastTree.FastTreeRegressionTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="6ef13-197">使用 `Train()` 方法中的下列程式碼行，傳回定型的模型：</span><span class="sxs-lookup"><span data-stu-id="6ef13-197">Return the trained model with the following line of code in the `Train()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="6ef13-198">評估模型</span><span class="sxs-lookup"><span data-stu-id="6ef13-198">Evaluate the model</span></span>

<span data-ttu-id="6ef13-199">接下來，使用測試資料評估您的模型效能，以進行品質保證和驗證。</span><span class="sxs-lookup"><span data-stu-id="6ef13-199">Next, evaluate your model performance with your test data for quality assurance and validation.</span></span> <span data-ttu-id="6ef13-200">在 `Train()` 之後，使用下列程式碼建立 `Evaluate()` 方法：</span><span class="sxs-lookup"><span data-stu-id="6ef13-200">Create the `Evaluate()` method, just after `Train()`, with the following code:</span></span>

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="6ef13-201">`Evaluate` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="6ef13-201">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="6ef13-202">載入測試資料集。</span><span class="sxs-lookup"><span data-stu-id="6ef13-202">Loads the test dataset.</span></span>
* <span data-ttu-id="6ef13-203">建立迴歸評估工具。</span><span class="sxs-lookup"><span data-stu-id="6ef13-203">Creates the regression evaluator.</span></span>
* <span data-ttu-id="6ef13-204">評估模型並建立計量。</span><span class="sxs-lookup"><span data-stu-id="6ef13-204">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="6ef13-205">顯示計量。</span><span class="sxs-lookup"><span data-stu-id="6ef13-205">Displays the metrics.</span></span>

<span data-ttu-id="6ef13-206">請使用下列程式碼，在緊接著 `Train` 方法呼叫底下，從 `Main` 方法新增對新方法的呼叫：</span><span class="sxs-lookup"><span data-stu-id="6ef13-206">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Call the Evaluate method")]

<span data-ttu-id="6ef13-207">使用 [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) 方法載入測試資料集。</span><span class="sxs-lookup"><span data-stu-id="6ef13-207">Load the test dataset using the [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method.</span></span> <span data-ttu-id="6ef13-208">透過在 `Evaluate` 方法中新增下列程式碼，使用此資料集作為品質檢查來評估模型：</span><span class="sxs-lookup"><span data-stu-id="6ef13-208">Evaluate the model using this dataset as a quality check by adding the following code in the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Load the test dataset")]

<span data-ttu-id="6ef13-209">接下來，透過將下列程式碼新增到 `EvaluateModel()` 來轉換 `Test` 資料：</span><span class="sxs-lookup"><span data-stu-id="6ef13-209">Next, transform the `Test` data by adding the following code to `EvaluateModel()`:</span></span>

[!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Predict using the Transformer")]

<span data-ttu-id="6ef13-210">[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) 方法會針對測試資料集輸入資料列進行預測。</span><span class="sxs-lookup"><span data-stu-id="6ef13-210">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for the test dataset input rows.</span></span>

<span data-ttu-id="6ef13-211">`RegressionContext.Evaluate` 方法會使用指定的資料集來計算 `PredictionModel` 的品質計量。</span><span class="sxs-lookup"><span data-stu-id="6ef13-211">The `RegressionContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="6ef13-212">它傳回的 <xref:Microsoft.ML.Data.RegressionMetrics> 物件包含迴歸評估工具所計算的整體計量。</span><span class="sxs-lookup"><span data-stu-id="6ef13-212">It returns a <xref:Microsoft.ML.Data.RegressionMetrics> object that contains the overall metrics computed by regression evaluators.</span></span> 

<span data-ttu-id="6ef13-213">若要顯示這些計量以判斷模型的品質，您必須先取得計量。</span><span class="sxs-lookup"><span data-stu-id="6ef13-213">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="6ef13-214">將下列程式碼加入為 `Evaluate` 方法中的下一行：</span><span class="sxs-lookup"><span data-stu-id="6ef13-214">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Compute Metrics")]

<span data-ttu-id="6ef13-215">在您設定好預測後，[Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) 方法會評估模型，將預測值與測試資料集中的實際 `Labels` 進行比較，並傳回模型的執行情況。</span><span class="sxs-lookup"><span data-stu-id="6ef13-215">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RegressionCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="6ef13-216">新增下列程式碼來評估模型並產生評估計量：</span><span class="sxs-lookup"><span data-stu-id="6ef13-216">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

<span data-ttu-id="6ef13-217">[RSquared](../resources/glossary.md#coefficient-of-determination) 是迴歸模型的另一個評估計量。</span><span class="sxs-lookup"><span data-stu-id="6ef13-217">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="6ef13-218">RSquared 接受介於 0 和 1 之間的值。</span><span class="sxs-lookup"><span data-stu-id="6ef13-218">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="6ef13-219">其值越接近 1，模型就越好。</span><span class="sxs-lookup"><span data-stu-id="6ef13-219">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="6ef13-220">將下列程式碼新增至 `Evaluate` 方法，以顯示 RSquared 值：</span><span class="sxs-lookup"><span data-stu-id="6ef13-220">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#18 "Display the RSquared metric.")]

<span data-ttu-id="6ef13-221">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) 是迴歸模型的評估計量之一。</span><span class="sxs-lookup"><span data-stu-id="6ef13-221">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="6ef13-222">此計量值越低，模型就越好。</span><span class="sxs-lookup"><span data-stu-id="6ef13-222">The lower it is, the better the model is.</span></span> <span data-ttu-id="6ef13-223">將下列程式碼新增至 `Evaluate` 方法，以顯示 RMS 值：</span><span class="sxs-lookup"><span data-stu-id="6ef13-223">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="6ef13-224">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="6ef13-224">Use the model for predictions</span></span>

<span data-ttu-id="6ef13-225">請使用下列程式碼，在緊接著 `Evaluate` 方法之後，建立 `TestSinglePrediction` 方法：</span><span class="sxs-lookup"><span data-stu-id="6ef13-225">Create the `TestSinglePrediction` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void TestSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="6ef13-226">`TestSinglePrediction` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="6ef13-226">The `TestSinglePrediction` method executes the following tasks:</span></span>

* <span data-ttu-id="6ef13-227">建立測試資料的單一評論。</span><span class="sxs-lookup"><span data-stu-id="6ef13-227">Creates a single comment of test data.</span></span>
* <span data-ttu-id="6ef13-228">根據測試資料預測費用金額。</span><span class="sxs-lookup"><span data-stu-id="6ef13-228">Predicts fare amount based on test data.</span></span>
* <span data-ttu-id="6ef13-229">合併測試資料和預測來進行報告。</span><span class="sxs-lookup"><span data-stu-id="6ef13-229">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="6ef13-230">顯示預測的結果。</span><span class="sxs-lookup"><span data-stu-id="6ef13-230">Displays the predicted results.</span></span>

<span data-ttu-id="6ef13-231">請使用下列程式碼，在緊接著 `Evaluate` 方法呼叫底下，從 `Main` 方法新增對新方法的呼叫：</span><span class="sxs-lookup"><span data-stu-id="6ef13-231">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallTestSinglePrediction](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#20 "Call the TestSinglePrediction method")]

<span data-ttu-id="6ef13-232">將下列程式碼新增到 `TestSinglePrediction()` 來使用 `PredictionEngine` 預測車資：</span><span class="sxs-lookup"><span data-stu-id="6ef13-232">Use the `PredictionEngine` to predict the fare by adding the following code to `TestSinglePrediction()`:</span></span>

[!code-csharp[MakePredictionEngine](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#22 "Create the PredictionFunction")]

<span data-ttu-id="6ef13-233">[PredictionEngine 類別](xref:Microsoft.ML.PredictionEngine%602)是一種便利的 API，可讓您傳遞單一資料執行個體，並在其上執行預測。</span><span class="sxs-lookup"><span data-stu-id="6ef13-233">The [PredictionEngine class](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass a single instance of data and then perform a prediction on it.</span></span>

<span data-ttu-id="6ef13-234">本教學課程會使用此類別內的一個測試行程。</span><span class="sxs-lookup"><span data-stu-id="6ef13-234">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="6ef13-235">您可以稍後新增其他案例來對此方法進行實驗。</span><span class="sxs-lookup"><span data-stu-id="6ef13-235">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="6ef13-236">透過建立 `TaxiTrip` 的執行個體，在 `TestSinglePrediction()` 方法中新增車程，以測試定型模型的費用預測：</span><span class="sxs-lookup"><span data-stu-id="6ef13-236">Add a trip to test the trained model's prediction of cost in the `TestSinglePrediction()` method by creating an instance of `TaxiTrip`:</span></span>

[!code-csharp[PredictionData](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#23 "Create test data for single prediction")]

<span data-ttu-id="6ef13-237">接下來，根據計程車車程資料的單一執行個體預測車資，然後透過將下列內容作為 `TestSinglePrediction()` 方法的下一行程式碼，來將它傳遞至 `PredictionEngine`：</span><span class="sxs-lookup"><span data-stu-id="6ef13-237">Next, predict the fare based on a single instance of the taxi trip data and pass it to the `PredictionEngine` by adding the following as the next lines of code in the `TestSinglePrediction()` method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#24 "Create a prediction of taxi fare")]

<span data-ttu-id="6ef13-238">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) 函式會在資料的單一執行個體上進行預測。</span><span class="sxs-lookup"><span data-stu-id="6ef13-238">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single instance of data.</span></span>

<span data-ttu-id="6ef13-239">若要顯示指定之車程的預測費用，請將下列程式碼加入到 `TestSinglePrediction` 方法：</span><span class="sxs-lookup"><span data-stu-id="6ef13-239">To display the predicted fare of the specified trip, add the following code into the `TestSinglePrediction` method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#25 "Display the prediction.")]

<span data-ttu-id="6ef13-240">執行程式以查看您測試案例的預測計程車車資。</span><span class="sxs-lookup"><span data-stu-id="6ef13-240">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="6ef13-241">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="6ef13-241">Congratulations!</span></span> <span data-ttu-id="6ef13-242">您現在已成功建置可預測計程車車資的機器學習模型、評估了它的準確率，並且也使用它進行了預測。</span><span class="sxs-lookup"><span data-stu-id="6ef13-242">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="6ef13-243">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="6ef13-243">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6ef13-244">後續步驟</span><span class="sxs-lookup"><span data-stu-id="6ef13-244">Next steps</span></span>

<span data-ttu-id="6ef13-245">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="6ef13-245">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="6ef13-246">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="6ef13-246">Prepare and understand the data</span></span>
> * <span data-ttu-id="6ef13-247">建立學習管線</span><span class="sxs-lookup"><span data-stu-id="6ef13-247">Create a learning pipeline</span></span>
> * <span data-ttu-id="6ef13-248">載入並轉換資料</span><span class="sxs-lookup"><span data-stu-id="6ef13-248">Load and transform the data</span></span>
> * <span data-ttu-id="6ef13-249">選擇學習演算法</span><span class="sxs-lookup"><span data-stu-id="6ef13-249">Choose a learning algorithm</span></span>
> * <span data-ttu-id="6ef13-250">將模型定型</span><span class="sxs-lookup"><span data-stu-id="6ef13-250">Train the model</span></span>
> * <span data-ttu-id="6ef13-251">評估模型</span><span class="sxs-lookup"><span data-stu-id="6ef13-251">Evaluate the model</span></span>
> * <span data-ttu-id="6ef13-252">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="6ef13-252">Use the model for predictions</span></span>

<span data-ttu-id="6ef13-253">前進到下一個教學課程來深入了解。</span><span class="sxs-lookup"><span data-stu-id="6ef13-253">Advance to the next tutorial to learn more.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6ef13-254">Iris 叢集</span><span class="sxs-lookup"><span data-stu-id="6ef13-254">Iris clustering</span></span>](iris-clustering.md)
