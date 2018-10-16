---
title: 在情感分析二元分類案例中使用 ML.NET
description: 探索如何在二元分類案例中使用 ML.NET，以了解如何使用情感預測來採取適當的動作。
ms.date: 06/04/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7d2935fafe9dbad28205c8a896d97d80474a686f
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2018
ms.locfileid: "47436137"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a><span data-ttu-id="09cb5-103">教學課程：在情感分析二元分類案例中使用 ML.NET</span><span class="sxs-lookup"><span data-stu-id="09cb5-103">Tutorial: Use ML.NET in a sentiment analysis binary classification scenario</span></span>

> [!NOTE]
> <span data-ttu-id="09cb5-104">此主題參考 ML.NET，此功能目前為公開預覽版，因此内容可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="09cb5-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="09cb5-105">如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) (英文)。</span><span class="sxs-lookup"><span data-stu-id="09cb5-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="09cb5-106">此範例教學課程說明如何使用 Visual Studio 2017 中的 C#，透過 .NET Core 主控台應用程式，使用 ML.NET 來建立情感分類器。</span><span class="sxs-lookup"><span data-stu-id="09cb5-106">This sample tutorial illustrates using ML.NET to create a sentiment classifier via a .NET Core console application using C# in Visual Studio 2017.</span></span>

<span data-ttu-id="09cb5-107">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="09cb5-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="09cb5-108">了解問題</span><span class="sxs-lookup"><span data-stu-id="09cb5-108">Understand the problem</span></span>
> * <span data-ttu-id="09cb5-109">選取適當的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="09cb5-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="09cb5-110">準備您的資料</span><span class="sxs-lookup"><span data-stu-id="09cb5-110">Prepare your data</span></span>
> * <span data-ttu-id="09cb5-111">建立學習管線</span><span class="sxs-lookup"><span data-stu-id="09cb5-111">Create the learning pipeline</span></span>
> * <span data-ttu-id="09cb5-112">載入分類器</span><span class="sxs-lookup"><span data-stu-id="09cb5-112">Load a classifier</span></span>
> * <span data-ttu-id="09cb5-113">將模型定型</span><span class="sxs-lookup"><span data-stu-id="09cb5-113">Train the model</span></span>
> * <span data-ttu-id="09cb5-114">使用不同的資料集來評估模型</span><span class="sxs-lookup"><span data-stu-id="09cb5-114">Evaluate the model with a different dataset</span></span>
> * <span data-ttu-id="09cb5-115">使用模型來預測測試資料結果</span><span class="sxs-lookup"><span data-stu-id="09cb5-115">Predict the test data outcomes with the model</span></span>

## <a name="sentiment-analysis-sample-overview"></a><span data-ttu-id="09cb5-116">情感分析範例概觀</span><span class="sxs-lookup"><span data-stu-id="09cb5-116">Sentiment analysis sample overview</span></span>

<span data-ttu-id="09cb5-117">範例是一個主控台應用程式，會使用 ML.NET 來定型模型，以將情感分類並預測為正面或負面。</span><span class="sxs-lookup"><span data-stu-id="09cb5-117">The sample is a console app that uses ML.NET to train a model that classifies and predicts sentiment as either positive or negative.</span></span> <span data-ttu-id="09cb5-118">它也會使用第二資料集來評估模型，以進行品質分析。</span><span class="sxs-lookup"><span data-stu-id="09cb5-118">It also evaluates the model with a second dataset for quality analysis.</span></span> <span data-ttu-id="09cb5-119">情感資料集來自 WikiDetox 專案。</span><span class="sxs-lookup"><span data-stu-id="09cb5-119">The sentiment datasets are from the WikiDetox project.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="09cb5-120">必要條件</span><span class="sxs-lookup"><span data-stu-id="09cb5-120">Prerequisites</span></span>

* <span data-ttu-id="09cb5-121">已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)。</span><span class="sxs-lookup"><span data-stu-id="09cb5-121">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="09cb5-122">[維基百科 Detox 行資料定位字元分隔檔案 (wikiPedia-detox-250-line-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv)。</span><span class="sxs-lookup"><span data-stu-id="09cb5-122">The [Wikipedia detox line data tab separated file (wikiPedia-detox-250-line-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span>
* <span data-ttu-id="09cb5-123">[維基百科 Detox 行測試定位字元分隔檔案 (wikipedia-detox-250-line-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv)。</span><span class="sxs-lookup"><span data-stu-id="09cb5-123">The [Wikipedia detox line test tab separated file (wikipedia-detox-250-line-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="09cb5-124">機器學習工作流程</span><span class="sxs-lookup"><span data-stu-id="09cb5-124">Machine learning workflow</span></span>

<span data-ttu-id="09cb5-125">本教學課程依循機器學習工作流程，可讓程序按順序移入。</span><span class="sxs-lookup"><span data-stu-id="09cb5-125">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="09cb5-126">工作流程階段如下：</span><span class="sxs-lookup"><span data-stu-id="09cb5-126">The workflow phases are as follows:</span></span>

1. <span data-ttu-id="09cb5-127">**了解問題**</span><span class="sxs-lookup"><span data-stu-id="09cb5-127">**Understand the problem**</span></span>
2. <span data-ttu-id="09cb5-128">**內嵌資料**</span><span class="sxs-lookup"><span data-stu-id="09cb5-128">**Ingest the data**</span></span>
3. <span data-ttu-id="09cb5-129">**資料前處理和特徵工程**</span><span class="sxs-lookup"><span data-stu-id="09cb5-129">**Data preprocess and feature engineering**</span></span>
4. <span data-ttu-id="09cb5-130">**定型和預測模型**</span><span class="sxs-lookup"><span data-stu-id="09cb5-130">**Train and predict the model**</span></span>
5. <span data-ttu-id="09cb5-131">**評估模型**</span><span class="sxs-lookup"><span data-stu-id="09cb5-131">**Evaluate the model**</span></span>
6. <span data-ttu-id="09cb5-132">**模型操作化**</span><span class="sxs-lookup"><span data-stu-id="09cb5-132">**Model operationalization**</span></span>

### <a name="understand-the-problem"></a><span data-ttu-id="09cb5-133">了解問題</span><span class="sxs-lookup"><span data-stu-id="09cb5-133">Understand the problem</span></span>

<span data-ttu-id="09cb5-134">您必須先了解問題，以便將其分解成可支援模型建置和定型的組件。</span><span class="sxs-lookup"><span data-stu-id="09cb5-134">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="09cb5-135">分解問題可讓您預測及評估結果。</span><span class="sxs-lookup"><span data-stu-id="09cb5-135">Breaking the problem down allows you to predict and evaluate the results.</span></span>

<span data-ttu-id="09cb5-136">本教學課程的問題是要了解傳入的網站評論情感，以採取適當的動作。</span><span class="sxs-lookup"><span data-stu-id="09cb5-136">The problem for this tutorial is to understand incoming website comment sentiment to take the appropriate action.</span></span>

<span data-ttu-id="09cb5-137">針對要用來將模型定型的資料，您可以將問題分解成情感文字和情感值，以及可評估並操作使用的預測情感值。</span><span class="sxs-lookup"><span data-stu-id="09cb5-137">You can break down the problem to the sentiment text and sentiment value for the data you want to train the model with, and a predicted sentiment value that you can evaluate and then use operationally.</span></span>

<span data-ttu-id="09cb5-138">接著，您需要**判斷**該情感，這可協助您選取機器學習工作。</span><span class="sxs-lookup"><span data-stu-id="09cb5-138">You then need to **determine** the sentiment, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="09cb5-139">選取適當的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="09cb5-139">Select the appropriate machine learning task</span></span>

<span data-ttu-id="09cb5-140">處理此問題時，您會知道下列事實：</span><span class="sxs-lookup"><span data-stu-id="09cb5-140">With this problem, you know the following facts:</span></span>

<span data-ttu-id="09cb5-141">定型資料：網站評論可能是正面的，也可能是負面的 (**情感**)。</span><span class="sxs-lookup"><span data-stu-id="09cb5-141">Training data: website comments can be positive or negative (**sentiment**).</span></span>
<span data-ttu-id="09cb5-142">預測新網站評論的**情感** (正面或負面)，例如在以下範例中：</span><span class="sxs-lookup"><span data-stu-id="09cb5-142">Predict the **sentiment** of a new website comment, either positive or negative, such as in the following examples:</span></span>

* <span data-ttu-id="09cb5-143">請避免在維基百科中新增毫無意義的內容。</span><span class="sxs-lookup"><span data-stu-id="09cb5-143">Please refrain from adding nonsense to Wikipedia.</span></span>
* <span data-ttu-id="09cb5-144">他是最棒的，而文章應該就那樣說。</span><span class="sxs-lookup"><span data-stu-id="09cb5-144">He is the best, and the article should say that.</span></span>

<span data-ttu-id="09cb5-145">分類機器學習工作最適合用於此案例。</span><span class="sxs-lookup"><span data-stu-id="09cb5-145">The classification machine learning task is best suited for this scenario.</span></span>

### <a name="about-the-classification-task"></a><span data-ttu-id="09cb5-146">關於分類工作</span><span class="sxs-lookup"><span data-stu-id="09cb5-146">About the classification task</span></span>

<span data-ttu-id="09cb5-147">分類是一項機器學習工作，會使用資料來**判斷**項目或資料列的分類、類型或類別。</span><span class="sxs-lookup"><span data-stu-id="09cb5-147">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="09cb5-148">例如，您可以使用分類來：</span><span class="sxs-lookup"><span data-stu-id="09cb5-148">For example, you can use classification to:</span></span>

* <span data-ttu-id="09cb5-149">識別情感是正面還是負面。</span><span class="sxs-lookup"><span data-stu-id="09cb5-149">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="09cb5-150">將電子郵件分類為垃圾郵件或正常郵件。</span><span class="sxs-lookup"><span data-stu-id="09cb5-150">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="09cb5-151">判斷病患的實驗樣本是否有癌症病兆。</span><span class="sxs-lookup"><span data-stu-id="09cb5-151">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="09cb5-152">依客戶回應銷售活動的傾向來分類客戶。</span><span class="sxs-lookup"><span data-stu-id="09cb5-152">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="09cb5-153">分類工作通常是下列其中一個類型：</span><span class="sxs-lookup"><span data-stu-id="09cb5-153">Classification tasks are frequently one of the following types:</span></span>

* <span data-ttu-id="09cb5-154">二元：不是 A 就是 B。</span><span class="sxs-lookup"><span data-stu-id="09cb5-154">Binary: either A or B.</span></span>
* <span data-ttu-id="09cb5-155">多元分類：可使用單一模型來預測的多重分類。</span><span class="sxs-lookup"><span data-stu-id="09cb5-155">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="09cb5-156">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="09cb5-156">Create a console application</span></span>

1. <span data-ttu-id="09cb5-157">開啟 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="09cb5-157">Open Visual Studio 2017.</span></span> <span data-ttu-id="09cb5-158">從功能表列中選取 [檔案]  >  [新增]  >  [專案]。</span><span class="sxs-lookup"><span data-stu-id="09cb5-158">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="09cb5-159">在 [新增專案] 對話方塊中，選取 [Visual C#] 節點，然後選取 [.NET Core] 節點。</span><span class="sxs-lookup"><span data-stu-id="09cb5-159">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="09cb5-160">然後選取 [主控台應用程式 (.NET Core)] 專案範本。</span><span class="sxs-lookup"><span data-stu-id="09cb5-160">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="09cb5-161">在 [名稱] 文字方塊中，輸入 "SentimentAnalysis"，然後選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="09cb5-161">In the **Name** text box, type "SentimentAnalysis" and then select the **OK** button.</span></span>

2. <span data-ttu-id="09cb5-162">在您的專案中建立一個名為 *Data* 的目錄以儲存資料集檔案：</span><span class="sxs-lookup"><span data-stu-id="09cb5-162">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="09cb5-163">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [新增] > [新增資料夾]。</span><span class="sxs-lookup"><span data-stu-id="09cb5-163">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="09cb5-164">輸入 "Data"，然後按 Enter。</span><span class="sxs-lookup"><span data-stu-id="09cb5-164">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="09cb5-165">安裝「Microsoft.ML NuGet 套件」：</span><span class="sxs-lookup"><span data-stu-id="09cb5-165">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="09cb5-166">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="09cb5-166">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="09cb5-167">選擇 "nuget.org" 作為 [套件來源]，選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="09cb5-167">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="09cb5-168">在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。</span><span class="sxs-lookup"><span data-stu-id="09cb5-168">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="09cb5-169">準備您的資料</span><span class="sxs-lookup"><span data-stu-id="09cb5-169">Prepare your data</span></span>

1. <span data-ttu-id="09cb5-170">下載 [WikiPedia detox-250-line-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) 和 [wikipedia-detox-250-line-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) 資料集，並將它們儲存至先前建立的 [Data] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="09cb5-170">Download the [WikiPedia detox-250-line-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) and the [wikipedia-detox-250-line-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="09cb5-171">第一個資料集會將機器學習模型定型，第二個資料集則可用來評估您模型的準確率。</span><span class="sxs-lookup"><span data-stu-id="09cb5-171">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="09cb5-172">在 [方案總管] 中，於每個 \*.tsv 檔案上按一下滑鼠右鍵，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="09cb5-172">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="09cb5-173">在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。</span><span class="sxs-lookup"><span data-stu-id="09cb5-173">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="09cb5-174">建立類別及定義路徑</span><span class="sxs-lookup"><span data-stu-id="09cb5-174">Create classes and define paths</span></span>

<span data-ttu-id="09cb5-175">在 *Program.cs* 檔案頂端新增下列額外的 `using` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="09cb5-175">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="09cb5-176">您必須建立三個全域欄位，以保存最近所下載檔案的路徑：</span><span class="sxs-lookup"><span data-stu-id="09cb5-176">You need to create three global fields to hold the paths to the recently downloaded files:</span></span>

* <span data-ttu-id="09cb5-177">`_dataPath` 包含用來將模型定型的資料集路徑。</span><span class="sxs-lookup"><span data-stu-id="09cb5-177">`_dataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="09cb5-178">`_testDataPath` 包含用來評估模型的資料集路徑。</span><span class="sxs-lookup"><span data-stu-id="09cb5-178">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="09cb5-179">`_modelPath` 包含用來儲存定型模型的路徑。</span><span class="sxs-lookup"><span data-stu-id="09cb5-179">`_modelPath` has the path where the trained model is saved.</span></span>

<span data-ttu-id="09cb5-180">將下列程式碼新增至緊接在 `Main` 方法上方的一行，以指定這些路徑：</span><span class="sxs-lookup"><span data-stu-id="09cb5-180">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Declare file variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#2 "Declare variables to store data files")]

<span data-ttu-id="09cb5-181">您必須為輸入資料和預測建立一些類別。</span><span class="sxs-lookup"><span data-stu-id="09cb5-181">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="09cb5-182">將新類別新增至專案：</span><span class="sxs-lookup"><span data-stu-id="09cb5-182">Add a new class to your project:</span></span>

1. <span data-ttu-id="09cb5-183">在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="09cb5-183">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="09cb5-184">在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *SentimentData.cs*。</span><span class="sxs-lookup"><span data-stu-id="09cb5-184">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="09cb5-185">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="09cb5-185">Then, select the **Add** button.</span></span>

    <span data-ttu-id="09cb5-186">*SentimentData.cs* 檔案隨即在程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="09cb5-186">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="09cb5-187">將以下 `using` 陳述式新增至 *SentimentData.cs* 頂端：</span><span class="sxs-lookup"><span data-stu-id="09cb5-187">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#1 "Add necessary usings")]

<span data-ttu-id="09cb5-188">移除現有的類別定義，然後將下列程式碼 (具有 `SentimentData` 和 `SentimentPrediction` 這兩個類別) 新增至 *SentimentData.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="09cb5-188">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#2 "Declare data record types")]

<span data-ttu-id="09cb5-189">`SentimentData` 是輸入資料集類別，並包含一個情感值為正數或負數的 `float` (`Sentiment`)，以及一個評論字串 (`SentimentText`)。</span><span class="sxs-lookup"><span data-stu-id="09cb5-189">`SentimentData` is the input dataset class and has a `float` (`Sentiment`) that has a value for sentiment of either positive or negative, and a string for the comment (`SentimentText`).</span></span> <span data-ttu-id="09cb5-190">兩個欄位都有連結的 `Column` 屬性。</span><span class="sxs-lookup"><span data-stu-id="09cb5-190">Both fields have `Column` attributes attached to them.</span></span> <span data-ttu-id="09cb5-191">此屬性描述資料檔中每個欄位的順序，以及哪一個是 `Label` 欄位。</span><span class="sxs-lookup"><span data-stu-id="09cb5-191">This attribute describes the order of each field in the data file, and which is the `Label` field.</span></span> <span data-ttu-id="09cb5-192">`SentimentPrediction` 是在模型定型後，用來進行預測的類別。</span><span class="sxs-lookup"><span data-stu-id="09cb5-192">`SentimentPrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="09cb5-193">它包含一個單一布林值 (`Sentiment`) 和一個 `PredictedLabel` `ColumnName` 屬性。</span><span class="sxs-lookup"><span data-stu-id="09cb5-193">It has a single boolean (`Sentiment`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="09cb5-194">`Label` 會用來建立和定型模型，也會與第二資料集搭配使用來評估模型。</span><span class="sxs-lookup"><span data-stu-id="09cb5-194">The `Label` is used to create and train the model, and it's also used with a second dataset to evaluate the model.</span></span> <span data-ttu-id="09cb5-195">`PredictedLabel` 的使用時機是在進行預測和評估的期間。</span><span class="sxs-lookup"><span data-stu-id="09cb5-195">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="09cb5-196">就評估而言，會使用含有定型資料、預設值及模型的輸入。</span><span class="sxs-lookup"><span data-stu-id="09cb5-196">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="09cb5-197">在 *Program.cs* 檔案中，以 `async Task` 取代 `void` 來變更 `Main` 方法簽章，如以下範例所示：</span><span class="sxs-lookup"><span data-stu-id="09cb5-197">In the *Program.cs* file, change the `Main` method signature by replacing `void` with `async Task`, as in the following example:</span></span>

```csharp
static async Task Main(string[] args) 
{

}
```

<span data-ttu-id="09cb5-198">您需將 `async` 新增至傳回類型為 <xref:System.Threading.Tasks.Task> 的 `Main`，因為稍後會將模型儲存成 ZIP 檔案，而程式必須等待，直到該外部工作完成為止。</span><span class="sxs-lookup"><span data-stu-id="09cb5-198">You add `async` to `Main` with a <xref:System.Threading.Tasks.Task> return type because you're saving the model to a zip file later, and the program needs to wait until that external task completes.</span></span>

> [!NOTE]
> <span data-ttu-id="09cb5-199">「非同步主要」方法可讓您在 `Main` 方法中使用 `await`。</span><span class="sxs-lookup"><span data-stu-id="09cb5-199">An *async main* method enables you to use `await` in your `Main` method.</span></span> <span data-ttu-id="09cb5-200">如需詳細資訊，請參閱 C# 程式設計指南中的[非同步主要](../../../docs/csharp/programming-guide/main-and-command-args/index.md)主題。</span><span class="sxs-lookup"><span data-stu-id="09cb5-200">For more information, see the [async main](../../../docs/csharp/programming-guide/main-and-command-args/index.md) topic in the C# programming guide.</span></span>

<span data-ttu-id="09cb5-201">在 `Main` 方法中，以下列程式碼取代 `Console.WriteLine("Hello World!")`：</span><span class="sxs-lookup"><span data-stu-id="09cb5-201">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[Train](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#3 "Train your model")]

<span data-ttu-id="09cb5-202">`Train` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="09cb5-202">The `Train` method executes the following tasks:</span></span>

* <span data-ttu-id="09cb5-203">載入或內嵌資料。</span><span class="sxs-lookup"><span data-stu-id="09cb5-203">Loads or ingests the data.</span></span>
* <span data-ttu-id="09cb5-204">對資料進行前處理和特徵化。</span><span class="sxs-lookup"><span data-stu-id="09cb5-204">Preprocesses and featurizes the data.</span></span>
* <span data-ttu-id="09cb5-205">將模型定型。</span><span class="sxs-lookup"><span data-stu-id="09cb5-205">Trains the model.</span></span>
* <span data-ttu-id="09cb5-206">根據測試資料預測情感。</span><span class="sxs-lookup"><span data-stu-id="09cb5-206">Predicts sentiment based on test data.</span></span>

<span data-ttu-id="09cb5-207">請使用下列程式碼，在緊接著 `Main` 方法之後，建立 `Train` 方法：</span><span class="sxs-lookup"><span data-stu-id="09cb5-207">Create the `Train` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static async Task<PredictionModel<SentimentData, SentimentPrediction>> Train()
{

}
```

## <a name="ingest-the-data"></a><span data-ttu-id="09cb5-208">內嵌資料</span><span class="sxs-lookup"><span data-stu-id="09cb5-208">Ingest the data</span></span>

<span data-ttu-id="09cb5-209">把將包含資料載入、資料處理/特徵化及模型的新 <xref:Microsoft.ML.LearningPipeline> 執行個體初始化。</span><span class="sxs-lookup"><span data-stu-id="09cb5-209">Initialize a new instance of <xref:Microsoft.ML.LearningPipeline> that will include the data loading, data processing/featurization, and model.</span></span> <span data-ttu-id="09cb5-210">將下列程式碼新增為 `Train` 方法的第一行：</span><span class="sxs-lookup"><span data-stu-id="09cb5-210">Add the following code as the first line of the `Train` method:</span></span>

[!code-csharp[LearningPipeline](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#5 "Create a learning pipeline")]

<span data-ttu-id="09cb5-211"><xref:Microsoft.ML.Data.TextLoader> 物件是管線的第一個部分，並且會載入定型檔案資料。</span><span class="sxs-lookup"><span data-stu-id="09cb5-211">The <xref:Microsoft.ML.Data.TextLoader> object is the first part of the pipeline, and loads the training file data.</span></span>

[!code-csharp[TextLoader](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#6 "Add a text loader to the pipeline")]

## <a name="data-preprocess-and-feature-engineering"></a><span data-ttu-id="09cb5-212">資料前處理和特徵工程</span><span class="sxs-lookup"><span data-stu-id="09cb5-212">Data preprocess and feature engineering</span></span>

<span data-ttu-id="09cb5-213">資料前處理和清除是相當重要的工作，發生在有效地使用資料集來進行機器學習之前。</span><span class="sxs-lookup"><span data-stu-id="09cb5-213">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="09cb5-214">原始資料通常雜訊多且不可靠，而可能遺漏值。</span><span class="sxs-lookup"><span data-stu-id="09cb5-214">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="09cb5-215">使用資料時，如果未進行這些模型化工作，可能會產生誤導的結果。</span><span class="sxs-lookup"><span data-stu-id="09cb5-215">Using data without these modeling tasks can produce misleading results.</span></span> <span data-ttu-id="09cb5-216">ML.NET 的轉換管線可讓您撰寫一組自訂的轉換，可在定型或測試之前先套用到您的資料。</span><span class="sxs-lookup"><span data-stu-id="09cb5-216">ML.NET's transform pipelines allow you to compose a custom set of transforms that are applied to your data before training or testing.</span></span> <span data-ttu-id="09cb5-217">轉換的主要目的是將資料特徵化。</span><span class="sxs-lookup"><span data-stu-id="09cb5-217">The transforms' primary purpose is for data featurization.</span></span> <span data-ttu-id="09cb5-218">轉換管線的優點在於，在定義轉換管理之後，儲存管線即可將它套用至測試資料。</span><span class="sxs-lookup"><span data-stu-id="09cb5-218">A transform pipeline's advantage is that after transform pipeline definition, save the pipeline to apply it to test data.</span></span>

<span data-ttu-id="09cb5-219">請套用 <xref:Microsoft.ML.Transforms.TextFeaturizer>，以將 `SentimentText` 資料行轉換成機器學習演算法所使用、名為 `Features` 的[數值向量](../resources/glossary.md#numerical-feature-vector)。</span><span class="sxs-lookup"><span data-stu-id="09cb5-219">Apply a <xref:Microsoft.ML.Transforms.TextFeaturizer> to convert the `SentimentText` column into a [numeric vector](../resources/glossary.md#numerical-feature-vector) called `Features` used by the machine learning algorithm.</span></span> <span data-ttu-id="09cb5-220">這就是前處理/特徵化步驟。</span><span class="sxs-lookup"><span data-stu-id="09cb5-220">This is the preprocessing/featurization step.</span></span> <span data-ttu-id="09cb5-221">使用 ML.NET 中可用的額外元件可讓您的模型產生更佳的結果。</span><span class="sxs-lookup"><span data-stu-id="09cb5-221">Using additional components available in ML.NET can enable better results with your model.</span></span> <span data-ttu-id="09cb5-222">將 `TextFeaturizer` 新增至管線來作為下一行程式碼：</span><span class="sxs-lookup"><span data-stu-id="09cb5-222">Add `TextFeaturizer` to the pipeline as the next line of code:</span></span>

[!code-csharp[TextFeaturizer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#7 "Add a TextFeaturizer to the pipeline")]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="09cb5-223">選擇學習演算法</span><span class="sxs-lookup"><span data-stu-id="09cb5-223">Choose a learning algorithm</span></span>

<span data-ttu-id="09cb5-224"><xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier> 是您將在此管線中使用的決策樹學習工具。</span><span class="sxs-lookup"><span data-stu-id="09cb5-224">The <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier> object is a decision tree learner you'll use in this pipeline.</span></span> <span data-ttu-id="09cb5-225">與特徵化步驟類似，試驗 ML.NET 中可用的各種不同學習工具並變更其參數會導致不同的結果。</span><span class="sxs-lookup"><span data-stu-id="09cb5-225">Similar to the featurization step, trying out different learners available in ML.NET and changing their parameters leads to different results.</span></span> <span data-ttu-id="09cb5-226">針對微調，您可以設定[超參數](../resources/glossary.md#hyperparameter)，例如 <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumTrees>、<xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumLeaves> 及 <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.MinDocumentsInLeafs>。</span><span class="sxs-lookup"><span data-stu-id="09cb5-226">For tuning, you can set [hyperparameters](../resources/glossary.md#hyperparameter) like <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumTrees>, <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.NumLeaves>, and <xref:Microsoft.ML.Trainers.FastTreeBinaryClassifier.MinDocumentsInLeafs>.</span></span> <span data-ttu-id="09cb5-227">這些超參數是在任何因素影響模型之前設定的，並且為模型專屬。</span><span class="sxs-lookup"><span data-stu-id="09cb5-227">These hyperparameters are set before anything affects the model and are model-specific.</span></span> <span data-ttu-id="09cb5-228">它們可用來微調決策樹以影響效能，因此較大的值會對效能產生負面影響。</span><span class="sxs-lookup"><span data-stu-id="09cb5-228">They're used to tune the decision tree for performance, so larger values can negatively impact performance.</span></span>

<span data-ttu-id="09cb5-229">將下列程式碼加入 `Train` 方法：</span><span class="sxs-lookup"><span data-stu-id="09cb5-229">Add the following code to the `Train` method:</span></span>

[!code-csharp[BinaryClassifier](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#8 "Add a fast binary tree classifier")]

## <a name="train-the-model"></a><span data-ttu-id="09cb5-230">將模型定型</span><span class="sxs-lookup"><span data-stu-id="09cb5-230">Train the model</span></span>

<span data-ttu-id="09cb5-231">您會根據已載入和轉換的資料集將模型 <xref:Microsoft.ML.PredictionModel%602>定型。</span><span class="sxs-lookup"><span data-stu-id="09cb5-231">You train the model, <xref:Microsoft.ML.PredictionModel%602>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="09cb5-232">`pipeline.Train<SentimentData, SentimentPrediction>()` 會將管線定型 (載入資料、將特徵化工具和學習工具定型)。</span><span class="sxs-lookup"><span data-stu-id="09cb5-232">`pipeline.Train<SentimentData, SentimentPrediction>()` trains the pipeline (loads the data, trains the featurizer and learner).</span></span> <span data-ttu-id="09cb5-233">實驗會等到定型之後才會執行。</span><span class="sxs-lookup"><span data-stu-id="09cb5-233">The experiment is not executed until this happens.</span></span>

<span data-ttu-id="09cb5-234">將下列程式碼加入 `Train` 方法：</span><span class="sxs-lookup"><span data-stu-id="09cb5-234">Add the following code to the `Train` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#9 "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="09cb5-235">儲存並傳回所定型以供評估使用的模型</span><span class="sxs-lookup"><span data-stu-id="09cb5-235">Save and Return the model trained to use for evaluation</span></span>

<span data-ttu-id="09cb5-236">此時，您已有一個可整合至任何現有或新 .NET 應用程式的模型。</span><span class="sxs-lookup"><span data-stu-id="09cb5-236">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="09cb5-237">若要將您的模型先儲存成 .zip 檔案再傳回，請將下列程式碼新增至 `Train` 中的下一行：</span><span class="sxs-lookup"><span data-stu-id="09cb5-237">To save your model to a .zip file before returning, add the following code to the next line in `Train`:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#10 "Save the model")]

<span data-ttu-id="09cb5-238">在 `Train` 方法的結尾傳回模型。</span><span class="sxs-lookup"><span data-stu-id="09cb5-238">Return the model at the end of the `Train` method.</span></span>

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#11 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="09cb5-239">評估模型</span><span class="sxs-lookup"><span data-stu-id="09cb5-239">Evaluate the model</span></span>

<span data-ttu-id="09cb5-240">建立並定型模型之後，現在必須使用不同的資料集來評估它，以確保和驗證品質。</span><span class="sxs-lookup"><span data-stu-id="09cb5-240">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="09cb5-241">在 `Evaluate` 方法中，會傳入在 `Train` 中建立的模型以供評估。</span><span class="sxs-lookup"><span data-stu-id="09cb5-241">In the `Evaluate` method, the model created in `Train` is passed in to be evaluated.</span></span> <span data-ttu-id="09cb5-242">在緊接著 `Train` 之後，建立 `Evaluate` 方法，如以下程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="09cb5-242">Create the `Evaluate` method, just after `Train`, as in the following code:</span></span>

```csharp
public static void Evaluate(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

<span data-ttu-id="09cb5-243">`Evaluate` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="09cb5-243">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="09cb5-244">載入測試資料集。</span><span class="sxs-lookup"><span data-stu-id="09cb5-244">Loads the test dataset.</span></span>
* <span data-ttu-id="09cb5-245">建立二元評估工具。</span><span class="sxs-lookup"><span data-stu-id="09cb5-245">Creates the binary evaluator.</span></span>
* <span data-ttu-id="09cb5-246">評估模型並建立計量。</span><span class="sxs-lookup"><span data-stu-id="09cb5-246">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="09cb5-247">顯示計量。</span><span class="sxs-lookup"><span data-stu-id="09cb5-247">Displays the metrics.</span></span>

<span data-ttu-id="09cb5-248">請使用下列程式碼，在緊接著 `Train` 方法呼叫底下，從 `Main` 方法新增對新方法的呼叫：</span><span class="sxs-lookup"><span data-stu-id="09cb5-248">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#12 "Call the Evaluate method")]

<span data-ttu-id="09cb5-249"><xref:Microsoft.ML.Data.TextLoader> 類別會載入具有相同結構描述的新測試資料集。</span><span class="sxs-lookup"><span data-stu-id="09cb5-249">The <xref:Microsoft.ML.Data.TextLoader> class loads the new test dataset with the same schema.</span></span> <span data-ttu-id="09cb5-250">您可以使用此資料集來評估模型，以作為品質檢查。</span><span class="sxs-lookup"><span data-stu-id="09cb5-250">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="09cb5-251">將下列程式碼加入 `Evaluate` 方法：</span><span class="sxs-lookup"><span data-stu-id="09cb5-251">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadText](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#13 "Load the test dataset")]

<span data-ttu-id="09cb5-252"><xref:Microsoft.ML.Models.BinaryClassificationEvaluator> 物件會使用指定的資料集來計算 `PredictionModel` 的品質計量。</span><span class="sxs-lookup"><span data-stu-id="09cb5-252">The <xref:Microsoft.ML.Models.BinaryClassificationEvaluator> object computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="09cb5-253">若要查看這些計量，請使用下列程式碼，將評估工具新增為 `Evaluate` 方法中的下一行：</span><span class="sxs-lookup"><span data-stu-id="09cb5-253">To see those metrics, add the evaluator as the next line in the `Evaluate` method, with the following code:</span></span>

[!code-csharp[BinaryEvaluator](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#14 "Create the binary evaluator")]

<span data-ttu-id="09cb5-254"><xref:Microsoft.ML.Models.BinaryClassificationMetrics> 包含二元分類評估工具所計算的整體計量。</span><span class="sxs-lookup"><span data-stu-id="09cb5-254">The <xref:Microsoft.ML.Models.BinaryClassificationMetrics> contains the overall metrics computed by binary classification evaluators.</span></span> <span data-ttu-id="09cb5-255">若要顯示這些計量以判斷模型的品質，您必須先取得計量。</span><span class="sxs-lookup"><span data-stu-id="09cb5-255">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="09cb5-256">加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="09cb5-256">Add the following code:</span></span>

[!code-csharp[CreateMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#15 "Evaluate the model and create metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="09cb5-257">顯示模型驗證的計量</span><span class="sxs-lookup"><span data-stu-id="09cb5-257">Displaying the metrics for model validation</span></span>

<span data-ttu-id="09cb5-258">使用下列程式碼來顯示計量、共用結果，然後依結果採取動作：</span><span class="sxs-lookup"><span data-stu-id="09cb5-258">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#16 "Display selected metrics")]

## <a name="predict-the-test-data-outcomes-with-the-model"></a><span data-ttu-id="09cb5-259">使用模型來預測測試資料結果</span><span class="sxs-lookup"><span data-stu-id="09cb5-259">Predict the test data outcomes with the model</span></span>

<span data-ttu-id="09cb5-260">請使用下列程式碼，在緊接著 `Evaluate` 方法之後，建立 `Predict` 方法：</span><span class="sxs-lookup"><span data-stu-id="09cb5-260">Create the `Predict` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
public static void Predict(PredictionModel<SentimentData, SentimentPrediction> model)
{

}
```

<span data-ttu-id="09cb5-261">`Predict` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="09cb5-261">The `Predict` method executes the following tasks:</span></span>

* <span data-ttu-id="09cb5-262">建立測試資料。</span><span class="sxs-lookup"><span data-stu-id="09cb5-262">Creates test data.</span></span>
* <span data-ttu-id="09cb5-263">根據測試資料預測情感。</span><span class="sxs-lookup"><span data-stu-id="09cb5-263">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="09cb5-264">合併測試資料和預測來進行報告。</span><span class="sxs-lookup"><span data-stu-id="09cb5-264">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="09cb5-265">顯示預測的結果。</span><span class="sxs-lookup"><span data-stu-id="09cb5-265">Displays the predicted results.</span></span>

<span data-ttu-id="09cb5-266">請使用下列程式碼，在緊接著 `Evaluate` 方法呼叫底下，從 `Main` 方法新增對新方法的呼叫：</span><span class="sxs-lookup"><span data-stu-id="09cb5-266">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#17 "Call the Predict method")]

<span data-ttu-id="09cb5-267">新增一些評論以測試 `Predict` 方法中定型模型的預測：</span><span class="sxs-lookup"><span data-stu-id="09cb5-267">Add some comments to test the trained model's predictions in the `Predict` method:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#18 "Create test data for predictions")]

<span data-ttu-id="09cb5-268">既然您已有模型，現在即可利用 <xref:Microsoft.ML.PredictionModel.Predict%2A?displayProperty=nameWithType> 方法，使用該模型來預測評論資料的正面或負面情感。</span><span class="sxs-lookup"><span data-stu-id="09cb5-268">Now that you have a model, you can use that to predict the positive or negative sentiment of the comment data using the <xref:Microsoft.ML.PredictionModel.Predict%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="09cb5-269">若要取得預測，請在新資料上使用 `Predict`。</span><span class="sxs-lookup"><span data-stu-id="09cb5-269">To get a prediction, use `Predict` on new data.</span></span> <span data-ttu-id="09cb5-270">請注意，輸入資料是一個字串，且模型包含特徵化。</span><span class="sxs-lookup"><span data-stu-id="09cb5-270">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="09cb5-271">在定型和預測期間，您的管線會同步。</span><span class="sxs-lookup"><span data-stu-id="09cb5-271">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="09cb5-272">您無須特別為預測撰寫前處理/特徵化程式碼，同一個 API 會同時負責批次和單次預測。</span><span class="sxs-lookup"><span data-stu-id="09cb5-272">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#19 "Create predictions of sentiments")]

### <a name="model-operationalization-prediction"></a><span data-ttu-id="09cb5-273">模型操作化：預測</span><span class="sxs-lookup"><span data-stu-id="09cb5-273">Model operationalization: prediction</span></span>

<span data-ttu-id="09cb5-274">顯示 `SentimentText` 和對應的情感預測，以便共用結果並根據結果相應地採取動作。</span><span class="sxs-lookup"><span data-stu-id="09cb5-274">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="09cb5-275">這稱為操作化，其中會使用傳回的資料作為操作原則的一部份。</span><span class="sxs-lookup"><span data-stu-id="09cb5-275">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="09cb5-276">請使用下列 <xref:System.Console.WriteLine?displayProperty=nameWithType> 程式碼來為結果建立標頭：</span><span class="sxs-lookup"><span data-stu-id="09cb5-276">Create a header for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#20 "Display prediction outputs")]

<span data-ttu-id="09cb5-277">顯示預測的結果之前，請先將情感和預測合併在一起，以將原始評論搭配其預測情感一起查看。</span><span class="sxs-lookup"><span data-stu-id="09cb5-277">Before displaying the predicted results, combine the sentiment and prediction together to see the original comment with its predicted sentiment.</span></span> <span data-ttu-id="09cb5-278">下列程式碼會使用 <xref:System.Linq.Enumerable.Zip%2A> 方法來使其發生，因此接下來請新增該程式碼：</span><span class="sxs-lookup"><span data-stu-id="09cb5-278">The following code uses the <xref:System.Linq.Enumerable.Zip%2A> method to make that happen, so add that code next:</span></span>

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#21 "Build the pairs of sentiment data and predictions")]

<span data-ttu-id="09cb5-279">既然您已將 `SentimentText` 和 `Sentiment` 合併成一個類別，現在即可使用 <xref:System.Console.WriteLine?displayProperty=nameWithType> 方法來顯示結果：</span><span class="sxs-lookup"><span data-stu-id="09cb5-279">Now that you've combined the `SentimentText` and `Sentiment` into a class, you can display the results using the <xref:System.Console.WriteLine?displayProperty=nameWithType> method:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#22 "Display the predictions")]

<span data-ttu-id="09cb5-280">由於推斷的元組元素名稱是 C# 7.1 中的新功能，而專案的預設語言版本是 C# 7.0，因此您必須將語言版本變更為 C# 7.1 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="09cb5-280">Because inferred tuple element names are a new feature in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span>
<span data-ttu-id="09cb5-281">若要這樣做，請在 [方案總管] 中的專案節點上按一下滑鼠右鍵，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="09cb5-281">To do that, right-click on the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="09cb5-282">選取 [建置] 索引標籤並選取 [進階] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="09cb5-282">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="09cb5-283">從下拉式清單中，選取 [C# 7.1] (或更新版本)。</span><span class="sxs-lookup"><span data-stu-id="09cb5-283">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="09cb5-284">選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="09cb5-284">Select the **OK** button.</span></span>

## <a name="results"></a><span data-ttu-id="09cb5-285">結果</span><span class="sxs-lookup"><span data-stu-id="09cb5-285">Results</span></span>

<span data-ttu-id="09cb5-286">您的結果應該與以下類似。</span><span class="sxs-lookup"><span data-stu-id="09cb5-286">Your results should be similar to the following.</span></span> <span data-ttu-id="09cb5-287">當管線進行處理時，會顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="09cb5-287">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="09cb5-288">您可能會看到警告或處理訊息。</span><span class="sxs-lookup"><span data-stu-id="09cb5-288">You may see warnings, or processing messages.</span></span> <span data-ttu-id="09cb5-289">為了清晰起見，下列結果中已將這些都移除。</span><span class="sxs-lookup"><span data-stu-id="09cb5-289">These have been removed from the following results for clarity.</span></span>

```

PredictionModel quality metrics evaluation
------------------------------------------
Accuracy: 66.67%
Auc: 94.44%
F1Score: 75.00%

Sentiment Predictions
---------------------
Sentiment: Please refrain from adding nonsense to Wikipedia. | Prediction: Negative
Sentiment: He is the best, and the article should say that. | Prediction: Positive

```

<span data-ttu-id="09cb5-290">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="09cb5-290">Congratulations!</span></span> <span data-ttu-id="09cb5-291">您現在已成功建置可對訊息情感進行分類和預測的機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="09cb5-291">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span> <span data-ttu-id="09cb5-292">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="09cb5-292">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="09cb5-293">後續步驟</span><span class="sxs-lookup"><span data-stu-id="09cb5-293">Next steps</span></span>

<span data-ttu-id="09cb5-294">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="09cb5-294">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="09cb5-295">了解問題</span><span class="sxs-lookup"><span data-stu-id="09cb5-295">Understand the problem</span></span>
> * <span data-ttu-id="09cb5-296">選取適當的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="09cb5-296">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="09cb5-297">準備您的資料</span><span class="sxs-lookup"><span data-stu-id="09cb5-297">Prepare your data</span></span>
> * <span data-ttu-id="09cb5-298">建立學習管線</span><span class="sxs-lookup"><span data-stu-id="09cb5-298">Create the learning pipeline</span></span>
> * <span data-ttu-id="09cb5-299">載入分類器</span><span class="sxs-lookup"><span data-stu-id="09cb5-299">Load a classifier</span></span>
> * <span data-ttu-id="09cb5-300">將模型定型</span><span class="sxs-lookup"><span data-stu-id="09cb5-300">Train the model</span></span>
> * <span data-ttu-id="09cb5-301">使用不同的資料集來評估模型</span><span class="sxs-lookup"><span data-stu-id="09cb5-301">Evaluate the model with a different dataset</span></span>
> * <span data-ttu-id="09cb5-302">使用模型來預測測試資料結果</span><span class="sxs-lookup"><span data-stu-id="09cb5-302">Predict the test data outcomes with the model</span></span>

<span data-ttu-id="09cb5-303">前進到下一個教學課程來深入了解</span><span class="sxs-lookup"><span data-stu-id="09cb5-303">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="09cb5-304">計程車車資預測工具</span><span class="sxs-lookup"><span data-stu-id="09cb5-304">Taxi Fare Predictor</span></span>](taxi-fare.md)
