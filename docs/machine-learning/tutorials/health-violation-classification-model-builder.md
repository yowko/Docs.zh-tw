---
title: 教程：使用模型產生器對運行狀況違規進行分類
description: 本教程演示如何使用ML.NET模型產生器構建多類分類模型，對三藩市的餐廳健康違規嚴重性進行分類。
author: luisquintanilla
ms.author: luquinta
ms.date: 11/21/2019
ms.topic: tutorial
ms.custom: mvc,mlnet-tooling
ms.openlocfilehash: e94313277a025d482105a6d78b6608d4df442c43
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185849"
---
# <a name="tutorial-classify-the-severity-of-restaurant-health-violations-with-model-builder"></a><span data-ttu-id="cbad8-103">教程：使用模型產生器對餐廳健康違規的嚴重程度進行分類</span><span class="sxs-lookup"><span data-stu-id="cbad8-103">Tutorial: Classify the severity of restaurant health violations with Model Builder</span></span>

<span data-ttu-id="cbad8-104">瞭解如何使用模型產生器構建多類分類模型，以對運行狀況檢查中發現的餐館違規行為的風險級別進行分類。</span><span class="sxs-lookup"><span data-stu-id="cbad8-104">Learn how to build a multiclass classification model using Model Builder to categorize the risk level of restaurant violations found during health inspections.</span></span>

<span data-ttu-id="cbad8-105">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="cbad8-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="cbad8-106">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="cbad8-106">Prepare and understand the data</span></span>
> - <span data-ttu-id="cbad8-107">選擇案例</span><span class="sxs-lookup"><span data-stu-id="cbad8-107">Choose a scenario</span></span>
> - <span data-ttu-id="cbad8-108">從資料庫載入資料</span><span class="sxs-lookup"><span data-stu-id="cbad8-108">Load data from a database</span></span>
> - <span data-ttu-id="cbad8-109">將模型定型</span><span class="sxs-lookup"><span data-stu-id="cbad8-109">Train the model</span></span>
> - <span data-ttu-id="cbad8-110">評估模型</span><span class="sxs-lookup"><span data-stu-id="cbad8-110">Evaluate the model</span></span>
> - <span data-ttu-id="cbad8-111">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="cbad8-111">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="cbad8-112">模型產生器目前為預覽版。</span><span class="sxs-lookup"><span data-stu-id="cbad8-112">Model Builder is currently in Preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cbad8-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="cbad8-113">Prerequisites</span></span>

<span data-ttu-id="cbad8-114">有關先決條件和安裝說明的清單，請訪問[模型產生器安裝指南](../how-to-guides/install-model-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="cbad8-114">For a list of prerequisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="model-builder-multiclass-classification-overview"></a><span data-ttu-id="cbad8-115">模型產生器多類分類概述</span><span class="sxs-lookup"><span data-stu-id="cbad8-115">Model Builder multiclass classification overview</span></span>

<span data-ttu-id="cbad8-116">此示例創建一個 C# .NET Core 主控台應用程式，該應用程式使用使用模型產生器構建的機器學習模型對運行狀況衝突的風險進行分類。</span><span class="sxs-lookup"><span data-stu-id="cbad8-116">This sample creates a C# .NET Core console application that categorizes the risk of health violations using a machine learning model built with Model Builder.</span></span> <span data-ttu-id="cbad8-117">您可以在[dotnet/機器學習示例](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations)GitHub 存儲庫中找到本教程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="cbad8-117">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations) GitHub repository.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="cbad8-118">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="cbad8-118">Create a console application</span></span>

1. <span data-ttu-id="cbad8-119">創建名為"餐廳違規"的**C# .NET 核心主控台應用程式**。</span><span class="sxs-lookup"><span data-stu-id="cbad8-119">Create a **C# .NET Core console application** called "RestaurantViolations".</span></span> <span data-ttu-id="cbad8-120">確保**未選中\*\*\*\*同一目錄中的放置解決方案和專案**（VS 2019），或**選中\*\*\*\*"創建解決方案目錄**"（VS 2017）。</span><span class="sxs-lookup"><span data-stu-id="cbad8-120">Make sure **Place solution and project in the same directory** is **unchecked** (VS 2019), or **Create directory for solution** is **checked** (VS 2017).</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="cbad8-121">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="cbad8-121">Prepare and understand the data</span></span>

> <span data-ttu-id="cbad8-122">用於培訓和評估機器學習模型的資料集最初來自[三藩市公共衛生部餐廳安全評分](https://www.sfdph.org/dph/EH/Food/score/default.asp)。</span><span class="sxs-lookup"><span data-stu-id="cbad8-122">The data set used to train and evaluate the machine learning model is originally from the [San Francisco Department of Public Health Restaurant Safety Scores](https://www.sfdph.org/dph/EH/Food/score/default.asp).</span></span> <span data-ttu-id="cbad8-123">為方便起見，資料集已壓縮為僅包括與訓練模型和進行預測相關的列。</span><span class="sxs-lookup"><span data-stu-id="cbad8-123">For convenience, the dataset has been condensed to only include the columns relevant to train the model and make predictions.</span></span> <span data-ttu-id="cbad8-124">請訪問以下網站，瞭解有關[資料集](https://data.sfgov.org/Health-and-Social-Services/Restaurant-Scores-LIVES-Standard/pyih-qa8i?row_index=0)的資訊。</span><span class="sxs-lookup"><span data-stu-id="cbad8-124">Visit the following website to learn more about the [dataset](https://data.sfgov.org/Health-and-Social-Services/Restaurant-Scores-LIVES-Standard/pyih-qa8i?row_index=0).</span></span>

<span data-ttu-id="cbad8-125">[下載餐廳安全分數資料集](https://github.com/luisquintanilla/machinelearning-samples/raw/AB1608219/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantScores.zip)並解壓縮。</span><span class="sxs-lookup"><span data-stu-id="cbad8-125">[Download the Restaurant Safety Scores dataset](https://github.com/luisquintanilla/machinelearning-samples/raw/AB1608219/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantScores.zip) and unzip it.</span></span>

<span data-ttu-id="cbad8-126">資料集中的每一行都包含有關在衛生部檢查期間觀察到的違規行為的資訊，以及對這些違規行為對公眾健康和安全構成的威脅的風險評估。</span><span class="sxs-lookup"><span data-stu-id="cbad8-126">Each row in the dataset contains information regarding violations observed during an inspection from the Health Department and a risk assessment of the threat those violations present to public health and safety.</span></span>

| <span data-ttu-id="cbad8-127">檢測類型</span><span class="sxs-lookup"><span data-stu-id="cbad8-127">InspectionType</span></span> | <span data-ttu-id="cbad8-128">違規描述</span><span class="sxs-lookup"><span data-stu-id="cbad8-128">ViolationDescription</span></span> | <span data-ttu-id="cbad8-129">風險類別</span><span class="sxs-lookup"><span data-stu-id="cbad8-129">RiskCategory</span></span> |
| --- | --- | --- |
| <span data-ttu-id="cbad8-130">常式 - 計畫外</span><span class="sxs-lookup"><span data-stu-id="cbad8-130">Routine - Unscheduled</span></span> | <span data-ttu-id="cbad8-131">未充分清潔或消毒食品接觸表面</span><span class="sxs-lookup"><span data-stu-id="cbad8-131">Inadequately cleaned or sanitized food contact surfaces</span></span> | <span data-ttu-id="cbad8-132">中等風險</span><span class="sxs-lookup"><span data-stu-id="cbad8-132">Moderate Risk</span></span> |
| <span data-ttu-id="cbad8-133">新擁有權</span><span class="sxs-lookup"><span data-stu-id="cbad8-133">New Ownership</span></span> | <span data-ttu-id="cbad8-134">高風險害蟲侵擾</span><span class="sxs-lookup"><span data-stu-id="cbad8-134">High risk vermin infestation</span></span> | <span data-ttu-id="cbad8-135">高風險</span><span class="sxs-lookup"><span data-stu-id="cbad8-135">High Risk</span></span> |
| <span data-ttu-id="cbad8-136">常式 - 計畫外</span><span class="sxs-lookup"><span data-stu-id="cbad8-136">Routine - Unscheduled</span></span> | <span data-ttu-id="cbad8-137">擦拭未清潔或未正確存放或消毒器不足的布</span><span class="sxs-lookup"><span data-stu-id="cbad8-137">Wiping cloths not clean or properly stored or inadequate sanitizer</span></span> | <span data-ttu-id="cbad8-138">低風險</span><span class="sxs-lookup"><span data-stu-id="cbad8-138">Low Risk</span></span> |

- <span data-ttu-id="cbad8-139">**檢驗類型**：檢驗類型。</span><span class="sxs-lookup"><span data-stu-id="cbad8-139">**InspectionType**: the type of inspection.</span></span> <span data-ttu-id="cbad8-140">這可以是新機構的首次檢查、例行檢查、投訴檢查和許多其他類型。</span><span class="sxs-lookup"><span data-stu-id="cbad8-140">This can either be a first-time inspection for a new establishment, a routine inspection, a complaint inspection, and many other types.</span></span>
- <span data-ttu-id="cbad8-141">**違規說明**：檢查中發現的違規行為的描述。</span><span class="sxs-lookup"><span data-stu-id="cbad8-141">**ViolationDescription**: a description of the violation found during inspection.</span></span>
- <span data-ttu-id="cbad8-142">**風險類別**：違規行為對公眾健康和安全構成的風險嚴重性。</span><span class="sxs-lookup"><span data-stu-id="cbad8-142">**RiskCategory**: the risk severity a violation poses to public health and safety.</span></span>

<span data-ttu-id="cbad8-143">`label` 是您希望進行預測的資料行。</span><span class="sxs-lookup"><span data-stu-id="cbad8-143">The `label` is the column you want to predict.</span></span> <span data-ttu-id="cbad8-144">執行分類任務時，目標是分配類別（文本或數位）。</span><span class="sxs-lookup"><span data-stu-id="cbad8-144">When performing a classification task, the goal is to assign a category (text or numerical).</span></span> <span data-ttu-id="cbad8-145">在此分類方案中，將指定衝突的嚴重性為低、中或高風險的值。</span><span class="sxs-lookup"><span data-stu-id="cbad8-145">In this classification scenario, the severity of the violation is assigned the value of low, moderate, or high risk.</span></span> <span data-ttu-id="cbad8-146">因此，**風險類別**是標籤。</span><span class="sxs-lookup"><span data-stu-id="cbad8-146">Therefore, the **RiskCategory** is the label.</span></span> <span data-ttu-id="cbad8-147">是`features`您為模型提供用於預測 的`label`輸入。</span><span class="sxs-lookup"><span data-stu-id="cbad8-147">The `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="cbad8-148">在這種情況下，**檢查類型**和**違規描述**用作用於預測**風險類別**的功能或輸入。</span><span class="sxs-lookup"><span data-stu-id="cbad8-148">In this case, the **InspectionType** and **ViolationDescription** are used as features or inputs to predict the **RiskCategory**.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="cbad8-149">選擇案例</span><span class="sxs-lookup"><span data-stu-id="cbad8-149">Choose a scenario</span></span>

![視覺化工作室中的模型產生器嚮導](./media/sentiment-analysis-model-builder/model-builder-screen.png)

<span data-ttu-id="cbad8-151">要訓練模型，請從模型產生器提供的可用機器學習方案清單中選擇。</span><span class="sxs-lookup"><span data-stu-id="cbad8-151">To train your model, select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="cbad8-152">在這種情況下，方案是*問題分類*。</span><span class="sxs-lookup"><span data-stu-id="cbad8-152">In this case, the scenario is *Issue Classification*.</span></span>

1. <span data-ttu-id="cbad8-153">在**解決方案資源管理器中**，按右鍵 *"餐廳違規"* 專案，然後選擇"**添加** > **機器學習**"。</span><span class="sxs-lookup"><span data-stu-id="cbad8-153">In **Solution Explorer**, right-click the *RestaurantViolations* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="cbad8-154">對於此示例，方案是多類分類。</span><span class="sxs-lookup"><span data-stu-id="cbad8-154">For this sample, the scenario is multiclass classification.</span></span> <span data-ttu-id="cbad8-155">在模型產生器*的方案*步驟中，選擇**問題分類**方案。</span><span class="sxs-lookup"><span data-stu-id="cbad8-155">In the *Scenario* step of Model Builder, select the **Issue Classification** scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="cbad8-156">載入資料</span><span class="sxs-lookup"><span data-stu-id="cbad8-156">Load the data</span></span>

<span data-ttu-id="cbad8-157">模型產生器接受來自 SQL Server 資料庫或本地檔的資料`csv`，`tsv`其格式或格式。</span><span class="sxs-lookup"><span data-stu-id="cbad8-157">Model Builder accepts data from a SQL Server database or a local file in `csv` or `tsv` format.</span></span>

1. <span data-ttu-id="cbad8-158">在模型產生器工具的資料步驟中，從資料來源下拉清單中選擇**SQL Server。**</span><span class="sxs-lookup"><span data-stu-id="cbad8-158">In the data step of the Model Builder tool, select **SQL Server** from the data source dropdown.</span></span>
1. <span data-ttu-id="cbad8-159">選擇"連接到 SQL **Server 資料庫"文本**框旁邊的按鈕。</span><span class="sxs-lookup"><span data-stu-id="cbad8-159">Select the button next to the **Connect to SQL Server database** text box.</span></span>
    1. <span data-ttu-id="cbad8-160">在 **"選擇資料"** 對話方塊中，選擇**Microsoft SQL 伺服器資料庫檔案**。</span><span class="sxs-lookup"><span data-stu-id="cbad8-160">In the **Choose Data** dialog, select **Microsoft SQL Server Database File**.</span></span>
    1. <span data-ttu-id="cbad8-161">取消選中 **"始終使用此選擇**"核取方塊，然後選擇"**繼續**"。</span><span class="sxs-lookup"><span data-stu-id="cbad8-161">Uncheck the **Always use this selection** checkbox and select **Continue**.</span></span>
    1. <span data-ttu-id="cbad8-162">在 **"連接屬性**"對話方塊中，選擇 **"流覽**"並選擇下載的*餐館分數.mdf*檔。</span><span class="sxs-lookup"><span data-stu-id="cbad8-162">In the **Connection Properties** dialog, select **Browse** and select the downloaded *RestaurantScores.mdf* file.</span></span>
    1. <span data-ttu-id="cbad8-163">選取 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cbad8-163">Select **OK**.</span></span>
1. <span data-ttu-id="cbad8-164">從**表名稱**下拉清單中選擇 **"衝突**"。</span><span class="sxs-lookup"><span data-stu-id="cbad8-164">Choose **Violations** from the **Table Name** dropdown.</span></span>
1. <span data-ttu-id="cbad8-165">在"列"中選擇 **"風險類別\*\*\*\*"以預測（標籤）** 下拉清單。</span><span class="sxs-lookup"><span data-stu-id="cbad8-165">Choose **RiskCategory** in the **Column to Predict (Label)** dropdown.</span></span>
1. <span data-ttu-id="cbad8-166">在**輸入列（功能）** 下拉下下下下下，保留預設列選擇、**檢查類型**和**違規描述**。</span><span class="sxs-lookup"><span data-stu-id="cbad8-166">Leave the default column selections, **InspectionType** and **ViolationDescription**, checked in the **Input Columns (Features)** dropdown.</span></span>
1. <span data-ttu-id="cbad8-167">選擇 **"訓練"** 連結以移動到模型產生器中的下一步。</span><span class="sxs-lookup"><span data-stu-id="cbad8-167">Select the **Train** link to move to the next step in Model Builder.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="cbad8-168">將模型定型</span><span class="sxs-lookup"><span data-stu-id="cbad8-168">Train the model</span></span>

<span data-ttu-id="cbad8-169">本教程中用於訓練問題分類模型的機器學習任務是多類分類。</span><span class="sxs-lookup"><span data-stu-id="cbad8-169">The machine learning task used to train the issue classification model in this tutorial is multiclass classification.</span></span> <span data-ttu-id="cbad8-170">在模型培訓過程中，模型產生器使用不同的多類分類演算法和設置訓練單獨的模型，以查找資料集的最佳模型。</span><span class="sxs-lookup"><span data-stu-id="cbad8-170">During the model training process, Model Builder trains separate models using different multiclass classification algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="cbad8-171">模型訓練所需的時間與資料量成正比。</span><span class="sxs-lookup"><span data-stu-id="cbad8-171">The time required for the model to train is proportional to the amount of data.</span></span> <span data-ttu-id="cbad8-172">模型產生器根據資料來源的大小自動選擇**時間訓練時間（秒）** 的預設值。</span><span class="sxs-lookup"><span data-stu-id="cbad8-172">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="cbad8-173">儘管模型產生器將**訓練時間（秒）** 的值設置為 10 秒，但將其增加到 30 秒。</span><span class="sxs-lookup"><span data-stu-id="cbad8-173">Although Model Builder sets the value of **Time to train (seconds)** to 10 seconds, increase it to 30 seconds.</span></span> <span data-ttu-id="cbad8-174">經過更長時間的培訓，模型構建器可以探索更多演算法和參數組合，以查找最佳模型。</span><span class="sxs-lookup"><span data-stu-id="cbad8-174">Training for a longer period of time allows Model Builder to explore a larger number of algorithms and combination of parameters in search of the best model.</span></span>
1. <span data-ttu-id="cbad8-175">選取 [開始定型]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="cbad8-175">Select **Start Training**.</span></span>

    <span data-ttu-id="cbad8-176">在整個定型程序期間，進度資料會顯示在定型步驟的 `Progress` 區段中。</span><span class="sxs-lookup"><span data-stu-id="cbad8-176">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

    - <span data-ttu-id="cbad8-177">**狀態**顯示培訓過程的完成狀態。</span><span class="sxs-lookup"><span data-stu-id="cbad8-177">**Status** displays the completion status of the training process.</span></span>
    - <span data-ttu-id="cbad8-178">**最佳精度** 顯示模型產生器迄今找到的最佳模型的準確性。</span><span class="sxs-lookup"><span data-stu-id="cbad8-178">**Best accuracy** displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="cbad8-179">正確性越高，表示模型針對測試資料的預測越正確。</span><span class="sxs-lookup"><span data-stu-id="cbad8-179">Higher accuracy means the model predicted more correctly on test data.</span></span>
    - <span data-ttu-id="cbad8-180">**最佳演算法** 顯示模型產生器迄今找到的表現最好的演算法的名稱。</span><span class="sxs-lookup"><span data-stu-id="cbad8-180">**Best algorithm** displays the name of the best-performing algorithm found by Model Builder so far.</span></span>
    - <span data-ttu-id="cbad8-181">**最後一個演算法** 顯示模型產生器最近用於訓練模型的演算法的名稱。</span><span class="sxs-lookup"><span data-stu-id="cbad8-181">**Last algorithm** displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

1. <span data-ttu-id="cbad8-182">培訓完成後，選擇 **"評估**"連結以轉到下一步。</span><span class="sxs-lookup"><span data-stu-id="cbad8-182">Once training is complete, select the **Evaluate** link to move to the next step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="cbad8-183">評估模型</span><span class="sxs-lookup"><span data-stu-id="cbad8-183">Evaluate the model</span></span>

<span data-ttu-id="cbad8-184">訓練步驟的結果是性能最好的模型。</span><span class="sxs-lookup"><span data-stu-id="cbad8-184">The result of the training step is the one model that had the best performance.</span></span> <span data-ttu-id="cbad8-185">在模型產生器的計算步驟中，輸出部分包含**最佳模型**條目中性能最佳的模型使用的演算法以及**最佳模型精度**中的指標。</span><span class="sxs-lookup"><span data-stu-id="cbad8-185">In the evaluate step of Model Builder, the output section contains the algorithm used by the best performing model in the **Best Model** entry along with metrics in **Best Model Accuracy**.</span></span> <span data-ttu-id="cbad8-186">此外，還會顯示一個摘要表，其中包含最多五個已流覽的模型及其指標。</span><span class="sxs-lookup"><span data-stu-id="cbad8-186">Additionally, a summary table containing up to five models that were explored and their metrics is displayed.</span></span>

<span data-ttu-id="cbad8-187">如果您對準確性指標不滿意，則嘗試提高模型準確性的一些簡單方法是增加訓練模型或使用更多資料的時間。</span><span class="sxs-lookup"><span data-stu-id="cbad8-187">If you're not satisfied with your accuracy metrics, some easy ways to try to improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="cbad8-188">否則，選擇要移動到模型產生器中的最後一步**的代碼**連結。</span><span class="sxs-lookup"><span data-stu-id="cbad8-188">Otherwise, select the **code** link to move to the final step in Model Builder.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="cbad8-189">新增程式碼來進行預測</span><span class="sxs-lookup"><span data-stu-id="cbad8-189">Add the code to make predictions</span></span>

<span data-ttu-id="cbad8-190">培訓過程的結果創建了兩個專案。</span><span class="sxs-lookup"><span data-stu-id="cbad8-190">Two projects are created as a result of the training process.</span></span>

- <span data-ttu-id="cbad8-191">餐廳違規ML.ConsoleApp：包含模型培訓和示例消耗代碼的 C# .NET 核心主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="cbad8-191">RestaurantViolationsML.ConsoleApp: A C# .NET Core Console application that contains the model training and sample consumption code.</span></span>
- <span data-ttu-id="cbad8-192">餐廳違規ML.Model：一個.NET標準類庫，其中包含定義輸入和輸出模型資料架構的資料模型、培訓期間最佳性能模型的保存版本以及調用`ConsumeModel`用於進行預測的説明器類。</span><span class="sxs-lookup"><span data-stu-id="cbad8-192">RestaurantViolationsML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data, the saved version of the best performing model during training, and a helper class called `ConsumeModel` to make predictions.</span></span>

1. <span data-ttu-id="cbad8-193">在模型產生器的代碼步驟中，選擇 **"添加專案"** 以將自動生成的專案添加到解決方案中。</span><span class="sxs-lookup"><span data-stu-id="cbad8-193">In the code step of Model Builder, select **Add Projects** to add the autogenerated projects to the solution.</span></span>
1. <span data-ttu-id="cbad8-194">打開 *"餐廳違規"* 專案中*的Program.cs*檔。</span><span class="sxs-lookup"><span data-stu-id="cbad8-194">Open the *Program.cs* file in the *RestaurantViolations* project.</span></span>
1. <span data-ttu-id="cbad8-195">添加以下使用語句以引用*餐廳違規ML.模型*專案：</span><span class="sxs-lookup"><span data-stu-id="cbad8-195">Add the following using statement to reference the *RestaurantViolationsML.Model* project:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L2)]

1. <span data-ttu-id="cbad8-196">要使用模型對新資料進行預測，請在應用程式`ModelInput``Main`的方法內創建類的新實例。</span><span class="sxs-lookup"><span data-stu-id="cbad8-196">To make a prediction on new data using the model, create a new instance of the `ModelInput` class inside the `Main` method of your application.</span></span> <span data-ttu-id="cbad8-197">請注意，風險類別不是輸入的一部分。</span><span class="sxs-lookup"><span data-stu-id="cbad8-197">Notice that the risk category is not part of the input.</span></span> <span data-ttu-id="cbad8-198">這是因為模型為其生成預測。</span><span class="sxs-lookup"><span data-stu-id="cbad8-198">This is because the model generates the prediction for it.</span></span>

    [!code-csharp [TestData](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L11-L15)]

1. <span data-ttu-id="cbad8-199">使用`Predict`類 中`ConsumeModel`的方法。</span><span class="sxs-lookup"><span data-stu-id="cbad8-199">Use the `Predict` method from the `ConsumeModel` class.</span></span> <span data-ttu-id="cbad8-200">該方法`Predict`載入訓練的模型，為模型創建[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)。</span><span class="sxs-lookup"><span data-stu-id="cbad8-200">The `Predict` method loads the trained model, creates a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) for the model, and uses it to make predictions on new data.</span></span>

    [!code-csharp [Prediction](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L17-L24)]

1. <span data-ttu-id="cbad8-201">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="cbad8-201">Run the application.</span></span>

    <span data-ttu-id="cbad8-202">程式所產生的輸出看起來應該會和以下程式碼片段相似：</span><span class="sxs-lookup"><span data-stu-id="cbad8-202">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Inspection Type: Complaint
    Violation Description: Inadequate sewage or wastewater disposal
    Risk Category: Moderate Risk
    ```

<span data-ttu-id="cbad8-203">若您需要於稍後在另外一個解決方案中參考所產生的專案，您可以在 `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` 目錄中找到它們。</span><span class="sxs-lookup"><span data-stu-id="cbad8-203">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

<span data-ttu-id="cbad8-204">恭喜！</span><span class="sxs-lookup"><span data-stu-id="cbad8-204">Congratulations!</span></span> <span data-ttu-id="cbad8-205">您已成功構建機器學習模型，以便使用模型產生器對健康違規的風險進行分類。</span><span class="sxs-lookup"><span data-stu-id="cbad8-205">You've successfully built a machine learning model to categorize the risk of health violations using Model Builder.</span></span> <span data-ttu-id="cbad8-206">您可以在[dotnet/機器學習示例](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations)GitHub 存儲庫中找到本教程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="cbad8-206">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations) GitHub repository.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="cbad8-207">其他資源</span><span class="sxs-lookup"><span data-stu-id="cbad8-207">Additional resources</span></span>

<span data-ttu-id="cbad8-208">若要深入了解此教學課程中提及的主題，請瀏覽下列資源：</span><span class="sxs-lookup"><span data-stu-id="cbad8-208">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="cbad8-209">模型建立器案例</span><span class="sxs-lookup"><span data-stu-id="cbad8-209">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="cbad8-210">多類分類</span><span class="sxs-lookup"><span data-stu-id="cbad8-210">Multiclass Classification</span></span>](../resources/glossary.md#multiclass-classification)
- [<span data-ttu-id="cbad8-211">多類分類模型指標</span><span class="sxs-lookup"><span data-stu-id="cbad8-211">Multiclass Classification Model Metrics</span></span>](../resources/metrics.md#evaluation-metrics-for-multi-class-classification)
