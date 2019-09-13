---
title: 搭配模型產生器使用迴歸來預測價格
description: 本教學課程會特別示範如何使用 ML.NET 模型產生器來建置迴歸模型以預測紐約市的計程車費用。
author: luisquintanilla
ms.author: luquinta
ms.date: 07/15/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: bc1dacdad436cc5384bca4bbce224acc18d69201
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929436"
---
# <a name="predict-prices-using-regression-with-model-builder"></a><span data-ttu-id="6ff53-103">搭配模型產生器使用迴歸來預測價格</span><span class="sxs-lookup"><span data-stu-id="6ff53-103">Predict prices using regression with Model Builder</span></span>

<span data-ttu-id="6ff53-104">了解如何使用 ML.NET 模型建立器建置迴歸模型來預測價格。</span><span class="sxs-lookup"><span data-stu-id="6ff53-104">Learn how to use ML.NET Model Builder to build a regression model() to predict prices.</span></span>  <span data-ttu-id="6ff53-105">在本教學課程中您所開發 .NET 主控台應用程式會根據紐約的歷史計程車費用資料來預測計程車費用。</span><span class="sxs-lookup"><span data-stu-id="6ff53-105">The .NET console app that you develop in this tutorial predicts taxi fares based on historical New York taxi fare data.</span></span>

<span data-ttu-id="6ff53-106">模型建置器價格預測範例可用於任何需要數字預測值的案例。</span><span class="sxs-lookup"><span data-stu-id="6ff53-106">The Model Builder price prediction template can be used for any scenario requiring a numerical prediction value.</span></span> <span data-ttu-id="6ff53-107">範例案例包括：房價預測、需求預測及銷售預測。</span><span class="sxs-lookup"><span data-stu-id="6ff53-107">Example scenarios include: house price prediction, demand prediction, and sales forecasting.</span></span>

<span data-ttu-id="6ff53-108">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="6ff53-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="6ff53-109">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="6ff53-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="6ff53-110">選擇案例</span><span class="sxs-lookup"><span data-stu-id="6ff53-110">Choose a scenario</span></span>
> - <span data-ttu-id="6ff53-111">載入資料</span><span class="sxs-lookup"><span data-stu-id="6ff53-111">Load the data</span></span>
> - <span data-ttu-id="6ff53-112">將模型定型</span><span class="sxs-lookup"><span data-stu-id="6ff53-112">Train the model</span></span>
> - <span data-ttu-id="6ff53-113">評估模型</span><span class="sxs-lookup"><span data-stu-id="6ff53-113">Evaluate the model</span></span>
> - <span data-ttu-id="6ff53-114">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="6ff53-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="6ff53-115">模型產生器目前為預覽版。</span><span class="sxs-lookup"><span data-stu-id="6ff53-115">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="6ff53-116">先決條件</span><span class="sxs-lookup"><span data-stu-id="6ff53-116">Pre-requisites</span></span>

<span data-ttu-id="6ff53-117">如需必要條件和安裝指示清單，請瀏覽[模型產生器安裝指南](../how-to-guides/install-model-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="6ff53-117">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="6ff53-118">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="6ff53-118">Create a console application</span></span>

1. <span data-ttu-id="6ff53-119">建立稱為 "TaxiFarePrediction" 的 **.NET Core 主控台應用程式**。</span><span class="sxs-lookup"><span data-stu-id="6ff53-119">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="6ff53-120">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="6ff53-120">Prepare and understand the data</span></span>

1. <span data-ttu-id="6ff53-121">在您專案中建立名為 *Data* 的目錄來儲存資料集檔案。</span><span class="sxs-lookup"><span data-stu-id="6ff53-121">Create a directory named *Data* in your project to store the data set files.</span></span>

1. <span data-ttu-id="6ff53-122">用來定型和評估機器學習模型的資料集，最初是來自 NYC TLC 計程車旅程資料集。</span><span class="sxs-lookup"><span data-stu-id="6ff53-122">The data set used to train and evaluate the machine learning model is originally from the NYC TLC Taxi Trip data set.</span></span>

    <span data-ttu-id="6ff53-123">若要下載該資料集，請瀏覽至 [taxi-fare-train.csv 下載連結](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv)。</span><span class="sxs-lookup"><span data-stu-id="6ff53-123">To download the data set, navigate to the [taxi-fare-train.csv download link](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span></span>

    <span data-ttu-id="6ff53-124">當頁面載入時，以滑鼠右鍵按一下頁面上的任何位置，然後選取 [另存新檔]。</span><span class="sxs-lookup"><span data-stu-id="6ff53-124">When the page loads, right-click anywhere on the page and select **Save as**.</span></span>

    <span data-ttu-id="6ff53-125">然後使用 [另存新檔] 對話方塊，將檔案儲存於您在上一步所建立的 [Data] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="6ff53-125">Use the **Save As Dialog** to save the file in the *Data* folder you created at the previous step.</span></span>

1. <span data-ttu-id="6ff53-126">在 [方案總管] 中，以滑鼠右鍵按一下 *taxi-fare-train.csv* 檔案，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="6ff53-126">In **Solution Explorer**, right-click the *taxi-fare-train.csv* file and select **Properties**.</span></span> <span data-ttu-id="6ff53-127">在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。</span><span class="sxs-lookup"><span data-stu-id="6ff53-127">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="6ff53-128">`taxi-fare-train.csv` 資料集中的每個資料列都包含計程車車程的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="6ff53-128">Each row in the `taxi-fare-train.csv` data set contains details of trips made by a taxi.</span></span>

1. <span data-ttu-id="6ff53-129">開啟 **taxi-fare-train.csv** 資料集</span><span class="sxs-lookup"><span data-stu-id="6ff53-129">Open the **taxi-fare-train.csv** data set</span></span>

    <span data-ttu-id="6ff53-130">提供的資料集包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="6ff53-130">The provided data set contains the following columns:</span></span>

    - <span data-ttu-id="6ff53-131">**vendor_id：** 計程車廠商的識別碼是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="6ff53-131">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
    - <span data-ttu-id="6ff53-132">**rate_code：** 計程車行程的費率類型是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="6ff53-132">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
    - <span data-ttu-id="6ff53-133">**passenger_count：** 行程的乘客數目是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="6ff53-133">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
    - <span data-ttu-id="6ff53-134">**trip_time_in_secs：** 行程所花費的時間長度。</span><span class="sxs-lookup"><span data-stu-id="6ff53-134">**trip_time_in_secs:** The amount of time the trip took.</span></span>
    - <span data-ttu-id="6ff53-135">**trip_distance：** 行程的距離是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="6ff53-135">**trip_distance:** The distance of the trip is a feature.</span></span>
    - <span data-ttu-id="6ff53-136">**payment_type：** 付款方式 (現金或信用卡) 是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="6ff53-136">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
    - <span data-ttu-id="6ff53-137">**fare_amount：** 計程車車資總計是標籤。</span><span class="sxs-lookup"><span data-stu-id="6ff53-137">**fare_amount:** The total taxi fare paid is the label.</span></span>

<span data-ttu-id="6ff53-138">`label` 是您希望進行預測的資料行。</span><span class="sxs-lookup"><span data-stu-id="6ff53-138">The `label` is the column you want to predict.</span></span> <span data-ttu-id="6ff53-139">執行迴歸工作時，目標是預測數值。</span><span class="sxs-lookup"><span data-stu-id="6ff53-139">When performing a regression task, the goal is to predict a numerical value.</span></span> <span data-ttu-id="6ff53-140">在這個價格預測案例中，會預測計程車車程的成本。</span><span class="sxs-lookup"><span data-stu-id="6ff53-140">In this price prediction scenario, the cost of a taxi ride is being predicted.</span></span> <span data-ttu-id="6ff53-141">因此，**fare_amount** 為標籤。</span><span class="sxs-lookup"><span data-stu-id="6ff53-141">Therefore, the **fare_amount** is the label.</span></span> <span data-ttu-id="6ff53-142">所識別 `features` 則是您提供模型來預測 `label` 的輸入。</span><span class="sxs-lookup"><span data-stu-id="6ff53-142">The identified `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="6ff53-143">在此案例中，其餘資料行都會用來作為特徵或輸入，來預測費用金額。</span><span class="sxs-lookup"><span data-stu-id="6ff53-143">In this case, the rest of the columns are used as features or inputs to predict the fare amount.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="6ff53-144">選擇案例</span><span class="sxs-lookup"><span data-stu-id="6ff53-144">Choose a scenario</span></span>

<span data-ttu-id="6ff53-145">若要定型您的模型，您需要從模型產生器所提供的可用機器學習服務案例清單中選取。</span><span class="sxs-lookup"><span data-stu-id="6ff53-145">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="6ff53-146">在此案例中，案例為 `Price Prediction`。</span><span class="sxs-lookup"><span data-stu-id="6ff53-146">In this case, the scenario is `Price Prediction`.</span></span>

1. <span data-ttu-id="6ff53-147">在 [方案總管] 中，以滑鼠右鍵按一下 *TaxiFarePrediction* 專案，然後選取 [新增] > [機器學習服務]。</span><span class="sxs-lookup"><span data-stu-id="6ff53-147">In **Solution Explorer**, right-click the *TaxiFarePrediction* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="6ff53-148">在模型產生器工具的案例步驟中，請選取 *Price Prediction* 案例。</span><span class="sxs-lookup"><span data-stu-id="6ff53-148">In the scenario step of the Model Builder tool, select *Price Prediction* scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="6ff53-149">載入資料</span><span class="sxs-lookup"><span data-stu-id="6ff53-149">Load the data</span></span>

<span data-ttu-id="6ff53-150">模型建立器接受來自兩個來源的資料：SQL Server 資料庫或 CSV 或 TSV 格式的本機檔案。</span><span class="sxs-lookup"><span data-stu-id="6ff53-150">Model Builder accepts data from two sources, a SQL Server database or a local file in csv or tsv format.</span></span>

1. <span data-ttu-id="6ff53-151">在模型產生器工具的資料步驟中，從資料來源下拉式清單中選取 [檔案]。</span><span class="sxs-lookup"><span data-stu-id="6ff53-151">In the data step of the Model Builder tool, select *File* from the data source dropdown.</span></span>
1. <span data-ttu-id="6ff53-152">選取 [選取檔案] 文字方塊旁邊的按鈕，然後使用 [檔案總管] 進行瀏覽，並選取 *Data* 目錄中的 *taxi-fare-test.csv*</span><span class="sxs-lookup"><span data-stu-id="6ff53-152">Select the button next to the *Select a file* text box and use File Explorer to browse and select the *taxi-fare-test.csv* in the *Data* directory</span></span>
1. <span data-ttu-id="6ff53-153">在 [要預測的標籤或資料行] 下拉式清單中選擇 *fare_amount*，然後巡覽至模型產生器工具的定型步驟。</span><span class="sxs-lookup"><span data-stu-id="6ff53-153">Choose *fare_amount* in the *Label or Column to Predict* dropdown and navigate to the train step of the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="6ff53-154">將模型定型</span><span class="sxs-lookup"><span data-stu-id="6ff53-154">Train the model</span></span>

<span data-ttu-id="6ff53-155">在本教學課程中用來定型價格預測模型的機器學習服務工作是迴歸。</span><span class="sxs-lookup"><span data-stu-id="6ff53-155">The machine learning task used to train the price prediction model in this tutorial is regression.</span></span> <span data-ttu-id="6ff53-156">在模型定型程序的期間，模型產生器會使用不同迴歸演算法及設定來定型不同模型以尋找可最佳執行您資料集的模型。</span><span class="sxs-lookup"><span data-stu-id="6ff53-156">During the model training process, Model Builder trains separate models using different regression algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="6ff53-157">定型模型所需要的時間會與資料量成比例。</span><span class="sxs-lookup"><span data-stu-id="6ff53-157">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="6ff53-158">請使用此圖表作為指導，為 `Time to train (seconds)` 欄位選取適當的值：</span><span class="sxs-lookup"><span data-stu-id="6ff53-158">Use this chart as guidance to select an adequate value for the `Time to train (seconds)` field:</span></span>

<span data-ttu-id="6ff53-159">\*資料集大小</span><span class="sxs-lookup"><span data-stu-id="6ff53-159">\*Dataset Size</span></span>  | <span data-ttu-id="6ff53-160">資料集型別</span><span class="sxs-lookup"><span data-stu-id="6ff53-160">Dataset Type</span></span>       | <span data-ttu-id="6ff53-161">Avg.定型時間\*</span><span class="sxs-lookup"><span data-stu-id="6ff53-161">Avg. Time to train\*</span></span>
------------- | ------------------ | --------------
<span data-ttu-id="6ff53-162">0 - 10 MB</span><span class="sxs-lookup"><span data-stu-id="6ff53-162">0 - 10 Mb</span></span>     | <span data-ttu-id="6ff53-163">數值和文字</span><span class="sxs-lookup"><span data-stu-id="6ff53-163">Numeric and Text</span></span>   | <span data-ttu-id="6ff53-164">10 秒</span><span class="sxs-lookup"><span data-stu-id="6ff53-164">10 sec</span></span>
<span data-ttu-id="6ff53-165">10 - 100 MB</span><span class="sxs-lookup"><span data-stu-id="6ff53-165">10 - 100 Mb</span></span>   | <span data-ttu-id="6ff53-166">數值和文字</span><span class="sxs-lookup"><span data-stu-id="6ff53-166">Numeric and Text</span></span>   | <span data-ttu-id="6ff53-167">10 分鐘</span><span class="sxs-lookup"><span data-stu-id="6ff53-167">10 min</span></span>
<span data-ttu-id="6ff53-168">100 - 500 MB</span><span class="sxs-lookup"><span data-stu-id="6ff53-168">100 - 500 Mb</span></span>  | <span data-ttu-id="6ff53-169">數值和文字</span><span class="sxs-lookup"><span data-stu-id="6ff53-169">Numeric and Text</span></span>   | <span data-ttu-id="6ff53-170">30 分鐘</span><span class="sxs-lookup"><span data-stu-id="6ff53-170">30 min</span></span>
<span data-ttu-id="6ff53-171">500 - 1 GB</span><span class="sxs-lookup"><span data-stu-id="6ff53-171">500 - 1 Gb</span></span>    | <span data-ttu-id="6ff53-172">數值和文字</span><span class="sxs-lookup"><span data-stu-id="6ff53-172">Numeric and Text</span></span>   | <span data-ttu-id="6ff53-173">60 分鐘</span><span class="sxs-lookup"><span data-stu-id="6ff53-173">60 min</span></span>
<span data-ttu-id="6ff53-174">1 GB+</span><span class="sxs-lookup"><span data-stu-id="6ff53-174">1 Gb+</span></span>         | <span data-ttu-id="6ff53-175">數值和文字</span><span class="sxs-lookup"><span data-stu-id="6ff53-175">Numeric and Text</span></span>   | <span data-ttu-id="6ff53-176">3 小時以上</span><span class="sxs-lookup"><span data-stu-id="6ff53-176">3 hour+</span></span>

1. <span data-ttu-id="6ff53-177">因為定型資料檔案超過 10 MB，所以請使用 600 秒 (10 分鐘) 作為 [定型時間 (秒)] 的值。</span><span class="sxs-lookup"><span data-stu-id="6ff53-177">Because the training data file is more than 10MB, use 600 seconds (10 minutes) as the value for *Time to train (seconds)*.</span></span>
2. <span data-ttu-id="6ff53-178">選取 [開始定型]。</span><span class="sxs-lookup"><span data-stu-id="6ff53-178">Select *Start Training*.</span></span>

<span data-ttu-id="6ff53-179">在整個定型程序期間，進度資料會顯示在定型步驟的 `Progress` 區段中。</span><span class="sxs-lookup"><span data-stu-id="6ff53-179">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

- <span data-ttu-id="6ff53-180">[狀態] 會顯示定型程序的完成狀態。</span><span class="sxs-lookup"><span data-stu-id="6ff53-180">Status displays the completion status of the training process.</span></span>
- <span data-ttu-id="6ff53-181">[最佳正確性] 會顯示模型產生器到目前為止所找到執行效能最佳模型的正確性。</span><span class="sxs-lookup"><span data-stu-id="6ff53-181">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="6ff53-182">正確性越高，表示模型針對測試資料的預測越正確。</span><span class="sxs-lookup"><span data-stu-id="6ff53-182">Higher accuracy means the model predicted more correctly on test data.</span></span>
- <span data-ttu-id="6ff53-183">[最佳演算法] 會顯示模型產生器到目前為止所執行演算法中效能最佳的演算法名稱。</span><span class="sxs-lookup"><span data-stu-id="6ff53-183">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
- <span data-ttu-id="6ff53-184">[上一個演算法] 會顯示模型產生器最近一次用來定型模型的演算法名稱。</span><span class="sxs-lookup"><span data-stu-id="6ff53-184">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

<span data-ttu-id="6ff53-185">定型完成後，請巡覽至評估步驟。</span><span class="sxs-lookup"><span data-stu-id="6ff53-185">Once training is complete, navigate to the evaluate step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="6ff53-186">評估模型</span><span class="sxs-lookup"><span data-stu-id="6ff53-186">Evaluate the model</span></span>

<span data-ttu-id="6ff53-187">定型步驟之結果將會是具備最佳效能的單一模型。</span><span class="sxs-lookup"><span data-stu-id="6ff53-187">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="6ff53-188">在模型產生器工具的評估步驟中，輸出區段將會在 [最佳模型] 項目中包含執行效能最佳模型所使用的演算法，並在 [最佳模型品質 (RSquared)] 中包含計量。</span><span class="sxs-lookup"><span data-stu-id="6ff53-188">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the *Best Model* entry along with metrics in *Best Model Quality (RSquared)*.</span></span> <span data-ttu-id="6ff53-189">此外，還會具備一個摘要表，其中包含前五個模型及其計量。</span><span class="sxs-lookup"><span data-stu-id="6ff53-189">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="6ff53-190">若您不滿意您的正確性計量，可嘗試及改善模型正確性的一些簡單方法為增加定型模型的時間，或是使用更多資料。</span><span class="sxs-lookup"><span data-stu-id="6ff53-190">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="6ff53-191">如果您覺得滿意，請瀏覽至程式碼步驟。</span><span class="sxs-lookup"><span data-stu-id="6ff53-191">Otherwise, navigate to the code step.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="6ff53-192">新增程式碼來進行預測</span><span class="sxs-lookup"><span data-stu-id="6ff53-192">Add the code to make predictions</span></span>

<span data-ttu-id="6ff53-193">定型程序的結果會建立兩個專案。</span><span class="sxs-lookup"><span data-stu-id="6ff53-193">Two projects will be created as a result of the training process.</span></span>

- <span data-ttu-id="6ff53-194">TaxiFarePredictionML.ConsoleApp：包含模型定型及使用程式碼的 .NET Core 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="6ff53-194">TaxiFarePredictionML.ConsoleApp: A .NET Core Console application that contains the model training and consumption code.</span></span>
- <span data-ttu-id="6ff53-195">TaxiFarePredictionML.Model：.NET Standard 類別庫，包含定義輸入及輸出模型資料結構描述的資料模型，以及定型期間執行效能最佳模型的保存版本。</span><span class="sxs-lookup"><span data-stu-id="6ff53-195">TaxiFarePredictionML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the persisted version of the best performing model during training.</span></span>

1. <span data-ttu-id="6ff53-196">在模型建立器工具的程式碼步驟中，選取 [新增專案] 來將自動產生的專案新增到解決方案。</span><span class="sxs-lookup"><span data-stu-id="6ff53-196">In the code step of the Model Builder tool, select **Add Projects** to add the auto-generated projects to the solution.</span></span>
1. <span data-ttu-id="6ff53-197">以滑鼠右鍵按一下 *TaxiFarePrediction* 專案。</span><span class="sxs-lookup"><span data-stu-id="6ff53-197">Right-click *TaxiFarePrediction* project.</span></span> <span data-ttu-id="6ff53-198">然後，選取 [新增] > [參考]。</span><span class="sxs-lookup"><span data-stu-id="6ff53-198">Then, **Add > Reference**.</span></span> <span data-ttu-id="6ff53-199">選擇 [專案] > [方案] 節點，並從清單選取 *TaxiFarePredictionML.Model* 專案，然後選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="6ff53-199">Choose the **Projects > Solution** node and from the list, check the *TaxiFarePredictionML.Model* project and select OK.</span></span>
1. <span data-ttu-id="6ff53-200">開啟 *TaxiFarePrediction* 專案中的 *Program.cs* 檔案。</span><span class="sxs-lookup"><span data-stu-id="6ff53-200">Open the *Program.cs* file in the *TaxiFarePrediction* project.</span></span>
1. <span data-ttu-id="6ff53-201">新增下列 using 陳述式，以參考 *Microsoft.ML* NuGet 套件與 *TaxiFarePredictionML.Model* 專案：</span><span class="sxs-lookup"><span data-stu-id="6ff53-201">Add the following using statements to reference the *Microsoft.ML* NuGet package and *TaxiFarePredictionML.Model* project:</span></span>

    ```csharp
    using System;
    using Microsoft.ML;
    using TaxiFarePredictionML.Model.DataModels;
    ```

1. <span data-ttu-id="6ff53-202">將 `ConsumeModel` 方法新增至 `Program` 類別。</span><span class="sxs-lookup"><span data-stu-id="6ff53-202">Add the `ConsumeModel` method to the `Program` class.</span></span>

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

    <span data-ttu-id="6ff53-203">`ConsumeModel` 會載入已定型的模型、從模型建立 [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)，並使用它來對新資料進行預測。</span><span class="sxs-lookup"><span data-stu-id="6ff53-203">The `ConsumeModel` will load the trained model, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) for the model and use it to make predictions on new data.</span></span>

1. <span data-ttu-id="6ff53-204">若要使用模型對新資料進行預測，請建立 `ModelInput` 類別的新執行個體，並使用 `ConsumeModel` 方法。</span><span class="sxs-lookup"><span data-stu-id="6ff53-204">To make a prediction on new data using the model, create a new instance of the `ModelInput` class and use the `ConsumeModel` method.</span></span> <span data-ttu-id="6ff53-205">請注意，費用金額不是輸入的一部分。</span><span class="sxs-lookup"><span data-stu-id="6ff53-205">Notice that the fare amount is not part of the input.</span></span> <span data-ttu-id="6ff53-206">這是因為模型會為它產生預測。</span><span class="sxs-lookup"><span data-stu-id="6ff53-206">This is because the model will generate the prediction for it.</span></span> <span data-ttu-id="6ff53-207">將下列程式碼新增到 `Main` 方法並執行應用程式</span><span class="sxs-lookup"><span data-stu-id="6ff53-207">Add the following code to the `Main` method and run the application</span></span>

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

    <span data-ttu-id="6ff53-208">程式所產生的輸出看起來應該會和以下程式碼片段相似：</span><span class="sxs-lookup"><span data-stu-id="6ff53-208">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Fare: 16.82245
    ```

<span data-ttu-id="6ff53-209">若您需要於稍後在另外一個解決方案中參考所產生的專案，您可以在 `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` 目錄中找到它們。</span><span class="sxs-lookup"><span data-stu-id="6ff53-209">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6ff53-210">後續步驟</span><span class="sxs-lookup"><span data-stu-id="6ff53-210">Next Steps</span></span>

<span data-ttu-id="6ff53-211">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="6ff53-211">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="6ff53-212">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="6ff53-212">Prepare and understand the data</span></span>
> - <span data-ttu-id="6ff53-213">選擇案例</span><span class="sxs-lookup"><span data-stu-id="6ff53-213">Choose a scenario</span></span>
> - <span data-ttu-id="6ff53-214">載入資料</span><span class="sxs-lookup"><span data-stu-id="6ff53-214">Load the data</span></span>
> - <span data-ttu-id="6ff53-215">將模型定型</span><span class="sxs-lookup"><span data-stu-id="6ff53-215">Train the model</span></span>
> - <span data-ttu-id="6ff53-216">評估模型</span><span class="sxs-lookup"><span data-stu-id="6ff53-216">Evaluate the model</span></span>
> - <span data-ttu-id="6ff53-217">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="6ff53-217">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="6ff53-218">其他資源</span><span class="sxs-lookup"><span data-stu-id="6ff53-218">Additional Resources</span></span>

<span data-ttu-id="6ff53-219">若要深入了解此教學課程中提及的主題，請瀏覽下列資源：</span><span class="sxs-lookup"><span data-stu-id="6ff53-219">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="6ff53-220">模型建立器案例</span><span class="sxs-lookup"><span data-stu-id="6ff53-220">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="6ff53-221">迴歸</span><span class="sxs-lookup"><span data-stu-id="6ff53-221">Regression</span></span>](../resources/glossary.md#regression)
- [<span data-ttu-id="6ff53-222">迴歸模型計量</span><span class="sxs-lookup"><span data-stu-id="6ff53-222">Regression Model Metrics</span></span>](../resources/metrics.md#metrics-for-regression)
- <span data-ttu-id="6ff53-223">[NYC TLC 計程車旅程資料集](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="6ff53-223">[NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)</span></span>
