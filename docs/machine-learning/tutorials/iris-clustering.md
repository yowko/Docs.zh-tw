---
title: 使用叢集學習工具建立鳶尾花叢集 - ML.NET
description: 了解如何在群集案例中使用 ML.NET
author: pkulikov
ms.author: johalex
ms.date: 03/18/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 502a7aafd434650d09cefa2781d3749e5a435564
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2019
ms.locfileid: "58186126"
---
# <a name="tutorial-cluster-iris-flowers-using-a-clustering-learner-with-mlnet"></a><span data-ttu-id="574ae-103">教學課程：ML.NET 的使用叢集學習工具建立鳶尾花叢集</span><span class="sxs-lookup"><span data-stu-id="574ae-103">Tutorial: Cluster iris flowers using a clustering learner with ML.NET</span></span>

> [!NOTE]
> <span data-ttu-id="574ae-104">本主題涉及 ML.NET，此功能目前為公開預覽版，因此内容可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="574ae-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="574ae-105">如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) \(英文)。</span><span class="sxs-lookup"><span data-stu-id="574ae-105">For more information, see the [ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="574ae-106">此教學課程與關聯的範例目前是使用 **ML.NET 0.11 版**。</span><span class="sxs-lookup"><span data-stu-id="574ae-106">This tutorial and related sample are currently using **ML.NET version 0.11**.</span></span> <span data-ttu-id="574ae-107">如需詳細資訊，請參閱 [dotnet/machinelearning GitHub 存放庫](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes) \(英文\) 中的版本資訊。</span><span class="sxs-lookup"><span data-stu-id="574ae-107">For more information, see the release notes at the [dotnet/machinelearning GitHub repo](https://github.com/dotnet/machinelearning/tree/master/docs/release-notes).</span></span>

<span data-ttu-id="574ae-108">本教學課程說明如何使用 ML.NET 為[鳶尾花資料集](https://en.wikipedia.org/wiki/Iris_flower_data_set)建立一個[群集模型](../resources/tasks.md#clustering)。</span><span class="sxs-lookup"><span data-stu-id="574ae-108">This tutorial illustrates how to use ML.NET to build a [clustering model](../resources/tasks.md#clustering) for the [iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span></span>

<span data-ttu-id="574ae-109">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="574ae-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="574ae-110">了解問題</span><span class="sxs-lookup"><span data-stu-id="574ae-110">Understand the problem</span></span>
> - <span data-ttu-id="574ae-111">選取適當的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="574ae-111">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="574ae-112">準備資料</span><span class="sxs-lookup"><span data-stu-id="574ae-112">Prepare the data</span></span>
> - <span data-ttu-id="574ae-113">載入並轉換資料</span><span class="sxs-lookup"><span data-stu-id="574ae-113">Load and transform the data</span></span>
> - <span data-ttu-id="574ae-114">選擇學習演算法</span><span class="sxs-lookup"><span data-stu-id="574ae-114">Choose a learning algorithm</span></span>
> - <span data-ttu-id="574ae-115">將模型定型</span><span class="sxs-lookup"><span data-stu-id="574ae-115">Train the model</span></span>
> - <span data-ttu-id="574ae-116">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="574ae-116">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="574ae-117">必要條件</span><span class="sxs-lookup"><span data-stu-id="574ae-117">Prerequisites</span></span>

- <span data-ttu-id="574ae-118">已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)。</span><span class="sxs-lookup"><span data-stu-id="574ae-118">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="574ae-119">了解問題</span><span class="sxs-lookup"><span data-stu-id="574ae-119">Understand the problem</span></span>

<span data-ttu-id="574ae-120">這個問題是關於將一組鳶尾花按照花卉特徵分成不同的群組。</span><span class="sxs-lookup"><span data-stu-id="574ae-120">This problem is about dividing the set of iris flowers in different groups based on the flower features.</span></span> <span data-ttu-id="574ae-121">這些特徵是萼片的長度和寬度以及花瓣的長度和寬度。</span><span class="sxs-lookup"><span data-stu-id="574ae-121">Those features are the length and width of a sepal and the length and width of a petal.</span></span> <span data-ttu-id="574ae-122">本教學課程中假設不知道每個花卉的類型。</span><span class="sxs-lookup"><span data-stu-id="574ae-122">For this tutorial, assume that the type of each flower is unknown.</span></span> <span data-ttu-id="574ae-123">您想要從特徵了解資料集的結構，還要預測資料執行個體如何符合此結構。</span><span class="sxs-lookup"><span data-stu-id="574ae-123">You want to learn the structure of a data set from the features and predict how a data instance fits this structure.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="574ae-124">選取適當的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="574ae-124">Select the appropriate machine learning task</span></span>

<span data-ttu-id="574ae-125">因為您不知道每個花卉屬於哪個群組，所以您選擇[非監督式機器學習](../resources/glossary.md#unsupervised-machine-learning)工作。</span><span class="sxs-lookup"><span data-stu-id="574ae-125">As you don't know to which group each flower belongs to, you choose the [unsupervised machine learning](../resources/glossary.md#unsupervised-machine-learning) task.</span></span> <span data-ttu-id="574ae-126">若要按照類似元素歸於同一群組中的方式來分割群組中的資料集，請使用[群集](../resources/tasks.md#clustering)機器學習工作。</span><span class="sxs-lookup"><span data-stu-id="574ae-126">To divide a data set in groups in such a way that elements in the same group are more similar to each other than to those in other groups, use a [clustering](../resources/tasks.md#clustering) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="574ae-127">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="574ae-127">Create a console application</span></span>

1. <span data-ttu-id="574ae-128">開啟 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="574ae-128">Open Visual Studio 2017.</span></span> <span data-ttu-id="574ae-129">從功能表列中選取 [檔案]  >  [新增]  >  [專案]。</span><span class="sxs-lookup"><span data-stu-id="574ae-129">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="574ae-130">在 [新增專案] 對話方塊中，選取 [Visual C#] 節點，然後選取 [.NET Core] 節點。</span><span class="sxs-lookup"><span data-stu-id="574ae-130">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="574ae-131">然後選取 [主控台應用程式 (.NET Core)] 專案範本。</span><span class="sxs-lookup"><span data-stu-id="574ae-131">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="574ae-132">在 [名稱] 文字方塊中，鍵入 "IrisFlowerClustering"，然後選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="574ae-132">In the **Name** text box, type "IrisFlowerClustering" and then select the **OK** button.</span></span>

1. <span data-ttu-id="574ae-133">在您的專案中建立一個名為 *Data* 的目錄以儲存資料集和模型檔案：</span><span class="sxs-lookup"><span data-stu-id="574ae-133">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="574ae-134">在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取 [新增] > [新增資料夾]。</span><span class="sxs-lookup"><span data-stu-id="574ae-134">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="574ae-135">輸入 "Data"，然後按 Enter。</span><span class="sxs-lookup"><span data-stu-id="574ae-135">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="574ae-136">安裝 **Microsoft.ML** NuGet 套件：</span><span class="sxs-lookup"><span data-stu-id="574ae-136">Install the **Microsoft.ML** NuGet package:</span></span>

    <span data-ttu-id="574ae-137">在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="574ae-137">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="574ae-138">選擇 "nuget.org" 作為 [套件來源]，選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="574ae-138">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="574ae-139">在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。</span><span class="sxs-lookup"><span data-stu-id="574ae-139">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-the-data"></a><span data-ttu-id="574ae-140">準備資料</span><span class="sxs-lookup"><span data-stu-id="574ae-140">Prepare the data</span></span>

1. <span data-ttu-id="574ae-141">下載 [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) 資料集，並將它儲存到上一個步驟中建立的 *Data* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="574ae-141">Download the [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) data set and save it to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="574ae-142">如需有關鳶尾花資料集的詳細資訊，請參閱[鳶尾花資料集](https://en.wikipedia.org/wiki/Iris_flower_data_set)維基百科頁面和[鳶尾花資料集](https://archive.ics.uci.edu/ml/datasets/Iris)頁面 (也就是資料集的來源)。</span><span class="sxs-lookup"><span data-stu-id="574ae-142">For more information about the iris data set, see the [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia page and the [Iris Data Set](https://archive.ics.uci.edu/ml/datasets/Iris) page, which is the source of the data set.</span></span>

1. <span data-ttu-id="574ae-143">以滑鼠右鍵按一下 [方案總管] 中的 *iris.data* 檔案，然後選取 [內容]。</span><span class="sxs-lookup"><span data-stu-id="574ae-143">In **Solution Explorer**, right-click the *iris.data* file and select **Properties**.</span></span> <span data-ttu-id="574ae-144">在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。</span><span class="sxs-lookup"><span data-stu-id="574ae-144">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="574ae-145">*Iris.data* 檔案包含五個資料行，分別表示：</span><span class="sxs-lookup"><span data-stu-id="574ae-145">The *iris.data* file contains five columns that represent:</span></span>

- <span data-ttu-id="574ae-146">萼片長度 (以公分為單位)</span><span class="sxs-lookup"><span data-stu-id="574ae-146">sepal length in centimetres</span></span>
- <span data-ttu-id="574ae-147">萼片寬度 (以公分為單位)</span><span class="sxs-lookup"><span data-stu-id="574ae-147">sepal width in centimetres</span></span>
- <span data-ttu-id="574ae-148">花瓣長度 (以公分為單位)</span><span class="sxs-lookup"><span data-stu-id="574ae-148">petal length in centimetres</span></span>
- <span data-ttu-id="574ae-149">花瓣寬度 (以公分為單位)</span><span class="sxs-lookup"><span data-stu-id="574ae-149">petal width in centimetres</span></span>
- <span data-ttu-id="574ae-150">鳶尾花的類型</span><span class="sxs-lookup"><span data-stu-id="574ae-150">type of iris flower</span></span>

<span data-ttu-id="574ae-151">為了示範群集方法，本教學課程會略過最後一個資料行。</span><span class="sxs-lookup"><span data-stu-id="574ae-151">For the sake of the clustering example, this tutorial ignores the last column.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="574ae-152">建立資料類別</span><span class="sxs-lookup"><span data-stu-id="574ae-152">Create data classes</span></span>

<span data-ttu-id="574ae-153">為輸入資料和預測建立類別：</span><span class="sxs-lookup"><span data-stu-id="574ae-153">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="574ae-154">在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="574ae-154">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="574ae-155">在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *IrisData.cs*。</span><span class="sxs-lookup"><span data-stu-id="574ae-155">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *IrisData.cs*.</span></span> <span data-ttu-id="574ae-156">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="574ae-156">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="574ae-157">將下列的 `using` 指示詞加入新檔案：</span><span class="sxs-lookup"><span data-stu-id="574ae-157">Add the following `using` directive to the new file:</span></span>

   [!code-csharp[Add necessary usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#Usings)]

<span data-ttu-id="574ae-158">移除現有的類別定義，然後將下列程式碼 (定義 `IrisData` 和 `ClusterPrediction` 這兩個類別) 新增至 *IrisData.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="574ae-158">Remove the existing class definition and add the following code, which defines the classes `IrisData` and `ClusterPrediction`, to the *IrisData.cs* file:</span></span>

[!code-csharp[Define data classes](~/samples/machine-learning/tutorials/IrisFlowerClustering/IrisData.cs#ClassDefinitions)]

<span data-ttu-id="574ae-159">`IrisData` 是輸入資料類別，它含有資料集中每個特徵的定義。</span><span class="sxs-lookup"><span data-stu-id="574ae-159">`IrisData` is the input data class and has definitions for each feature from the data set.</span></span> <span data-ttu-id="574ae-160">請使用 [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) 屬性來指定資料集檔案中來源資料行的索引。</span><span class="sxs-lookup"><span data-stu-id="574ae-160">Use the [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute) attribute to specify the indices of the source columns in the data set file.</span></span>

<span data-ttu-id="574ae-161">`ClusterPrediction` 類別代表套用至 `IrisData` 執行個體的群集模型結果。</span><span class="sxs-lookup"><span data-stu-id="574ae-161">The `ClusterPrediction` class represents the output of the clustering model applied to an `IrisData` instance.</span></span> <span data-ttu-id="574ae-162">使用 [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) 屬性分別將 `PredictedClusterId` 和 `Distances` 欄位繫結至 **PredictedLabel** 和 **Score** 資料行。</span><span class="sxs-lookup"><span data-stu-id="574ae-162">Use the [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute) attribute to bind the `PredictedClusterId` and `Distances` fields to the **PredictedLabel** and **Score** columns respectively.</span></span> <span data-ttu-id="574ae-163">群集這些資料行的工作具有下列意義：</span><span class="sxs-lookup"><span data-stu-id="574ae-163">In case of the clustering task those columns have the following meaning:</span></span>

- <span data-ttu-id="574ae-164">**PredictedLabel** 資料行包含預測群集的 ID。</span><span class="sxs-lookup"><span data-stu-id="574ae-164">**PredictedLabel** column contains the ID of the predicted cluster.</span></span>
- <span data-ttu-id="574ae-165">**Score** 資料行包含平方歐幾里得距離到群集矩心的陣列。</span><span class="sxs-lookup"><span data-stu-id="574ae-165">**Score** column contains an array with squared Euclidean distances to the cluster centroids.</span></span> <span data-ttu-id="574ae-166">陣列長度等於群集數目。</span><span class="sxs-lookup"><span data-stu-id="574ae-166">The array length is equal to the number of clusters.</span></span>

> [!NOTE]
> <span data-ttu-id="574ae-167">使用 `float` 型別表示輸入和預測資料類別中的浮點值。</span><span class="sxs-lookup"><span data-stu-id="574ae-167">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="574ae-168">定義資料和模型路徑</span><span class="sxs-lookup"><span data-stu-id="574ae-168">Define data and model paths</span></span>

<span data-ttu-id="574ae-169">返回 *Program.cs* 檔案並新增兩個欄位，保存資料集檔案的路徑以及儲存模型之檔案的路徑：</span><span class="sxs-lookup"><span data-stu-id="574ae-169">Go back to the *Program.cs* file and add two fields to hold the paths to the data set file and to the file to save the model:</span></span>

- <span data-ttu-id="574ae-170">`_dataPath` 會針對具有用來定型模型之資料集的檔案，包含檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="574ae-170">`_dataPath` contains the path to the file with the data set used to train the model.</span></span>
- <span data-ttu-id="574ae-171">`_modelPath` 會針對儲存定型模型的檔案，包含檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="574ae-171">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="574ae-172">將下列程式碼加入 `Main` 方法的緊鄰上方，以指定這些路徑：</span><span class="sxs-lookup"><span data-stu-id="574ae-172">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Initialize paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Paths)]

<span data-ttu-id="574ae-173">若要將上述的程式碼進行編譯，請在 *Program.cs* 檔案頂端加入下列 `using` 指示詞：</span><span class="sxs-lookup"><span data-stu-id="574ae-173">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add usings for paths](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#UsingsForPaths)]

## <a name="create-ml-context"></a><span data-ttu-id="574ae-174">建立 ML 內容</span><span class="sxs-lookup"><span data-stu-id="574ae-174">Create ML context</span></span>

<span data-ttu-id="574ae-175">在 *Program.cs* 檔案頂端加入下列額外的 `using` 指示詞：</span><span class="sxs-lookup"><span data-stu-id="574ae-175">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[Add Microsoft.ML usings](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#MLUsings)]

<span data-ttu-id="574ae-176">在 `Console.WriteLine("Hello World!");` 方法中，以下列程式碼取代 `Main` 行：</span><span class="sxs-lookup"><span data-stu-id="574ae-176">In the `Main` method, replace the `Console.WriteLine("Hello World!");` line with the following code:</span></span>

[!code-csharp[Create ML context](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreateContext)]

<span data-ttu-id="574ae-177"><xref:Microsoft.ML.MLContext?displayProperty=nameWithType> 類別表示機器學習環境，並為資料載入、模型定型、預測和其他工作提供記錄機制和進入點。</span><span class="sxs-lookup"><span data-stu-id="574ae-177">The <xref:Microsoft.ML.MLContext?displayProperty=nameWithType> class represents the machine learning environment and provides mechanisms for logging and entry points for data loading, model training, prediction, and other tasks.</span></span> <span data-ttu-id="574ae-178">這在概念上類似於在 Entity Framework 中使用 `DbContext`。</span><span class="sxs-lookup"><span data-stu-id="574ae-178">This is comparable conceptually to using `DbContext` in Entity Framework.</span></span>

## <a name="setup-data-loading"></a><span data-ttu-id="574ae-179">設定資料載入</span><span class="sxs-lookup"><span data-stu-id="574ae-179">Setup data loading</span></span>

<span data-ttu-id="574ae-180">將下列程式碼新增至 `Main` 方法，以設定資料載入方式：</span><span class="sxs-lookup"><span data-stu-id="574ae-180">Add the following code to the `Main` method to setup the way to load data:</span></span>

[!code-csharp[Create text loader](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SetupTextLoader)]

<span data-ttu-id="574ae-181">使用 [LoadFromTextFile 方法](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29)的泛型 `MLContext.Data.LoadFromTextFile` 包裝函式來載入資料。</span><span class="sxs-lookup"><span data-stu-id="574ae-181">Load the data using the generic `MLContext.Data.LoadFromTextFile` wrapper for the [LoadFromTextFile method](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29).</span></span> <span data-ttu-id="574ae-182">它會傳回從 `IrisData` 資料模型類型推斷資料集結構描述的 <xref:Microsoft.Data.DataView.IDataView>、使用資料集標頭，並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="574ae-182">It returns a <xref:Microsoft.Data.DataView.IDataView> which infers the dataset schema from the `IrisData` data model type, uses the dataset header and is separated by a comma.</span></span>

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="574ae-183">建立學習管線</span><span class="sxs-lookup"><span data-stu-id="574ae-183">Create a learning pipeline</span></span>

<span data-ttu-id="574ae-184">在本教學課程中，叢集工作的學習管線包含下列兩個步驟：</span><span class="sxs-lookup"><span data-stu-id="574ae-184">For this tutorial, the learning pipeline of the clustering task comprises two following steps:</span></span>

- <span data-ttu-id="574ae-185">將載入的資料行串連成一個 [特徵] 資料行，以供叢集定型器使用；</span><span class="sxs-lookup"><span data-stu-id="574ae-185">concatenate loaded columns into one **Features** column, which is used by a clustering trainer;</span></span>
- <span data-ttu-id="574ae-186">使用 <xref:Microsoft.ML.Trainers.KMeans.KMeansPlusPlusTrainer> 定型器透過 k-means++ 叢集演算法將模型定型。</span><span class="sxs-lookup"><span data-stu-id="574ae-186">use a <xref:Microsoft.ML.Trainers.KMeans.KMeansPlusPlusTrainer> trainer to train the model using the k-means++ clustering algorithm.</span></span>

<span data-ttu-id="574ae-187">將下列程式碼加入 `Main` 方法：</span><span class="sxs-lookup"><span data-stu-id="574ae-187">Add the following code to the `Main` method:</span></span>

[!code-csharp[Create pipeline](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#CreatePipeline)]

<span data-ttu-id="574ae-188">此程式碼指定應該將資料集分成三個叢集。</span><span class="sxs-lookup"><span data-stu-id="574ae-188">The code specifies that the data set should be split in three clusters.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="574ae-189">將模型定型</span><span class="sxs-lookup"><span data-stu-id="574ae-189">Train the model</span></span>

<span data-ttu-id="574ae-190">上述小節中加入的步驟已準備好訓練的管道，不過，還沒有開始執行。</span><span class="sxs-lookup"><span data-stu-id="574ae-190">The steps added in the preceding sections prepared the pipeline for training, however, none have been executed.</span></span> <span data-ttu-id="574ae-191">將下列程式碼行新增至 `Main` 方法，以執行資料載入和模型定型：</span><span class="sxs-lookup"><span data-stu-id="574ae-191">Add the following line to the `Main` method to perform data loading and model training:</span></span>

[!code-csharp[Train the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#TrainModel)]

### <a name="save-the-model"></a><span data-ttu-id="574ae-192">儲存模型</span><span class="sxs-lookup"><span data-stu-id="574ae-192">Save the model</span></span>

<span data-ttu-id="574ae-193">此時，您已有一個可整合至任何現有或新 .NET 應用程式的模型。</span><span class="sxs-lookup"><span data-stu-id="574ae-193">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="574ae-194">若要將您的模型儲存成 .zip 檔案，請將下列程式碼新增至 `Main` 方法：</span><span class="sxs-lookup"><span data-stu-id="574ae-194">To save your model to a .zip file, add the following code to the `Main` method:</span></span>

[!code-csharp[Save the model](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#SaveModel)]

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="574ae-195">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="574ae-195">Use the model for predictions</span></span>

<span data-ttu-id="574ae-196">為了進行預測，請使用 <xref:Microsoft.ML.PredictionEngine%602> 類別，其帶領輸入類型的執行個體通過轉換程式管線，並產生輸出類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="574ae-196">To make predictions, use the <xref:Microsoft.ML.PredictionEngine%602> class that takes instances of the input type through the transformer pipeline and produces instances of the output type.</span></span> <span data-ttu-id="574ae-197">將下列程式碼行新增至 `Main` 方法，以建立該類別的執行個體：</span><span class="sxs-lookup"><span data-stu-id="574ae-197">Add the following line to the `Main` method to create an instance of that class:</span></span>

[!code-csharp[Create predictor](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#Predictor)]

<span data-ttu-id="574ae-198">建立 `TestIrisData` 類型以容納測試資料執行個體：</span><span class="sxs-lookup"><span data-stu-id="574ae-198">Create the `TestIrisData` class to house test data instances:</span></span>

1. <span data-ttu-id="574ae-199">在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="574ae-199">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="574ae-200">在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *TestIrisData.cs*。</span><span class="sxs-lookup"><span data-stu-id="574ae-200">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestIrisData.cs*.</span></span> <span data-ttu-id="574ae-201">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="574ae-201">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="574ae-202">將類別修改成靜態，如以下範例所示：</span><span class="sxs-lookup"><span data-stu-id="574ae-202">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[Make class static](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#Static)]

<span data-ttu-id="574ae-203">本教學課程介紹此類別內一個鳶尾花資料執行個體。</span><span class="sxs-lookup"><span data-stu-id="574ae-203">This tutorial introduces one iris data instance within this class.</span></span> <span data-ttu-id="574ae-204">您可以新增其他案例來對此模型進行實驗。</span><span class="sxs-lookup"><span data-stu-id="574ae-204">You can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="574ae-205">將下列程式碼新增至 `TestIrisData` 類別：</span><span class="sxs-lookup"><span data-stu-id="574ae-205">Add the following code into the `TestIrisData` class:</span></span>

[!code-csharp[Test data](~/samples/machine-learning/tutorials/IrisFlowerClustering/TestIrisData.cs#TestData)]

<span data-ttu-id="574ae-206">若要找出指定項目所屬的群集，請返回 *Program.cs* 檔案，然後將下列程式碼加入至 `Main` 方法：</span><span class="sxs-lookup"><span data-stu-id="574ae-206">To find out the cluster to which the specified item belongs to, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict and output results](~/samples/machine-learning/tutorials/IrisFlowerClustering/Program.cs#PredictionExample)]

<span data-ttu-id="574ae-207">執行程式，以查看哪些群集包含指定的資料執行個體以及從該執行個體到群集矩心的平方距離。</span><span class="sxs-lookup"><span data-stu-id="574ae-207">Run the program to see which cluster contains the specified data instance and squared distances from that instance to the cluster centroids.</span></span> <span data-ttu-id="574ae-208">您的結果應該與以下類似：</span><span class="sxs-lookup"><span data-stu-id="574ae-208">Your results should be similar to the following:</span></span>

```text
Cluster: 2
Distances: 11.69127 0.02159119 25.59896
```

<span data-ttu-id="574ae-209">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="574ae-209">Congratulations!</span></span> <span data-ttu-id="574ae-210">您現在已成功建置用來群集鳶尾花並進行預測的機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="574ae-210">You've now successfully built a machine learning model for iris clustering and used it to make predictions.</span></span> <span data-ttu-id="574ae-211">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="574ae-211">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisFlowerClustering) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="574ae-212">後續步驟</span><span class="sxs-lookup"><span data-stu-id="574ae-212">Next steps</span></span>

<span data-ttu-id="574ae-213">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="574ae-213">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="574ae-214">了解問題</span><span class="sxs-lookup"><span data-stu-id="574ae-214">Understand the problem</span></span>
> - <span data-ttu-id="574ae-215">選取適當的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="574ae-215">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="574ae-216">準備資料</span><span class="sxs-lookup"><span data-stu-id="574ae-216">Prepare the data</span></span>
> - <span data-ttu-id="574ae-217">載入並轉換資料</span><span class="sxs-lookup"><span data-stu-id="574ae-217">Load and transform the data</span></span>
> - <span data-ttu-id="574ae-218">選擇學習演算法</span><span class="sxs-lookup"><span data-stu-id="574ae-218">Choose a learning algorithm</span></span>
> - <span data-ttu-id="574ae-219">將模型定型</span><span class="sxs-lookup"><span data-stu-id="574ae-219">Train the model</span></span>
> - <span data-ttu-id="574ae-220">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="574ae-220">Use the model for predictions</span></span>

<span data-ttu-id="574ae-221">請查看我們的 GitHub 存放庫來繼續學習及尋找更多範例。</span><span class="sxs-lookup"><span data-stu-id="574ae-221">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="574ae-222">dotnet/machinelearning GitHub 存放庫</span><span class="sxs-lookup"><span data-stu-id="574ae-222">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
