---
title: 教學課程：搭配模型產生器使用迴歸來預測價格
description: 本教學課程會特別示範如何使用 ML.NET 模型產生器來建置迴歸模型以預測紐約市的計程車費用。
author: luisquintanilla
ms.author: luquinta
ms.date: 10/08/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: a851bf3c405d15243bc1457b8c3dff815d072ebe
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180289"
---
# <a name="tutorial-predict-prices-using-regression-with-model-builder"></a><span data-ttu-id="0f1b9-103">教學課程：搭配模型產生器使用迴歸來預測價格</span><span class="sxs-lookup"><span data-stu-id="0f1b9-103">Tutorial: Predict prices using regression with Model Builder</span></span>

<span data-ttu-id="0f1b9-104">瞭解如何使用 ML.NET 模型產生器來建立回歸模型，以預測價格。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-104">Learn how to use ML.NET Model Builder to build a regression model to predict prices.</span></span>  <span data-ttu-id="0f1b9-105">在本教學課程中您所開發 .NET 主控台應用程式會根據紐約的歷史計程車費用資料來預測計程車費用。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-105">The .NET console app that you develop in this tutorial predicts taxi fares based on historical New York taxi fare data.</span></span>

<span data-ttu-id="0f1b9-106">模型建置器價格預測範例可用於任何需要數字預測值的案例。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-106">The Model Builder price prediction template can be used for any scenario requiring a numerical prediction value.</span></span> <span data-ttu-id="0f1b9-107">範例案例包括：房價預測、需求預測及銷售預測。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-107">Example scenarios include: house price prediction, demand prediction, and sales forecasting.</span></span>

<span data-ttu-id="0f1b9-108">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="0f1b9-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="0f1b9-109">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="0f1b9-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="0f1b9-110">選擇案例</span><span class="sxs-lookup"><span data-stu-id="0f1b9-110">Choose a scenario</span></span>
> - <span data-ttu-id="0f1b9-111">載入資料</span><span class="sxs-lookup"><span data-stu-id="0f1b9-111">Load the data</span></span>
> - <span data-ttu-id="0f1b9-112">將模型定型</span><span class="sxs-lookup"><span data-stu-id="0f1b9-112">Train the model</span></span>
> - <span data-ttu-id="0f1b9-113">評估模型</span><span class="sxs-lookup"><span data-stu-id="0f1b9-113">Evaluate the model</span></span>
> - <span data-ttu-id="0f1b9-114">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="0f1b9-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="0f1b9-115">模型產生器目前為預覽版。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-115">Model Builder is currently in Preview.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="0f1b9-116">先決條件</span><span class="sxs-lookup"><span data-stu-id="0f1b9-116">Pre-requisites</span></span>

<span data-ttu-id="0f1b9-117">如需必要條件和安裝指示清單，請瀏覽[模型產生器安裝指南](../how-to-guides/install-model-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-117">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="0f1b9-118">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="0f1b9-118">Create a console application</span></span>

1. <span data-ttu-id="0f1b9-119">建立稱為 "TaxiFarePrediction" 的 **.NET Core 主控台應用程式**。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-119">Create a **.NET Core Console Application** called "TaxiFarePrediction".</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="0f1b9-120">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="0f1b9-120">Prepare and understand the data</span></span>

1. <span data-ttu-id="0f1b9-121">在您專案中建立名為 *Data* 的目錄來儲存資料集檔案。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-121">Create a directory named *Data* in your project to store the data set files.</span></span>

1. <span data-ttu-id="0f1b9-122">用來定型和評估機器學習模型的資料集，最初是來自 NYC TLC 計程車旅程資料集。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-122">The data set used to train and evaluate the machine learning model is originally from the NYC TLC Taxi Trip data set.</span></span>

    1. <span data-ttu-id="0f1b9-123">若要下載該資料集，請瀏覽至 [taxi-fare-train.csv 下載連結](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv)。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-123">To download the data set, navigate to the [taxi-fare-train.csv download link](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/taxi-fare-train.csv).</span></span>

    1. <span data-ttu-id="0f1b9-124">當頁面載入時，以滑鼠右鍵按一下頁面上的任何位置，然後選取 [另存新檔]。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-124">When the page loads, right-click anywhere on the page and select **Save as**.</span></span>

    1. <span data-ttu-id="0f1b9-125">然後使用 [另存新檔] 對話方塊，將檔案儲存於您在上一步所建立的 [Data] 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-125">Use the **Save As Dialog** to save the file in the *Data* folder you created at the previous step.</span></span>

1. <span data-ttu-id="0f1b9-126">在 [方案總管] 中，以滑鼠右鍵按一下 *taxi-fare-train.csv* 檔案，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-126">In **Solution Explorer**, right-click the *taxi-fare-train.csv* file and select **Properties**.</span></span> <span data-ttu-id="0f1b9-127">在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-127">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="0f1b9-128">`taxi-fare-train.csv` 資料集中的每個資料列都包含計程車車程的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-128">Each row in the `taxi-fare-train.csv` data set contains details of trips made by a taxi.</span></span>

1. <span data-ttu-id="0f1b9-129">開啟 **taxi-fare-train.csv** 資料集</span><span class="sxs-lookup"><span data-stu-id="0f1b9-129">Open the **taxi-fare-train.csv** data set</span></span>

    <span data-ttu-id="0f1b9-130">提供的資料集包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="0f1b9-130">The provided data set contains the following columns:</span></span>

    - <span data-ttu-id="0f1b9-131">**vendor_id：** 計程車廠商的識別碼是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-131">**vendor_id:** The ID of the taxi vendor is a feature.</span></span>
    - <span data-ttu-id="0f1b9-132">**rate_code：** 計程車行程的費率類型是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-132">**rate_code:** The rate type of the taxi trip is a feature.</span></span>
    - <span data-ttu-id="0f1b9-133">**passenger_count：** 行程的乘客數目是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-133">**passenger_count:** The number of passengers on the trip is a feature.</span></span>
    - <span data-ttu-id="0f1b9-134">**trip_time_in_secs：** 行程所花費的時間長度。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-134">**trip_time_in_secs:** The amount of time the trip took.</span></span> <span data-ttu-id="0f1b9-135">您想要在行程結束之前預測行程的車資。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-135">You want to predict the fare of the trip before the trip is completed.</span></span> <span data-ttu-id="0f1b9-136">那時，您並不知道行程需要多長的時間。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-136">At that moment you don't know how long the trip would take.</span></span> <span data-ttu-id="0f1b9-137">因此，行程時間不是一項特徵，您將從模型中排除這個資料行。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-137">Thus, the trip time is not a feature and you'll exclude this column from the model.</span></span>
    - <span data-ttu-id="0f1b9-138">**trip_distance：** 行程的距離是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-138">**trip_distance:** The distance of the trip is a feature.</span></span>
    - <span data-ttu-id="0f1b9-139">**payment_type：** 付款方式 (現金或信用卡) 是一項特徵。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-139">**payment_type:** The payment method (cash or credit card) is a feature.</span></span>
    - <span data-ttu-id="0f1b9-140">**fare_amount：** 計程車車資總計是標籤。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-140">**fare_amount:** The total taxi fare paid is the label.</span></span>

<span data-ttu-id="0f1b9-141">`label` 是您希望進行預測的資料行。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-141">The `label` is the column you want to predict.</span></span> <span data-ttu-id="0f1b9-142">執行迴歸工作時，目標是預測數值。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-142">When performing a regression task, the goal is to predict a numerical value.</span></span> <span data-ttu-id="0f1b9-143">在這個價格預測案例中，會預測計程車車程的成本。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-143">In this price prediction scenario, the cost of a taxi ride is being predicted.</span></span> <span data-ttu-id="0f1b9-144">因此，**fare_amount** 為標籤。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-144">Therefore, the **fare_amount** is the label.</span></span> <span data-ttu-id="0f1b9-145">所識別 `features` 則是您提供模型來預測 `label` 的輸入。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-145">The identified `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="0f1b9-146">在此情況下，除了**trip_time_in_secs**以外，其餘的資料行會當做特徵或輸入來預測費用量。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-146">In this case, the rest of the columns with the exception of **trip_time_in_secs** are used as features or inputs to predict the fare amount.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="0f1b9-147">選擇案例</span><span class="sxs-lookup"><span data-stu-id="0f1b9-147">Choose a scenario</span></span>

<span data-ttu-id="0f1b9-148">若要定型您的模型，您需要從模型產生器所提供的可用機器學習服務案例清單中選取。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-148">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="0f1b9-149">在此案例中，案例為 `Price Prediction`。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-149">In this case, the scenario is `Price Prediction`.</span></span>

1. <span data-ttu-id="0f1b9-150">在 [方案總管] 中，以滑鼠右鍵按一下 *TaxiFarePrediction* 專案，然後選取 [新增] > [機器學習服務]。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-150">In **Solution Explorer**, right-click the *TaxiFarePrediction* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="0f1b9-151">在模型產生器工具的案例步驟中，請選取 *Price Prediction* 案例。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-151">In the scenario step of the Model Builder tool, select *Price Prediction* scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="0f1b9-152">載入資料</span><span class="sxs-lookup"><span data-stu-id="0f1b9-152">Load the data</span></span>

<span data-ttu-id="0f1b9-153">模型建立器接受來自兩個來源的資料：SQL Server 資料庫或 CSV 或 TSV 格式的本機檔案。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-153">Model Builder accepts data from two sources, a SQL Server database or a local file in csv or tsv format.</span></span>

1. <span data-ttu-id="0f1b9-154">在模型產生器工具的資料步驟中，從資料來源下拉式清單中選取 [檔案]。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-154">In the data step of the Model Builder tool, select *File* from the data source dropdown.</span></span>
1. <span data-ttu-id="0f1b9-155">選取 [選取檔案] 文字方塊旁邊的按鈕，然後使用 [檔案總管] 進行瀏覽，並選取 *Data* 目錄中的 *taxi-fare-test.csv*</span><span class="sxs-lookup"><span data-stu-id="0f1b9-155">Select the button next to the *Select a file* text box and use File Explorer to browse and select the *taxi-fare-test.csv* in the *Data* directory</span></span>
1. <span data-ttu-id="0f1b9-156">在資料行中選擇 [ *fare_amount* ]*以預測（標籤）* 下拉式清單，然後流覽至模型產生器工具的 [定型] 步驟。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-156">Choose *fare_amount* in the *Column to Predict (Label)* dropdown and navigate to the train step of the Model Builder tool.</span></span>
1. <span data-ttu-id="0f1b9-157">展開 [*輸入資料行（功能）* ] 下拉式清單，並取消核取 [ *trip_time_in_secs* ] 資料行，在定型期間將它排除為一項功能</span><span class="sxs-lookup"><span data-stu-id="0f1b9-157">Expand the *Input Columns (Features)* dropdown and uncheck the *trip_time_in_secs* column to exclude it as a feature during training.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="0f1b9-158">將模型定型</span><span class="sxs-lookup"><span data-stu-id="0f1b9-158">Train the model</span></span>

<span data-ttu-id="0f1b9-159">在本教學課程中用來定型價格預測模型的機器學習服務工作是迴歸。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-159">The machine learning task used to train the price prediction model in this tutorial is regression.</span></span> <span data-ttu-id="0f1b9-160">在模型定型程序的期間，模型產生器會使用不同迴歸演算法及設定來定型不同模型以尋找可最佳執行您資料集的模型。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-160">During the model training process, Model Builder trains separate models using different regression algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="0f1b9-161">定型模型所需要的時間會與資料量成比例。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-161">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="0f1b9-162">「模型產生器」會根據您的資料來源大小，自動選取要定型的預設值 **（秒）** 。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-162">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="0f1b9-163">除非您想要定型較長的時間，否則請保留預設值 [針對*時間進行定型（秒）* ]。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-163">Leave the default value as is for *Time to train (seconds)* unless you prefer to train for a longer time.</span></span>
2. <span data-ttu-id="0f1b9-164">選取 [開始定型]。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-164">Select *Start Training*.</span></span>

<span data-ttu-id="0f1b9-165">在整個定型程序期間，進度資料會顯示在定型步驟的 `Progress` 區段中。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-165">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

- <span data-ttu-id="0f1b9-166">[狀態] 會顯示定型程序的完成狀態。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-166">Status displays the completion status of the training process.</span></span>
- <span data-ttu-id="0f1b9-167">[最佳正確性] 會顯示模型產生器到目前為止所找到執行效能最佳模型的正確性。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-167">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="0f1b9-168">正確性越高，表示模型針對測試資料的預測越正確。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-168">Higher accuracy means the model predicted more correctly on test data.</span></span>
- <span data-ttu-id="0f1b9-169">[最佳演算法] 會顯示模型產生器到目前為止所執行演算法中效能最佳的演算法名稱。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-169">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
- <span data-ttu-id="0f1b9-170">[上一個演算法] 會顯示模型產生器最近一次用來定型模型的演算法名稱。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-170">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

<span data-ttu-id="0f1b9-171">定型完成後，請巡覽至評估步驟。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-171">Once training is complete, navigate to the evaluate step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="0f1b9-172">評估模型</span><span class="sxs-lookup"><span data-stu-id="0f1b9-172">Evaluate the model</span></span>

<span data-ttu-id="0f1b9-173">定型步驟之結果將會是具備最佳效能的單一模型。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-173">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="0f1b9-174">在模型產生器工具的評估步驟中，輸出區段將會在 [最佳模型] 項目中包含執行效能最佳模型所使用的演算法，並在 [最佳模型品質 (RSquared)] 中包含計量。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-174">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the *Best Model* entry along with metrics in *Best Model Quality (RSquared)*.</span></span> <span data-ttu-id="0f1b9-175">此外，還會具備一個摘要表，其中包含前五個模型及其計量。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-175">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="0f1b9-176">若您不滿意您的正確性計量，可嘗試及改善模型正確性的一些簡單方法為增加定型模型的時間，或是使用更多資料。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-176">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="0f1b9-177">如果您覺得滿意，請瀏覽至程式碼步驟。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-177">Otherwise, navigate to the code step.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="0f1b9-178">新增程式碼來進行預測</span><span class="sxs-lookup"><span data-stu-id="0f1b9-178">Add the code to make predictions</span></span>

<span data-ttu-id="0f1b9-179">定型程序的結果會建立兩個專案。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-179">Two projects will be created as a result of the training process.</span></span>

- <span data-ttu-id="0f1b9-180">TaxiFarePredictionML.ConsoleApp：.NET Core 主控台應用程式，其中包含模型定型和範例耗用量程式碼。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-180">TaxiFarePredictionML.ConsoleApp: A .NET Core Console application that contains the model training and sample consumption code.</span></span>
- <span data-ttu-id="0f1b9-181">TaxiFarePredictionML.Model：.NET Standard 類別庫，其中包含定義輸入和輸出模型資料之架構的資料模型、定型期間儲存的最佳執行模型版本，以及稱為 `ConsumeModel` 的 helper 類別進行預測。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-181">TaxiFarePredictionML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data, the saved version of the best performing model during training and a helper class called `ConsumeModel` to make predictions.</span></span>

1. <span data-ttu-id="0f1b9-182">在模型建立器工具的程式碼步驟中，選取 [新增專案] 來將自動產生的專案新增到解決方案。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-182">In the code step of the Model Builder tool, select **Add Projects** to add the auto-generated projects to the solution.</span></span>
1. <span data-ttu-id="0f1b9-183">開啟 *TaxiFarePrediction* 專案中的 *Program.cs* 檔案。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-183">Open the *Program.cs* file in the *TaxiFarePrediction* project.</span></span>
1. <span data-ttu-id="0f1b9-184">新增下列 using 語句，以參考*TaxiFarePredictionML 模型*專案：</span><span class="sxs-lookup"><span data-stu-id="0f1b9-184">Add the following using statement to reference the *TaxiFarePredictionML.Model* project:</span></span>

    ```csharp
    using System;
    using TaxiFarePredictionML.Model;
    ```

1. <span data-ttu-id="0f1b9-185">若要使用模型對新資料進行預測，請在應用程式的 `Main` 方法內，建立 `ModelInput` 類別的新實例。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-185">To make a prediction on new data using the model, create a new instance of the `ModelInput` class inside the `Main` method of your application.</span></span> <span data-ttu-id="0f1b9-186">請注意，費用金額不是輸入的一部分。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-186">Notice that the fare amount is not part of the input.</span></span> <span data-ttu-id="0f1b9-187">這是因為模型會為它產生預測。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-187">This is because the model will generate the prediction for it.</span></span> 

    ```csharp
    // Create sample data
    ModelInput input = new ModelInput()
    {
        Vendor_id = "CMT",
        Rate_code = 1,
        Passenger_count = 1,
        Trip_distance = 3.8f,
        Payment_type = "CRD"
    };
    ```

1. <span data-ttu-id="0f1b9-188">使用 `ConsumeModel` 類別中的 `Predict` 方法。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-188">Use the `Predict` method from the `ConsumeModel` class.</span></span> <span data-ttu-id="0f1b9-189">@No__t-0 方法會載入定型的模型、為模型建立[@no__t 2](xref:Microsoft.ML.PredictionEngine%602) ，並使用它來對新資料進行預測。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-189">The `Predict` method loads the trained model, create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) for the model and uses it to make predictions on new data.</span></span> 

    ```csharp
    // Make prediction
    ModelOutput prediction = ConsumeModel.Predict(input);

    // Print Prediction
    Console.WriteLine($"Predicted Fare: {prediction.Score}");
    Console.ReadKey();
    ```

1. <span data-ttu-id="0f1b9-190">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-190">Run the application.</span></span>

    <span data-ttu-id="0f1b9-191">程式所產生的輸出看起來應該會和以下程式碼片段相似：</span><span class="sxs-lookup"><span data-stu-id="0f1b9-191">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Predicted Fare: 14.96086
    ```

<span data-ttu-id="0f1b9-192">若您需要於稍後在另外一個解決方案中參考所產生的專案，您可以在 `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` 目錄中找到它們。</span><span class="sxs-lookup"><span data-stu-id="0f1b9-192">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0f1b9-193">後續步驟</span><span class="sxs-lookup"><span data-stu-id="0f1b9-193">Next Steps</span></span>

<span data-ttu-id="0f1b9-194">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="0f1b9-194">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="0f1b9-195">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="0f1b9-195">Prepare and understand the data</span></span>
> - <span data-ttu-id="0f1b9-196">選擇案例</span><span class="sxs-lookup"><span data-stu-id="0f1b9-196">Choose a scenario</span></span>
> - <span data-ttu-id="0f1b9-197">載入資料</span><span class="sxs-lookup"><span data-stu-id="0f1b9-197">Load the data</span></span>
> - <span data-ttu-id="0f1b9-198">將模型定型</span><span class="sxs-lookup"><span data-stu-id="0f1b9-198">Train the model</span></span>
> - <span data-ttu-id="0f1b9-199">評估模型</span><span class="sxs-lookup"><span data-stu-id="0f1b9-199">Evaluate the model</span></span>
> - <span data-ttu-id="0f1b9-200">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="0f1b9-200">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="0f1b9-201">其他資源</span><span class="sxs-lookup"><span data-stu-id="0f1b9-201">Additional Resources</span></span>

<span data-ttu-id="0f1b9-202">若要深入了解此教學課程中提及的主題，請瀏覽下列資源：</span><span class="sxs-lookup"><span data-stu-id="0f1b9-202">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="0f1b9-203">模型建立器案例</span><span class="sxs-lookup"><span data-stu-id="0f1b9-203">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="0f1b9-204">迴歸</span><span class="sxs-lookup"><span data-stu-id="0f1b9-204">Regression</span></span>](../resources/glossary.md#regression)
- [<span data-ttu-id="0f1b9-205">迴歸模型計量</span><span class="sxs-lookup"><span data-stu-id="0f1b9-205">Regression Model Metrics</span></span>](../resources/metrics.md#metrics-for-regression)
- <span data-ttu-id="0f1b9-206">[NYC TLC 計程車旅程資料集](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="0f1b9-206">[NYC TLC Taxi Trip data set](http://www.nyc.gov/html/tlc/html/about/trip_record_data.shtml)</span></span>
