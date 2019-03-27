---
title: 透過 ML.NET 使用迴歸學習工具預測價格
description: 透過 ML.NET 使用迴歸學習工具預測價格。
author: aditidugar
ms.author: johalex
ms.date: 03/20/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 0a027b3b4930f7dda48d884faf0484cf33856c8d
ms.sourcegitcommit: 77854e8704b9689b73103d691db34d71c2bf1dad
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2019
ms.locfileid: "58307976"
---
# <a name="tutorial-predict-prices-using-a-regression-learner-with-mlnet"></a><span data-ttu-id="6d27c-103">教學課程：透過 ML.NET 使用迴歸學習工具預測價格</span><span class="sxs-lookup"><span data-stu-id="6d27c-103">Tutorial: Predict prices using a regression learner with ML.NET</span></span>

<span data-ttu-id="6d27c-104">本教學課程說明如何使用 ML.NET 建置用於預測價格 (特別是紐約市計程車車資) 的[迴歸模型](../resources/glossary.md#regression)。</span><span class="sxs-lookup"><span data-stu-id="6d27c-104">This tutorial illustrates how to use ML.NET to build a [regression model](../resources/glossary.md#regression) for predicting prices, specifically, New York City taxi fares.</span></span>

> [!NOTE]
> <span data-ttu-id="6d27c-105">本主題涉及 ML.NET，此功能目前為公開預覽版，因此内容可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="6d27c-105">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="6d27c-106">如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) \(英文)。</span><span class="sxs-lookup"><span data-stu-id="6d27c-106">For more information, see the [ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="6d27c-107">此教學課程與關聯的範例目前是使用 **ML.NET 0.11 版**。</span><span class="sxs-lookup"><span data-stu-id="6d27c-107">This tutorial and related sample are currently using **ML.NET version 0.11**.</span></span> <span data-ttu-id="6d27c-108">如需詳細資訊，請參閱 [dotnet/machinelearning GitHub 存放庫](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes) \(英文\) 中的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="6d27c-108">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="6d27c-109">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="6d27c-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="6d27c-110">了解問題</span><span class="sxs-lookup"><span data-stu-id="6d27c-110">Understand the problem</span></span>
> * <span data-ttu-id="6d27c-111">選取適當的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="6d27c-111">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="6d27c-112">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="6d27c-112">Prepare and understand the data</span></span>
> * <span data-ttu-id="6d27c-113">建立學習管線</span><span class="sxs-lookup"><span data-stu-id="6d27c-113">Create a learning pipeline</span></span>
> * <span data-ttu-id="6d27c-114">載入並轉換資料</span><span class="sxs-lookup"><span data-stu-id="6d27c-114">Load and transform the data</span></span>
> * <span data-ttu-id="6d27c-115">選擇學習演算法</span><span class="sxs-lookup"><span data-stu-id="6d27c-115">Choose a learning algorithm</span></span>
> * <span data-ttu-id="6d27c-116">將模型定型</span><span class="sxs-lookup"><span data-stu-id="6d27c-116">Train the model</span></span>
> * <span data-ttu-id="6d27c-117">評估模型</span><span class="sxs-lookup"><span data-stu-id="6d27c-117">Evaluate the model</span></span>
> * <span data-ttu-id="6d27c-118">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="6d27c-118">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6d27c-119">必要條件</span><span class="sxs-lookup"><span data-stu-id="6d27c-119">Prerequisites</span></span>

* <span data-ttu-id="6d27c-120">已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)。</span><span class="sxs-lookup"><span data-stu-id="6d27c-120">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="6d27c-121">了解問題</span><span class="sxs-lookup"><span data-stu-id="6d27c-121">Understand the problem</span></span>

<span data-ttu-id="6d27c-122">此問題是關於預測紐約市計程車的車資。</span><span class="sxs-lookup"><span data-stu-id="6d27c-122">This problem is about predicting the fare of a taxi trip in New York City.</span></span> <span data-ttu-id="6d27c-123">乍看之下，這可能看似單純取決於行程遠近。</span><span class="sxs-lookup"><span data-stu-id="6d27c-123">At first glance, it may seem to depend simply on the distance traveled.</span></span> <span data-ttu-id="6d27c-124">不過，紐約計程車廠商會針對其他因素 (例如額外的乘客，或使用信用卡而非現金付費) 收取不同的金額。</span><span class="sxs-lookup"><span data-stu-id="6d27c-124">However, taxi vendors in New York charge varying amounts for other factors such as additional passengers or paying with a credit card instead of cash.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="6d27c-125">選取適當的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="6d27c-125">Select the appropriate machine learning task</span></span>

<span data-ttu-id="6d27c-126">您希望根據資料集當中的其他因素來預測價格值，這是一個實際值。</span><span class="sxs-lookup"><span data-stu-id="6d27c-126">You want to predict the price value, which is a real value, based on the other factors in the data set.</span></span> <span data-ttu-id="6d27c-127">為了這麼做，您選擇[迴歸](../resources/glossary.md#regression)機器學習工作。</span><span class="sxs-lookup"><span data-stu-id="6d27c-127">To do that you choose a [regression](../resources/glossary.md#regression) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="6d27c-128">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="6d27c-128">Create a console application</span></span>

1. <span data-ttu-id="6d27c-129">開啟 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="6d27c-129">Open Visual Studio 2017.</span></span> <span data-ttu-id="6d27c-130">從功能表列中選取 [檔案]  >  [新增]  >  [專案]。</span><span class="sxs-lookup"><span data-stu-id="6d27c-130">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="6d27c-131">在 [新增專案] 對話方塊中，選取 [Visual C#] 節點，然後選取 [.NET Core] 節點。</span><span class="sxs-lookup"><span data-stu-id="6d27c-131">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="6d27c-132">然後選取 [主控台應用程式 (.NET Core)] 專案範本。</span><span class="sxs-lookup"><span data-stu-id="6d27c-132">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="6d27c-133">在 [名稱] 文字方塊中，輸入 "TaxiFarePrediction"，然後選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6d27c-133">In the **Name** text box, type "TaxiFarePrediction" and then select the **OK** button.</span></span>

1. <span data-ttu-id="6d27c-134">在您的專案中建立一個名為 *Data* 的目錄以儲存資料集和模型檔案：</span><span class="sxs-lookup"><span data-stu-id="6d27c-134">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="6d27c-135">在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取 [新增] > [新增資料夾]。</span><span class="sxs-lookup"><span data-stu-id="6d27c-135">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="6d27c-136">輸入 "Data"，然後按 Enter。</span><span class="sxs-lookup"><span data-stu-id="6d27c-136">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="6d27c-137">安裝 **Microsoft.ML** NuGet 套件：</span><span class="sxs-lookup"><span data-stu-id="6d27c-137">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="6d27c-138">在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="6d27c-138">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="6d27c-139">選擇 "nuget.org" 作為 [套件來源]，選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6d27c-139">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="6d27c-140">在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。</span><span class="sxs-lookup"><span data-stu-id="6d27c-140">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="6d27c-141">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="6d27c-141">Prepare and understand the data</span></span>

1. <span data-ttu-id="6d27c-142">下載 [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) 和 [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) 資料集，並將它們儲存至您在上一個步驟所建立的 *Data* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="6d27c-142">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) and the [taxi-fare-test.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-test.csv) data sets and save them to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="6d27c-143">我們可以使用這些資料集將機器學習模型定型，然後評估模型的準確程度。</span><span class="sxs-lookup"><span data-stu-id="6d27c-143">We use these data sets to train the machine learning model and then evaluate how accurate the model is.</span></span> <span data-ttu-id="6d27c-144">這些資料集原先來自 [NYC TLC Taxi Trip 資料集](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)。</span><span class="sxs-lookup"><span data-stu-id="6d27c-144">These data sets are originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

1. <span data-ttu-id="6d27c-145">在 [方案總管] 中，以滑鼠右鍵按一下每個 \*.csv 檔案，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="6d27c-145">In **Solution Explorer**, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="6d27c-146">在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。</span><span class="sxs-lookup"><span data-stu-id="6d27c-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

1. <span data-ttu-id="6d27c-147">開啟 **taxi-fare-train.csv** 資料集，然後查看第一個資料列中的資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="6d27c-147">Open the **taxi-fare-train.csv** data set and look at column headers in the first row.</span></span> <span data-ttu-id="6d27c-148">請查看每個資料行。</span><span class="sxs-lookup"><span data-stu-id="6d27c-148">Take a look at each of the columns.</span></span> <span data-ttu-id="6d27c-149">了解資料，並決定哪些資料行是 **features**，以及哪一個資料行是 **label**。</span><span class="sxs-lookup"><span data-stu-id="6d27c-149">Understand the data and decide which columns are **features** and which one is the **label**.</span></span>

<span data-ttu-id="6d27c-150">**label** 是您要預測之資料行的識別碼。</span><span class="sxs-lookup"><span data-stu-id="6d27c-150">The **label** is the identifier of the column you want to predict.</span></span> <span data-ttu-id="6d27c-151">所識別的**特徵**會用來預測標籤。</span><span class="sxs-lookup"><span data-stu-id="6d27c-151">The identified **features** are used to predict the label.</span></span>

<span data-ttu-id="6d27c-152">提供的資料集包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="6d27c-152">The provided data set contains the following columns:</span></span>

* <span data-ttu-id="6d27c-153">**vendor_id：** 計程車廠商的識別碼是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="6d27c-153">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
* <span data-ttu-id="6d27c-154">**rate_code：** 計程車行程的費率類型是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="6d27c-154">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
* <span data-ttu-id="6d27c-155">**passenger_count：** 行程的乘客數目是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="6d27c-155">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
* <span data-ttu-id="6d27c-156">**trip_time_in_secs：** 行程所花費的時間長度。</span><span class="sxs-lookup"><span data-stu-id="6d27c-156">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="6d27c-157">您想要在行程結束之前預測行程的車資。</span><span class="sxs-lookup"><span data-stu-id="6d27c-157">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="6d27c-158">那時，您並不知道行程需要多長的時間。</span><span class="sxs-lookup"><span data-stu-id="6d27c-158">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="6d27c-159">因此，行程時間不是一項特徵，您將從模型中排除這個資料行。</span><span class="sxs-lookup"><span data-stu-id="6d27c-159">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
* <span data-ttu-id="6d27c-160">**trip_distance：** 行程的距離是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="6d27c-160">**trip_distance:** The distance of the trip is a feature.</span></span>
* <span data-ttu-id="6d27c-161">**payment_type：** 付款方式 (現金或信用卡) 是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="6d27c-161">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
* <span data-ttu-id="6d27c-162">**fare_amount：** 計程車車資總計是標籤。</span><span class="sxs-lookup"><span data-stu-id="6d27c-162">**fare_amount:** The total taxi fare paid is the label.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="6d27c-163">建立資料類別</span><span class="sxs-lookup"><span data-stu-id="6d27c-163">Create data classes</span></span>

<span data-ttu-id="6d27c-164">為輸入資料和預測建立類別：</span><span class="sxs-lookup"><span data-stu-id="6d27c-164">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="6d27c-165">在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="6d27c-165">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="6d27c-166">在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *TaxiTrip.cs*。</span><span class="sxs-lookup"><span data-stu-id="6d27c-166">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TaxiTrip.cs*.</span></span> <span data-ttu-id="6d27c-167">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6d27c-167">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="6d27c-168">將下列的 `using` 指示詞加入新檔案：</span><span class="sxs-lookup"><span data-stu-id="6d27c-168">Add the following `using` directives to the new file:</span></span>

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#1 "Add necessary usings")]

<span data-ttu-id="6d27c-169">移除現有的類別定義，然後將下列程式碼 (具有 `TaxiTrip` 和 `TaxiTripFarePrediction` 這兩個類別) 新增至 *TaxiTrip.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="6d27c-169">Remove the existing class definition and add the following code, which has two classes `TaxiTrip` and `TaxiTripFarePrediction`, to the *TaxiTrip.cs* file:</span></span>

[!code-csharp[DefineTaxiTrip](../../../samples/machine-learning/tutorials/TaxiFarePrediction/TaxiTrip.cs#2 "Define the taxi trip and fare predictions classes")]

<span data-ttu-id="6d27c-170">`TaxiTrip` 是輸入資料類別，並含有每個資料集資料行的定義。</span><span class="sxs-lookup"><span data-stu-id="6d27c-170">`TaxiTrip` is the input data class and has definitions for each of the data set columns.</span></span> <span data-ttu-id="6d27c-171">使用 <xref:Microsoft.ML.Data.LoadColumnAttribute> 屬性來指定資料集中來源資料行的索引。</span><span class="sxs-lookup"><span data-stu-id="6d27c-171">Use the <xref:Microsoft.ML.Data.LoadColumnAttribute> attribute to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="6d27c-172">`TaxiTripFarePrediction` 類別代表預測的結果。</span><span class="sxs-lookup"><span data-stu-id="6d27c-172">The `TaxiTripFarePrediction` class represents predicted results.</span></span> <span data-ttu-id="6d27c-173">包含一個套用 `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> 屬性的單一浮點數欄位 `FareAmount`。</span><span class="sxs-lookup"><span data-stu-id="6d27c-173">It has a single float field, `FareAmount`, with a `Score` <xref:Microsoft.ML.Data.ColumnNameAttribute> attribute applied.</span></span> <span data-ttu-id="6d27c-174">如果是迴歸工作，則**分數**資料行包含預測的標籤值。</span><span class="sxs-lookup"><span data-stu-id="6d27c-174">In case of the regression task the **Score** column contains predicted label values.</span></span>

> [!NOTE]
> <span data-ttu-id="6d27c-175">使用 `float` 型別表示輸入和預測資料類別中的浮點值。</span><span class="sxs-lookup"><span data-stu-id="6d27c-175">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="6d27c-176">定義資料和模型路徑</span><span class="sxs-lookup"><span data-stu-id="6d27c-176">Define data and model paths</span></span>

<span data-ttu-id="6d27c-177">在 *Program.cs* 檔案頂端新增下列額外的 `using` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="6d27c-177">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="6d27c-178">您必須建立三個欄位，保存含有資料集的檔案與用來儲存模型之檔案的檔案路徑：</span><span class="sxs-lookup"><span data-stu-id="6d27c-178">You need to create three fields to hold the paths to the files with data sets and the file to save the model:</span></span>

* <span data-ttu-id="6d27c-179">`_trainDataPath` 會針對具有用來定型模型之資料集的檔案，包含檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="6d27c-179">`_trainDataPath` contains the path to the file with the data set used to train the model.</span></span>
* <span data-ttu-id="6d27c-180">`_testDataPath` 會針對具有用來評估模型之資料集的檔案，包含檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="6d27c-180">`_testDataPath` contains the path to the file with the data set used to evaluate the model.</span></span>
* <span data-ttu-id="6d27c-181">`_modelPath` 會針對儲存定型模型的檔案，包含檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="6d27c-181">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="6d27c-182">將下列程式碼加入至緊接在 `Main` 方法上方，以指定這些路徑和 `_textLoader` 變數：</span><span class="sxs-lookup"><span data-stu-id="6d27c-182">Add the following code right above the `Main` method to specify those paths and for the `_textLoader` variable:</span></span>

[!code-csharp[InitializePaths](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#2 "Define variables to store the data file paths")]

<span data-ttu-id="6d27c-183">使用 ML.NET 建置模型時，您要從建立 ML 內容開始。</span><span class="sxs-lookup"><span data-stu-id="6d27c-183">When building a model with ML.NET you start by creating an ML Context.</span></span> <span data-ttu-id="6d27c-184">這在概念上類似於在 Entity Framework 中使用 `DbContext`。</span><span class="sxs-lookup"><span data-stu-id="6d27c-184">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span> <span data-ttu-id="6d27c-185">環境為機器學習作業提供的內容，可用來進行例外狀況追蹤和記錄。</span><span class="sxs-lookup"><span data-stu-id="6d27c-185">The environment provides a context for your machine learning job that can be used for exception tracking and logging.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="6d27c-186">在 Main 中初始化變數</span><span class="sxs-lookup"><span data-stu-id="6d27c-186">Initialize variables in Main</span></span>

<span data-ttu-id="6d27c-187">建立名為 `mlContext` 的變數，並使用 `MLContext` 的新執行個體將它初始化。</span><span class="sxs-lookup"><span data-stu-id="6d27c-187">Create a variable called `mlContext` and initialize it with a new instance of `MLContext`.</span></span>  <span data-ttu-id="6d27c-188">在 `Main` 方法中，以下列程式碼取代 `Console.WriteLine("Hello World!")`：</span><span class="sxs-lookup"><span data-stu-id="6d27c-188">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="6d27c-189">將下列內容加入為 `Main` 方法中的下一行程式碼，來呼叫 `Train` 方法：</span><span class="sxs-lookup"><span data-stu-id="6d27c-189">Add the following as the next line of code in the `Main` method to call the `Train` method:</span></span>

[!code-csharp[Train](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#5 "Train your model")]

<span data-ttu-id="6d27c-190">`Train` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="6d27c-190">The `Train` method executes the following tasks:</span></span>

* <span data-ttu-id="6d27c-191">載入資料。</span><span class="sxs-lookup"><span data-stu-id="6d27c-191">Loads the data.</span></span>
* <span data-ttu-id="6d27c-192">擷取並轉換資料。</span><span class="sxs-lookup"><span data-stu-id="6d27c-192">Extracts and transforms the data.</span></span>
* <span data-ttu-id="6d27c-193">將模型定型。</span><span class="sxs-lookup"><span data-stu-id="6d27c-193">Trains the model.</span></span>
* <span data-ttu-id="6d27c-194">將模型儲存為 .zip 檔案。</span><span class="sxs-lookup"><span data-stu-id="6d27c-194">Saves the model as .zip file.</span></span>
* <span data-ttu-id="6d27c-195">傳回模型。</span><span class="sxs-lookup"><span data-stu-id="6d27c-195">Returns the model.</span></span>

<span data-ttu-id="6d27c-196">`Train` 方法會將模型定型。</span><span class="sxs-lookup"><span data-stu-id="6d27c-196">The `Train` method trains the model.</span></span> <span data-ttu-id="6d27c-197">請使用下列程式碼，在緊接著 `Main` 底下建立該方法：</span><span class="sxs-lookup"><span data-stu-id="6d27c-197">Create that method just below `Main`, using the following code:</span></span>

```csharp
public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

<span data-ttu-id="6d27c-198">我們將兩個參數傳遞到 `Train` 方法：內容 (`mlContext`) 的 `MLContext`，和資料集路徑 (`dataPath`) 的字串。</span><span class="sxs-lookup"><span data-stu-id="6d27c-198">We are passing two parameters into the `Train` method; an `MLContext` for the context (`mlContext`), and a string for the dataset path (`dataPath`).</span></span> <span data-ttu-id="6d27c-199">我們將重複使用此方法來載入資料集。</span><span class="sxs-lookup"><span data-stu-id="6d27c-199">We're going to reuse this method for loading datasets.</span></span>

## <a name="load-and-transform-data"></a><span data-ttu-id="6d27c-200">載入並轉換資料</span><span class="sxs-lookup"><span data-stu-id="6d27c-200">Load and transform data</span></span>

<span data-ttu-id="6d27c-201">使用 [LoadFromTextFile 方法](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29)的 `MLContext.Data.LoadFromTextFile` 包裝函式載入資料。</span><span class="sxs-lookup"><span data-stu-id="6d27c-201">Load the data using the `MLContext.Data.LoadFromTextFile` wrapper for the [LoadFromTextFile method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29).</span></span> <span data-ttu-id="6d27c-202">它會傳回 <xref:Microsoft.Data.DataView.IDataView>。</span><span class="sxs-lookup"><span data-stu-id="6d27c-202">It returns a <xref:Microsoft.Data.DataView.IDataView>.</span></span> 

<span data-ttu-id="6d27c-203">作為 `Transforms` 的輸入和輸出，`DataView` 是基本的資料管線類型，相當於 `LINQ` 的 `IEnumerable`。</span><span class="sxs-lookup"><span data-stu-id="6d27c-203">As the input and output of `Transforms`, a `DataView` is the fundamental data pipeline type, comparable to `IEnumerable` for `LINQ`.</span></span>

<span data-ttu-id="6d27c-204">在 ML.NET 中，資料相當於 SQL 檢視。</span><span class="sxs-lookup"><span data-stu-id="6d27c-204">In ML.NET, data is similar to a SQL view.</span></span> <span data-ttu-id="6d27c-205">它是延遲評估、結構描述化且異質性的。</span><span class="sxs-lookup"><span data-stu-id="6d27c-205">It is lazily evaluated, schematized, and heterogenous.</span></span> <span data-ttu-id="6d27c-206">物件是管線的第一個部分，並且會載入資料。</span><span class="sxs-lookup"><span data-stu-id="6d27c-206">The object is the first part of the pipeline, and loads the data.</span></span> <span data-ttu-id="6d27c-207">在本教學課程中，會載入具有計程車車程定價資訊的資料集。</span><span class="sxs-lookup"><span data-stu-id="6d27c-207">For this tutorial, it loads a dataset with taxi trip pricing information.</span></span> <span data-ttu-id="6d27c-208">這會用來建立模型，並將模型定型。</span><span class="sxs-lookup"><span data-stu-id="6d27c-208">This is used to create the model, and train it.</span></span>

<span data-ttu-id="6d27c-209">將下列程式碼新增為 `Train` 方法的第一行：</span><span class="sxs-lookup"><span data-stu-id="6d27c-209">Add the following code as the first line of the `Train` method:</span></span>

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#6 "loading training dataset")]

<span data-ttu-id="6d27c-210">在接下來的步驟中，我們透過 `TaxiTrip` 類別中定義的名稱來參考資料行。</span><span class="sxs-lookup"><span data-stu-id="6d27c-210">In the next steps we refer to the columns by the names defined in the `TaxiTrip` class.</span></span>

<span data-ttu-id="6d27c-211">根據預設，在定型和評估模型時，**Label** 資料行中的值會視為要預測的正確值。</span><span class="sxs-lookup"><span data-stu-id="6d27c-211">When the model is trained and evaluated, by default, the values in the **Label** column are considered as correct values to be predicted.</span></span> <span data-ttu-id="6d27c-212">因為我們想要預測計程車行程車資，請將 `FareAmount` 資料行複製到 **Label** 資料行。</span><span class="sxs-lookup"><span data-stu-id="6d27c-212">As we want to predict the taxi trip fare, copy the `FareAmount` column into the **Label** column.</span></span> <span data-ttu-id="6d27c-213">若要這樣做，請使用 `CopyColumnsEstimator` 轉換類別，並加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="6d27c-213">To do that, use the `CopyColumnsEstimator` transformation class, and add the following code:</span></span>

[!code-csharp[CopyColumnsEstimator](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#7 "Use the CopyColumnsEstimator")]

<span data-ttu-id="6d27c-214">將模型定型的演算法需要**數值**特徵，因此您需要將類別目錄資料 (`VendorId`、`RateCode` 與 `PaymentType`) 值轉換成數字 (`VendorIdEncoded`、`RateCodeEncoded` 與 `PaymentTypeEncoded`)。</span><span class="sxs-lookup"><span data-stu-id="6d27c-214">The algorithm that trains the model requires **numeric** features, so you have to transform the categorical data (`VendorId`, `RateCode`, and `PaymentType`) values into numbers (`VendorIdEncoded`, `RateCodeEncoded`, and `PaymentTypeEncoded`).</span></span> <span data-ttu-id="6d27c-215">若要這樣做，請使用 Microsoft.ML.Transforms.OneHotEncodingTransformer> 轉換類別，這會將不同的數值索引鍵值指派給每個資料行中的不同值，並新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="6d27c-215">To do that, use the Microsoft.ML.Transforms.OneHotEncodingTransformer> transformation class, which assigns different numeric key values to the different values in each of the columns, and add the following code:</span></span>

[!code-csharp[OneHotEncodingEstimator](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#8 "Use the OneHotEncodingEstimator")]

<span data-ttu-id="6d27c-216">資料準備工作的最後一個步驟是使用 `mlContext.Transforms.Concatenate` 轉換類別，將所有特徵資料行合併為 **Features** 資料行。</span><span class="sxs-lookup"><span data-stu-id="6d27c-216">The last step in data preparation combines all of the feature columns into the **Features** column using the `mlContext.Transforms.Concatenate` transformation class.</span></span> <span data-ttu-id="6d27c-217">根據預設，學習演算法只會處理來自 **Features** 資料行的特徵。</span><span class="sxs-lookup"><span data-stu-id="6d27c-217">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="6d27c-218">加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="6d27c-218">Add the following code:</span></span>

[!code-csharp[ColumnConcatenatingEstimator](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#9 "Use the ColumnConcatenatingEstimator")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="6d27c-219">選擇學習演算法</span><span class="sxs-lookup"><span data-stu-id="6d27c-219">Choose a learning algorithm</span></span>

<span data-ttu-id="6d27c-220">將資料新增至管線並將其轉換成正確的輸入格式之後，我們需選取學習演算法 (**學習工具**)。</span><span class="sxs-lookup"><span data-stu-id="6d27c-220">After adding the data to the pipeline and transforming it into the correct input format, we select a learning algorithm (**learner**).</span></span> <span data-ttu-id="6d27c-221">學習工具會將模型定型。</span><span class="sxs-lookup"><span data-stu-id="6d27c-221">The learner trains the model.</span></span> <span data-ttu-id="6d27c-222">我們為這個問題選擇了**迴歸**工作，因此我們將使用 `FastTreeRegressionTrainer` 學習工具，這是 ML.NET 所提供的其中一個迴歸學習工具。</span><span class="sxs-lookup"><span data-stu-id="6d27c-222">We chose a **regression** task for this problem, so we use a `FastTreeRegressionTrainer` learner, which is one of the regression learners provided by ML.NET.</span></span>

<span data-ttu-id="6d27c-223">`FastTreeRegressionTrainer` 訓練演算法使用梯度提升。</span><span class="sxs-lookup"><span data-stu-id="6d27c-223">The `FastTreeRegressionTrainer` training algorithm utilizes gradient boosting.</span></span> <span data-ttu-id="6d27c-224">梯度提升是一種適用於迴歸問題的機器學習技術。</span><span class="sxs-lookup"><span data-stu-id="6d27c-224">Gradient boosting is a machine learning technique for regression problems.</span></span> <span data-ttu-id="6d27c-225">它會以逐步方式建置每個迴歸樹。</span><span class="sxs-lookup"><span data-stu-id="6d27c-225">It builds each regression tree in a step-wise fashion.</span></span> <span data-ttu-id="6d27c-226">它會使用預先定義的損失函式來評估每個步驟中的誤差，然後在下一個步驟中為其進行修正。</span><span class="sxs-lookup"><span data-stu-id="6d27c-226">It uses a pre-defined loss function to measure the error in each step and correct for it in the next.</span></span> <span data-ttu-id="6d27c-227">結果會產生一個預測模型，這實際上就是較弱預測模型的總體。</span><span class="sxs-lookup"><span data-stu-id="6d27c-227">The result is a prediction model that is actually an ensemble of weaker prediction models.</span></span> <span data-ttu-id="6d27c-228">如需有關梯度提升的詳細資訊，請參閱[提升的決策樹迴歸](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="6d27c-228">For more information about gradient boosting, see [Boosted Decision Tree Regression](/azure/machine-learning/studio-module-reference/boosted-decision-tree-regression).</span></span>

<span data-ttu-id="6d27c-229">將下列程式碼加入至 `Train` 方法中以將 `FastTreeRegressionTrainer` 加入到上一個步驟中加入的資料處理程式碼：</span><span class="sxs-lookup"><span data-stu-id="6d27c-229">Add the following code into the `Train` method to add the `FastTreeRegressionTrainer` to the data processing code added in the previous step:</span></span>

[!code-csharp[FastTreeRegressionTrainer](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#10 "Add the FastTreeRegressionTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="6d27c-230">將模型定型</span><span class="sxs-lookup"><span data-stu-id="6d27c-230">Train the model</span></span>

<span data-ttu-id="6d27c-231">最後一個步驟是將模型定型。</span><span class="sxs-lookup"><span data-stu-id="6d27c-231">The final step is to train the model.</span></span> <span data-ttu-id="6d27c-232">我們會根據已載入和轉換的資料集將模型 <xref:Microsoft.ML.Data.TransformerChain> 定型。</span><span class="sxs-lookup"><span data-stu-id="6d27c-232">We train the model, <xref:Microsoft.ML.Data.TransformerChain>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="6d27c-233">一旦定義了評估工具之後，我們使用 <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> 定型模型，並提供已載入的定型資料。</span><span class="sxs-lookup"><span data-stu-id="6d27c-233">Once the estimator has been defined, we train the model using the <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> while providing the already loaded training data.</span></span> <span data-ttu-id="6d27c-234">這會傳回要用於預測的模型。</span><span class="sxs-lookup"><span data-stu-id="6d27c-234">This returns a model to use for predictions.</span></span> <span data-ttu-id="6d27c-235">`pipeline.Fit()` 會定型管線，並根據傳入的 `DataView` 傳回 `Transformer`。</span><span class="sxs-lookup"><span data-stu-id="6d27c-235">`pipeline.Fit()` trains the pipeline and returns a `Transformer` based on the `DataView` passed in.</span></span> <span data-ttu-id="6d27c-236">實驗會等到定型之後才會執行。</span><span class="sxs-lookup"><span data-stu-id="6d27c-236">The experiment is not executed until this happens.</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#11 "Train the model")]

### <a name="save-the-model"></a><span data-ttu-id="6d27c-237">儲存模型</span><span class="sxs-lookup"><span data-stu-id="6d27c-237">Save the model</span></span>

<span data-ttu-id="6d27c-238">此時，您已有一個可整合至任何現有或新 .NET 應用程式之 <xref:Microsoft.ML.Data.TransformerChain> 類型的模型。</span><span class="sxs-lookup"><span data-stu-id="6d27c-238">At this point, you have a model of type <xref:Microsoft.ML.Data.TransformerChain> that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="6d27c-239">若要將模型儲存至 .zip 檔案，請在 `Train` 方法的結尾新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="6d27c-239">To save the model to a .zip file, add the following code at the end of the `Train` method:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#12 "Save the model as a .zip file and return the model")]

## <a name="save-the-model-as-a-zip-file"></a><span data-ttu-id="6d27c-240">將模型儲存為 .zip 檔案</span><span class="sxs-lookup"><span data-stu-id="6d27c-240">Save the model as a .zip file</span></span>

<span data-ttu-id="6d27c-241">請使用下列程式碼，在緊接著 `Train` 方法之後，建立 `SaveModelAsFile` 方法：</span><span class="sxs-lookup"><span data-stu-id="6d27c-241">Create the `SaveModelAsFile` method, just after the `Train` method, using the following code:</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="6d27c-242">`SaveModelAsFile` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="6d27c-242">The `SaveModelAsFile` method executes the following tasks:</span></span>

* <span data-ttu-id="6d27c-243">將模型儲存為 .zip 檔案。</span><span class="sxs-lookup"><span data-stu-id="6d27c-243">Saves the model as a .zip file.</span></span>

<span data-ttu-id="6d27c-244">我們需要建立儲存模型的方法，以便在其他應用程式中重複使用。</span><span class="sxs-lookup"><span data-stu-id="6d27c-244">We need to create a method to save the model so that it can be reused and consumed in other applications.</span></span> <span data-ttu-id="6d27c-245">`ITransformer` 具有 <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> 方法，它會採用 `_modelPath` 全域欄位和 <xref:System.IO.Stream>。</span><span class="sxs-lookup"><span data-stu-id="6d27c-245">The `ITransformer` has a <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> method that takes in the `_modelPath` global field, and a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="6d27c-246">因為我們想要將此儲存為 ZIP 檔案，我們將建立 `FileStream`，緊接著呼叫 `SaveTo` 方法。</span><span class="sxs-lookup"><span data-stu-id="6d27c-246">Since we want to save this as a zip file, we'll create the `FileStream` immediately before calling the `SaveTo` method.</span></span> <span data-ttu-id="6d27c-247">將下列程式碼加入為 `SaveModelAsFile` 方法中的下一行：</span><span class="sxs-lookup"><span data-stu-id="6d27c-247">Add the following code to the `SaveModelAsFile` method as the next line:</span></span>

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#13 "Add the SaveTo Method")]

<span data-ttu-id="6d27c-248">我們可以搭配 `_modelPath` 使用下列程式碼撰寫主控台訊息，來顯示檔案寫入的位置：</span><span class="sxs-lookup"><span data-stu-id="6d27c-248">We could also display where the file was written by writing a console message with the `_modelPath`, using the following code:</span></span>

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="evaluate-the-model"></a><span data-ttu-id="6d27c-249">評估模型</span><span class="sxs-lookup"><span data-stu-id="6d27c-249">Evaluate the model</span></span>

<span data-ttu-id="6d27c-250">評估係指檢查模型預測標籤值之良好程度的程序。</span><span class="sxs-lookup"><span data-stu-id="6d27c-250">Evaluation is the process of checking how well the model predicts label values.</span></span> <span data-ttu-id="6d27c-251">對模型來說，能夠針對其定型時未使用的資料做出良好的預測是相當重要的。</span><span class="sxs-lookup"><span data-stu-id="6d27c-251">It's important that the model makes good predictions on data that was not used to train the model.</span></span> <span data-ttu-id="6d27c-252">若要達到此目的，其中一個做法是將資料分割成訓練和測試資料集，就像在本教學課程中所做的一樣。</span><span class="sxs-lookup"><span data-stu-id="6d27c-252">One way to do this is to split the data into training and test data sets, as it's done in this tutorial.</span></span> <span data-ttu-id="6d27c-253">既然您已依據訓練資料來訓練模型，現在即可查看模型對測試資料的表現。</span><span class="sxs-lookup"><span data-stu-id="6d27c-253">Now that you've trained the model on the training data, you can see how well it performs on the test data.</span></span>

<span data-ttu-id="6d27c-254">`Evaluate` 方法會評估模型。</span><span class="sxs-lookup"><span data-stu-id="6d27c-254">The `Evaluate` method evaluates the model.</span></span> <span data-ttu-id="6d27c-255">若要建立該方法，請在 `Train` 方法底下新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="6d27c-255">To create that method, add the following code below the `Train` method:</span></span>

```csharp
private static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```
<span data-ttu-id="6d27c-256">`Evaluate` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="6d27c-256">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="6d27c-257">載入測試資料集。</span><span class="sxs-lookup"><span data-stu-id="6d27c-257">Loads the test dataset.</span></span>
* <span data-ttu-id="6d27c-258">建立迴歸評估工具。</span><span class="sxs-lookup"><span data-stu-id="6d27c-258">Creates the regression evaluator.</span></span>
* <span data-ttu-id="6d27c-259">評估模型並建立計量。</span><span class="sxs-lookup"><span data-stu-id="6d27c-259">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="6d27c-260">顯示計量。</span><span class="sxs-lookup"><span data-stu-id="6d27c-260">Displays the metrics.</span></span>

<span data-ttu-id="6d27c-261">請使用下列程式碼，在緊接著 `Train` 方法呼叫底下，從 `Main` 方法新增對新方法的呼叫：</span><span class="sxs-lookup"><span data-stu-id="6d27c-261">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#14 "Call the Evaluate method")]

<span data-ttu-id="6d27c-262">使用 `MLContext.Data.LoadFromTextFile` 包裝函式載入測試資料集。</span><span class="sxs-lookup"><span data-stu-id="6d27c-262">Load the test dataset using the `MLContext.Data.LoadFromTextFile` wrapper.</span></span> <span data-ttu-id="6d27c-263">您可以使用此資料集來評估模型，以作為品質檢查。</span><span class="sxs-lookup"><span data-stu-id="6d27c-263">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="6d27c-264">將下列程式碼加入 `Evaluate` 方法：</span><span class="sxs-lookup"><span data-stu-id="6d27c-264">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#15 "Load the test dataset")]

<span data-ttu-id="6d27c-265">接下來，使用機器學習 `model` 參數 (轉換器) 來輸入特徵並傳回預測。</span><span class="sxs-lookup"><span data-stu-id="6d27c-265">Next, use the machine learning `model` parameter (a transformer) to input the features and return predictions.</span></span> <span data-ttu-id="6d27c-266">將下列程式碼加入 `Evaluate` 方法中作為的下一行：</span><span class="sxs-lookup"><span data-stu-id="6d27c-266">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#16 "Predict using the Transformer")]

<span data-ttu-id="6d27c-267">`RegressionContext.Evaluate` 方法會使用指定的資料集來計算 `PredictionModel` 的品質計量。</span><span class="sxs-lookup"><span data-stu-id="6d27c-267">The `RegressionContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="6d27c-268">它傳回的 <xref:Microsoft.ML.Data.RegressionMetrics> 物件包含迴歸評估工具所計算的整體計量。</span><span class="sxs-lookup"><span data-stu-id="6d27c-268">It returns a <xref:Microsoft.ML.Data.RegressionMetrics> object that contains the overall metrics computed by regression evaluators.</span></span> <span data-ttu-id="6d27c-269">若要顯示這些計量以判斷模型的品質，您必須先取得計量。</span><span class="sxs-lookup"><span data-stu-id="6d27c-269">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="6d27c-270">將下列程式碼加入為 `Evaluate` 方法中的下一行：</span><span class="sxs-lookup"><span data-stu-id="6d27c-270">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#17 "Compute Metrics")]

<span data-ttu-id="6d27c-271">新增下列程式碼來評估模型並產生評估計量：</span><span class="sxs-lookup"><span data-stu-id="6d27c-271">Add the following code to evaluate the model and produce the evaluation metrics:</span></span>

```csharp
Console.WriteLine();
Console.WriteLine($"*************************************************");
Console.WriteLine($"*       Model quality metrics evaluation         ");
Console.WriteLine($"*------------------------------------------------");
```

<span data-ttu-id="6d27c-272">[RSquared](../resources/glossary.md#coefficient-of-determination) 是迴歸模型的另一個評估計量。</span><span class="sxs-lookup"><span data-stu-id="6d27c-272">[RSquared](../resources/glossary.md#coefficient-of-determination) is another evaluation metric of the regression models.</span></span> <span data-ttu-id="6d27c-273">RSquared 接受介於 0 和 1 之間的值。</span><span class="sxs-lookup"><span data-stu-id="6d27c-273">RSquared takes values between 0 and 1.</span></span> <span data-ttu-id="6d27c-274">其值越接近 1，模型就越好。</span><span class="sxs-lookup"><span data-stu-id="6d27c-274">The closer its value is to 1, the better the model is.</span></span> <span data-ttu-id="6d27c-275">將下列程式碼新增至 `Evaluate` 方法，以顯示 RSquared 值：</span><span class="sxs-lookup"><span data-stu-id="6d27c-275">Add the following code into the `Evaluate` method to display the RSquared value:</span></span>

[!code-csharp[DisplayRSquared](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#18 "Display the RSquared metric.")]

<span data-ttu-id="6d27c-276">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) 是迴歸模型的評估計量之一。</span><span class="sxs-lookup"><span data-stu-id="6d27c-276">[RMS](../resources/glossary.md##root-of-mean-squared-error-rmse) is one of the evaluation metrics of the regression model.</span></span> <span data-ttu-id="6d27c-277">此計量值越低，模型就越好。</span><span class="sxs-lookup"><span data-stu-id="6d27c-277">The lower it is, the better the model is.</span></span> <span data-ttu-id="6d27c-278">將下列程式碼新增至 `Evaluate` 方法，以顯示 RMS 值：</span><span class="sxs-lookup"><span data-stu-id="6d27c-278">Add the following code into the `Evaluate` method to display the RMS value:</span></span>

[!code-csharp[DisplayRMS](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#19 "Display the RMS metric.")]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="6d27c-279">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="6d27c-279">Use the model for predictions</span></span>


## <a name="predict-the-test-data-outcome-with-the-model-and-a-single-comment"></a><span data-ttu-id="6d27c-280">使用模型和單一評論來預測測試資料結果</span><span class="sxs-lookup"><span data-stu-id="6d27c-280">Predict the test data outcome with the model and a single comment</span></span>

<span data-ttu-id="6d27c-281">請使用下列程式碼，在緊接著 `Evaluate` 方法之後，建立 `TestSinglePrediction` 方法：</span><span class="sxs-lookup"><span data-stu-id="6d27c-281">Create the `TestSinglePrediction` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void TestSinglePrediction(MLContext mlContext)
{

}
```

<span data-ttu-id="6d27c-282">`TestSinglePrediction` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="6d27c-282">The `TestSinglePrediction` method executes the following tasks:</span></span>

* <span data-ttu-id="6d27c-283">建立測試資料的單一評論。</span><span class="sxs-lookup"><span data-stu-id="6d27c-283">Creates a single comment of test data.</span></span>
* <span data-ttu-id="6d27c-284">根據測試資料預測費用金額。</span><span class="sxs-lookup"><span data-stu-id="6d27c-284">Predicts fare amount based on test data.</span></span>
* <span data-ttu-id="6d27c-285">合併測試資料和預測來進行報告。</span><span class="sxs-lookup"><span data-stu-id="6d27c-285">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="6d27c-286">顯示預測的結果。</span><span class="sxs-lookup"><span data-stu-id="6d27c-286">Displays the predicted results.</span></span>

<span data-ttu-id="6d27c-287">請使用下列程式碼，在緊接著 `Evaluate` 方法呼叫底下，從 `Main` 方法新增對新方法的呼叫：</span><span class="sxs-lookup"><span data-stu-id="6d27c-287">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallTestSinglePrediction](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#20 "Call the TestSinglePrediction method")]

<span data-ttu-id="6d27c-288">因為我們想要從已儲存的 ZIP 檔案載入模型，我們要建立 `FileStream`，緊接著呼叫 `Load` 方法。</span><span class="sxs-lookup"><span data-stu-id="6d27c-288">Since we want to load the model from the zip file we saved, we'll create the `FileStream` immediately before calling the `Load` method.</span></span> <span data-ttu-id="6d27c-289">將下列程式碼加入為 `TestSinglePrediction` 方法中的下一行：</span><span class="sxs-lookup"><span data-stu-id="6d27c-289">Add the following code to the `TestSinglePrediction` method as the next line:</span></span>

[!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#21 "Load the model")]

<span data-ttu-id="6d27c-290">雖然 `model` 是可在多個資料列上運作的 `transformer`，但常見的生產環境案例需要根據個別範例進行預測。</span><span class="sxs-lookup"><span data-stu-id="6d27c-290">While the `model` is a `transformer` that operates on many rows of data, a very common production scenario is a need for predictions on individual examples.</span></span> <span data-ttu-id="6d27c-291"><xref:Microsoft.ML.PredictionEngine%602> 是從 `CreatePredictionEngine` 方法傳回的包裝函式。</span><span class="sxs-lookup"><span data-stu-id="6d27c-291">The <xref:Microsoft.ML.PredictionEngine%602> is a wrapper that is returned from the `CreatePredictionEngine` method.</span></span> <span data-ttu-id="6d27c-292">讓我們在 `TestSinglePrediction` 方法中的第二行新增下列程式碼，來建立 `PredictionEngine`：</span><span class="sxs-lookup"><span data-stu-id="6d27c-292">Let's add the following code to create the `PredictionEngine` as the next line in the `TestSinglePrediction` Method:</span></span>

[!code-csharp[MakePredictionEngine](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#22 "Create the PredictionFunction")]
  
<span data-ttu-id="6d27c-293">本教學課程會使用此類別內的一個測試行程。</span><span class="sxs-lookup"><span data-stu-id="6d27c-293">This tutorial uses one test trip within this class.</span></span> <span data-ttu-id="6d27c-294">您可以稍後新增其他案例來對此方法進行實驗。</span><span class="sxs-lookup"><span data-stu-id="6d27c-294">Later you can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="6d27c-295">透過建立 `TaxiTrip` 的執行個體，在 `TestSinglePrediction` 方法中新增車程，以測試定型模型的費用預測：</span><span class="sxs-lookup"><span data-stu-id="6d27c-295">Add a trip to test the trained model's prediction of cost in the `TestSinglePrediction` method by creating an instance of `TaxiTrip`:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#23 "Create test data for single prediction")]

 <span data-ttu-id="6d27c-296">我們可以使用它來根據計程車車程資料的單一執行個體預測費用。</span><span class="sxs-lookup"><span data-stu-id="6d27c-296">We can use that to predict the fare based on a single instance of the taxi trip data.</span></span> <span data-ttu-id="6d27c-297">若要取得預測，請在資料上使用 <xref:Microsoft.ML.PredictionEngine%602.Predict%2A>。</span><span class="sxs-lookup"><span data-stu-id="6d27c-297">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="6d27c-298">請注意，輸入資料是一個字串，且模型包含特徵化。</span><span class="sxs-lookup"><span data-stu-id="6d27c-298">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="6d27c-299">在定型和預測期間，您的管線會同步。</span><span class="sxs-lookup"><span data-stu-id="6d27c-299">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="6d27c-300">您無須特別為預測撰寫前處理/特徵化程式碼，同一個 API 會同時負責批次和單次預測。</span><span class="sxs-lookup"><span data-stu-id="6d27c-300">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#24 "Create a prediction of taxi fare")]

<span data-ttu-id="6d27c-301">若要顯示指定之車程的預測費用，請將下列程式碼加入到 `TestSinglePrediction` 方法：</span><span class="sxs-lookup"><span data-stu-id="6d27c-301">To display the predicted fare of the specified trip, add the following code into the `TestSinglePrediction` method:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/TaxiFarePrediction/Program.cs#25 "Display the prediction.")]

<span data-ttu-id="6d27c-302">執行程式以查看您測試案例的預測計程車車資。</span><span class="sxs-lookup"><span data-stu-id="6d27c-302">Run the program to see the predicted taxi fare for your test case.</span></span>

<span data-ttu-id="6d27c-303">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="6d27c-303">Congratulations!</span></span> <span data-ttu-id="6d27c-304">您現在已成功建置可預測計程車車資的機器學習模型、評估了它的準確率，並且也使用它進行了預測。</span><span class="sxs-lookup"><span data-stu-id="6d27c-304">You've now successfully built a machine learning model for predicting taxi trip fares, evaluated its accuracy, and used it to make predictions.</span></span> <span data-ttu-id="6d27c-305">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="6d27c-305">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TaxiFarePrediction) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6d27c-306">後續步驟</span><span class="sxs-lookup"><span data-stu-id="6d27c-306">Next steps</span></span>

<span data-ttu-id="6d27c-307">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="6d27c-307">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="6d27c-308">了解問題</span><span class="sxs-lookup"><span data-stu-id="6d27c-308">Understand the problem</span></span>
> * <span data-ttu-id="6d27c-309">選取適當的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="6d27c-309">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="6d27c-310">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="6d27c-310">Prepare and understand the data</span></span>
> * <span data-ttu-id="6d27c-311">建立學習管線</span><span class="sxs-lookup"><span data-stu-id="6d27c-311">Create a learning pipeline</span></span>
> * <span data-ttu-id="6d27c-312">載入並轉換資料</span><span class="sxs-lookup"><span data-stu-id="6d27c-312">Load and transform the data</span></span>
> * <span data-ttu-id="6d27c-313">選擇學習演算法</span><span class="sxs-lookup"><span data-stu-id="6d27c-313">Choose a learning algorithm</span></span>
> * <span data-ttu-id="6d27c-314">將模型定型</span><span class="sxs-lookup"><span data-stu-id="6d27c-314">Train the model</span></span>
> * <span data-ttu-id="6d27c-315">評估模型</span><span class="sxs-lookup"><span data-stu-id="6d27c-315">Evaluate the model</span></span>
> * <span data-ttu-id="6d27c-316">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="6d27c-316">Use the model for predictions</span></span>

<span data-ttu-id="6d27c-317">前進到下一個教學課程來深入了解。</span><span class="sxs-lookup"><span data-stu-id="6d27c-317">Advance to the next tutorial to learn more.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="6d27c-318">Iris 叢集</span><span class="sxs-lookup"><span data-stu-id="6d27c-318">Iris clustering</span></span>](iris-clustering.md)
