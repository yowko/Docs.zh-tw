---
title: 搭配模型產生器使用迴歸來預測價格
description: 本教學課程會特別示範如何使用 ML.NET 模型產生器來建置迴歸模型以預測紐約市的計程車費用。
author: luisquintanilla
ms.author: luquinta
ms.date: 06/26/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: d9a6f193d877fc1a679b7a3cafd7491e021cb2ad
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539626"
---
# <a name="predict-prices-using-regression-with-model-builder"></a><span data-ttu-id="157f9-103">搭配模型產生器使用迴歸來預測價格</span><span class="sxs-lookup"><span data-stu-id="157f9-103">Predict prices using regression with Model Builder</span></span>

<span data-ttu-id="157f9-104">了解如何使用 ML.NET 模型產生器建置[迴歸模型](../resources/glossary.md#regression)來預測價格。</span><span class="sxs-lookup"><span data-stu-id="157f9-104">Learn how to use ML.NET Model Builder to build a [regression model](../resources/glossary.md#regression) to predict prices.</span></span>  <span data-ttu-id="157f9-105">在本教學課程中您所開發 .NET 主控台應用程式會根據紐約的歷史計程車費用資料來預測計程車費用。</span><span class="sxs-lookup"><span data-stu-id="157f9-105">The .NET console app that you develop in this tutorial predicts taxi fares based on historical New York taxi fare data.</span></span>

<span data-ttu-id="157f9-106">模型建置器價格預測範例可用於任何需要數字預測值的案例。</span><span class="sxs-lookup"><span data-stu-id="157f9-106">The Model Builder price prediction template can be used for any scenario requiring a numerical prediction value.</span></span> <span data-ttu-id="157f9-107">範例案例包括：房價預測、需求預測及銷售預測。</span><span class="sxs-lookup"><span data-stu-id="157f9-107">Example scenarios include: house price prediction, demand prediction, and sales forecasting.</span></span>

<span data-ttu-id="157f9-108">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="157f9-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="157f9-109">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="157f9-109">Prepare and understand the data</span></span>
> * <span data-ttu-id="157f9-110">選擇案例</span><span class="sxs-lookup"><span data-stu-id="157f9-110">Choose a scenario</span></span>
> * <span data-ttu-id="157f9-111">載入資料</span><span class="sxs-lookup"><span data-stu-id="157f9-111">Load the data</span></span>
> * <span data-ttu-id="157f9-112">將模型定型</span><span class="sxs-lookup"><span data-stu-id="157f9-112">Train the model</span></span>
> * <span data-ttu-id="157f9-113">評估模型</span><span class="sxs-lookup"><span data-stu-id="157f9-113">Evaluate the model</span></span>
> * <span data-ttu-id="157f9-114">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="157f9-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="157f9-115">模型產生器目前為預覽版。</span><span class="sxs-lookup"><span data-stu-id="157f9-115">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="157f9-116">必要條件</span><span class="sxs-lookup"><span data-stu-id="157f9-116">Pre-requisites</span></span>

<span data-ttu-id="157f9-117">如需必要條件和安裝指示清單，請瀏覽[模型產生器安裝指南](../how-to-guides/install-model-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="157f9-117">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="157f9-118">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="157f9-118">Create a console application</span></span>

1. <span data-ttu-id="157f9-119">建立稱為 "TaxiFarePrediction" 的 **.NET Core 主控台應用程式**。</span><span class="sxs-lookup"><span data-stu-id="157f9-119">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

1. <span data-ttu-id="157f9-120">安裝 **Microsoft.ML** NuGet 套件：</span><span class="sxs-lookup"><span data-stu-id="157f9-120">Install the **Microsoft.ML** NuGet Package:</span></span>

    <span data-ttu-id="157f9-121">在 [方案總管]  中，以滑鼠右鍵按一下 *TaxiFarePrediction* 專案，然後選取 [管理 NuGet 套件]  。</span><span class="sxs-lookup"><span data-stu-id="157f9-121">In **Solution Explorer**, right-click the *TaxiFarePrediction* project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="157f9-122">選擇 "nuget.org" 作為 [套件來源]、選取 [瀏覽]  索引標籤、搜尋 **Microsoft.ML**、從清單中選取該套件，然後選取 [安裝]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="157f9-122">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="157f9-123">在 [預覽變更]  對話方塊上，選取 [確定]  按鈕，然後在 [授權接受]  對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]  。</span><span class="sxs-lookup"><span data-stu-id="157f9-123">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="157f9-124">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="157f9-124">Prepare and understand the data</span></span>

1. <span data-ttu-id="157f9-125">在您專案中建立名為 *Data* 的目錄來儲存資料集檔案。</span><span class="sxs-lookup"><span data-stu-id="157f9-125">Create a directory named *Data* in your project to store the data set files.</span></span>

1. <span data-ttu-id="157f9-126">下載 [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) 資料集，並將它儲存到您在前一個步驟中建立的 *Data* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="157f9-126">Download the [taxi-fare-train.csv](https://github.com/dotnet/machinelearning/blob/master/test/data/taxi-fare-train.csv) data set and save it to the *Data* folder you created at the previous step.</span></span> <span data-ttu-id="157f9-127">此資料集會用來定型及評估機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="157f9-127">This data set is used to train and evaluate the machine learning model.</span></span> <span data-ttu-id="157f9-128">此資料集源自 [NYC TLC Taxi Trip 資料集](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)。</span><span class="sxs-lookup"><span data-stu-id="157f9-128">This data set is originally from the [NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml).</span></span>

1. <span data-ttu-id="157f9-129">在 [方案總管]  中，以滑鼠右鍵按一下 *taxi-fare-train.csv* 檔案，然後選取 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="157f9-129">In **Solution Explorer**, right-click the *taxi-fare-train.csv* file and select **Properties**.</span></span> <span data-ttu-id="157f9-130">在 [進階]  底下，將 [複製到輸出目錄]  的值變更為 [有更新時才複製]  。</span><span class="sxs-lookup"><span data-stu-id="157f9-130">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="157f9-131">`taxi-fare-train.csv` 資料集中的每個資料列都包含計程車車程的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="157f9-131">Each row in the `taxi-fare-train.csv` data set contains details of trips made by a taxi.</span></span>

1. <span data-ttu-id="157f9-132">開啟 **taxi-fare-train.csv** 資料集</span><span class="sxs-lookup"><span data-stu-id="157f9-132">Open the **taxi-fare-train.csv** data set</span></span>

    <span data-ttu-id="157f9-133">提供的資料集包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="157f9-133">The provided data set contains the following columns:</span></span>

    * <span data-ttu-id="157f9-134">**vendor_id：** 計程車廠商的識別碼是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="157f9-134">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
    * <span data-ttu-id="157f9-135">**rate_code：** 計程車行程的費率類型是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="157f9-135">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
    * <span data-ttu-id="157f9-136">**passenger_count：** 行程的乘客數目是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="157f9-136">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
    * <span data-ttu-id="157f9-137">**trip_time_in_secs：** 行程所花費的時間長度。</span><span class="sxs-lookup"><span data-stu-id="157f9-137">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="157f9-138">您想要在行程結束之前預測行程的車資。</span><span class="sxs-lookup"><span data-stu-id="157f9-138">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="157f9-139">那時，您並不知道行程需要多長的時間。</span><span class="sxs-lookup"><span data-stu-id="157f9-139">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="157f9-140">因此，行程時間不是一項特徵，您將從模型中排除這個資料行。</span><span class="sxs-lookup"><span data-stu-id="157f9-140">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
    * <span data-ttu-id="157f9-141">**trip_distance：** 行程的距離是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="157f9-141">**trip_distance:** The distance of the trip is a feature.</span></span>
    * <span data-ttu-id="157f9-142">**payment_type：** 付款方式 (現金或信用卡) 是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="157f9-142">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
    * <span data-ttu-id="157f9-143">**fare_amount：** 計程車車資總計是標籤。</span><span class="sxs-lookup"><span data-stu-id="157f9-143">**fare_amount:** The total taxi fare paid is the label.</span></span>

<span data-ttu-id="157f9-144">`label` 是您希望進行預測的資料行。</span><span class="sxs-lookup"><span data-stu-id="157f9-144">The `label` is the column you want to predict.</span></span> <span data-ttu-id="157f9-145">執行迴歸工作時，目標是預測數值。</span><span class="sxs-lookup"><span data-stu-id="157f9-145">When performing a regression task, the goal is to predict a numerical value.</span></span> <span data-ttu-id="157f9-146">在這個價格預測案例中，會預測計程車車程的成本。</span><span class="sxs-lookup"><span data-stu-id="157f9-146">In this price prediction scenario, the cost of a taxi ride is being predicted.</span></span> <span data-ttu-id="157f9-147">因此，**fare_amount** 為標籤。</span><span class="sxs-lookup"><span data-stu-id="157f9-147">Therefore, the **fare_amount** is the label.</span></span> <span data-ttu-id="157f9-148">所識別 `features` 則是您提供模型來預測 `label` 的輸入。</span><span class="sxs-lookup"><span data-stu-id="157f9-148">The identified `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="157f9-149">在此案例中，其餘資料行都會用來作為特徵或輸入，來預測費用金額。</span><span class="sxs-lookup"><span data-stu-id="157f9-149">In this case, the rest of the columns are used as features or inputs to predict the fare amount.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="157f9-150">選擇案例</span><span class="sxs-lookup"><span data-stu-id="157f9-150">Choose a scenario</span></span>

<span data-ttu-id="157f9-151">若要定型您的模型，您需要從模型產生器所提供的可用機器學習服務案例清單中選取。</span><span class="sxs-lookup"><span data-stu-id="157f9-151">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="157f9-152">在此案例中，案例為 `Price Prediction`。</span><span class="sxs-lookup"><span data-stu-id="157f9-152">In this case, the scenario is `Price Prediction`.</span></span> <span data-ttu-id="157f9-153">如需更廣泛的清單，請瀏覽[模型產生器概觀文章](../automate-training-with-model-builder.md#scenarios)。</span><span class="sxs-lookup"><span data-stu-id="157f9-153">For a more extensive list visit the [Model Builder overview article](../automate-training-with-model-builder.md#scenarios).</span></span>

1. <span data-ttu-id="157f9-154">在 [方案總管]  中，以滑鼠右鍵按一下 *TaxiFarePrediction* 專案，然後選取 [新增]   > [機器學習服務]  。</span><span class="sxs-lookup"><span data-stu-id="157f9-154">In **Solution Explorer**, right-click the *TaxiFarePrediction* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="157f9-155">在模型產生器工具的案例步驟中，請選取 *Price Prediction* 案例。</span><span class="sxs-lookup"><span data-stu-id="157f9-155">In the scenario step of the Model Builder tool, select *Price Prediction* scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="157f9-156">載入資料</span><span class="sxs-lookup"><span data-stu-id="157f9-156">Load the data</span></span>

<span data-ttu-id="157f9-157">模型產生器會接受來自兩個來源的資料：SQL Server 資料庫或本機檔案 CSV 或 TSV 檔案。</span><span class="sxs-lookup"><span data-stu-id="157f9-157">Model Builder accepts data from two sources, a SQL Server database or a local file csv or tsv file.</span></span> <span data-ttu-id="157f9-158">如需資料格式需求的詳細資訊，請瀏覽下列[連結](../how-to-guides/install-model-builder.md#limitations)。</span><span class="sxs-lookup"><span data-stu-id="157f9-158">For more information on data format requirements, visit the following [link](../how-to-guides/install-model-builder.md#limitations).</span></span>

1. <span data-ttu-id="157f9-159">在模型產生器工具的資料步驟中，從資料來源下拉式清單中選取 [檔案]  。</span><span class="sxs-lookup"><span data-stu-id="157f9-159">In the data step of the Model Builder tool, select *File* from the data source dropdown.</span></span>
1. <span data-ttu-id="157f9-160">選取 [選取檔案]  文字方塊旁邊的按鈕，然後使用 [檔案總管] 進行瀏覽，並選取 *Data* 目錄中的 *taxi-fare-test.csv*</span><span class="sxs-lookup"><span data-stu-id="157f9-160">Select the button next to the *Select a file* text box and use File Explorer to browse and select the *taxi-fare-test.csv* in the *Data* directory</span></span>
1. <span data-ttu-id="157f9-161">在 [要預測的標籤或資料行]  下拉式清單中選擇 *fare_amount*，然後巡覽至模型產生器工具的定型步驟。</span><span class="sxs-lookup"><span data-stu-id="157f9-161">Choose *fare_amount* in the *Label or Column to Predict* dropdown and navigate to the train step of the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="157f9-162">將模型定型</span><span class="sxs-lookup"><span data-stu-id="157f9-162">Train the model</span></span>

<span data-ttu-id="157f9-163">在本教學課程中用來定型價格預測模型的機器學習服務工作是迴歸。</span><span class="sxs-lookup"><span data-stu-id="157f9-163">The machine learning task used to train the price prediction model in this tutorial is regression.</span></span> <span data-ttu-id="157f9-164">在模型定型程序的期間，模型產生器會使用不同迴歸演算法及設定來定型不同模型以尋找可最佳執行您資料集的模型。</span><span class="sxs-lookup"><span data-stu-id="157f9-164">During the model training process, Model Builder trains separate models using different regression algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="157f9-165">定型模型所需要的時間會與資料量成比例。</span><span class="sxs-lookup"><span data-stu-id="157f9-165">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="157f9-166">請使用此圖表作為指導，為 `Time to train (seconds)` 欄位選取適當的值：</span><span class="sxs-lookup"><span data-stu-id="157f9-166">Use this chart as guidance to select an adequate value for the `Time to train (seconds)` field:</span></span>

<span data-ttu-id="157f9-167">\*資料集大小</span><span class="sxs-lookup"><span data-stu-id="157f9-167">\*Dataset Size</span></span>  | <span data-ttu-id="157f9-168">資料集型別</span><span class="sxs-lookup"><span data-stu-id="157f9-168">Dataset Type</span></span>       | <span data-ttu-id="157f9-169">Avg.定型時間\*</span><span class="sxs-lookup"><span data-stu-id="157f9-169">Avg. Time to train\*</span></span>
------------- | ------------------ | --------------
<span data-ttu-id="157f9-170">0 - 10 MB</span><span class="sxs-lookup"><span data-stu-id="157f9-170">0 - 10 Mb</span></span>     | <span data-ttu-id="157f9-171">數值和文字</span><span class="sxs-lookup"><span data-stu-id="157f9-171">Numeric and Text</span></span>   | <span data-ttu-id="157f9-172">10 秒</span><span class="sxs-lookup"><span data-stu-id="157f9-172">10 sec</span></span>
<span data-ttu-id="157f9-173">10 - 100 MB</span><span class="sxs-lookup"><span data-stu-id="157f9-173">10 - 100 Mb</span></span>   | <span data-ttu-id="157f9-174">數值和文字</span><span class="sxs-lookup"><span data-stu-id="157f9-174">Numeric and Text</span></span>   | <span data-ttu-id="157f9-175">10 分鐘</span><span class="sxs-lookup"><span data-stu-id="157f9-175">10 min</span></span>
<span data-ttu-id="157f9-176">100 - 500 MB</span><span class="sxs-lookup"><span data-stu-id="157f9-176">100 - 500 Mb</span></span>  | <span data-ttu-id="157f9-177">數值和文字</span><span class="sxs-lookup"><span data-stu-id="157f9-177">Numeric and Text</span></span>   | <span data-ttu-id="157f9-178">30 分鐘</span><span class="sxs-lookup"><span data-stu-id="157f9-178">30 min</span></span>
<span data-ttu-id="157f9-179">500 - 1 GB</span><span class="sxs-lookup"><span data-stu-id="157f9-179">500 - 1 Gb</span></span>    | <span data-ttu-id="157f9-180">數值和文字</span><span class="sxs-lookup"><span data-stu-id="157f9-180">Numeric and Text</span></span>   | <span data-ttu-id="157f9-181">60 分鐘</span><span class="sxs-lookup"><span data-stu-id="157f9-181">60 min</span></span>
<span data-ttu-id="157f9-182">1 GB+</span><span class="sxs-lookup"><span data-stu-id="157f9-182">1 Gb+</span></span>         | <span data-ttu-id="157f9-183">數值和文字</span><span class="sxs-lookup"><span data-stu-id="157f9-183">Numeric and Text</span></span>   | <span data-ttu-id="157f9-184">3 小時以上</span><span class="sxs-lookup"><span data-stu-id="157f9-184">3 hour+</span></span>

1. <span data-ttu-id="157f9-185">因為定型資料檔案超過 10 MB，所以請使用 600 秒 (10 分鐘) 作為 [定型時間 (秒)]  的值。</span><span class="sxs-lookup"><span data-stu-id="157f9-185">Because the training data file is more than 10MB, use 600 seconds (10 minutes) as the value for *Time to train (seconds)*.</span></span>
2. <span data-ttu-id="157f9-186">選取 [開始定型]  。</span><span class="sxs-lookup"><span data-stu-id="157f9-186">Select *Start Training*.</span></span>

<span data-ttu-id="157f9-187">在整個定型程序期間，進度資料會顯示在定型步驟的 `Progress` 區段中。</span><span class="sxs-lookup"><span data-stu-id="157f9-187">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

- <span data-ttu-id="157f9-188">[狀態] 會顯示定型程序的完成狀態。</span><span class="sxs-lookup"><span data-stu-id="157f9-188">Status displays the completion status of the training process.</span></span>
- <span data-ttu-id="157f9-189">[最佳正確性] 會顯示模型產生器到目前為止所找到執行效能最佳模型的正確性。</span><span class="sxs-lookup"><span data-stu-id="157f9-189">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="157f9-190">正確性越高，表示模型針對測試資料的預測越正確。</span><span class="sxs-lookup"><span data-stu-id="157f9-190">Higher accuracy means the model predicted more correctly on test data.</span></span>
- <span data-ttu-id="157f9-191">[最佳演算法] 會顯示模型產生器到目前為止所執行演算法中效能最佳的演算法名稱。</span><span class="sxs-lookup"><span data-stu-id="157f9-191">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
- <span data-ttu-id="157f9-192">[上一個演算法] 會顯示模型產生器最近一次用來定型模型的演算法名稱。</span><span class="sxs-lookup"><span data-stu-id="157f9-192">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

<span data-ttu-id="157f9-193">定型完成後，請巡覽至評估步驟。</span><span class="sxs-lookup"><span data-stu-id="157f9-193">Once training is complete, navigate to the evaluate step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="157f9-194">評估模型</span><span class="sxs-lookup"><span data-stu-id="157f9-194">Evaluate the model</span></span>

<span data-ttu-id="157f9-195">定型步驟之結果將會是具備最佳效能的單一模型。</span><span class="sxs-lookup"><span data-stu-id="157f9-195">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="157f9-196">在模型產生器工具的評估步驟中，輸出區段將會在 [最佳模型]  項目中包含執行效能最佳模型所使用的演算法，並在 [最佳模型品質 (RSquared)]  中包含計量。</span><span class="sxs-lookup"><span data-stu-id="157f9-196">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the *Best Model* entry along with metrics in *Best Model Quality (RSquared)*.</span></span> <span data-ttu-id="157f9-197">此外，還會具備一個摘要表，其中包含前五個模型及其計量。</span><span class="sxs-lookup"><span data-stu-id="157f9-197">Additionally, a summary table containing top five models and their metrics.</span></span> <span data-ttu-id="157f9-198">請瀏覽下列連結來深入了解[評估模型計量](https://docs.microsoft.com/dotnet/machine-learning/resources/metrics)。</span><span class="sxs-lookup"><span data-stu-id="157f9-198">Visit the following link to learn more about [evaluating model metrics](https://docs.microsoft.com/dotnet/machine-learning/resources/metrics).</span></span>

<span data-ttu-id="157f9-199">若您不滿意您的正確性計量，可嘗試及改善模型正確性的一些簡單方法為增加定型模型的時間，或是使用更多資料。</span><span class="sxs-lookup"><span data-stu-id="157f9-199">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span>

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="157f9-200">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="157f9-200">Use the model for predictions</span></span>

<span data-ttu-id="157f9-201">定型程序的結果會建立兩個專案。</span><span class="sxs-lookup"><span data-stu-id="157f9-201">Two projects will be created as a result of the training process.</span></span>

- <span data-ttu-id="157f9-202">TaxiFarePredictionML.ConsoleApp：.NET 主控台應用程式，包含模型定型及使用程式碼的 。</span><span class="sxs-lookup"><span data-stu-id="157f9-202">TaxiFarePredictionML.ConsoleApp: A .NET Console application that contains the model training and consumption code.</span></span>
- <span data-ttu-id="157f9-203">TaxiFarePredictionML.Model：.NET Standard 類別庫，包含定義輸入及輸出模型資料結構描述的資料模型，以及定型期間執行效能最佳模型的保存版本。</span><span class="sxs-lookup"><span data-stu-id="157f9-203">TaxiFarePredictionML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the persisted version of the best performing model during training.</span></span>

1. <span data-ttu-id="157f9-204">在模型產生器工具的程式碼區段中，選取 [新增專案]  來將專案新增到解決方案。</span><span class="sxs-lookup"><span data-stu-id="157f9-204">In the code section of the Model Builder tool, select **Added Projects** to add the projects to the solution.</span></span>
2. <span data-ttu-id="157f9-205">在 [方案總管] 中，以滑鼠右鍵按一下 *TaxiFarePrediction* 專案。</span><span class="sxs-lookup"><span data-stu-id="157f9-205">In solution explorer, right-click the *TaxiFarePrediction* project.</span></span> <span data-ttu-id="157f9-206">然後，選取 [新增] > [現有項目]  。</span><span class="sxs-lookup"><span data-stu-id="157f9-206">Then, select **Add > Existing Item**.</span></span> <span data-ttu-id="157f9-207">針對檔案型別下拉式清單，請選取 `All Files` 來巡覽至 *TaxiFarePredictionML.Model* 專案目錄，然後選取 `MLModel.zip` 檔案。</span><span class="sxs-lookup"><span data-stu-id="157f9-207">For file type drop down, select `All Files`, navigate to the *TaxiFarePredictionML.Model* project directory and select the `MLModel.zip` file.</span></span> <span data-ttu-id="157f9-208">接著以滑鼠右鍵按一下最近新增的 `MLModel.zip` 檔案，然後選取 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="157f9-208">Then right-click the recently added `MLModel.zip` file and select *Properties*.</span></span> <span data-ttu-id="157f9-209">針對 [複製到輸出目錄] 選項，從下拉式清單選取 [有更新時才複製]  。</span><span class="sxs-lookup"><span data-stu-id="157f9-209">For the Copy to Output Directory option, select *Copy if Newer* from the dropdown.</span></span>
3. <span data-ttu-id="157f9-210">以滑鼠右鍵按一下 *TaxiFarePrediction* 專案。</span><span class="sxs-lookup"><span data-stu-id="157f9-210">Right-click *TaxiFarePrediction* project.</span></span> <span data-ttu-id="157f9-211">然後，選取 [新增] > [參考]  。</span><span class="sxs-lookup"><span data-stu-id="157f9-211">Then, **Add > Reference**.</span></span> <span data-ttu-id="157f9-212">選擇 [專案] > [方案]  節點，並從清單選取 *TaxiFarePredictionML.Model* 專案，然後選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="157f9-212">Choose the **Projects > Solution** node and from the list, check the *TaxiFarePredictionML.Model* project and select OK.</span></span>

4. <span data-ttu-id="157f9-213">開啟 *TaxiFarePrediction* 專案中的 *Program.cs* 檔案。</span><span class="sxs-lookup"><span data-stu-id="157f9-213">Open the *Program.cs* file in the *TaxiFarePrediction* project.</span></span>
5. <span data-ttu-id="157f9-214">加入下列 using 陳述式：</span><span class="sxs-lookup"><span data-stu-id="157f9-214">Add the following using statements:</span></span>

    ```csharp
    using System;
    using Microsoft.ML;
    using TaxiFarePredictionML.Model.DataModels;
    ```

6. <span data-ttu-id="157f9-215">將 `ConsumeModel` 方法新增至 `Program` 類別。</span><span class="sxs-lookup"><span data-stu-id="157f9-215">Add the `ConsumeModel` method to the `Program` class.</span></span> <span data-ttu-id="157f9-216">`ConsumeModel` 會根據模型產生器所產生的模型建立 `PredictionEngine`，以針對新資料進行預測，並將它們印出到主控台。</span><span class="sxs-lookup"><span data-stu-id="157f9-216">The `ConsumeModel` will create a `PredictionEngine` based on the model generated by Model Builder to make predictions on new data and print them out to the console.</span></span>

    ```csharp
    static ModelOutput ConsumeModel(ModelInput input)
    {
        // 1. Load the model
        MLContext mlContext = new MLContext();
        ITransformer mlModel = mlContext.Model.Load("MLModel.zip", out var modelInputSchema);

        // 2. Create PredictionEngine
        var predictionEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(mlModel);

        // 3. Use PredictionEngine to use model on input data
        ModelOutput result = predictionEngine.Predict(input);

        // 4. Return prediction result
        return result;
    }
    ```

7. <span data-ttu-id="157f9-217">將下列程式碼新增到 `Main` 方法並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="157f9-217">Add the following code to the `Main` method and run the application.</span></span>

    ```csharp
    // Create sample data
    ModelInput input = new ModelInput()
    {
        Vendor_id = "CMT",
        Rate_code = 1,
        Passenger_count = 1,
        Trip_time_in_secs = 1271,
        Trip_distance = 3.8f,
        Payment_type = "CRD"
    };

    // Make prediction
    ModelOutput prediction = ConsumeModel(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

    <span data-ttu-id="157f9-218">程式所產生的輸出看起來應該會和以下程式碼片段相似：</span><span class="sxs-lookup"><span data-stu-id="157f9-218">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Fare: 16.82245
    ```

<span data-ttu-id="157f9-219">若您需要於稍後在另外一個解決方案中參考所產生的專案，您可以在 `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` 目錄中找到它們。</span><span class="sxs-lookup"><span data-stu-id="157f9-219">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="157f9-220">後續步驟</span><span class="sxs-lookup"><span data-stu-id="157f9-220">Next Steps</span></span>

<span data-ttu-id="157f9-221">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="157f9-221">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="157f9-222">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="157f9-222">Prepare and understand the data</span></span>
> * <span data-ttu-id="157f9-223">選擇案例</span><span class="sxs-lookup"><span data-stu-id="157f9-223">Choose a scenario</span></span>
> * <span data-ttu-id="157f9-224">載入資料</span><span class="sxs-lookup"><span data-stu-id="157f9-224">Load the data</span></span>
> * <span data-ttu-id="157f9-225">將模型定型</span><span class="sxs-lookup"><span data-stu-id="157f9-225">Train the model</span></span>
> * <span data-ttu-id="157f9-226">評估模型</span><span class="sxs-lookup"><span data-stu-id="157f9-226">Evaluate the model</span></span>
> * <span data-ttu-id="157f9-227">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="157f9-227">Use the model for predictions</span></span>

<span data-ttu-id="157f9-228">請前進到下列任何一篇操作說明文章，了解如何部署您的模型。</span><span class="sxs-lookup"><span data-stu-id="157f9-228">Advance to either of the following how-to articles to learn how to deploy your model.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="157f9-229">將模型部署到 Azure Functions</span><span class="sxs-lookup"><span data-stu-id="157f9-229">Deploy a model to Azure Functions</span></span>](../how-to-guides/serve-model-serverless-azure-functions-ml-net.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="157f9-230">將模型部署到 Web API</span><span class="sxs-lookup"><span data-stu-id="157f9-230">Deploy a model to a Web API</span></span>](../how-to-guides/serve-model-web-api-ml-net.md)
