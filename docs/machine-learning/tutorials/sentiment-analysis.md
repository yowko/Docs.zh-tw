---
title: 在情感分析二元分類案例中使用 ML.NET
description: 探索如何在二元分類案例中使用 ML.NET，以了解如何使用情感預測來採取適當的動作。
ms.date: 03/07/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: b0d02babd126a62ef9a87b251f525a08376069aa
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2019
ms.locfileid: "57845787"
---
# <a name="tutorial-use-mlnet-in-a-sentiment-analysis-binary-classification-scenario"></a><span data-ttu-id="0826b-103">教學課程：在情感分析二元分類案例中使用 ML.NET</span><span class="sxs-lookup"><span data-stu-id="0826b-103">Tutorial: Use ML.NET in a sentiment analysis binary classification scenario</span></span>

<span data-ttu-id="0826b-104">此範例教學課程說明如何在 Visual Studio 2017 中使用 C#，透過 .NET Core 主控台應用程式使用 ML.NET 來建立情感分類器，以預測正面或負面的情感。</span><span class="sxs-lookup"><span data-stu-id="0826b-104">This sample tutorial illustrates using ML.NET to create a sentiment classifier to predict either positive or negative sentiment via a .NET Core console application using C# in Visual Studio 2017.</span></span> <span data-ttu-id="0826b-105">在機器學習的領域中，此類型的預測被稱為二元分類。</span><span class="sxs-lookup"><span data-stu-id="0826b-105">In the world of machine learning, this type of prediction is known as binary classification.</span></span>

> [!NOTE]
> <span data-ttu-id="0826b-106">此主題涉及 ML.NET，此功能目前為公開預覽版，因此内容可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="0826b-106">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="0826b-107">如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) (英文)。</span><span class="sxs-lookup"><span data-stu-id="0826b-107">For more information, visit [the ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="0826b-108">此教學課程與關聯的範例目前是使用 **ML.NET 0.11 版**。</span><span class="sxs-lookup"><span data-stu-id="0826b-108">This tutorial and related sample are currently using **ML.NET version 0.11**.</span></span> <span data-ttu-id="0826b-109">如需詳細資訊，請參閱 [dotnet/machinelearning GitHub 存放庫](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes) \(英文\) 中的版本資訊</span><span class="sxs-lookup"><span data-stu-id="0826b-109">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes)</span></span>

<span data-ttu-id="0826b-110">在此教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="0826b-110">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="0826b-111">了解問題</span><span class="sxs-lookup"><span data-stu-id="0826b-111">Understand the problem</span></span>
> * <span data-ttu-id="0826b-112">選取適當的機器學習演算法</span><span class="sxs-lookup"><span data-stu-id="0826b-112">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="0826b-113">準備您的資料</span><span class="sxs-lookup"><span data-stu-id="0826b-113">Prepare your data</span></span>
> * <span data-ttu-id="0826b-114">轉換資料</span><span class="sxs-lookup"><span data-stu-id="0826b-114">Transform the data</span></span>
> * <span data-ttu-id="0826b-115">將模型定型</span><span class="sxs-lookup"><span data-stu-id="0826b-115">Train the model</span></span>
> * <span data-ttu-id="0826b-116">評估模型</span><span class="sxs-lookup"><span data-stu-id="0826b-116">Evaluate the model</span></span>
> * <span data-ttu-id="0826b-117">使用訓練過的模型預測</span><span class="sxs-lookup"><span data-stu-id="0826b-117">Predict with the trained model</span></span>
> * <span data-ttu-id="0826b-118">使用已載入的模型部署和預測</span><span class="sxs-lookup"><span data-stu-id="0826b-118">Deploy and Predict with a loaded model</span></span>

## <a name="sentiment-analysis-sample-overview"></a><span data-ttu-id="0826b-119">情感分析範例概觀</span><span class="sxs-lookup"><span data-stu-id="0826b-119">Sentiment analysis sample overview</span></span>

<span data-ttu-id="0826b-120">範例是一個主控台應用程式，會使用 ML.NET 來定型模型，以將情感分類並預測為正面或負面。</span><span class="sxs-lookup"><span data-stu-id="0826b-120">The sample is a console app that uses ML.NET to train a model that classifies and predicts sentiment as either positive or negative.</span></span> <span data-ttu-id="0826b-121">Yelp 情感資料集是來自加州大學爾灣分校 (UCI)，且被分割成定型資料集與測試資料集。</span><span class="sxs-lookup"><span data-stu-id="0826b-121">The Yelp sentiment dataset is from University of California, Irvine (UCI), which is split into a train dataset and a test dataset.</span></span> <span data-ttu-id="0826b-122">範例使用測試資料集來評估模型，以進行品質分析。</span><span class="sxs-lookup"><span data-stu-id="0826b-122">The sample evaluates the model with the test dataset for quality analysis.</span></span> 

<span data-ttu-id="0826b-123">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) 存放庫中找到此教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="0826b-123">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0826b-124">先決條件</span><span class="sxs-lookup"><span data-stu-id="0826b-124">Prerequisites</span></span>

* <span data-ttu-id="0826b-125">已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)。</span><span class="sxs-lookup"><span data-stu-id="0826b-125">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* [<span data-ttu-id="0826b-126">UCI 情感標記句子資料集 zip 檔案</span><span class="sxs-lookup"><span data-stu-id="0826b-126">The UCI Sentiment Labeled Sentences dataset zip file</span></span>](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)

## <a name="machine-learning-workflow"></a><span data-ttu-id="0826b-127">機器學習工作流程</span><span class="sxs-lookup"><span data-stu-id="0826b-127">Machine learning workflow</span></span>

<span data-ttu-id="0826b-128">此教學課程依循機器學習工作流程，可讓程序按順序移入。</span><span class="sxs-lookup"><span data-stu-id="0826b-128">This tutorial follows a machine learning workflow that enables the process to move in an orderly fashion.</span></span>

<span data-ttu-id="0826b-129">工作流程階段如下：</span><span class="sxs-lookup"><span data-stu-id="0826b-129">The workflow phases are as follows:</span></span>

1. <span data-ttu-id="0826b-130">**了解問題**</span><span class="sxs-lookup"><span data-stu-id="0826b-130">**Understand the problem**</span></span>
2. <span data-ttu-id="0826b-131">**準備您的資料**</span><span class="sxs-lookup"><span data-stu-id="0826b-131">**Prepare your data**</span></span>
   * <span data-ttu-id="0826b-132">**載入資料**</span><span class="sxs-lookup"><span data-stu-id="0826b-132">**Load the data**</span></span>
   * <span data-ttu-id="0826b-133">**擷取特徵 (轉換您的資料)**</span><span class="sxs-lookup"><span data-stu-id="0826b-133">**Extract features (Transform your data)**</span></span>
3. <span data-ttu-id="0826b-134">**建置和定型**</span><span class="sxs-lookup"><span data-stu-id="0826b-134">**Build and train**</span></span> 
   * <span data-ttu-id="0826b-135">**將模型定型**</span><span class="sxs-lookup"><span data-stu-id="0826b-135">**Train the model**</span></span>
   * <span data-ttu-id="0826b-136">**評估模型**</span><span class="sxs-lookup"><span data-stu-id="0826b-136">**Evaluate the model**</span></span>
4. <span data-ttu-id="0826b-137">**部署模型**</span><span class="sxs-lookup"><span data-stu-id="0826b-137">**Deploy Model**</span></span>
   * <span data-ttu-id="0826b-138">**使用模型預測**</span><span class="sxs-lookup"><span data-stu-id="0826b-138">**Use the Model to predict**</span></span>

### <a name="understand-the-problem"></a><span data-ttu-id="0826b-139">了解問題</span><span class="sxs-lookup"><span data-stu-id="0826b-139">Understand the problem</span></span>

<span data-ttu-id="0826b-140">您必須先了解問題，以便將其分解成可支援模型建置和定型的組件。</span><span class="sxs-lookup"><span data-stu-id="0826b-140">You first need to understand the problem, so you can break it down to parts that can support building and training the model.</span></span> <span data-ttu-id="0826b-141">分解問題可讓您預測及評估結果。</span><span class="sxs-lookup"><span data-stu-id="0826b-141">Breaking the problem down allows you to predict and evaluate the results.</span></span>

<span data-ttu-id="0826b-142">此教學課程的問題是要了解傳入的網站評論情感，以採取適當的動作。</span><span class="sxs-lookup"><span data-stu-id="0826b-142">The problem for this tutorial is to understand incoming website comment sentiment to take the appropriate action.</span></span>

<span data-ttu-id="0826b-143">針對要用來將模型定型的資料，您可以將問題分解成情感文字和情感值，以及可評估並操作使用的預測情感值。</span><span class="sxs-lookup"><span data-stu-id="0826b-143">You can break down the problem to the sentiment text and sentiment value for the data you want to train the model with, and a predicted sentiment value that you can evaluate and then use operationally.</span></span>

<span data-ttu-id="0826b-144">接著，您需要**判斷**該情感，這可協助您選取機器學習工作。</span><span class="sxs-lookup"><span data-stu-id="0826b-144">You then need to **determine** the sentiment, which helps you with the machine learning task selection.</span></span>

## <a name="select-the-appropriate-machine-learning-algorithm"></a><span data-ttu-id="0826b-145">選取適當的機器學習演算法</span><span class="sxs-lookup"><span data-stu-id="0826b-145">Select the appropriate machine learning algorithm</span></span>

<span data-ttu-id="0826b-146">處理此問題時，您會知道下列事實：</span><span class="sxs-lookup"><span data-stu-id="0826b-146">With this problem, you know the following facts:</span></span>

<span data-ttu-id="0826b-147">定型資料：網站評論可能是正面的 (1)，也可能是負面的 (0) (**情感**)。</span><span class="sxs-lookup"><span data-stu-id="0826b-147">Training data: website comments can be positive (1) or negative (0) (**sentiment**).</span></span>

<span data-ttu-id="0826b-148">預測新網站評論的**情感** (正面或負面)，例如在以下範例中：</span><span class="sxs-lookup"><span data-stu-id="0826b-148">Predict the **sentiment** of a new website comment, either positive or negative, such as in the following examples:</span></span>

* <span data-ttu-id="0826b-149">我喜歡這裡的服務生。</span><span class="sxs-lookup"><span data-stu-id="0826b-149">I love the wait staff here.</span></span> <span data-ttu-id="0826b-150">他們超棒的。</span><span class="sxs-lookup"><span data-stu-id="0826b-150">They rock.</span></span>
* <span data-ttu-id="0826b-151">這裡的湯非常差勁。</span><span class="sxs-lookup"><span data-stu-id="0826b-151">This place has the worst soup.</span></span>

<span data-ttu-id="0826b-152">分類機器學習演算法最適合用於此案例。</span><span class="sxs-lookup"><span data-stu-id="0826b-152">The classification machine learning algorithm is best suited for this scenario.</span></span>

### <a name="about-the-classification-algorithm"></a><span data-ttu-id="0826b-153">關於分類演算法</span><span class="sxs-lookup"><span data-stu-id="0826b-153">About the classification algorithm</span></span>

<span data-ttu-id="0826b-154">分類是一個機器學習演算法，會使用資料來**判斷**項目或資料列的分類、類型或類別。</span><span class="sxs-lookup"><span data-stu-id="0826b-154">Classification is a machine learning algorithm that uses data to **determine** the category, type, or class of an item or row of data.</span></span> <span data-ttu-id="0826b-155">例如，您可以使用分類來：</span><span class="sxs-lookup"><span data-stu-id="0826b-155">For example, you can use classification to:</span></span>

* <span data-ttu-id="0826b-156">識別情感是正面還是負面。</span><span class="sxs-lookup"><span data-stu-id="0826b-156">Identify sentiment as positive or negative.</span></span>
* <span data-ttu-id="0826b-157">將電子郵件分類為垃圾郵件或正常郵件。</span><span class="sxs-lookup"><span data-stu-id="0826b-157">Classify email as spam, junk, or good.</span></span>
* <span data-ttu-id="0826b-158">判斷病患的實驗樣本是否有癌症病兆。</span><span class="sxs-lookup"><span data-stu-id="0826b-158">Determine whether a patient's lab sample is cancerous.</span></span>
* <span data-ttu-id="0826b-159">依客戶回應銷售活動的傾向來分類客戶。</span><span class="sxs-lookup"><span data-stu-id="0826b-159">Categorize customers by their propensity to respond to a sales campaign.</span></span>

<span data-ttu-id="0826b-160">分類演算法通常是下列其中一種：</span><span class="sxs-lookup"><span data-stu-id="0826b-160">Classification algorithms are frequently one of the following types:</span></span>

* <span data-ttu-id="0826b-161">二元：不是 A 就是 B。</span><span class="sxs-lookup"><span data-stu-id="0826b-161">Binary: either A or B.</span></span>
* <span data-ttu-id="0826b-162">多元分類：可使用單一模型來預測的多重分類。</span><span class="sxs-lookup"><span data-stu-id="0826b-162">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="0826b-163">由於網站評論必須被分類為正面或負面的，您將會使用二元分類演算法。</span><span class="sxs-lookup"><span data-stu-id="0826b-163">Because the website comments need to be classified as either positive or negative, you use the Binary Classification algorithm.</span></span> 

## <a name="create-a-console-application"></a><span data-ttu-id="0826b-164">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="0826b-164">Create a console application</span></span>

1. <span data-ttu-id="0826b-165">開啟 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="0826b-165">Open Visual Studio 2017.</span></span> <span data-ttu-id="0826b-166">從功能表列中選取 [檔案]  >  [新增]  >  [專案]。</span><span class="sxs-lookup"><span data-stu-id="0826b-166">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="0826b-167">在 [新增專案] 對話方塊中，選取 [Visual C#] 節點，然後選取 [.NET Core] 節點。</span><span class="sxs-lookup"><span data-stu-id="0826b-167">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="0826b-168">然後選取 [主控台應用程式 (.NET Core)] 專案範本。</span><span class="sxs-lookup"><span data-stu-id="0826b-168">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="0826b-169">在 [名稱] 文字方塊中，輸入 "SentimentAnalysis"，然後選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0826b-169">In the **Name** text box, type "SentimentAnalysis" and then select the **OK** button.</span></span>

2. <span data-ttu-id="0826b-170">在您的專案中建立名為 *Data* 的目錄以儲存資料集檔案：</span><span class="sxs-lookup"><span data-stu-id="0826b-170">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="0826b-171">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [新增] > [新增資料夾]。</span><span class="sxs-lookup"><span data-stu-id="0826b-171">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="0826b-172">輸入 "Data"，然後按 Enter。</span><span class="sxs-lookup"><span data-stu-id="0826b-172">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="0826b-173">安裝「Microsoft.ML NuGet 套件」：</span><span class="sxs-lookup"><span data-stu-id="0826b-173">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="0826b-174">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="0826b-174">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="0826b-175">選擇 "nuget.org" 作為 [套件來源]，選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0826b-175">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="0826b-176">在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。</span><span class="sxs-lookup"><span data-stu-id="0826b-176">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="0826b-177">準備您的資料</span><span class="sxs-lookup"><span data-stu-id="0826b-177">Prepare your data</span></span>

1. <span data-ttu-id="0826b-178">下載 [UCI 情感標記句子資料集 zip 檔案 (請參閱下列附註中的引文)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)，然後將它解壓縮。</span><span class="sxs-lookup"><span data-stu-id="0826b-178">Download [The UCI Sentiment Labeled Sentences dataset zip file (see citations in the following note)](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="0826b-179">將 `yelp_labelled.txt` 檔案複製到您所建立的 *Data* 目錄。</span><span class="sxs-lookup"><span data-stu-id="0826b-179">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

> [!NOTE]
> <span data-ttu-id="0826b-180">此教學課程所使用的資料集是來自 'From Group to Individual Labels using Deep Features' (從群組到使用深度特徵的個別標籤) (Kotzias et.</span><span class="sxs-lookup"><span data-stu-id="0826b-180">The datasets this tutorial uses are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="0826b-181">al，</span><span class="sxs-lookup"><span data-stu-id="0826b-181">al,.</span></span> <span data-ttu-id="0826b-182">KDD 2015)，而且裝載於「UCI Machine Learning Repository (UCI 機器學習存放庫)」- Dua, D. and Karra Taniskidou, E.(2017)。</span><span class="sxs-lookup"><span data-stu-id="0826b-182">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="0826b-183">「UCI Machine Learning Repository (UCI 機器學習存放庫)」[http://archive.ics.uci.edu/ml]。</span><span class="sxs-lookup"><span data-stu-id="0826b-183">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="0826b-184">爾灣，加利福尼亞州：加州大學，資訊與電腦科學學院。</span><span class="sxs-lookup"><span data-stu-id="0826b-184">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

3. <span data-ttu-id="0826b-185">在 [方案總管] 中，以滑鼠右鍵按一下 `yelp_labeled.txt` 檔案，並選取 [內容]。</span><span class="sxs-lookup"><span data-stu-id="0826b-185">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="0826b-186">在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。</span><span class="sxs-lookup"><span data-stu-id="0826b-186">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="0826b-187">建立類別及定義路徑</span><span class="sxs-lookup"><span data-stu-id="0826b-187">Create classes and define paths</span></span>

<span data-ttu-id="0826b-188">在 *Program.cs* 檔案頂端新增下列額外的 `using` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="0826b-188">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

<span data-ttu-id="0826b-189">您必須建立兩個全域欄位，以保存最近所下載的資料集檔案路徑與儲存的模型檔案路徑：</span><span class="sxs-lookup"><span data-stu-id="0826b-189">You need to create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

* <span data-ttu-id="0826b-190">`_dataPath` 包含用來將模型定型的資料集路徑。</span><span class="sxs-lookup"><span data-stu-id="0826b-190">`_dataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="0826b-191">`_modelPath` 包含用來儲存定型模型的路徑。</span><span class="sxs-lookup"><span data-stu-id="0826b-191">`_modelPath` has the path where the trained model is saved.</span></span>

<span data-ttu-id="0826b-192">將下列程式碼新增至緊接在 `Main` 方法上方的一行，以指定這些路徑：</span><span class="sxs-lookup"><span data-stu-id="0826b-192">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Declare global variables](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

<span data-ttu-id="0826b-193">您必須為輸入資料和預測建立一些類別。</span><span class="sxs-lookup"><span data-stu-id="0826b-193">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="0826b-194">將新類別新增至專案：</span><span class="sxs-lookup"><span data-stu-id="0826b-194">Add a new class to your project:</span></span>

1. <span data-ttu-id="0826b-195">在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="0826b-195">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="0826b-196">在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *SentimentData.cs*。</span><span class="sxs-lookup"><span data-stu-id="0826b-196">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="0826b-197">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0826b-197">Then, select the **Add** button.</span></span>

    <span data-ttu-id="0826b-198">*SentimentData.cs* 檔案隨即在程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="0826b-198">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="0826b-199">將以下 `using` 陳述式新增至 *SentimentData.cs* 頂端：</span><span class="sxs-lookup"><span data-stu-id="0826b-199">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

[!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

<span data-ttu-id="0826b-200">移除現有的類別定義，然後將下列程式碼 (具有 `SentimentData` 和 `SentimentPrediction` 這兩個類別) 新增至 *SentimentData.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="0826b-200">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

[!code-csharp[DeclareTypes](../../../samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

<span data-ttu-id="0826b-201">輸入資料集類別 `SentimentData` 具有評論 (`SentimentText`) 的 `string`，以及代表正面或負面情感的 `bool` (`Sentiment`) 值。</span><span class="sxs-lookup"><span data-stu-id="0826b-201">The input dataset class, `SentimentData`, has a `string` for the comment (`SentimentText`) and a `bool` (`Sentiment`) that has a value for sentiment of either positive or negative.</span></span> <span data-ttu-id="0826b-202">兩個欄位都有連結的 <xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29> 屬性。</span><span class="sxs-lookup"><span data-stu-id="0826b-202">Both fields have <xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29> attributes attached to them.</span></span> <span data-ttu-id="0826b-203">此屬性描述資料檔中每個欄位的順序。</span><span class="sxs-lookup"><span data-stu-id="0826b-203">This attribute describes the order of each field in the data file.</span></span>  <span data-ttu-id="0826b-204">此外，`Sentiment` 屬性具有 <xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A> 來將它指定為 `Label` 欄位。</span><span class="sxs-lookup"><span data-stu-id="0826b-204">In addition, the `Sentiment` property has a <xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A> to designate it as the `Label` field.</span></span> <span data-ttu-id="0826b-205">`SentimentPrediction` 是在模型定型後，用來進行預測的類別。</span><span class="sxs-lookup"><span data-stu-id="0826b-205">`SentimentPrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="0826b-206">它包含一個單一布林值 (`Sentiment`) 和一個 `PredictedLabel` `ColumnName` 屬性。</span><span class="sxs-lookup"><span data-stu-id="0826b-206">It has a single boolean (`Sentiment`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="0826b-207">`Label` 會用來建立和定型模型，也會用來搭配分割出來的測試資料集來評估模型。</span><span class="sxs-lookup"><span data-stu-id="0826b-207">The `Label` is used to create and train the model, and it's also used with the split out test dataset to evaluate the model.</span></span> <span data-ttu-id="0826b-208">`PredictedLabel` 的使用時機是在進行預測和評估的期間。</span><span class="sxs-lookup"><span data-stu-id="0826b-208">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="0826b-209">就評估而言，會使用含有定型資料、預設值及模型的輸入。</span><span class="sxs-lookup"><span data-stu-id="0826b-209">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="0826b-210">使用 ML.NET 建置模型時，您要從建立 <xref:Microsoft.ML.MLContext> 開始。</span><span class="sxs-lookup"><span data-stu-id="0826b-210">When building a model with ML.NET you start by creating an <xref:Microsoft.ML.MLContext>.</span></span> <span data-ttu-id="0826b-211">`MLContext` 在概念上類似於在 Entity Framework 中使用 `DbContext`。</span><span class="sxs-lookup"><span data-stu-id="0826b-211">`MLContext` is comparable conceptually to using `DbContext` in Entity Framework.</span></span> <span data-ttu-id="0826b-212">環境能夠為 ML 作業提供內容，可用來進行例外狀況追蹤和記錄。</span><span class="sxs-lookup"><span data-stu-id="0826b-212">The environment provides a context for your ML job that can be used for exception tracking and logging.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="0826b-213">在 Main 中初始化變數</span><span class="sxs-lookup"><span data-stu-id="0826b-213">Initialize variables in Main</span></span>

<span data-ttu-id="0826b-214">建立名為 `mlContext` 的變數，並使用 `MLContext` 的新執行個體將它初始化。</span><span class="sxs-lookup"><span data-stu-id="0826b-214">Create a variable called `mlContext` and initialize it with a new instance of `MLContext`.</span></span>  <span data-ttu-id="0826b-215">在 `Main` 方法中，以下列程式碼取代 `Console.WriteLine("Hello World!")`：</span><span class="sxs-lookup"><span data-stu-id="0826b-215">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

<span data-ttu-id="0826b-216">將下列程式碼加入為 `Main` 方法中的下一行程式碼：</span><span class="sxs-lookup"><span data-stu-id="0826b-216">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallLoadData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

<span data-ttu-id="0826b-217">`LoadData` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="0826b-217">The `LoadData` method executes the following tasks:</span></span>

* <span data-ttu-id="0826b-218">載入資料。</span><span class="sxs-lookup"><span data-stu-id="0826b-218">Loads the data.</span></span>
* <span data-ttu-id="0826b-219">將載入的資料集分割為定型與測試資料集。</span><span class="sxs-lookup"><span data-stu-id="0826b-219">Splits the loaded dataset into train and test datasets.</span></span>
* <span data-ttu-id="0826b-220">傳回分割的定型與測試資料集。</span><span class="sxs-lookup"><span data-stu-id="0826b-220">Returns the split train and test datasets.</span></span>

<span data-ttu-id="0826b-221">請使用下列程式碼，在緊接著 `Main` 方法之後，建立 `LoadData` 方法：</span><span class="sxs-lookup"><span data-stu-id="0826b-221">Create the `LoadData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static (IDataView trainSet, IDataView testSet) LoadData(MLContext mlContext)
{

}
```
## <a name="load-the-data"></a><span data-ttu-id="0826b-222">載入資料</span><span class="sxs-lookup"><span data-stu-id="0826b-222">Load the data</span></span>

<span data-ttu-id="0826b-223">因為您先前所建立的 `SentimentData` 資料模型類型符合資料集結構描述，所以您可以針對 [LoadFromTextFile 方法](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29)使用 `MLContext.Data.LoadFromTextFile` 包裝函式，來將初始化、對應和資料集載入合併成一行程式碼。</span><span class="sxs-lookup"><span data-stu-id="0826b-223">Since your previously created `SentimentData` data model type matches the dataset schema, you can combine the initialization, mapping, and dataset loading into one line of code using the `MLContext.Data.LoadFromTextFile` wrapper for the [LoadFromTextFile method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29).</span></span> <span data-ttu-id="0826b-224">它會傳回 <xref:Microsoft.Data.DataView.IDataView>。</span><span class="sxs-lookup"><span data-stu-id="0826b-224">It returns a <xref:Microsoft.Data.DataView.IDataView>.</span></span> 

 <span data-ttu-id="0826b-225">作為 `Transforms` 的輸入和輸出，`DataView` 是基本的資料管線類型，相當於 `LINQ` 的 `IEnumerable`。</span><span class="sxs-lookup"><span data-stu-id="0826b-225">As the input and output of `Transforms`, a `DataView` is the fundamental data pipeline type, comparable to `IEnumerable` for `LINQ`.</span></span>

<span data-ttu-id="0826b-226">在 ML.NET 中，資料相當於 SQL 檢視。</span><span class="sxs-lookup"><span data-stu-id="0826b-226">In ML.NET, data is similar to a SQL view.</span></span> <span data-ttu-id="0826b-227">它是延遲評估、結構描述化且異質性的。</span><span class="sxs-lookup"><span data-stu-id="0826b-227">It is lazily evaluated, schematized, and heterogenous.</span></span> <span data-ttu-id="0826b-228">物件是管線的第一個部分，並且會載入資料。</span><span class="sxs-lookup"><span data-stu-id="0826b-228">The object is the first part of the pipeline, and loads the data.</span></span> <span data-ttu-id="0826b-229">在此教學課程中，它會載入資料集，其中包含評論及所對應的有害的或無害的情感。</span><span class="sxs-lookup"><span data-stu-id="0826b-229">For this tutorial, it loads a dataset with comments and corresponding toxic or non toxic sentiment.</span></span> <span data-ttu-id="0826b-230">這用來建立模型並加以定型。</span><span class="sxs-lookup"><span data-stu-id="0826b-230">This is used to create the model, and train it.</span></span>

 <span data-ttu-id="0826b-231">將下列程式碼新增為 `LoadData` 方法的第一行：</span><span class="sxs-lookup"><span data-stu-id="0826b-231">Add the following code as the first line of the `LoadData` method:</span></span>

[!code-csharp[LoadData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="0826b-232">分割資料集以進行模型定型與測試</span><span class="sxs-lookup"><span data-stu-id="0826b-232">Split the dataset for model training and testing</span></span>

<span data-ttu-id="0826b-233">接下來，您需要定型資料集與測試資料集，以分別對模型進行定型與評估。</span><span class="sxs-lookup"><span data-stu-id="0826b-233">Next, you need both a training dataset to train the model and a test dataset to evaluate the model.</span></span> <span data-ttu-id="0826b-234">使用 `MLContext.BinaryClassification.TrainTestSplit`，其會包裝 <xref:Microsoft.ML.StaticPipe.TrainingStaticExtensions.TrainTestSplit%2A> 以將載入的資料集分割為定型與測試資料集，然後將它們包含在 <xref:Microsoft.ML.TrainCatalogBase.TrainTestData> 內並傳回。</span><span class="sxs-lookup"><span data-stu-id="0826b-234">Use the `MLContext.BinaryClassification.TrainTestSplit` which wraps <xref:Microsoft.ML.StaticPipe.TrainingStaticExtensions.TrainTestSplit%2A> to split the loaded dataset into train and test datasets and return them inside of a <xref:Microsoft.ML.TrainCatalogBase.TrainTestData>.</span></span> <span data-ttu-id="0826b-235">您可以搭配 `testFraction` 參數來指定測試集的資料分數。</span><span class="sxs-lookup"><span data-stu-id="0826b-235">You can specify the fraction of data for the test set with the `testFraction`parameter.</span></span> <span data-ttu-id="0826b-236">預設值是 10%，但您在此範例中會使用 20% 以針對評估使用更多資料。</span><span class="sxs-lookup"><span data-stu-id="0826b-236">The default is 10% but you use 20% in this case to use more data for the evaluation.</span></span>  

<span data-ttu-id="0826b-237">若要將載入的資料分割成所需的資料集，請將下列程式碼加入為 `LoadData` 方法中的下一行：</span><span class="sxs-lookup"><span data-stu-id="0826b-237">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData` method:</span></span>

[!code-csharp[SplitData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

<span data-ttu-id="0826b-238">在 `LoadData` 方法的結尾傳回 `splitDataView`：</span><span class="sxs-lookup"><span data-stu-id="0826b-238">Return the `splitDataView` at the end of the `LoadData` method:</span></span>

[!code-csharp[ReturnSplitData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="0826b-239">建置和定型模型</span><span class="sxs-lookup"><span data-stu-id="0826b-239">Build and train the model</span></span>

<span data-ttu-id="0826b-240">將下列呼叫新增至 `BuildAndTrainModel` 方法作為 `Main` 方法中的下一行程式碼：</span><span class="sxs-lookup"><span data-stu-id="0826b-240">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="0826b-241">`BuildAndTrainModel` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="0826b-241">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="0826b-242">擷取並轉換資料。</span><span class="sxs-lookup"><span data-stu-id="0826b-242">Extracts and transforms the data.</span></span>
* <span data-ttu-id="0826b-243">將模型定型。</span><span class="sxs-lookup"><span data-stu-id="0826b-243">Trains the model.</span></span>
* <span data-ttu-id="0826b-244">根據測試資料預測情感。</span><span class="sxs-lookup"><span data-stu-id="0826b-244">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="0826b-245">傳回模型。</span><span class="sxs-lookup"><span data-stu-id="0826b-245">Returns the model.</span></span>

<span data-ttu-id="0826b-246">請使用下列程式碼，在緊接著 `Main` 方法之後，建立 `BuildAndTrainModel` 方法：</span><span class="sxs-lookup"><span data-stu-id="0826b-246">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
{

}
```

<span data-ttu-id="0826b-247">請注意，有兩個參數傳遞至 Train 方法中：針對內容 (`mlContext`) 的 `MLContext`，以及針對定型資料集 (`splitTrainSet`) 的 `IDataView`。</span><span class="sxs-lookup"><span data-stu-id="0826b-247">Notice that two parameters are passed into the Train method; a `MLContext` for the context (`mlContext`), and an `IDataView`for the training dataset (`splitTrainSet`).</span></span> 

## <a name="extract-and-transform-the-data"></a><span data-ttu-id="0826b-248">擷取並轉換資料</span><span class="sxs-lookup"><span data-stu-id="0826b-248">Extract and transform the data</span></span>

<span data-ttu-id="0826b-249">資料前處理和清除是相當重要的工作，發生在有效地使用資料集來進行機器學習之前。</span><span class="sxs-lookup"><span data-stu-id="0826b-249">Pre-processing and cleaning data are important tasks that occur before a dataset is used effectively for machine learning.</span></span> <span data-ttu-id="0826b-250">原始資料通常雜訊多且不可靠，而可能遺漏值。</span><span class="sxs-lookup"><span data-stu-id="0826b-250">Raw data is often noisy and unreliable, and may be missing values.</span></span> <span data-ttu-id="0826b-251">使用資料時，如果未進行這些模型化工作，可能會產生誤導的結果。</span><span class="sxs-lookup"><span data-stu-id="0826b-251">Using data without these modeling tasks can produce misleading results.</span></span>

<span data-ttu-id="0826b-252">ML.NET 的轉換管線撰寫一組自訂的轉換，可在定型或測試之前先套用到您的資料。</span><span class="sxs-lookup"><span data-stu-id="0826b-252">ML.NET's transform pipelines compose a custom set of transforms that are applied to your data before training or testing.</span></span> <span data-ttu-id="0826b-253">轉換的主要目的是將資料[特徵化](../resources/glossary.md#feature-engineering)。</span><span class="sxs-lookup"><span data-stu-id="0826b-253">The transforms' primary purpose is data [featurization](../resources/glossary.md#feature-engineering).</span></span> <span data-ttu-id="0826b-254">機器學習演算法了解[特徵化](../resources/glossary.md#feature)資料，因此下一步是將我們的文字資料轉換成 ML 演算法可辨識的格式。</span><span class="sxs-lookup"><span data-stu-id="0826b-254">Machine learning algorithms understand [featurized](../resources/glossary.md#feature) data, so the next step is to transform our textual data into a format that our ML algorithms recognize.</span></span> <span data-ttu-id="0826b-255">該格式為[數值向量](../resources/glossary.md#numerical-feature-vector)。</span><span class="sxs-lookup"><span data-stu-id="0826b-255">That format is a [numeric vector](../resources/glossary.md#numerical-feature-vector).</span></span>

<span data-ttu-id="0826b-256">接下來，呼叫 `mlContext.Transforms.Text.FeaturizeText` 將文字資料行 (`SentimentText`) 轉換成名為 `Features` 的數值向量，機器學習演算法會使用此數值向量。</span><span class="sxs-lookup"><span data-stu-id="0826b-256">Next, call `mlContext.Transforms.Text.FeaturizeText` which featurizes the text column (`SentimentText`) column into a numeric vector called `Features` used by the machine learning algorithm.</span></span> <span data-ttu-id="0826b-257">此包裝函式呼叫會傳回 <xref:Microsoft.ML.Data.EstimatorChain%601>，可作為有效的管線。</span><span class="sxs-lookup"><span data-stu-id="0826b-257">This is a wrapper call that returns an <xref:Microsoft.ML.Data.EstimatorChain%601> that will effectively be a pipeline.</span></span> <span data-ttu-id="0826b-258">照一般作法為此 `pipeline` 命名，然後將定型程式附加至 `EstimatorChain`。</span><span class="sxs-lookup"><span data-stu-id="0826b-258">Name this `pipeline` as you will then append the trainer to the `EstimatorChain`.</span></span> <span data-ttu-id="0826b-259">將下列程式碼加入為下一行：</span><span class="sxs-lookup"><span data-stu-id="0826b-259">Add this as the next line of code:</span></span>

[!code-csharp[FeaturizeText](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

>[!WARNING]
> <span data-ttu-id="0826b-260">ML.NET 0.10 版已變更 Transform 參數的順序。</span><span class="sxs-lookup"><span data-stu-id="0826b-260">ML.NET Version 0.10 changed the order of the Transform parameters.</span></span> <span data-ttu-id="0826b-261">在您執行應用程式及建置模型之前，這個順序不會亂掉。</span><span class="sxs-lookup"><span data-stu-id="0826b-261">This will not error out until you run the application and build the model.</span></span> <span data-ttu-id="0826b-262">請使用先前程式碼片段中的 Transforms 參數名稱。</span><span class="sxs-lookup"><span data-stu-id="0826b-262">Use the parameter names for Transforms as illustrated in the previous code snippet.</span></span>

<span data-ttu-id="0826b-263">這就是前處理/特徵化步驟。</span><span class="sxs-lookup"><span data-stu-id="0826b-263">This is the preprocessing/featurization step.</span></span> <span data-ttu-id="0826b-264">使用 ML.NET 中可用的額外元件可讓您的模型產生更佳的結果。</span><span class="sxs-lookup"><span data-stu-id="0826b-264">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="0826b-265">選擇學習演算法</span><span class="sxs-lookup"><span data-stu-id="0826b-265">Choose a learning algorithm</span></span>

<span data-ttu-id="0826b-266">若要新增訓練程式，請呼叫會傳回 <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> 的 `mlContext.BinaryClassification.Trainers.FastTree` 包裝方法。</span><span class="sxs-lookup"><span data-stu-id="0826b-266">To add the trainer, call the `mlContext.BinaryClassification.Trainers.FastTree` wrapper method which returns a <xref:Microsoft.ML.Trainers.FastTree.FastTreeBinaryClassificationTrainer> object.</span></span> <span data-ttu-id="0826b-267">這是您將在此管線中使用的決策樹學習工具。</span><span class="sxs-lookup"><span data-stu-id="0826b-267">This is a decision tree learner you'll use in this pipeline.</span></span> <span data-ttu-id="0826b-268">`FastTreeBinaryClassificationTrainer` 是附加到 `pipeline`，且接受特徵化 `SentimentText` (`Features`) 和 `Label` 輸入參數，以從歷史資料學習。</span><span class="sxs-lookup"><span data-stu-id="0826b-268">The `FastTreeBinaryClassificationTrainer` is appended to the `pipeline` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

<span data-ttu-id="0826b-269">將下列程式碼加入 `BuildAndTrainModel` 方法：</span><span class="sxs-lookup"><span data-stu-id="0826b-269">Add the following code to the `BuildAndTrainModel` method:</span></span>

[!code-csharp[FastTreeBinaryClassificationTrainer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a FastTreeBinaryClassificationTrainer")]

## <a name="train-the-model"></a><span data-ttu-id="0826b-270">將模型定型</span><span class="sxs-lookup"><span data-stu-id="0826b-270">Train the model</span></span>

<span data-ttu-id="0826b-271">您會根據已載入和轉換的資料集將模型 <xref:Microsoft.ML.Data.TransformerChain%601>定型。</span><span class="sxs-lookup"><span data-stu-id="0826b-271">You train the model, <xref:Microsoft.ML.Data.TransformerChain%601>, based on the dataset that has been loaded and transformed.</span></span> <span data-ttu-id="0826b-272">定義評估工具之後，您會使用 <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> 方法來對模型進行定型，同時提供已載入的定型資料。</span><span class="sxs-lookup"><span data-stu-id="0826b-272">Once the estimator has been defined, you train your model using the <xref:Microsoft.ML.Data.EstimatorChain%601.Fit%2A> method while providing the already loaded training data.</span></span> <span data-ttu-id="0826b-273">這會傳回要用於預測的模型。</span><span class="sxs-lookup"><span data-stu-id="0826b-273">This returns a model to use for predictions.</span></span> <span data-ttu-id="0826b-274">`pipeline.Fit()` 會定型管線，並根據傳入的 `DataView` 傳回 `Transformer`。</span><span class="sxs-lookup"><span data-stu-id="0826b-274">`pipeline.Fit()` trains the pipeline and returns a `Transformer` based on the `DataView` passed in.</span></span> <span data-ttu-id="0826b-275">實驗會等到 `.Fit()` 方法執行之後才會執行。</span><span class="sxs-lookup"><span data-stu-id="0826b-275">The experiment is not executed until the `.Fit()` method runs.</span></span>

<span data-ttu-id="0826b-276">將下列程式碼加入 `BuildAndTrainModel` 方法：</span><span class="sxs-lookup"><span data-stu-id="0826b-276">Add the following code to the `BuildAndTrainModel` method:</span></span>

[!code-csharp[TrainModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

### <a name="save-and-return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="0826b-277">儲存並傳回所定型以供評估使用的模型</span><span class="sxs-lookup"><span data-stu-id="0826b-277">Save and Return the model trained to use for evaluation</span></span>

<span data-ttu-id="0826b-278">此時，您已有一個可整合至任何現有或新 .NET 應用程式之 <xref:Microsoft.ML.Data.TransformerChain%601> 類型的模型。</span><span class="sxs-lookup"><span data-stu-id="0826b-278">At this point, you have a model of type <xref:Microsoft.ML.Data.TransformerChain%601> that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="0826b-279">在 `BuildAndTrainModel` 方法的結尾傳回模型。</span><span class="sxs-lookup"><span data-stu-id="0826b-279">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="0826b-280">評估模型</span><span class="sxs-lookup"><span data-stu-id="0826b-280">Evaluate the model</span></span>

<span data-ttu-id="0826b-281">建立並定型模型之後，現在必須使用不同的資料集來評估它，以確保和驗證品質。</span><span class="sxs-lookup"><span data-stu-id="0826b-281">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="0826b-282">在 `Evaluate` 方法中，會傳入在 `BuildAndTrainModel` 中建立的模型以供評估。</span><span class="sxs-lookup"><span data-stu-id="0826b-282">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="0826b-283">在緊接著 `BuildAndTrainModel` 之後，建立 `Evaluate` 方法，如以下程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="0826b-283">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
{

}
```

<span data-ttu-id="0826b-284">`Evaluate` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="0826b-284">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="0826b-285">載入測試資料集。</span><span class="sxs-lookup"><span data-stu-id="0826b-285">Loads the test dataset.</span></span>
* <span data-ttu-id="0826b-286">建立 binaryclassification 評估工具。</span><span class="sxs-lookup"><span data-stu-id="0826b-286">Creates the binaryclassification evaluator.</span></span>
* <span data-ttu-id="0826b-287">評估模型並建立計量。</span><span class="sxs-lookup"><span data-stu-id="0826b-287">Evaluates the model and creates metrics.</span></span>
* <span data-ttu-id="0826b-288">顯示計量。</span><span class="sxs-lookup"><span data-stu-id="0826b-288">Displays the metrics.</span></span>

<span data-ttu-id="0826b-289">請使用下列程式碼，在緊接著 `Train` 方法呼叫底下，從 `Main` 方法新增對新方法的呼叫：</span><span class="sxs-lookup"><span data-stu-id="0826b-289">Add a call to the new method from the `Main` method, right under the `Train` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

<span data-ttu-id="0826b-290">接下來，您將會使用機器學習 `model` 參數 (一種轉換器)，以及 `splitTestSet` 參數來輸入特徵並傳回預測。</span><span class="sxs-lookup"><span data-stu-id="0826b-290">Next, you'll use the machine learning `model` parameter (a transformer) and the `splitTestSet` parameter to input the features and return predictions.</span></span> <span data-ttu-id="0826b-291">將下列程式碼加入 `Evaluate` 方法中作為的下一行：</span><span class="sxs-lookup"><span data-stu-id="0826b-291">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[PredictWithTransformer](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

<span data-ttu-id="0826b-292">`mlContext.BinaryClassification.Evaluate` 方法會使用指定的資料集來計算 `PredictionModel` 的品質計量。</span><span class="sxs-lookup"><span data-stu-id="0826b-292">The `mlContext.BinaryClassification.Evaluate` method computes the quality metrics for the `PredictionModel` using the specified dataset.</span></span> <span data-ttu-id="0826b-293">它會傳回 <xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics> 物件，其包含由二元分類評估工具所計算的整體計量。</span><span class="sxs-lookup"><span data-stu-id="0826b-293">It returns a <xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics> object that contains the overall metrics computed by binary classification evaluators.</span></span> <span data-ttu-id="0826b-294">若要顯示這些計量以判斷模型的品質，您必須先取得計量。</span><span class="sxs-lookup"><span data-stu-id="0826b-294">To display these to determine the quality of the model, you need to get the metrics first.</span></span> <span data-ttu-id="0826b-295">將下列程式碼加入為 `Evaluate` 方法中的下一行：</span><span class="sxs-lookup"><span data-stu-id="0826b-295">Add the following code as the next line in the `Evaluate` method:</span></span>

[!code-csharp[ComputeMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="0826b-296">顯示模型驗證的計量</span><span class="sxs-lookup"><span data-stu-id="0826b-296">Displaying the metrics for model validation</span></span>

<span data-ttu-id="0826b-297">使用下列程式碼來顯示計量、共用結果，然後依結果採取動作：</span><span class="sxs-lookup"><span data-stu-id="0826b-297">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

<span data-ttu-id="0826b-298">若要將您的模型先儲存成 .zip 檔案再傳回，請將下列呼叫 `SaveModelAsFile` 方法的程式碼加入為 `Evaluate` 中的下一行：</span><span class="sxs-lookup"><span data-stu-id="0826b-298">To save your model to a .zip file before returning, add the following code to call the `SaveModelAsFile` method as the next line in `Evaluate`:</span></span>

[!code-csharp[SaveModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallSaveModel "Save the model")]

## <a name="save-the-model-as-azip-file"></a><span data-ttu-id="0826b-299">將模型儲存為 .zip 檔案</span><span class="sxs-lookup"><span data-stu-id="0826b-299">Save the model as a.zip file</span></span>

<span data-ttu-id="0826b-300">請使用下列程式碼，在緊接著 `Evaluate` 方法之後，建立 `SaveModelAsFile` 方法：</span><span class="sxs-lookup"><span data-stu-id="0826b-300">Create the `SaveModelAsFile` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void SaveModelAsFile(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="0826b-301">`SaveModelAsFile` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="0826b-301">The `SaveModelAsFile` method executes the following tasks:</span></span>

* <span data-ttu-id="0826b-302">將模型儲存為 .zip 檔案。</span><span class="sxs-lookup"><span data-stu-id="0826b-302">Saves the model as a .zip file.</span></span>

<span data-ttu-id="0826b-303">接下來，請建立儲存模型的方法，以便在其他應用程式中重複使用。</span><span class="sxs-lookup"><span data-stu-id="0826b-303">Next, create a method to save the model so that it can be reused and consumed in other applications.</span></span> <span data-ttu-id="0826b-304">`ITransformer` 具有 <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> 方法，它會採用 `_modelPath` 全域欄位和 <xref:System.IO.Stream>。</span><span class="sxs-lookup"><span data-stu-id="0826b-304">The `ITransformer` has a <xref:Microsoft.ML.Data.TransformerChain%601.SaveTo(Microsoft.ML.IHostEnvironment,System.IO.Stream)> method that takes in the `_modelPath` global field, and a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="0826b-305">為了將模型儲存為 zip 檔案，您會在呼叫 `SaveTo` 方法之前立即建立 `FileStream`。</span><span class="sxs-lookup"><span data-stu-id="0826b-305">To save this as a zip file, you'll create the `FileStream` immediately before calling the `SaveTo` method.</span></span> <span data-ttu-id="0826b-306">將下列程式碼加入 `SaveModelAsFile` 方法中作為的下一行：</span><span class="sxs-lookup"><span data-stu-id="0826b-306">Add the following code to the `SaveModelAsFile` method as the next line:</span></span>

[!code-csharp[SaveToMethod](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SaveModel "Add the SaveTo Method")]

## <a name="deploy-and-predict-with-a-loaded-model"></a><span data-ttu-id="0826b-307">使用已載入的模型部署和預測</span><span class="sxs-lookup"><span data-stu-id="0826b-307">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="0826b-308">您也可以透過使用下列程式碼，以 `_modelPath` 寫入主控台訊息來顯示檔案寫入的位置：</span><span class="sxs-lookup"><span data-stu-id="0826b-308">You could also display where the file was written by writing a console message with the `_modelPath`, using the following code:</span></span>

```csharp
Console.WriteLine("The model is saved to {0}", _modelPath);
```

## <a name="predict-the-test-data-outcome-with-the-saved-model"></a><span data-ttu-id="0826b-309">使用儲存的模型來預測測試資料結果</span><span class="sxs-lookup"><span data-stu-id="0826b-309">Predict the test data outcome with the saved model</span></span>

<span data-ttu-id="0826b-310">請使用下列程式碼，在緊接著 `Evaluate` 方法之後，建立 `UseModelWithSingleItem` 方法：</span><span class="sxs-lookup"><span data-stu-id="0826b-310">Create the `UseModelWithSingleItem` method, just after the `Evaluate` method, using the following code:</span></span>

```csharp
private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="0826b-311">`UseModelWithSingleItem` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="0826b-311">The `UseModelWithSingleItem` method executes the following tasks:</span></span>

* <span data-ttu-id="0826b-312">建立單一評論的測試資料。</span><span class="sxs-lookup"><span data-stu-id="0826b-312">Creates a single comment of test data.</span></span>
* <span data-ttu-id="0826b-313">根據測試資料預測情感。</span><span class="sxs-lookup"><span data-stu-id="0826b-313">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="0826b-314">合併測試資料和預測來進行報告。</span><span class="sxs-lookup"><span data-stu-id="0826b-314">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="0826b-315">顯示預測的結果。</span><span class="sxs-lookup"><span data-stu-id="0826b-315">Displays the predicted results.</span></span>

<span data-ttu-id="0826b-316">請使用下列程式碼，在緊接著 `Evaluate` 方法呼叫底下，從 `Main` 方法新增對新方法的呼叫：</span><span class="sxs-lookup"><span data-stu-id="0826b-316">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallUseModelWithSingleItem](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

<span data-ttu-id="0826b-317">雖然 `model` 是可在多個資料列上運作的 `transformer`，但常見的生產環境案例需要根據個別範例進行預測。</span><span class="sxs-lookup"><span data-stu-id="0826b-317">While the `model` is a `transformer` that operates on many rows of data, a very common production scenario is a need for predictions on individual examples.</span></span> <span data-ttu-id="0826b-318"><xref:Microsoft.ML.PredictionEngine%602> 是從 `CreatePredictionEngine` 方法傳回的包裝函式。</span><span class="sxs-lookup"><span data-stu-id="0826b-318">The <xref:Microsoft.ML.PredictionEngine%602> is a wrapper that is returned from the `CreatePredictionEngine` method.</span></span> <span data-ttu-id="0826b-319">讓我們在 `Predict` 方法中的第一行加入下列程式碼，來建立 `PredictionEngine`：</span><span class="sxs-lookup"><span data-stu-id="0826b-319">Let's add the following code to create the `PredictionEngine` as the first line in the `Predict` Method:</span></span>

[!code-csharp[CreatePredictionEngine](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]
  
<span data-ttu-id="0826b-320">透過建立 `SentimentData` 的執行個體，在 `Predict` 方法中新增評論，以測試定型模型的預測：</span><span class="sxs-lookup"><span data-stu-id="0826b-320">Add a comment to test the trained model's prediction in the `Predict` method by creating an instance of `SentimentData`:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

 <span data-ttu-id="0826b-321">您可以使用該方法來預測評論資料之單一執行個體的正面或負面情感。</span><span class="sxs-lookup"><span data-stu-id="0826b-321">You can use that to predict the positive or negative sentiment of a single instance of the comment data.</span></span> <span data-ttu-id="0826b-322">若要取得預測，請在資料上使用 <xref:Microsoft.ML.PredictionEngine%602.Predict%2A>。</span><span class="sxs-lookup"><span data-stu-id="0826b-322">To get a prediction, use <xref:Microsoft.ML.PredictionEngine%602.Predict%2A> on the data.</span></span> <span data-ttu-id="0826b-323">請注意，輸入資料是一個字串，且模型包含特徵化。</span><span class="sxs-lookup"><span data-stu-id="0826b-323">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="0826b-324">在定型和預測期間，您的管線會同步。</span><span class="sxs-lookup"><span data-stu-id="0826b-324">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="0826b-325">您無須特別為預測撰寫前處理/特徵化程式碼，同一個 API 會同時負責批次和單次預測。</span><span class="sxs-lookup"><span data-stu-id="0826b-325">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

### <a name="use-the-model-prediction"></a><span data-ttu-id="0826b-326">使用模型：預測</span><span class="sxs-lookup"><span data-stu-id="0826b-326">Use the model: prediction</span></span>

<span data-ttu-id="0826b-327">顯示 `SentimentText` 和對應的情感預測，以便共用結果並根據結果相應地採取動作。</span><span class="sxs-lookup"><span data-stu-id="0826b-327">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="0826b-328">這稱為操作化，其中會使用傳回的資料作為操作原則的一部份。</span><span class="sxs-lookup"><span data-stu-id="0826b-328">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="0826b-329">請使用下列 <xref:System.Console.WriteLine?displayProperty=nameWithType> 程式碼來為結果建立顯示：</span><span class="sxs-lookup"><span data-stu-id="0826b-329">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="deploy-and-predict-with-a-loaded-model"></a><span data-ttu-id="0826b-330">使用已載入的模型部署和預測</span><span class="sxs-lookup"><span data-stu-id="0826b-330">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="0826b-331">請使用下列程式碼，緊接在 `SaveModelAsFile` 方法之前，建立 `UseLoadedModelWithBatchItems` 方法：</span><span class="sxs-lookup"><span data-stu-id="0826b-331">Create the `UseLoadedModelWithBatchItems` method, just before the `SaveModelAsFile` method, using the following code:</span></span>

```csharp
public static void UseLoadedModelWithBatchItems(MLContext mlContext)
{

}
```

<span data-ttu-id="0826b-332">`UseLoadedModelWithBatchItems` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="0826b-332">The `UseLoadedModelWithBatchItems` method executes the following tasks:</span></span>

* <span data-ttu-id="0826b-333">建立批次測試資料。</span><span class="sxs-lookup"><span data-stu-id="0826b-333">Creates batch test data.</span></span>
* <span data-ttu-id="0826b-334">根據測試資料預測情感。</span><span class="sxs-lookup"><span data-stu-id="0826b-334">Predicts sentiment based on test data.</span></span>
* <span data-ttu-id="0826b-335">合併測試資料和預測來進行報告。</span><span class="sxs-lookup"><span data-stu-id="0826b-335">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="0826b-336">顯示預測的結果。</span><span class="sxs-lookup"><span data-stu-id="0826b-336">Displays the predicted results.</span></span>

<span data-ttu-id="0826b-337">請使用下列程式碼，在緊接著 `UseModelWithSingleItem` 方法呼叫底下，從 `Main` 方法新增對新方法的呼叫：</span><span class="sxs-lookup"><span data-stu-id="0826b-337">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem` method call, using the following code:</span></span>

[!code-csharp[CallPredictModelLoaded](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseLoadedModelWithBatchItems "Call the CallUseLoadedModelWithBatchItems method")]

<span data-ttu-id="0826b-338">新增一些評論以測試 `UseLoadedModelWithBatchItems` 方法中定型模型的預測：</span><span class="sxs-lookup"><span data-stu-id="0826b-338">Add some comments to test the trained model's predictions in the `UseLoadedModelWithBatchItems` method:</span></span>

[!code-csharp[PredictionData](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

<span data-ttu-id="0826b-339">載入模型</span><span class="sxs-lookup"><span data-stu-id="0826b-339">Load the model</span></span>

[!code-csharp[LoadTheModel](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadModel "Load the model")]

<span data-ttu-id="0826b-340">既然您已有模型，現在即可利用 <xref:Microsoft.ML.ITransformer.Transform%2A> 方法，使用該模型來預測評論資料的 Toxic (有害的) 或 Non Toxic (無害的) 情感。</span><span class="sxs-lookup"><span data-stu-id="0826b-340">Now that you have a model, you can use that to predict the Toxic or Non Toxic sentiment of the comment data using the <xref:Microsoft.ML.ITransformer.Transform%2A> method.</span></span> <span data-ttu-id="0826b-341">若要取得預測，請在新資料上使用 `Predict`。</span><span class="sxs-lookup"><span data-stu-id="0826b-341">To get a prediction, use `Predict` on new data.</span></span> <span data-ttu-id="0826b-342">請注意，輸入資料是一個字串，且模型包含特徵化。</span><span class="sxs-lookup"><span data-stu-id="0826b-342">Note that the input data is a string and the model includes the featurization.</span></span> <span data-ttu-id="0826b-343">在定型和預測期間，您的管線會同步。</span><span class="sxs-lookup"><span data-stu-id="0826b-343">Your pipeline is in sync during training and prediction.</span></span> <span data-ttu-id="0826b-344">您無須特別為預測撰寫前處理/特徵化程式碼，同一個 API 會同時負責批次和單次預測。</span><span class="sxs-lookup"><span data-stu-id="0826b-344">You didn’t have to write preprocessing/featurization code specifically for predictions, and the same API takes care of both batch and one-time predictions.</span></span> <span data-ttu-id="0826b-345">將下列程式碼加入預測的 `UseLoadedModelWithBatchItems` 方法：</span><span class="sxs-lookup"><span data-stu-id="0826b-345">Add the following code to the `UseLoadedModelWithBatchItems` method for the predictions:</span></span>

[!code-csharp[Predict](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="use-the-loaded-model-for-prediction"></a><span data-ttu-id="0826b-346">使用載入的模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="0826b-346">Use the loaded model for prediction</span></span>

<span data-ttu-id="0826b-347">顯示 `SentimentText` 和對應的情感預測，以便共用結果並根據結果相應地採取動作。</span><span class="sxs-lookup"><span data-stu-id="0826b-347">Display `SentimentText` and corresponding sentiment prediction in order to share the results and act on them accordingly.</span></span> <span data-ttu-id="0826b-348">這稱為操作化，其中會使用傳回的資料作為操作原則的一部份。</span><span class="sxs-lookup"><span data-stu-id="0826b-348">This is called operationalization, using the returned data as part of the operational policies.</span></span> <span data-ttu-id="0826b-349">請使用下列 <xref:System.Console.WriteLine?displayProperty=nameWithType> 程式碼來為結果建立標頭：</span><span class="sxs-lookup"><span data-stu-id="0826b-349">Create a header for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputHeaders](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="0826b-350">顯示預測的結果之前，請先將情感和預測合併在一起，以將原始評論搭配其預測情感一起查看。</span><span class="sxs-lookup"><span data-stu-id="0826b-350">Before displaying the predicted results, combine the sentiment and prediction together to see the original comment with its predicted sentiment.</span></span> <span data-ttu-id="0826b-351">下列程式碼會使用 <xref:System.Linq.Enumerable.Zip%2A> 方法來使其發生，因此接下來請新增該程式碼：</span><span class="sxs-lookup"><span data-stu-id="0826b-351">The following code uses the <xref:System.Linq.Enumerable.Zip%2A> method to make that happen, so add that code next:</span></span>

[!code-csharp[BuildTuples](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#BuildSentimentPredictionPairs "Build the pairs of sentiment data and predictions")]

<span data-ttu-id="0826b-352">既然您已將 `SentimentText` 和 `Sentiment` 合併成一個類別，現在即可使用 <xref:System.Console.WriteLine?displayProperty=nameWithType> 方法來顯示結果：</span><span class="sxs-lookup"><span data-stu-id="0826b-352">Now that you've combined the `SentimentText` and `Sentiment` into a class, you can display the results using the <xref:System.Console.WriteLine?displayProperty=nameWithType> method:</span></span>

[!code-csharp[DisplayPredictions](../../../samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

<span data-ttu-id="0826b-353">由於推斷的元組元素名稱是 C# 7.1 中的新功能，而專案的預設語言版本是 C# 7.0，因此您必須將語言版本變更為 C# 7.1 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="0826b-353">Because inferred tuple element names are a new feature in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span>
<span data-ttu-id="0826b-354">若要這樣做，請在 [方案總管] 中的專案節點上按一下滑鼠右鍵，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="0826b-354">To do that, right-click on the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="0826b-355">選取 [建置] 索引標籤並選取 [進階] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0826b-355">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="0826b-356">從下拉式清單中，選取 [C# 7.1] (或更新版本)。</span><span class="sxs-lookup"><span data-stu-id="0826b-356">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="0826b-357">選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0826b-357">Select the **OK** button.</span></span>

## <a name="results"></a><span data-ttu-id="0826b-358">結果</span><span class="sxs-lookup"><span data-stu-id="0826b-358">Results</span></span>

<span data-ttu-id="0826b-359">您的結果應該與以下類似。</span><span class="sxs-lookup"><span data-stu-id="0826b-359">Your results should be similar to the following.</span></span> <span data-ttu-id="0826b-360">當管線進行處理時，會顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="0826b-360">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="0826b-361">您可能會看到警告或處理訊息。</span><span class="sxs-lookup"><span data-stu-id="0826b-361">You may see warnings, or processing messages.</span></span> <span data-ttu-id="0826b-362">為了清晰起見，下列結果中已將這些都移除。</span><span class="sxs-lookup"><span data-stu-id="0826b-362">These have been removed from the following results for clarity.</span></span>

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 79.14%
Auc: 86.27%
F1Score: 80.60%

=============== End of model evaluation ===============
The model is saved to C:\Tutorials\SentimentAnalysis\bin\Debug\netcoreapp2.1\Data\Model.zip

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This was a very bad steak | Prediction: Negative | Probability: 0.4641322
=============== End of Predictions ===============


=============== Prediction Test of loaded model with a multiple samples ===============

Sentiment: This was a horrible meal | Prediction: Negative | Probability: 0.1391833
Sentiment: I love this spaghetti. | Prediction: Positive | Probability: 0.9819039
=============== End of predictions ===============

=============== End of process ===============
Press any key to continue . . .

```

<span data-ttu-id="0826b-363">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="0826b-363">Congratulations!</span></span> <span data-ttu-id="0826b-364">您現在已成功建置可對訊息情感進行分類和預測的機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="0826b-364">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span> 

<span data-ttu-id="0826b-365">建立成功的模型是一個需要反覆嘗試的程序。</span><span class="sxs-lookup"><span data-stu-id="0826b-365">Building successful models is an iterative process.</span></span> <span data-ttu-id="0826b-366">此模型一開始的品質較低，因為此教學課程是使用小型的資料集來提供快速的模型定型。</span><span class="sxs-lookup"><span data-stu-id="0826b-366">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="0826b-367">如果您對於模型的品質感到不滿意，可以嘗試為它提供較大的定型資料集，或選擇不同的定型演算法，並針對每個演算法搭配不同的超參數來改善它。</span><span class="sxs-lookup"><span data-stu-id="0826b-367">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different hyper-parameters for each algorithm.</span></span>

<span data-ttu-id="0826b-368">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) 存放庫中找到此教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="0826b-368">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="0826b-369">後續步驟</span><span class="sxs-lookup"><span data-stu-id="0826b-369">Next steps</span></span>

<span data-ttu-id="0826b-370">在此教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="0826b-370">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="0826b-371">了解問題</span><span class="sxs-lookup"><span data-stu-id="0826b-371">Understand the problem</span></span>
> * <span data-ttu-id="0826b-372">選取適當的機器學習演算法</span><span class="sxs-lookup"><span data-stu-id="0826b-372">Select the appropriate machine learning algorithm</span></span>
> * <span data-ttu-id="0826b-373">準備您的資料</span><span class="sxs-lookup"><span data-stu-id="0826b-373">Prepare your data</span></span>
> * <span data-ttu-id="0826b-374">轉換資料</span><span class="sxs-lookup"><span data-stu-id="0826b-374">Transform the data</span></span>
> * <span data-ttu-id="0826b-375">將模型定型</span><span class="sxs-lookup"><span data-stu-id="0826b-375">Train the model</span></span>
> * <span data-ttu-id="0826b-376">評估模型</span><span class="sxs-lookup"><span data-stu-id="0826b-376">Evaluate the model</span></span>
> * <span data-ttu-id="0826b-377">使用訓練過的模型預測</span><span class="sxs-lookup"><span data-stu-id="0826b-377">Predict with the trained model</span></span>
> * <span data-ttu-id="0826b-378">使用已載入的模型部署和預測</span><span class="sxs-lookup"><span data-stu-id="0826b-378">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="0826b-379">前進到下一個教學課程來深入了解</span><span class="sxs-lookup"><span data-stu-id="0826b-379">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="0826b-380">問題分類</span><span class="sxs-lookup"><span data-stu-id="0826b-380">Issue Classification</span></span>](github-issue-classification.md)
