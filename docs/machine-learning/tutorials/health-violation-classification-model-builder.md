---
title: 教學課程：使用模型產生器分類健全狀況違規
description: 本教學課程說明如何使用 ML.NET 模型產生器來建立多元分類模型，以分類三藩市中的餐廳健康情況違規嚴重性。
author: luisquintanilla
ms.author: luquinta
ms.date: 10/30/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: cbe20183d317ac6fe39a937e1cfa8a5e3df81b74
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977214"
---
# <a name="tutorial-classify-the-severity-of-restaurant-health-violations-with-model-builder"></a><span data-ttu-id="401fe-103">教學課程：使用模型產生器分類餐廳健康情況違規的嚴重性</span><span class="sxs-lookup"><span data-stu-id="401fe-103">Tutorial: Classify the severity of restaurant health violations with Model Builder</span></span>

<span data-ttu-id="401fe-104">瞭解如何使用模型產生器來建立多元分類模型，以將在健康情況檢查期間找到的餐廳違規風險層級分類。</span><span class="sxs-lookup"><span data-stu-id="401fe-104">Learn how to build a multiclass classification model using Model Builder to categorize the risk level of restaurant violations found during health inspections.</span></span>

<span data-ttu-id="401fe-105">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="401fe-105">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="401fe-106">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="401fe-106">Prepare and understand the data</span></span>
> - <span data-ttu-id="401fe-107">選擇案例</span><span class="sxs-lookup"><span data-stu-id="401fe-107">Choose a scenario</span></span>
> - <span data-ttu-id="401fe-108">從資料庫載入資料</span><span class="sxs-lookup"><span data-stu-id="401fe-108">Load data from a database</span></span>
> - <span data-ttu-id="401fe-109">將模型定型</span><span class="sxs-lookup"><span data-stu-id="401fe-109">Train the model</span></span>
> - <span data-ttu-id="401fe-110">評估模型</span><span class="sxs-lookup"><span data-stu-id="401fe-110">Evaluate the model</span></span>
> - <span data-ttu-id="401fe-111">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="401fe-111">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="401fe-112">模型建立器目前為預覽版。</span><span class="sxs-lookup"><span data-stu-id="401fe-112">Model Builder is currently in Preview.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="401fe-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="401fe-113">Prerequisites</span></span>

<span data-ttu-id="401fe-114">如需必要條件和安裝指示的清單，請造訪[模型產生器安裝指南](../how-to-guides/install-model-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="401fe-114">For a list of prerequisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="model-builder-multiclass-classification-overview"></a><span data-ttu-id="401fe-115">模型產生器多元分類總覽</span><span class="sxs-lookup"><span data-stu-id="401fe-115">Model Builder multiclass classification overview</span></span>

<span data-ttu-id="401fe-116">這個範例會建立C# .net Core 主控台應用程式，以使用以模型產生器建立的機器學習模型，將健康情況違規的風險分類。</span><span class="sxs-lookup"><span data-stu-id="401fe-116">This sample creates a C# .NET Core console application that categorizes the risk of health violations using a machine learning model built with Model Builder.</span></span> <span data-ttu-id="401fe-117">您可以在[dotnet/machinelearning 範例](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations)GitHub 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="401fe-117">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations) GitHub repository.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="401fe-118">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="401fe-118">Create a console application</span></span>

1. <span data-ttu-id="401fe-119">建立名為 "RestaurantViolations" 的 **C# .net Core 主控台應用程式**。</span><span class="sxs-lookup"><span data-stu-id="401fe-119">Create a **C# .NET Core console application** called "RestaurantViolations".</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="401fe-120">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="401fe-120">Prepare and understand the data</span></span>

> <span data-ttu-id="401fe-121">用來定型和評估機器學習模型的資料集，原本是由[三藩市部門的公用健康餐廳安全分數所組成](https://www.sfdph.org/dph/EH/Food/score/default.asp)。</span><span class="sxs-lookup"><span data-stu-id="401fe-121">The data set used to train and evaluate the machine learning model is originally from the [San Francisco Department of Public Health Restaurant Safety Scores](https://www.sfdph.org/dph/EH/Food/score/default.asp).</span></span> <span data-ttu-id="401fe-122">為了方便起見，資料集已壓縮成隻包含與定型模型和進行預測相關的資料行。</span><span class="sxs-lookup"><span data-stu-id="401fe-122">For convenience, the dataset has been condensed to only include the columns relevant to train the model and make predictions.</span></span> <span data-ttu-id="401fe-123">流覽下列網站以深入瞭解[資料集](https://data.sfgov.org/Health-and-Social-Services/Restaurant-Scores-LIVES-Standard/pyih-qa8i?row_index=0)。</span><span class="sxs-lookup"><span data-stu-id="401fe-123">Visit the following website to learn more about the [dataset](https://data.sfgov.org/Health-and-Social-Services/Restaurant-Scores-LIVES-Standard/pyih-qa8i?row_index=0).</span></span>

<span data-ttu-id="401fe-124">[下載餐廳安全分數資料集](https://github.com/luisquintanilla/machinelearning-samples/raw/AB1608219/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantScores.zip)，並將它解壓縮。</span><span class="sxs-lookup"><span data-stu-id="401fe-124">[Download the Restaurant Safety Scores dataset](https://github.com/luisquintanilla/machinelearning-samples/raw/AB1608219/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantScores.zip) and unzip it.</span></span>

<span data-ttu-id="401fe-125">Dataset 中的每個資料列都包含在健康情況部門進行檢查時所觀察到之違規的相關資訊，以及對公開健康狀態和安全性的違規威脅的風險評估。</span><span class="sxs-lookup"><span data-stu-id="401fe-125">Each row in the dataset contains information regarding violations observed during an inspection from the Health Department and a risk assessment of the threat those violations present to public health and safety.</span></span>

| <span data-ttu-id="401fe-126">InspectionType</span><span class="sxs-lookup"><span data-stu-id="401fe-126">InspectionType</span></span> | <span data-ttu-id="401fe-127">ViolationDescription</span><span class="sxs-lookup"><span data-stu-id="401fe-127">ViolationDescription</span></span> | <span data-ttu-id="401fe-128">RiskCategory</span><span class="sxs-lookup"><span data-stu-id="401fe-128">RiskCategory</span></span> |
| --- | --- | --- |
| <span data-ttu-id="401fe-129">例行排程</span><span class="sxs-lookup"><span data-stu-id="401fe-129">Routine - Unscheduled</span></span> | <span data-ttu-id="401fe-130">未充分清除或清理的食物連絡人表面</span><span class="sxs-lookup"><span data-stu-id="401fe-130">Inadequately cleaned or sanitized food contact surfaces</span></span> | <span data-ttu-id="401fe-131">中度風險</span><span class="sxs-lookup"><span data-stu-id="401fe-131">Moderate Risk</span></span> |
| <span data-ttu-id="401fe-132">新擁有權</span><span class="sxs-lookup"><span data-stu-id="401fe-132">New Ownership</span></span> | <span data-ttu-id="401fe-133">高風險 vermin 感染</span><span class="sxs-lookup"><span data-stu-id="401fe-133">High risk vermin infestation</span></span> | <span data-ttu-id="401fe-134">高風險</span><span class="sxs-lookup"><span data-stu-id="401fe-134">High Risk</span></span> |
| <span data-ttu-id="401fe-135">例行排程</span><span class="sxs-lookup"><span data-stu-id="401fe-135">Routine - Unscheduled</span></span> | <span data-ttu-id="401fe-136">抹除換喪服未清除或正確儲存或 sanitizer 不足</span><span class="sxs-lookup"><span data-stu-id="401fe-136">Wiping cloths not clean or properly stored or inadequate sanitizer</span></span> | <span data-ttu-id="401fe-137">低風險</span><span class="sxs-lookup"><span data-stu-id="401fe-137">Low Risk</span></span> |

- <span data-ttu-id="401fe-138">**InspectionType**：檢查的類型。</span><span class="sxs-lookup"><span data-stu-id="401fe-138">**InspectionType**: the type of inspection.</span></span> <span data-ttu-id="401fe-139">這可以是新建立的第一次檢查，也就是例行的檢查、抱怨檢查，以及許多其他類型。</span><span class="sxs-lookup"><span data-stu-id="401fe-139">This can either be a first-time inspection for a new establishment, a routine inspection, a complaint inspection, and many other types.</span></span>
- <span data-ttu-id="401fe-140">**ViolationDescription**：在檢查期間找到之違規的描述。</span><span class="sxs-lookup"><span data-stu-id="401fe-140">**ViolationDescription**: a description of the violation found during inspection.</span></span>
- <span data-ttu-id="401fe-141">**RiskCategory**：違反的風險嚴重性會造成公用的健全狀況和安全。</span><span class="sxs-lookup"><span data-stu-id="401fe-141">**RiskCategory**: the risk severity a violation poses to public health and safety.</span></span>

<span data-ttu-id="401fe-142">`label` 是您希望進行預測的資料行。</span><span class="sxs-lookup"><span data-stu-id="401fe-142">The `label` is the column you want to predict.</span></span> <span data-ttu-id="401fe-143">執行分類工作時，目標是要指派分類（文字或數位）。</span><span class="sxs-lookup"><span data-stu-id="401fe-143">When performing a classification task, the goal is to assign a category (text or numerical).</span></span> <span data-ttu-id="401fe-144">在此分類案例中，違規的嚴重性會指派為 [低]、[中] 或 [高] 風險的值。</span><span class="sxs-lookup"><span data-stu-id="401fe-144">In this classification scenario, the severity of the violation is assigned the value of low, moderate, or high risk.</span></span> <span data-ttu-id="401fe-145">因此， **RiskCategory**是標籤。</span><span class="sxs-lookup"><span data-stu-id="401fe-145">Therefore, the **RiskCategory** is the label.</span></span> <span data-ttu-id="401fe-146">`features` 是您為模型提供預測 `label`的輸入。</span><span class="sxs-lookup"><span data-stu-id="401fe-146">The `features` are the inputs you give the model to predict the `label`.</span></span> <span data-ttu-id="401fe-147">在此情況下， **InspectionType**和**ViolationDescription**會當做功能或輸入來預測**RiskCategory**。</span><span class="sxs-lookup"><span data-stu-id="401fe-147">In this case, the **InspectionType** and **ViolationDescription** are used as features or inputs to predict the **RiskCategory**.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="401fe-148">選擇案例</span><span class="sxs-lookup"><span data-stu-id="401fe-148">Choose a scenario</span></span>

![Visual Studio 中的模型產生器 wizard](./media/sentiment-analysis-model-builder/model-builder-screen.png)

<span data-ttu-id="401fe-150">若要定型您的模型，請從模型產生器所提供的可用機器學習服務案例清單中選取。</span><span class="sxs-lookup"><span data-stu-id="401fe-150">To train your model, select from the list of available machine learning scenarios provided by Model Builder.</span></span> <span data-ttu-id="401fe-151">在此情況下，案例是「*問題分類*」。</span><span class="sxs-lookup"><span data-stu-id="401fe-151">In this case, the scenario is *Issue Classification*.</span></span>

1. <span data-ttu-id="401fe-152">在**方案總管**中，以滑鼠右鍵按一下*RestaurantViolations*專案，然後選取 [**新增** > **Machine Learning**]。</span><span class="sxs-lookup"><span data-stu-id="401fe-152">In **Solution Explorer**, right-click the *RestaurantViolations* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="401fe-153">在此範例中，案例是多元分類。</span><span class="sxs-lookup"><span data-stu-id="401fe-153">For this sample, the scenario is multiclass classification.</span></span> <span data-ttu-id="401fe-154">在模型產生器的*情節*步驟中，選取 [**問題分類**] 案例。</span><span class="sxs-lookup"><span data-stu-id="401fe-154">In the *Scenario* step of Model Builder, select the **Issue Classification** scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="401fe-155">載入資料</span><span class="sxs-lookup"><span data-stu-id="401fe-155">Load the data</span></span>

<span data-ttu-id="401fe-156">模型產生器會以 `csv` 或 `tsv` 格式，接受來自 SQL Server 資料庫或本機檔案的資料。</span><span class="sxs-lookup"><span data-stu-id="401fe-156">Model Builder accepts data from a SQL Server database or a local file in `csv` or `tsv` format.</span></span>

1. <span data-ttu-id="401fe-157">在模型產生器工具的 [資料] 步驟中，從 [資料來源] 下拉式清單中選取 [ **SQL Server** ]。</span><span class="sxs-lookup"><span data-stu-id="401fe-157">In the data step of the Model Builder tool, select **SQL Server** from the data source dropdown.</span></span>
1. <span data-ttu-id="401fe-158">選取 [**連接到 SQL Server 資料庫**] 文字方塊旁的按鈕。</span><span class="sxs-lookup"><span data-stu-id="401fe-158">Select the button next to the **Connect to SQL Server database** text box.</span></span>
    1. <span data-ttu-id="401fe-159">在 [**選擇資料**] 對話方塊中，選取 [ **Microsoft SQL Server 資料庫**檔案]。</span><span class="sxs-lookup"><span data-stu-id="401fe-159">In the **Choose Data** dialog, select **Microsoft SQL Server Database File**.</span></span>
    1. <span data-ttu-id="401fe-160">取消核取 [**一律使用此選取專案**] 核取方塊，然後選取 [**繼續**]。</span><span class="sxs-lookup"><span data-stu-id="401fe-160">Uncheck the **Always use this selection** checkbox and select **Continue**.</span></span>
    1. <span data-ttu-id="401fe-161">在 [**連接屬性**] 對話方塊中，選取 [**流覽]** ，然後選取已下載的*RestaurantScores .mdf*檔案。</span><span class="sxs-lookup"><span data-stu-id="401fe-161">In the **Connection Properties** dialog, select **Browse** and select the downloaded *RestaurantScores.mdf* file.</span></span>
    1. <span data-ttu-id="401fe-162">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="401fe-162">Select **OK**.</span></span>
1. <span data-ttu-id="401fe-163">從 [**資料表名稱**] 下拉式清單中選擇 [**違規**]。</span><span class="sxs-lookup"><span data-stu-id="401fe-163">Choose **Violations** from the **Table Name** dropdown.</span></span>
1. <span data-ttu-id="401fe-164">在 [**要預測的資料行（標籤）** ] 下拉式清單中選擇 [ **RiskCategory** ]。</span><span class="sxs-lookup"><span data-stu-id="401fe-164">Choose **RiskCategory** in the **Column to Predict (Label)** dropdown.</span></span>
1. <span data-ttu-id="401fe-165">保留 [**輸入資料行（功能）** ] 下拉式清單中選取的預設資料行 [ **InspectionType** ] 和 [ **ViolationDescription**]。</span><span class="sxs-lookup"><span data-stu-id="401fe-165">Leave the default column selections, **InspectionType** and **ViolationDescription**, checked in the **Input Columns (Features)** dropdown.</span></span>
1. <span data-ttu-id="401fe-166">選取 [**定型**] 連結，以移至 [模型產生器] 中的下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="401fe-166">Select the **Train** link to move to the next step in Model Builder.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="401fe-167">將模型定型</span><span class="sxs-lookup"><span data-stu-id="401fe-167">Train the model</span></span>

<span data-ttu-id="401fe-168">在本教學課程中用來定型問題分類模型的機器學習工作是多元分類。</span><span class="sxs-lookup"><span data-stu-id="401fe-168">The machine learning task used to train the issue classification model in this tutorial is multiclass classification.</span></span> <span data-ttu-id="401fe-169">在模型定型程式期間，模型產生器會使用不同的多元分類演算法和設定來訓練不同的模型，以尋找資料集最佳的執行模型。</span><span class="sxs-lookup"><span data-stu-id="401fe-169">During the model training process, Model Builder trains separate models using different multiclass classification algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="401fe-170">定型模型所需的時間與資料量成正比。</span><span class="sxs-lookup"><span data-stu-id="401fe-170">The time required for the model to train is proportional to the amount of data.</span></span> <span data-ttu-id="401fe-171">「模型產生器」會根據您的資料來源大小，自動選取要定型的預設值 **（秒）** 。</span><span class="sxs-lookup"><span data-stu-id="401fe-171">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="401fe-172">雖然模型產生器會將 [**要定型的時間] 值（秒）** 設定為10秒，但將它增加為30秒。</span><span class="sxs-lookup"><span data-stu-id="401fe-172">Although Model Builder sets the value of **Time to train (seconds)** to 10 seconds, increase it to 30 seconds.</span></span> <span data-ttu-id="401fe-173">定型一段較長的時間，可讓模型產生器在搜尋最佳模型時，探索更多的演算法和參數組合。</span><span class="sxs-lookup"><span data-stu-id="401fe-173">Training for a longer period of time allows Model Builder to explore a larger number of algorithms and combination of parameters in search of the best model.</span></span>
1. <span data-ttu-id="401fe-174">選取 [開始定型]。</span><span class="sxs-lookup"><span data-stu-id="401fe-174">Select **Start Training**.</span></span>

    <span data-ttu-id="401fe-175">在整個定型程序期間，進度資料會顯示在定型步驟的 `Progress` 區段中。</span><span class="sxs-lookup"><span data-stu-id="401fe-175">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

    - <span data-ttu-id="401fe-176">**狀態**顯示定型進程的完成狀態。</span><span class="sxs-lookup"><span data-stu-id="401fe-176">**Status** displays the completion status of the training process.</span></span>
    - <span data-ttu-id="401fe-177">**最佳精確度** 會顯示目前為止模型產生器所找到之最佳執行模型的精確度。</span><span class="sxs-lookup"><span data-stu-id="401fe-177">**Best accuracy** displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="401fe-178">正確性越高，表示模型針對測試資料的預測越正確。</span><span class="sxs-lookup"><span data-stu-id="401fe-178">Higher accuracy means the model predicted more correctly on test data.</span></span>
    - <span data-ttu-id="401fe-179">**最佳演算法** 會顯示目前為止模型產生器所找到之最佳演算法的名稱。</span><span class="sxs-lookup"><span data-stu-id="401fe-179">**Best algorithm** displays the name of the best-performing algorithm found by Model Builder so far.</span></span>
    - <span data-ttu-id="401fe-180">[**上次演算法]**  顯示模型產生器最近用來定型模型的演算法名稱。</span><span class="sxs-lookup"><span data-stu-id="401fe-180">**Last algorithm** displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

1. <span data-ttu-id="401fe-181">定型完成後，請選取 [**評估**] 連結以移至下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="401fe-181">Once training is complete, select the **Evaluate** link to move to the next step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="401fe-182">評估模型</span><span class="sxs-lookup"><span data-stu-id="401fe-182">Evaluate the model</span></span>

<span data-ttu-id="401fe-183">定型步驟的結果是一個具有最佳效能的模型。</span><span class="sxs-lookup"><span data-stu-id="401fe-183">The result of the training step is the one model that had the best performance.</span></span> <span data-ttu-id="401fe-184">在模型產生器的評估步驟中，[輸出] 區段包含最佳**模型**專案中最佳執行模型所使用的演算法，以及最佳**模型精確度**中的計量。</span><span class="sxs-lookup"><span data-stu-id="401fe-184">In the evaluate step of Model Builder, the output section contains the algorithm used by the best performing model in the **Best Model** entry along with metrics in **Best Model Accuracy**.</span></span> <span data-ttu-id="401fe-185">此外，摘要資料表包含最多五個已探索到的模型，而且會顯示其計量。</span><span class="sxs-lookup"><span data-stu-id="401fe-185">Additionally, a summary table containing up to five models that were explored and their metrics is displayed.</span></span>

<span data-ttu-id="401fe-186">如果您不滿意精確度計量，嘗試改善模型精確度的一些簡單方法，就是增加定型模型或使用更多資料的時間量。</span><span class="sxs-lookup"><span data-stu-id="401fe-186">If you're not satisfied with your accuracy metrics, some easy ways to try to improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="401fe-187">否則，請選取 [程式**代碼**] 連結，以移至模型產生器中的最後一個步驟。</span><span class="sxs-lookup"><span data-stu-id="401fe-187">Otherwise, select the **code** link to move to the final step in Model Builder.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="401fe-188">新增程式碼來進行預測</span><span class="sxs-lookup"><span data-stu-id="401fe-188">Add the code to make predictions</span></span>

<span data-ttu-id="401fe-189">定型程式會建立兩個專案。</span><span class="sxs-lookup"><span data-stu-id="401fe-189">Two projects are created as a result of the training process.</span></span>

- <span data-ttu-id="401fe-190">RestaurantViolationsML. Consoleapp.exe： C# .Net Core 主控台應用程式，其中包含模型定型和範例耗用量程式碼。</span><span class="sxs-lookup"><span data-stu-id="401fe-190">RestaurantViolationsML.ConsoleApp: A C# .NET Core Console application that contains the model training and sample consumption code.</span></span>
- <span data-ttu-id="401fe-191">RestaurantViolationsML： .NET Standard 類別庫，其中包含定義輸入和輸出模型資料之架構的資料模型、定型期間儲存的最佳執行模型版本，以及稱為 `ConsumeModel` 以進行預測的 helper 類別。</span><span class="sxs-lookup"><span data-stu-id="401fe-191">RestaurantViolationsML.Model: A .NET Standard class library containing the data models that define the schema of input and output model data, the saved version of the best performing model during training, and a helper class called `ConsumeModel` to make predictions.</span></span>

1. <span data-ttu-id="401fe-192">在模型產生器的程式碼步驟中，選取 [**加入專案**]，將自動產生的專案加入至方案。</span><span class="sxs-lookup"><span data-stu-id="401fe-192">In the code step of Model Builder, select **Add Projects** to add the autogenerated projects to the solution.</span></span>
1. <span data-ttu-id="401fe-193">開啟*RestaurantViolations*專案中的*Program.cs*檔案。</span><span class="sxs-lookup"><span data-stu-id="401fe-193">Open the *Program.cs* file in the *RestaurantViolations* project.</span></span>
1. <span data-ttu-id="401fe-194">新增下列 using 語句，以參考*RestaurantViolationsML 模型*專案：</span><span class="sxs-lookup"><span data-stu-id="401fe-194">Add the following using statement to reference the *RestaurantViolationsML.Model* project:</span></span>

    [!code-csharp [ProgramUsings](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L2)]

1. <span data-ttu-id="401fe-195">若要使用模型對新資料進行預測，請在應用程式的 `Main` 方法內，建立 `ModelInput` 類別的新實例。</span><span class="sxs-lookup"><span data-stu-id="401fe-195">To make a prediction on new data using the model, create a new instance of the `ModelInput` class inside the `Main` method of your application.</span></span> <span data-ttu-id="401fe-196">請注意，[風險] 分類不是輸入的一部分。</span><span class="sxs-lookup"><span data-stu-id="401fe-196">Notice that the risk category is not part of the input.</span></span> <span data-ttu-id="401fe-197">這是因為模型會產生它的預測。</span><span class="sxs-lookup"><span data-stu-id="401fe-197">This is because the model generates the prediction for it.</span></span>

    [!code-csharp [TestData](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L11-L15)]

1. <span data-ttu-id="401fe-198">使用來自 `ConsumeModel` 類別的 `Predict` 方法。</span><span class="sxs-lookup"><span data-stu-id="401fe-198">Use the `Predict` method from the `ConsumeModel` class.</span></span> <span data-ttu-id="401fe-199">`Predict` 方法會載入定型的模型、建立模型的[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) ，並使用它來對新資料進行預測。</span><span class="sxs-lookup"><span data-stu-id="401fe-199">The `Predict` method loads the trained model, creates a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) for the model, and uses it to make predictions on new data.</span></span>

    [!code-csharp [Prediction](~/machinelearning-samples/samples/modelbuilder/MulticlassClassification_RestaurantViolations/RestaurantViolations/Program.cs#L17-L24)]

1. <span data-ttu-id="401fe-200">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="401fe-200">Run the application.</span></span>

    <span data-ttu-id="401fe-201">程式所產生的輸出看起來應該會和以下程式碼片段相似：</span><span class="sxs-lookup"><span data-stu-id="401fe-201">The output generated by the program should look similar to the snippet below:</span></span>

    ```bash
    Inspection Type: Complaint
    Violation Description: Inadequate sewage or wastewater disposal
    Risk Category: Moderate Risk
    ```

<span data-ttu-id="401fe-202">若您需要於稍後在另外一個解決方案中參考所產生的專案，您可以在 `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` 目錄中找到它們。</span><span class="sxs-lookup"><span data-stu-id="401fe-202">If you need to reference the generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

<span data-ttu-id="401fe-203">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="401fe-203">Congratulations!</span></span> <span data-ttu-id="401fe-204">您已成功建立機器學習模型，以使用模型產生器來分類健康情況違規的風險。</span><span class="sxs-lookup"><span data-stu-id="401fe-204">You've successfully built a machine learning model to categorize the risk of health violations using Model Builder.</span></span> <span data-ttu-id="401fe-205">您可以在[dotnet/machinelearning 範例](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations)GitHub 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="401fe-205">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/modelbuilder/MulticlassClassification_RestaurantViolations) GitHub repository.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="401fe-206">其他資源</span><span class="sxs-lookup"><span data-stu-id="401fe-206">Additional resources</span></span>

<span data-ttu-id="401fe-207">若要深入了解此教學課程中提及的主題，請瀏覽下列資源：</span><span class="sxs-lookup"><span data-stu-id="401fe-207">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="401fe-208">模型建立器案例</span><span class="sxs-lookup"><span data-stu-id="401fe-208">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="401fe-209">多元分類</span><span class="sxs-lookup"><span data-stu-id="401fe-209">Multiclass Classification</span></span>](../resources/glossary.md#multiclass-classification)
- [<span data-ttu-id="401fe-210">多元分類模型計量</span><span class="sxs-lookup"><span data-stu-id="401fe-210">Multiclass Classification Model Metrics</span></span>](../resources/metrics.md#metrics-for-multi-class-classification)
