---
title: 教學課程：分類支援問題 - 多類別分類
description: 了解如何在多類別分類案例中使用 ML.NET 來分類 GitHub 問題，以將它們指派至特定區域。
ms.date: 05/16/2019
ms.topic: tutorial
ms.custom: mvc, title-hack-0516
ms.openlocfilehash: da4f82c1b2c4ebdc8ccc8f307722c2719909cf56
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/24/2019
ms.locfileid: "66195579"
---
# <a name="tutorial-categorize-support-issues-using-multiclass-classification-with-ml-net"></a><span data-ttu-id="77669-103">教學課程：搭配 ML .NET 使用多類別分類來分類支援問題</span><span class="sxs-lookup"><span data-stu-id="77669-103">Tutorial: Categorize support issues using multiclass classification with ML .NET</span></span>

<span data-ttu-id="77669-104">此範例教學課程會示範使用 ML.NET，透過使用 Visual Studio 中 C# 的 .NET Core 主控台應用程式，建立 GitHub 問題分類器，來定型分類及預測 GitHub 問題 Area 標籤的模型。</span><span class="sxs-lookup"><span data-stu-id="77669-104">This sample tutorial illustrates using ML.NET to create a GitHub issue classifier to train a model that classifies and predicts the Area label for a GitHub issue via a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="77669-105">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="77669-105">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="77669-106">準備您的資料</span><span class="sxs-lookup"><span data-stu-id="77669-106">Prepare your data</span></span>
> * <span data-ttu-id="77669-107">轉換資料</span><span class="sxs-lookup"><span data-stu-id="77669-107">Transform the data</span></span>
> * <span data-ttu-id="77669-108">將模型定型</span><span class="sxs-lookup"><span data-stu-id="77669-108">Train the model</span></span>
> * <span data-ttu-id="77669-109">評估模型</span><span class="sxs-lookup"><span data-stu-id="77669-109">Evaluate the model</span></span>
> * <span data-ttu-id="77669-110">使用訓練過的模型預測</span><span class="sxs-lookup"><span data-stu-id="77669-110">Predict with the trained model</span></span>
> * <span data-ttu-id="77669-111">使用已載入的模型部署和預測</span><span class="sxs-lookup"><span data-stu-id="77669-111">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="77669-112">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="77669-112">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="77669-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="77669-113">Prerequisites</span></span>

* <span data-ttu-id="77669-114">已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)。</span><span class="sxs-lookup"><span data-stu-id="77669-114">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

* <span data-ttu-id="77669-115">[Github issues tab separated file (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) (Github 問題定位字元分隔檔案 (issues_train.tsv))。</span><span class="sxs-lookup"><span data-stu-id="77669-115">The [Github issues tab separated file (issues_train.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv).</span></span>
* <span data-ttu-id="77669-116">[Github issues test tab separated file (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) (Github 問題測試定位字元分隔檔案 (issues_test.tsv))。</span><span class="sxs-lookup"><span data-stu-id="77669-116">The [Github issues test tab separated file (issues_test.tsv)](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="77669-117">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="77669-117">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="77669-118">建立專案</span><span class="sxs-lookup"><span data-stu-id="77669-118">Create a project</span></span>

1. <span data-ttu-id="77669-119">開啟 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="77669-119">Open Visual Studio 2017.</span></span> <span data-ttu-id="77669-120">從功能表列中選取 [檔案]  >  [新增]  >  [專案]。</span><span class="sxs-lookup"><span data-stu-id="77669-120">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="77669-121">在 [新增專案] 對話方塊中，選取 [Visual C#] 節點，然後選取 [.NET Core] 節點。</span><span class="sxs-lookup"><span data-stu-id="77669-121">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="77669-122">然後選取 [主控台應用程式 (.NET Core)] 專案範本。</span><span class="sxs-lookup"><span data-stu-id="77669-122">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="77669-123">在 [名稱] 文字方塊中，鍵入 "GitHubIssueClassification"，然後選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="77669-123">In the **Name** text box, type "GitHubIssueClassification" and then select the **OK** button.</span></span>

2. <span data-ttu-id="77669-124">在您的專案中建立一個名為 *Data* 的目錄以儲存資料集檔案：</span><span class="sxs-lookup"><span data-stu-id="77669-124">Create a directory named *Data* in your project to save your data set files:</span></span>

    <span data-ttu-id="77669-125">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [新增] > [新增資料夾]。</span><span class="sxs-lookup"><span data-stu-id="77669-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="77669-126">輸入 "Data"，然後按 Enter。</span><span class="sxs-lookup"><span data-stu-id="77669-126">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="77669-127">在您的專案中建立名為 *Models* 的目錄，以儲存您的模型：</span><span class="sxs-lookup"><span data-stu-id="77669-127">Create a directory named *Models* in your project to save your model:</span></span>

    <span data-ttu-id="77669-128">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [新增] > [新增資料夾]。</span><span class="sxs-lookup"><span data-stu-id="77669-128">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="77669-129">鍵入 "Models"，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="77669-129">Type "Models" and hit Enter.</span></span>

4. <span data-ttu-id="77669-130">安裝「Microsoft.ML NuGet 套件」：</span><span class="sxs-lookup"><span data-stu-id="77669-130">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="77669-131">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="77669-131">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="77669-132">選擇 "nuget.org" 作為套件來源、選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、在清單中選取 **v 1.0.0** 套件，然後選取 [安裝] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="77669-132">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select the **v 1.0.0** package in the list, and select the **Install** button.</span></span> <span data-ttu-id="77669-133">在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。</span><span class="sxs-lookup"><span data-stu-id="77669-133">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

### <a name="prepare-your-data"></a><span data-ttu-id="77669-134">準備您的資料</span><span class="sxs-lookup"><span data-stu-id="77669-134">Prepare your data</span></span>

1. <span data-ttu-id="77669-135">下載 [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) 和 [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) 資料集，並將它們儲存至先前建立的 *Data* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="77669-135">Download the [issues_train.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_train.tsv) and the [issues_test.tsv](https://raw.githubusercontent.com/dotnet/samples/master/machine-learning/tutorials/GitHubIssueClassification/Data/issues_test.tsv) data sets and save them to the *Data* folder previously created.</span></span> <span data-ttu-id="77669-136">第一個資料集會將機器學習模型定型，第二個資料集則可用來評估您模型的準確率。</span><span class="sxs-lookup"><span data-stu-id="77669-136">The first dataset trains the machine learning model and the second can be used to evaluate how accurate your model is.</span></span>

2. <span data-ttu-id="77669-137">在 [方案總管] 中，於每個 \*.tsv 檔案上按一下滑鼠右鍵，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="77669-137">In Solution Explorer, right-click each of the \*.tsv files and select **Properties**.</span></span> <span data-ttu-id="77669-138">在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。</span><span class="sxs-lookup"><span data-stu-id="77669-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="77669-139">建立類別及定義路徑</span><span class="sxs-lookup"><span data-stu-id="77669-139">Create classes and define paths</span></span>

<span data-ttu-id="77669-140">在 *Program.cs* 檔案頂端新增下列額外的 `using` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="77669-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddUsings)]

<span data-ttu-id="77669-141">建立三個全域欄位來保留近期下載檔案的路徑，以及 `MLContext`、`DataView` 和 `PredictionEngine` 的全域變數：</span><span class="sxs-lookup"><span data-stu-id="77669-141">Create three global fields to hold the paths to the recently downloaded files, and global variables for the `MLContext`,`DataView`, and `PredictionEngine`:</span></span>

* <span data-ttu-id="77669-142">`_trainDataPath` 包含用來將模型定型的資料集路徑。</span><span class="sxs-lookup"><span data-stu-id="77669-142">`_trainDataPath` has the path to the dataset used to train the model.</span></span>
* <span data-ttu-id="77669-143">`_testDataPath` 包含用來評估模型的資料集路徑。</span><span class="sxs-lookup"><span data-stu-id="77669-143">`_testDataPath` has the path to the dataset used to evaluate the model.</span></span>
* <span data-ttu-id="77669-144">`_modelPath` 包含用來儲存定型模型的路徑。</span><span class="sxs-lookup"><span data-stu-id="77669-144">`_modelPath` has the path where the trained model is saved.</span></span>
* <span data-ttu-id="77669-145">`_mlContext` 是提供處理內容的 <xref:Microsoft.ML.MLContext>。</span><span class="sxs-lookup"><span data-stu-id="77669-145">`_mlContext` is the <xref:Microsoft.ML.MLContext> that provides processing context.</span></span>
* <span data-ttu-id="77669-146">`_trainingDataView` 是用來處理定型資料集的 <xref:Microsoft.ML.IDataView>。</span><span class="sxs-lookup"><span data-stu-id="77669-146">`_trainingDataView` is the <xref:Microsoft.ML.IDataView> used to process the training dataset.</span></span>
* <span data-ttu-id="77669-147">`_predEngine` 是用於單一預測的 <xref:Microsoft.ML.PredictionEngine%602>。</span><span class="sxs-lookup"><span data-stu-id="77669-147">`_predEngine` is the <xref:Microsoft.ML.PredictionEngine%602> used for single predictions.</span></span>

<span data-ttu-id="77669-148">將下列程式碼新增至 `Main` 方法正上方的一行，以指定這些路徑和其他變數：</span><span class="sxs-lookup"><span data-stu-id="77669-148">Add the following code to the line right above the `Main` method to specify those paths and the other variables:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DeclareGlobalVariables)]

<span data-ttu-id="77669-149">為輸入資料和預測建立一些類別。</span><span class="sxs-lookup"><span data-stu-id="77669-149">Create some classes for your input data and predictions.</span></span> <span data-ttu-id="77669-150">將新類別新增至專案：</span><span class="sxs-lookup"><span data-stu-id="77669-150">Add a new class to your project:</span></span>

1. <span data-ttu-id="77669-151">在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="77669-151">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="77669-152">在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *GitHubIssueData.cs*。</span><span class="sxs-lookup"><span data-stu-id="77669-152">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *GitHubIssueData.cs*.</span></span> <span data-ttu-id="77669-153">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="77669-153">Then, select the **Add** button.</span></span>

    <span data-ttu-id="77669-154">*GitHubIssueData.cs* 檔案隨即在程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="77669-154">The *GitHubIssueData.cs* file opens in the code editor.</span></span> <span data-ttu-id="77669-155">將下列 `using` 陳述式新增至 *GitHubIssueData.cs* 最上方：</span><span class="sxs-lookup"><span data-stu-id="77669-155">Add the following `using` statement to the top of *GitHubIssueData.cs*:</span></span>

[!code-csharp[AddUsings](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#AddUsings)]

<span data-ttu-id="77669-156">移除現有的類別定義，然後將下列程式碼 (具有 `GitHubIssue` 和 `IssuePrediction` 這兩個類別) 新增至 *GitHubIssueData.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="77669-156">Remove the existing class definition and add the following code, which has two classes `GitHubIssue` and `IssuePrediction`, to the *GitHubIssueData.cs* file:</span></span>

[!code-csharp[DeclareGlobalVariables](~/samples/machine-learning/tutorials/GitHubIssueClassification/GitHubIssueData.cs#DeclareTypes)]

<span data-ttu-id="77669-157">`label` 是您希望進行預測的資料行。</span><span class="sxs-lookup"><span data-stu-id="77669-157">The `label` is the column you want to predict.</span></span> <span data-ttu-id="77669-158">識別的 `Features` 是您提供模型，以預測標籤 (Label) 的輸入。</span><span class="sxs-lookup"><span data-stu-id="77669-158">The identified `Features` are the inputs you give the model to predict the Label.</span></span>

<span data-ttu-id="77669-159">請使用 [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) 來指定資料集中來源資料行的索引。</span><span class="sxs-lookup"><span data-stu-id="77669-159">Use the [LoadColumnAttribute](xref:Microsoft.ML.Data.LoadColumnAttribute) to specify the indices of the source columns in the data set.</span></span>

<span data-ttu-id="77669-160">`GitHubIssue` 是輸入資料集類別，並具有下列 <xref:System.String> 欄位：</span><span class="sxs-lookup"><span data-stu-id="77669-160">`GitHubIssue` is the input dataset class and has the following <xref:System.String> fields:</span></span>

* <span data-ttu-id="77669-161">第一個資料行 `ID`(GitHub 問題識別碼)</span><span class="sxs-lookup"><span data-stu-id="77669-161">the first column `ID` (GitHub Issue ID)</span></span>
* <span data-ttu-id="77669-162">第二個資料行 `Area`(用於定型的預測)</span><span class="sxs-lookup"><span data-stu-id="77669-162">the second column `Area` (the prediction for training)</span></span>
* <span data-ttu-id="77669-163">第三個資料行 `Title` (GitHub 問題標題) 是第一個用來預測 `Area` 的 `feature`</span><span class="sxs-lookup"><span data-stu-id="77669-163">the third column `Title` (GitHub issue title) is the first `feature` used for predicting the `Area`</span></span>
* <span data-ttu-id="77669-164">第四個資料行 `Description` 是第二個用來預測 `Area` 的 `feature`</span><span class="sxs-lookup"><span data-stu-id="77669-164">the fourth column  `Description` is the second `feature` used for predicting the `Area`</span></span>

<span data-ttu-id="77669-165">`IssuePrediction` 是在模型定型後，用來進行預測的類別。</span><span class="sxs-lookup"><span data-stu-id="77669-165">`IssuePrediction` is the class used for prediction after the model has been trained.</span></span> <span data-ttu-id="77669-166">它包含單一布林值 `string` (`Area`) 和 `PredictedLabel` `ColumnName` 屬性。</span><span class="sxs-lookup"><span data-stu-id="77669-166">It has a single `string` (`Area`) and a `PredictedLabel` `ColumnName` attribute.</span></span>  <span data-ttu-id="77669-167">`PredictedLabel` 的使用時機是在進行預測和評估的期間。</span><span class="sxs-lookup"><span data-stu-id="77669-167">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="77669-168">就評估而言，會使用含有定型資料、預設值及模型的輸入。</span><span class="sxs-lookup"><span data-stu-id="77669-168">For evaluation, an input with training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="77669-169">所有 ML.NET 作業都是從 [MLContext](xref:Microsoft.ML.MLContext) 類別開始。</span><span class="sxs-lookup"><span data-stu-id="77669-169">All ML.NET operations start in the [MLContext](xref:Microsoft.ML.MLContext) class.</span></span> <span data-ttu-id="77669-170">初始化 `mlContext` 會建立新的 ML.NET 環境，可在模型建立工作流程物件間共用。</span><span class="sxs-lookup"><span data-stu-id="77669-170">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="77669-171">就概念而言，它與 `Entity Framework` 中的 `DBContext` 相似。</span><span class="sxs-lookup"><span data-stu-id="77669-171">It's similar, conceptually, to `DBContext` in `Entity Framework`.</span></span>

### <a name="initialize-variables-in-main"></a><span data-ttu-id="77669-172">在 Main 中初始化變數</span><span class="sxs-lookup"><span data-stu-id="77669-172">Initialize variables in Main</span></span>

<span data-ttu-id="77669-173">將具有包含隨機種子 (`seed: 0`) 之新 `MLContext` 執行個體的 `_mlContext` 全域變數初始化，以讓多個定型間的結果可重複/具有確定性。</span><span class="sxs-lookup"><span data-stu-id="77669-173">Initialize the `_mlContext` global variable  with a new instance of `MLContext` with a random seed (`seed: 0`) for repeatable/deterministic results across multiple trainings.</span></span>  <span data-ttu-id="77669-174">在 `Main` 方法中，以下列程式碼取代 `Console.WriteLine("Hello World!")`：</span><span class="sxs-lookup"><span data-stu-id="77669-174">Replace the `Console.WriteLine("Hello World!")` line with the following code in the `Main` method:</span></span>

[!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateMLContext)]

## <a name="load-the-data"></a><span data-ttu-id="77669-175">載入資料</span><span class="sxs-lookup"><span data-stu-id="77669-175">Load the data</span></span>

<span data-ttu-id="77669-176">ML.NET 使用 [IDataView 類別](xref:Microsoft.ML.IDataView)作為描述數字或文字表格式資料彈性且有效率的方式。</span><span class="sxs-lookup"><span data-stu-id="77669-176">ML.NET uses the [IDataView class](xref:Microsoft.ML.IDataView) as a flexible, efficient way of describing numeric or text tabular data.</span></span> <span data-ttu-id="77669-177">`IDataView` 可載入文字檔案或即時進行 (例如 SQL 資料庫或記錄檔)。</span><span class="sxs-lookup"><span data-stu-id="77669-177">`IDataView` can load either text files or in real time (for example, SQL database or log files).</span></span>

<span data-ttu-id="77669-178">若要初始化並載入 `_trainingDataView` 全域變數以將其用於管線，請在 `mlContext` 初始化後，新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="77669-178">To initialize and load the `_trainingDataView` global variable in order to use it for the pipeline, add the following code after the  `mlContext` initialization:</span></span>

[!code-csharp[LoadTrainData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTrainData)]

<span data-ttu-id="77669-179">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) 會定義資料結構描述並讀入檔案中。</span><span class="sxs-lookup"><span data-stu-id="77669-179">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="77669-180">會接受資料路徑變數然後傳回 `IDataView`。</span><span class="sxs-lookup"><span data-stu-id="77669-180">It takes in the data path variables and returns an `IDataView`.</span></span>

<span data-ttu-id="77669-181">將下列程式碼加入為 `Main` 方法中的下一行程式碼：</span><span class="sxs-lookup"><span data-stu-id="77669-181">Add the following as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallProcessData](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallProcessData)]

<span data-ttu-id="77669-182">`ProcessData` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="77669-182">The `ProcessData` method executes the following tasks:</span></span>

* <span data-ttu-id="77669-183">擷取並轉換資料。</span><span class="sxs-lookup"><span data-stu-id="77669-183">Extracts and transforms the data.</span></span>
* <span data-ttu-id="77669-184">傳回處理管線。</span><span class="sxs-lookup"><span data-stu-id="77669-184">Returns the processing pipeline.</span></span>

<span data-ttu-id="77669-185">請使用下列程式碼，在緊接著 `Main` 方法之後，建立 `ProcessData` 方法：</span><span class="sxs-lookup"><span data-stu-id="77669-185">Create the `ProcessData` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> ProcessData()
{

}
```

## <a name="extract-features-and-transform-the-data"></a><span data-ttu-id="77669-186">擷取 Features 並傳輸資料</span><span class="sxs-lookup"><span data-stu-id="77669-186">Extract Features and transform the data</span></span>

<span data-ttu-id="77669-187">當您想要針對 `GitHubIssue` 預測 Area GitHub 標籤時，請使用 [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) 方法，將 `Area` 資料行轉換成數字索引鍵類型 `Label` 資料行 (分類演算法接受的格式)，並將它新增為新的資料集資料行：</span><span class="sxs-lookup"><span data-stu-id="77669-187">As you want to predict the Area GitHub label for a `GitHubIssue`, use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform the `Area` column into a numeric key type `Label` column (a format accepted by classification algorithms) and add it as a new dataset column:</span></span>

[!code-csharp[MapValueToKey](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#MapValueToKey)]

<span data-ttu-id="77669-188">接下來，請呼叫 `mlContext.Transforms.Text.FeaturizeText`，針對每個呼叫的 `TitleFeaturized` 和 `DescriptionFeaturized`，將文字 (`Title` 和 `Description`) 資料行轉換成數值向量。</span><span class="sxs-lookup"><span data-stu-id="77669-188">Next, call `mlContext.Transforms.Text.FeaturizeText` which transforms the text (`Title` and `Description`) columns into a numeric vector for each called `TitleFeaturized` and `DescriptionFeaturized`.</span></span> <span data-ttu-id="77669-189">將這兩個資料行的特徵轉換附加至管線，使用的程式碼如下：</span><span class="sxs-lookup"><span data-stu-id="77669-189">Append the featurization for both columns to the pipeline with the following code:</span></span>

[!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#FeaturizeText)]

<span data-ttu-id="77669-190">資料準備的最後一個步驟是使用 [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) 方法，將所有特徵資料行合併到 **Features** (特徵) 資料行。</span><span class="sxs-lookup"><span data-stu-id="77669-190">The last step in data preparation combines all of the feature columns into the **Features** column using the [Concatenate()](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate%2A) method.</span></span> <span data-ttu-id="77669-191">根據預設，學習演算法只會處理來自 **Features** 資料行的特徵。</span><span class="sxs-lookup"><span data-stu-id="77669-191">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="77669-192">將這此轉換附加至管線，使用的程式碼如下：</span><span class="sxs-lookup"><span data-stu-id="77669-192">Append this transformation to the pipeline with the following code:</span></span>

[!code-csharp[Concatenate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Concatenate)]

 <span data-ttu-id="77669-193">接著，附加 <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> 來快取 DataView，以便在您多次逐一查看資料時，使用快取可獲得更高的效能，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="77669-193">Next, append a <xref:Microsoft.ML.Data.EstimatorChain%601.AppendCacheCheckpoint%2A> to cache the DataView so when you iterate over the data multiple times using the cache might get better performance, as with the following code:</span></span>

[!code-csharp[AppendCache](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AppendCache)]

> [!WARNING]
> <span data-ttu-id="77669-194">針對小型/中型資料集使用 AppendCacheCheckpoint 以減少訓練時間。</span><span class="sxs-lookup"><span data-stu-id="77669-194">Use AppendCacheCheckpoint for small/medium datasets to lower training time.</span></span> <span data-ttu-id="77669-195">請不要在處理非常大的資料集時使用它 (移除 .AppendCacheCheckpoint())。</span><span class="sxs-lookup"><span data-stu-id="77669-195">Do NOT use it (remove .AppendCacheCheckpoint()) when handling very large datasets.</span></span>

<span data-ttu-id="77669-196">在 `ProcessData` 方法的結尾傳回管線。</span><span class="sxs-lookup"><span data-stu-id="77669-196">Return the pipeline at the end of the `ProcessData` method.</span></span>

[!code-csharp[ReturnPipeline](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnPipeline)]

<span data-ttu-id="77669-197">這個步驟會處理前置處理/特徵轉換。</span><span class="sxs-lookup"><span data-stu-id="77669-197">This step handles preprocessing/featurization.</span></span> <span data-ttu-id="77669-198">使用 ML.NET 中可用的額外元件可讓您的模型產生更佳的結果。</span><span class="sxs-lookup"><span data-stu-id="77669-198">Using additional components available in ML.NET can enable better results with your model.</span></span>

## <a name="build-and-train-the-model"></a><span data-ttu-id="77669-199">建置和定型模型</span><span class="sxs-lookup"><span data-stu-id="77669-199">Build and train the model</span></span>

<span data-ttu-id="77669-200">將下列呼叫新增至 `BuildAndTrainModel` 方法作為 `Main` 方法中的下一行程式碼：</span><span class="sxs-lookup"><span data-stu-id="77669-200">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main` method:</span></span>

[!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallBuildAndTrainModel)]

<span data-ttu-id="77669-201">`BuildAndTrainModel` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="77669-201">The `BuildAndTrainModel` method executes the following tasks:</span></span>

* <span data-ttu-id="77669-202">建立定型演算法類別。</span><span class="sxs-lookup"><span data-stu-id="77669-202">Creates the training algorithm class.</span></span>
* <span data-ttu-id="77669-203">將模型定型。</span><span class="sxs-lookup"><span data-stu-id="77669-203">Trains the model.</span></span>
* <span data-ttu-id="77669-204">根據定型資料預測區域。</span><span class="sxs-lookup"><span data-stu-id="77669-204">Predicts area based on training data.</span></span>
* <span data-ttu-id="77669-205">傳回模型。</span><span class="sxs-lookup"><span data-stu-id="77669-205">Returns the model.</span></span>

<span data-ttu-id="77669-206">請使用下列程式碼，在緊接著 `Main` 方法之後，建立 `BuildAndTrainModel` 方法：</span><span class="sxs-lookup"><span data-stu-id="77669-206">Create the `BuildAndTrainModel` method, just after the `Main` method, using the following code:</span></span>

```csharp
public static IEstimator<ITransformer> BuildAndTrainModel(IDataView trainingDataView, IEstimator<ITransformer> pipeline)
{

}
```

### <a name="about-the-classification-task"></a><span data-ttu-id="77669-207">關於分類工作</span><span class="sxs-lookup"><span data-stu-id="77669-207">About the classification task</span></span>

<span data-ttu-id="77669-208">分類是一項機器學習服務工作，會使用資料來**判斷**項目或資料列的分類、類型或類別，且經常是下列其中一種類型：</span><span class="sxs-lookup"><span data-stu-id="77669-208">Classification is a machine learning task that uses data to **determine** the category, type, or class of an item or row of data and is frequently one of the following types:</span></span>

* <span data-ttu-id="77669-209">二元：不是 A 就是 B。</span><span class="sxs-lookup"><span data-stu-id="77669-209">Binary: either A or B.</span></span>
* <span data-ttu-id="77669-210">多元分類：可使用單一模型來預測的多重分類。</span><span class="sxs-lookup"><span data-stu-id="77669-210">Multiclass: multiple categories that can be predicted by using a single model.</span></span>

<span data-ttu-id="77669-211">針對此類型的問題，請使用多類別分類學習演算法，因為您的問題類別預測可能是多個類別 (多類別) 的其中之一，而不只是兩個類別 (二元)。</span><span class="sxs-lookup"><span data-stu-id="77669-211">For this type of problem, use a Multiclass classification learning algorithm, since your issue category prediction can be one of multiple categories (multiclass) rather than just two (binary).</span></span>

<span data-ttu-id="77669-212">透過將下列內容新增為 `BuildAndTrainModel()` 中的第一行程式碼，將機器學習服務演算法附加到資料轉換定義：</span><span class="sxs-lookup"><span data-stu-id="77669-212">Append the machine learning algorithm to the data transformation definitions by adding the following as the first line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddTrainer](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTrainer)]

<span data-ttu-id="77669-213">[SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) 是您的多類別分類定型演算法。</span><span class="sxs-lookup"><span data-stu-id="77669-213">The [SdcaMaximumEntropy](xref:Microsoft.ML.Trainers.SdcaMaximumEntropyMulticlassTrainer) is your multiclass classification training algorithm.</span></span> <span data-ttu-id="77669-214">它會附加到 `pipeline` 並接受特徵化的 `Title` 和 `Description` (`Features`) 及 `Label` 輸入參數，以從歷史資料學習。</span><span class="sxs-lookup"><span data-stu-id="77669-214">This is appended to the `pipeline` and accepts the featurized `Title` and `Description` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="77669-215">將模型定型</span><span class="sxs-lookup"><span data-stu-id="77669-215">Train the model</span></span>

<span data-ttu-id="77669-216">將下列內容新增為 `BuildAndTrainModel()` 方法中的下一行程式碼，調整模型為合適於 `splitTrainSet` 資料並傳回已定型模型：</span><span class="sxs-lookup"><span data-stu-id="77669-216">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#TrainModel)]

<span data-ttu-id="77669-217">`Fit()` 方法會透過轉換資料集和套用定型來定型您的模型。</span><span class="sxs-lookup"><span data-stu-id="77669-217">The `Fit()`method trains your model by transforming the dataset and applying the training.</span></span>

<span data-ttu-id="77669-218">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) 是一種便利的 API，可讓您傳遞並在單一資料執行個體上接著執行預測。</span><span class="sxs-lookup"><span data-stu-id="77669-218">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span> <span data-ttu-id="77669-219">將此新增為 `BuildAndTrainModel()` 方法中的下一行：</span><span class="sxs-lookup"><span data-stu-id="77669-219">Add this as the next line in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[CreatePredictionEngine1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine1)]

### <a name="predict-with-the-trained-model"></a><span data-ttu-id="77669-220">使用訓練過的模型預測</span><span class="sxs-lookup"><span data-stu-id="77669-220">Predict with the trained model</span></span>

<span data-ttu-id="77669-221">透過建立 `GitHubIssue` 的執行個體，在 `Predict` 方法中新增 GitHub 問題，以測試所定型模型的預測：</span><span class="sxs-lookup"><span data-stu-id="77669-221">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[CreateTestIssue1](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreateTestIssue1)]

<span data-ttu-id="77669-222">使用 [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) 函式來針對單一資料列進行預測：</span><span class="sxs-lookup"><span data-stu-id="77669-222">Use the [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Predict)]

### <a name="using-the-model-prediction-results"></a><span data-ttu-id="77669-223">使用模型：預測結果</span><span class="sxs-lookup"><span data-stu-id="77669-223">Using the model: prediction results</span></span>

<span data-ttu-id="77669-224">顯示 `GitHubIssue` 和相對應的 `Area` 標籤預測，以共用結果並根據結果相應地採取動作。</span><span class="sxs-lookup"><span data-stu-id="77669-224">Display `GitHubIssue` and corresponding `Area` label prediction in order to share the results and act on them accordingly.</span></span>  <span data-ttu-id="77669-225">請使用下列 <xref:System.Console.WriteLine?displayProperty=nameWithType> 程式碼來為結果建立顯示：</span><span class="sxs-lookup"><span data-stu-id="77669-225">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#OutputPrediction)]

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="77669-226">傳回經訓練以供評估使用的模型</span><span class="sxs-lookup"><span data-stu-id="77669-226">Return the model trained to use for evaluation</span></span>

<span data-ttu-id="77669-227">在 `BuildAndTrainModel` 方法的結尾傳回模型。</span><span class="sxs-lookup"><span data-stu-id="77669-227">Return the model at the end of the `BuildAndTrainModel` method.</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#ReturnModel)]

## <a name="evaluate-the-model"></a><span data-ttu-id="77669-228">評估模型</span><span class="sxs-lookup"><span data-stu-id="77669-228">Evaluate the model</span></span>

<span data-ttu-id="77669-229">建立並定型模型之後，現在必須使用不同的資料集來評估它，以確保和驗證品質。</span><span class="sxs-lookup"><span data-stu-id="77669-229">Now that you've created and trained the model, you need to evaluate it with a different dataset for quality assurance and validation.</span></span> <span data-ttu-id="77669-230">在 `Evaluate` 方法中，會傳入在 `BuildAndTrainModel` 中建立的模型以供評估。</span><span class="sxs-lookup"><span data-stu-id="77669-230">In the `Evaluate` method, the model created in `BuildAndTrainModel` is passed in to be evaluated.</span></span> <span data-ttu-id="77669-231">在緊接著 `BuildAndTrainModel` 之後，建立 `Evaluate` 方法，如以下程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="77669-231">Create the `Evaluate` method, just after `BuildAndTrainModel`, as in the following code:</span></span>

```csharp
public static void Evaluate(DataViewSchema trainingDataViewSchema)
{

}
```

<span data-ttu-id="77669-232">`Evaluate` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="77669-232">The `Evaluate` method executes the following tasks:</span></span>

* <span data-ttu-id="77669-233">載入測試資料集。</span><span class="sxs-lookup"><span data-stu-id="77669-233">Loads the test dataset.</span></span>
* <span data-ttu-id="77669-234">建立多類別評估工具。</span><span class="sxs-lookup"><span data-stu-id="77669-234">Creates the multiclass evaluator.</span></span>
* <span data-ttu-id="77669-235">評估模型並建立計量。</span><span class="sxs-lookup"><span data-stu-id="77669-235">Evaluates the model and create metrics.</span></span>
* <span data-ttu-id="77669-236">顯示計量。</span><span class="sxs-lookup"><span data-stu-id="77669-236">Displays the metrics.</span></span>

<span data-ttu-id="77669-237">請使用下列程式碼，在緊接著 `BuildAndTrainModel` 方法呼叫底下，從 `Main` 方法新增對新方法的呼叫：</span><span class="sxs-lookup"><span data-stu-id="77669-237">Add a call to the new method from the `Main` method, right under the `BuildAndTrainModel` method call, using the following code:</span></span>

[!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallEvaluate)]

<span data-ttu-id="77669-238">如同您先前針對定型資料集所進行的操作，請透過將下列程式碼新增到 `Evaluate` 方法，來載入測試資料集：</span><span class="sxs-lookup"><span data-stu-id="77669-238">As you did previously with the training dataset, load the test dataset by adding the following code to the `Evaluate` method:</span></span>

[!code-csharp[LoadTestDataset](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#LoadTestDataset)]

<span data-ttu-id="77669-239">[Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) 方法會使用指定的資料集，計算模型的品質計量。</span><span class="sxs-lookup"><span data-stu-id="77669-239">The [Evaluate()](xref:Microsoft.ML.MulticlassClassificationCatalog.Evaluate%2A) method computes the quality metrics for the model using the specified dataset.</span></span> <span data-ttu-id="77669-240">它傳回的 <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> 物件包含多類別分類評估工具所計算的整體計量。</span><span class="sxs-lookup"><span data-stu-id="77669-240">It returns a <xref:Microsoft.ML.Data.MulticlassClassificationMetrics> object that contains the overall metrics computed by multiclass classification evaluators.</span></span>
<span data-ttu-id="77669-241">若要顯示計量以判斷模型的品質，您必須先取得計量。</span><span class="sxs-lookup"><span data-stu-id="77669-241">To display the metrics to determine the quality of the model, you need to get them first.</span></span>
<span data-ttu-id="77669-242">請注意我們在此處使用機器學習服務 `_trainedModel` 全域變數 (一個 [ITransformer](xref:Microsoft.ML.ITransformer)) 的 [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) 方法來輸入特徵並傳回預測。</span><span class="sxs-lookup"><span data-stu-id="77669-242">Notice the use of the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method of the machine learning `_trainedModel` global variable (an [ITransformer](xref:Microsoft.ML.ITransformer)) to input the features and return predictions.</span></span> <span data-ttu-id="77669-243">將下列程式碼加入 `Evaluate` 方法中作為的下一行：</span><span class="sxs-lookup"><span data-stu-id="77669-243">Add the following code to the `Evaluate` method as the next line:</span></span>

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#Evaluate)]

<span data-ttu-id="77669-244">針對多類別分類評估的計量如下：</span><span class="sxs-lookup"><span data-stu-id="77669-244">The following metrics are evaluated for multiclass classification:</span></span>

* <span data-ttu-id="77669-245">微精確度 - 每個範例類別組同樣都會對精確度計量提出貢獻。</span><span class="sxs-lookup"><span data-stu-id="77669-245">Micro Accuracy - Every sample-class pair contributes equally to the accuracy metric.</span></span>  <span data-ttu-id="77669-246">建議讓微精確度盡量接近 1。</span><span class="sxs-lookup"><span data-stu-id="77669-246">You want Micro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="77669-247">大精確度 - 每個類別同樣都會對精確度計量提出貢獻。</span><span class="sxs-lookup"><span data-stu-id="77669-247">Macro Accuracy - Every class contributes equally to the accuracy metric.</span></span> <span data-ttu-id="77669-248">少數類別會加上與較大類別相同的權重。</span><span class="sxs-lookup"><span data-stu-id="77669-248">Minority classes are given equal weight as the larger classes.</span></span> <span data-ttu-id="77669-249">建議讓大精確度盡量接近 1。</span><span class="sxs-lookup"><span data-stu-id="77669-249">You want Macro Accuracy to be as close to 1 as possible.</span></span>

* <span data-ttu-id="77669-250">記錄檔遺失 - 請參閱[記錄檔遺失](../resources/glossary.md#log-loss)。</span><span class="sxs-lookup"><span data-stu-id="77669-250">Log-loss - see [Log Loss](../resources/glossary.md#log-loss).</span></span> <span data-ttu-id="77669-251">建議讓記錄檔遺失盡量接近零。</span><span class="sxs-lookup"><span data-stu-id="77669-251">You want Log-loss to be as close to zero as possible.</span></span>

* <span data-ttu-id="77669-252">記錄檔遺失減少 - 範圍介於 [-inf, 100]，其中 100 表示完美的預測，而 0 表示平均預測。</span><span class="sxs-lookup"><span data-stu-id="77669-252">Log-loss reduction - Ranges from [-inf, 100], where 100 is perfect predictions and 0 indicates mean predictions.</span></span> <span data-ttu-id="77669-253">建議讓記錄檔遺失減少盡量接近零。</span><span class="sxs-lookup"><span data-stu-id="77669-253">You want Log-loss reduction to be as close to zero as possible.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="77669-254">顯示模型驗證的計量</span><span class="sxs-lookup"><span data-stu-id="77669-254">Displaying the metrics for model validation</span></span>

<span data-ttu-id="77669-255">使用下列程式碼來顯示計量、共用結果，然後依結果採取動作：</span><span class="sxs-lookup"><span data-stu-id="77669-255">Use the following code to display the metrics, share the results, and then act on them:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayMetrics)]

## <a name="deploy-and-predict-with-a-model"></a><span data-ttu-id="77669-256">部署及使用模型進行預測</span><span class="sxs-lookup"><span data-stu-id="77669-256">Deploy and Predict with a model</span></span>

<span data-ttu-id="77669-257">請使用下列程式碼，在緊接著 `Evaluate` 方法呼叫底下，從 `Main` 方法新增對新方法的呼叫：</span><span class="sxs-lookup"><span data-stu-id="77669-257">Add a call to the new method from the `Main` method, right under the `Evaluate` method call, using the following code:</span></span>

[!code-csharp[CallPredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CallPredictIssue)]

<span data-ttu-id="77669-258">請使用下列程式碼，緊接在 `Evaluate` 方法之後 (並緊接在 `SaveModelAsFile` 方法之前)，建立 `PredictIssue` 方法：</span><span class="sxs-lookup"><span data-stu-id="77669-258">Create the `PredictIssue` method, just after the `Evaluate` method (and just before the `SaveModelAsFile` method), using the following code:</span></span>

```csharp
private static void PredictIssue()
{

}
```

<span data-ttu-id="77669-259">`PredictIssue` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="77669-259">The `PredictIssue` method executes the following tasks:</span></span>

* <span data-ttu-id="77669-260">建立測試資料的單一問題。</span><span class="sxs-lookup"><span data-stu-id="77669-260">Creates a single issue of test data.</span></span>
* <span data-ttu-id="77669-261">根據測試資料預測區域。</span><span class="sxs-lookup"><span data-stu-id="77669-261">Predicts Area based on test data.</span></span>
* <span data-ttu-id="77669-262">合併測試資料和預測來進行報告。</span><span class="sxs-lookup"><span data-stu-id="77669-262">Combines test data and predictions for reporting.</span></span>
* <span data-ttu-id="77669-263">顯示預測的結果。</span><span class="sxs-lookup"><span data-stu-id="77669-263">Displays the predicted results.</span></span>

<span data-ttu-id="77669-264">透過建立 `GitHubIssue` 的執行個體，在 `Predict` 方法中新增 GitHub 問題，以測試所定型模型的預測：</span><span class="sxs-lookup"><span data-stu-id="77669-264">Add a GitHub issue to test the trained model's prediction in the `Predict` method by creating an instance of `GitHubIssue`:</span></span>

[!code-csharp[AddTestIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#AddTestIssue)]

<span data-ttu-id="77669-265">如同您先前進行的操作，請使用下列程式碼建立 `PredictionEngine` 執行個體：</span><span class="sxs-lookup"><span data-stu-id="77669-265">As you did previously, create a `PredictionEngine` instance with the following code:</span></span>

[!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#CreatePredictionEngine)]
  
<span data-ttu-id="77669-266">使用 `PredictionEngine` 來透過將下列程式碼新增到預測的 `PredictIssue` 方法，來預測 Area GitHub 標籤：</span><span class="sxs-lookup"><span data-stu-id="77669-266">Use the `PredictionEngine` to predict the Area GitHub label by adding the following code to the `PredictIssue` method for the prediction:</span></span>

[!code-csharp[PredictIssue](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#PredictIssue)]

### <a name="using-the-loaded-model-for-prediction"></a><span data-ttu-id="77669-267">使用載入的模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="77669-267">Using the loaded model for prediction</span></span>

<span data-ttu-id="77669-268">顯示 `Area` 以分類問題，並根據該分類採取動作。</span><span class="sxs-lookup"><span data-stu-id="77669-268">Display `Area` in order to categorize the issue and act on it accordingly.</span></span> <span data-ttu-id="77669-269">請使用下列 <xref:System.Console.WriteLine?displayProperty=nameWithType> 程式碼來為結果建立顯示：</span><span class="sxs-lookup"><span data-stu-id="77669-269">Create a display for the results using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

[!code-csharp[DisplayResults](~/samples/machine-learning/tutorials/GitHubIssueClassification/Program.cs#DisplayResults)]

## <a name="results"></a><span data-ttu-id="77669-270">結果</span><span class="sxs-lookup"><span data-stu-id="77669-270">Results</span></span>

<span data-ttu-id="77669-271">您的結果應該與以下類似。</span><span class="sxs-lookup"><span data-stu-id="77669-271">Your results should be similar to the following.</span></span> <span data-ttu-id="77669-272">當管線進行處理時，會顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="77669-272">As the pipeline processes, it displays messages.</span></span> <span data-ttu-id="77669-273">您可能會看到警告或處理訊息。</span><span class="sxs-lookup"><span data-stu-id="77669-273">You may see warnings, or processing messages.</span></span> <span data-ttu-id="77669-274">為了讓結果變得清楚，這些訊息已從下列結果中移除。</span><span class="sxs-lookup"><span data-stu-id="77669-274">These messages have been removed from the following results for clarity.</span></span>

```console
=============== Single Prediction just-trained-model - Result: area-System.Net ===============
*************************************************************************************************************
*       Metrics for Multi-class Classification model - Test Data
*------------------------------------------------------------------------------------------------------------
*       MicroAccuracy:    0.738
*       MacroAccuracy:    0.668
*       LogLoss:          .919
*       LogLossReduction: .643
*************************************************************************************************************
=============== Single Prediction - Result: area-System.Data ===============
```

<span data-ttu-id="77669-275">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="77669-275">Congratulations!</span></span> <span data-ttu-id="77669-276">您現在已成功建置可對 GitHub 問題分類和預測 Area 標籤的機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="77669-276">You've now successfully built a machine learning model for classifying and predicting an Area label for a GitHub issue.</span></span> <span data-ttu-id="77669-277">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="77669-277">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/GitHubIssueClassification) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="77669-278">後續步驟</span><span class="sxs-lookup"><span data-stu-id="77669-278">Next steps</span></span>

<span data-ttu-id="77669-279">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="77669-279">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="77669-280">準備您的資料</span><span class="sxs-lookup"><span data-stu-id="77669-280">Prepare your data</span></span>
> * <span data-ttu-id="77669-281">轉換資料</span><span class="sxs-lookup"><span data-stu-id="77669-281">Transform the data</span></span>
> * <span data-ttu-id="77669-282">將模型定型</span><span class="sxs-lookup"><span data-stu-id="77669-282">Train the model</span></span>
> * <span data-ttu-id="77669-283">評估模型</span><span class="sxs-lookup"><span data-stu-id="77669-283">Evaluate the model</span></span>
> * <span data-ttu-id="77669-284">使用訓練過的模型預測</span><span class="sxs-lookup"><span data-stu-id="77669-284">Predict with the trained model</span></span>
> * <span data-ttu-id="77669-285">使用已載入的模型部署和預測</span><span class="sxs-lookup"><span data-stu-id="77669-285">Deploy and Predict with a loaded model</span></span>

<span data-ttu-id="77669-286">前進到下一個教學課程來深入了解</span><span class="sxs-lookup"><span data-stu-id="77669-286">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="77669-287">計程車車資預測工具</span><span class="sxs-lookup"><span data-stu-id="77669-287">Taxi Fare Predictor</span></span>](taxi-fare.md)
