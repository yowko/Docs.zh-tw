---
title: 使用 ML.NET 來預測紐約計程車車資 (迴歸)
description: 了解如何在迴歸案例中使用 ML.NET。
author: aditidugar
ms.author: johalex
ms.date: 06/18/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 9706dad0a8e32651496e0404be4501c2c70e9d75
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948627"
---
# <a name="tutorial-use-mlnet-to-predict-new-york-taxi-fares-regression"></a><span data-ttu-id="8db7b-103">教學課程：使用 ML.NET 來預測紐約計程車車資 (迴歸)</span><span class="sxs-lookup"><span data-stu-id="8db7b-103">Tutorial: Use ML.NET to predict New York taxi fares (regression)</span></span>

> [!NOTE]
> <span data-ttu-id="8db7b-104">本主題參考 ML.NET，此功能目前為公開預覽版，而可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="8db7b-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="8db7b-105">如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) \(英文)\。</span><span class="sxs-lookup"><span data-stu-id="8db7b-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="8db7b-106">本教學課程說明如何使用 ML.NET 來建置用於預測紐約市計程車車資的 [迴歸模型](../resources/glossary.md#regression)。</span><span class="sxs-lookup"><span data-stu-id="8db7b-106">This tutorial illustrates how to use ML.NET to build a [regression model](../resources/glossary.md#regression) for predicting New York City taxi fares.</span></span>

<span data-ttu-id="8db7b-107">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="8db7b-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="8db7b-108">了解問題</span><span class="sxs-lookup"><span data-stu-id="8db7b-108">Understand the problem</span></span>
> * <span data-ttu-id="8db7b-109">選取適當的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="8db7b-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="8db7b-110">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="8db7b-110">Prepare and understand the data</span></span>
> * <span data-ttu-id="8db7b-111">建立學習管線</span><span class="sxs-lookup"><span data-stu-id="8db7b-111">Create a learning pipeline</span></span>
> * <span data-ttu-id="8db7b-112">載入並轉換資料</span><span class="sxs-lookup"><span data-stu-id="8db7b-112">Load and transform the data</span></span>
> * <span data-ttu-id="8db7b-113">選擇學習演算法</span><span class="sxs-lookup"><span data-stu-id="8db7b-113">Choose a learning algorithm</span></span>
> * <span data-ttu-id="8db7b-114">將模型定型</span><span class="sxs-lookup"><span data-stu-id="8db7b-114">Train the model</span></span>
> * <span data-ttu-id="8db7b-115">評估模型</span><span class="sxs-lookup"><span data-stu-id="8db7b-115">Evaluate the model</span></span>
> * <span data-ttu-id="8db7b-116">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="8db7b-116">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8db7b-117">必要條件</span><span class="sxs-lookup"><span data-stu-id="8db7b-117">Prerequisites</span></span>

* <span data-ttu-id="8db7b-118">已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)。</span><span class="sxs-lookup"><span data-stu-id="8db7b-118">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="8db7b-119">了解問題</span><span class="sxs-lookup"><span data-stu-id="8db7b-119">Understand the problem</span></span>

<span data-ttu-id="8db7b-120">此問題的焦點在於**預測紐約市計程車的車資**。</span><span class="sxs-lookup"><span data-stu-id="8db7b-120">This problem is centered around **predicting the fare of a taxi trip in New York City**.</span></span> <span data-ttu-id="8db7b-121">乍看之下，這可能看似單純取決於行程遠近。</span><span class="sxs-lookup"><span data-stu-id="8db7b-121">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="8db7b-122">不過，紐約計程車廠商會針對其他因素 (例如額外的乘客，或使用信用卡而非現金付費) 收取不同的金額。</span><span class="sxs-lookup"><span data-stu-id="8db7b-122">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="8db7b-123">選取適當的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="8db7b-123">Select the appropriate machine learning task</span></span>

<span data-ttu-id="8db7b-124">若要預測計程車車資，您需先選取適當的機器學習工作。</span><span class="sxs-lookup"><span data-stu-id="8db7b-124">To predict the taxi fare, you first select the appropriate machine learning task.</span></span> <span data-ttu-id="8db7b-125">您希望根據資料集內的其他因素來預測實際值 (一個代表價格的雙精度浮點數)。</span><span class="sxs-lookup"><span data-stu-id="8db7b-125">You are looking to predict a real value (a double that represents price) based on the other factors in the dataset.</span></span> <span data-ttu-id="8db7b-126">您需選擇[**迴歸**](../resources/glossary.md#regression)工作。</span><span class="sxs-lookup"><span data-stu-id="8db7b-126">You choose a [**regression**](../resources/glossary.md#regression) task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="8db7b-127">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="8db7b-127">Create a console application</span></span>

1. <span data-ttu-id="8db7b-128">開啟 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="8db7b-128">Open Visual Studio 2017.</span></span> <span data-ttu-id="8db7b-129">從功能表列中選取 [檔案]  >  [新增]  >  [專案]。</span><span class="sxs-lookup"><span data-stu-id="8db7b-129">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="8db7b-130">在 [新增專案] 對話方塊中，選取 [Visual C#] 節點，然後選取 [.NET Core] 節點。</span><span class="sxs-lookup"><span data-stu-id="8db7b-130">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="8db7b-131">然後選取 [主控台應用程式 (.NET Core)] 專案範本。</span><span class="sxs-lookup"><span data-stu-id="8db7b-131">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="8db7b-132">在 [名稱] 文字方塊中，輸入 "TaxiFarePrediction"，然後選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="8db7b-132">In the **Name** text box, type "TaxiFarePrediction" and then select the **OK** button.</span></span>

2. <span data-ttu-id="8db7b-133">在您的專案中建立一個名為 *Data* 的目錄以儲存資料集檔案：</span><span class="sxs-lookup"><span data-stu-id="8db7b-133">Create a directory named *Data* in your project to save the data set files:</span></span>

    <span data-ttu-id="8db7b-134">在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取 [新增] > [新增資料夾]。</span><span class="sxs-lookup"><span data-stu-id="8db7b-134">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="8db7b-135">輸入 "Data"，然後按 Enter。</span><span class="sxs-lookup"><span data-stu-id="8db7b-135">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="8db7b-136">安裝「Microsoft.ML NuGet 套件」：</span><span class="sxs-lookup"><span data-stu-id="8db7b-136">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="8db7b-137">在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="8db7b-137">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="8db7b-138">選擇 "nuget.org" 作為 [套件來源]，選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="8db7b-138">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="8db7b-139">在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。</span><span class="sxs-lookup"><span data-stu-id="8db7b-139">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="8db7b-140">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="8db7b-140">Prepare and understand the data</span></span>

1. <span data-ttu-id="8db7b-141">下載 [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) 和 [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) 資料集，並將它們儲存至您在上一個步驟所建立的 *Data* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="8db7b-141">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="8db7b-142">我們可以使用這些資料集將機器學習模型定型，然後評估模型的準確程度。</span><span class="sxs-lookup"><span data-stu-id="8db7b-142">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="8db7b-143">這些資料集原先來自 [NYC TLC Taxi Trip 資料集](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)。</span><span class="sxs-lookup"><span data-stu-id="8db7b-143">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

2. <span data-ttu-id="8db7b-144">在 [方案總管] 中，以滑鼠右鍵按一下每個 \*.csv 檔案，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="8db7b-144">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="8db7b-145">在 [進階] 底下，將 [複製到輸出目錄]的值變更為 [永遠]。</span><span class="sxs-lookup"><span data-stu-id="8db7b-145">Under **Advanced**, change the value of **Copy to Output Directory** to **Always**.</span></span>

3. <span data-ttu-id="8db7b-146">開啟 **taxi-fare-train.csv** 資料集，然後查看第一個資料列中的資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="8db7b-146">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="8db7b-147">請查看每個資料行。</span><span class="sxs-lookup"><span data-stu-id="8db7b-147">Take a look at each of the columns.</span></span> <span data-ttu-id="8db7b-148">了解資料，並決定哪些資料行是 **features**，以及哪一個資料行是 **label**。</span><span class="sxs-lookup"><span data-stu-id="8db7b-148">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="8db7b-149">**label** 是您要預測之資料行的識別碼。</span><span class="sxs-lookup"><span data-stu-id="8db7b-149">The **label** is the identifier of the column you want to predict.</span></span> <span data-ttu-id="8db7b-150">所識別的**特徵**會用來預測標籤。</span><span class="sxs-lookup"><span data-stu-id="8db7b-150">The identified **features** are used to predict the label.</span></span>

<span data-ttu-id="8db7b-151">提供的資料集包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="8db7b-151">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="8db7b-152">**vendor_id：** 計程車廠商的識別碼是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="8db7b-152">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="8db7b-153">**rate_code：** 計程車行程的費率類型是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="8db7b-153">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="8db7b-154">**passenger_count：** 行程的乘客數目是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="8db7b-154">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="8db7b-155">**trip_time_in_secs：** 行程所花費的時間長度。</span><span class="sxs-lookup"><span data-stu-id="8db7b-155">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="8db7b-156">您想要在行程結束之前預測行程的車資。</span><span class="sxs-lookup"><span data-stu-id="8db7b-156">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="8db7b-157">那時，您並不知道行程需要多長的時間。</span><span class="sxs-lookup"><span data-stu-id="8db7b-157">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="8db7b-158">因此，行程時間不是一項特徵，您將從模型中排除這個資料行。</span><span class="sxs-lookup"><span data-stu-id="8db7b-158">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="8db7b-159">**trip_distance：** 行程的距離是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="8db7b-159">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="8db7b-160">**payment_type：** 付款方式 (現金或信用卡) 是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="8db7b-160">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="8db7b-161">**fare_amount：** 計程車車資總計是標籤。</span><span class="sxs-lookup"><span data-stu-id="8db7b-161">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="8db7b-162">建立資料類別</span><span class="sxs-lookup"><span data-stu-id="8db7b-162">Create data classes</span></span>

<span data-ttu-id="8db7b-163">為輸入資料和預測建立類別：</span><span class="sxs-lookup"><span data-stu-id="8db7b-163">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="8db7b-164">在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="8db7b-164">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="8db7b-165">在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *TaxiTrip.cs*。</span><span class="sxs-lookup"><span data-stu-id="8db7b-165">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="8db7b-166">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="8db7b-166">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="8db7b-167">將下列的 `using` 指示詞加入新檔案：</span><span class="sxs-lookup"><span data-stu-id="8db7b-167">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="8db7b-168">移除現有的類別定義，然後將下列程式碼 (具有 `TaxiTrip` 和 `TaxiTripFarePrediction` 這兩個類別) 新增至 *TaxiTrip.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="8db7b-168">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="8db7b-169">`TaxiTrip` 是輸入資料類別，並含有每個資料集資料行的定義。</span><span class="sxs-lookup"><span data-stu-id="8db7b-169">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="8db7b-170">請使用 [Column](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) 屬性來指定資料集中來源資料行的索引。</span><span class="sxs-lookup"><span data-stu-id="8db7b-170">Use the [Column](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="8db7b-171">`TaxiTripFarePrediction` 類別用來代表預測的結果。</span><span class="sxs-lookup"><span data-stu-id="8db7b-171">The `TaxiTripFarePrediction` class is used to represent predicted results.</span></span> <span data-ttu-id="8db7b-172">它包含一個套用 `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) 屬性的單一浮點數 (`FareAmount`) 欄位。</span><span class="sxs-lookup"><span data-stu-id="8db7b-172">It has a single float (`FareAmount`) field with a `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) attribute applied.</span></span> <span data-ttu-id="8db7b-173">**Score** 資料行是 ML.NET 中的特殊資料行。</span><span class="sxs-lookup"><span data-stu-id="8db7b-173">The **Score** column is the special column in ML.NET.</span></span> <span data-ttu-id="8db7b-174">模型會將預測值輸出至該資料行。</span><span class="sxs-lookup"><span data-stu-id="8db7b-174">The model outputs predicted values into that column.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="8db7b-175">定義資料和模型路徑</span><span class="sxs-lookup"><span data-stu-id="8db7b-175">Define data and model paths</span></span>

<span data-ttu-id="8db7b-176">請返回 *Program.cs* 檔案，並新增三個欄位，針對包含資料集的檔案與用來儲存模型的檔案，以保存這些檔案的路徑：</span><span class="sxs-lookup"><span data-stu-id="8db7b-176">Go back to the *Program.cs* file and add three fields to hold the paths to the files with data sets and the file to save the model:</span></span>

* <span data-ttu-id="8db7b-177">`_datapath` 會針對具有用來定型模型之資料集的檔案，包含檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="8db7b-177">`_datapath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="8db7b-178">`_testdatapath` 會針對具有用來評估模型之資料集的檔案，包含檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="8db7b-178">`_testdatapath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="8db7b-179">`_modelpath` 會針對儲存定型模型的檔案，包含檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="8db7b-179">`_modelpath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="8db7b-180">將下列程式碼加入 `Main` 方法的緊鄰上方，以指定這些路徑：</span><span class="sxs-lookup"><span data-stu-id="8db7b-180">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="8db7b-181">若要將上述的程式碼進行編譯，請在 *Program.cs* 檔案頂端加入下列 `using` 指示詞：</span><span class="sxs-lookup"><span data-stu-id="8db7b-181">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsingsForPaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Using statements for path definitions")]

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="8db7b-182">建立學習管線</span><span class="sxs-lookup"><span data-stu-id="8db7b-182">Create a learning pipeline</span></span>

<span data-ttu-id="8db7b-183">在 *Program.cs* 檔案頂端加入下列額外的 `using` 指示詞：</span><span class="sxs-lookup"><span data-stu-id="8db7b-183">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="8db7b-184">在 `Main` 中，以下列程式碼取代 `Console.WriteLine("Hello World!")`：</span><span class="sxs-lookup"><span data-stu-id="8db7b-184">In `Main`, replace the `Console.WriteLine("Hello World!")` with the following code:</span></span>

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

<span data-ttu-id="8db7b-185">`Train` 方法會將模型定型。</span><span class="sxs-lookup"><span data-stu-id="8db7b-185">The `Train` method trains the model.</span></span> <span data-ttu-id="8db7b-186">請使用下列程式碼，在緊接著 `Main` 底下建立該方法：</span><span class="sxs-lookup"><span data-stu-id="8db7b-186">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

<span data-ttu-id="8db7b-187">學習管線會載入將模型定型所需的所有資料和演算法。</span><span class="sxs-lookup"><span data-stu-id="8db7b-187">The learning pipeline loads all of the data and algorithms necessary to train the model.</span></span> <span data-ttu-id="8db7b-188">將下列程式碼新增至 `Train` 方法：</span><span class="sxs-lookup"><span data-stu-id="8db7b-188">Add the following code into the `Train` method:</span></span>

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-data"></a><span data-ttu-id="8db7b-189">載入並轉換資料</span><span class="sxs-lookup"><span data-stu-id="8db7b-189">Load and transform data</span></span>

<span data-ttu-id="8db7b-190">學習管線執行的第一個步驟是從定型資料集載入資料。</span><span class="sxs-lookup"><span data-stu-id="8db7b-190">The first step that the learning pipeline performs is loading data from the training data set.</span></span> <span data-ttu-id="8db7b-191">在我們的案例中，定型資料集儲存在具有 `_datapath` 欄位所定義路徑的文字檔中。</span><span class="sxs-lookup"><span data-stu-id="8db7b-191">In our case, training data set is stored in the text file with a path defined by the `_datapath` field.</span></span> <span data-ttu-id="8db7b-192">這個檔案包含具有資料行名稱的標頭，因此載入資料時應該忽略第一個資料列。</span><span class="sxs-lookup"><span data-stu-id="8db7b-192">That file contains the header with the column names, so the first row should be ignored while loading data.</span></span> <span data-ttu-id="8db7b-193">檔案中的資料行是以逗號 (",") 分隔。</span><span class="sxs-lookup"><span data-stu-id="8db7b-193">Columns in the file are separated by the comma (",").</span></span> <span data-ttu-id="8db7b-194">將下列程式碼新增至 `Train` 方法：</span><span class="sxs-lookup"><span data-stu-id="8db7b-194">Add the following code into the `Train` method:</span></span>

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(useHeader: true, separator: ','));
```

<span data-ttu-id="8db7b-195">在接下來的步驟中，我們透過 `TaxiTrip` 類別中定義的名稱來參考資料行。</span><span class="sxs-lookup"><span data-stu-id="8db7b-195">In the next steps we refer to the columns by the names defined in the `TaxiTrip` class.</span></span>

<span data-ttu-id="8db7b-196">在定型和評估模型時，**Label** 資料行中的值被視為要預測的正確值。</span><span class="sxs-lookup"><span data-stu-id="8db7b-196">When the model is trained and evaluated, the values in the **Label** column are considered as correct values to be predicted.</span></span> <span data-ttu-id="8db7b-197">因為我們想要預測計程車行程車資，請將 `FareAmount` 資料行複製到 **Label** 資料行。</span><span class="sxs-lookup"><span data-stu-id="8db7b-197">As we want to predict the taxi trip fare, copy the `FareAmount` column into the **Label** column.</span></span> <span data-ttu-id="8db7b-198">若要這樣做，請使用 <xref:Microsoft.ML.Transforms.ColumnCopier>，並新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="8db7b-198">To do that, use <xref:Microsoft.ML.Transforms.ColumnCopier> and add the following code:</span></span>

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

<span data-ttu-id="8db7b-199">將模型定型的演算法需要**數值**特徵，因此您需要將類別目錄資料 (`VendorId`、`RateCode` 及 `PaymentType`) 值轉換成數字。</span><span class="sxs-lookup"><span data-stu-id="8db7b-199">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers.</span></span> <span data-ttu-id="8db7b-200">若要這樣做，請使用 <xref:Microsoft.ML.Transforms.CategoricalOneHotVectorizer>，這會將不同的數值索引鍵值指派給每個資料行中的不同值，並新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="8db7b-200">To do that, use <xref:Microsoft.ML.Transforms.CategoricalOneHotVectorizer>, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

<span data-ttu-id="8db7b-201">資料準備工作的最後一個步驟是使用 <xref:Microsoft.ML.Transforms.ColumnConcatenator> 轉換類別，將所有特徵資料行合併為 **Features** 資料行。</span><span class="sxs-lookup"><span data-stu-id="8db7b-201">The last step in data preparation combines all of the feature columns into the **Features** column using the <xref:Microsoft.ML.Transforms.ColumnConcatenator> transformation class.</span></span> <span data-ttu-id="8db7b-202">由於學習工具只會處理來自 **Features** 資料行的特徵，因此必須執行這個步驟。</span><span class="sxs-lookup"><span data-stu-id="8db7b-202">This step is necessary as a learner processes only features from the **Features** column.</span></span> <span data-ttu-id="8db7b-203">加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="8db7b-203">Add the following code:</span></span>

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

<span data-ttu-id="8db7b-204">請注意，未包含 `TripTime` 資料行，其對應於資料集檔案中的 `trip_time_in_secs` 資料行。</span><span class="sxs-lookup"><span data-stu-id="8db7b-204">Notice that the `TripTime` column, which corresponds to the `trip_time_in_secs` column in the data set file, isn't included.</span></span> <span data-ttu-id="8db7b-205">您已經判斷它並非有用的預測特徵。</span><span class="sxs-lookup"><span data-stu-id="8db7b-205">You already determined that it isn't a useful prediction feature.</span></span>

> [!NOTE]
> <span data-ttu-id="8db7b-206">您必須以上述指定的順序將這些步驟新增至管線中，才能成功執行。</span><span class="sxs-lookup"><span data-stu-id="8db7b-206">These steps must be added to the pipeline in the order specified above for successful execution.</span></span>

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="8db7b-207">選擇學習演算法</span><span class="sxs-lookup"><span data-stu-id="8db7b-207">Choose a learning algorithm</span></span>

<span data-ttu-id="8db7b-208">將資料新增至管線並將其轉換成正確的輸入格式之後，您需選取學習演算法 (**學習工具**)。</span><span class="sxs-lookup"><span data-stu-id="8db7b-208">After adding the data to the pipeline and transforming it into the correct input format, you select a learning algorithm (**learner**).</span></span> <span data-ttu-id="8db7b-209">學習工具會將模型定型。</span><span class="sxs-lookup"><span data-stu-id="8db7b-209">The learner trains the model.</span></span> <span data-ttu-id="8db7b-210">您為這個問題選擇了**迴歸工作**，因此您將新增 <xref:Microsoft.ML.Trainers.FastTreeRegressor> 學習工具，這是 ML.NET 所提供的其中一個迴歸學習工具。</span><span class="sxs-lookup"><span data-stu-id="8db7b-210">You chose a **regression task** for this problem, so you add a <xref:Microsoft.ML.Trainers.FastTreeRegressor> learner, which is one of the regression learners provided by ML.NET.</span></span>

<span data-ttu-id="8db7b-211"><xref:Microsoft.ML.Trainers.FastTreeRegressor> 學習工具會利用梯度提升。</span><span class="sxs-lookup"><span data-stu-id="8db7b-211"><xref:Microsoft.ML.Trainers.FastTreeRegressor> learner utilizes gradient boosting.</span></span> <span data-ttu-id="8db7b-212">梯度提升是一種適用於迴歸問題的機器學習技術。</span><span class="sxs-lookup"><span data-stu-id="8db7b-212">Gradient boosting is a machine learning technique for regression problems.</span></span> <span data-ttu-id="8db7b-213">它會以逐步方式建置每個迴歸樹。</span><span class="sxs-lookup"><span data-stu-id="8db7b-213">It builds each regression tree in a step-wise fashion.</span></span> <span data-ttu-id="8db7b-214">它會使用預先定義的損失函式來評估每個步驟中的誤差，然後在下一個步驟中為其進行修正。</span><span class="sxs-lookup"><span data-stu-id="8db7b-214">It uses a pre-defined loss function to measure the error in each step and correct for it in the next.</span></span> <span data-ttu-id="8db7b-215">結果會產生一個預測模型，這實際上就是較弱預測模型的總體。</span><span class="sxs-lookup"><span data-stu-id="8db7b-215">The result is a prediction model that is actually an ensemble of weaker prediction models.</span></span> <span data-ttu-id="8db7b-216">如需有關梯度提升的詳細資訊，請參閱[提升的決策樹迴歸](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="8db7b-216">For more information about gradient boosting, see [Boosted Decision Tree Regression](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span></span>

<span data-ttu-id="8db7b-217">將下列程式碼新增至 `Train` 方法中、上一個步驟中新增的資料處理程式碼之後：</span><span class="sxs-lookup"><span data-stu-id="8db7b-217">Add the following code into the `Train` method following the data processing code added in the previous step:</span></span>

```csharp
pipeline.Add(new FastTreeRegressor());
```

<span data-ttu-id="8db7b-218">您已將上述所有步驟新增至管線中作為個別的陳述式，但 C# 有個便利的集合初始化語法，可讓您更輕鬆地建立管線並將其初始化。</span><span class="sxs-lookup"><span data-stu-id="8db7b-218">You added all the preceding steps to the pipeline as individual statements, but C# has a handy collection initialization syntax that makes it simpler to create and initialize the pipeline.</span></span> <span data-ttu-id="8db7b-219">以下列程式碼取代您到目前為止已新增至 `Train` 方法中的程式碼：</span><span class="sxs-lookup"><span data-stu-id="8db7b-219">Replace the code you added so far to the `Train` method with the following code:</span></span>

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a><span data-ttu-id="8db7b-220">將模型定型</span><span class="sxs-lookup"><span data-stu-id="8db7b-220">Train the model</span></span>

<span data-ttu-id="8db7b-221">最後一個步驟是將模型定型。</span><span class="sxs-lookup"><span data-stu-id="8db7b-221">The final step is to train the model.</span></span> <span data-ttu-id="8db7b-222">到目前為止，尚未執行管線中的任何部分。</span><span class="sxs-lookup"><span data-stu-id="8db7b-222">Until this point, nothing in the pipeline has been executed.</span></span> <span data-ttu-id="8db7b-223">`pipeline.Train<TInput, TOutput>` 方法會產生模型，以接受 `TInput` 類型的執行個體，並輸出`TOutput` 類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="8db7b-223">The `pipeline.Train<TInput, TOutput>` method produces the model that takes in an instance of the `TInput` type and outputs an instance of the `TOutput` type.</span></span> <span data-ttu-id="8db7b-224">將下列程式碼新增至 `Train` 方法：</span><span class="sxs-lookup"><span data-stu-id="8db7b-224">Add the following code into the `Train` method:</span></span>

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

<span data-ttu-id="8db7b-225">就是這麼容易！</span><span class="sxs-lookup"><span data-stu-id="8db7b-225">And that's it!</span></span> <span data-ttu-id="8db7b-226">您已順利將可預測 NYC 中計程車車資的機器學習模型定型。</span><span class="sxs-lookup"><span data-stu-id="8db7b-226">You have successfully trained a machine learning model that can predict taxi fares in NYC.</span></span> <span data-ttu-id="8db7b-227">現在，讓我們來了解模型的準確程度，並了解如何使用它來預測計程車車資值。</span><span class="sxs-lookup"><span data-stu-id="8db7b-227">Now let's take a look to understand how accurate the model is and learn how to use it to predict taxi fare values.</span></span>

### <a name="save-the-model"></a><span data-ttu-id="8db7b-228">儲存模型</span><span class="sxs-lookup"><span data-stu-id="8db7b-228">Save the model</span></span>

<span data-ttu-id="8db7b-229">在您前進到下一個步驟之前，請先在 `Train` 方法的結尾新增下列程式碼，將模型儲存成 .zip 檔案：</span><span class="sxs-lookup"><span data-stu-id="8db7b-229">Before you go onto the next step, save the model to a .zip file by adding the following code at the end of the `Train` method:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

<span data-ttu-id="8db7b-230">將 `await` 陳述式新增至 `model.WriteAsync` 呼叫時，意謂著必須將 `Train` 方法變更為會傳回 Task 的非同步方法。</span><span class="sxs-lookup"><span data-stu-id="8db7b-230">Adding the `await` statement to the `model.WriteAsync` call means that the `Train` method must be changed to an async method that returns a task.</span></span> <span data-ttu-id="8db7b-231">請修改 `Train`，如以下範例所示：</span><span class="sxs-lookup"><span data-stu-id="8db7b-231">Modify the signature of `Train` as shown in the following code:</span></span>

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

<span data-ttu-id="8db7b-232">變更 `Train` 方法的傳回類型時，意謂著您必須將 `await` 新增至會呼叫 `Main` 方法中 `Train` 的程式碼，如以下程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="8db7b-232">Changing the return type of the `Train` method means you have to add an `await` to the code that calls `Train` in the `Main` method as shown in the following code:</span></span>

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

<span data-ttu-id="8db7b-233">在 `Main` 方法中使用 `await` 時，意謂著 `Main` 方法必須包含 `async` 修飾詞並傳回 `Task`：</span><span class="sxs-lookup"><span data-stu-id="8db7b-233">Using `await` in the `Main` method means the `Main` method must have the `async` modifier and return a `Task`:</span></span>

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

<span data-ttu-id="8db7b-234">您還必須在檔案頂端新增下列 `using` 指示詞：</span><span class="sxs-lookup"><span data-stu-id="8db7b-234">You also need to add the following `using` directive at the top of the file:</span></span>

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

<span data-ttu-id="8db7b-235">由於 `async Main` 方法是 C# 7.1 中的新增功能，而專案的預設語言版本是 C# 7.0，因此您必須將語言版本變更為 C# 7.1 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="8db7b-235">Because the `async Main` method is the feature added in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span> <span data-ttu-id="8db7b-236">若要這樣做，請以滑鼠右鍵按一下 [方案總管] 中的專案節點，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="8db7b-236">To do that, right-click the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="8db7b-237">選取 [建置] 索引標籤並選取 [進階] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="8db7b-237">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="8db7b-238">從下拉式清單中，選取 [C# 7.1] (或更新版本)。</span><span class="sxs-lookup"><span data-stu-id="8db7b-238">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="8db7b-239">選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="8db7b-239">Select the **OK** button.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="8db7b-240">評估模型</span><span class="sxs-lookup"><span data-stu-id="8db7b-240">Evaluate the model</span></span>

<span data-ttu-id="8db7b-241">評估係指檢查模型預測標籤值之良好程度的程序。</span><span class="sxs-lookup"><span data-stu-id="8db7b-241">Evaluation is the process of checking how well the model predicts label values.</span></span> <span data-ttu-id="8db7b-242">對模型來說，能夠針對其定型時未使用的資料做出良好的預測是相當重要的。</span><span class="sxs-lookup"><span data-stu-id="8db7b-242">It's important that the model makes good predictions on data that was not used to train the model.</span></span> <span data-ttu-id="8db7b-243">若要達到此目的，其中一個做法是將資料分割成定型和測試資料集，就像在本教學課程中所做的一樣。</span><span class="sxs-lookup"><span data-stu-id="8db7b-243">One way to do this is to split the data into train and test data sets, as it's done in this tutorial.</span></span> <span data-ttu-id="8db7b-244">既然您已依據定型資料將模型定型，現在即可查看模型對測試資料的表現。</span><span class="sxs-lookup"><span data-stu-id="8db7b-244">Now that you've trained the model on the train data, you can see how well it performs on the test data.</span></span>

<span data-ttu-id="8db7b-245">返回 `Main` 方法，然後在 `Train` 方法的呼叫底下，新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="8db7b-245">Go back to the `Main` method and add the following code beneath the call to the `Train`method:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

<span data-ttu-id="8db7b-246">`Evaluate` 方法會評估模型。</span><span class="sxs-lookup"><span data-stu-id="8db7b-246">The `Evaluate` method evaluates the model.</span></span> <span data-ttu-id="8db7b-247">若要建立該方法，請在 `Train` 方法底下新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="8db7b-247">To create that method, add the following code below the `Train` method:</span></span>

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

<span data-ttu-id="8db7b-248">將下列程式碼新增至 `Evaluate` 方法，來設定測試資料的載入：</span><span class="sxs-lookup"><span data-stu-id="8db7b-248">Add the following code into the `Evaluate` method to setup loading of the test data:</span></span>

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

<span data-ttu-id="8db7b-249">新增下列程式碼來評估模型並產生評估計量：</span><span class="sxs-lookup"><span data-stu-id="8db7b-249">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

<span data-ttu-id="8db7b-250">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) 是迴歸模型的評估計量之一。</span><span class="sxs-lookup"><span data-stu-id="8db7b-250">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="8db7b-251">此計量值越低，模型就越好。</span><span class="sxs-lookup"><span data-stu-id="8db7b-251">The lower it is, the better the model is.</span></span> <span data-ttu-id="8db7b-252">將下列程式碼新增至 `Evaluate` 方法，以顯示 RMS 值：</span><span class="sxs-lookup"><span data-stu-id="8db7b-252">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

<span data-ttu-id="8db7b-253">[RSquared](../resources/glossary.md#coefficient-of-determination) 是迴歸模型的另一個評估計量。</span><span class="sxs-lookup"><span data-stu-id="8db7b-253">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="8db7b-254">RSquared 接受介於 0 和 1 之間的值。</span><span class="sxs-lookup"><span data-stu-id="8db7b-254">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="8db7b-255">其值越接近 1，模型就越好。</span><span class="sxs-lookup"><span data-stu-id="8db7b-255">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="8db7b-256">將下列程式碼新增至 `Evaluate` 方法，以顯示 RSquared 值：</span><span class="sxs-lookup"><span data-stu-id="8db7b-256">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="8db7b-257">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="8db7b-257">Use the model for predictions</span></span>

<span data-ttu-id="8db7b-258">接著，建立一個類別來裝載可用來確定模型是否正確運作的測試案例：</span><span class="sxs-lookup"><span data-stu-id="8db7b-258">Next, create a class to house test scenarios that you can use to make sure the model is working correctly:</span></span>

1. <span data-ttu-id="8db7b-259">在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="8db7b-259">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="8db7b-260">在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *TestTrips.cs*。</span><span class="sxs-lookup"><span data-stu-id="8db7b-260">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestTrips.cs*.</span></span> <span data-ttu-id="8db7b-261">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="8db7b-261">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="8db7b-262">將類別修改成靜態，如以下範例所示：</span><span class="sxs-lookup"><span data-stu-id="8db7b-262">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

<span data-ttu-id="8db7b-263">本教學課程會使用此類別內的一個測試行程。</span><span class="sxs-lookup"><span data-stu-id="8db7b-263">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="8db7b-264">您可以稍後新增其他案例來對此方法進行實驗。</span><span class="sxs-lookup"><span data-stu-id="8db7b-264">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="8db7b-265">將下列程式碼新增至 `TestTrips` 類別：</span><span class="sxs-lookup"><span data-stu-id="8db7b-265">Add the following code into the `TestTrips` class:</span></span>

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

<span data-ttu-id="8db7b-266">這個行程的實際車資是 29.5。</span><span class="sxs-lookup"><span data-stu-id="8db7b-266">This trip's actual fare is 29.5.</span></span> <span data-ttu-id="8db7b-267">請使用 0 作為預留位置，因為此模型將會預測車資。</span><span class="sxs-lookup"><span data-stu-id="8db7b-267">Use 0 as a placeholder, as the model will predict the fare.</span></span>

<span data-ttu-id="8db7b-268">若要預測指定行程的車資，請返回 *Program.cs* 檔案，然後將下列程式碼新增至 `Main` 方法：</span><span class="sxs-lookup"><span data-stu-id="8db7b-268">To predict the fare of the specified trip, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

<span data-ttu-id="8db7b-269">執行程式以查看您測試案例的預測計程車車資。</span><span class="sxs-lookup"><span data-stu-id="8db7b-269">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="8db7b-270">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="8db7b-270">Congratulations!</span></span> <span data-ttu-id="8db7b-271">您現在已成功建置可預測計程車車資的機器學習模型、評估了它的準確率，並且也使用它進行了預測。</span><span class="sxs-lookup"><span data-stu-id="8db7b-271">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="8db7b-272">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="8db7b-272">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8db7b-273">後續步驟</span><span class="sxs-lookup"><span data-stu-id="8db7b-273">Next steps</span></span>

<span data-ttu-id="8db7b-274">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="8db7b-274">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="8db7b-275">了解問題</span><span class="sxs-lookup"><span data-stu-id="8db7b-275">Understand the problem</span></span>
> * <span data-ttu-id="8db7b-276">選取適當的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="8db7b-276">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="8db7b-277">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="8db7b-277">Prepare and understand the data</span></span>
> * <span data-ttu-id="8db7b-278">建立學習管線</span><span class="sxs-lookup"><span data-stu-id="8db7b-278">Create a learning pipeline</span></span>
> * <span data-ttu-id="8db7b-279">載入並轉換資料</span><span class="sxs-lookup"><span data-stu-id="8db7b-279">Load and transform the data</span></span>
> * <span data-ttu-id="8db7b-280">選擇學習演算法</span><span class="sxs-lookup"><span data-stu-id="8db7b-280">Choose a learning algorithm</span></span>
> * <span data-ttu-id="8db7b-281">將模型定型</span><span class="sxs-lookup"><span data-stu-id="8db7b-281">Train the model</span></span>
> * <span data-ttu-id="8db7b-282">評估模型</span><span class="sxs-lookup"><span data-stu-id="8db7b-282">Evaluate the model</span></span>
> * <span data-ttu-id="8db7b-283">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="8db7b-283">Use the model for predictions</span></span>

<span data-ttu-id="8db7b-284">請查看我們的 GitHub 存放庫來繼續學習及尋找更多範例。</span><span class="sxs-lookup"><span data-stu-id="8db7b-284">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="8db7b-285">dotnet/machinelearning GitHub 存放庫</span><span class="sxs-lookup"><span data-stu-id="8db7b-285">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
