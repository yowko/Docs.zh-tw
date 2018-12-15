---
title: 在情感分析二元分類案例中使用 ML.NET
description: 探索如何在二元分類案例中使用 ML.NET，以了解如何使用情感預測來採取適當的動作。
ms.date: 11/06/2018
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: cffce6258685502191e1dd33ef8282d664ea2d4c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149649"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a><span data-ttu-id="dd3af-103">教學課程：在情感分析二元分類案例中使用 ML.NET</span><span class="sxs-lookup"><span data-stu-id="dd3af-103">Tutorial: Use ML.NET in a sentiment analysis binary classification scenario</span></span>

> [!NOTE]
> <span data-ttu-id="dd3af-104">此主題參考 ML.NET，此功能目前為公開預覽版，因此内容可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="dd3af-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="dd3af-105">如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) (英文)。</span><span class="sxs-lookup"><span data-stu-id="dd3af-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="dd3af-106">此範例教學課程說明如何使用 Visual Studio 2017 中的 C#，透過 .NET Core 主控台應用程式，使用 ML.NET 來建立情感分類器。</span><span class="sxs-lookup"><span data-stu-id="dd3af-106">This sample tutorial illustrates using ML.NET to create a sentiment classifier via a .NET Core console application using C# in Visual Studio 2017.</span></span>

<span data-ttu-id="dd3af-107">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="dd3af-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="dd3af-108">了解問題</span><span class="sxs-lookup"><span data-stu-id="dd3af-108">Understand the problem</span></span>
> * <span data-ttu-id="dd3af-109">選取適當的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="dd3af-109">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="dd3af-110">準備您的資料</span><span class="sxs-lookup"><span data-stu-id="dd3af-110">Prepare your data</span></span>
> * <span data-ttu-id="dd3af-111">建立學習管線</span><span class="sxs-lookup"><span data-stu-id="dd3af-111">Create the learning pipeline</span></span>
> * <span data-ttu-id="dd3af-112">載入分類器</span><span class="sxs-lookup"><span data-stu-id="dd3af-112">Load a classifier</span></span>
> * <span data-ttu-id="dd3af-113">將模型定型</span><span class="sxs-lookup"><span data-stu-id="dd3af-113">Train the model</span></span>
> * <span data-ttu-id="dd3af-114">使用不同的資料集來評估模型</span><span class="sxs-lookup"><span data-stu-id="dd3af-114">Evaluate the model with a different dataset</span></span>
> * <span data-ttu-id="dd3af-115">使用模型來預測測試資料結果的單一執行個體</span><span class="sxs-lookup"><span data-stu-id="dd3af-115">Predict a single instance of test data outcome with the model</span></span>
> * <span data-ttu-id="dd3af-116">使用載入模型預測測試資料結果</span><span class="sxs-lookup"><span data-stu-id="dd3af-116">Predict the test data outcomes with a loaded model</span></span>

## <a name="sentiment-analysis-sample-overview"></a><span data-ttu-id="dd3af-117">情感分析範例概觀</span><span class="sxs-lookup"><span data-stu-id="dd3af-117">Sentiment analysis sample overview</span></span>

<span data-ttu-id="dd3af-118">範例是一個主控台應用程式，會使用 ML.NET 來定型模型，以將情感分類並預測為正面或負面。</span><span class="sxs-lookup"><span data-stu-id="dd3af-118">The sample is a console app that uses ML.NET to train a model that classifies and predicts sentiment as either positive or negative.</span></span> <span data-ttu-id="dd3af-119">它也會使用第二資料集來評估模型，以進行品質分析。</span><span class="sxs-lookup"><span data-stu-id="dd3af-119">It also evaluates the model with a second dataset for quality analysis.</span></span> <span data-ttu-id="dd3af-120">情感資料集來自 WikiDetox 專案。</span><span class="sxs-lookup"><span data-stu-id="dd3af-120">The sentiment datasets are from the WikiDetox project.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dd3af-121">必要條件</span><span class="sxs-lookup"><span data-stu-id="dd3af-121">Prerequisites</span></span>

* <span data-ttu-id="dd3af-122">已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)。</span><span class="sxs-lookup"><span data-stu-id="dd3af-122">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="dd3af-123">[維基百科 Detox 行資料定位字元分隔檔案 (wikiPedia-detox-250-line-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv)。</span><span class="sxs-lookup"><span data-stu-id="dd3af-123">The [Wikipedia detox line data tab separated file (wikiPedia-detox-250-line-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span>
* <span data-ttu-id="dd3af-124">[維基百科 Detox 行測試定位字元分隔檔案 (wikipedia-detox-250-line-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv)。</span><span class="sxs-lookup"><span data-stu-id="dd3af-124">The [Wikipedia detox line test tab separated file (wikipedia-detox-250-line-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="dd3af-125">機器學習工作流程</span><span class="sxs-lookup"><span data-stu-id="dd3af-125">Machine learning workflow</span></span>

<span data-ttu-id="dd3af-126">本教學課程依循機器學習工作流程，可讓程序按順序移入。</span><span class="sxs-lookup"><span data-stu-id="dd3af-126">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="dd3af-127">工作流程階段如下：</span><span class="sxs-lookup"><span data-stu-id="dd3af-127">The workflow phases are as follows:</span></span>

1. <span data-ttu-id="dd3af-128">**了解問題**</span><span class="sxs-lookup"><span data-stu-id="dd3af-128">**Understand the problem**</span></span>
2. <span data-ttu-id="dd3af-129">**準備您的資料**</span><span class="sxs-lookup"><span data-stu-id="dd3af-129">**Prepare your data**</span></span>
   * <span data-ttu-id="dd3af-130">**載入資料**</span><span class="sxs-lookup"><span data-stu-id="dd3af-130">**Load the data**</span></span>
   * <span data-ttu-id="dd3af-131">**擷取特徵 (轉換您的資料)**</span><span class="sxs-lookup"><span data-stu-id="dd3af-131">**Extract features (Transform your data)**</span></span>
3. <span data-ttu-id="dd3af-132">**建置和定型**</span><span class="sxs-lookup"><span data-stu-id="dd3af-132">**Build and train**</span></span> 
   * <span data-ttu-id="dd3af-133">**將模型定型**</span><span class="sxs-lookup"><span data-stu-id="dd3af-133">**Train the model**</span></span>
   * <span data-ttu-id="dd3af-134">**評估模型**</span><span class="sxs-lookup"><span data-stu-id="dd3af-134">**Evaluate the model**</span></span>
4. <span data-ttu-id="dd3af-135">**執行**</span><span class="sxs-lookup"><span data-stu-id="dd3af-135">**Run**</span></span>
   * <span data-ttu-id="dd3af-136">**模型取用**</span><span class="sxs-lookup"><span data-stu-id="dd3af-136">**Model consumption**</span></span>

### <a name="understand-the-problem"></a><span data-ttu-id="dd3af-137">了解問題</span><span class="sxs-lookup"><span data-stu-id="dd3af-137">Understand the problem</span></span>

<span data-ttu-id="dd3af-138">您必須先了解問題，以便將其分解成可支援模型建置和定型的組件。</span><span class="sxs-lookup"><span data-stu-id="dd3af-138">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="dd3af-139">分解問題可讓您預測及評估結果。</span><span class="sxs-lookup"><span data-stu-id="dd3af-139">Breaking the problem down allows you to predict and evaluate the results.</span></span>

<span data-ttu-id="dd3af-140">本教學課程的問題是要了解傳入的網站評論情感，以採取適當的動作。</span><span class="sxs-lookup"><span data-stu-id="dd3af-140">The problem for this tutorial is to understand incoming website comment sentiment to take the appropriate action.</span></span>

<span data-ttu-id="dd3af-141">針對要用來將模型定型的資料，您可以將問題分解成情感文字和情感值，以及可評估並操作使用的預測情感值。</span><span class="sxs-lookup"><span data-stu-id="dd3af-141">You can break down the problem to the sentiment text and sentiment value for the data you want to train the model with, and a predicted sentiment value that you can evaluate and then use operationally.</span></span>

<span data-ttu-id="dd3af-142">接著，您需要**判斷**該情感，這可協助您選取機器學習工作。</span><span class="sxs-lookup"><span data-stu-id="dd3af-142">You then need to **determine** the sentiment, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="dd3af-143">選取適當的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="dd3af-143">Select the appropriate machine learning task</span></span>

<span data-ttu-id="dd3af-144">處理此問題時，您會知道下列事實：</span><span class="sxs-lookup"><span data-stu-id="dd3af-144">With this problem, you know the following facts:</span></span>

<span data-ttu-id="dd3af-145">將資料定型：網站評論可能為有害的 (1) 或無害的 (0) (**情感**)。</span><span class="sxs-lookup"><span data-stu-id="dd3af-145">Training data: website comments can be toxic (1) or not toxic (0) (**sentiment**).</span></span>
<span data-ttu-id="dd3af-146">預測新網站評論的**情感**，判斷是有害的或無害的，例如下列範例中所示：</span><span class="sxs-lookup"><span data-stu-id="dd3af-146">Predict the **sentiment** of a new website comment, either toxic or not toxic, such as in the following examples:</span></span>

* <span data-ttu-id="dd3af-147">請避免在維基百科中新增毫無意義的內容。</span><span class="sxs-lookup"><span data-stu-id="dd3af-147">Please refrain from adding nonsense to Wikipedia.</span></span>
* <span data-ttu-id="dd3af-148">他是最棒的，而文章應該就那樣說。</span><span class="sxs-lookup"><span data-stu-id="dd3af-148">He is the best, and the article should say that.</span></span>

<span data-ttu-id="dd3af-149">分類機器學習工作最適合用於此案例。</span><span class="sxs-lookup"><span data-stu-id="dd3af-149">The classification machine learning task is best suited for this scenario.</span></span>

### <a name="about-the-classification-task"></a><span data-ttu-id="dd3af-150">關於分類工作</span><span class="sxs-lookup"><span data-stu-id="dd3af-150">About the classification task</span></span>

<span data-ttu-id="dd3af-151">分類是一項機器學習工作，會使用資料來**判斷**項目或資料列的分類、類型或類別。</span><span class="sxs-lookup"><span data-stu-id="dd3af-151">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="dd3af-152">例如，您可以使用分類來：</span><span class="sxs-lookup"><span data-stu-id="dd3af-152">For example, you can use classification to:</span></span>

* <span data-ttu-id="dd3af-153">識別情感是正面還是負面。</span><span class="sxs-lookup"><span data-stu-id="dd3af-153">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="dd3af-154">將電子郵件分類為垃圾郵件或正常郵件。</span><span class="sxs-lookup"><span data-stu-id="dd3af-154">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="dd3af-155">判斷病患的實驗樣本是否有癌症病兆。</span><span class="sxs-lookup"><span data-stu-id="dd3af-155">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="dd3af-156">依客戶回應銷售活動的傾向來分類客戶。</span><span class="sxs-lookup"><span data-stu-id="dd3af-156">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="dd3af-157">分類工作通常是下列其中一個類型：</span><span class="sxs-lookup"><span data-stu-id="dd3af-157">Classification tasks are frequently one of the following types:</span></span>

* <span data-ttu-id="dd3af-158">二元：不是 A 就是 B。</span><span class="sxs-lookup"><span data-stu-id="dd3af-158">Binary: either A or B.</span></span>
* <span data-ttu-id="dd3af-159">多元分類：可使用單一模型來預測的多重分類。</span><span class="sxs-lookup"><span data-stu-id="dd3af-159">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="dd3af-160">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="dd3af-160">Create a console application</span></span>

1. <span data-ttu-id="dd3af-161">開啟 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="dd3af-161">Open Visual Studio 2017.</span></span> <span data-ttu-id="dd3af-162">從功能表列中選取 [檔案]  >  [新增]  >  [專案]。</span><span class="sxs-lookup"><span data-stu-id="dd3af-162">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="dd3af-163">在 [新增專案] 對話方塊中，選取 [Visual C#] 節點，然後選取 [.NET Core] 節點。</span><span class="sxs-lookup"><span data-stu-id="dd3af-163">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="dd3af-164">然後選取 [主控台應用程式 (.NET Core)] 專案範本。</span><span class="sxs-lookup"><span data-stu-id="dd3af-164">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="dd3af-165">在 [名稱] 文字方塊中，輸入 "SentimentAnalysis"，然後選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="dd3af-165">In the **Name** text box, type "SentimentAnalysis" and then select the **OK** button.</span></span>

2. <span data-ttu-id="dd3af-166">在您的專案中建立一個名為 *Data* 的目錄以儲存資料集檔案：</span><span class="sxs-lookup"><span data-stu-id="dd3af-166">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="dd3af-167">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [新增] > [新增資料夾]。</span><span class="sxs-lookup"><span data-stu-id="dd3af-167">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="dd3af-168">輸入 "Data"，然後按 Enter。</span><span class="sxs-lookup"><span data-stu-id="dd3af-168">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="dd3af-169">安裝「Microsoft.ML NuGet 套件」：</span><span class="sxs-lookup"><span data-stu-id="dd3af-169">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="dd3af-170">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="dd3af-170">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="dd3af-171">選擇 "nuget.org" 作為 [套件來源]，選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="dd3af-171">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="dd3af-172">在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。</span><span class="sxs-lookup"><span data-stu-id="dd3af-172">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="dd3af-173">準備您的資料</span><span class="sxs-lookup"><span data-stu-id="dd3af-173">Prepare your data</span></span>

1. <span data-ttu-id="dd3af-174">下載 [WikiPedia detox-250-line-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) 和 [wikipedia-detox-250-line-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) 資料集，並將它們儲存至先前建立的 [Data] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="dd3af-174">Download the [WikiPedia detox-250-line-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) and the [wikipedia-detox-250-line-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="dd3af-175">第一個資料集會將機器學習模型定型，第二個資料集則可用來評估您模型的準確率。</span><span class="sxs-lookup"><span data-stu-id="dd3af-175">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="dd3af-176">在 [方案總管] 中，於每個 \*.tsv 檔案上按一下滑鼠右鍵，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="dd3af-176">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="dd3af-177">在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。</span><span class="sxs-lookup"><span data-stu-id="dd3af-177">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="dd3af-178">建立類別及定義路徑</span><span class="sxs-lookup"><span data-stu-id="dd3af-178">Create classes and define paths</span></span>

<span data-ttu-id="dd3af-179">在 *Program.cs* 檔案頂端新增下列額外的 `using` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="dd3af-179">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="dd3af-180">您需要建立三個全域欄位來持有最近下載之檔案的路徑，還要建立 `TextLoader` 的全域變數：</span><span class="sxs-lookup"><span data-stu-id="dd3af-180">You need to create three global fields to hold the paths to the recently downloaded files, and a global variable for the `TextLoader`:</span></span>

* <span data-ttu-id="dd3af-181">`_trainDataPath` 包含用來將模型定型的資料集路徑。</span><span class="sxs-lookup"><span data-stu-id="dd3af-181">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="dd3af-182">`_testDataPath` 包含用來評估模型的資料集路徑。</span><span class="sxs-lookup"><span data-stu-id="dd3af-182">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="dd3af-183">`_modelPath` 包含用來儲存定型模型的路徑。</span><span class="sxs-lookup"><span data-stu-id="dd3af-183">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="dd3af-184">`_reader` 是 <xref:Microsoft.ML.Runtime.Data.TextLoader>，用來載入並轉換資料集。</span><span class="sxs-lookup"><span data-stu-id="dd3af-184">`_reader` is the <xref:Microsoft.ML.Runtime.Data.TextLoader> used to load and transform the datasets.</span></span>

<span data-ttu-id="dd3af-185">將下列程式碼新增至緊接在 `Main` 方法上方的一行，以指定這些路徑和 `_textLoader` 變數：</span><span class="sxs-lookup"><span data-stu-id="dd3af-185">Add the following code to the line right above the `Main` method to specify those paths and the `_textLoader` variable:</span></span>

[!code-csharp[Declare global variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#2 "Declare global variables")]

<span data-ttu-id="dd3af-186">您必須為輸入資料和預測建立一些類別。</span><span class="sxs-lookup"><span data-stu-id="dd3af-186">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="dd3af-187">將新類別新增至專案：</span><span class="sxs-lookup"><span data-stu-id="dd3af-187">Add a new class to your project:</span></span>

1. <span data-ttu-id="dd3af-188">在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="dd3af-188">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="dd3af-189">在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *SentimentData.cs*。</span><span class="sxs-lookup"><span data-stu-id="dd3af-189">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="dd3af-190">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="dd3af-190">Then, select the **Add** button.</span></span>

    <span data-ttu-id="dd3af-191">*SentimentData.cs* 檔案隨即在程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="dd3af-191">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="dd3af-192">將以下 `using` 陳述式新增至 *SentimentData.cs* 頂端：</span><span class="sxs-lookup"><span data-stu-id="dd3af-192">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#1 "Add necessary usings")]

<span data-ttu-id="dd3af-193">移除現有的類別定義，然後將下列程式碼 (具有 `SentimentData` 和 `SentimentPrediction` 這兩個類別) 新增至 *SentimentData.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="dd3af-193">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#2 "Declare data record types")]

<span data-ttu-id="dd3af-194">`SentimentData` 是輸入資料集類別，並包含一個情感值為正數或負數的 `float` (`Sentiment`)，以及一個評論字串 (`SentimentText`)。</span><span class="sxs-lookup"><span data-stu-id="dd3af-194">`SentimentData` is the input dataset class and has a `float` (`Sentiment`) that has a value for sentiment of either positive or negative, and a string for the comment (`SentimentText`).</span></span> <span data-ttu-id="dd3af-195">兩個欄位都有連結的 `Column` 屬性。</span><span class="sxs-lookup"><span data-stu-id="dd3af-195">Both fields have `Column` attributes attached to them.</span></span> <span data-ttu-id="dd3af-196">此屬性描述資料檔中每個欄位的順序，以及哪一個是 `Label` 欄位。</span><span class="sxs-lookup"><span data-stu-id="dd3af-196">This attribute describes the order of each field in the data file, and which is the `Label` field.</span></span> <span data-ttu-id="dd3af-197">`SentimentPrediction` 是在模型定型後，用來進行預測的類別。</span><span class="sxs-lookup"><span data-stu-id="dd3af-197">`SentimentPrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="dd3af-198">它包含一個單一布林值 (`Sentiment`) 和一個 `PredictedLabel` `ColumnName` 屬性。</span><span class="sxs-lookup"><span data-stu-id="dd3af-198">It has a single boolean (`Sentiment`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="dd3af-199">`Label` 會用來建立和定型模型，也會與第二資料集搭配使用來評估模型。</span><span class="sxs-lookup"><span data-stu-id="dd3af-199">The `Label` is used to create and train the model, and it's also used with a second dataset to evaluate the model.</span></span> <span data-ttu-id="dd3af-200">`PredictedLabel` 的使用時機是在進行預測和評估的期間。</span><span class="sxs-lookup"><span data-stu-id="dd3af-200">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="dd3af-201">就評估而言，會使用含有定型資料、預設值及模型的輸入。</span><span class="sxs-lookup"><span data-stu-id="dd3af-201">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="dd3af-202">使用 ML.NET 建置模型時，您要從建立 `MLContext` 開始。</span><span class="sxs-lookup"><span data-stu-id="dd3af-202">When building a model with ML.NET you start by creating an `MLContext`.</span></span> <span data-ttu-id="dd3af-203">這在概念上類似於在 Entity Framework 中使用的 `DbContext`。</span><span class="sxs-lookup"><span data-stu-id="dd3af-203">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span> <span data-ttu-id="dd3af-204">環境能夠為 ML 作業提供內容，可用來進行例外狀況追蹤和記錄。</span><span class="sxs-lookup"><span data-stu-id="dd3af-204">The environment provides a context for your ML job that can be used for exception tracking and logging.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="dd3af-205">在 Main 中初始化變數</span><span class="sxs-lookup"><span data-stu-id="dd3af-205">Initialize variables in Main</span></span>

<span data-ttu-id="dd3af-206">建立名為 `mlContext` 的變數，並使用 `MLContext` 的新執行個體將它初始化。</span><span class="sxs-lookup"><span data-stu-id="dd3af-206">Create a variable called `mlContext` and initialize it with a new instance of `MLContext`.</span></span>  <span data-ttu-id="dd3af-207">在 `Main` 方法中，以下列程式碼取代 `Console.WriteLine("Hello World!")`：</span><span class="sxs-lookup"><span data-stu-id="dd3af-207">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="dd3af-208">接下來，為了設定資料載入，將 `_textLoader` 全域變數初始化以重複使用它。</span><span class="sxs-lookup"><span data-stu-id="dd3af-208">Next, to setup for data loading initialize the `_textLoader` global variable in order to reuse it.</span></span>  <span data-ttu-id="dd3af-209">請留意到您正在使用 `TextReader`。</span><span class="sxs-lookup"><span data-stu-id="dd3af-209">Notice that you're using a `TextReader`.</span></span> <span data-ttu-id="dd3af-210">當您使用 `TextReader` 建立 `TextLoader` 時，您要傳入需要的內容和啟用自訂功能的 <xref:Microsoft.ML.Runtime.Data.TextLoader.Arguments> 類別。</span><span class="sxs-lookup"><span data-stu-id="dd3af-210">When you create a `TextLoader` using a `TextReader`, you pass in the context needed and the <xref:Microsoft.ML.Runtime.Data.TextLoader.Arguments> class which enables customization.</span></span>

 <span data-ttu-id="dd3af-211">透過將 <xref:Microsoft.ML.Runtime.Data.TextLoader.Column> 物件的陣列傳遞至包含所有資料行名稱及其類別的載入程式，來指定資料結構描述。</span><span class="sxs-lookup"><span data-stu-id="dd3af-211">Specify the data schema by passing an array of <xref:Microsoft.ML.Runtime.Data.TextLoader.Column> objects to the loader containing all the column names and their types.</span></span> <span data-ttu-id="dd3af-212">您先前建立 `SentimentData` 類別時已定義了資料結構描述。</span><span class="sxs-lookup"><span data-stu-id="dd3af-212">You defined the data schema previously when you created our `SentimentData` class.</span></span> <span data-ttu-id="dd3af-213">對於我們的結構描述，第一個資料行 (Label) 是 <xref:System.Boolean> (預測)，第二個資料行 (SentimentText) 是用來預測情感的文字/字串類型特徵。</span><span class="sxs-lookup"><span data-stu-id="dd3af-213">For our schema, the first column (Label) is a <xref:System.Boolean> (the prediction) and the second column (SentimentText) is the feature of type text/string used for predicting the sentiment.</span></span>
<span data-ttu-id="dd3af-214">`TextReader` 類別會傳回完整初始化的 <xref:Microsoft.ML.Runtime.Data.TextLoader></span><span class="sxs-lookup"><span data-stu-id="dd3af-214">The `TextReader` class returns a fully initialized <xref:Microsoft.ML.Runtime.Data.TextLoader></span></span>  

<span data-ttu-id="dd3af-215">若要初始化 `_textLoader` 全域變數以針對需要的資料集重複使用它，請在 `mlContext` 初始化之後加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="dd3af-215">To initialize the `_textLoader` global variable in order to reuse it for the needed datasets, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[initTextReader](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#4 "Initialize the TextReader")]

<span data-ttu-id="dd3af-216">將下列程式碼加入為 `Main` 方法中的下一行程式碼：</span><span class="sxs-lookup"><span data-stu-id="dd3af-216">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[Train](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#5 "Train your model")]

<span data-ttu-id="dd3af-217">`Train` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="dd3af-217">The `Train` method executes the following tasks:</span></span>

* <span data-ttu-id="dd3af-218">載入資料。</span><span class="sxs-lookup"><span data-stu-id="dd3af-218">Loads the data.</span></span>
* <span data-ttu-id="dd3af-219">擷取並轉換資料。</span><span class="sxs-lookup"><span data-stu-id="dd3af-219">Extracts and transforms the data.</span></span>
* <span data-ttu-id="dd3af-220">將模型定型。</span><span class="sxs-lookup"><span data-stu-id="dd3af-220">Trains the model.</span></span>
* <span data-ttu-id="dd3af-221">根據測試資料預測情感。</span><span class="sxs-lookup"><span data-stu-id="dd3af-221">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="dd3af-222">傳回模型。</span><span class="sxs-lookup"><span data-stu-id="dd3af-222">Returns the model.</span></span>

<span data-ttu-id="dd3af-223">請使用下列程式碼，在緊接著 `Main` 方法之後，建立 `Train` 方法：</span><span class="sxs-lookup"><span data-stu-id="dd3af-223">Create the `Train` method, just after the `Main` method, using the following code:</span></span>

```csharp
 public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

<span data-ttu-id="dd3af-224">請注意，有兩個參數傳遞至 Train 方法中；內容 (`mlContext`) 的 `MLContext` 和資料集路徑 (`dataPath`) 的 <xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="dd3af-224">Notice that two parameters are passed into the Train method; a `MLContext` for the context (`mlContext`), and a <xref:System.String> for the dataset path (`dataPath`).</span></span> <span data-ttu-id="dd3af-225">您會將此方法多次用於定型和測試。</span><span class="sxs-lookup"><span data-stu-id="dd3af-225">You're going to use this method more than once for training and testing.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="dd3af-226">載入資料</span><span class="sxs-lookup"><span data-stu-id="dd3af-226">Load the data</span></span>

<span data-ttu-id="dd3af-227">您將使用 `_textLoader` 全域變數搭配 `dataPath` 參數來載入資料。</span><span class="sxs-lookup"><span data-stu-id="dd3af-227">You'll load the data using the `_textLoader` global variable with the `dataPath` parameter.</span></span> <span data-ttu-id="dd3af-228">它會傳回 <xref:Microsoft.ML.Runtime.Data.IDataView>。</span><span class="sxs-lookup"><span data-stu-id="dd3af-228">It returns a <xref:Microsoft.ML.Runtime.Data.IDataView>.</span></span> <span data-ttu-id="dd3af-229">作為 `Transforms` 的輸入和輸出，`DataView` 是基本的資料管線類型，相當於 `LINQ` 的 `IEnumerable`。</span><span class="sxs-lookup"><span data-stu-id="dd3af-229">As the input and output of `Transforms`, a `DataView` is the fundamental data pipeline type, comparable to `IEnumerable` for `LINQ`.</span></span>

<span data-ttu-id="dd3af-230">在 ML.NET 中，資料相當於 SQL 檢視。</span><span class="sxs-lookup"><span data-stu-id="dd3af-230">In ML.NET, data is similar to a SQL view.</span></span> <span data-ttu-id="dd3af-231">它是延遲評估、結構描述化且異質性的。</span><span class="sxs-lookup"><span data-stu-id="dd3af-231">It is lazily evaluated, schematized, and heterogenous.</span></span> <span data-ttu-id="dd3af-232">物件是管線的第一個部分，並且會載入資料。</span><span class="sxs-lookup"><span data-stu-id="dd3af-232">The object is the first part of the pipeline, and loads the data.</span></span> <span data-ttu-id="dd3af-233">在本教學課程中，它會載入資料集，其中包含評論及所對應的有害的或無害的情感。</span><span class="sxs-lookup"><span data-stu-id="dd3af-233">For this tutorial, it loads a dataset with comments and corresponding toxic or non toxic sentiment.</span></span> <span data-ttu-id="dd3af-234">這用來建立模型並加以定型。</span><span class="sxs-lookup"><span data-stu-id="dd3af-234">This is used to create the model, and train it.</span></span>

 <span data-ttu-id="dd3af-235">將下列程式碼新增為 `Train` 方法的第一行：</span><span class="sxs-lookup"><span data-stu-id="dd3af-235">Add the following code as the first line of the `Train` method:</span></span>

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#6 "loading training dataset")]

## <a name="extract-and-transform-the-data"></a><span data-ttu-id="dd3af-236">擷取並轉換資料</span><span class="sxs-lookup"><span data-stu-id="dd3af-236">Extract and transform the data</span></span>

<span data-ttu-id="dd3af-237">資料前處理和清除是相當重要的工作，發生在有效地使用資料集來進行機器學習之前。</span><span class="sxs-lookup"><span data-stu-id="dd3af-237">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="dd3af-238">原始資料通常雜訊多且不可靠，而可能遺漏值。</span><span class="sxs-lookup"><span data-stu-id="dd3af-238">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="dd3af-239">使用資料時，如果未進行這些模型化工作，可能會產生誤導的結果。</span><span class="sxs-lookup"><span data-stu-id="dd3af-239">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="dd3af-240">ML.NET 的轉換管線撰寫一組自訂的轉換，可在定型或測試之前先套用到您的資料。</span><span class="sxs-lookup"><span data-stu-id="dd3af-240">ML.NET's transform pipelines compose a custom set of transforms that are applied to your data before training or testing.</span></span> <span data-ttu-id="dd3af-241">轉換的主要目的是將資料[特徵化](../resources/glossary.md#feature-engineering)。</span><span class="sxs-lookup"><span data-stu-id="dd3af-241">The transforms' primary purpose is data [featurization](../resources/glossary.md#feature-engineering).</span></span> <span data-ttu-id="dd3af-242">機器學習演算法了解[特徵化](../resources/glossary.md#feature)資料，因此下一步是將我們的文字資料轉換成 ML 演算法可辨識的格式。</span><span class="sxs-lookup"><span data-stu-id="dd3af-242">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, so the next step is to transform our textual data into a format that our ML algorithms recognize.</span></span> <span data-ttu-id="dd3af-243">該格式為[數值向量](../resources/glossary.md#numerical-feature-vector)。</span><span class="sxs-lookup"><span data-stu-id="dd3af-243">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="dd3af-244">接下來，呼叫 `mlContext.Transforms.Text.FeaturizeText` 將文字資料行 (`SentimentText`) 轉換成名為 `Features` 的數值向量，機器學習演算法會使用此數值向量。</span><span class="sxs-lookup"><span data-stu-id="dd3af-244">Next, call `mlContext.Transforms.Text.FeaturizeText` which featurizes the text column (`SentimentText`) column into a numeric vector called `Features` used by the machine learning algorithm.</span></span> <span data-ttu-id="dd3af-245">此包裝函式呼叫會傳回 <xref:Microsoft.ML.Runtime.Data.EstimatorChain%601>，可作為有效的管線。</span><span class="sxs-lookup"><span data-stu-id="dd3af-245">This is a wrapper call that returns an <xref:Microsoft.ML.Runtime.Data.EstimatorChain%601> that will effectively be a pipeline.</span></span> <span data-ttu-id="dd3af-246">照一般作法為此 `pipeline` 命名，然後將定型程式附加至 `EstimatorChain`。</span><span class="sxs-lookup"><span data-stu-id="dd3af-246">Name this `pipeline` as you will then append the trainer to the `EstimatorChain`.</span></span> <span data-ttu-id="dd3af-247">將下列程式碼加入為下一行：</span><span class="sxs-lookup"><span data-stu-id="dd3af-247">Add this as the next line of code:</span></span>

[!code-csharp[TextFeaturizingEstimator](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#7 "Add a TextFeaturizingEstimator")]

<span data-ttu-id="dd3af-248">這就是前處理/特徵化步驟。</span><span class="sxs-lookup"><span data-stu-id="dd3af-248">This is the preprocessing/featurization step.</span></span> <span data-ttu-id="dd3af-249">使用 ML.NET 中可用的額外元件可讓您的模型產生更佳的結果。</span><span class="sxs-lookup"><span data-stu-id="dd3af-249">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="dd3af-250">選擇學習演算法</span><span class="sxs-lookup"><span data-stu-id="dd3af-250">Choose a learning algorithm</span></span>

<span data-ttu-id="dd3af-251">若要新增訓練程式，請呼叫會傳回 <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> 的 `mlContext.Transforms.Text.FeaturizeText` 包裝方法。</span><span class="sxs-lookup"><span data-stu-id="dd3af-251">To add the trainer, call the `mlContext.Transforms.Text.FeaturizeText` wrapper method which returns a <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> object.</span></span> <span data-ttu-id="dd3af-252">這是您將在此管線中使用的決策樹學習工具。</span><span class="sxs-lookup"><span data-stu-id="dd3af-252">This is a decision tree learner you'll use in this pipeline.</span></span> <span data-ttu-id="dd3af-253">`FastTreeBinaryClassificationTrainer` 是附加到 `pipeline`，且接受特徵化 `SentimentText` (`Features`) 和 `Label` 輸入參數，以從歷史資料學習。</span><span class="sxs-lookup"><span data-stu-id="dd3af-253">The `FastTreeBinaryClassificationTrainer` is appended to the `pipeline` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

<span data-ttu-id="dd3af-254">將下列程式碼加入 `Train` 方法：</span><span class="sxs-lookup"><span data-stu-id="dd3af-254">Add the following code to the `Train` method:</span></span>

[!code-csharp[FastTreeBinaryClassificationTrainer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#8 "Add a FastTreeBinaryClassificationTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="dd3af-255">將模型定型</span><span class="sxs-lookup"><span data-stu-id="dd3af-255">Train the model</span></span>

<span data-ttu-id="dd3af-256">您會根據已載入和轉換的資料集將模型 <xref:Microsoft.ML.Runtime.Data.TransformerChain%601>定型。</span><span class="sxs-lookup"><span data-stu-id="dd3af-256">You train the model, <xref:Microsoft.ML.Runtime.Data.TransformerChain%601>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="dd3af-257">定義了評估工具之後，我們使用 <xref:Microsoft.ML.Runtime.Data.EstimatorChain%601.Fit%2A> 定型模型，並提供已載入的定型資料。</span><span class="sxs-lookup"><span data-stu-id="dd3af-257">Once the estimator has been defined, you train your model using the <xref:Microsoft.ML.Runtime.Data.EstimatorChain%601.Fit%2A> while providing the already loaded training data.</span></span> <span data-ttu-id="dd3af-258">這會傳回要用於預測的模型。</span><span class="sxs-lookup"><span data-stu-id="dd3af-258">This returns a model to use for predictions.</span></span> <span data-ttu-id="dd3af-259">`pipeline.Fit()` 會定型管線，並根據傳入的 `DataView` 傳回 `Transformer`。</span><span class="sxs-lookup"><span data-stu-id="dd3af-259">`pipeline.Fit()` trains the pipeline and returns a `Transformer` based on the `DataView` passed in.</span></span> <span data-ttu-id="dd3af-260">實驗會等到定型之後才會執行。</span><span class="sxs-lookup"><span data-stu-id="dd3af-260">The experiment is not executed until this happens.</span></span>

<span data-ttu-id="dd3af-261">將下列程式碼加入 `Train` 方法：</span><span class="sxs-lookup"><span data-stu-id="dd3af-261">Add the following code to the `Train` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#9 "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="dd3af-262">儲存並傳回所定型以供評估使用的模型</span><span class="sxs-lookup"><span data-stu-id="dd3af-262">Save and Return the model trained to use for evaluation</span></span>

<span data-ttu-id="dd3af-263">此時，您已有一個可整合至任何現有或新 .NET 應用程式之 <xref:Microsoft.ML.Data.TransformerChain%601> 類型的模型。</span><span class="sxs-lookup"><span data-stu-id="dd3af-263">At this point, you have a model of type <xref:Microsoft.ML.Data.TransformerChain%601> that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="dd3af-264">在 `Train` 方法的結尾傳回模型。</span><span class="sxs-lookup"><span data-stu-id="dd3af-264">Return the model at the end of the `Train` method.</span></span>

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#10 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="dd3af-265">評估模型</span><span class="sxs-lookup"><span data-stu-id="dd3af-265">Evaluate the model</span></span>

<span data-ttu-id="dd3af-266">建立並定型模型之後，現在必須使用不同的資料集來評估它，以確保和驗證品質。</span><span class="sxs-lookup"><span data-stu-id="dd3af-266">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="dd3af-267">在 `Evaluate` 方法中，會傳入在 `Train` 中建立的模型以供評估。</span><span class="sxs-lookup"><span data-stu-id="dd3af-267">In the `Evaluate` method, the model created in `Train` is passed in to be evaluated.</span></span> <span data-ttu-id="dd3af-268">在緊接著 `Train` 之後，建立 `Evaluate` 方法，如以下程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="dd3af-268">Create the `Evaluate` method, just after `Train`, as in the following code:</span></span>

```csharp
public static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="dd3af-269">`Evaluate` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="dd3af-269">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="dd3af-270">載入測試資料集。</span><span class="sxs-lookup"><span data-stu-id="dd3af-270">Loads the test dataset.</span></span>
* <span data-ttu-id="dd3af-271">建立二元評估工具。</span><span class="sxs-lookup"><span data-stu-id="dd3af-271">Creates the binary evaluator.</span></span>
* <span data-ttu-id="dd3af-272">評估模型並建立計量。</span><span class="sxs-lookup"><span data-stu-id="dd3af-272">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="dd3af-273">顯示計量。</span><span class="sxs-lookup"><span data-stu-id="dd3af-273">Displays the metrics.</span></span>

<span data-ttu-id="dd3af-274">請使用下列程式碼，在緊接著 `Train` 方法呼叫底下，從 `Main` 方法新增對新方法的呼叫：</span><span class="sxs-lookup"><span data-stu-id="dd3af-274">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#11 "Call the Evaluate method")]

<span data-ttu-id="dd3af-275">我們將使用先前已初始化的 `_textLoader` 全域變數與 `_testDataPath` 全域欄位來載入測試資料集。</span><span class="sxs-lookup"><span data-stu-id="dd3af-275">You'll load the test dataset using the previously initialized  `_textLoader` global variable with the `_testDataPath` global field.</span></span> <span data-ttu-id="dd3af-276">您可以使用此資料集來評估模型，以作為品質檢查。</span><span class="sxs-lookup"><span data-stu-id="dd3af-276">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="dd3af-277">將下列程式碼加入 `Evaluate` 方法：</span><span class="sxs-lookup"><span data-stu-id="dd3af-277">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#12 "Load the test dataset")]

<span data-ttu-id="dd3af-278">接下來，您將使用機器學習 `model` 參數 (轉換器) 來輸入特徵並傳回預測。</span><span class="sxs-lookup"><span data-stu-id="dd3af-278">Next, you'll use the machine learning `model` parameter (a transformer) to input the features and return predictions.</span></span> <span data-ttu-id="dd3af-279">將下列程式碼加入 `Evaluate` 方法中作為下一行：</span><span class="sxs-lookup"><span data-stu-id="dd3af-279">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#13 "Predict using the Transformer")]

<span data-ttu-id="dd3af-280">`BinaryClassificationContext.Evaluate` 方法會使用指定的資料集來計算 `PredictionModel` 的品質計量。</span><span class="sxs-lookup"><span data-stu-id="dd3af-280">The `BinaryClassificationContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="dd3af-281">它傳回的 `BinaryClassificationEvaluator.CalibratedResult` 物件包含二元分類評估工具所計算的整體計量。</span><span class="sxs-lookup"><span data-stu-id="dd3af-281">It returns a `BinaryClassificationEvaluator.CalibratedResult` object contains the overall metrics computed by binary classification evaluators.</span></span> <span data-ttu-id="dd3af-282">若要顯示這些計量以判斷模型的品質，您必須先取得計量。</span><span class="sxs-lookup"><span data-stu-id="dd3af-282">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="dd3af-283">將下列程式碼加入為 `Evaluate` 方法中的下一行：</span><span class="sxs-lookup"><span data-stu-id="dd3af-283">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#14 "Compute Metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="dd3af-284">顯示模型驗證的計量</span><span class="sxs-lookup"><span data-stu-id="dd3af-284">Displaying the metrics for model validation</span></span>

<span data-ttu-id="dd3af-285">使用下列程式碼來顯示計量、共用結果，然後依結果採取動作：</span><span class="sxs-lookup"><span data-stu-id="dd3af-285">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#15 "Display selected metrics")]

<span data-ttu-id="dd3af-286">若要將您的模型先儲存成 .zip 檔案再傳回，請將下列呼叫 `SaveModelAsFile` 方法的程式碼加入為 `TrainFinalModel` 中的下一行：</span><span class="sxs-lookup"><span data-stu-id="dd3af-286">To save your model to a .zip file before returning, add the following code to call the `SaveModelAsFile` method as the next line in `TrainFinalModel`:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#23 "Save the model")]

## <a name="save-the-model-as-azip-file"></a><span data-ttu-id="dd3af-287">將模型儲存為 .zip 檔案</span><span class="sxs-lookup"><span data-stu-id="dd3af-287">Save the model as a.zip file</span></span>

<span data-ttu-id="dd3af-288">請使用下列程式碼，在緊接著 `Evaluate` 方法之後，建立 `SaveModelAsFile` 方法：</span><span class="sxs-lookup"><span data-stu-id="dd3af-288">Create the `SaveModelAsFile` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="dd3af-289">`SaveModelAsFile` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="dd3af-289">The `SaveModelAsFile` method executes the following tasks:</span></span>

* <span data-ttu-id="dd3af-290">將模型儲存為 .zip 檔案。</span><span class="sxs-lookup"><span data-stu-id="dd3af-290">Saves the model as a .zip file.</span></span>

<span data-ttu-id="dd3af-291">接下來，請建立儲存模型的方法，以便在其他應用程式中重複使用。</span><span class="sxs-lookup"><span data-stu-id="dd3af-291">Next, create a method to save the model so that it can be reused and consumed in other applications.</span></span> <span data-ttu-id="dd3af-292">`ITransformer` 具有 <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.Runtime.IHostEnvironment,System.IO.Stream)> 方法，它會採用 `_modelPath` 全域欄位和 <xref:System.IO.Stream>。</span><span class="sxs-lookup"><span data-stu-id="dd3af-292">The `ITransformer` has a <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.Runtime.IHostEnvironment,System.IO.Stream)> method that takes in the `_modelPath` global field, and a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="dd3af-293">為了將模型儲存為 zip 檔案，您會在呼叫 `SaveTo` 方法之前立即建立 `FileStream`。</span><span class="sxs-lookup"><span data-stu-id="dd3af-293">To save this as a zip file, you'll create the `FileStream` immediately before calling the `SaveTo` method.</span></span> <span data-ttu-id="dd3af-294">將下列程式碼加入 `SaveModelAsFile` 方法中作為的下一行：</span><span class="sxs-lookup"><span data-stu-id="dd3af-294">Add the following code to the `SaveModelAsFile` method as the next line:</span></span>

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#24 "Add the SaveTo Method")]

<span data-ttu-id="dd3af-295">您也可以透過使用下列程式碼，以 `_modelPath` 寫入主控台訊息來顯示檔案寫入的位置：</span><span class="sxs-lookup"><span data-stu-id="dd3af-295">You could also display where the file was written by writing a console message with the `_modelPath`, using the following code:</span></span>

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="predict-the-test-data-outcome-with-the-model-and-a-single-comment"></a><span data-ttu-id="dd3af-296">使用模型和單一評論來預測測試資料輸出</span><span class="sxs-lookup"><span data-stu-id="dd3af-296">Predict the test data outcome with the model and a single comment</span></span>

<span data-ttu-id="dd3af-297">請使用下列程式碼，在緊接著 `Evaluate` 方法之後，建立 `Predict` 方法：</span><span class="sxs-lookup"><span data-stu-id="dd3af-297">Create the `Predict` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void Predict(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="dd3af-298">`Predict` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="dd3af-298">The `Predict` method executes the following tasks:</span></span>

* <span data-ttu-id="dd3af-299">建立單一評論的測試資料。</span><span class="sxs-lookup"><span data-stu-id="dd3af-299">Creates a single comment of test data.</span></span>
* <span data-ttu-id="dd3af-300">根據測試資料預測情感。</span><span class="sxs-lookup"><span data-stu-id="dd3af-300">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="dd3af-301">合併測試資料和預測來進行報告。</span><span class="sxs-lookup"><span data-stu-id="dd3af-301">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="dd3af-302">顯示預測的結果。</span><span class="sxs-lookup"><span data-stu-id="dd3af-302">Displays the predicted results.</span></span>

<span data-ttu-id="dd3af-303">請使用下列程式碼，在緊接著 `Evaluate` 方法呼叫底下，從 `Main` 方法新增對新方法的呼叫：</span><span class="sxs-lookup"><span data-stu-id="dd3af-303">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#16 "Call the Predict method")]

<span data-ttu-id="dd3af-304">雖然 `model` 是可在多個資料列上運作的 `transformer`，但常見的生產環境案例需要根據個別範例進行預測。</span><span class="sxs-lookup"><span data-stu-id="dd3af-304">While the `model` is a `transformer` that operates on many rows of data, a very common production scenario is a need for predictions on individual examples.</span></span> <span data-ttu-id="dd3af-305"><xref:Microsoft.ML.Runtime.Data.PredictionFunction%602> 是從 `MakePredictionFunction` 方法傳回的包裝函式。</span><span class="sxs-lookup"><span data-stu-id="dd3af-305">The <xref:Microsoft.ML.Runtime.Data.PredictionFunction%602> is a wrapper that is returned from the `MakePredictionFunction` method.</span></span> <span data-ttu-id="dd3af-306">讓我們將下列程式碼加入為 `Predict` 方法中的第一行，以建立 PredictionFunction：</span><span class="sxs-lookup"><span data-stu-id="dd3af-306">Let's add the following code to create the PredictionFunction as the first line in the `Predict` Method:</span></span>

[!code-csharp[MakePredictionFunction](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#17 "Create the PredictionFunction")]
  
<span data-ttu-id="dd3af-307">透過建立 `SentimentData` 的執行個體，在 `Predict` 方法中新增評論，以測試定型模型的預測：</span><span class="sxs-lookup"><span data-stu-id="dd3af-307">Add a comment to test the trained model's prediction in the `Predict` method by creating an instance of `SentimentData`:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#18 "Create test data for single prediction")]


 <span data-ttu-id="dd3af-308">您可以使用該方法來預測評論資料之單一執行個體的情感為 Toxic (有害的) 或 Non Toxic (無害的)。</span><span class="sxs-lookup"><span data-stu-id="dd3af-308">You can use that to predict the Toxic or Non Toxic sentiment of a single instance of the comment data.</span></span> <span data-ttu-id="dd3af-309">若要取得預測，請在資料上使用 <xref:Microsoft.ML.Runtime.Data.PredictionFunction%602.Predict(%600)>。</span><span class="sxs-lookup"><span data-stu-id="dd3af-309">To get a prediction, use <xref:Microsoft.ML.Runtime.Data.PredictionFunction%602.Predict(%600)> on the data.</span></span> <span data-ttu-id="dd3af-310">請注意，輸入資料是一個字串，且模型包含特徵化。</span><span class="sxs-lookup"><span data-stu-id="dd3af-310">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="dd3af-311">在定型和預測期間，您的管線會同步。</span><span class="sxs-lookup"><span data-stu-id="dd3af-311">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="dd3af-312">您無須特別為預測撰寫前處理/特徵化程式碼，同一個 API 會同時負責批次和單次預測。</span><span class="sxs-lookup"><span data-stu-id="dd3af-312">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#19 "Create a prediction of sentiment")]

### <a name="model-operationalization-prediction"></a><span data-ttu-id="dd3af-313">模型操作化：預測</span><span class="sxs-lookup"><span data-stu-id="dd3af-313">Model operationalization: prediction</span></span>

<span data-ttu-id="dd3af-314">顯示 `SentimentText` 和對應的情感預測，以便共用結果並根據結果相應地採取動作。</span><span class="sxs-lookup"><span data-stu-id="dd3af-314">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="dd3af-315">這稱為操作化，其中會使用傳回的資料作為操作原則的一部份。</span><span class="sxs-lookup"><span data-stu-id="dd3af-315">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="dd3af-316">請使用下列 <xref:System.Console.WriteLine?displayProperty=nameWithType> 程式碼來為結果建立顯示：</span><span class="sxs-lookup"><span data-stu-id="dd3af-316">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#20 "Display prediction output")]

## <a name="predict-the-test-data-outcomes-with-the-saved-model"></a><span data-ttu-id="dd3af-317">使用儲存的模型來預測測試資料結果</span><span class="sxs-lookup"><span data-stu-id="dd3af-317">Predict the test data outcomes with the saved model</span></span>

<span data-ttu-id="dd3af-318">請使用下列程式碼，緊接在 `SaveModelAsFile` 方法之前，建立 `PredictWithModelLoadedFromFile` 方法：</span><span class="sxs-lookup"><span data-stu-id="dd3af-318">Create the `PredictWithModelLoadedFromFile` method, just before the `SaveModelAsFile` method, using the following code:</span></span>

```csharp
public static void PredictWithModelLoadedFromFile(MLContext mlContext)
{

}
```

<span data-ttu-id="dd3af-319">`PredictWithModelLoadedFromFile` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="dd3af-319">The `PredictWithModelLoadedFromFile` method executes the following tasks:</span></span>

* <span data-ttu-id="dd3af-320">建立批次測試資料。</span><span class="sxs-lookup"><span data-stu-id="dd3af-320">Creates batch test data.</span></span>
* <span data-ttu-id="dd3af-321">根據測試資料預測情感。</span><span class="sxs-lookup"><span data-stu-id="dd3af-321">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="dd3af-322">合併測試資料和預測來進行報告。</span><span class="sxs-lookup"><span data-stu-id="dd3af-322">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="dd3af-323">顯示預測的結果。</span><span class="sxs-lookup"><span data-stu-id="dd3af-323">Displays the predicted results.</span></span>

<span data-ttu-id="dd3af-324">請使用下列程式碼，在緊接著 `Predict` 方法呼叫底下，從 `Main` 方法新增對新方法的呼叫：</span><span class="sxs-lookup"><span data-stu-id="dd3af-324">Add a call to the new method from the `Main` method, right under the `Predict` method call, using the following code:</span></span>

[!code-csharp[CallPredictModelLoaded](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#25 "Call the PredictWithModelLoadedFromFile method")]

<span data-ttu-id="dd3af-325">新增一些評論以測試 `PredictWithModelLoadedFromFile` 方法中定型模型的預測：</span><span class="sxs-lookup"><span data-stu-id="dd3af-325">Add some comments to test the trained model's predictions in the `PredictWithModelLoadedFromFile` method:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#26 "Create test data for predictions")]

<span data-ttu-id="dd3af-326">載入模型 [!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#27 "Load the model")]</span><span class="sxs-lookup"><span data-stu-id="dd3af-326">Load the model [!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#27 "Load the model")]</span></span>

<span data-ttu-id="dd3af-327">既然您已有模型，現在即可利用 <xref:Microsoft.ML.Core.Data.ITransformer.Transform(Microsoft.ML.Runtime.Data.IDataView)> 方法，使用該模型來預測評論資料的 Toxic (有害的) 或 Non Toxic (無害的) 情感。</span><span class="sxs-lookup"><span data-stu-id="dd3af-327">Now that you have a model, you can use that to predict the Toxic or Non Toxic sentiment of the comment data using the <xref:Microsoft.ML.Core.Data.ITransformer.Transform(Microsoft.ML.Runtime.Data.IDataView)> method.</span></span> <span data-ttu-id="dd3af-328">若要取得預測，請在新資料上使用 `Predict`。</span><span class="sxs-lookup"><span data-stu-id="dd3af-328">To get a prediction, use `Predict` on new data.</span></span> <span data-ttu-id="dd3af-329">請注意，輸入資料是一個字串，且模型包含特徵化。</span><span class="sxs-lookup"><span data-stu-id="dd3af-329">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="dd3af-330">在定型和預測期間，您的管線會同步。</span><span class="sxs-lookup"><span data-stu-id="dd3af-330">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="dd3af-331">您無須特別為預測撰寫前處理/特徵化程式碼，同一個 API 會同時負責批次和單次預測。</span><span class="sxs-lookup"><span data-stu-id="dd3af-331">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span> <span data-ttu-id="dd3af-332">將下列程式碼加入預測的 `PredictWithModelLoadedFromFile` 方法：</span><span class="sxs-lookup"><span data-stu-id="dd3af-332">Add the following code to the `PredictWithModelLoadedFromFile` method for the predictions:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#28 "Create predictions of sentiments")]

### <a name="model-operationalization-prediction"></a><span data-ttu-id="dd3af-333">模型操作化：預測</span><span class="sxs-lookup"><span data-stu-id="dd3af-333">Model operationalization: prediction</span></span>

<span data-ttu-id="dd3af-334">顯示 `SentimentText` 和對應的情感預測，以便共用結果並根據結果相應地採取動作。</span><span class="sxs-lookup"><span data-stu-id="dd3af-334">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="dd3af-335">這稱為操作化，其中會使用傳回的資料作為操作原則的一部份。</span><span class="sxs-lookup"><span data-stu-id="dd3af-335">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="dd3af-336">請使用下列 <xref:System.Console.WriteLine?displayProperty=nameWithType> 程式碼來為結果建立標頭：</span><span class="sxs-lookup"><span data-stu-id="dd3af-336">Create a header for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#29 "Display prediction outputs")]

<span data-ttu-id="dd3af-337">顯示預測的結果之前，請先將情感和預測合併在一起，以將原始評論搭配其預測情感一起查看。</span><span class="sxs-lookup"><span data-stu-id="dd3af-337">Before displaying the predicted results, combine the sentiment and prediction together to see the original comment with its predicted sentiment.</span></span> <span data-ttu-id="dd3af-338">下列程式碼會使用 <xref:System.Linq.Enumerable.Zip%2A> 方法來使其發生，因此接下來請新增該程式碼：</span><span class="sxs-lookup"><span data-stu-id="dd3af-338">The following code uses the <xref:System.Linq.Enumerable.Zip%2A> method to make that happen, so add that code next:</span></span>

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#30 "Build the pairs of sentiment data and predictions")]

<span data-ttu-id="dd3af-339">既然您已將 `SentimentText` 和 `Sentiment` 合併成一個類別，現在即可使用 <xref:System.Console.WriteLine?displayProperty=nameWithType> 方法來顯示結果：</span><span class="sxs-lookup"><span data-stu-id="dd3af-339">Now that you've combined the `SentimentText` and `Sentiment` into a class, you can display the results using the <xref:System.Console.WriteLine?displayProperty=nameWithType> method:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#31 "Display the predictions")]

<span data-ttu-id="dd3af-340">由於推斷的元組元素名稱是 C# 7.1 中的新功能，而專案的預設語言版本是 C# 7.0，因此您必須將語言版本變更為 C# 7.1 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="dd3af-340">Because inferred tuple element names are a new feature in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span>
<span data-ttu-id="dd3af-341">若要這樣做，請在 [方案總管] 中的專案節點上按一下滑鼠右鍵，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="dd3af-341">To do that, right-click on the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="dd3af-342">選取 [建置] 索引標籤並選取 [進階] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="dd3af-342">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="dd3af-343">從下拉式清單中，選取 [C# 7.1] (或更新版本)。</span><span class="sxs-lookup"><span data-stu-id="dd3af-343">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="dd3af-344">選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="dd3af-344">Select the **OK** button.</span></span>

## <a name="results"></a><span data-ttu-id="dd3af-345">結果</span><span class="sxs-lookup"><span data-stu-id="dd3af-345">Results</span></span>

<span data-ttu-id="dd3af-346">您的結果應該與以下類似。</span><span class="sxs-lookup"><span data-stu-id="dd3af-346">Your results should be similar to the following.</span></span> <span data-ttu-id="dd3af-347">當管線進行處理時，會顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="dd3af-347">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="dd3af-348">您可能會看到警告或處理訊息。</span><span class="sxs-lookup"><span data-stu-id="dd3af-348">You may see warnings, or processing messages.</span></span> <span data-ttu-id="dd3af-349">為了清晰起見，下列結果中已將這些都移除。</span><span class="sxs-lookup"><span data-stu-id="dd3af-349">These have been removed from the following results for clarity.</span></span>

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 94.44%
Auc: 98.77%
F1Score: 94.74%
=============== End of model evaluation ===============

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This is a very rude movie | Prediction: Toxic | Probability: 0.5297049
=============== End of Predictions ===============

=============== New iteration of Model ===============
=============== Create and Train the Model ===============
=============== End of training ===============


The model is saved to: C:\Tutorial\SentimentAnalysis\bin\Debug\netcoreapp2.0\Data\Model.zip

=============== Prediction Test of loaded model with a multiple samples ===============

Sentiment: This is a very rude movie | Prediction: Toxic | Probability: 0.4585565
Sentiment: He is the best, and the article should say that. | Prediction: Not Toxic | Probability: 0.9924279

```

<span data-ttu-id="dd3af-350">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="dd3af-350">Congratulations!</span></span> <span data-ttu-id="dd3af-351">您現在已成功建置可對訊息情感進行分類和預測的機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="dd3af-351">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span> <span data-ttu-id="dd3af-352">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="dd3af-352">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="dd3af-353">後續步驟</span><span class="sxs-lookup"><span data-stu-id="dd3af-353">Next steps</span></span>

<span data-ttu-id="dd3af-354">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="dd3af-354">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="dd3af-355">了解問題</span><span class="sxs-lookup"><span data-stu-id="dd3af-355">Understand the problem</span></span>
> * <span data-ttu-id="dd3af-356">選取適當的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="dd3af-356">Select the appropriate machine learning task</span></span>
> * <span data-ttu-id="dd3af-357">準備您的資料</span><span class="sxs-lookup"><span data-stu-id="dd3af-357">Prepare your data</span></span>
> * <span data-ttu-id="dd3af-358">建立學習管線</span><span class="sxs-lookup"><span data-stu-id="dd3af-358">Create the learning pipeline</span></span>
> * <span data-ttu-id="dd3af-359">載入分類器</span><span class="sxs-lookup"><span data-stu-id="dd3af-359">Load a classifier</span></span>
> * <span data-ttu-id="dd3af-360">將模型定型</span><span class="sxs-lookup"><span data-stu-id="dd3af-360">Train the model</span></span>
> * <span data-ttu-id="dd3af-361">使用不同的資料集來評估模型</span><span class="sxs-lookup"><span data-stu-id="dd3af-361">Evaluate the model with a different dataset</span></span>
> * <span data-ttu-id="dd3af-362">使用模型來預測測試資料結果</span><span class="sxs-lookup"><span data-stu-id="dd3af-362">Predict the test data outcomes with the model</span></span>

<span data-ttu-id="dd3af-363">前進到下一個教學課程來深入了解</span><span class="sxs-lookup"><span data-stu-id="dd3af-363">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="dd3af-364">計程車車資預測工具</span><span class="sxs-lookup"><span data-stu-id="dd3af-364">Taxi Fare Predictor</span></span>](taxi-fare.md)
