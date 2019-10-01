---
title: 教學課程：分析情感-二進位分類
description: 本教學課程會示範如何建立 Razor Pages 應用程式，以將情感從網站批註中分類，並採取適當的動作。 二元情感分類器會在 Visual Studio 中使用模型產生器。
ms.date: 09/30/2019
author: luisquintanilla
ms.author: luquinta
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: ce64f0d11b1da65e460235fdabc2b07e05ffcbe4
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700904"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-in-a-web-application-using-mlnet-model-builder"></a><span data-ttu-id="1b613-104">教學課程：在 web 應用程式中使用 ML.NET 模型產生器來分析網站批註的情感</span><span class="sxs-lookup"><span data-stu-id="1b613-104">Tutorial: Analyze sentiment of website comments in a web application using ML.NET Model Builder</span></span>

<span data-ttu-id="1b613-105">瞭解如何在 web 應用程式內即時分析批註中的情感。</span><span class="sxs-lookup"><span data-stu-id="1b613-105">Learn how to analyze sentiment from comments in real-time inside a web application.</span></span>

<span data-ttu-id="1b613-106">本教學課程會示範如何建立 ASP.NET Core Razor Pages 應用程式，以即時將情感的網站批註分類。</span><span class="sxs-lookup"><span data-stu-id="1b613-106">This tutorial shows you how to create an ASP.NET Core Razor Pages application that classifies sentiment from website comments in real-time.</span></span>

<span data-ttu-id="1b613-107">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="1b613-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="1b613-108">建立 ASP.NET Core Razor Pages 應用程式</span><span class="sxs-lookup"><span data-stu-id="1b613-108">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="1b613-109">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="1b613-109">Prepare and understand the data</span></span>
> - <span data-ttu-id="1b613-110">選擇案例</span><span class="sxs-lookup"><span data-stu-id="1b613-110">Choose a scenario</span></span>
> - <span data-ttu-id="1b613-111">載入資料</span><span class="sxs-lookup"><span data-stu-id="1b613-111">Load the data</span></span>
> - <span data-ttu-id="1b613-112">將模型定型</span><span class="sxs-lookup"><span data-stu-id="1b613-112">Train the model</span></span>
> - <span data-ttu-id="1b613-113">評估模型</span><span class="sxs-lookup"><span data-stu-id="1b613-113">Evaluate the model</span></span>
> - <span data-ttu-id="1b613-114">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="1b613-114">Use the model for predictions</span></span>

> [!NOTE]
> <span data-ttu-id="1b613-115">模型產生器目前為預覽版。</span><span class="sxs-lookup"><span data-stu-id="1b613-115">Model Builder is currently in Preview.</span></span>

<span data-ttu-id="1b613-116">您可以在[dotnet/machinelearning 範例](https://github.com/dotnet/machinelearning-samples)存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="1b613-116">You can find the source code for this tutorial at the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples) repository.</span></span>

## <a name="pre-requisites"></a><span data-ttu-id="1b613-117">先決條件</span><span class="sxs-lookup"><span data-stu-id="1b613-117">Pre-requisites</span></span>

<span data-ttu-id="1b613-118">如需必要條件和安裝指示清單，請瀏覽[模型產生器安裝指南](../how-to-guides/install-model-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="1b613-118">For a list of pre-requisites and installation instructions, visit the [Model Builder installation guide](../how-to-guides/install-model-builder.md).</span></span>

## <a name="create-a-razor-pages-application"></a><span data-ttu-id="1b613-119">建立 Razor Pages 應用程式</span><span class="sxs-lookup"><span data-stu-id="1b613-119">Create a Razor Pages application</span></span>

1. <span data-ttu-id="1b613-120">建立**ASP.NET Core Razor Pages 應用程式**。</span><span class="sxs-lookup"><span data-stu-id="1b613-120">Create a **ASP.NET Core Razor Pages Application**.</span></span>

    1. <span data-ttu-id="1b613-121">開啟 Visual Studio，然後從功能表列選取 [檔案] **> [新增 > 專案**]。</span><span class="sxs-lookup"><span data-stu-id="1b613-121">Open Visual Studio and select **File > New > Project** from the menu bar.</span></span>
    1. <span data-ttu-id="1b613-122">在 [新增專案] 對話方塊中，選取 [Visual C#] 節點，然後選取 [Web] 節點。</span><span class="sxs-lookup"><span data-stu-id="1b613-122">In the New Project dialog, select the **Visual C#** node followed by the **Web** node.</span></span>
    1. <span data-ttu-id="1b613-123">然後，選取 [ASP.NET Core Web 應用程式] 專案範本。</span><span class="sxs-lookup"><span data-stu-id="1b613-123">Then select the **ASP.NET Core Web Application** project template.</span></span>
    1. <span data-ttu-id="1b613-124">在 [**名稱**] 文字方塊中，輸入 "SentimentRazor"。</span><span class="sxs-lookup"><span data-stu-id="1b613-124">In the **Name** text box, type "SentimentRazor".</span></span>
    1. <span data-ttu-id="1b613-125">預設應該會核取 [**為方案建立目錄**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="1b613-125">The **Create a directory for solution** checkbox should be checked by default.</span></span> <span data-ttu-id="1b613-126">如果不是這種情況，請檢查它。</span><span class="sxs-lookup"><span data-stu-id="1b613-126">If that's not the case, check it.</span></span>
    1. <span data-ttu-id="1b613-127">選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1b613-127">Select the **OK** button.</span></span>
    1. <span data-ttu-id="1b613-128">在顯示不同類型 ASP.NET Core 專案的視窗中，選擇 [ **Web 應用程式**]，然後選取 [**確定]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1b613-128">Choose **Web Application** in the window that displays the different types of ASP.NET Core Projects, and then select the **OK** button.</span></span>

## <a name="prepare-and-understand-the-data"></a><span data-ttu-id="1b613-129">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="1b613-129">Prepare and understand the data</span></span>

<span data-ttu-id="1b613-130">下載[維琪百科 detox 資料集](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv)。</span><span class="sxs-lookup"><span data-stu-id="1b613-130">Download [Wikipedia detox dataset](https://raw.githubusercontent.com/dotnet/machinelearning/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span> <span data-ttu-id="1b613-131">當網頁開啟時，以滑鼠右鍵按一下頁面，選取 [**另存**新檔]，然後將檔案儲存在您電腦上的任何位置。</span><span class="sxs-lookup"><span data-stu-id="1b613-131">When the webpage opens, right-click on the page, select **Save As** and save the file anywhere on your computer.</span></span>

<span data-ttu-id="1b613-132">*維琪百科-detox-250-line-data.tsv*中的每個資料列都代表使用者在維琪百科上留下的不同評論。</span><span class="sxs-lookup"><span data-stu-id="1b613-132">Each row in the *wikipedia-detox-250-line-data.tsv* dataset represents a different review left by a user on Wikipedia.</span></span> <span data-ttu-id="1b613-133">第一個資料行代表文字的情感（0是非有毒，1是有毒），而第二個數據行代表使用者所留下的批註。</span><span class="sxs-lookup"><span data-stu-id="1b613-133">The first column represents the sentiment of the text (0 is non-toxic, 1 is toxic), and the second column represents the comment left by the user.</span></span> <span data-ttu-id="1b613-134">資料行是以 tab 鍵分隔。</span><span class="sxs-lookup"><span data-stu-id="1b613-134">The columns are separated by tabs.</span></span> <span data-ttu-id="1b613-135">資料看起來如下所示：</span><span class="sxs-lookup"><span data-stu-id="1b613-135">The data looks like the following:</span></span>

| <span data-ttu-id="1b613-136">情感</span><span class="sxs-lookup"><span data-stu-id="1b613-136">Sentiment</span></span> | <span data-ttu-id="1b613-137">SentimentText</span><span class="sxs-lookup"><span data-stu-id="1b613-137">SentimentText</span></span> |
| :---: | :---: |
<span data-ttu-id="1b613-138">1</span><span class="sxs-lookup"><span data-stu-id="1b613-138">1</span></span> | <span data-ttu-id="1b613-139">= = 「強制」 = = Dude，您可以將 carl 的上傳放回，或其他。</span><span class="sxs-lookup"><span data-stu-id="1b613-139">==RUDE== Dude, you are rude upload that carl picture back, or else.</span></span>
<span data-ttu-id="1b613-140">1</span><span class="sxs-lookup"><span data-stu-id="1b613-140">1</span></span> | <span data-ttu-id="1b613-141">= = OK！</span><span class="sxs-lookup"><span data-stu-id="1b613-141">== OK!</span></span> <span data-ttu-id="1b613-142">= = IM 即將 VANDALIZE 萬用字元 WIKI 然後!!!</span><span class="sxs-lookup"><span data-stu-id="1b613-142">==  IM GOING TO VANDALIZE WILD ONES WIKI THEN!!!</span></span>
<span data-ttu-id="1b613-143">0</span><span class="sxs-lookup"><span data-stu-id="1b613-143">0</span></span> | <span data-ttu-id="1b613-144">我希望這有説明。</span><span class="sxs-lookup"><span data-stu-id="1b613-144">I hope this helps.</span></span>

## <a name="choose-a-scenario"></a><span data-ttu-id="1b613-145">選擇案例</span><span class="sxs-lookup"><span data-stu-id="1b613-145">Choose a scenario</span></span>

![Visual Studio 中的模型產生器 wizard](./media/sentiment-analysis-model-builder/model-builder-screen.png)

<span data-ttu-id="1b613-147">若要定型您的模型，您需要從模型產生器所提供的可用機器學習服務案例清單中選取。</span><span class="sxs-lookup"><span data-stu-id="1b613-147">To train your model, you need to select from the list of available machine learning scenarios provided by Model Builder.</span></span>

1. <span data-ttu-id="1b613-148">在**方案總管**中，以滑鼠右鍵按一下*SentimentRazor*專案，然後選取 [**新增** >  **Machine Learning**]。</span><span class="sxs-lookup"><span data-stu-id="1b613-148">In **Solution Explorer**, right-click the *SentimentRazor* project, and select **Add** > **Machine Learning**.</span></span>
1. <span data-ttu-id="1b613-149">在此範例中，案例是情感分析。</span><span class="sxs-lookup"><span data-stu-id="1b613-149">For this sample, the scenario is sentiment analysis.</span></span> <span data-ttu-id="1b613-150">在模型產生器工具的*情節*步驟中，選取 [**情感分析**] 案例。</span><span class="sxs-lookup"><span data-stu-id="1b613-150">In the *scenario* step of the Model Builder tool, select the **Sentiment Analysis** scenario.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="1b613-151">載入資料</span><span class="sxs-lookup"><span data-stu-id="1b613-151">Load the data</span></span>

<span data-ttu-id="1b613-152">模型產生器會接受來自兩個來源、SQL Server 資料庫或本機`csv`檔案或`tsv`格式的資料。</span><span class="sxs-lookup"><span data-stu-id="1b613-152">Model Builder accepts data from two sources, a SQL Server database or a local file in `csv` or `tsv` format.</span></span>

1. <span data-ttu-id="1b613-153">在模型產生器工具的資料步驟中，從資料來源下拉式清單中選取 [檔案]。</span><span class="sxs-lookup"><span data-stu-id="1b613-153">In the data step of the Model Builder tool, select **File** from the data source dropdown.</span></span>
1. <span data-ttu-id="1b613-154">選取 [**選取**檔案] 文字方塊旁的按鈕，然後使用 [檔案瀏覽器] 流覽並選取 [*維琪百科-detox-250-line-data.tsv* ] 檔案。</span><span class="sxs-lookup"><span data-stu-id="1b613-154">Select the button next to the **Select a file** text box and use File Explorer to browse and select the *wikipedia-detox-250-line-data.tsv* file.</span></span>
1. <span data-ttu-id="1b613-155">在 [**要預測的資料行（標籤）** ] 下拉式清單中選擇 [**情感**]。</span><span class="sxs-lookup"><span data-stu-id="1b613-155">Choose **Sentiment** in the **Column to Predict (Label)** dropdown.</span></span>
1. <span data-ttu-id="1b613-156">保留 [**輸入資料行（功能）** ] 下拉式清單的預設值。</span><span class="sxs-lookup"><span data-stu-id="1b613-156">Leave the default values for the **Input Columns (Features)** dropdown.</span></span>
1. <span data-ttu-id="1b613-157">選取 [**定型**] 連結，以移至模型產生器工具中的下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="1b613-157">Select the **Train** link to move to the next step in the Model Builder tool.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="1b613-158">將模型定型</span><span class="sxs-lookup"><span data-stu-id="1b613-158">Train the model</span></span>

<span data-ttu-id="1b613-159">在本教學課程中用來定型價格預測模型的機器學習工作是二元分類。</span><span class="sxs-lookup"><span data-stu-id="1b613-159">The machine learning task used to train the price prediction model in this tutorial is binary classification.</span></span> <span data-ttu-id="1b613-160">在模型定型程式期間，模型產生器會使用不同的二進位分類演算法和設定來訓練不同的模型，以尋找資料集最佳的執行模型。</span><span class="sxs-lookup"><span data-stu-id="1b613-160">During the model training process, Model Builder trains separate models using different binary classification algorithms and settings to find the best performing model for your dataset.</span></span>

<span data-ttu-id="1b613-161">定型模型所需要的時間會與資料量成比例。</span><span class="sxs-lookup"><span data-stu-id="1b613-161">The time required for the model to train is proportionate to the amount of data.</span></span> <span data-ttu-id="1b613-162">「模型產生器」會根據您的資料來源大小，自動選取要定型的預設值 **（秒）** 。</span><span class="sxs-lookup"><span data-stu-id="1b613-162">Model Builder automatically selects a default value for **Time to train (seconds)** based on the size of your data source.</span></span>

1. <span data-ttu-id="1b613-163">雖然模型產生器會將 [**要定型的時間] 值（秒）** 設定為10秒，但將它增加為30秒。</span><span class="sxs-lookup"><span data-stu-id="1b613-163">Although Model Builder sets the value of **Time to train (seconds)** to 10 seconds, increase it to 30 seconds.</span></span> <span data-ttu-id="1b613-164">定型一段較長的時間，可讓模型產生器在搜尋最佳模型時，探索更多的演算法和參數組合。</span><span class="sxs-lookup"><span data-stu-id="1b613-164">Training for a longer period of time allows Model Builder to explore a larger number of algorithms and combination of parameters in search of the best model.</span></span>
1. <span data-ttu-id="1b613-165">選取 [開始定型]。</span><span class="sxs-lookup"><span data-stu-id="1b613-165">Select **Start Training**.</span></span>

    <span data-ttu-id="1b613-166">在整個定型程序期間，進度資料會顯示在定型步驟的 `Progress` 區段中。</span><span class="sxs-lookup"><span data-stu-id="1b613-166">Throughout the training process, progress data is displayed in the `Progress` section of the train step.</span></span>

    - <span data-ttu-id="1b613-167">[狀態] 會顯示定型程序的完成狀態。</span><span class="sxs-lookup"><span data-stu-id="1b613-167">Status displays the completion status of the training process.</span></span>
    - <span data-ttu-id="1b613-168">[最佳正確性] 會顯示模型產生器到目前為止所找到執行效能最佳模型的正確性。</span><span class="sxs-lookup"><span data-stu-id="1b613-168">Best accuracy displays the accuracy of the best performing model found by Model Builder so far.</span></span> <span data-ttu-id="1b613-169">正確性越高，表示模型針對測試資料的預測越正確。</span><span class="sxs-lookup"><span data-stu-id="1b613-169">Higher accuracy means the model predicted more correctly on test data.</span></span>
    - <span data-ttu-id="1b613-170">[最佳演算法] 會顯示模型產生器到目前為止所執行演算法中效能最佳的演算法名稱。</span><span class="sxs-lookup"><span data-stu-id="1b613-170">Best algorithm displays the name of the best performing algorithm performed found by Model Builder so far.</span></span>
    - <span data-ttu-id="1b613-171">[上一個演算法] 會顯示模型產生器最近一次用來定型模型的演算法名稱。</span><span class="sxs-lookup"><span data-stu-id="1b613-171">Last algorithm displays the name of the algorithm most recently used by Model Builder to train the model.</span></span>

1. <span data-ttu-id="1b613-172">定型完成後，請選取 [**評估**] 連結以移至下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="1b613-172">Once training is complete, select the **evaluate** link to move to the next step.</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="1b613-173">評估模型</span><span class="sxs-lookup"><span data-stu-id="1b613-173">Evaluate the model</span></span>

<span data-ttu-id="1b613-174">定型步驟之結果將會是具備最佳效能的單一模型。</span><span class="sxs-lookup"><span data-stu-id="1b613-174">The result of the training step will be one model which had the best performance.</span></span> <span data-ttu-id="1b613-175">在模型產生器工具的評估步驟中，[輸出] 區段會包含最佳**模型**專案中最佳執行模型所使用的演算法，以及最佳**模型精確度**中的計量。</span><span class="sxs-lookup"><span data-stu-id="1b613-175">In the evaluate step of the Model Builder tool, the output section, will contain the algorithm used by the best performing model in the **Best Model** entry along with metrics in **Best Model Accuracy**.</span></span> <span data-ttu-id="1b613-176">此外，還會具備一個摘要表，其中包含前五個模型及其計量。</span><span class="sxs-lookup"><span data-stu-id="1b613-176">Additionally, a summary table containing top five models and their metrics.</span></span>

<span data-ttu-id="1b613-177">若您不滿意您的正確性計量，可嘗試及改善模型正確性的一些簡單方法為增加定型模型的時間，或是使用更多資料。</span><span class="sxs-lookup"><span data-stu-id="1b613-177">If you're not satisfied with your accuracy metrics, some easy ways to try and improve model accuracy are to increase the amount of time to train the model or use more data.</span></span> <span data-ttu-id="1b613-178">否則，請選取 [程式**代碼**] 連結，以移至模型產生器工具中的最後一個步驟。</span><span class="sxs-lookup"><span data-stu-id="1b613-178">Otherwise, select the **code** link to move to the final step in the Model Builder tool.</span></span>

## <a name="add-the-code-to-make-predictions"></a><span data-ttu-id="1b613-179">新增程式碼來進行預測</span><span class="sxs-lookup"><span data-stu-id="1b613-179">Add the code to make predictions</span></span>

<span data-ttu-id="1b613-180">定型程序的結果會建立兩個專案。</span><span class="sxs-lookup"><span data-stu-id="1b613-180">Two projects will be created as a result of the training process.</span></span>

### <a name="reference-the-trained-model"></a><span data-ttu-id="1b613-181">參考定型的模型</span><span class="sxs-lookup"><span data-stu-id="1b613-181">Reference the trained model</span></span>

1. <span data-ttu-id="1b613-182">在模型產生器工具的程式*代碼*步驟中，選取 [**加入專案**]，將自動產生的專案加入至方案。</span><span class="sxs-lookup"><span data-stu-id="1b613-182">In the *code* step of the Model Builder tool, select **Add Projects** to add the autogenerated projects to the solution.</span></span>

    <span data-ttu-id="1b613-183">下列專案應該會出現在**方案總管**中：</span><span class="sxs-lookup"><span data-stu-id="1b613-183">The following projects should appear in the **Solution Explorer**:</span></span>

    - <span data-ttu-id="1b613-184">*SentimentRazorML. consoleapp.exe*：包含模型定型和預測程式碼的 .NET Core 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="1b613-184">*SentimentRazorML.ConsoleApp*: A .NET Core Console application that contains the model training and prediction code.</span></span>
    - <span data-ttu-id="1b613-185">*SentimentRazorML。模型*：.NET Standard 類別庫，其中包含定義輸入和輸出模型資料之架構的資料模型，以及定型期間所儲存的最佳執行模型版本。</span><span class="sxs-lookup"><span data-stu-id="1b613-185">*SentimentRazorML.Model*: A .NET Standard class library containing the data models that define the schema of input and output model data as well as the saved version of the best performing model during training.</span></span>

    <span data-ttu-id="1b613-186">在本教學課程中，只會使用*SentimentRazorML 模型*專案，因為會在*SentimentRazor* web 應用程式中，而不是在主控台中進行預測。</span><span class="sxs-lookup"><span data-stu-id="1b613-186">For this tutorial, only the *SentimentRazorML.Model* project is used because predictions will be made in the *SentimentRazor* web application rather than in the console.</span></span> <span data-ttu-id="1b613-187">雖然*SentimentRazorML*不會用於計分，但它可以用來在稍後使用新資料重新定型模型。</span><span class="sxs-lookup"><span data-stu-id="1b613-187">Although the *SentimentRazorML.ConsoleApp* won't be used for scoring, it can be used to retrain the model using new data at a later time.</span></span> <span data-ttu-id="1b613-188">不過，重新定型已超出本教學課程的範圍。</span><span class="sxs-lookup"><span data-stu-id="1b613-188">Retraining is outside the scope of this tutorial though.</span></span>

### <a name="configure-the-predictionengine-pool"></a><span data-ttu-id="1b613-189">設定 PredictionEngine 集區</span><span class="sxs-lookup"><span data-stu-id="1b613-189">Configure the PredictionEngine pool</span></span>

<span data-ttu-id="1b613-190">若要進行單一預測，您必須建立[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)。</span><span class="sxs-lookup"><span data-stu-id="1b613-190">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="1b613-191">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) 不是安全執行緒。</span><span class="sxs-lookup"><span data-stu-id="1b613-191">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="1b613-192">此外，您必須在應用程式內需要的任何地方建立它的實例。</span><span class="sxs-lookup"><span data-stu-id="1b613-192">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="1b613-193">當您的應用程式成長時，此進程可能會變得難以管理。</span><span class="sxs-lookup"><span data-stu-id="1b613-193">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="1b613-194">為了改善效能和執行緒安全性，請使用相依性插入和 `PredictionEnginePool` 服務的組合，這會建立[@no__t 4](xref:Microsoft.ML.PredictionEngine%602)物件的[@no__t 2](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) ，以便在整個應用程式中使用。</span><span class="sxs-lookup"><span data-stu-id="1b613-194">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

1. <span data-ttu-id="1b613-195">安裝*Microsoft.Extensions.ML* NuGet 套件：</span><span class="sxs-lookup"><span data-stu-id="1b613-195">Install the *Microsoft.Extensions.ML* NuGet package:</span></span>

    1. <span data-ttu-id="1b613-196">在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="1b613-196">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span>
    1. <span data-ttu-id="1b613-197">選擇 "nuget.org" 作為套件來源。</span><span class="sxs-lookup"><span data-stu-id="1b613-197">Choose "nuget.org" as the Package source.</span></span>
    1. <span data-ttu-id="1b613-198">選取 [**流覽**] 索引標籤，並搜尋**Microsoft.Extensions.ML**。</span><span class="sxs-lookup"><span data-stu-id="1b613-198">Select the **Browse** tab and search for **Microsoft.Extensions.ML**.</span></span>
    1. <span data-ttu-id="1b613-199">在清單中選取套件，然後選取 [**安裝**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1b613-199">Select the package in the list, and select the **Install** button.</span></span>
    1. <span data-ttu-id="1b613-200">選取 [**預覽變更**] 對話方塊上的 [**確定]** 按鈕</span><span class="sxs-lookup"><span data-stu-id="1b613-200">Select the **OK** button on the **Preview Changes** dialog</span></span>
    1. <span data-ttu-id="1b613-201">如果您同意所列套件的授權條款，請選取 [**授權接受**] 對話方塊上的 [**我接受**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1b613-201">Select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="1b613-202">開啟*SentimentRazor*專案中的*Startup.cs*檔案。</span><span class="sxs-lookup"><span data-stu-id="1b613-202">Open the *Startup.cs* file in the *SentimentRazor* project.</span></span>
1. <span data-ttu-id="1b613-203">新增下列 using 語句，以參考*Microsoft.Extensions.ML* NuGet 封裝和*SentimentRazorML*專案：</span><span class="sxs-lookup"><span data-stu-id="1b613-203">Add the following using statements to reference the *Microsoft.Extensions.ML* NuGet package and *SentimentRazorML.Model* project:</span></span>

    ```csharp
    using System.IO;
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

1. <span data-ttu-id="1b613-204">建立全域變數來儲存定型模型檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="1b613-204">Create a global variable to store the location of the trained model file.</span></span>

    ```csharp
    private readonly string _modelPath;
    ```

1. <span data-ttu-id="1b613-205">模型檔案會連同應用程式的元件檔案一起儲存在組建目錄中。</span><span class="sxs-lookup"><span data-stu-id="1b613-205">The model file is stored in the build directory alongside the assembly files of your application.</span></span> <span data-ttu-id="1b613-206">若要讓它更容易存取，請建立一個在`GetAbsolutePath` `Configure`方法之後呼叫的 helper 方法</span><span class="sxs-lookup"><span data-stu-id="1b613-206">To make it easier to access, create a helper method called `GetAbsolutePath` after the `Configure` method</span></span>

    ```csharp
    public static string GetAbsolutePath(string relativePath)
    {
        FileInfo _dataRoot = new FileInfo(typeof(Program).Assembly.Location);
        string assemblyFolderPath = _dataRoot.Directory.FullName;

        string fullPath = Path.Combine(assemblyFolderPath, relativePath);
        return fullPath;
    }    
    ```

1. <span data-ttu-id="1b613-207">在類別的函式中使用`GetAbsolutePath`方法，以`_modelPath`設定 `Startup` 。</span><span class="sxs-lookup"><span data-stu-id="1b613-207">Use the `GetAbsolutePath` method in the `Startup` class constructor to set the `_modelPath`.</span></span>

    ```csharp
    _modelPath = GetAbsolutePath("MLModel.zip");
    ```

1. <span data-ttu-id="1b613-208">在方法中，為您的應用程式設定： `PredictionEnginePool` `ConfigureServices`</span><span class="sxs-lookup"><span data-stu-id="1b613-208">Configure the `PredictionEnginePool` for your application in the `ConfigureServices` method:</span></span>

    ```csharp
    services.AddPredictionEnginePool<ModelInput, ModelOutput>()
            .FromFile(_modelPath);
    ```

### <a name="create-sentiment-analysis-handler"></a><span data-ttu-id="1b613-209">建立情感分析處理常式</span><span class="sxs-lookup"><span data-stu-id="1b613-209">Create sentiment analysis handler</span></span>

<span data-ttu-id="1b613-210">預測將會在應用程式的主頁面中進行。</span><span class="sxs-lookup"><span data-stu-id="1b613-210">Predictions will be made inside the main page of the application.</span></span> <span data-ttu-id="1b613-211">因此，接受使用者輸入並使用`PredictionEnginePool`傳回預測的方法必須加入。</span><span class="sxs-lookup"><span data-stu-id="1b613-211">Therefore, a method that takes the user input and uses the `PredictionEnginePool` to return a prediction needs to be added.</span></span>

1. <span data-ttu-id="1b613-212">開啟位於*Pages*目錄中的*Index.cshtml.cs*檔案，並新增下列 using 語句：</span><span class="sxs-lookup"><span data-stu-id="1b613-212">Open the *Index.cshtml.cs* file located in the *Pages* directory and add the following using statements:</span></span>

    ```csharp
    using Microsoft.Extensions.ML;
    using SentimentRazorML.Model;
    ```

    <span data-ttu-id="1b613-213">若要使用在`PredictionEnginePool` `Startup`類別中設定的，您必須將它插入您想要使用它的模型的函式中。</span><span class="sxs-lookup"><span data-stu-id="1b613-213">In order to use the `PredictionEnginePool` configured in the `Startup` class, you have to inject it into the constructor of the model where you want to use it.</span></span>

1. <span data-ttu-id="1b613-214">新增變數以參考`PredictionEnginePool` `IndexModel`類別內的。</span><span class="sxs-lookup"><span data-stu-id="1b613-214">Add a variable to reference the `PredictionEnginePool` inside the `IndexModel` class.</span></span>

    ```csharp
    private readonly PredictionEnginePool<ModelInput, ModelOutput> _predictionEnginePool;
    ```

1. <span data-ttu-id="1b613-215">在`IndexModel`類別中建立一個函式，並`PredictionEnginePool`將服務插入其中。</span><span class="sxs-lookup"><span data-stu-id="1b613-215">Create a constructor in the `IndexModel` class and inject the `PredictionEnginePool` service into it.</span></span>

    ```csharp
    public IndexModel(PredictionEnginePool<ModelInput, ModelOutput> predictionEnginePool)
    {
        _predictionEnginePool = predictionEnginePool;
    }    
    ```

1. <span data-ttu-id="1b613-216">建立方法處理常式， `PredictionEnginePool`以使用從網頁接收的使用者輸入進行預測。</span><span class="sxs-lookup"><span data-stu-id="1b613-216">Create a method handler that uses the `PredictionEnginePool` to make predictions from user input received from the web page.</span></span>

    1. <span data-ttu-id="1b613-217">在`OnGet`方法下方，建立名為的新方法`OnGetAnalyzeSentiment`</span><span class="sxs-lookup"><span data-stu-id="1b613-217">Below the `OnGet` method, create a new method called `OnGetAnalyzeSentiment`</span></span>

        ```csharp
        public IActionResult OnGetAnalyzeSentiment([FromQuery] string text)
        {

        }
        ```

    1. <span data-ttu-id="1b613-218">在方法內，如果使用者輸入空白或為 null，則傳回中性情感。 `OnGetAnalyzeSentiment`</span><span class="sxs-lookup"><span data-stu-id="1b613-218">Inside the `OnGetAnalyzeSentiment` method, return *Neutral* sentiment if the input from the user is blank or null.</span></span>

        ```csharp
        if (String.IsNullOrEmpty(text)) return Content("Neutral");
        ```

    1. <span data-ttu-id="1b613-219">指定有效的輸入，建立的新實例`ModelInput`。</span><span class="sxs-lookup"><span data-stu-id="1b613-219">Given a valid input, create a new instance of `ModelInput`.</span></span>

        ```csharp
        var input = new ModelInput { SentimentText = text };
        ```

    1. <span data-ttu-id="1b613-220">`PredictionEnginePool`使用來預測情感。</span><span class="sxs-lookup"><span data-stu-id="1b613-220">Use the `PredictionEnginePool` to predict sentiment.</span></span>

        ```csharp
        var prediction = _predictionEnginePool.Predict(input);
        ```

    1. <span data-ttu-id="1b613-221">使用下列程式`bool`代碼，將預測值轉換成有毒或 not 有毒。</span><span class="sxs-lookup"><span data-stu-id="1b613-221">Convert the predicted `bool` value into toxic or not toxic with the following code.</span></span>

        ```csharp
        var sentiment = Convert.ToBoolean(prediction.Prediction) ? "Toxic" : "Not Toxic";
        ```

    1. <span data-ttu-id="1b613-222">最後，將情感回到網頁。</span><span class="sxs-lookup"><span data-stu-id="1b613-222">Finally, return the sentiment back to the web page.</span></span>

        ```csharp
        return Content(sentiment);
        ```

### <a name="configure-the-web-page"></a><span data-ttu-id="1b613-223">設定網頁</span><span class="sxs-lookup"><span data-stu-id="1b613-223">Configure the web page</span></span>

<span data-ttu-id="1b613-224">所傳回`OnGetAnalyzeSentiment`的結果會動態顯示`Index`在網頁上。</span><span class="sxs-lookup"><span data-stu-id="1b613-224">The results returned by the `OnGetAnalyzeSentiment` will be dynamically displayed on the `Index` web page.</span></span>

1. <span data-ttu-id="1b613-225">開啟*Pages*目錄中的*Index. cshtml*檔案，並以下列程式碼取代其內容：</span><span class="sxs-lookup"><span data-stu-id="1b613-225">Open the *Index.cshtml* file in the *Pages* directory and replace its contents with the following code:</span></span>

    [!code-cshtml [IndexPage](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/Pages/Index.cshtml)]

1. <span data-ttu-id="1b613-226">接下來，將 css 樣式程式碼新增至*wwwroot\css*目錄中的*網站 .css*頁面結尾：</span><span class="sxs-lookup"><span data-stu-id="1b613-226">Next, add css styling code to the end of the *site.css* page in the *wwwroot\css* directory:</span></span>

    [!code-css [CssStyling](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/css/site.css#L61-L105)]

1. <span data-ttu-id="1b613-227">之後，請新增`OnGetAnalyzeSentiment`程式碼，以將網頁的輸入傳送至處理常式。</span><span class="sxs-lookup"><span data-stu-id="1b613-227">After that, add code to send inputs from the web page to the `OnGetAnalyzeSentiment` handler.</span></span>

    1. <span data-ttu-id="1b613-228">在位於*wwwroot\js*目錄中的`getSentiment` *網站 .js*檔案中，建立名為的函式，以向`OnGetAnalyzeSentiment`處理常式的使用者輸入提出 GET HTTP 要求。</span><span class="sxs-lookup"><span data-stu-id="1b613-228">In the *site.js* file located in the *wwwroot\js* directory, create a function called `getSentiment` to make a GET HTTP request with the user input to the `OnGetAnalyzeSentiment` handler.</span></span>

        [!code-javascript [GetSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L5-L10)]

    1. <span data-ttu-id="1b613-229">如下所示，新增另一個`updateMarker`名為的函式，以動態方式在情感預測時更新網頁上標記的位置。</span><span class="sxs-lookup"><span data-stu-id="1b613-229">Below that, add another function called `updateMarker` to dynamically update the position of the marker on the web page as sentiment is predicted.</span></span>

        [!code-javascript [UpdateMarkerMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L12-L15)]

    1. <span data-ttu-id="1b613-230">建立名`updateSentiment`為的事件處理常式函式，以取得使用者的輸入、使用`getSentiment`函`OnGetAnalyzeSentiment`式將它傳送至函式，並使用`updateMarker`函數更新標記。</span><span class="sxs-lookup"><span data-stu-id="1b613-230">Create an event handler function called `updateSentiment` to get the input from the user, send it to the `OnGetAnalyzeSentiment` function using the `getSentiment` function and update the marker with the `updateMarker` function.</span></span>

        [!code-javascript [UpdateSentimentMethod](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L17-L34)]

    1. <span data-ttu-id="1b613-231">最後，註冊事件處理常式，並`textarea` `id=Message`使用屬性將它系結至元素。</span><span class="sxs-lookup"><span data-stu-id="1b613-231">Finally, register the event handler and bind it to the `textarea` element with the `id=Message` attribute.</span></span>

        [!code-javascript [UpdateSentimentEvtHandler](~/machinelearning-samples/samples/modelbuilder/BinaryClassification_Sentiment_Razor/SentimentRazor/wwwroot/js/site.js#L36)]

## <a name="run-the-application"></a><span data-ttu-id="1b613-232">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="1b613-232">Run the application</span></span>

<span data-ttu-id="1b613-233">現在您已設定好應用程式，請執行應用程式，以在瀏覽器中啟動。</span><span class="sxs-lookup"><span data-stu-id="1b613-233">Now that your application is set up, run the application which should launch in your browser.</span></span>

<span data-ttu-id="1b613-234">當應用程式啟動時，進入「模型產生器」*是很酷的！*</span><span class="sxs-lookup"><span data-stu-id="1b613-234">When the application launches, enter *Model Builder is cool!*</span></span> <span data-ttu-id="1b613-235">在文字區域中。</span><span class="sxs-lookup"><span data-stu-id="1b613-235">into the text area.</span></span> <span data-ttu-id="1b613-236">所顯示的預測情感應該*不會有毒*。</span><span class="sxs-lookup"><span data-stu-id="1b613-236">The predicted sentiment displayed should be *Not Toxic*.</span></span>

![使用預測的情感視窗執行視窗](./media/sentiment-analysis-model-builder/web-app.png)

<span data-ttu-id="1b613-238">如果您稍後需要參考模型產生器的專案，您可以在`C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools`目錄中找到它們。</span><span class="sxs-lookup"><span data-stu-id="1b613-238">If you need to reference the Model Builder generated projects at a later time inside of another solution, you can find them inside the `C:\Users\%USERNAME%\AppData\Local\Temp\MLVSTools` directory.</span></span>

## <a name="next-steps"></a><span data-ttu-id="1b613-239">後續步驟</span><span class="sxs-lookup"><span data-stu-id="1b613-239">Next steps</span></span>

<span data-ttu-id="1b613-240">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="1b613-240">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="1b613-241">建立 ASP.NET Core Razor Pages 應用程式</span><span class="sxs-lookup"><span data-stu-id="1b613-241">Create an ASP.NET Core Razor Pages application</span></span>
> - <span data-ttu-id="1b613-242">準備並了解資料</span><span class="sxs-lookup"><span data-stu-id="1b613-242">Prepare and understand the data</span></span>
> - <span data-ttu-id="1b613-243">選擇案例</span><span class="sxs-lookup"><span data-stu-id="1b613-243">Choose a scenario</span></span>
> - <span data-ttu-id="1b613-244">載入資料</span><span class="sxs-lookup"><span data-stu-id="1b613-244">Load the data</span></span>
> - <span data-ttu-id="1b613-245">將模型定型</span><span class="sxs-lookup"><span data-stu-id="1b613-245">Train the model</span></span>
> - <span data-ttu-id="1b613-246">評估模型</span><span class="sxs-lookup"><span data-stu-id="1b613-246">Evaluate the model</span></span>
> - <span data-ttu-id="1b613-247">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="1b613-247">Use the model for predictions</span></span>

### <a name="additional-resources"></a><span data-ttu-id="1b613-248">其他資源</span><span class="sxs-lookup"><span data-stu-id="1b613-248">Additional Resources</span></span>

<span data-ttu-id="1b613-249">若要深入了解此教學課程中提及的主題，請瀏覽下列資源：</span><span class="sxs-lookup"><span data-stu-id="1b613-249">To learn more about topics mentioned in this tutorial, visit the following resources:</span></span>

- [<span data-ttu-id="1b613-250">模型建立器案例</span><span class="sxs-lookup"><span data-stu-id="1b613-250">Model Builder Scenarios</span></span>](../automate-training-with-model-builder.md#scenarios)
- [<span data-ttu-id="1b613-251">二元分類</span><span class="sxs-lookup"><span data-stu-id="1b613-251">Binary Classification</span></span>](../resources/glossary.md#binary-classification)
- [<span data-ttu-id="1b613-252">二元分類模型計量</span><span class="sxs-lookup"><span data-stu-id="1b613-252">Binary Classification Model Metrics</span></span>](../resources/metrics.md#metrics-for-binary-classification)
