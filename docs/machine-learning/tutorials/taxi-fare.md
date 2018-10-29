---
title: 使用 ML.NET 來預測紐約計程車車資 (迴歸)
description: 了解如何在迴歸案例中使用 ML.NET。
author: aditidugar
ms.author: johalex
ms.date: 07/02/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: bfae97d65ec192e9289841c82d84807b4937b09a
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183811"
---
# <a name="tutorial-use-mlnet-to-predict-new-york-taxi-fares-regression"></a><span data-ttu-id="e7628-103">教學課程：使用 ML.NET 來預測紐約計程車車資 (迴歸)</span><span class="sxs-lookup"><span data-stu-id="e7628-103">Tutorial: Use ML.NET to predict New York taxi fares (regression)</span></span>

> [!NOTE]
> <span data-ttu-id="e7628-104">本主題涉及 ML.NET，此功能目前為公開預覽版，因此内容可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="e7628-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="e7628-105">如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) \(英文)。</span><span class="sxs-lookup"><span data-stu-id="e7628-105">For more information, see the [ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="e7628-106">本教學課程說明如何使用 ML.NET 來建置用於預測紐約市計程車車資的 [迴歸模型](../resources/glossary.md#regression)。</span><span class="sxs-lookup"><span data-stu-id="e7628-106">This tutorial illustrates how to use ML.NET to build a [regression model](../resources/glossary.md#regression) for predicting New York City taxi fares.</span></span>

<span data-ttu-id="e7628-107">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="e7628-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="e7628-108">了解問題</span><span class="sxs-lookup"><span data-stu-id="e7628-108">Understand the problem</span></span>
> * <span data-ttu-id="e7628-109">選取適當的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="e7628-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="e7628-110">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="e7628-110">Prepare and understand the data</span></span>
> * <span data-ttu-id="e7628-111">建立學習管線</span><span class="sxs-lookup"><span data-stu-id="e7628-111">Create a learning pipeline</span></span>
> * <span data-ttu-id="e7628-112">載入並轉換資料</span><span class="sxs-lookup"><span data-stu-id="e7628-112">Load and transform the data</span></span>
> * <span data-ttu-id="e7628-113">選擇學習演算法</span><span class="sxs-lookup"><span data-stu-id="e7628-113">Choose a learning algorithm</span></span>
> * <span data-ttu-id="e7628-114">將模型定型</span><span class="sxs-lookup"><span data-stu-id="e7628-114">Train the model</span></span>
> * <span data-ttu-id="e7628-115">評估模型</span><span class="sxs-lookup"><span data-stu-id="e7628-115">Evaluate the model</span></span>
> * <span data-ttu-id="e7628-116">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="e7628-116">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e7628-117">必要條件</span><span class="sxs-lookup"><span data-stu-id="e7628-117">Prerequisites</span></span>

* <span data-ttu-id="e7628-118">已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)。</span><span class="sxs-lookup"><span data-stu-id="e7628-118">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="e7628-119">了解問題</span><span class="sxs-lookup"><span data-stu-id="e7628-119">Understand the problem</span></span>

<span data-ttu-id="e7628-120">此問題是關於預測紐約市計程車的車資。</span><span class="sxs-lookup"><span data-stu-id="e7628-120">This problem is about predicting the fare of a taxi trip in New York City.</span></span> <span data-ttu-id="e7628-121">乍看之下，這可能看似單純取決於行程遠近。</span><span class="sxs-lookup"><span data-stu-id="e7628-121">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="e7628-122">不過，紐約計程車廠商會針對其他因素 (例如額外的乘客，或使用信用卡而非現金付費) 收取不同的金額。</span><span class="sxs-lookup"><span data-stu-id="e7628-122">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="e7628-123">選取適當的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="e7628-123">Select the appropriate machine learning task</span></span>

<span data-ttu-id="e7628-124">您希望根據資料集當中的其他因素來預測價格值，這是一個實際值。</span><span class="sxs-lookup"><span data-stu-id="e7628-124">You want to predict the price value, which is a real value, based on the other factors in the data set.</span></span> <span data-ttu-id="e7628-125">為了這麼做，您選擇[迴歸](../resources/glossary.md#regression)機器學習工作。</span><span class="sxs-lookup"><span data-stu-id="e7628-125">To do that you choose a [regression](../resources/glossary.md#regression) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="e7628-126">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="e7628-126">Create a console application</span></span>

1. <span data-ttu-id="e7628-127">開啟 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="e7628-127">Open Visual Studio 2017.</span></span> <span data-ttu-id="e7628-128">從功能表列中選取 [檔案]  >  [新增]  >  [專案]。</span><span class="sxs-lookup"><span data-stu-id="e7628-128">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="e7628-129">在 [新增專案] 對話方塊中，選取 [Visual C#] 節點，然後選取 [.NET Core] 節點。</span><span class="sxs-lookup"><span data-stu-id="e7628-129">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="e7628-130">然後選取 [主控台應用程式 (.NET Core)] 專案範本。</span><span class="sxs-lookup"><span data-stu-id="e7628-130">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="e7628-131">在 [名稱] 文字方塊中，輸入 "TaxiFarePrediction"，然後選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e7628-131">In the **Name** text box, type "TaxiFarePrediction" and then select the **OK** button.</span></span>

1. <span data-ttu-id="e7628-132">在您的專案中建立一個名為 *Data* 的目錄以儲存資料集和模型檔案：</span><span class="sxs-lookup"><span data-stu-id="e7628-132">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="e7628-133">在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取 [新增] > [新增資料夾]。</span><span class="sxs-lookup"><span data-stu-id="e7628-133">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="e7628-134">輸入 "Data"，然後按 Enter。</span><span class="sxs-lookup"><span data-stu-id="e7628-134">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="e7628-135">安裝 **Microsoft.ML** NuGet 套件：</span><span class="sxs-lookup"><span data-stu-id="e7628-135">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="e7628-136">在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="e7628-136">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="e7628-137">選擇 "nuget.org" 作為 [套件來源]，選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e7628-137">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="e7628-138">在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。</span><span class="sxs-lookup"><span data-stu-id="e7628-138">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="e7628-139">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="e7628-139">Prepare and understand the data</span></span>

1. <span data-ttu-id="e7628-140">下載 [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) 和 [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) 資料集，並將它們儲存至您在上一個步驟所建立的 *Data* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="e7628-140">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="e7628-141">我們可以使用這些資料集將機器學習模型定型，然後評估模型的準確程度。</span><span class="sxs-lookup"><span data-stu-id="e7628-141">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="e7628-142">這些資料集原先來自 [NYC TLC Taxi Trip 資料集](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)。</span><span class="sxs-lookup"><span data-stu-id="e7628-142">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

1. <span data-ttu-id="e7628-143">在 [方案總管] 中，以滑鼠右鍵按一下每個 \*.csv 檔案，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="e7628-143">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="e7628-144">在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。</span><span class="sxs-lookup"><span data-stu-id="e7628-144">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

1. <span data-ttu-id="e7628-145">開啟 **taxi-fare-train.csv** 資料集，然後查看第一個資料列中的資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="e7628-145">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="e7628-146">請查看每個資料行。</span><span class="sxs-lookup"><span data-stu-id="e7628-146">Take a look at each of the columns.</span></span> <span data-ttu-id="e7628-147">了解資料，並決定哪些資料行是 **features**，以及哪一個資料行是 **label**。</span><span class="sxs-lookup"><span data-stu-id="e7628-147">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="e7628-148">**label** 是您要預測之資料行的識別碼。</span><span class="sxs-lookup"><span data-stu-id="e7628-148">The **label** is the identifier of the column you want to predict.</span></span> <span data-ttu-id="e7628-149">所識別的**特徵**會用來預測標籤。</span><span class="sxs-lookup"><span data-stu-id="e7628-149">The identified **features** are used to predict the label.</span></span>

<span data-ttu-id="e7628-150">提供的資料集包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="e7628-150">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="e7628-151">**vendor_id：** 計程車廠商的識別碼是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="e7628-151">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="e7628-152">**rate_code：** 計程車行程的費率類型是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="e7628-152">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="e7628-153">**passenger_count：** 行程的乘客數目是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="e7628-153">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="e7628-154">**trip_time_in_secs：** 行程所花費的時間長度。</span><span class="sxs-lookup"><span data-stu-id="e7628-154">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="e7628-155">您想要在行程結束之前預測行程的車資。</span><span class="sxs-lookup"><span data-stu-id="e7628-155">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="e7628-156">那時，您並不知道行程需要多長的時間。</span><span class="sxs-lookup"><span data-stu-id="e7628-156">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="e7628-157">因此，行程時間不是一項特徵，您將從模型中排除這個資料行。</span><span class="sxs-lookup"><span data-stu-id="e7628-157">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="e7628-158">**trip_distance：** 行程的距離是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="e7628-158">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="e7628-159">**payment_type：** 付款方式 (現金或信用卡) 是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="e7628-159">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="e7628-160">**fare_amount：** 計程車車資總計是標籤。</span><span class="sxs-lookup"><span data-stu-id="e7628-160">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="e7628-161">建立資料類別</span><span class="sxs-lookup"><span data-stu-id="e7628-161">Create data classes</span></span>

<span data-ttu-id="e7628-162">為輸入資料和預測建立類別：</span><span class="sxs-lookup"><span data-stu-id="e7628-162">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="e7628-163">在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="e7628-163">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="e7628-164">在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *TaxiTrip.cs*。</span><span class="sxs-lookup"><span data-stu-id="e7628-164">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="e7628-165">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e7628-165">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="e7628-166">將下列的 `using` 指示詞加入新檔案：</span><span class="sxs-lookup"><span data-stu-id="e7628-166">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="e7628-167">移除現有的類別定義，然後將下列程式碼 (具有 `TaxiTrip` 和 `TaxiTripFarePrediction` 這兩個類別) 新增至 *TaxiTrip.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="e7628-167">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="e7628-168">`TaxiTrip` 是輸入資料類別，並含有每個資料集資料行的定義。</span><span class="sxs-lookup"><span data-stu-id="e7628-168">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="e7628-169">請使用 [Column](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) 屬性來指定資料集中來源資料行的索引。</span><span class="sxs-lookup"><span data-stu-id="e7628-169">Use the [Column](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="e7628-170">`TaxiTripFarePrediction` 類別代表預測的結果。</span><span class="sxs-lookup"><span data-stu-id="e7628-170">The `TaxiTripFarePrediction` class represents predicted results.</span></span> <span data-ttu-id="e7628-171">包含一個套用 `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) 屬性的單一浮點數欄位 `FareAmount`。</span><span class="sxs-lookup"><span data-stu-id="e7628-171">It has a single float field, `FareAmount`, with a `Score` [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) attribute applied.</span></span> <span data-ttu-id="e7628-172">如果是迴歸工作，則**分數**資料行包含預測的標籤值。</span><span class="sxs-lookup"><span data-stu-id="e7628-172">In case of the regression task the **Score** column contains predicted label values.</span></span>

> [!NOTE]
> <span data-ttu-id="e7628-173">使用 `float` 型別表示輸入和預測資料類別中的浮點值。</span><span class="sxs-lookup"><span data-stu-id="e7628-173">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="e7628-174">定義資料和模型路徑</span><span class="sxs-lookup"><span data-stu-id="e7628-174">Define data and model paths</span></span>

<span data-ttu-id="e7628-175">請返回 *Program.cs* 檔案，並新增三個欄位，針對包含資料集的檔案與用來儲存模型的檔案，以保存這些檔案的路徑：</span><span class="sxs-lookup"><span data-stu-id="e7628-175">Go back to the *Program.cs* file and add three fields to hold the paths to the files with data sets and the file to save the model:</span></span>

* <span data-ttu-id="e7628-176">`_datapath` 會針對具有用來定型模型之資料集的檔案，包含檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="e7628-176">`_datapath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="e7628-177">`_testdatapath` 會針對具有用來評估模型之資料集的檔案，包含檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="e7628-177">`_testdatapath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="e7628-178">`_modelpath` 會針對儲存定型模型的檔案，包含檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="e7628-178">`_modelpath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="e7628-179">將下列程式碼加入 `Main` 方法的緊鄰上方，以指定這些路徑：</span><span class="sxs-lookup"><span data-stu-id="e7628-179">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="e7628-180">若要將上述的程式碼進行編譯，請在 *Program.cs* 檔案頂端加入下列 `using` 指示詞：</span><span class="sxs-lookup"><span data-stu-id="e7628-180">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsingsForPaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Using statements for path definitions")]

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="e7628-181">建立學習管線</span><span class="sxs-lookup"><span data-stu-id="e7628-181">Create a learning pipeline</span></span>

<span data-ttu-id="e7628-182">在 *Program.cs* 檔案頂端加入下列額外的 `using` 指示詞：</span><span class="sxs-lookup"><span data-stu-id="e7628-182">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="e7628-183">在 `Main` 方法中，以下列程式碼取代 `Console.WriteLine("Hello World!")`：</span><span class="sxs-lookup"><span data-stu-id="e7628-183">In the `Main` method, replace the `Console.WriteLine("Hello World!")` with the following code:</span></span>

```csharp
PredictionModel<TaxiTrip, TaxiTripFarePrediction> model = Train();
```

<span data-ttu-id="e7628-184">`Train` 方法會將模型定型。</span><span class="sxs-lookup"><span data-stu-id="e7628-184">The `Train` method trains the model.</span></span> <span data-ttu-id="e7628-185">請使用下列程式碼，在緊接著 `Main` 底下建立該方法：</span><span class="sxs-lookup"><span data-stu-id="e7628-185">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static PredictionModel<TaxiTrip, TaxiTripFarePrediction> Train()
{

}
```

<span data-ttu-id="e7628-186">學習管線會載入將模型定型所需的所有資料和演算法。</span><span class="sxs-lookup"><span data-stu-id="e7628-186">The learning pipeline loads all of the data and algorithms necessary to train the model.</span></span> <span data-ttu-id="e7628-187">將下列程式碼新增至 `Train` 方法：</span><span class="sxs-lookup"><span data-stu-id="e7628-187">Add the following code into the `Train` method:</span></span>

```csharp
var pipeline = new LearningPipeline();
```

## <a name="load-and-transform-data"></a><span data-ttu-id="e7628-188">載入並轉換資料</span><span class="sxs-lookup"><span data-stu-id="e7628-188">Load and transform data</span></span>

<span data-ttu-id="e7628-189">要執行的第一個步驟是從訓練資料集載入資料。</span><span class="sxs-lookup"><span data-stu-id="e7628-189">The first step to perform is to load data from the training data set.</span></span> <span data-ttu-id="e7628-190">在我們的案例中，定型資料集儲存在具有 `_datapath` 欄位所定義路徑的文字檔中。</span><span class="sxs-lookup"><span data-stu-id="e7628-190">In our case, training data set is stored in the text file with a path defined by the `_datapath` field.</span></span> <span data-ttu-id="e7628-191">這個檔案具有包含資料行名稱的標頭，因此載入資料時應該忽略第一個資料列。</span><span class="sxs-lookup"><span data-stu-id="e7628-191">That file has the header with the column names, so the first row should be ignored while loading data.</span></span> <span data-ttu-id="e7628-192">檔案中的資料行是以逗號 (",") 分隔。</span><span class="sxs-lookup"><span data-stu-id="e7628-192">Columns in the file are separated by the comma (",").</span></span> <span data-ttu-id="e7628-193">將下列程式碼新增至 `Train` 方法：</span><span class="sxs-lookup"><span data-stu-id="e7628-193">Add the following code into the `Train` method:</span></span>

```csharp
pipeline.Add(new TextLoader(_datapath).CreateFrom<TaxiTrip>(useHeader: true, separator: ','));
```

<span data-ttu-id="e7628-194">在接下來的步驟中，我們透過 `TaxiTrip` 類別中定義的名稱來參考資料行。</span><span class="sxs-lookup"><span data-stu-id="e7628-194">In the next steps we refer to the columns by the names defined in the `TaxiTrip` class.</span></span>

<span data-ttu-id="e7628-195">根據預設，在定型和評估模型時，**Label** 資料行中的值會視為要預測的正確值。</span><span class="sxs-lookup"><span data-stu-id="e7628-195">When the model is trained and evaluated, by default, the values in the **Label** column are considered as correct values to be predicted.</span></span> <span data-ttu-id="e7628-196">因為我們想要預測計程車行程車資，請將 `FareAmount` 資料行複製到 **Label** 資料行。</span><span class="sxs-lookup"><span data-stu-id="e7628-196">As we want to predict the taxi trip fare, copy the `FareAmount` column into the **Label** column.</span></span> <span data-ttu-id="e7628-197">若要這樣做，請使用 <xref:Microsoft.ML.Legacy.Transforms.ColumnCopier>，並新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="e7628-197">To do that, use <xref:Microsoft.ML.Legacy.Transforms.ColumnCopier> and add the following code:</span></span>

```csharp
pipeline.Add(new ColumnCopier(("FareAmount", "Label")));
```

<span data-ttu-id="e7628-198">將模型定型的演算法需要**數值**特徵，因此您需要將類別目錄資料 (`VendorId`、`RateCode` 及 `PaymentType`) 值轉換成數字。</span><span class="sxs-lookup"><span data-stu-id="e7628-198">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers.</span></span> <span data-ttu-id="e7628-199">若要這樣做，請使用 <xref:Microsoft.ML.Legacy.Transforms.CategoricalOneHotVectorizer>，這會將不同的數值索引鍵值指派給每個資料行中的不同值，並新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="e7628-199">To do that, use <xref:Microsoft.ML.Legacy.Transforms.CategoricalOneHotVectorizer>, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

```csharp
pipeline.Add(new CategoricalOneHotVectorizer("VendorId",
                                             "RateCode",
                                             "PaymentType"));
```

<span data-ttu-id="e7628-200">資料準備工作的最後一個步驟是使用 <xref:Microsoft.ML.Legacy.Transforms.ColumnConcatenator> 轉換類別，將所有特徵資料行合併為 **Features** 資料行。</span><span class="sxs-lookup"><span data-stu-id="e7628-200">The last step in data preparation combines all of the feature columns into the **Features** column using the <xref:Microsoft.ML.Legacy.Transforms.ColumnConcatenator> transformation class.</span></span> <span data-ttu-id="e7628-201">根據預設，學習演算法只會處理來自 **Features** 資料行的特徵。</span><span class="sxs-lookup"><span data-stu-id="e7628-201">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="e7628-202">加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="e7628-202">Add the following code:</span></span>

```csharp
pipeline.Add(new ColumnConcatenator("Features",
                                    "VendorId",
                                    "RateCode",
                                    "PassengerCount",
                                    "TripDistance",
                                    "PaymentType"));
```

<span data-ttu-id="e7628-203">請注意，未包含 `TripTime` 資料行，其對應於資料集檔案中的 `trip_time_in_secs` 資料行。</span><span class="sxs-lookup"><span data-stu-id="e7628-203">Notice that the `TripTime` column, which corresponds to the `trip_time_in_secs` column in the data set file, isn't included.</span></span> <span data-ttu-id="e7628-204">您已經判斷它並非有用的預測特徵。</span><span class="sxs-lookup"><span data-stu-id="e7628-204">You already determined that it isn't a useful prediction feature.</span></span>

> [!NOTE]
> <span data-ttu-id="e7628-205">您必須以上述指定的順序將這些步驟新增至管線中，才能成功執行。</span><span class="sxs-lookup"><span data-stu-id="e7628-205">These steps must be added to the pipeline in the order specified above for successful execution.</span></span>

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="e7628-206">選擇學習演算法</span><span class="sxs-lookup"><span data-stu-id="e7628-206">Choose a learning algorithm</span></span>

<span data-ttu-id="e7628-207">將資料新增至管線並將其轉換成正確的輸入格式之後，您需選取學習演算法 (**學習工具**)。</span><span class="sxs-lookup"><span data-stu-id="e7628-207">After adding the data to the pipeline and transforming it into the correct input format, you select a learning algorithm (**learner**).</span></span> <span data-ttu-id="e7628-208">學習工具會將模型定型。</span><span class="sxs-lookup"><span data-stu-id="e7628-208">The learner trains the model.</span></span> <span data-ttu-id="e7628-209">您為這個問題選擇了**迴歸工作**，因此您將使用 <xref:Microsoft.ML.Legacy.Trainers.FastTreeRegressor> 學習工具，這是 ML.NET 所提供的其中一個迴歸學習工具。</span><span class="sxs-lookup"><span data-stu-id="e7628-209">You chose a **regression** task for this problem, so you use a <xref:Microsoft.ML.Legacy.Trainers.FastTreeRegressor> learner, which is one of the regression learners provided by ML.NET.</span></span>

<span data-ttu-id="e7628-210"><xref:Microsoft.ML.Legacy.Trainers.FastTreeRegressor> 學習工具會利用梯度提升。</span><span class="sxs-lookup"><span data-stu-id="e7628-210"><xref:Microsoft.ML.Legacy.Trainers.FastTreeRegressor> learner utilizes gradient boosting.</span></span> <span data-ttu-id="e7628-211">梯度提升是一種適用於迴歸問題的機器學習技術。</span><span class="sxs-lookup"><span data-stu-id="e7628-211">Gradient boosting is a machine learning technique for regression problems.</span></span> <span data-ttu-id="e7628-212">它會以逐步方式建置每個迴歸樹。</span><span class="sxs-lookup"><span data-stu-id="e7628-212">It builds each regression tree in a step-wise fashion.</span></span> <span data-ttu-id="e7628-213">它會使用預先定義的損失函式來評估每個步驟中的誤差，然後在下一個步驟中為其進行修正。</span><span class="sxs-lookup"><span data-stu-id="e7628-213">It uses a pre-defined loss function to measure the error in each step and correct for it in the next.</span></span> <span data-ttu-id="e7628-214">結果會產生一個預測模型，這實際上就是較弱預測模型的總體。</span><span class="sxs-lookup"><span data-stu-id="e7628-214">The result is a prediction model that is actually an ensemble of weaker prediction models.</span></span> <span data-ttu-id="e7628-215">如需有關梯度提升的詳細資訊，請參閱[提升的決策樹迴歸](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="e7628-215">For more information about gradient boosting, see [Boosted Decision Tree Regression](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span></span>

<span data-ttu-id="e7628-216">將下列程式碼新增至 `Train` 方法中、上一個步驟中新增的資料處理程式碼之後：</span><span class="sxs-lookup"><span data-stu-id="e7628-216">Add the following code into the `Train` method following the data processing code added in the previous step:</span></span>

```csharp
pipeline.Add(new FastTreeRegressor());
```

<span data-ttu-id="e7628-217">您已將上述所有步驟新增至管線中作為個別的陳述式，但 C# 有個便利的集合初始化語法，可讓您更輕鬆地建立管線並將其初始化。</span><span class="sxs-lookup"><span data-stu-id="e7628-217">You added all the preceding steps to the pipeline as individual statements, but C# has a handy collection initialization syntax that makes it simpler to create and initialize the pipeline.</span></span> <span data-ttu-id="e7628-218">以下列程式碼取代您到目前為止已新增至 `Train` 方法中的程式碼：</span><span class="sxs-lookup"><span data-stu-id="e7628-218">Replace the code you added so far to the `Train` method with the following code:</span></span>

[!code-csharp[CreatePipeline](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create and initialize the learning pipeline")]

## <a name="train-the-model"></a><span data-ttu-id="e7628-219">將模型定型</span><span class="sxs-lookup"><span data-stu-id="e7628-219">Train the model</span></span>

<span data-ttu-id="e7628-220">最後一個步驟是將模型定型。</span><span class="sxs-lookup"><span data-stu-id="e7628-220">The final step is to train the model.</span></span> <span data-ttu-id="e7628-221">到目前為止，尚未執行管線中的任何部分。</span><span class="sxs-lookup"><span data-stu-id="e7628-221">Until this point, nothing in the pipeline has been executed.</span></span> <span data-ttu-id="e7628-222">`pipeline.Train<TInput, TOutput>` 方法會產生模型，以接受 `TInput` 類型的執行個體，並輸出`TOutput` 類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e7628-222">The `pipeline.Train<TInput, TOutput>` method produces the model that takes in an instance of the `TInput` type and outputs an instance of the `TOutput` type.</span></span> <span data-ttu-id="e7628-223">將下列程式碼新增至 `Train` 方法：</span><span class="sxs-lookup"><span data-stu-id="e7628-223">Add the following code into the `Train` method:</span></span>

[!code-csharp[TrainMOdel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#4 "Train your model")]

<span data-ttu-id="e7628-224">就是這麼容易！</span><span class="sxs-lookup"><span data-stu-id="e7628-224">And that's it!</span></span> <span data-ttu-id="e7628-225">您已順利將可預測 NYC 中計程車車資的機器學習模型定型。</span><span class="sxs-lookup"><span data-stu-id="e7628-225">You have successfully trained a machine learning model that can predict taxi fares in NYC.</span></span> <span data-ttu-id="e7628-226">現在，讓我們來了解模型的準確程度，並了解如何使用它來預測計程車車資值。</span><span class="sxs-lookup"><span data-stu-id="e7628-226">Now let's take a look to understand how accurate the model is and learn how to use it to predict taxi fare values.</span></span>

### <a name="save-the-model"></a><span data-ttu-id="e7628-227">儲存模型</span><span class="sxs-lookup"><span data-stu-id="e7628-227">Save the model</span></span>

<span data-ttu-id="e7628-228">此時，您已有一個可整合至任何現有或新 .NET 應用程式的模型。</span><span class="sxs-lookup"><span data-stu-id="e7628-228">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="e7628-229">若要將模型儲存至 .zip 檔案，請在 `Train` 方法的結尾新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="e7628-229">To save the model to a .zip file, add the following code at the end of the `Train` method:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Save the model asynchronously and return the model")]

<span data-ttu-id="e7628-230">將 `await` 陳述式新增至 `model.WriteAsync` 呼叫時，意謂著必須將 `Train` 方法變更為會傳回 Task 的非同步方法。</span><span class="sxs-lookup"><span data-stu-id="e7628-230">Adding the `await` statement to the `model.WriteAsync` call means that the `Train` method must be changed to an async method that returns a task.</span></span> <span data-ttu-id="e7628-231">請修改 `Train`，如以下範例所示：</span><span class="sxs-lookup"><span data-stu-id="e7628-231">Modify the signature of `Train` as shown in the following code:</span></span>

[!code-csharp[AsyncTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "Make the Train method async and return a task.")]

<span data-ttu-id="e7628-232">變更 `Train` 方法的傳回類型時，意謂著您必須將 `await` 新增至會呼叫 `Main` 方法中 `Train` 的程式碼，如以下程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="e7628-232">Changing the return type of the `Train` method means you have to add an `await` to the code that calls `Train` in the `Main` method as shown in the following code:</span></span>

[!code-csharp[AwaitTraining](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Await the Train method")]

<span data-ttu-id="e7628-233">在 `Main` 方法中使用 `await` 時，意謂著 `Main` 方法必須包含 `async` 修飾詞並傳回 `Task`：</span><span class="sxs-lookup"><span data-stu-id="e7628-233">Using `await` in the `Main` method means the `Main` method must have the `async` modifier and return a `Task`:</span></span>

[!code-csharp[AsyncMain](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Make the Main method async and return a task.")]

<span data-ttu-id="e7628-234">您還必須在檔案頂端新增下列 `using` 指示詞：</span><span class="sxs-lookup"><span data-stu-id="e7628-234">You also need to add the following `using` directive at the top of the file:</span></span>

[!code-csharp[UsingTasks](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Add System.Threading.Tasks. to your usings.")]

<span data-ttu-id="e7628-235">由於 `async Main` 方法是 C# 7.1 中的新增功能，而專案的預設語言版本是 C# 7.0，因此您必須將語言版本變更為 C# 7.1 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="e7628-235">Because the `async Main` method is the feature added in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span> <span data-ttu-id="e7628-236">若要這樣做，請以滑鼠右鍵按一下 [方案總管] 中的專案節點，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="e7628-236">To do that, right-click the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="e7628-237">選取 [建置] 索引標籤並選取 [進階] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e7628-237">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="e7628-238">從下拉式清單中，選取 [C# 7.1] (或更新版本)。</span><span class="sxs-lookup"><span data-stu-id="e7628-238">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="e7628-239">選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e7628-239">Select the **OK** button.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="e7628-240">評估模型</span><span class="sxs-lookup"><span data-stu-id="e7628-240">Evaluate the model</span></span>

<span data-ttu-id="e7628-241">評估係指檢查模型預測標籤值之良好程度的程序。</span><span class="sxs-lookup"><span data-stu-id="e7628-241">Evaluation is the process of checking how well the model predicts label values.</span></span> <span data-ttu-id="e7628-242">對模型來說，能夠針對其定型時未使用的資料做出良好的預測是相當重要的。</span><span class="sxs-lookup"><span data-stu-id="e7628-242">It's important that the model makes good predictions on data that was not used to train the model.</span></span> <span data-ttu-id="e7628-243">若要達到此目的，其中一個做法是將資料分割成訓練和測試資料集，就像在本教學課程中所做的一樣。</span><span class="sxs-lookup"><span data-stu-id="e7628-243">One way to do this is to split the data into training and test data sets, as it's done in this tutorial.</span></span> <span data-ttu-id="e7628-244">既然您已依據訓練資料來訓練模型，現在即可查看模型對測試資料的表現。</span><span class="sxs-lookup"><span data-stu-id="e7628-244">Now that you've trained the model on the training data, you can see how well it performs on the test data.</span></span>

<span data-ttu-id="e7628-245">返回 `Main` 方法，然後在 `Train` 方法的呼叫底下，新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="e7628-245">Go back to the `Main` method and add the following code beneath the call to the `Train`method:</span></span>

[!code-csharp[Evaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Evaluate the model.")]

<span data-ttu-id="e7628-246">`Evaluate` 方法會評估模型。</span><span class="sxs-lookup"><span data-stu-id="e7628-246">The `Evaluate` method evaluates the model.</span></span> <span data-ttu-id="e7628-247">若要建立該方法，請在 `Train` 方法底下新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="e7628-247">To create that method, add the following code below the `Train` method:</span></span>

```csharp
private static void Evaluate(PredictionModel<TaxiTrip, TaxiTripFarePrediction> model)
{

}
```

<span data-ttu-id="e7628-248">將下列程式碼新增至 `Evaluate` 方法，來設定測試資料的載入：</span><span class="sxs-lookup"><span data-stu-id="e7628-248">Add the following code into the `Evaluate` method to setup loading of the test data:</span></span>

[!code-csharp[LoadTestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Load the test data.")]

<span data-ttu-id="e7628-249">新增下列程式碼來評估模型並產生評估計量：</span><span class="sxs-lookup"><span data-stu-id="e7628-249">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

[!code-csharp[EvaluateAndMeasure](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Evaluate the model and its predictions.")]

<span data-ttu-id="e7628-250">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) 是迴歸模型的評估計量之一。</span><span class="sxs-lookup"><span data-stu-id="e7628-250">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="e7628-251">此計量值越低，模型就越好。</span><span class="sxs-lookup"><span data-stu-id="e7628-251">The lower it is, the better the model is.</span></span> <span data-ttu-id="e7628-252">將下列程式碼新增至 `Evaluate` 方法，以顯示 RMS 值：</span><span class="sxs-lookup"><span data-stu-id="e7628-252">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Display the RMS metric.")]

<span data-ttu-id="e7628-253">[RSquared](../resources/glossary.md#coefficient-of-determination) 是迴歸模型的另一個評估計量。</span><span class="sxs-lookup"><span data-stu-id="e7628-253">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="e7628-254">RSquared 接受介於 0 和 1 之間的值。</span><span class="sxs-lookup"><span data-stu-id="e7628-254">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="e7628-255">其值越接近 1，模型就越好。</span><span class="sxs-lookup"><span data-stu-id="e7628-255">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="e7628-256">將下列程式碼新增至 `Evaluate` 方法，以顯示 RSquared 值：</span><span class="sxs-lookup"><span data-stu-id="e7628-256">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Display the RSquared metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="e7628-257">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="e7628-257">Use the model for predictions</span></span>

<span data-ttu-id="e7628-258">建立類型以容納測試資料執行個體：</span><span class="sxs-lookup"><span data-stu-id="e7628-258">Create a class to house test data instances:</span></span>

1. <span data-ttu-id="e7628-259">在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="e7628-259">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="e7628-260">在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *TestTrips.cs*。</span><span class="sxs-lookup"><span data-stu-id="e7628-260">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestTrips.cs*.</span></span> <span data-ttu-id="e7628-261">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e7628-261">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="e7628-262">將類別修改成靜態，如以下範例所示：</span><span class="sxs-lookup"><span data-stu-id="e7628-262">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[StaticClass](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#1 "Change class to be a static class.")]

<span data-ttu-id="e7628-263">本教學課程會使用此類別內的一個測試行程。</span><span class="sxs-lookup"><span data-stu-id="e7628-263">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="e7628-264">您可以稍後新增其他案例來對此方法進行實驗。</span><span class="sxs-lookup"><span data-stu-id="e7628-264">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="e7628-265">將下列程式碼新增至 `TestTrips` 類別：</span><span class="sxs-lookup"><span data-stu-id="e7628-265">Add the following code into the `TestTrips` class:</span></span>

[!code-csharp[TestData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TestTrips.cs#2 "Create aq trip to predict its cost.")]

<span data-ttu-id="e7628-266">這個行程的實際車資是 29.5。</span><span class="sxs-lookup"><span data-stu-id="e7628-266">This trip's actual fare is 29.5.</span></span> <span data-ttu-id="e7628-267">請使用 0 作為預留位置，因為此模型將會預測車資。</span><span class="sxs-lookup"><span data-stu-id="e7628-267">Use 0 as a placeholder, as the model will predict the fare.</span></span>

<span data-ttu-id="e7628-268">若要預測指定行程的車資，請返回 *Program.cs* 檔案，然後將下列程式碼新增至 `Main` 方法：</span><span class="sxs-lookup"><span data-stu-id="e7628-268">To predict the fare of the specified trip, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Try a prediction.")]

<span data-ttu-id="e7628-269">執行程式以查看您測試案例的預測計程車車資。</span><span class="sxs-lookup"><span data-stu-id="e7628-269">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="e7628-270">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="e7628-270">Congratulations!</span></span> <span data-ttu-id="e7628-271">您現在已成功建置可預測計程車車資的機器學習模型、評估了它的準確率，並且也使用它進行了預測。</span><span class="sxs-lookup"><span data-stu-id="e7628-271">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="e7628-272">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="e7628-272">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e7628-273">後續步驟</span><span class="sxs-lookup"><span data-stu-id="e7628-273">Next steps</span></span>

<span data-ttu-id="e7628-274">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="e7628-274">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="e7628-275">了解問題</span><span class="sxs-lookup"><span data-stu-id="e7628-275">Understand the problem</span></span>
> * <span data-ttu-id="e7628-276">選取適當的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="e7628-276">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="e7628-277">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="e7628-277">Prepare and understand the data</span></span>
> * <span data-ttu-id="e7628-278">建立學習管線</span><span class="sxs-lookup"><span data-stu-id="e7628-278">Create a learning pipeline</span></span>
> * <span data-ttu-id="e7628-279">載入並轉換資料</span><span class="sxs-lookup"><span data-stu-id="e7628-279">Load and transform the data</span></span>
> * <span data-ttu-id="e7628-280">選擇學習演算法</span><span class="sxs-lookup"><span data-stu-id="e7628-280">Choose a learning algorithm</span></span>
> * <span data-ttu-id="e7628-281">將模型定型</span><span class="sxs-lookup"><span data-stu-id="e7628-281">Train the model</span></span>
> * <span data-ttu-id="e7628-282">評估模型</span><span class="sxs-lookup"><span data-stu-id="e7628-282">Evaluate the model</span></span>
> * <span data-ttu-id="e7628-283">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="e7628-283">Use the model for predictions</span></span>

<span data-ttu-id="e7628-284">前進到下一個教學課程來深入了解。</span><span class="sxs-lookup"><span data-stu-id="e7628-284">Advance to the next tutorial to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="e7628-285">Iris 叢集</span><span class="sxs-lookup"><span data-stu-id="e7628-285">Iris clustering</span></span>](iris-clustering.md)
