---
title: 在情感分析二元分類案例中使用 ML.NET
description: 探索如何在二元分類案例中使用 ML.NET，以了解如何使用情感預測來採取適當的動作。
ms.date: 02/15/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: d6d5cae107e25000add5c8430a35131a79696bc2
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092757"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a><span data-ttu-id="0e087-103">教學課程：在情感分析二元分類案例中使用 ML.NET</span><span class="sxs-lookup"><span data-stu-id="0e087-103">Tutorial: Use ML.NET in a sentiment analysis binary classification scenario</span></span>

> [!NOTE]
> <span data-ttu-id="0e087-104">本主題涉及 ML.NET，此功能目前為公開預覽版，因此内容可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="0e087-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="0e087-105">如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) (英文)。</span><span class="sxs-lookup"><span data-stu-id="0e087-105">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="0e087-106">此範例教學課程說明如何使用 Visual Studio 2017 中的 C#，透過 .NET Core 主控台應用程式，使用 ML.NET 來建立情感分類器。</span><span class="sxs-lookup"><span data-stu-id="0e087-106">This sample tutorial illustrates using ML.NET to create a sentiment classifier via a .NET Core console application using C# in Visual Studio 2017.</span></span>

<span data-ttu-id="0e087-107">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="0e087-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="0e087-108">了解問題</span><span class="sxs-lookup"><span data-stu-id="0e087-108">Understand the problem</span></span>
> * <span data-ttu-id="0e087-109">選取適當的機器學習演算法</span><span class="sxs-lookup"><span data-stu-id="0e087-109">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="0e087-110">準備您的資料</span><span class="sxs-lookup"><span data-stu-id="0e087-110">Prepare your data</span></span>
> * <span data-ttu-id="0e087-111">轉換資料</span><span class="sxs-lookup"><span data-stu-id="0e087-111">Transform the data</span></span>
> * <span data-ttu-id="0e087-112">將模型定型</span><span class="sxs-lookup"><span data-stu-id="0e087-112">Train the model</span></span>
> * <span data-ttu-id="0e087-113">評估模型</span><span class="sxs-lookup"><span data-stu-id="0e087-113">Evaluate the model</span></span>
> * <span data-ttu-id="0e087-114">使用訓練過的模型預測</span><span class="sxs-lookup"><span data-stu-id="0e087-114">Predict with the trained model</span></span>
> * <span data-ttu-id="0e087-115">使用已載入的模型部署和預測</span><span class="sxs-lookup"><span data-stu-id="0e087-115">Deploy and Predict with a loaded model</span></span>

## <a name="sentiment-analysis-sample-overview"></a><span data-ttu-id="0e087-116">情感分析範例概觀</span><span class="sxs-lookup"><span data-stu-id="0e087-116">Sentiment analysis sample overview</span></span>

<span data-ttu-id="0e087-117">範例是一個主控台應用程式，會使用 ML.NET 來定型模型，以將情感分類並預測為正面或負面。</span><span class="sxs-lookup"><span data-stu-id="0e087-117">The sample is a console app that uses ML.NET to train a model that classifies and predicts sentiment as either positive or negative.</span></span> <span data-ttu-id="0e087-118">它也會使用第二資料集來評估模型，以進行品質分析。</span><span class="sxs-lookup"><span data-stu-id="0e087-118">It also evaluates the model with a second dataset for quality analysis.</span></span> <span data-ttu-id="0e087-119">情感資料集來自 WikiDetox 專案。</span><span class="sxs-lookup"><span data-stu-id="0e087-119">The sentiment datasets are from the WikiDetox project.</span></span>

<span data-ttu-id="0e087-120">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="0e087-120">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0e087-121">必要條件</span><span class="sxs-lookup"><span data-stu-id="0e087-121">Prerequisites</span></span>

* <span data-ttu-id="0e087-122">已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)。</span><span class="sxs-lookup"><span data-stu-id="0e087-122">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="0e087-123">[維基百科 Detox 行資料定位字元分隔檔案 (wikiPedia-detox-250-line-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv)。</span><span class="sxs-lookup"><span data-stu-id="0e087-123">The [Wikipedia detox line data tab separated file (wikiPedia-detox-250-line-data.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv).</span></span>
* <span data-ttu-id="0e087-124">[維基百科 Detox 行測試定位字元分隔檔案 (wikipedia-detox-250-line-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv)。</span><span class="sxs-lookup"><span data-stu-id="0e087-124">The [Wikipedia detox line test tab separated file (wikipedia-detox-250-line-test.tsv)](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv).</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="0e087-125">機器學習工作流程</span><span class="sxs-lookup"><span data-stu-id="0e087-125">Machine learning workflow</span></span>

<span data-ttu-id="0e087-126">本教學課程依循機器學習工作流程，可讓程序按順序移入。</span><span class="sxs-lookup"><span data-stu-id="0e087-126">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="0e087-127">工作流程階段如下：</span><span class="sxs-lookup"><span data-stu-id="0e087-127">The workflow phases are as follows:</span></span>

1. <span data-ttu-id="0e087-128">**了解問題**</span><span class="sxs-lookup"><span data-stu-id="0e087-128">**Understand the problem**</span></span>
2. <span data-ttu-id="0e087-129">**準備您的資料**</span><span class="sxs-lookup"><span data-stu-id="0e087-129">**Prepare your data**</span></span>
   * <span data-ttu-id="0e087-130">**載入資料**</span><span class="sxs-lookup"><span data-stu-id="0e087-130">**Load the data**</span></span>
   * <span data-ttu-id="0e087-131">**擷取特徵 (轉換您的資料)**</span><span class="sxs-lookup"><span data-stu-id="0e087-131">**Extract features (Transform your data)**</span></span>
3. <span data-ttu-id="0e087-132">**建置和定型**</span><span class="sxs-lookup"><span data-stu-id="0e087-132">**Build and train**</span></span> 
   * <span data-ttu-id="0e087-133">**將模型定型**</span><span class="sxs-lookup"><span data-stu-id="0e087-133">**Train the model**</span></span>
   * <span data-ttu-id="0e087-134">**評估模型**</span><span class="sxs-lookup"><span data-stu-id="0e087-134">**Evaluate the model**</span></span>
4. <span data-ttu-id="0e087-135">**部署模型**</span><span class="sxs-lookup"><span data-stu-id="0e087-135">**Deploy Model**</span></span>
   * <span data-ttu-id="0e087-136">**使用模型預測**</span><span class="sxs-lookup"><span data-stu-id="0e087-136">**Use the Model to predict**</span></span>

### <a name="understand-the-problem"></a><span data-ttu-id="0e087-137">了解問題</span><span class="sxs-lookup"><span data-stu-id="0e087-137">Understand the problem</span></span>

<span data-ttu-id="0e087-138">您必須先了解問題，以便將其分解成可支援模型建置和定型的組件。</span><span class="sxs-lookup"><span data-stu-id="0e087-138">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="0e087-139">分解問題可讓您預測及評估結果。</span><span class="sxs-lookup"><span data-stu-id="0e087-139">Breaking the problem down allows you to predict and evaluate the results.</span></span>

<span data-ttu-id="0e087-140">本教學課程的問題是要了解傳入的網站評論情感，以採取適當的動作。</span><span class="sxs-lookup"><span data-stu-id="0e087-140">The problem for this tutorial is to understand incoming website comment sentiment to take the appropriate action.</span></span>

<span data-ttu-id="0e087-141">針對要用來將模型定型的資料，您可以將問題分解成情感文字和情感值，以及可評估並操作使用的預測情感值。</span><span class="sxs-lookup"><span data-stu-id="0e087-141">You can break down the problem to the sentiment text and sentiment value for the data you want to train the model with, and a predicted sentiment value that you can evaluate and then use operationally.</span></span>

<span data-ttu-id="0e087-142">接著，您需要**判斷**該情感，這可協助您選取機器學習工作。</span><span class="sxs-lookup"><span data-stu-id="0e087-142">You then need to **determine** the sentiment, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-algorithm"></a><span data-ttu-id="0e087-143">選取適當的機器學習演算法</span><span class="sxs-lookup"><span data-stu-id="0e087-143">Select the appropriate machine learning algorithm</span></span>

<span data-ttu-id="0e087-144">處理此問題時，您會知道下列事實：</span><span class="sxs-lookup"><span data-stu-id="0e087-144">With this problem, you know the following facts:</span></span>

<span data-ttu-id="0e087-145">將資料定型：網站評論可能為有害的 (1) 或無害的 (0) (**情感**)。</span><span class="sxs-lookup"><span data-stu-id="0e087-145">Training data: website comments can be toxic (1) or not toxic (0) (**sentiment**).</span></span>
<span data-ttu-id="0e087-146">預測新網站評論的**情感**，判斷是有害的或無害的，例如下列範例中所示：</span><span class="sxs-lookup"><span data-stu-id="0e087-146">Predict the **sentiment** of a new website comment, either toxic or not toxic, such as in the following examples:</span></span>

* <span data-ttu-id="0e087-147">請避免在維基百科中新增毫無意義的內容。</span><span class="sxs-lookup"><span data-stu-id="0e087-147">Please refrain from adding nonsense to Wikipedia.</span></span>
* <span data-ttu-id="0e087-148">他是最棒的，而文章應該就那樣說。</span><span class="sxs-lookup"><span data-stu-id="0e087-148">He is the best, and the article should say that.</span></span>

<span data-ttu-id="0e087-149">分類機器學習演算法最適合用於此案例。</span><span class="sxs-lookup"><span data-stu-id="0e087-149">The classification machine learning algorithm is best suited for this scenario.</span></span>

### <a name="about-the-classification-task"></a><span data-ttu-id="0e087-150">關於分類工作</span><span class="sxs-lookup"><span data-stu-id="0e087-150">About the classification task</span></span>

<span data-ttu-id="0e087-151">分類是一項機器學習演算法，會使用資料來**判斷**項目或資料列的分類、類型或類別。</span><span class="sxs-lookup"><span data-stu-id="0e087-151">Classification is a machine learning algorithm that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="0e087-152">例如，您可以使用分類來：</span><span class="sxs-lookup"><span data-stu-id="0e087-152">For example, you can use classification to:</span></span>

* <span data-ttu-id="0e087-153">識別情感是正面還是負面。</span><span class="sxs-lookup"><span data-stu-id="0e087-153">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="0e087-154">將電子郵件分類為垃圾郵件或正常郵件。</span><span class="sxs-lookup"><span data-stu-id="0e087-154">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="0e087-155">判斷病患的實驗樣本是否有癌症病兆。</span><span class="sxs-lookup"><span data-stu-id="0e087-155">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="0e087-156">依客戶回應銷售活動的傾向來分類客戶。</span><span class="sxs-lookup"><span data-stu-id="0e087-156">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="0e087-157">分類演算法通常是下列其中一種：</span><span class="sxs-lookup"><span data-stu-id="0e087-157">Classification algorithms are frequently one of the following types:</span></span>

* <span data-ttu-id="0e087-158">二元：不是 A 就是 B。</span><span class="sxs-lookup"><span data-stu-id="0e087-158">Binary: either A or B.</span></span>
* <span data-ttu-id="0e087-159">多元分類：可使用單一模型來預測的多重分類。</span><span class="sxs-lookup"><span data-stu-id="0e087-159">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="0e087-160">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="0e087-160">Create a console application</span></span>

1. <span data-ttu-id="0e087-161">開啟 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="0e087-161">Open Visual Studio 2017.</span></span> <span data-ttu-id="0e087-162">從功能表列中選取 [檔案]  >  [新增]  >  [專案]。</span><span class="sxs-lookup"><span data-stu-id="0e087-162">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="0e087-163">在 [新增專案] 對話方塊中，選取 [Visual C#] 節點，然後選取 [.NET Core] 節點。</span><span class="sxs-lookup"><span data-stu-id="0e087-163">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="0e087-164">然後選取 [主控台應用程式 (.NET Core)] 專案範本。</span><span class="sxs-lookup"><span data-stu-id="0e087-164">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="0e087-165">在 [名稱] 文字方塊中，輸入 "SentimentAnalysis"，然後選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0e087-165">In the **Name** text box, type "SentimentAnalysis" and then select the **OK** button.</span></span>

2. <span data-ttu-id="0e087-166">在您的專案中建立一個名為 *Data* 的目錄以儲存資料集檔案：</span><span class="sxs-lookup"><span data-stu-id="0e087-166">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="0e087-167">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [新增] > [新增資料夾]。</span><span class="sxs-lookup"><span data-stu-id="0e087-167">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="0e087-168">輸入 "Data"，然後按 Enter。</span><span class="sxs-lookup"><span data-stu-id="0e087-168">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="0e087-169">安裝「Microsoft.ML NuGet 套件」：</span><span class="sxs-lookup"><span data-stu-id="0e087-169">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="0e087-170">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="0e087-170">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="0e087-171">選擇 "nuget.org" 作為 [套件來源]，選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0e087-171">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="0e087-172">在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。</span><span class="sxs-lookup"><span data-stu-id="0e087-172">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="0e087-173">準備您的資料</span><span class="sxs-lookup"><span data-stu-id="0e087-173">Prepare your data</span></span>

1. <span data-ttu-id="0e087-174">下載 [WikiPedia detox-250-line-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) 和 [wikipedia-detox-250-line-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) 資料集，並將它們儲存至先前建立的 *Data* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="0e087-174">Download the [Wikipedia detox-250-line-data.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-data.tsv) and the [wikipedia-detox-250-line-test.tsv](https://github.com/dotnet/machinelearning/blob/master/test/data/wikipedia-detox-250-line-test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="0e087-175">第一個資料集會將機器學習模型定型，第二個資料集則可用來評估您模型的準確率。</span><span class="sxs-lookup"><span data-stu-id="0e087-175">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="0e087-176">在 [方案總管] 中，於每個 \*.tsv 檔案上按一下滑鼠右鍵，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="0e087-176">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="0e087-177">在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。</span><span class="sxs-lookup"><span data-stu-id="0e087-177">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="0e087-178">建立類別及定義路徑</span><span class="sxs-lookup"><span data-stu-id="0e087-178">Create classes and define paths</span></span>

<span data-ttu-id="0e087-179">在 *Program.cs* 檔案頂端新增下列額外的 `using` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="0e087-179">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#1 "Add necessary usings")]

<span data-ttu-id="0e087-180">您需要建立三個全域欄位來持有最近下載之檔案的路徑，還要建立 `TextLoader` 的全域變數：</span><span class="sxs-lookup"><span data-stu-id="0e087-180">You need to create three global fields to hold the paths to the recently downloaded files, and a global variable for the `TextLoader`:</span></span>

* <span data-ttu-id="0e087-181">`_trainDataPath` 包含用來將模型定型的資料集路徑。</span><span class="sxs-lookup"><span data-stu-id="0e087-181">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="0e087-182">`_testDataPath` 包含用來評估模型的資料集路徑。</span><span class="sxs-lookup"><span data-stu-id="0e087-182">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="0e087-183">`_modelPath` 包含用來儲存定型模型的路徑。</span><span class="sxs-lookup"><span data-stu-id="0e087-183">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="0e087-184">`_textLoader` 是 <xref:Microsoft.ML.Data.TextLoader>，用來載入並轉換資料集。</span><span class="sxs-lookup"><span data-stu-id="0e087-184">`_textLoader` is the <xref:Microsoft.ML.Data.TextLoader> used to load and transform the datasets.</span></span>

<span data-ttu-id="0e087-185">將下列程式碼新增至緊接在 `Main` 方法上方的一行，以指定這些路徑和 `_textLoader` 變數：</span><span class="sxs-lookup"><span data-stu-id="0e087-185">Add the following code to the line right above the `Main` method to specify those paths and the `_textLoader` variable:</span></span>

[!code-csharp[Declare global variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#2 "Declare global variables")]

<span data-ttu-id="0e087-186">您必須為輸入資料和預測建立一些類別。</span><span class="sxs-lookup"><span data-stu-id="0e087-186">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="0e087-187">將新類別新增至專案：</span><span class="sxs-lookup"><span data-stu-id="0e087-187">Add a new class to your project:</span></span>

1. <span data-ttu-id="0e087-188">在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="0e087-188">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="0e087-189">在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *SentimentData.cs*。</span><span class="sxs-lookup"><span data-stu-id="0e087-189">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="0e087-190">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0e087-190">Then, select the **Add** button.</span></span>

    <span data-ttu-id="0e087-191">*SentimentData.cs* 檔案隨即在程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="0e087-191">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="0e087-192">將以下 `using` 陳述式新增至 *SentimentData.cs* 頂端：</span><span class="sxs-lookup"><span data-stu-id="0e087-192">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#1 "Add necessary usings")]

<span data-ttu-id="0e087-193">移除現有的類別定義，然後將下列程式碼 (具有 `SentimentData` 和 `SentimentPrediction` 這兩個類別) 新增至 *SentimentData.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="0e087-193">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#2 "Declare data record types")]

<span data-ttu-id="0e087-194">`SentimentData` 是輸入資料集類別，並包含一個情感值為正數或負數的 `float` (`Sentiment`)，以及一個評論字串 (`SentimentText`)。</span><span class="sxs-lookup"><span data-stu-id="0e087-194">`SentimentData` is the input dataset class and has a `float` (`Sentiment`) that has a value for sentiment of either positive or negative, and a string for the comment (`SentimentText`).</span></span> <span data-ttu-id="0e087-195">兩個欄位都有連結的 `Column` 屬性。</span><span class="sxs-lookup"><span data-stu-id="0e087-195">Both fields have `Column` attributes attached to them.</span></span> <span data-ttu-id="0e087-196">此屬性描述資料檔中每個欄位的順序，以及哪一個是 `Label` 欄位。</span><span class="sxs-lookup"><span data-stu-id="0e087-196">This attribute describes the order of each field in the data file, and which is the `Label` field.</span></span> <span data-ttu-id="0e087-197">`SentimentPrediction` 是在模型定型後，用來進行預測的類別。</span><span class="sxs-lookup"><span data-stu-id="0e087-197">`SentimentPrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="0e087-198">它包含一個單一布林值 (`Sentiment`) 和一個 `PredictedLabel` `ColumnName` 屬性。</span><span class="sxs-lookup"><span data-stu-id="0e087-198">It has a single boolean (`Sentiment`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="0e087-199">`Label` 會用來建立和定型模型，也會與第二資料集搭配使用來評估模型。</span><span class="sxs-lookup"><span data-stu-id="0e087-199">The `Label` is used to create and train the model, and it's also used with a second dataset to evaluate the model.</span></span> <span data-ttu-id="0e087-200">`PredictedLabel` 的使用時機是在進行預測和評估的期間。</span><span class="sxs-lookup"><span data-stu-id="0e087-200">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="0e087-201">就評估而言，會使用含有定型資料、預設值及模型的輸入。</span><span class="sxs-lookup"><span data-stu-id="0e087-201">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="0e087-202">使用 ML.NET 建置模型時，您要從建立 `MLContext` 開始。</span><span class="sxs-lookup"><span data-stu-id="0e087-202">When building a model with ML.NET you start by creating an `MLContext`.</span></span> <span data-ttu-id="0e087-203">這在概念上類似於在 Entity Framework 中使用的 `DbContext`。</span><span class="sxs-lookup"><span data-stu-id="0e087-203">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span> <span data-ttu-id="0e087-204">環境能夠為 ML 作業提供內容，可用來進行例外狀況追蹤和記錄。</span><span class="sxs-lookup"><span data-stu-id="0e087-204">The environment provides a context for your ML job that can be used for exception tracking and logging.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="0e087-205">在 Main 中初始化變數</span><span class="sxs-lookup"><span data-stu-id="0e087-205">Initialize variables in Main</span></span>

<span data-ttu-id="0e087-206">建立名為 `mlContext` 的變數，並使用 `MLContext` 的新執行個體將它初始化。</span><span class="sxs-lookup"><span data-stu-id="0e087-206">Create a variable called `mlContext` and initialize it with a new instance of `MLContext`.</span></span>  <span data-ttu-id="0e087-207">在 `Main` 方法中，以下列程式碼取代 `Console.WriteLine("Hello World!")`：</span><span class="sxs-lookup"><span data-stu-id="0e087-207">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#3 "Create the ML Context")]

<span data-ttu-id="0e087-208">接下來，為了設定資料載入，將 `_textLoader` 全域變數初始化以重複使用它。</span><span class="sxs-lookup"><span data-stu-id="0e087-208">Next, to setup for data loading initialize the `_textLoader` global variable in order to reuse it.</span></span>  <span data-ttu-id="0e087-209">當您使用 `MLContext.Data.CreateTextLoader` 建立 `TextLoader` 時，您必須傳入所需的內容和啟用自訂功能的 <xref:Microsoft.ML.Data.TextLoader.Arguments> 類別。</span><span class="sxs-lookup"><span data-stu-id="0e087-209">When you create a `TextLoader` using  `MLContext.Data.CreateTextLoader`, you pass in the context needed and the <xref:Microsoft.ML.Data.TextLoader.Arguments> class which enables customization.</span></span>

 <span data-ttu-id="0e087-210">透過將 <xref:Microsoft.ML.Data.TextLoader.Column> 物件的陣列傳遞至包含所有資料行名稱及其類別的載入程式，來指定資料結構描述。</span><span class="sxs-lookup"><span data-stu-id="0e087-210">Specify the data schema by passing an array of <xref:Microsoft.ML.Data.TextLoader.Column> objects to the loader containing all the column names and their types.</span></span> <span data-ttu-id="0e087-211">您先前建立 `SentimentData` 類別時已定義了資料結構描述。</span><span class="sxs-lookup"><span data-stu-id="0e087-211">You defined the data schema previously when you created our `SentimentData` class.</span></span> <span data-ttu-id="0e087-212">對於我們的結構描述，第一個資料行 (Label) 是 <xref:System.Boolean> (預測)，第二個資料行 (SentimentText) 是用來預測情感的文字/字串類型特徵。</span><span class="sxs-lookup"><span data-stu-id="0e087-212">For our schema, the first column (Label) is a <xref:System.Boolean> (the prediction) and the second column (SentimentText) is the feature of type text/string used for predicting the sentiment.</span></span>
<span data-ttu-id="0e087-213">`TextLoader` 類別會傳回完整初始化的 <xref:Microsoft.ML.Data.TextLoader></span><span class="sxs-lookup"><span data-stu-id="0e087-213">The `TextLoader` class returns a fully initialized <xref:Microsoft.ML.Data.TextLoader></span></span>  

<span data-ttu-id="0e087-214">若要初始化 `_textLoader` 全域變數以針對需要的資料集重複使用它，請在 `mlContext` 初始化之後加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="0e087-214">To initialize the `_textLoader` global variable in order to reuse it for the needed datasets, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[initTextLoader](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#4 "Initialize the TextLoader")]

<span data-ttu-id="0e087-215">將下列程式碼加入為 `Main` 方法中的下一行程式碼：</span><span class="sxs-lookup"><span data-stu-id="0e087-215">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[Train](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#5 "Train your model")]

<span data-ttu-id="0e087-216">`Train` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="0e087-216">The `Train` method executes the following tasks:</span></span>

* <span data-ttu-id="0e087-217">載入資料。</span><span class="sxs-lookup"><span data-stu-id="0e087-217">Loads the data.</span></span>
* <span data-ttu-id="0e087-218">擷取並轉換資料。</span><span class="sxs-lookup"><span data-stu-id="0e087-218">Extracts and transforms the data.</span></span>
* <span data-ttu-id="0e087-219">將模型定型。</span><span class="sxs-lookup"><span data-stu-id="0e087-219">Trains the model.</span></span>
* <span data-ttu-id="0e087-220">根據測試資料預測情感。</span><span class="sxs-lookup"><span data-stu-id="0e087-220">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="0e087-221">傳回模型。</span><span class="sxs-lookup"><span data-stu-id="0e087-221">Returns the model.</span></span>

<span data-ttu-id="0e087-222">請使用下列程式碼，在緊接著 `Main` 方法之後，建立 `Train` 方法：</span><span class="sxs-lookup"><span data-stu-id="0e087-222">Create the `Train` method, just after the `Main` method, using the following code:</span></span>

```csharp
 public static ITransformer Train(MLContext mlContext, string dataPath)
{

}
```

<span data-ttu-id="0e087-223">請注意，有兩個參數傳遞至 Train 方法中；內容 (`mlContext`) 的 `MLContext` 和資料集路徑 (`dataPath`) 的 <xref:System.String>。</span><span class="sxs-lookup"><span data-stu-id="0e087-223">Notice that two parameters are passed into the Train method; a `MLContext` for the context (`mlContext`), and a <xref:System.String> for the dataset path (`dataPath`).</span></span> <span data-ttu-id="0e087-224">您會將此方法多次用於定型和測試。</span><span class="sxs-lookup"><span data-stu-id="0e087-224">You're going to use this method more than once for training and testing.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="0e087-225">載入資料</span><span class="sxs-lookup"><span data-stu-id="0e087-225">Load the data</span></span>

<span data-ttu-id="0e087-226">您將使用 `_textLoader` 全域變數搭配 `dataPath` 參數來載入資料。</span><span class="sxs-lookup"><span data-stu-id="0e087-226">You'll load the data using the `_textLoader` global variable with the `dataPath` parameter.</span></span> <span data-ttu-id="0e087-227">它會傳回 <xref:Microsoft.Data.DataView.IDataView>。</span><span class="sxs-lookup"><span data-stu-id="0e087-227">It returns a <xref:Microsoft.Data.DataView.IDataView>.</span></span> <span data-ttu-id="0e087-228">作為 `Transforms` 的輸入和輸出，`DataView` 是基本的資料管線類型，相當於 `LINQ` 的 `IEnumerable`。</span><span class="sxs-lookup"><span data-stu-id="0e087-228">As the input and output of `Transforms`, a `DataView` is the fundamental data pipeline type, comparable to `IEnumerable` for `LINQ`.</span></span>

<span data-ttu-id="0e087-229">在 ML.NET 中，資料相當於 SQL 檢視。</span><span class="sxs-lookup"><span data-stu-id="0e087-229">In ML.NET, data is similar to a SQL view.</span></span> <span data-ttu-id="0e087-230">它是延遲評估、結構描述化且異質性的。</span><span class="sxs-lookup"><span data-stu-id="0e087-230">It is lazily evaluated, schematized, and heterogenous.</span></span> <span data-ttu-id="0e087-231">物件是管線的第一個部分，並且會載入資料。</span><span class="sxs-lookup"><span data-stu-id="0e087-231">The object is the first part of the pipeline, and loads the data.</span></span> <span data-ttu-id="0e087-232">在本教學課程中，它會載入資料集，其中包含評論及所對應的有害的或無害的情感。</span><span class="sxs-lookup"><span data-stu-id="0e087-232">For this tutorial, it loads a dataset with comments and corresponding toxic or non toxic sentiment.</span></span> <span data-ttu-id="0e087-233">這用來建立模型並加以定型。</span><span class="sxs-lookup"><span data-stu-id="0e087-233">This is used to create the model, and train it.</span></span>

 <span data-ttu-id="0e087-234">將下列程式碼新增為 `Train` 方法的第一行：</span><span class="sxs-lookup"><span data-stu-id="0e087-234">Add the following code as the first line of the `Train` method:</span></span>

[!code-csharp[LoadTrainData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#6 "loading training dataset")]

## <a name="extract-and-transform-the-data"></a><span data-ttu-id="0e087-235">擷取並轉換資料</span><span class="sxs-lookup"><span data-stu-id="0e087-235">Extract and transform the data</span></span>

<span data-ttu-id="0e087-236">資料前處理和清除是相當重要的工作，發生在有效地使用資料集來進行機器學習之前。</span><span class="sxs-lookup"><span data-stu-id="0e087-236">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="0e087-237">原始資料通常雜訊多且不可靠，而可能遺漏值。</span><span class="sxs-lookup"><span data-stu-id="0e087-237">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="0e087-238">使用資料時，如果未進行這些模型化工作，可能會產生誤導的結果。</span><span class="sxs-lookup"><span data-stu-id="0e087-238">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="0e087-239">ML.NET 的轉換管線撰寫一組自訂的轉換，可在定型或測試之前先套用到您的資料。</span><span class="sxs-lookup"><span data-stu-id="0e087-239">ML.NET's transform pipelines compose a custom set of transforms that are applied to your data before training or testing.</span></span> <span data-ttu-id="0e087-240">轉換的主要目的是將資料[特徵化](../resources/glossary.md#feature-engineering)。</span><span class="sxs-lookup"><span data-stu-id="0e087-240">The transforms' primary purpose is data [featurization](../resources/glossary.md#feature-engineering).</span></span> <span data-ttu-id="0e087-241">機器學習演算法了解[特徵化](../resources/glossary.md#feature)資料，因此下一步是將我們的文字資料轉換成 ML 演算法可辨識的格式。</span><span class="sxs-lookup"><span data-stu-id="0e087-241">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, so the next step is to transform our textual data into a format that our ML algorithms recognize.</span></span> <span data-ttu-id="0e087-242">該格式為[數值向量](../resources/glossary.md#numerical-feature-vector)。</span><span class="sxs-lookup"><span data-stu-id="0e087-242">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="0e087-243">接下來，呼叫 `mlContext.Transforms.Text.FeaturizeText` 將文字資料行 (`SentimentText`) 轉換成名為 `Features` 的數值向量，機器學習演算法會使用此數值向量。</span><span class="sxs-lookup"><span data-stu-id="0e087-243">Next, call `mlContext.Transforms.Text.FeaturizeText` which featurizes the text column (`SentimentText`) column into a numeric vector called `Features` used by the machine learning algorithm.</span></span> <span data-ttu-id="0e087-244">此包裝函式呼叫會傳回 <xref:Microsoft.ML.Data.EstimatorChain%601>，可作為有效的管線。</span><span class="sxs-lookup"><span data-stu-id="0e087-244">This is a wrapper call that returns an <xref:Microsoft.ML.Data.EstimatorChain%601> that will effectively be a pipeline.</span></span> <span data-ttu-id="0e087-245">照一般作法為此 `pipeline` 命名，然後將定型程式附加至 `EstimatorChain`。</span><span class="sxs-lookup"><span data-stu-id="0e087-245">Name this `pipeline` as you will then append the trainer to the `EstimatorChain`.</span></span> <span data-ttu-id="0e087-246">將下列程式碼加入為下一行：</span><span class="sxs-lookup"><span data-stu-id="0e087-246">Add this as the next line of code:</span></span>

[!code-csharp[TextFeaturizingEstimator](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#7 "Add a TextFeaturizingEstimator")]

<span data-ttu-id="0e087-247">這就是前處理/特徵化步驟。</span><span class="sxs-lookup"><span data-stu-id="0e087-247">This is the preprocessing/featurization step.</span></span> <span data-ttu-id="0e087-248">使用 ML.NET 中可用的額外元件可讓您的模型產生更佳的結果。</span><span class="sxs-lookup"><span data-stu-id="0e087-248">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="0e087-249">選擇學習演算法</span><span class="sxs-lookup"><span data-stu-id="0e087-249">Choose a learning algorithm</span></span>

<span data-ttu-id="0e087-250">若要新增訓練程式，請呼叫會傳回 <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> 的 `mlContext.Transforms.Text.FeaturizeText` 包裝方法。</span><span class="sxs-lookup"><span data-stu-id="0e087-250">To add the trainer, call the `mlContext.Transforms.Text.FeaturizeText` wrapper method which returns a <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> object.</span></span> <span data-ttu-id="0e087-251">這是您將在此管線中使用的決策樹學習工具。</span><span class="sxs-lookup"><span data-stu-id="0e087-251">This is a decision tree learner you'll use in this pipeline.</span></span> <span data-ttu-id="0e087-252">`FastTreeBinaryClassificationTrainer` 是附加到 `pipeline`，且接受特徵化 `SentimentText` (`Features`) 和 `Label` 輸入參數，以從歷史資料學習。</span><span class="sxs-lookup"><span data-stu-id="0e087-252">The `FastTreeBinaryClassificationTrainer` is appended to the `pipeline` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

<span data-ttu-id="0e087-253">將下列程式碼加入 `Train` 方法：</span><span class="sxs-lookup"><span data-stu-id="0e087-253">Add the following code to the `Train` method:</span></span>

[!code-csharp[FastTreeBinaryClassificationTrainer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#8 "Add a FastTreeBinaryClassificationTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="0e087-254">將模型定型</span><span class="sxs-lookup"><span data-stu-id="0e087-254">Train the model</span></span>

<span data-ttu-id="0e087-255">您會根據已載入和轉換的資料集將模型 <xref:Microsoft.ML.Data.TransformerChain%601>定型。</span><span class="sxs-lookup"><span data-stu-id="0e087-255">You train the model, <xref:Microsoft.ML.Data.TransformerChain%601>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="0e087-256">定義了評估工具之後，我們使用 <xref:Microsoft.ML.Data.EstimatorChain%601.Fit*> 定型模型，並提供已載入的定型資料。</span><span class="sxs-lookup"><span data-stu-id="0e087-256">Once the estimator has been defined, you train your model using the <xref:Microsoft.ML.Data.EstimatorChain%601.Fit*> while providing the already loaded training data.</span></span> <span data-ttu-id="0e087-257">這會傳回要用於預測的模型。</span><span class="sxs-lookup"><span data-stu-id="0e087-257">This returns a model to use for predictions.</span></span> <span data-ttu-id="0e087-258">`pipeline.Fit()` 會定型管線，並根據傳入的 `DataView` 傳回 `Transformer`。</span><span class="sxs-lookup"><span data-stu-id="0e087-258">`pipeline.Fit()` trains the pipeline and returns a `Transformer` based on the `DataView` passed in.</span></span> <span data-ttu-id="0e087-259">實驗會等到定型之後才會執行。</span><span class="sxs-lookup"><span data-stu-id="0e087-259">The experiment is not executed until this happens.</span></span>

<span data-ttu-id="0e087-260">將下列程式碼加入 `Train` 方法：</span><span class="sxs-lookup"><span data-stu-id="0e087-260">Add the following code to the `Train` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#9 "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="0e087-261">儲存並傳回所定型以供評估使用的模型</span><span class="sxs-lookup"><span data-stu-id="0e087-261">Save and Return the model trained to use for evaluation</span></span>

<span data-ttu-id="0e087-262">此時，您已有一個可整合至任何現有或新 .NET 應用程式之 <xref:Microsoft.ML.Data.TransformerChain%601> 類型的模型。</span><span class="sxs-lookup"><span data-stu-id="0e087-262">At this point, you have a model of type <xref:Microsoft.ML.Data.TransformerChain%601> that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="0e087-263">在 `Train` 方法的結尾傳回模型。</span><span class="sxs-lookup"><span data-stu-id="0e087-263">Return the model at the end of the `Train` method.</span></span>

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#10 "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="0e087-264">評估模型</span><span class="sxs-lookup"><span data-stu-id="0e087-264">Evaluate the model</span></span>

<span data-ttu-id="0e087-265">建立並定型模型之後，現在必須使用不同的資料集來評估它，以確保和驗證品質。</span><span class="sxs-lookup"><span data-stu-id="0e087-265">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="0e087-266">在 `Evaluate` 方法中，會傳入在 `Train` 中建立的模型以供評估。</span><span class="sxs-lookup"><span data-stu-id="0e087-266">In the `Evaluate` method, the model created in `Train` is passed in to be evaluated.</span></span> <span data-ttu-id="0e087-267">在緊接著 `Train` 之後，建立 `Evaluate` 方法，如以下程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="0e087-267">Create the `Evaluate` method, just after `Train`, as in the following code:</span></span>

```csharp
public static void Evaluate(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="0e087-268">`Evaluate` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="0e087-268">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="0e087-269">載入測試資料集。</span><span class="sxs-lookup"><span data-stu-id="0e087-269">Loads the test dataset.</span></span>
* <span data-ttu-id="0e087-270">建立二元評估工具。</span><span class="sxs-lookup"><span data-stu-id="0e087-270">Creates the binary evaluator.</span></span>
* <span data-ttu-id="0e087-271">評估模型並建立計量。</span><span class="sxs-lookup"><span data-stu-id="0e087-271">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="0e087-272">顯示計量。</span><span class="sxs-lookup"><span data-stu-id="0e087-272">Displays the metrics.</span></span>

<span data-ttu-id="0e087-273">請使用下列程式碼，在緊接著 `Train` 方法呼叫底下，從 `Main` 方法新增對新方法的呼叫：</span><span class="sxs-lookup"><span data-stu-id="0e087-273">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#11 "Call the Evaluate method")]

<span data-ttu-id="0e087-274">我們將使用先前已初始化的 `_textLoader` 全域變數與 `_testDataPath` 全域欄位來載入測試資料集。</span><span class="sxs-lookup"><span data-stu-id="0e087-274">You'll load the test dataset using the previously initialized  `_textLoader` global variable with the `_testDataPath` global field.</span></span> <span data-ttu-id="0e087-275">您可以使用此資料集來評估模型，以作為品質檢查。</span><span class="sxs-lookup"><span data-stu-id="0e087-275">You can evaluate the model using this dataset as a quality check.</span></span> <span data-ttu-id="0e087-276">將下列程式碼加入 `Evaluate` 方法：</span><span class="sxs-lookup"><span data-stu-id="0e087-276">Add the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#12 "Load the test dataset")]

<span data-ttu-id="0e087-277">接下來，您將使用機器學習 `model` 參數 (轉換器) 來輸入特徵並傳回預測。</span><span class="sxs-lookup"><span data-stu-id="0e087-277">Next, you'll use the machine learning `model` parameter (a transformer) to input the features and return predictions.</span></span> <span data-ttu-id="0e087-278">將下列程式碼加入 `Evaluate` 方法中作為下一行：</span><span class="sxs-lookup"><span data-stu-id="0e087-278">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#13 "Predict using the Transformer")]

<span data-ttu-id="0e087-279">`BinaryClassificationContext.Evaluate` 方法會使用指定的資料集來計算 `PredictionModel` 的品質計量。</span><span class="sxs-lookup"><span data-stu-id="0e087-279">The `BinaryClassificationContext.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="0e087-280">它傳回的 `BinaryClassificationEvaluator.CalibratedResult` 物件包含二元分類評估工具所計算的整體計量。</span><span class="sxs-lookup"><span data-stu-id="0e087-280">It returns a `BinaryClassificationEvaluator.CalibratedResult` object contains the overall metrics computed by binary classification evaluators.</span></span> <span data-ttu-id="0e087-281">若要顯示這些計量以判斷模型的品質，您必須先取得計量。</span><span class="sxs-lookup"><span data-stu-id="0e087-281">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="0e087-282">將下列程式碼加入為 `Evaluate` 方法中的下一行：</span><span class="sxs-lookup"><span data-stu-id="0e087-282">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#14 "Compute Metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="0e087-283">顯示模型驗證的計量</span><span class="sxs-lookup"><span data-stu-id="0e087-283">Displaying the metrics for model validation</span></span>

<span data-ttu-id="0e087-284">使用下列程式碼來顯示計量、共用結果，然後依結果採取動作：</span><span class="sxs-lookup"><span data-stu-id="0e087-284">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#15 "Display selected metrics")]

<span data-ttu-id="0e087-285">若要將您的模型先儲存成 .zip 檔案再傳回，請將下列呼叫 `SaveModelAsFile` 方法的程式碼加入為 `Evaluate` 中的下一行：</span><span class="sxs-lookup"><span data-stu-id="0e087-285">To save your model to a .zip file before returning, add the following code to call the `SaveModelAsFile` method as the next line in `Evaluate`:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#23 "Save the model")]

## <a name="save-the-model-as-azip-file"></a><span data-ttu-id="0e087-286">將模型儲存為 .zip 檔案</span><span class="sxs-lookup"><span data-stu-id="0e087-286">Save the model as a.zip file</span></span>

<span data-ttu-id="0e087-287">請使用下列程式碼，在緊接著 `Evaluate` 方法之後，建立 `SaveModelAsFile` 方法：</span><span class="sxs-lookup"><span data-stu-id="0e087-287">Create the `SaveModelAsFile` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="0e087-288">`SaveModelAsFile` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="0e087-288">The `SaveModelAsFile` method executes the following tasks:</span></span>

* <span data-ttu-id="0e087-289">將模型儲存為 .zip 檔案。</span><span class="sxs-lookup"><span data-stu-id="0e087-289">Saves the model as a .zip file.</span></span>

<span data-ttu-id="0e087-290">接下來，請建立儲存模型的方法，以便在其他應用程式中重複使用。</span><span class="sxs-lookup"><span data-stu-id="0e087-290">Next, create a method to save the model so that it can be reused and consumed in other applications.</span></span> <span data-ttu-id="0e087-291">`ITransformer` 具有 <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> 方法，它會採用 `_modelPath` 全域欄位和 <xref:System.IO.Stream>。</span><span class="sxs-lookup"><span data-stu-id="0e087-291">The `ITransformer` has a <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> method that takes in the `_modelPath` global field, and a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="0e087-292">為了將模型儲存為 zip 檔案，您會在呼叫 `SaveTo` 方法之前立即建立 `FileStream`。</span><span class="sxs-lookup"><span data-stu-id="0e087-292">To save this as a zip file, you'll create the `FileStream` immediately before calling the `SaveTo` method.</span></span> <span data-ttu-id="0e087-293">將下列程式碼加入 `SaveModelAsFile` 方法中作為的下一行：</span><span class="sxs-lookup"><span data-stu-id="0e087-293">Add the following code to the `SaveModelAsFile` method as the next line:</span></span>

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#24 "Add the SaveTo Method")]
<span data-ttu-id="0e087-294">使用已載入的模型部署及預測。您也可以透過使用下列程式碼，以 `_modelPath` 寫入主控台訊息來顯示檔案寫入的位置：</span><span class="sxs-lookup"><span data-stu-id="0e087-294">Deploy and Predict with a loaded model You could also display where the file was written by writing a console message with the `_modelPath`, using the following code:</span></span>

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="predict-the-test-data-outcome-with-the-saved-model"></a><span data-ttu-id="0e087-295">使用儲存的模型來預測測試資料結果</span><span class="sxs-lookup"><span data-stu-id="0e087-295">Predict the test data outcome with the saved model</span></span>

<span data-ttu-id="0e087-296">請使用下列程式碼，在緊接著 `Evaluate` 方法之後，建立 `Predict` 方法：</span><span class="sxs-lookup"><span data-stu-id="0e087-296">Create the `Predict` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void Predict(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="0e087-297">`Predict` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="0e087-297">The `Predict` method executes the following tasks:</span></span>

* <span data-ttu-id="0e087-298">建立單一評論的測試資料。</span><span class="sxs-lookup"><span data-stu-id="0e087-298">Creates a single comment of test data.</span></span>
* <span data-ttu-id="0e087-299">根據測試資料預測情感。</span><span class="sxs-lookup"><span data-stu-id="0e087-299">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="0e087-300">合併測試資料和預測來進行報告。</span><span class="sxs-lookup"><span data-stu-id="0e087-300">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="0e087-301">顯示預測的結果。</span><span class="sxs-lookup"><span data-stu-id="0e087-301">Displays the predicted results.</span></span>

<span data-ttu-id="0e087-302">請使用下列程式碼，在緊接著 `Evaluate` 方法呼叫底下，從 `Main` 方法新增對新方法的呼叫：</span><span class="sxs-lookup"><span data-stu-id="0e087-302">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#16 "Call the Predict method")]

<span data-ttu-id="0e087-303">雖然 `model` 是可在多個資料列上運作的 `transformer`，但常見的生產環境案例需要根據個別範例進行預測。</span><span class="sxs-lookup"><span data-stu-id="0e087-303">While the `model` is a `transformer` that operates on many rows of data, a very common production scenario is a need for predictions on individual examples.</span></span> <span data-ttu-id="0e087-304"><xref:Microsoft.ML.PredictionEngine%602> 是從 `CreatePredictionEngine` 方法傳回的包裝函式。</span><span class="sxs-lookup"><span data-stu-id="0e087-304">The <xref:Microsoft.ML.PredictionEngine%602> is a wrapper that is returned from the `CreatePredictionEngine` method.</span></span> <span data-ttu-id="0e087-305">讓我們在 `Predict` 方法中的第一行加入下列程式碼，來建立 `PredictionEngine`：</span><span class="sxs-lookup"><span data-stu-id="0e087-305">Let's add the following code to create the `PredictionEngine` as the first line in the `Predict` Method:</span></span>

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#17 "Create the PredictionEngine")]
  
<span data-ttu-id="0e087-306">透過建立 `SentimentData` 的執行個體，在 `Predict` 方法中新增評論，以測試定型模型的預測：</span><span class="sxs-lookup"><span data-stu-id="0e087-306">Add a comment to test the trained model's prediction in the `Predict` method by creating an instance of `SentimentData`:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#18 "Create test data for single prediction")]

 <span data-ttu-id="0e087-307">您可以使用該方法來預測評論資料之單一執行個體的情感為 Toxic (有害的) 或 Non Toxic (無害的)。</span><span class="sxs-lookup"><span data-stu-id="0e087-307">You can use that to predict the Toxic or Non Toxic sentiment of a single instance of the comment data.</span></span> <span data-ttu-id="0e087-308">若要取得預測，請在資料上使用 <xref:Microsoft.ML.PredictionEngine%602.Predict%2A>。</span><span class="sxs-lookup"><span data-stu-id="0e087-308">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="0e087-309">請注意，輸入資料是一個字串，且模型包含特徵化。</span><span class="sxs-lookup"><span data-stu-id="0e087-309">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="0e087-310">在定型和預測期間，您的管線會同步。</span><span class="sxs-lookup"><span data-stu-id="0e087-310">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="0e087-311">您無須特別為預測撰寫前處理/特徵化程式碼，同一個 API 會同時負責批次和單次預測。</span><span class="sxs-lookup"><span data-stu-id="0e087-311">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#19 "Create a prediction of sentiment")]

### <a name="using-the-model-prediction"></a><span data-ttu-id="0e087-312">使用模型：預測</span><span class="sxs-lookup"><span data-stu-id="0e087-312">Using the model: prediction</span></span>

<span data-ttu-id="0e087-313">顯示 `SentimentText` 和對應的情感預測，以便共用結果並根據結果相應地採取動作。</span><span class="sxs-lookup"><span data-stu-id="0e087-313">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="0e087-314">這稱為操作化，其中會使用傳回的資料作為操作原則的一部份。</span><span class="sxs-lookup"><span data-stu-id="0e087-314">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="0e087-315">請使用下列 <xref:System.Console.WriteLine?displayProperty=nameWithType> 程式碼來為結果建立顯示：</span><span class="sxs-lookup"><span data-stu-id="0e087-315">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#20 "Display prediction output")]

## <a name="deploy-and-predict-with-a-loaded-model"></a><span data-ttu-id="0e087-316">使用已載入的模型部署和預測</span><span class="sxs-lookup"><span data-stu-id="0e087-316">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="0e087-317">請使用下列程式碼，緊接在 `SaveModelAsFile` 方法之前，建立 `PredictWithModelLoadedFromFile` 方法：</span><span class="sxs-lookup"><span data-stu-id="0e087-317">Create the `PredictWithModelLoadedFromFile` method, just before the `SaveModelAsFile` method, using the following code:</span></span>

```csharp
public static void PredictWithModelLoadedFromFile(MLContext mlContext)
{

}
```

<span data-ttu-id="0e087-318">`PredictWithModelLoadedFromFile` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="0e087-318">The `PredictWithModelLoadedFromFile` method executes the following tasks:</span></span>

* <span data-ttu-id="0e087-319">建立批次測試資料。</span><span class="sxs-lookup"><span data-stu-id="0e087-319">Creates batch test data.</span></span>
* <span data-ttu-id="0e087-320">根據測試資料預測情感。</span><span class="sxs-lookup"><span data-stu-id="0e087-320">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="0e087-321">合併測試資料和預測來進行報告。</span><span class="sxs-lookup"><span data-stu-id="0e087-321">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="0e087-322">顯示預測的結果。</span><span class="sxs-lookup"><span data-stu-id="0e087-322">Displays the predicted results.</span></span>

<span data-ttu-id="0e087-323">請使用下列程式碼，在緊接著 `Predict` 方法呼叫底下，從 `Main` 方法新增對新方法的呼叫：</span><span class="sxs-lookup"><span data-stu-id="0e087-323">Add a call to the new method from the `Main` method, right under the `Predict` method call, using the following code:</span></span>

[!code-csharp[CallPredictModelLoaded](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#25 "Call the PredictWithModelLoadedFromFile method")]

<span data-ttu-id="0e087-324">新增一些評論以測試 `PredictWithModelLoadedFromFile` 方法中定型模型的預測：</span><span class="sxs-lookup"><span data-stu-id="0e087-324">Add some comments to test the trained model's predictions in the `PredictWithModelLoadedFromFile` method:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#26 "Create test data for predictions")]

<span data-ttu-id="0e087-325">載入模型</span><span class="sxs-lookup"><span data-stu-id="0e087-325">Load the model</span></span>

[!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#27 "Load the model")]

<span data-ttu-id="0e087-326">既然您已有模型，現在即可利用 <xref:Microsoft.ML.Core.Data.ITransformer.Transform%2A> 方法，使用該模型來預測評論資料的 Toxic (有害的) 或 Non Toxic (無害的) 情感。</span><span class="sxs-lookup"><span data-stu-id="0e087-326">Now that you have a model, you can use that to predict the Toxic or Non Toxic sentiment of the comment data using the <xref:Microsoft.ML.Core.Data.ITransformer.Transform%2A> method.</span></span> <span data-ttu-id="0e087-327">若要取得預測，請在新資料上使用 `Predict`。</span><span class="sxs-lookup"><span data-stu-id="0e087-327">To get a prediction, use `Predict` on new data.</span></span> <span data-ttu-id="0e087-328">請注意，輸入資料是一個字串，且模型包含特徵化。</span><span class="sxs-lookup"><span data-stu-id="0e087-328">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="0e087-329">在定型和預測期間，您的管線會同步。</span><span class="sxs-lookup"><span data-stu-id="0e087-329">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="0e087-330">您無須特別為預測撰寫前處理/特徵化程式碼，同一個 API 會同時負責批次和單次預測。</span><span class="sxs-lookup"><span data-stu-id="0e087-330">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span> <span data-ttu-id="0e087-331">將下列程式碼加入預測的 `PredictWithModelLoadedFromFile` 方法：</span><span class="sxs-lookup"><span data-stu-id="0e087-331">Add the following code to the `PredictWithModelLoadedFromFile` method for the predictions:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#28 "Create predictions of sentiments")]

### <a name="using-the-loaded-model-for-prediction"></a><span data-ttu-id="0e087-332">使用載入的模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="0e087-332">Using the loaded model for prediction</span></span>

<span data-ttu-id="0e087-333">顯示 `SentimentText` 和對應的情感預測，以便共用結果並根據結果相應地採取動作。</span><span class="sxs-lookup"><span data-stu-id="0e087-333">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="0e087-334">這稱為操作化，其中會使用傳回的資料作為操作原則的一部份。</span><span class="sxs-lookup"><span data-stu-id="0e087-334">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="0e087-335">請使用下列 <xref:System.Console.WriteLine?displayProperty=nameWithType> 程式碼來為結果建立標頭：</span><span class="sxs-lookup"><span data-stu-id="0e087-335">Create a header for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#29 "Display prediction outputs")]

<span data-ttu-id="0e087-336">顯示預測的結果之前，請先將情感和預測合併在一起，以將原始評論搭配其預測情感一起查看。</span><span class="sxs-lookup"><span data-stu-id="0e087-336">Before displaying the predicted results, combine the sentiment and prediction together to see the original comment with its predicted sentiment.</span></span> <span data-ttu-id="0e087-337">下列程式碼會使用 <xref:System.Linq.Enumerable.Zip%2A> 方法來使其發生，因此接下來請新增該程式碼：</span><span class="sxs-lookup"><span data-stu-id="0e087-337">The following code uses the <xref:System.Linq.Enumerable.Zip%2A> method to make that happen, so add that code next:</span></span>

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#30 "Build the pairs of sentiment data and predictions")]

<span data-ttu-id="0e087-338">既然您已將 `SentimentText` 和 `Sentiment` 合併成一個類別，現在即可使用 <xref:System.Console.WriteLine?displayProperty=nameWithType> 方法來顯示結果：</span><span class="sxs-lookup"><span data-stu-id="0e087-338">Now that you've combined the `SentimentText` and `Sentiment` into a class, you can display the results using the <xref:System.Console.WriteLine?displayProperty=nameWithType> method:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#31 "Display the predictions")]

<span data-ttu-id="0e087-339">由於推斷的元組元素名稱是 C# 7.1 中的新功能，而專案的預設語言版本是 C# 7.0，因此您必須將語言版本變更為 C# 7.1 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="0e087-339">Because inferred tuple element names are a new feature in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span>
<span data-ttu-id="0e087-340">若要這樣做，請在 [方案總管] 中的專案節點上按一下滑鼠右鍵，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="0e087-340">To do that, right-click on the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="0e087-341">選取 [建置] 索引標籤並選取 [進階] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0e087-341">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="0e087-342">從下拉式清單中，選取 [C# 7.1] (或更新版本)。</span><span class="sxs-lookup"><span data-stu-id="0e087-342">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="0e087-343">選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0e087-343">Select the **OK** button.</span></span>

## <a name="results"></a><span data-ttu-id="0e087-344">結果</span><span class="sxs-lookup"><span data-stu-id="0e087-344">Results</span></span>

<span data-ttu-id="0e087-345">您的結果應該與以下類似。</span><span class="sxs-lookup"><span data-stu-id="0e087-345">Your results should be similar to the following.</span></span> <span data-ttu-id="0e087-346">當管線進行處理時，會顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="0e087-346">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="0e087-347">您可能會看到警告或處理訊息。</span><span class="sxs-lookup"><span data-stu-id="0e087-347">You may see warnings, or processing messages.</span></span> <span data-ttu-id="0e087-348">為了清晰起見，下列結果中已將這些都移除。</span><span class="sxs-lookup"><span data-stu-id="0e087-348">These have been removed from the following results for clarity.</span></span>

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


The model is saved to: C:\Tutorial\SentimentAnalysis\bin\Debug\netcoreapp2.1\Data\Model.zip

=============== Prediction Test of loaded model with a multiple sample ===============

Sentiment: This is a very rude movie | Prediction: Toxic | Probability: 0.4585565
Sentiment: I love this article. | Prediction: Not Toxic | Probability: 0.09454837

```

<span data-ttu-id="0e087-349">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="0e087-349">Congratulations!</span></span> <span data-ttu-id="0e087-350">您現在已成功建置可對訊息情感進行分類和預測的機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="0e087-350">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span> <span data-ttu-id="0e087-351">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="0e087-351">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0e087-352">後續步驟</span><span class="sxs-lookup"><span data-stu-id="0e087-352">Next steps</span></span>

<span data-ttu-id="0e087-353">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="0e087-353">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="0e087-354">了解問題</span><span class="sxs-lookup"><span data-stu-id="0e087-354">Understand the problem</span></span>
> * <span data-ttu-id="0e087-355">選取適當的機器學習演算法</span><span class="sxs-lookup"><span data-stu-id="0e087-355">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="0e087-356">準備您的資料</span><span class="sxs-lookup"><span data-stu-id="0e087-356">Prepare your data</span></span>
> * <span data-ttu-id="0e087-357">轉換資料</span><span class="sxs-lookup"><span data-stu-id="0e087-357">Transform the data</span></span>
> * <span data-ttu-id="0e087-358">將模型定型</span><span class="sxs-lookup"><span data-stu-id="0e087-358">Train the model</span></span>
> * <span data-ttu-id="0e087-359">評估模型</span><span class="sxs-lookup"><span data-stu-id="0e087-359">Evaluate the model</span></span>
> * <span data-ttu-id="0e087-360">使用訓練過的模型預測</span><span class="sxs-lookup"><span data-stu-id="0e087-360">Predict with the trained model</span></span>
> * <span data-ttu-id="0e087-361">使用已載入的模型部署和預測</span><span class="sxs-lookup"><span data-stu-id="0e087-361">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="0e087-362">前進到下一個教學課程來深入了解</span><span class="sxs-lookup"><span data-stu-id="0e087-362">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="0e087-363">問題分類</span><span class="sxs-lookup"><span data-stu-id="0e087-363">Issue Classification</span></span>](github-issue-classification.md)
