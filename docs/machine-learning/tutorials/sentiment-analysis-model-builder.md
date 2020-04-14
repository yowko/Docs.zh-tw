---
title: 教程:分析情緒 - 二進位分類
description: 本教程演示如何創建 Razor Pages 應用程式,該應用程式從網站評論中對情緒進行分類並採取適當的操作。 二進位情緒分類器在可視化工作室中使用模型生成器。
ms.date: 11/21/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc,mlnet-tooling
ms.openlocfilehash: 7761240055c90ae9c713b1c460e9e83316d256f9
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81278947"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a><span data-ttu-id="8f8b4-104">教學:使用模型產生器分析 Web 應用程式中網站評論的情緒ML.NET</span><span class="sxs-lookup"><span data-stu-id="8f8b4-104">Tutorial: Analyze sentiment of website comments in a web application using ML.NET Model Builder</span></span>

<span data-ttu-id="8f8b4-105">瞭解如何在 Web 應用程式內即時分析來自評論的情緒。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-105">Learn how to analyze sentiment from comments in real time inside a web application.</span></span>

<span data-ttu-id="8f8b4-106">本教程介紹如何創建一個ASP.NET核心剃刀頁面應用程式,該應用程式即時從網站評論中對情緒進行分類。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-106">This tutorial shows you how to create an ASP.NET Core Razor Pages application that classifies sentiment from website comments in real time.</span></span>

<span data-ttu-id="8f8b4-107">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="8f8b4-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="8f8b4-108">建立ASP.NET核心剃鬚刀頁面應用程式</span><span class="sxs-lookup"><span data-stu-id="8f8b4-108">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="8f8b4-109">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="8f8b4-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="8f8b4-110">選擇案例</span><span class="sxs-lookup"><span data-stu-id="8f8b4-110">Choose a scenario</span></span>
> - <span data-ttu-id="8f8b4-111">載入資料</span><span class="sxs-lookup"><span data-stu-id="8f8b4-111">Load the data</span></span>
> - <span data-ttu-id="8f8b4-112">將模型定型</span><span class="sxs-lookup"><span data-stu-id="8f8b4-112">Train the model</span></span>
> - <span data-ttu-id="8f8b4-113">評估模型</span><span class="sxs-lookup"><span data-stu-id="8f8b4-113">Evaluate the model</span></span>
> - <span data-ttu-id="8f8b4-114">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="8f8b4-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="8f8b4-115">模型產生器目前為預覽版。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-115">Model Builder is currently in Preview.</span></span>

<span data-ttu-id="8f8b4-116">您可以在[dotnet/機器學習範例](https://github.com/dotnet/machinelearning-samples)儲存庫中找到本教程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-116">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples) repository.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="8f8b4-117">必要條件</span><span class="sxs-lookup"><span data-stu-id="8f8b4-117">Pre-requisites</span></span>

<span data-ttu-id="8f8b4-118">如需必要條件和安裝指示清單，請瀏覽[模型產生器安裝指南](../how-to-guides/install-model-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-118">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-razor-pages-application"></a><span data-ttu-id="8f8b4-119">建立剃刀頁面應用程式</span><span class="sxs-lookup"><span data-stu-id="8f8b4-119">Create a Razor Pages application</span></span>

1. <span data-ttu-id="8f8b4-120">建立**ASP.NET 核心剃刀頁應用程式**。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-120">Create a **ASP.NET Core Razor Pages Application**.</span></span>

    1. <span data-ttu-id="8f8b4-121">打開視覺化工作室,並從菜單欄中選擇**檔>"新>專案**"。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-121">Open Visual Studio and select **File > New > Project** from the menu bar.</span></span>
    1. <span data-ttu-id="8f8b4-122">在 [新增專案] 對話方塊中，選取 [Visual C#]\*\*\*\* 節點，然後選取 [Web]\*\*\*\* 節點。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-122">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span>
    1. <span data-ttu-id="8f8b4-123">然後，選取 [ASP.NET Core Web 應用程式]\*\*\*\* 專案範本。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-123">Then select the **ASP.NET Core Web Application** project template.</span></span>
    1. <span data-ttu-id="8f8b4-124">在 **「名稱**」文本框中,鍵入"情緒剃鬚刀"。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-124">In the **Name** text box, type "SentimentRazor".</span></span>
    1. <span data-ttu-id="8f8b4-125">確保**未選取\*\*\*\*同一目錄中的放置解決方案和專案**(VS 2019),或**選中\*\*\*\*「創建解決方案目錄**」(VS 2017)。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-125">Make sure **Place solution and project in the same directory** is **unchecked** (VS 2019), or **Create directory for solution** is **checked** (VS 2017).</span></span>
    1. <span data-ttu-id="8f8b4-126">選擇「**確定」** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-126">Select the **OK** button.</span></span>
    1. <span data-ttu-id="8f8b4-127">在視窗中選擇**顯示**不同類型的ASP.NET核心項目,然後選擇 **「確定**」按鈕。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-127">Choose **Web Application** in the window that displays the different types of ASP.NET Core Projects, and then select the **OK** button.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="8f8b4-128">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="8f8b4-128">Prepare and understand the data</span></span>

<span data-ttu-id="8f8b4-129">下載[維琪百科排毒資料集](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-129">Download [Wikipedia detox dataset](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span> <span data-ttu-id="8f8b4-130">打開網頁時,右鍵單擊頁面,選擇 **「保存為」,** 並將檔保存在電腦上的任意位置。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-130">When the webpage opens, right-click on the page, select **Save As** and save the file anywhere on your computer.</span></span>

<span data-ttu-id="8f8b4-131">*維琪百科-排毒-250行數據.tsv*數據集中的每一行代表使用者在維琪百科上留下的不同評論。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-131">Each row in the *wikipedia-detox-250-line-data.tsv* dataset represents a different review left by a user on Wikipedia.</span></span> <span data-ttu-id="8f8b4-132">第一列表示文本的情緒(0 無毒,1 是有毒的),第二列表示使用者留下的註釋。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-132">The first column represents the sentiment of the text (0 is non-toxic, 1 is toxic), and the second column represents the comment left by the user.</span></span> <span data-ttu-id="8f8b4-133">列由選項卡分隔。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-133">The columns are separated by tabs.</span></span> <span data-ttu-id="8f8b4-134">資料如下所示:</span><span class="sxs-lookup"><span data-stu-id="8f8b4-134">The data looks like the following:</span></span>

| <span data-ttu-id="8f8b4-135">情感</span><span class="sxs-lookup"><span data-stu-id="8f8b4-135">Sentiment</span></span> | <span data-ttu-id="8f8b4-136">SentimentText</span><span class="sxs-lookup"><span data-stu-id="8f8b4-136">SentimentText</span></span> |
| :---: | :---: |
<span data-ttu-id="8f8b4-137">1</span><span class="sxs-lookup"><span data-stu-id="8f8b4-137">1</span></span> | <span data-ttu-id="8f8b4-138">[RUDE] 杜德,你粗魯地把卡爾的照片上傳回來,否則。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-138">==RUDE== Dude, you are rude upload that carl picture back, or else.</span></span>
<span data-ttu-id="8f8b4-139">1</span><span class="sxs-lookup"><span data-stu-id="8f8b4-139">1</span></span> | <span data-ttu-id="8f8b4-140">• 正常!</span><span class="sxs-lookup"><span data-stu-id="8f8b4-140">== OK!</span></span> <span data-ttu-id="8f8b4-141">•我要破壞野生維琪然後!!!</span><span class="sxs-lookup"><span data-stu-id="8f8b4-141">==  IM GOING TO VANDALIZE WILD ONES WIKI THEN!!!</span></span>
<span data-ttu-id="8f8b4-142">0</span><span class="sxs-lookup"><span data-stu-id="8f8b4-142">0</span></span> | <span data-ttu-id="8f8b4-143">我希望這會有所説明。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-143">I hope this helps.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="8f8b4-144">選擇案例</span><span class="sxs-lookup"><span data-stu-id="8f8b4-144">Choose a scenario</span></span>

![視覺化工作室中的模型產生器精靈](./media/sentiment-analysis-model-builder/model-builder-screen.png)

<span data-ttu-id="8f8b4-146">若要定型您的模型，您需要從模型產生器所提供的可用機器學習服務案例清單中選取。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-146">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span>

1. <span data-ttu-id="8f8b4-147">在**解決方案資源管理器**中,右鍵按*下 「情緒剃鬚刀*」專案,然後選擇「**添加** > **機器學習**」。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-147">In **Solution Explorer**, right-click the *SentimentRazor* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="8f8b4-148">對於此示例,方案是情緒分析。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-148">For this sample, the scenario is sentiment analysis.</span></span> <span data-ttu-id="8f8b4-149">在模型生成器工具*的方案*步驟中,選擇**情緒分析**方案。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-149">In the *scenario* step of the Model Builder tool, select the **Sentiment Analysis** scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="8f8b4-150">載入資料</span><span class="sxs-lookup"><span data-stu-id="8f8b4-150">Load the data</span></span>

<span data-ttu-id="8f8b4-151">模型生成器接受來自兩個源的數據:SQL Server 資料庫或`csv`本地`tsv`檔案( 或格式)。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-151">Model Builder accepts data from two sources, a SQL Server database or a local file in `csv` or `tsv` format.</span></span>

1. <span data-ttu-id="8f8b4-152">在模型產生器工具的資料步驟中，從資料來源下拉式清單中選取 [檔案]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-152">In the data step of the Model Builder tool, select **File** from the data source dropdown.</span></span>
1. <span data-ttu-id="8f8b4-153">選擇「**選擇檔案**文字框」 旁邊的按鈕,並使用檔案資源管理器瀏覽並選擇*wikipedia-detox-250 行資料.tsv*檔。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-153">Select the button next to the **Select a file** text box and use File Explorer to browse and select the *wikipedia-detox-250-line-data.tsv* file.</span></span>
1. <span data-ttu-id="8f8b4-154">在 **「要預測(標籤)** 下拉清單的列中選擇 **「情緒**」。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-154">Choose **Sentiment** in the **Column to Predict (Label)** dropdown.</span></span>
1. <span data-ttu-id="8f8b4-155">保留**輸入列(要素)** 下拉的預設值。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-155">Leave the default values for the **Input Columns (Features)** dropdown.</span></span>
1. <span data-ttu-id="8f8b4-156">選擇 **「訓練」** 連結以移動到模型生成器工具中的下一步。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-156">Select the **Train** link to move to the next step in the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="8f8b4-157">將模型定型</span><span class="sxs-lookup"><span data-stu-id="8f8b4-157">Train the model</span></span>

<span data-ttu-id="8f8b4-158">本教程中用於訓練情緒分析模型的機器學習任務是二進位製分類。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-158">The machine learning task used to train the sentiment analysis model in this tutorial is binary classification.</span></span> <span data-ttu-id="8f8b4-159">在模型培訓過程中,模型生成器使用不同的二進位分類演演演算法和設置訓練單獨的模型,以查找數據集的最佳模型。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-159">During the model training process, Model Builder trains separate models using different binary classification algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="8f8b4-160">定型模型所需要的時間會與資料量成比例。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-160">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="8f8b4-161">模型生成器根據資料來源的大小自動選擇**時間訓練時間(秒)** 的預設值。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-161">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="8f8b4-162">儘管模型生成器將**訓練時間(秒)** 的值設置為 10 秒,但將其增加到 30 秒。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-162">Although Model Builder sets the value of **Time to train (seconds)** to 10 seconds, increase it to 30 seconds.</span></span> <span data-ttu-id="8f8b4-163">經過更長時間的培訓,模型構建器可以探索更多演演演算法和參數組合,以查找最佳模型。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-163">Training for a longer period of time allows Model Builder to explore a larger number of algorithms and combination of parameters in search of the best model.</span></span>
1. <span data-ttu-id="8f8b4-164">選取 [開始定型]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-164">Select **Start Training**.</span></span>

    <span data-ttu-id="8f8b4-165">在整個定型程序期間，進度資料會顯示在定型步驟的 `Progress` 區段中。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-165">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

    - <span data-ttu-id="8f8b4-166">[狀態] 會顯示定型程序的完成狀態。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-166">Status displays the completion status of the training process.</span></span>
    - <span data-ttu-id="8f8b4-167">[最佳正確性] 會顯示模型產生器到目前為止所找到執行效能最佳模型的正確性。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-167">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="8f8b4-168">正確性越高，表示模型針對測試資料的預測越正確。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-168">Higher accuracy means the model predicted more correctly on test data.</span></span>
    - <span data-ttu-id="8f8b4-169">[最佳演算法] 會顯示模型產生器到目前為止所執行演算法中效能最佳的演算法名稱。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-169">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
    - <span data-ttu-id="8f8b4-170">[上一個演算法] 會顯示模型產生器最近一次用來定型模型的演算法名稱。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-170">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

1. <span data-ttu-id="8f8b4-171">培訓完成後,選擇**評估**鏈接以移動到下一步。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-171">Once training is complete, select the **evaluate** link to move to the next step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="8f8b4-172">評估模型</span><span class="sxs-lookup"><span data-stu-id="8f8b4-172">Evaluate the model</span></span>

<span data-ttu-id="8f8b4-173">訓練步驟的結果將是一個性能最好的模型。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-173">The result of the training step will be one model that has the best performance.</span></span> <span data-ttu-id="8f8b4-174">在模型生成器工具的計算步驟中,輸出部分將包含**最佳模型**條目中性能最佳的模型使用的演演演算法以及**最佳模型精度**中的指標。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-174">In the evaluate step of the Model Builder tool, the output section will contain the algorithm used by the best-performing model in the **Best Model** entry along with metrics in **Best Model Accuracy**.</span></span> <span data-ttu-id="8f8b4-175">此外,還顯示了包含前五個模型及其指標的匯總表。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-175">Additionally, a summary table containing the top five models and their metrics is shown.</span></span>

<span data-ttu-id="8f8b4-176">如果您對準確性指標不滿意,則嘗試提高模型準確性的一些簡單方法是增加訓練模型或使用更多數據的時間。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-176">If you're not satisfied with your accuracy metrics, some easy ways to try to improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="8f8b4-177">否則,選擇**代碼**連結以移動到模型生成器工具中的最後一步。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-177">Otherwise, select the **code** link to move to the final step in the Model Builder tool.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="8f8b4-178">新增程式碼來進行預測</span><span class="sxs-lookup"><span data-stu-id="8f8b4-178">Add the code to make predictions</span></span>

<span data-ttu-id="8f8b4-179">定型程序的結果會建立兩個專案。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-179">Two projects will be created as a result of the training process.</span></span>

### <a name="reference-the-trained-model"></a><span data-ttu-id="8f8b4-180">參考經過培訓的模型</span><span class="sxs-lookup"><span data-stu-id="8f8b4-180">Reference the trained model</span></span>

1. <span data-ttu-id="8f8b4-181">在模型生成器工具*的代碼*步驟中,選擇 **「添加專案」** 以將自動生成的專案添加到解決方案。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-181">In the *code* step of the Model Builder tool, select **Add Projects** to add the autogenerated projects to the solution.</span></span>

    <span data-ttu-id="8f8b4-182">以下項目應出現在**解決方案資源管理員**中:</span><span class="sxs-lookup"><span data-stu-id="8f8b4-182">The following projects should appear in the **Solution Explorer**:</span></span>

    - <span data-ttu-id="8f8b4-183">*情緒剃鬚刀.控制台應用程式*:一個 .NET 核心控制台應用程式,其中包含模型訓練和預測代碼。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-183">*SentimentRazorML.ConsoleApp*: A .NET Core Console application that contains the model training and prediction code.</span></span>
    - <span data-ttu-id="8f8b4-184">*情緒剃鬚刀ML.模型*:.NET 標準類庫,其中包含定義輸入和輸出模型數據的架構的數據模型,以及在培訓期間保存的保存版本最佳性能模型。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-184">*SentimentRazorML.Model*: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the saved version of the best performing model during training.</span></span>

    <span data-ttu-id="8f8b4-185">在本教程中,僅使用*情緒RazorML.Model*項目,因為預測將在*情緒剃鬚刀*Web 應用程式中而不是在控制台中進行。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-185">For this tutorial, only the *SentimentRazorML.Model* project is used because predictions will be made in the *SentimentRazor* web application rather than in the console.</span></span> <span data-ttu-id="8f8b4-186">儘管*情緒剃鬚刀ML.ConsoleApp*不會用於評分,但它可用於在以後使用新數據重新訓練模型。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-186">Although the *SentimentRazorML.ConsoleApp* won't be used for scoring, it can be used to retrain the model using new data at a later time.</span></span> <span data-ttu-id="8f8b4-187">不過,再培訓不在本教程的範圍之內。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-187">Retraining is outside the scope of this tutorial though.</span></span>

### <a name="configure-the-predictionengine-pool"></a><span data-ttu-id="8f8b4-188">設定預測引擎池</span><span class="sxs-lookup"><span data-stu-id="8f8b4-188">Configure the PredictionEngine pool</span></span>

<span data-ttu-id="8f8b4-189">要進行單一預測,必須建立一個<xref:Microsoft.ML.PredictionEngine%602>。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-189">To make a single prediction, you have to create a <xref:Microsoft.ML.PredictionEngine%602>.</span></span> <span data-ttu-id="8f8b4-190"><xref:Microsoft.ML.PredictionEngine%602> 不是安全執行緒。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-190"><xref:Microsoft.ML.PredictionEngine%602> is not thread-safe.</span></span> <span data-ttu-id="8f8b4-191">此外,您必須在應用程式中需要它的地方創建它的實例。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-191">Additionally, you have to create an instance of it everywhere it's needed within your application.</span></span> <span data-ttu-id="8f8b4-192">隨著應用程式的增長,此過程可能會變得難以管理。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-192">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="8f8b4-193">為提高性能和線程安全性,請使用依賴項注入和服務`PredictionEnginePool`的組合,該服務將創建一個<xref:Microsoft.Extensions.ObjectPool.ObjectPool%601><xref:Microsoft.ML.PredictionEngine%602>物件,供整個應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-193">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an <xref:Microsoft.Extensions.ObjectPool.ObjectPool%601> of <xref:Microsoft.ML.PredictionEngine%602> objects for use throughout your application.</span></span>

1. <span data-ttu-id="8f8b4-194">安裝*Microsoft.Extensions.ML* NuGet 套件:</span><span class="sxs-lookup"><span data-stu-id="8f8b4-194">Install the *Microsoft.Extensions.ML* NuGet package:</span></span>

    1. <span data-ttu-id="8f8b4-195">在**解決方案資源管理員**中,右鍵單擊專案並選擇 **「管理 NuGet 包**」 。。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-195">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="8f8b4-196">選擇「nuget.org」作為包源。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-196">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="8f8b4-197">選擇「**瀏覽**」選項卡並搜尋**Microsoft.Extensions.ML**。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-197">Select the **Browse** tab and search for **Microsoft.Extensions.ML**.</span></span>
    1. <span data-ttu-id="8f8b4-198">選擇清單中的套件,然後選擇 **「安裝**」按鈕。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-198">Select the package in the list, and select the **Install** button.</span></span>
    1. <span data-ttu-id="8f8b4-199">選擇 **「預覽變更**」 對話框上的 **「 確定**」 按鈕</span><span class="sxs-lookup"><span data-stu-id="8f8b4-199">Select the **OK** button on the **Preview Changes** dialog</span></span>
    1. <span data-ttu-id="8f8b4-200">如果您同意列出的套件的許可證條款,請選擇 **「許可證接受」** 對話方塊上的 **「接受」** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-200">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="8f8b4-201">打開 *「情緒剃鬚刀*」專案中*的Startup.cs*檔。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-201">Open the *Startup.cs* file in the *SentimentRazor* project.</span></span>
1. <span data-ttu-id="8f8b4-202">新增以下使用敘述以引用nuGet 包和*情緒RazorML.model*專案*Microsoft.Extensions.ML:*</span><span class="sxs-lookup"><span data-stu-id="8f8b4-202">Add the following using statements to reference the *Microsoft.Extensions.ML* NuGet package and *SentimentRazorML.Model* project:</span></span>

    ```csharp
    using System.IO;
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

1. <span data-ttu-id="8f8b4-203">建立全域變數以存儲已訓練的模型檔的位置。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-203">Create a global variable to store the location of the trained model file.</span></span>

    ```csharp
    private readonly string _modelPath;
    ```

1. <span data-ttu-id="8f8b4-204">模型檔與應用程式的程式集檔一起存儲在生成目錄中。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-204">The model file is stored in the build directory alongside the assembly files of your application.</span></span> <span data-ttu-id="8f8b4-205">為了便於存取,請建立一個`GetAbsolutePath``Configure`在 方法之後呼叫的說明器方法</span><span class="sxs-lookup"><span data-stu-id="8f8b4-205">To make it easier to access, create a helper method called `GetAbsolutePath` after the `Configure` method</span></span>

    ```csharp
    public static string GetAbsolutePath(string relativePath)
    {
        FileInfo _dataRoot = new FileInfo(typeof(Program).Assembly.Location);
        string assemblyFolderPath = _dataRoot.Directory.FullName;

        string fullPath = Path.Combine(assemblyFolderPath, relativePath);
        return fullPath;
    }
    ```

1. <span data-ttu-id="8f8b4-206">使用`GetAbsolutePath`類別建構函`Startup`式中的方法`_modelPath`設定 。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-206">Use the `GetAbsolutePath` method in the `Startup` class constructor to set the `_modelPath`.</span></span>

    ```csharp
    _modelPath = GetAbsolutePath("MLModel.zip");
    ```

1. <span data-ttu-id="8f8b4-207">在`PredictionEnginePool`方法中為應用程式設定`ConfigureServices`的 。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-207">Configure the `PredictionEnginePool` for your application in the `ConfigureServices` method:</span></span>

    ```csharp
    services.AddPredictionEnginePool<ModelInput, ModelOutput>()
            .FromFile(_modelPath);
    ```

### <a name="create-sentiment-analysis-handler"></a><span data-ttu-id="8f8b4-208">建立情緒分析處理程式</span><span class="sxs-lookup"><span data-stu-id="8f8b4-208">Create sentiment analysis handler</span></span>

<span data-ttu-id="8f8b4-209">將在應用程式的主頁內進行預測。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-209">Predictions will be made inside the main page of the application.</span></span> <span data-ttu-id="8f8b4-210">因此,需要添加一個獲取使用者輸入並使用`PredictionEnginePool`返回預測的方法。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-210">Therefore, a method that takes the user input and uses the `PredictionEnginePool` to return a prediction needs to be added.</span></span>

1. <span data-ttu-id="8f8b4-211">開啟*頁面'* 目錄中*的Index.cshtml.cs*檔,並使用敘述加入以下內容:</span><span class="sxs-lookup"><span data-stu-id="8f8b4-211">Open the *Index.cshtml.cs* file located in the *Pages* directory and add the following using statements:</span></span>

    ```csharp
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

    <span data-ttu-id="8f8b4-212">為了在類別使用配置`PredictionEnginePool`,`Startup`必須將其注入到要使用它的模型的建構函數中。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-212">In order to use the `PredictionEnginePool` configured in the `Startup` class, you have to inject it into the constructor of the model where you want to use it.</span></span>

1. <span data-ttu-id="8f8b4-213">添加變數以引用類`PredictionEnginePool`內部。 `IndexModel`</span><span class="sxs-lookup"><span data-stu-id="8f8b4-213">Add a variable to reference the `PredictionEnginePool` inside the `IndexModel` class.</span></span>

    ```csharp
    private readonly PredictionEnginePool<ModelInput, ModelOutput> _predictionEnginePool;
    ```

1. <span data-ttu-id="8f8b4-214">在`IndexModel`類中創建一個構造函數`PredictionEnginePool`, 並將服務注入其中。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-214">Create a constructor in the `IndexModel` class and inject the `PredictionEnginePool` service into it.</span></span>

    ```csharp
    public IndexModel(PredictionEnginePool<ModelInput, ModelOutput> predictionEnginePool)
    {
        _predictionEnginePool = predictionEnginePool;
    }
    ```

1. <span data-ttu-id="8f8b4-215">創建一個方法處理程式,使用`PredictionEnginePool`從從網頁收到的使用者輸入進行預測。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-215">Create a method handler that uses the `PredictionEnginePool` to make predictions from user input received from the web page.</span></span>

    1. <span data-ttu-id="8f8b4-216">在方法`OnGet`下方,創建一個稱為`OnGetAnalyzeSentiment`</span><span class="sxs-lookup"><span data-stu-id="8f8b4-216">Below the `OnGet` method, create a new method called `OnGetAnalyzeSentiment`</span></span>

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. <span data-ttu-id="8f8b4-217">在`OnGetAnalyzeSentiment`方法內,如果來自用戶的輸入為空或為空,則返回*中性*情緒。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-217">Inside the `OnGetAnalyzeSentiment` method, return *Neutral* sentiment if the input from the user is blank or null.</span></span>

        ```csharp
        if (String.IsNullOrEmpty(text)) return Content("Neutral");
        ```

    1. <span data-ttu-id="8f8b4-218">給定有效的輸入,請建立新實體 。`ModelInput`</span><span class="sxs-lookup"><span data-stu-id="8f8b4-218">Given a valid input, create a new instance of `ModelInput`.</span></span>

        ```csharp
        var input = new ModelInput { SentimentText = text };
        ```

    1. <span data-ttu-id="8f8b4-219">使用`PredictionEnginePool`預測情緒。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-219">Use the `PredictionEnginePool` to predict sentiment.</span></span>

        ```csharp
        var prediction = _predictionEnginePool.Predict(input);
        ```

    1. <span data-ttu-id="8f8b4-220">使用以下代碼`bool`將預測值轉換為有毒或無毒值。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-220">Convert the predicted `bool` value into toxic or not toxic with the following code.</span></span>

        ```csharp
        var sentiment = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";
        ```

    1. <span data-ttu-id="8f8b4-221">最後,將情緒返回到網頁。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-221">Finally, return the sentiment back to the web page.</span></span>

        ```csharp
        return Content(sentiment);
        ```

### <a name="configure-the-web-page"></a><span data-ttu-id="8f8b4-222">設定網頁</span><span class="sxs-lookup"><span data-stu-id="8f8b4-222">Configure the web page</span></span>

<span data-ttu-id="8f8b4-223">返回的結果`OnGetAnalyzeSentiment`將動態顯示`Index`在網頁上。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-223">The results returned by the `OnGetAnalyzeSentiment` will be dynamically displayed on the `Index` web page.</span></span>

1. <span data-ttu-id="8f8b4-224">開啟*Pages*目錄中的*Index.cshtml*檔案,並將其內容取代為以下代碼:</span><span class="sxs-lookup"><span data-stu-id="8f8b4-224">Open the *Index.cshtml* file in the *Pages* directory and replace its contents with the following code:</span></span>

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. <span data-ttu-id="8f8b4-225">接下來,在*wwwroot_css*目錄中將 css 樣式代碼添加到*site.css*頁面的末尾:</span><span class="sxs-lookup"><span data-stu-id="8f8b4-225">Next, add css styling code to the end of the *site.css* page in the *wwwroot\css* directory:</span></span>

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. <span data-ttu-id="8f8b4-226">之後,添加代碼以將網頁中的輸入發送到`OnGetAnalyzeSentiment`處理程式。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-226">After that, add code to send inputs from the web page to the `OnGetAnalyzeSentiment` handler.</span></span>

    1. <span data-ttu-id="8f8b4-227">在位於*wwwroot_js*目錄中的*site.js*檔`getSentiment`中,創建一個調用函數,`OnGetAnalyzeSentiment`以便使用使用者輸入 處理程式發出 GET HTTP 請求。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-227">In the *site.js* file located in the *wwwroot\js* directory, create a function called `getSentiment` to make a GET HTTP request with the user input to the `OnGetAnalyzeSentiment` handler.</span></span>

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. <span data-ttu-id="8f8b4-228">在此下方,添加另一個`updateMarker`調用函數,以動態更新標記在網頁上的位置,因為情緒預測。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-228">Below that, add another function called `updateMarker` to dynamically update the position of the marker on the web page as sentiment is predicted.</span></span>

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. <span data-ttu-id="8f8b4-229">創建一個事件處理程式函數`updateSentiment`,用於從使用者獲取輸入,`OnGetAnalyzeSentiment``getSentiment`使用 函數將其發送到函數,`updateMarker`並使用函數更新標記。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-229">Create an event handler function called `updateSentiment` to get the input from the user, send it to the `OnGetAnalyzeSentiment` function using the `getSentiment` function and update the marker with the `updateMarker` function.</span></span>

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. <span data-ttu-id="8f8b4-230">最後,註冊事件處理程式並將其綁定到具有`textarea``id=Message`屬性的元素。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-230">Finally, register the event handler and bind it to the `textarea` element with the `id=Message` attribute.</span></span>

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a><span data-ttu-id="8f8b4-231">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="8f8b4-231">Run the application</span></span>

<span data-ttu-id="8f8b4-232">現在,您的應用程式已設置,請運行應用程式,該應用程式應在瀏覽器中啟動。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-232">Now that your application is set up, run the application, which should launch in your browser.</span></span>

<span data-ttu-id="8f8b4-233">當應用程式啟動時,輸入*模型生成器是很酷的!*</span><span class="sxs-lookup"><span data-stu-id="8f8b4-233">When the application launches, enter *Model Builder is cool!*</span></span> <span data-ttu-id="8f8b4-234">到文本區域。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-234">into the text area.</span></span> <span data-ttu-id="8f8b4-235">顯示的預測情緒應該*不是有毒的*。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-235">The predicted sentiment displayed should be *Not Toxic*.</span></span>

![使用預測情緒視窗執行視窗](./media/sentiment-analysis-model-builder/web-app.png)

<span data-ttu-id="8f8b4-237">如果需要在以後引用模型產生器產生的項目,可以在其他解決方案中找到這些專案`C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`。</span><span class="sxs-lookup"><span data-stu-id="8f8b4-237">If you need to reference the Model Builder generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8f8b4-238">後續步驟</span><span class="sxs-lookup"><span data-stu-id="8f8b4-238">Next steps</span></span>

<span data-ttu-id="8f8b4-239">在本教學課程中，您已了解如何：</span><span class="sxs-lookup"><span data-stu-id="8f8b4-239">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="8f8b4-240">建立ASP.NET核心剃鬚刀頁面應用程式</span><span class="sxs-lookup"><span data-stu-id="8f8b4-240">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="8f8b4-241">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="8f8b4-241">Prepare and understand the data</span></span>
> - <span data-ttu-id="8f8b4-242">選擇案例</span><span class="sxs-lookup"><span data-stu-id="8f8b4-242">Choose a scenario</span></span>
> - <span data-ttu-id="8f8b4-243">載入資料</span><span class="sxs-lookup"><span data-stu-id="8f8b4-243">Load the data</span></span>
> - <span data-ttu-id="8f8b4-244">將模型定型</span><span class="sxs-lookup"><span data-stu-id="8f8b4-244">Train the model</span></span>
> - <span data-ttu-id="8f8b4-245">評估模型</span><span class="sxs-lookup"><span data-stu-id="8f8b4-245">Evaluate the model</span></span>
> - <span data-ttu-id="8f8b4-246">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="8f8b4-246">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="8f8b4-247">其他資源</span><span class="sxs-lookup"><span data-stu-id="8f8b4-247">Additional Resources</span></span>

<span data-ttu-id="8f8b4-248">若要深入了解此教學課程中提及的主題，請瀏覽下列資源：</span><span class="sxs-lookup"><span data-stu-id="8f8b4-248">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="8f8b4-249">模型建立器案例</span><span class="sxs-lookup"><span data-stu-id="8f8b4-249">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenario)
- [<span data-ttu-id="8f8b4-250">二進位類別</span><span class="sxs-lookup"><span data-stu-id="8f8b4-250">Binary Classification</span></span>](../resources/glossary.md#binary-classification)
- [<span data-ttu-id="8f8b4-251">二進位類別模型指標</span><span class="sxs-lookup"><span data-stu-id="8f8b4-251">Binary Classification Model Metrics</span></span>](../resources/metrics.md#evaluation-metrics-for-binary-classification)
