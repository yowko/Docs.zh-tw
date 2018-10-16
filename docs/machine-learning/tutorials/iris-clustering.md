---
title: 使用 ML.NET 群集鳶尾花 (群集)
description: 了解如何在群集案例中使用 ML.NET
author: pkulikov
ms.author: johalex
ms.date: 07/02/2018
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 46db9dc7ff425c483f1a9f61da5e806e598b16d5
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37937163"
---
# <a name="tutorial-use-mlnet-to-cluster-iris-flowers-clustering"></a><span data-ttu-id="4b708-103">教學課程：使用 ML.NET 群集鳶尾花 (群集)</span><span class="sxs-lookup"><span data-stu-id="4b708-103">Tutorial: Use ML.NET to cluster iris flowers (clustering)</span></span>

> [!NOTE]
> <span data-ttu-id="4b708-104">本主題涉及 ML.NET，此功能目前為公開預覽版，因此内容可能會有變更。</span><span class="sxs-lookup"><span data-stu-id="4b708-104">This topic refers to ML.NET, which is currently in Preview, and material may be subject to change.</span></span> <span data-ttu-id="4b708-105">如需詳細資訊，請瀏覽 [ML.NET 簡介](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet) \(英文)。</span><span class="sxs-lookup"><span data-stu-id="4b708-105">For more information, see the [ML.NET introduction](https://www.microsoft.com/net/learn/apps/machine-learning-and-ai/ml-dotnet).</span></span>

<span data-ttu-id="4b708-106">本教學課程說明如何使用 ML.NET 為[鳶尾花資料集](https://en.wikipedia.org/wiki/Iris_flower_data_set)建立一個[群集模型](../resources/tasks.md#clustering)。</span><span class="sxs-lookup"><span data-stu-id="4b708-106">This tutorial illustrates how to use ML.NET to build a [clustering model](../resources/tasks.md#clustering) for the [iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set).</span></span>

<span data-ttu-id="4b708-107">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="4b708-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="4b708-108">了解問題</span><span class="sxs-lookup"><span data-stu-id="4b708-108">Understand the problem</span></span>
> - <span data-ttu-id="4b708-109">選取適當的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="4b708-109">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="4b708-110">準備資料</span><span class="sxs-lookup"><span data-stu-id="4b708-110">Prepare the data</span></span>
> - <span data-ttu-id="4b708-111">載入並轉換資料</span><span class="sxs-lookup"><span data-stu-id="4b708-111">Load and transform the data</span></span>
> - <span data-ttu-id="4b708-112">選擇學習演算法</span><span class="sxs-lookup"><span data-stu-id="4b708-112">Choose a learning algorithm</span></span>
> - <span data-ttu-id="4b708-113">將模型定型</span><span class="sxs-lookup"><span data-stu-id="4b708-113">Train the model</span></span>
> - <span data-ttu-id="4b708-114">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="4b708-114">Use the model for predictions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4b708-115">必要條件</span><span class="sxs-lookup"><span data-stu-id="4b708-115">Prerequisites</span></span>

- <span data-ttu-id="4b708-116">已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)。</span><span class="sxs-lookup"><span data-stu-id="4b708-116">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="understand-the-problem"></a><span data-ttu-id="4b708-117">了解問題</span><span class="sxs-lookup"><span data-stu-id="4b708-117">Understand the problem</span></span>

<span data-ttu-id="4b708-118">這個問題是關於將一組鳶尾花按照花卉特徵分成不同的群組。</span><span class="sxs-lookup"><span data-stu-id="4b708-118">This problem is about dividing the set of iris flowers in different groups based on the flower features.</span></span> <span data-ttu-id="4b708-119">這些特徵是萼片的長度和寬度以及花瓣的長度和寬度。</span><span class="sxs-lookup"><span data-stu-id="4b708-119">Those features are the length and width of a sepal and the length and width of a petal.</span></span> <span data-ttu-id="4b708-120">本教學課程中假設不知道每個花卉的類型。</span><span class="sxs-lookup"><span data-stu-id="4b708-120">For this tutorial, assume that the type of each flower is unknown.</span></span> <span data-ttu-id="4b708-121">您想要從特徵了解資料集的結構，還要預測資料執行個體如何符合此結構。</span><span class="sxs-lookup"><span data-stu-id="4b708-121">You want to learn the structure of a data set from the features and predict how a data instance fits this structure.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="4b708-122">選取適當的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="4b708-122">Select the appropriate machine learning task</span></span>

<span data-ttu-id="4b708-123">因為您不知道每個花卉屬於哪個群組，所以您選擇[非監督式機器學習](../resources/glossary.md#unsupervised-machine-learning)工作。</span><span class="sxs-lookup"><span data-stu-id="4b708-123">As you don't know to which group each flower belongs to, you choose the [unsupervised machine learning](../resources/glossary.md#unsupervised-machine-learning) task.</span></span> <span data-ttu-id="4b708-124">若要按照類似元素歸於同一群組中的方式來分割群組中的資料集，請使用[群集](../resources/tasks.md#clustering)機器學習工作。</span><span class="sxs-lookup"><span data-stu-id="4b708-124">To divide a data set in groups in such a way that elements in the same group are more similar to each other than to those in other groups, use a [clustering](../resources/tasks.md#clustering) machine learning task.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="4b708-125">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="4b708-125">Create a console application</span></span>

1. <span data-ttu-id="4b708-126">開啟 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="4b708-126">Open Visual Studio 2017.</span></span> <span data-ttu-id="4b708-127">從功能表列中選取 [檔案]  >  [新增]  >  [專案]。</span><span class="sxs-lookup"><span data-stu-id="4b708-127">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="4b708-128">在 [新增專案] 對話方塊中，選取 [Visual C#] 節點，然後選取 [.NET Core] 節點。</span><span class="sxs-lookup"><span data-stu-id="4b708-128">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="4b708-129">然後選取 [主控台應用程式 (.NET Core)] 專案範本。</span><span class="sxs-lookup"><span data-stu-id="4b708-129">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="4b708-130">在 [名稱] 文字方塊中，輸入 "IrisClustering"，然後選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4b708-130">In the **Name** text box, type "IrisClustering" and then select the **OK** button.</span></span>

1. <span data-ttu-id="4b708-131">在您的專案中建立一個名為 *Data* 的目錄以儲存資料集和模型檔案：</span><span class="sxs-lookup"><span data-stu-id="4b708-131">Create a directory named *Data* in your project to store the data set and model files:</span></span>

    <span data-ttu-id="4b708-132">在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取 [新增] > [新增資料夾]。</span><span class="sxs-lookup"><span data-stu-id="4b708-132">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="4b708-133">輸入 "Data"，然後按 Enter。</span><span class="sxs-lookup"><span data-stu-id="4b708-133">Type "Data" and hit Enter.</span></span>

1. <span data-ttu-id="4b708-134">安裝 **Microsoft.ML** NuGet 套件：</span><span class="sxs-lookup"><span data-stu-id="4b708-134">Install the **Microsoft.ML** NuGet package:</span></span>

    <span data-ttu-id="4b708-135">在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="4b708-135">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="4b708-136">選擇 "nuget.org" 作為 [套件來源]，選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4b708-136">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="4b708-137">在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。</span><span class="sxs-lookup"><span data-stu-id="4b708-137">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="prepare-the-data"></a><span data-ttu-id="4b708-138">準備資料</span><span class="sxs-lookup"><span data-stu-id="4b708-138">Prepare the data</span></span>

1. <span data-ttu-id="4b708-139">下載 [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) 資料集，並將它儲存到上一個步驟中建立的 *Data* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="4b708-139">Download the [iris.data](https://github.com/dotnet/machinelearning/blob/master/test/data/iris.data) data set and save it to the *Data* folder you've created at the previous step.</span></span> <span data-ttu-id="4b708-140">如需有關鳶尾花資料集的詳細資訊，請參閱[鳶尾花資料集](https://en.wikipedia.org/wiki/Iris_flower_data_set)維基百科頁面和[鳶尾花資料集](http://archive.ics.uci.edu/ml/datasets/Iris)頁面 (也就是資料集的來源)。</span><span class="sxs-lookup"><span data-stu-id="4b708-140">For more information about the iris data set, see the [Iris flower data set](https://en.wikipedia.org/wiki/Iris_flower_data_set) Wikipedia page and the [Iris Data Set](http://archive.ics.uci.edu/ml/datasets/Iris) page, which is the source of the data set.</span></span>

1. <span data-ttu-id="4b708-141">以滑鼠右鍵按一下 [方案總管] 中的 *iris.data* 檔案，然後選取 [內容]。</span><span class="sxs-lookup"><span data-stu-id="4b708-141">In **Solution Explorer**, right-click the *iris.data* file and select **Properties**.</span></span> <span data-ttu-id="4b708-142">在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。</span><span class="sxs-lookup"><span data-stu-id="4b708-142">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="4b708-143">*Iris.data* 檔案包含五個資料行，分別表示：</span><span class="sxs-lookup"><span data-stu-id="4b708-143">The *iris.data* file contains five columns that represent:</span></span>

- <span data-ttu-id="4b708-144">萼片長度 (以公分為單位)</span><span class="sxs-lookup"><span data-stu-id="4b708-144">sepal length in centimetres</span></span>
- <span data-ttu-id="4b708-145">萼片寬度 (以公分為單位)</span><span class="sxs-lookup"><span data-stu-id="4b708-145">sepal width in centimetres</span></span>
- <span data-ttu-id="4b708-146">花瓣長度 (以公分為單位)</span><span class="sxs-lookup"><span data-stu-id="4b708-146">petal length in centimetres</span></span>
- <span data-ttu-id="4b708-147">花瓣寬度 (以公分為單位)</span><span class="sxs-lookup"><span data-stu-id="4b708-147">petal width in centimetres</span></span>
- <span data-ttu-id="4b708-148">鳶尾花的類型</span><span class="sxs-lookup"><span data-stu-id="4b708-148">type of iris flower</span></span>

<span data-ttu-id="4b708-149">為了示範群集方法，本教學課程會略過最後一個資料行。</span><span class="sxs-lookup"><span data-stu-id="4b708-149">For the sake of the clustering example, this tutorial ignores the last column.</span></span>

## <a name="create-data-classes"></a><span data-ttu-id="4b708-150">建立資料類別</span><span class="sxs-lookup"><span data-stu-id="4b708-150">Create data classes</span></span>

<span data-ttu-id="4b708-151">為輸入資料和預測建立類別：</span><span class="sxs-lookup"><span data-stu-id="4b708-151">Create classes for the input data and the predictions:</span></span>

1. <span data-ttu-id="4b708-152">在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="4b708-152">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="4b708-153">在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *IrisData.cs*。</span><span class="sxs-lookup"><span data-stu-id="4b708-153">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *IrisData.cs*.</span></span> <span data-ttu-id="4b708-154">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4b708-154">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="4b708-155">將下列的 `using` 指示詞加入新檔案：</span><span class="sxs-lookup"><span data-stu-id="4b708-155">Add the following `using` directive to the new file:</span></span>

   [!code-csharp[Add necessary usings](../../../samples/machine-learning/tutorials/IrisClustering/IrisData.cs#1)]

<span data-ttu-id="4b708-156">移除現有的類別定義，然後將下列程式碼 (定義 `IrisData` 和 `ClusterPrediction` 這兩個類別) 新增至 *IrisData.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="4b708-156">Remove the existing class definition and add the following code, which defines the classes `IrisData` and `ClusterPrediction`, to the *IrisData.cs* file:</span></span>

[!code-csharp[Define data classes](../../../samples/machine-learning/tutorials/IrisClustering/IrisData.cs#2)]

<span data-ttu-id="4b708-157">`IrisData` 是輸入資料類別，它含有資料集中每個特徵的定義。</span><span class="sxs-lookup"><span data-stu-id="4b708-157">`IrisData` is the input data class and has definitions for each feature from the data set.</span></span> <span data-ttu-id="4b708-158">請使用 [Column](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) 屬性來指定資料集檔案中來源資料行的索引。</span><span class="sxs-lookup"><span data-stu-id="4b708-158">Use the [Column](xref:Microsoft.ML.Runtime.Api.ColumnAttribute) attribute to specify the indices of the source columns in the data set file.</span></span>

<span data-ttu-id="4b708-159">`ClusterPrediction` 類別代表套用至 `IrisData` 執行個體的群集模型結果。</span><span class="sxs-lookup"><span data-stu-id="4b708-159">The `ClusterPrediction` class represents the output of the clustering model applied to an `IrisData` instance.</span></span> <span data-ttu-id="4b708-160">使用 [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) 屬性分別將 `PredictedClusterId` 和 `Distances` 欄位繫結至 **PredictedLabel** 和 **Score** 資料行。</span><span class="sxs-lookup"><span data-stu-id="4b708-160">Use the [ColumnName](xref:Microsoft.ML.Runtime.Api.ColumnNameAttribute) attribute to bind the `PredictedClusterId` and `Distances` fields to the **PredictedLabel** and **Score** columns respectively.</span></span> <span data-ttu-id="4b708-161">群集這些資料行的工作具有下列意義：</span><span class="sxs-lookup"><span data-stu-id="4b708-161">In case of the clustering task those columns has the following meaning:</span></span>

- <span data-ttu-id="4b708-162">**PredictedLabel** 資料行包含預測群集的 ID。</span><span class="sxs-lookup"><span data-stu-id="4b708-162">**PredictedLabel** column contains the ID of the predicted cluster.</span></span>
- <span data-ttu-id="4b708-163">**Score** 資料行包含平方歐幾里得距離到群集矩心的陣列。</span><span class="sxs-lookup"><span data-stu-id="4b708-163">**Score** column contains an array with squared Euclidean distances to the cluster centroids.</span></span> <span data-ttu-id="4b708-164">陣列長度等於群集數目。</span><span class="sxs-lookup"><span data-stu-id="4b708-164">The array length is equal to the number of clusters.</span></span>

> [!NOTE]
> <span data-ttu-id="4b708-165">使用 `float` 型別表示輸入和預測資料類別中的浮點值。</span><span class="sxs-lookup"><span data-stu-id="4b708-165">Use the `float` type to represent floating-point values in the input and prediction data classes.</span></span>

## <a name="define-data-and-model-paths"></a><span data-ttu-id="4b708-166">定義資料和模型路徑</span><span class="sxs-lookup"><span data-stu-id="4b708-166">Define data and model paths</span></span>

<span data-ttu-id="4b708-167">返回 *Program.cs* 檔案並新增兩個欄位，保存資料集檔案的路徑以及儲存模型之檔案的路徑：</span><span class="sxs-lookup"><span data-stu-id="4b708-167">Go back to the *Program.cs* file and add two fields to hold the paths to the data set file and to the file to save the model:</span></span>

- <span data-ttu-id="4b708-168">`_dataPath` 會針對具有用來定型模型之資料集的檔案，包含檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="4b708-168">`_dataPath` contains the path to the file with the data set used to train the model.</span></span>
- <span data-ttu-id="4b708-169">`_modelPath` 會針對儲存定型模型的檔案，包含檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="4b708-169">`_modelPath` contains the path to the file where the trained model is stored.</span></span>

<span data-ttu-id="4b708-170">將下列程式碼加入 `Main` 方法的緊鄰上方，以指定這些路徑：</span><span class="sxs-lookup"><span data-stu-id="4b708-170">Add the following code right above the `Main` method to specify those paths:</span></span>

[!code-csharp[Initialize paths](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#1)]

<span data-ttu-id="4b708-171">若要將上述的程式碼進行編譯，請在 *Program.cs* 檔案頂端加入下列 `using` 指示詞：</span><span class="sxs-lookup"><span data-stu-id="4b708-171">To make the preceding code compile, add the following `using` directives at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add usings for paths](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#2)]

## <a name="create-a-learning-pipeline"></a><span data-ttu-id="4b708-172">建立學習管線</span><span class="sxs-lookup"><span data-stu-id="4b708-172">Create a learning pipeline</span></span>

<span data-ttu-id="4b708-173">在 *Program.cs* 檔案頂端加入下列額外的 `using` 指示詞：</span><span class="sxs-lookup"><span data-stu-id="4b708-173">Add the following additional `using` directives to the top of the *Program.cs* file:</span></span>

[!code-csharp[Add Microsoft.ML usings](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#3)]

<span data-ttu-id="4b708-174">在 `Main` 方法中，以下列程式碼取代 `Console.WriteLine("Hello World!")`：</span><span class="sxs-lookup"><span data-stu-id="4b708-174">In the `Main` method, replace the `Console.WriteLine("Hello World!")` with the following code:</span></span>

[!code-csharp[Call the Train method](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#4)]

<span data-ttu-id="4b708-175">`Train` 方法會將模型定型。</span><span class="sxs-lookup"><span data-stu-id="4b708-175">The `Train` method trains the model.</span></span> <span data-ttu-id="4b708-176">請使用下列程式碼，在緊接著 `Main` 方法底下建立該方法：</span><span class="sxs-lookup"><span data-stu-id="4b708-176">Create that method just below the `Main` method, using the following code:</span></span>

```csharp
private static PredictionModel<IrisData, ClusterPrediction> Train()
{

}
```

<span data-ttu-id="4b708-177">學習管線會載入將模型定型所需的所有資料和演算法。</span><span class="sxs-lookup"><span data-stu-id="4b708-177">The learning pipeline loads all of the data and algorithms necessary to train the model.</span></span> <span data-ttu-id="4b708-178">將下列程式碼新增至 `Train` 方法：</span><span class="sxs-lookup"><span data-stu-id="4b708-178">Add the following code into the `Train` method:</span></span>

[!code-csharp[Initialize pipeline](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#5)]

## <a name="load-and-transform-data"></a><span data-ttu-id="4b708-179">載入並轉換資料</span><span class="sxs-lookup"><span data-stu-id="4b708-179">Load and transform data</span></span>

<span data-ttu-id="4b708-180">要執行的第一個步驟是載入訓練資料集。</span><span class="sxs-lookup"><span data-stu-id="4b708-180">The first step to perform is to load the training data set.</span></span> <span data-ttu-id="4b708-181">在我們的案例中，訓練資料集儲存在具有由 `_dataPath` 欄位所定義路徑的文字檔中。</span><span class="sxs-lookup"><span data-stu-id="4b708-181">In our case, the training data set is stored in the text file with a path defined by the `_dataPath` field.</span></span> <span data-ttu-id="4b708-182">檔案中的資料行是以逗號 (",") 分隔。</span><span class="sxs-lookup"><span data-stu-id="4b708-182">Columns in the file are separated by the comma (",").</span></span> <span data-ttu-id="4b708-183">將下列程式碼新增至 `Train` 方法：</span><span class="sxs-lookup"><span data-stu-id="4b708-183">Add the following code into the `Train` method:</span></span>

[!code-csharp[Add step to load data](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#6)]

<span data-ttu-id="4b708-184">下一個步驟是使用 <xref:Microsoft.ML.Transforms.ColumnConcatenator> 轉換類別，將所有特徵資料行合併為 **Features** 資料行。</span><span class="sxs-lookup"><span data-stu-id="4b708-184">The next step is to combine all of the feature columns into the **Features** column using the <xref:Microsoft.ML.Transforms.ColumnConcatenator> transformation class.</span></span> <span data-ttu-id="4b708-185">根據預設，學習演算法只會處理來自 **Features** 資料行的特徵。</span><span class="sxs-lookup"><span data-stu-id="4b708-185">By default, a learning algorithm processes only features from the **Features** column.</span></span> <span data-ttu-id="4b708-186">加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="4b708-186">Add the following code:</span></span>

[!code-csharp[Add step to concatenate columns](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#7)]

## <a name="choose-a-learning-algorithm"></a><span data-ttu-id="4b708-187">選擇學習演算法</span><span class="sxs-lookup"><span data-stu-id="4b708-187">Choose a learning algorithm</span></span>

<span data-ttu-id="4b708-188">將資料新增至管線並將其轉換成正確的輸入格式之後，您需選取學習演算法 (**學習工具**)。</span><span class="sxs-lookup"><span data-stu-id="4b708-188">After adding the data to the pipeline and transforming it into the correct input format, you select a learning algorithm (**learner**).</span></span> <span data-ttu-id="4b708-189">學習工具會將模型定型。</span><span class="sxs-lookup"><span data-stu-id="4b708-189">The learner trains the model.</span></span> <span data-ttu-id="4b708-190">ML.NET 提供一個可實作 [k-means 演算法](https://en.wikipedia.org/wiki/K-means_clustering)的 <xref:Microsoft.ML.Trainers.KMeansPlusPlusClusterer> 學習工具，該演算法已改進選擇初始群集矩心的方法。</span><span class="sxs-lookup"><span data-stu-id="4b708-190">ML.NET provides a <xref:Microsoft.ML.Trainers.KMeansPlusPlusClusterer> learner that implements [k-means algorithm](https://en.wikipedia.org/wiki/K-means_clustering) with an improved method for choosing the initial cluster centroids.</span></span>

<span data-ttu-id="4b708-191">將下列程式碼新增至 `Train` 方法中、上一個步驟中新增的資料處理程式碼之後：</span><span class="sxs-lookup"><span data-stu-id="4b708-191">Add the following code into the `Train` method following the data processing code added in the previous step:</span></span>

[!code-csharp[Add a learner step](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#8)]

<span data-ttu-id="4b708-192">使用 <xref:Microsoft.ML.Trainers.KMeansPlusPlusClusterer.K?displayProperty=nameWithType> 屬性以指定群集數目。</span><span class="sxs-lookup"><span data-stu-id="4b708-192">Use the <xref:Microsoft.ML.Trainers.KMeansPlusPlusClusterer.K?displayProperty=nameWithType> property to specify number of clusters.</span></span> <span data-ttu-id="4b708-193">上述程式碼會指定資料集分成三個群集。</span><span class="sxs-lookup"><span data-stu-id="4b708-193">The code above specifies that the data set should be split in three clusters.</span></span>

## <a name="train-the-model"></a><span data-ttu-id="4b708-194">將模型定型</span><span class="sxs-lookup"><span data-stu-id="4b708-194">Train the model</span></span>

<span data-ttu-id="4b708-195">上述小節中加入的步驟已準備好訓練的管道，不過，還沒有開始執行。</span><span class="sxs-lookup"><span data-stu-id="4b708-195">The steps added in the preceding sections prepared the pipeline for training, however, none have been executed.</span></span> <span data-ttu-id="4b708-196">`pipeline.Train<TInput, TOutput>` 方法會產生模型，以接受 `TInput` 類型的執行個體，並輸出`TOutput` 類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="4b708-196">The `pipeline.Train<TInput, TOutput>` method produces the model that takes in an instance of the `TInput` type and outputs an instance of the `TOutput` type.</span></span> <span data-ttu-id="4b708-197">將下列程式碼新增至 `Train` 方法：</span><span class="sxs-lookup"><span data-stu-id="4b708-197">Add the following code into the `Train` method:</span></span>

[!code-csharp[Train the model and return](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#9)]

### <a name="save-the-model"></a><span data-ttu-id="4b708-198">儲存模型</span><span class="sxs-lookup"><span data-stu-id="4b708-198">Save the model</span></span>

<span data-ttu-id="4b708-199">此時，您已有一個可整合至任何現有或新 .NET 應用程式的模型。</span><span class="sxs-lookup"><span data-stu-id="4b708-199">At this point, you have a model that can be integrated into any of your existing or new .NET applications.</span></span> <span data-ttu-id="4b708-200">若要將您的模型儲存成 .zip 檔案，請將下列程式碼加入至呼叫 `Train` 方法下面的 `Main` 方法：</span><span class="sxs-lookup"><span data-stu-id="4b708-200">To save your model to a .zip file, add the following code to the `Main` method below the call to the `Train` method:</span></span>

[!code-csharp[Save the model](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#10)]

<span data-ttu-id="4b708-201">在 `Main` 方法中使用 `await` 時，意謂著 `Main` 方法必須包含 `async` 修飾詞並傳回 `Task`：</span><span class="sxs-lookup"><span data-stu-id="4b708-201">Using `await` in the `Main` method means the `Main` method must have the `async` modifier and return a `Task`:</span></span>

[!code-csharp[Make the Main method async](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#11)]

<span data-ttu-id="4b708-202">您還必須在 *Program.cs* 檔案頂端加入下列 `using` 指示詞：</span><span class="sxs-lookup"><span data-stu-id="4b708-202">You also need to add the following `using` directive at the top of the *Program.cs* file:</span></span>

[!code-csharp[Add System.Threading.Tasks using](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#12)]

<span data-ttu-id="4b708-203">由於 `async Main` 方法是 C# 7.1 中的新增功能，而專案的預設語言版本是 C# 7.0，因此您必須將語言版本變更為 C# 7.1 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="4b708-203">Because the `async Main` method is the feature added in C# 7.1 and the default language version of the project is C# 7.0, you need to change the language version to C# 7.1 or higher.</span></span> <span data-ttu-id="4b708-204">若要這樣做，請以滑鼠右鍵按一下 [方案總管] 中的專案節點，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="4b708-204">To do that, right-click the project node in **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="4b708-205">選取 [建置] 索引標籤並選取 [進階] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4b708-205">Select the **Build** tab and select the **Advanced** button.</span></span> <span data-ttu-id="4b708-206">從下拉式清單中，選取 [C# 7.1] (或更新版本)。</span><span class="sxs-lookup"><span data-stu-id="4b708-206">In the dropdown, select  **C# 7.1** (or a higher version).</span></span> <span data-ttu-id="4b708-207">選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4b708-207">Select the **OK** button.</span></span>

## <a name="use-the-model-for-predictions"></a><span data-ttu-id="4b708-208">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="4b708-208">Use the model for predictions</span></span>

<span data-ttu-id="4b708-209">建立 `TestIrisData` 類型以容納測試資料執行個體：</span><span class="sxs-lookup"><span data-stu-id="4b708-209">Create the `TestIrisData` class to house test data instances:</span></span>

1. <span data-ttu-id="4b708-210">在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="4b708-210">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="4b708-211">在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *TestIrisData.cs*。</span><span class="sxs-lookup"><span data-stu-id="4b708-211">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *TestIrisData.cs*.</span></span> <span data-ttu-id="4b708-212">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4b708-212">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="4b708-213">將類別修改成靜態，如以下範例所示：</span><span class="sxs-lookup"><span data-stu-id="4b708-213">Modify the class to be static like in the following example:</span></span>

   [!code-csharp[Make class static](../../../samples/machine-learning/tutorials/IrisClustering/TestIrisData.cs#1)]

<span data-ttu-id="4b708-214">本教學課程介紹此類別內一個鳶尾花資料執行個體。</span><span class="sxs-lookup"><span data-stu-id="4b708-214">This tutorial introduces one iris data instance within this class.</span></span> <span data-ttu-id="4b708-215">您可以新增其他案例來對此模型進行實驗。</span><span class="sxs-lookup"><span data-stu-id="4b708-215">You can add other scenarios to experiment with the model.</span></span> <span data-ttu-id="4b708-216">將下列程式碼新增至 `TestIrisData` 類別：</span><span class="sxs-lookup"><span data-stu-id="4b708-216">Add the following code into the `TestIrisData` class:</span></span>

[!code-csharp[Test data](../../../samples/machine-learning/tutorials/IrisClustering/TestIrisData.cs#2)]

<span data-ttu-id="4b708-217">若要找出指定項目所屬的群集，請返回 *Program.cs* 檔案，然後將下列程式碼加入至 `Main` 方法：</span><span class="sxs-lookup"><span data-stu-id="4b708-217">To find out the cluster to which the specified item belongs to, go back to the *Program.cs* file and add the following code into the `Main` method:</span></span>

[!code-csharp[Predict and output results](../../../samples/machine-learning/tutorials/IrisClustering/Program.cs#13)]

<span data-ttu-id="4b708-218">執行程式，以查看哪些群集包含指定的資料執行個體以及從該執行個體到群集矩心的平方距離。</span><span class="sxs-lookup"><span data-stu-id="4b708-218">Run the program to see which cluster contains the specified data instance and squared distances from that instance to the cluster centroids.</span></span> <span data-ttu-id="4b708-219">您的結果應該與以下類似。</span><span class="sxs-lookup"><span data-stu-id="4b708-219">Your results should be similar to the following.</span></span> <span data-ttu-id="4b708-220">當管道處理時，它可能會顯示警告或正在處理的訊息。</span><span class="sxs-lookup"><span data-stu-id="4b708-220">As the pipeline processes, it might display warnings or processing messages.</span></span> <span data-ttu-id="4b708-221">為了清晰起見，下列輸出已移除這些訊息。</span><span class="sxs-lookup"><span data-stu-id="4b708-221">These have been removed from the following output for clarity.</span></span>

```text
Cluster: 2
Distances: 0.4192338 0.0008847713 0.9660053
```

<span data-ttu-id="4b708-222">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="4b708-222">Congratulations!</span></span> <span data-ttu-id="4b708-223">您現在已成功建置用來群集鳶尾花並進行預測的機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="4b708-223">You've now successfully built a machine learning model for iris clustering and used it to make predictions.</span></span> <span data-ttu-id="4b708-224">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisClustering) GitHub 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="4b708-224">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/IrisClustering) GitHub repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4b708-225">後續步驟</span><span class="sxs-lookup"><span data-stu-id="4b708-225">Next steps</span></span>

<span data-ttu-id="4b708-226">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="4b708-226">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="4b708-227">了解問題</span><span class="sxs-lookup"><span data-stu-id="4b708-227">Understand the problem</span></span>
> - <span data-ttu-id="4b708-228">選取適當的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="4b708-228">Select the appropriate machine learning task</span></span>
> - <span data-ttu-id="4b708-229">準備資料</span><span class="sxs-lookup"><span data-stu-id="4b708-229">Prepare the data</span></span>
> - <span data-ttu-id="4b708-230">載入並轉換資料</span><span class="sxs-lookup"><span data-stu-id="4b708-230">Load and transform the data</span></span>
> - <span data-ttu-id="4b708-231">選擇學習演算法</span><span class="sxs-lookup"><span data-stu-id="4b708-231">Choose a learning algorithm</span></span>
> - <span data-ttu-id="4b708-232">將模型定型</span><span class="sxs-lookup"><span data-stu-id="4b708-232">Train the model</span></span>
> - <span data-ttu-id="4b708-233">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="4b708-233">Use the model for predictions</span></span>

<span data-ttu-id="4b708-234">請查看我們的 GitHub 存放庫來繼續學習及尋找更多範例。</span><span class="sxs-lookup"><span data-stu-id="4b708-234">Check out our GitHub repository to continue learning and find more samples.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="4b708-235">dotnet/machinelearning GitHub 存放庫</span><span class="sxs-lookup"><span data-stu-id="4b708-235">dotnet/machinelearning GitHub repository</span></span>](https://github.com/dotnet/machinelearning/)
