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
# <a name="tutorial-use-mlnet-to-predict-new-york-taxi-fares-regression"></a><span data-ttu-id="b1366-103">教學課程：使用 ML.NET 來預測紐約計程車車資 (迴歸)</span><span class="sxs-lookup"><span data-stu-id="b1366-103">Tutorial: Use ML.NET to predict New York taxi fares (regression)</span></span>

> [!NOTE]
> <span data-ttu-id="b1366-104">本主題參考 ML.NET，此功能目前為公開預覽版，而可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="b1366-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="b1366-105">如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) \(英文)\。</span><span class="sxs-lookup"><span data-stu-id="b1366-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="b1366-106">本教學課程說明如何使用 ML.NET 來建置用於預測紐約市計程車車資的 [迴歸模型](../resources/glossary.md#regression)。</span><span class="sxs-lookup"><span data-stu-id="b1366-106">This tutorial illustrates how to use ML.NET to build a [regression model](../resources/glossary.md#regression) for predicting New York City taxi fares.</span></span>

<span data-ttu-id="b1366-107">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="b1366-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="b1366-108">了解問題</span><span class="sxs-lookup"><span data-stu-id="b1366-108">Understand the problem</span></span>
> * <span data-ttu-id="b1366-109">選取適當的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="b1366-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="b1366-110">準備並了解您的資料</span><span class="sxs-lookup"><span data-stu-id="b1366-110">Prepare and understand your data</span></span>
> * <span data-ttu-id="b1366-111">建立學習管線</span><span class="sxs-lookup"><span data-stu-id="b1366-111">Create a learning pipeline</span></span>
> * <span data-ttu-id="b1366-112">載入並轉換您的資料</span><span class="sxs-lookup"><span data-stu-id="b1366-112">Load and transform your data</span></span>
> * <span data-ttu-id="b1366-113">選擇學習演算法</span><span class="sxs-lookup"><span data-stu-id="b1366-113">Choose a learning algorithm</span></span>
> * <span data-ttu-id="b1366-114">將模型定型</span><span class="sxs-lookup"><span data-stu-id="b1366-114">Train the model</span></span>
> * <span data-ttu-id="b1366-115">評估模型</span><span class="sxs-lookup"><span data-stu-id="b1366-115">Evaluate the model</span></span>
> * <span data-ttu-id="b1366-116">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="b1366-116">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b1366-117">必要條件</span><span class="sxs-lookup"><span data-stu-id="b1366-117">Prerequisites</span></span>

* <span data-ttu-id="b1366-118">已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)。</span><span class="sxs-lookup"><span data-stu-id="b1366-118">[Visual Studio 2017 15.6 or later](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="b1366-119">了解問題</span><span class="sxs-lookup"><span data-stu-id="b1366-119">Understand the problem</span></span>

<span data-ttu-id="b1366-120">此問題的焦點在於**預測紐約市計程車的車資**。</span><span class="sxs-lookup"><span data-stu-id="b1366-120">This problem is centered around **predicting the fare of a taxi trip in New York City**.</span></span> <span data-ttu-id="b1366-121">乍看之下，這可能看似單純取決於行程遠近。</span><span class="sxs-lookup"><span data-stu-id="b1366-121">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="b1366-122">不過，紐約計程車廠商會針對其他因素 (例如額外的乘客，或使用信用卡而非現金付費) 收取不同的金額。</span><span class="sxs-lookup"><span data-stu-id="b1366-122">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="b1366-123">選取適當的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="b1366-123">Select the appropriate machine learning task</span></span>

<span data-ttu-id="b1366-124">若要預測計程車車資，您需先選取適當的機器學習工作。</span><span class="sxs-lookup"><span data-stu-id="b1366-124">To predict the taxi fare, you first select the appropriate machine learning task.</span></span> <span data-ttu-id="b1366-125">您希望根據資料集內的其他因素來預測實際值 (一個代表價格的雙精度浮點數)。</span><span class="sxs-lookup"><span data-stu-id="b1366-125">You are looking to predict a real value (a double that represents price) based on the other factors in the dataset.</span></span> <span data-ttu-id="b1366-126">您需選擇[**迴歸**](../resources/glossary.md#regression)工作。</span><span class="sxs-lookup"><span data-stu-id="b1366-126">You choose a [**regression**](../resources/glossary.md#regression) task.</span></span>

<span data-ttu-id="b1366-127">模型的定型程序會識別資料集內的哪些因素，在預測最終車資價格時最具影響力。</span><span class="sxs-lookup"><span data-stu-id="b1366-127">The process of training the model identifies which factors in the dataset are most influential when predicting the final fare price.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="b1366-128">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="b1366-128">Create a console application</span></span>

1. <span data-ttu-id="b1366-129">開啟 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="b1366-129">Open Visual Studio 2017.</span></span> <span data-ttu-id="b1366-130">從功能表列中選取 [檔案]  >  [新增]  >  [專案]。</span><span class="sxs-lookup"><span data-stu-id="b1366-130">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="b1366-131">在 [新增專案] 對話方塊中，選取 [Visual C#] 節點，然後選取 [.NET Core] 節點。</span><span class="sxs-lookup"><span data-stu-id="b1366-131">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="b1366-132">然後選取 [主控台應用程式 (.NET Core)] 專案範本。</span><span class="sxs-lookup"><span data-stu-id="b1366-132">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="b1366-133">在 [名稱] 文字方塊中，輸入 "TaxiFarePrediction"，然後選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b1366-133">In the **Name** text box, type "TaxiFarePrediction" and then select the **OK** button.</span></span>

2. <span data-ttu-id="b1366-134">在您的專案中建立一個名為 *Data* 的目錄以儲存資料集檔案：</span><span class="sxs-lookup"><span data-stu-id="b1366-134">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="b1366-135">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [新增] > [新增資料夾]。</span><span class="sxs-lookup"><span data-stu-id="b1366-135">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="b1366-136">輸入 "Data"，然後按 Enter。</span><span class="sxs-lookup"><span data-stu-id="b1366-136">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="b1366-137">安裝「Microsoft.ML NuGet 套件」：</span><span class="sxs-lookup"><span data-stu-id="b1366-137">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="b1366-138">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="b1366-138">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="b1366-139">選擇 "nuget.org" 作為 [套件來源]，選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b1366-139">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="b1366-140">在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。</span><span class="sxs-lookup"><span data-stu-id="b1366-140">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-and-understand-your-data"></a><span data-ttu-id="b1366-141">準備並了解您的資料</span><span class="sxs-lookup"><span data-stu-id="b1366-141">Prepare and understand your data</span></span>

1. <span data-ttu-id="b1366-142">下載 [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) 和 [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) 資料集，並將它們儲存至先前建立的 [Data] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="b1366-142">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="b1366-143">Taxi Trip 資料集會將機器學習模型定型，並可用來評估您模型的準確率。</span><span class="sxs-lookup"><span data-stu-id="b1366-143">The Taxi Trip data set trains the machine learning model and can be used to evaluate how accurate your model is.</span></span> <span data-ttu-id="b1366-144">這些資料集原先來自 [NYC TLC Taxi Trip 資料集](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)。</span><span class="sxs-lookup"><span data-stu-id="b1366-144">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

2. <span data-ttu-id="b1366-145">在 [方案總管] 中，於每個 \*.csv 檔案上按一下滑鼠右鍵，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="b1366-145">In Solution Explorer, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="b1366-146">在 [進階] 底下，將 [複製到輸出目錄]的值變更為 [永遠]。</span><span class="sxs-lookup"><span data-stu-id="b1366-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Always**.</span></span>

3. <span data-ttu-id="b1366-147">在程式碼編輯器中開啟 **taxi-fare-train.csv** 資料集，然後查看第一個資料列中的資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="b1366-147">Open the **taxi-fare-train.csv** data set in the code editor and look at column headers in the first row.</span></span> <span data-ttu-id="b1366-148">請查看每個資料行。</span><span class="sxs-lookup"><span data-stu-id="b1366-148">Take a look at each of the columns.</span></span> <span data-ttu-id="b1366-149">了解資料並判斷哪些資料行是**特徵**，以及哪個是**標籤**。</span><span class="sxs-lookup"><span data-stu-id="b1366-149">Understand the data and decide which columns are **features** and which is the **label**.</span></span>

<span data-ttu-id="b1366-150">**標籤**是您嘗試預測之資料行的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b1366-150">The **label** is the identifier of the column you are trying to predict.</span></span> <span data-ttu-id="b1366-151">所識別的**特徵**會用來預測標籤。</span><span class="sxs-lookup"><span data-stu-id="b1366-151">The identified **features** are used to predict the label.</span></span>

* <span data-ttu-id="b1366-152">**vendor_id：** 計程車廠商的識別碼是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="b1366-152">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="b1366-153">**rate_code：** 計程車行程的費率類型是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="b1366-153">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="b1366-154">**passenger_count：** 行程的乘客數目是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="b1366-154">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="b1366-155">**trip_time_in_secs：** 行程所花費的時間長度。</span><span class="sxs-lookup"><span data-stu-id="b1366-155">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="b1366-156">您將必須等到行程完成之後，才能知道行程所花費的時間長度。</span><span class="sxs-lookup"><span data-stu-id="b1366-156">You won't know how long the trip takes until after it is completed.</span></span> <span data-ttu-id="b1366-157">您需將此資料行從模型中排除。</span><span class="sxs-lookup"><span data-stu-id="b1366-157">You exclude this column from the model.</span></span>
* <span data-ttu-id="b1366-158">**trip_distance：** 行程的距離是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="b1366-158">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="b1366-159">**payment_type：** 付款方式 (現金或信用卡) 是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="b1366-159">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="b1366-160">**fare_amount：** 計程車車資總計是標籤。</span><span class="sxs-lookup"><span data-stu-id="b1366-160">**fare_amount:** The total taxi fare paid is the label.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="b1366-161">建立類別及定義路徑</span><span class="sxs-lookup"><span data-stu-id="b1366-161">Create classes and define paths</span></span>

<span data-ttu-id="b1366-162">在 *Program.cs* 檔案頂端新增下列額外的 `using` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="b1366-162">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="b1366-163">您必須建立三個全域變數，以保存最近所下載檔案及儲存模型的路徑：</span><span class="sxs-lookup"><span data-stu-id="b1366-163">You need to create three global variables to hold the paths to the recently downloaded files and to save the model:</span></span>

* <span data-ttu-id="b1366-164">`_datapath` 包含用來將模型定型的資料集路徑。</span><span class="sxs-lookup"><span data-stu-id="b1366-164">`_datapath` has the path to the data set used to train the model.</span></span>
* <span data-ttu-id="b1366-165">`_testdatapath` 包含用來評估模型的資料集路徑。</span><span class="sxs-lookup"><span data-stu-id="b1366-165">`_testdatapath` has the path to the data set used to evaluate the model.</span></span>
* <span data-ttu-id="b1366-166">`_modelpath` 包含用來儲存定型模型的路徑。</span><span class="sxs-lookup"><span data-stu-id="b1366-166">`_modelpath` has the path where the trained model is stored.</span></span>

<span data-ttu-id="b1366-167">將下列程式碼新增至緊接在 `Main` 上方的一行，以指定最近下載的檔案：</span><span class="sxs-lookup"><span data-stu-id="b1366-167">Add the following code to the line right above `Main` to specify the recently downloaded files:</span></span>

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="b1366-168">接著，為輸入資料和預測建立類別：</span><span class="sxs-lookup"><span data-stu-id="b1366-168">Next, create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="b1366-169">在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="b1366-169">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="b1366-170">在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *TaxiTrip.cs*。</span><span class="sxs-lookup"><span data-stu-id="b1366-170">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="b1366-171">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b1366-171">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="b1366-172">將下列 `using` 陳述式新增至新的檔案：</span><span class="sxs-lookup"><span data-stu-id="b1366-172">Add the following `using` statements to the new file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="b1366-173">移除現有的類別定義，然後將下列程式碼 (具有 `TaxiTrip` 和 `TaxiTripFarePrediction` 這兩個類別) 新增至 *TaxiTrip.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="b1366-173">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="b1366-174">`TaxiTrip` 是輸入資料集類別，並含有每個資料集資料行的定義。</span><span class="sxs-lookup"><span data-stu-id="b1366-174">`TaxiTrip` is the input data set class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="b1366-175">`TaxiTripFarePrediction` 類別會在模型定型後，用來進行預測。</span><span class="sxs-lookup"><span data-stu-id="b1366-175">The `TaxiTripFarePrediction` class is used for prediction after the model has been trained.</span></span> <span data-ttu-id="b1366-176">它包含一個單一浮點數 (`FareAmount`) 和一個套用的 `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) 屬性。</span><span class="sxs-lookup"><span data-stu-id="b1366-176">It has a single float (`FareAmount`) and a `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) attribute applied.</span></span>

<span data-ttu-id="b1366-177">現在，請返回 **Program.cs** 檔案。</span><span class="sxs-lookup"><span data-stu-id="b1366-177">Now go back to the **Program.cs** file.</span></span> <span data-ttu-id="b1366-178">在 `Main` 中，以下列程式碼取代 `Console.WriteLine("Hello World!")`：</span><span class="sxs-lookup"><span data-stu-id="b1366-178">In `Main`, replace the `Console.WriteLine("Hello World!")` with the following code:</span></span>

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

<span data-ttu-id="b1366-179">`Train` 方法會將您的模型定型。</span><span class="sxs-lookup"><span data-stu-id="b1366-179">The `Train` method trains your model.</span></span> <span data-ttu-id="b1366-180">請使用下列程式碼，在緊接著 `Main` 底下，建立該函式：</span><span class="sxs-lookup"><span data-stu-id="b1366-180">Create that function just below `Main`, using the following code:</span></span>

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="b1366-181">建立學習管線</span><span class="sxs-lookup"><span data-stu-id="b1366-181">Create a learning pipeline</span></span>

<span data-ttu-id="b1366-182">學習管線會載入將模型定型所需的所有資料和演算法。</span><span class="sxs-lookup"><span data-stu-id="b1366-182">The learning pipeline loads all of the data and algorithms necessary to train the model.</span></span> <span data-ttu-id="b1366-183">將下列程式碼新增至 `Train()` 方法：</span><span class="sxs-lookup"><span data-stu-id="b1366-183">Add the following code into the `Train()` method:</span></span>

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-your-data"></a><span data-ttu-id="b1366-184">載入並轉換您的資料</span><span class="sxs-lookup"><span data-stu-id="b1366-184">Load and transform your data</span></span>

<span data-ttu-id="b1366-185">接著，將您的資料載入管線。</span><span class="sxs-lookup"><span data-stu-id="b1366-185">Next, load your data into the pipeline.</span></span> <span data-ttu-id="b1366-186">指向一開始建立的 `_datapath`，並指定 .csv file 的分隔符號 (,)。</span><span class="sxs-lookup"><span data-stu-id="b1366-186">Point to the `_datapath` created initially and specify the delimiter of the .csv file (,).</span></span> <span data-ttu-id="b1366-187">將下列程式碼新增至 `Train()` 方法中、上一個步驟底下：</span><span class="sxs-lookup"><span data-stu-id="b1366-187">Add the following code into the `Train()` method underneath the last step:</span></span>

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(separator:','));
```

<span data-ttu-id="b1366-188">您將在要建立的程式碼中，以不使用底線的方式參考資料行。</span><span class="sxs-lookup"><span data-stu-id="b1366-188">You'll refer to the columns without the underscores in the code you're creating.</span></span> <span data-ttu-id="b1366-189">請使用 `ColumnCopier()` 函式將 `FareAmount` 資料行複製到名為 "Label" 的新資料行中。</span><span class="sxs-lookup"><span data-stu-id="b1366-189">Copy the `FareAmount` column into a new column called "Label" using the `ColumnCopier()` function.</span></span> <span data-ttu-id="b1366-190">此資料行就是**標籤**。</span><span class="sxs-lookup"><span data-stu-id="b1366-190">This column is the **Label**.</span></span>

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

<span data-ttu-id="b1366-191">請進行一些**特徵工程**來轉換資料，以便能夠有效地使用此資料來進行機器學習。</span><span class="sxs-lookup"><span data-stu-id="b1366-191">Conduct some **feature engineering** to transform the data so that it can be used effectively for machine learning.</span></span> <span data-ttu-id="b1366-192">將模型定型的演算法需要**數值**特徵，您需將類別目錄資料 (`VendorId`、`RateCode` 及 `PaymentType`) 轉換成數字。</span><span class="sxs-lookup"><span data-stu-id="b1366-192">The algorithm that trains the model requires **numeric** features, you transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) into numbers.</span></span> <span data-ttu-id="b1366-193">`CategoricalOneHotVectorizer()` 函式會將數值索引鍵指派給這每個資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="b1366-193">The `CategoricalOneHotVectorizer()` function assigns a numeric key to the values in each of these columns.</span></span> <span data-ttu-id="b1366-194">請新增下列程式碼來轉換您的資料：</span><span class="sxs-lookup"><span data-stu-id="b1366-194">Transform your data by adding this code:</span></span>

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

<span data-ttu-id="b1366-195">資料準備的最後一個步驟會使用 `ColumnConcatenator()` 函式，將您的所有**特徵**合併成一個向量。</span><span class="sxs-lookup"><span data-stu-id="b1366-195">The last step in data preparation combines all of your **features** into one vector using the `ColumnConcatenator()` function.</span></span> <span data-ttu-id="b1366-196">這個必要步驟可協助演算法輕鬆處理您的特徵。</span><span class="sxs-lookup"><span data-stu-id="b1366-196">This necessary step helps the algorithm easily process your features.</span></span> <span data-ttu-id="b1366-197">加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="b1366-197">Add the following code:</span></span>

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

<span data-ttu-id="b1366-198">請注意，`trip_time_in_secs` 資料行並未包含在內。</span><span class="sxs-lookup"><span data-stu-id="b1366-198">Notice that the `trip_time_in_secs` column isn't included.</span></span> <span data-ttu-id="b1366-199">您已經判斷它並非有用的預測特徵。</span><span class="sxs-lookup"><span data-stu-id="b1366-199">You already determined that it isn't a useful prediction feature.</span></span>

> [!NOTE]
> <span data-ttu-id="b1366-200">您必須以上述指定的順序將這些步驟新增至管線中，才能成功執行。</span><span class="sxs-lookup"><span data-stu-id="b1366-200">These steps must be added to Pipeline in the order specified above for successful execution.</span></span>

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="b1366-201">選擇學習演算法</span><span class="sxs-lookup"><span data-stu-id="b1366-201">Choose a learning algorithm</span></span>

<span data-ttu-id="b1366-202">將資料新增至管線並將其轉換成正確的輸入格式之後，您需選取學習演算法 (**學習工具**)。</span><span class="sxs-lookup"><span data-stu-id="b1366-202">After adding the data to the pipeline and transforming it into the correct input format, you select a learning algorithm (**learner**).</span></span> <span data-ttu-id="b1366-203">學習演算法會將模型定型。</span><span class="sxs-lookup"><span data-stu-id="b1366-203">The learning algorithm trains the model.</span></span> <span data-ttu-id="b1366-204">針對此問題，您需選取**迴歸工作**，因此會將名為 `FastTreeRegressor()` 的學習工具新增至運用**梯度提升** (Gradient Boosting) 的管線。</span><span class="sxs-lookup"><span data-stu-id="b1366-204">You chose a **regression task** for this problem, so you add a learner called `FastTreeRegressor()` to the pipeline that utilizes **gradient boosting**.</span></span>

<span data-ttu-id="b1366-205">梯度提升是一種適用於迴歸問題的機器學習技術。</span><span class="sxs-lookup"><span data-stu-id="b1366-205">Gradient boosting is a machine learning technique for regression problems.</span></span> <span data-ttu-id="b1366-206">它會以逐步方式建置每個迴歸樹。</span><span class="sxs-lookup"><span data-stu-id="b1366-206">It builds each regression tree in a step-wise fashion.</span></span> <span data-ttu-id="b1366-207">它會使用預先定義的損失函式來評估每個步驟中的誤差，然後在下一個步驟中為其進行修正。</span><span class="sxs-lookup"><span data-stu-id="b1366-207">It uses a pre-defined loss function to measure the error in each step and correct for it in the next.</span></span> <span data-ttu-id="b1366-208">結果會產生一個預測模型，這實際上就是較弱預測模型的總體。</span><span class="sxs-lookup"><span data-stu-id="b1366-208">The result is a prediction model that is actually an ensemble of weaker prediction models.</span></span> <span data-ttu-id="b1366-209">如需有關梯度提升的詳細資訊，請參閱[提升的決策樹迴歸](https://docs.microsoft.com/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="b1366-209">For more information about gradient boosting, see [Boosted Decision Tree Regression](https://docs.microsoft.com/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span></span>

<span data-ttu-id="b1366-210">將下列程式碼新增至 `Train()` 方法中、上一個步驟中新增的資料處理程式碼之後：</span><span class="sxs-lookup"><span data-stu-id="b1366-210">Add the following code into the `Train()` method following the data processing code added in the last step:</span></span>

```csharp
pipeline.Add(new FastTreeRegressor());
```

<span data-ttu-id="b1366-211">您已將上述所有步驟新增至管線中作為個別的陳述式，但 C# 有個便利的集合初始化語法，可讓您更輕鬆地建立管線並將其初始化。</span><span class="sxs-lookup"><span data-stu-id="b1366-211">You added all the preceding steps to the pipeline as individual statements, but C# has a handy collection initialization syntax that makes it simpler to create and initialize the pipeline.</span></span> <span data-ttu-id="b1366-212">以下列程式碼取代您到目前為止已新增至 `Train()` 方法中的程式碼：</span><span class="sxs-lookup"><span data-stu-id="b1366-212">Replace the code you added so far to the `Train()` method with the following code:</span></span>

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a><span data-ttu-id="b1366-213">將模型定型</span><span class="sxs-lookup"><span data-stu-id="b1366-213">Train the model</span></span>

<span data-ttu-id="b1366-214">最後一個步驟是將模型定型。</span><span class="sxs-lookup"><span data-stu-id="b1366-214">The final step is to train the model.</span></span> <span data-ttu-id="b1366-215">到目前為止，尚未執行管線中的任何部分。</span><span class="sxs-lookup"><span data-stu-id="b1366-215">Until this point, nothing in the pipeline has been executed.</span></span> <span data-ttu-id="b1366-216">`pipeline.Train<T_Input, T_Output>()` 函式會採用預先定義的 `TaxiTrip` 類別類型，然後輸出 `TaxiTripFarePrediction` 類型。</span><span class="sxs-lookup"><span data-stu-id="b1366-216">The `pipeline.Train<T_Input, T_Output>()` function takes in the pre-defined `TaxiTrip` class type and outputs a `TaxiTripFarePrediction` type.</span></span> <span data-ttu-id="b1366-217">將這最後一段程式碼新增至 `Train()` 函式：</span><span class="sxs-lookup"><span data-stu-id="b1366-217">Add this final piece of code into the `Train()` function:</span></span>

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

<span data-ttu-id="b1366-218">就是這麼容易！</span><span class="sxs-lookup"><span data-stu-id="b1366-218">And that's it!</span></span> <span data-ttu-id="b1366-219">您已順利將可預測 NYC 中計程車車資的機器學習模型定型。</span><span class="sxs-lookup"><span data-stu-id="b1366-219">You have successfully trained a machine learning model that can predict taxi fares in NYC.</span></span> <span data-ttu-id="b1366-220">現在，請研究一下來了解您模型的準確率，以及模型的使用方式。</span><span class="sxs-lookup"><span data-stu-id="b1366-220">Now take a look to understand how accurate your model is and learn how to consume it.</span></span>

## <a name="save-the-model"></a><span data-ttu-id="b1366-221">儲存模型</span><span class="sxs-lookup"><span data-stu-id="b1366-221">Save the model</span></span>

<span data-ttu-id="b1366-222">在您前進到下一個步驟之前，請先在 `Train()` 函式的結尾新增下列程式碼，來將模型儲存成 .zip 檔案：</span><span class="sxs-lookup"><span data-stu-id="b1366-222">Before you go onto the next step, save your model to a .zip file by adding the following code at the end of your `Train()` function:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

<span data-ttu-id="b1366-223">將 `await` 陳述式新增至 `model.WriteAsync()` 呼叫時，意謂著必須將 `Train()` 方法變更為會傳回 `Task` 的非同步方法。</span><span class="sxs-lookup"><span data-stu-id="b1366-223">Adding the `await` statement to the `model.WriteAsync()` call means that the `Train()` method must be changed to an async method that returns a `Task`.</span></span> <span data-ttu-id="b1366-224">請修改 `Train`，如以下範例所示：</span><span class="sxs-lookup"><span data-stu-id="b1366-224">Modify the signature of `Train` as shown in the following code:</span></span>

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

<span data-ttu-id="b1366-225">變更 `Train` 方法的傳回類型時，意謂著您必須將 `await` 新增至會呼叫 `Main` 方法中 `Train` 的程式碼，如以下程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="b1366-225">Changing the return type of the `Train` method means you have to add an `await` to the code that calls `Train` in the `Main` method as shown in the following code:</span></span>

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

<span data-ttu-id="b1366-226">在 `Main` 方法中新增 `await` 時，意謂著 `Main` 方法必須包含 `async` 修飾詞並傳回 `Task`：</span><span class="sxs-lookup"><span data-stu-id="b1366-226">Adding an `await` in your `Main` method means the `Main` method must have the `async` modifier and return a `Task`:</span></span>

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

<span data-ttu-id="b1366-227">您還必須在檔案頂端新增下列 using 陳述式：</span><span class="sxs-lookup"><span data-stu-id="b1366-227">You also need to add the following using statement at the top of the file:</span></span>

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

<span data-ttu-id="b1366-228">由於 `async Main` 方法是 C# 7.1 中的新功能，而專案的預設語言版本是 C# 7.0，因此您必須將語言版本變更為 C# 7.1 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="b1366-228">Because the `async Main` method is a new feature in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span>
<span data-ttu-id="b1366-229">若要這樣做，請在 [方案總管] 中的專案節點上按一下滑鼠右鍵，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="b1366-229">To do that, right-click on the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="b1366-230">選取 [建置] 索引標籤並選取 [進階] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b1366-230">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="b1366-231">從下拉式清單中，選取 [C# 7.1] (或更新版本)。</span><span class="sxs-lookup"><span data-stu-id="b1366-231">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="b1366-232">選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b1366-232">Select the **OK** button.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="b1366-233">評估模型</span><span class="sxs-lookup"><span data-stu-id="b1366-233">Evaluate the model</span></span>

<span data-ttu-id="b1366-234">評估係指檢查模型運作情況良好程度的程序。</span><span class="sxs-lookup"><span data-stu-id="b1366-234">Evaluation is the process of checking how well the model works.</span></span> <span data-ttu-id="b1366-235">對模型來說，能夠針對在其定型時未使用的資料做出良好的預測，是相當重要的。</span><span class="sxs-lookup"><span data-stu-id="b1366-235">It's important that your model makes good predictions on data that it didn't use when it was trained.</span></span> <span data-ttu-id="b1366-236">若要達到此目的，其中一個做法是將資料分割成定型和測試資料集，就像您在本教學課程中所做的一樣。</span><span class="sxs-lookup"><span data-stu-id="b1366-236">One way to do this is by splitting the data into train and test datasets, as you did in this tutorial.</span></span> <span data-ttu-id="b1366-237">既然您已依據定型資料將模型定型，現在即可查看模型對測試資料的表現。</span><span class="sxs-lookup"><span data-stu-id="b1366-237">Now that you've trained the model on the train data, you can see how well it performs on the test data.</span></span>

<span data-ttu-id="b1366-238">返回您的 `Main` 函式，然後在對 `Train()` 方法的呼叫底下，新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="b1366-238">Go back to your `Main` function and add the following code beneath the call to the `Train()`method:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

<span data-ttu-id="b1366-239">`Evaluate()` 函式會評估您的模型。</span><span class="sxs-lookup"><span data-stu-id="b1366-239">The `Evaluate()` function evaluates your model.</span></span> <span data-ttu-id="b1366-240">請在 `Train()` 底下建立該函式。</span><span class="sxs-lookup"><span data-stu-id="b1366-240">Create that function below `Train()`.</span></span> <span data-ttu-id="b1366-241">加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="b1366-241">Add the following code:</span></span>

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

<span data-ttu-id="b1366-242">使用 `TextLoader()` 函式來載入測試資料。</span><span class="sxs-lookup"><span data-stu-id="b1366-242">Load the test data using the `TextLoader()` function.</span></span> <span data-ttu-id="b1366-243">將下列程式碼新增至 `Evaluate()` 方法：</span><span class="sxs-lookup"><span data-stu-id="b1366-243">Add the following code into the `Evaluate()` method:</span></span>

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

<span data-ttu-id="b1366-244">新增下列程式碼來評估模型並為其產生計量：</span><span class="sxs-lookup"><span data-stu-id="b1366-244">Add the following code to evaluate the model and produce the metrics for it:</span></span>

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

<span data-ttu-id="b1366-245">RMS 是一個用於評估迴歸問題的計量。</span><span class="sxs-lookup"><span data-stu-id="b1366-245">RMS is one metric for evaluating regression problems.</span></span> <span data-ttu-id="b1366-246">此計量值越低，您的模型就越好。</span><span class="sxs-lookup"><span data-stu-id="b1366-246">The lower it is, the better your model.</span></span> <span data-ttu-id="b1366-247">將下列程式碼新增至 `Evaluate()` 函式以顯示模型的 RMS。</span><span class="sxs-lookup"><span data-stu-id="b1366-247">Add the following code into the `Evaluate()` function to print the RMS for your model.</span></span>

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

<span data-ttu-id="b1366-248">RSquared 是另一個用於評估迴歸問題的計量。</span><span class="sxs-lookup"><span data-stu-id="b1366-248">RSquared is another metric for evaluating regression problems.</span></span> <span data-ttu-id="b1366-249">RSquared 會是介於 0 到 1 之間的值。</span><span class="sxs-lookup"><span data-stu-id="b1366-249">RSquared will be a value between 0 and 1.</span></span> <span data-ttu-id="b1366-250">越接近 1，您的模型就越好。</span><span class="sxs-lookup"><span data-stu-id="b1366-250">The closer you are to 1, the better your model.</span></span> <span data-ttu-id="b1366-251">將下列程式碼新增至 `Evaluate()` 函式以顯示模型的 RSquared 值。</span><span class="sxs-lookup"><span data-stu-id="b1366-251">Add the following code into the `Evaluate()` function to print the RSquared value for your model.</span></span>

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="b1366-252">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="b1366-252">Use the model for predictions</span></span>

<span data-ttu-id="b1366-253">接著，建立一個類別來裝載可用來確定模型是否正確運作的測試案例：</span><span class="sxs-lookup"><span data-stu-id="b1366-253">Next, create a class to house test scenarios that you can use to make sure your model is working correctly:</span></span>

1. <span data-ttu-id="b1366-254">在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="b1366-254">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="b1366-255">在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *TestTrips.cs*。</span><span class="sxs-lookup"><span data-stu-id="b1366-255">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestTrips.cs*.</span></span> <span data-ttu-id="b1366-256">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b1366-256">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="b1366-257">將類別修改成靜態，如以下範例所示：</span><span class="sxs-lookup"><span data-stu-id="b1366-257">Modify the class to be static like in the following example:</span></span>

[!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

<span data-ttu-id="b1366-258">本教學課程會使用此類別內的一個測試行程。</span><span class="sxs-lookup"><span data-stu-id="b1366-258">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="b1366-259">您可以稍後新增其他案例來對此範例進行實驗。</span><span class="sxs-lookup"><span data-stu-id="b1366-259">Later you can add other scenarios to experiment with this sample.</span></span> <span data-ttu-id="b1366-260">將下列程式碼新增至 `TestTrips` 類別：</span><span class="sxs-lookup"><span data-stu-id="b1366-260">Add the following code into the `TestTrips` class:</span></span>

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

<span data-ttu-id="b1366-261">這個行程的實際車資是 29.5，但使用 0 作為預留位置。</span><span class="sxs-lookup"><span data-stu-id="b1366-261">This trip's actual fare is 29.5, but use 0 as a placeholder.</span></span> <span data-ttu-id="b1366-262">機器學習演算法將會預測車資。</span><span class="sxs-lookup"><span data-stu-id="b1366-262">The machine learning algorithm will predict the fare.</span></span>

<span data-ttu-id="b1366-263">在 `Main` 函式中新增下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="b1366-263">Add the following code in your `Main` function.</span></span> <span data-ttu-id="b1366-264">它會使用 `TestTrip` 資料來檢驗您的模型：</span><span class="sxs-lookup"><span data-stu-id="b1366-264">It tests out your model using the `TestTrip` data:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

<span data-ttu-id="b1366-265">執行程式以查看您測試案例的預測計程車車資。</span><span class="sxs-lookup"><span data-stu-id="b1366-265">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="b1366-266">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="b1366-266">Congratulations!</span></span> <span data-ttu-id="b1366-267">您現在已成功建置可預測計程車車資的機器學習模型、評估了它的準確率，並且也對它進行了測試。</span><span class="sxs-lookup"><span data-stu-id="b1366-267">You've now successfully built a machine learning model for predicting taxi fares, evaluated its accuracy, and tested it.</span></span> <span data-ttu-id="b1366-268">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="b1366-268">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b1366-269">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b1366-269">Next steps</span></span>

<span data-ttu-id="b1366-270">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="b1366-270">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="b1366-271">了解問題</span><span class="sxs-lookup"><span data-stu-id="b1366-271">Understand the problem</span></span>
> * <span data-ttu-id="b1366-272">選取適當的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="b1366-272">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="b1366-273">準備並了解您的資料</span><span class="sxs-lookup"><span data-stu-id="b1366-273">Prepare and understand your data</span></span>
> * <span data-ttu-id="b1366-274">建立學習管線</span><span class="sxs-lookup"><span data-stu-id="b1366-274">Create a learning pipeline</span></span>
> * <span data-ttu-id="b1366-275">載入並轉換您的資料</span><span class="sxs-lookup"><span data-stu-id="b1366-275">Load and transform your data</span></span>
> * <span data-ttu-id="b1366-276">選擇學習演算法</span><span class="sxs-lookup"><span data-stu-id="b1366-276">Choose a learning algorithm</span></span>
> * <span data-ttu-id="b1366-277">將模型定型</span><span class="sxs-lookup"><span data-stu-id="b1366-277">Train the model</span></span>
> * <span data-ttu-id="b1366-278">評估模型</span><span class="sxs-lookup"><span data-stu-id="b1366-278">Evaluate the model</span></span>
> * <span data-ttu-id="b1366-279">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="b1366-279">Use the model for predictions</span></span>

<span data-ttu-id="b1366-280">請查看我們的 GitHub 存放庫來繼續學習及尋找更多範例。</span><span class="sxs-lookup"><span data-stu-id="b1366-280">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="b1366-281">dotnet/machinelearning GitHub 存放庫</span><span class="sxs-lookup"><span data-stu-id="b1366-281">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
