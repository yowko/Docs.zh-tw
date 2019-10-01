---
title: 教學課程：建置電影推薦工具 - 矩陣因式分解
description: 本教學課程會示範如何在 .NET Core 主控台應用程式中使用 ML.NET 建置電影推薦工具。 這些步驟會使用 C# 和 Visual Studio 2019。
author: briacht
ms.date: 09/30/2019
ms.custom: mvc, title-hack-0516
ms.topic: tutorial
ms.openlocfilehash: 1db2ad6c078cb6201b2a6a4e2f8572f589cee684
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700956"
---
# <a name="tutorial-build-a-movie-recommender-using-matrix-factorizaton-with-mlnet"></a><span data-ttu-id="c0fe6-104">教學課程：搭配 ML.NET 使用矩陣因式分解建置電影推薦工具</span><span class="sxs-lookup"><span data-stu-id="c0fe6-104">Tutorial: Build a movie recommender using matrix factorizaton with ML.NET</span></span>

<span data-ttu-id="c0fe6-105">本教學課程會示範如何在 .NET Core 主控台應用程式中使用 ML.NET 建置電影推薦工具。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-105">This tutorial shows you how to build a movie recommender with ML.NET in a .NET Core console application.</span></span> <span data-ttu-id="c0fe6-106">這些步驟會使用 C# 和 Visual Studio 2019。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-106">The steps use C# and Visual Studio 2019.</span></span>

<span data-ttu-id="c0fe6-107">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="c0fe6-108">選取機器學習演算法</span><span class="sxs-lookup"><span data-stu-id="c0fe6-108">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="c0fe6-109">準備及載入您的資料</span><span class="sxs-lookup"><span data-stu-id="c0fe6-109">Prepare and load your data</span></span>
> * <span data-ttu-id="c0fe6-110">建置及定型模型</span><span class="sxs-lookup"><span data-stu-id="c0fe6-110">Build and train a model</span></span>
> * <span data-ttu-id="c0fe6-111">評估模型</span><span class="sxs-lookup"><span data-stu-id="c0fe6-111">Evaluate a model</span></span>
> * <span data-ttu-id="c0fe6-112">部署及取用模型</span><span class="sxs-lookup"><span data-stu-id="c0fe6-112">Deploy and consume a model</span></span>

<span data-ttu-id="c0fe6-113">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="machine-learning-workflow"></a><span data-ttu-id="c0fe6-114">機器學習工作流程</span><span class="sxs-lookup"><span data-stu-id="c0fe6-114">Machine learning workflow</span></span>

<span data-ttu-id="c0fe6-115">您將使用下列步驟來完成您的工作以及任何其他 ML.NET 工作：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-115">You will use the following steps to accomplish your task, as well as any other ML.NET task:</span></span>

1. [<span data-ttu-id="c0fe6-116">載入您的資料</span><span class="sxs-lookup"><span data-stu-id="c0fe6-116">Load your data</span></span>](#load-your-data)
2. [<span data-ttu-id="c0fe6-117">建置及定型您的模型</span><span class="sxs-lookup"><span data-stu-id="c0fe6-117">Build and train your model</span></span>](#build-and-train-your-model)
3. [<span data-ttu-id="c0fe6-118">評估您的模型</span><span class="sxs-lookup"><span data-stu-id="c0fe6-118">Evaluate your model</span></span>](#evaluate-your-model)
4. [<span data-ttu-id="c0fe6-119">使用您的模型</span><span class="sxs-lookup"><span data-stu-id="c0fe6-119">Use your model</span></span>](#use-your-model)

## <a name="prerequisites"></a><span data-ttu-id="c0fe6-120">必要條件</span><span class="sxs-lookup"><span data-stu-id="c0fe6-120">Prerequisites</span></span>

* <span data-ttu-id="c0fe6-121">已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-121">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="select-the-appropriate-machine-learning-task"></a><span data-ttu-id="c0fe6-122">選取適當的機器學習工作</span><span class="sxs-lookup"><span data-stu-id="c0fe6-122">Select the appropriate machine learning task</span></span>

<span data-ttu-id="c0fe6-123">有數種方式可以解決推薦問題，例如推薦電影清單或推薦相關產品清單；但在此情況下，您將預測使用者會給予該電影的評等 (1-5)，如果特定電影的預測評等高於所定義閾值，即推薦該電影 (評等愈高，使用者喜歡特定電影的可能性愈高)。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-123">There are several ways to approach recommendation problems, such as recommending a list of movies or recommending a list of related products, but in this case you will predict what rating (1-5) a user will give to a particular movie and recommend that movie if it's higher than a defined threshold (the higher the rating, the higher the likelihood of a user liking a particular movie).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="c0fe6-124">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="c0fe6-124">Create a console application</span></span>

### <a name="create-a-project"></a><span data-ttu-id="c0fe6-125">建立專案</span><span class="sxs-lookup"><span data-stu-id="c0fe6-125">Create a project</span></span>

1. <span data-ttu-id="c0fe6-126">開啟 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-126">Open Visual Studio 2017.</span></span> <span data-ttu-id="c0fe6-127">從功能表列中選取 [檔案]  >  [新增]  >  [專案]。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-127">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="c0fe6-128">在 [新增專案] 對話方塊中，選取 [Visual C#] 節點，然後選取 [.NET Core] 節點。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-128">In the **New Project** dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="c0fe6-129">然後選取 [主控台應用程式 (.NET Core)] 專案範本。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-129">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="c0fe6-130">在 [名稱] 文字方塊中，鍵入 "MovieRecommender"，然後選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-130">In the **Name** text box, type "MovieRecommender" and then select the **OK** button.</span></span>

2. <span data-ttu-id="c0fe6-131">在您的專案中建立一個名為 *Data* 的目錄以儲存資料集：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-131">Create a directory named *Data* in your project to store the data set:</span></span>

    <span data-ttu-id="c0fe6-132">在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取 [新增] > [新增資料夾]。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-132">In **Solution Explorer**, right-click the project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="c0fe6-133">輸入 "Data"，然後按 Enter。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-133">Type "Data" and hit Enter.</span></span>

3. <span data-ttu-id="c0fe6-134">安裝 **Microsoft.ML** 和 **Microsoft.ML.Recommender** NuGet 套件：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-134">Install the **Microsoft.ML** and **Microsoft.ML.Recommender** NuGet Packages:</span></span>

    <span data-ttu-id="c0fe6-135">在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-135">In **Solution Explorer**, right-click the project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="c0fe6-136">選擇 "nuget.org" 作為 [套件來源]、選取 [瀏覽] 索引標籤、搜尋 **Microsoft.ML**、從清單中選取該套件，然後選取 [安裝] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-136">Choose "nuget.org" as the Package source, select the **Browse** tab, search for **Microsoft.ML**, select the package in the list, and select the **Install** button.</span></span> <span data-ttu-id="c0fe6-137">在 [預覽變更] 對話方塊上，選取 [確定] 按鈕，然後在 [授權接受] 對話方塊上，如果您同意所列套件的授權條款，請選取 [我接受]。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-137">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="c0fe6-138">為 **Microsoft.ML.Recommender** 重複這些步驟。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-138">Repeat these steps for **Microsoft.ML.Recommender**.</span></span>

4. <span data-ttu-id="c0fe6-139">在您的 *Program.cs* 檔案最上方新增下列 `using` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-139">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[UsingStatements](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UsingStatements "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="c0fe6-140">下載您的資料</span><span class="sxs-lookup"><span data-stu-id="c0fe6-140">Download your data</span></span>

1. <span data-ttu-id="c0fe6-141">下載兩個資料集，並儲存至您先前建立的 *Data* 資料夾：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-141">Download the two datasets and save them to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="c0fe6-142">以滑鼠右鍵按一下 [*recommendation-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv)，然後選取 [另存連結 (或目標)...]</span><span class="sxs-lookup"><span data-stu-id="c0fe6-142">Right click on [*recommendation-ratings-train.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-train.csv) and select "Save Link (or Target) As..."</span></span>
   * <span data-ttu-id="c0fe6-143">以滑鼠右鍵按一下 [*recommendation-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv)，然後選取 [另存連結 (或目標)...]</span><span class="sxs-lookup"><span data-stu-id="c0fe6-143">Right click on [*recommendation-ratings-test.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/MatrixFactorization_MovieRecommendation/Data/recommendation-ratings-test.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="c0fe6-144">請務必將 \*.csv 檔案儲存至 *Data* 資料夾，或儲存在其他位置之後將 \*.csv 檔案移至 *Data* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-144">Make sure you either save the \*.csv files to the *Data* folder, or after you save it elsewhere, move the \*.csv files to the *Data* folder.</span></span>

2. <span data-ttu-id="c0fe6-145">在 [方案總管] 中，於每個 \*.csv 檔案上按一下滑鼠右鍵，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-145">In Solution Explorer, right-click each of the \*.csv files and select **Properties**.</span></span> <span data-ttu-id="c0fe6-146">在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

   ![在 VS 中有更新版本時複製](./media/movie-recommendation/copytoout.gif)

## <a name="load-your-data"></a><span data-ttu-id="c0fe6-148">載入您的資料</span><span class="sxs-lookup"><span data-stu-id="c0fe6-148">Load your data</span></span>

<span data-ttu-id="c0fe6-149">ML.NET 程序的第一個步驟是準備並載入模型定型和測試資料。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-149">The first step in the ML.NET process is to prepare and load your model training and testing data.</span></span>

<span data-ttu-id="c0fe6-150">推薦評等資料會分成 `Train` 和 `Test` 資料集。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-150">The recommendation ratings data is split into `Train` and `Test` datasets.</span></span> <span data-ttu-id="c0fe6-151">`Train` 資料用來調整您的模型。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-151">The `Train` data is used to fit your model.</span></span> <span data-ttu-id="c0fe6-152">`Test` 資料用來以您的已定型模型進行預測並評估模型效能。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-152">The `Test` data is used to make predictions with your trained model and evaluate model performance.</span></span> <span data-ttu-id="c0fe6-153">`Train` 和 `Test` 資料通常會分割為 80/20 比例。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-153">It's common to have an 80/20 split with `Train` and `Test` data.</span></span>

<span data-ttu-id="c0fe6-154">以下是您 \*.csv 檔案的資料預覽：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-154">Below is a preview of the data from your \*.csv files:</span></span>

![資料預覽](./media/movie-recommendation/csv-dataset-preview.png)

<span data-ttu-id="c0fe6-156">在 \*.csv 檔案中有四個資料行：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-156">In the \*.csv files, there are four columns:</span></span>

* `userId`
* `movieId`
* `rating`
* `timestamp`

<span data-ttu-id="c0fe6-157">在機器學習服務中，用來進行預測的資料行稱為[特徵](../resources/glossary.md#feature)，而傳回預測的資料行稱為[標籤](../resources/glossary.md#label)。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-157">In machine learning, the columns that are used to make a prediction are called [Features](../resources/glossary.md#feature), and the column with the returned prediction is called the [Label](../resources/glossary.md#label).</span></span>

<span data-ttu-id="c0fe6-158">您希望預測電影評等，因此評等資料行是 `Label`。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-158">You want to predict movie ratings, so the rating column is the `Label`.</span></span> <span data-ttu-id="c0fe6-159">其他三個資料行 `userId`、`movieId` 和 `timestamp` 都是 `Features`，用來預測 `Label`。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-159">The other three columns, `userId`, `movieId`, and `timestamp` are all `Features` used to predict the `Label`.</span></span>

| <span data-ttu-id="c0fe6-160">功能</span><span class="sxs-lookup"><span data-stu-id="c0fe6-160">Features</span></span>      | <span data-ttu-id="c0fe6-161">ThisAddIn</span><span class="sxs-lookup"><span data-stu-id="c0fe6-161">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |
| `timestamp`     |               |

<span data-ttu-id="c0fe6-162">由您決定使用哪些 `Features` 來預測 `Label`。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-162">It's up to you to decide which `Features` are used to predict the `Label`.</span></span> <span data-ttu-id="c0fe6-163">您也可以使用類似[特徵排列重要性](../how-to-guides/determine-global-feature-importance-in-model.md)的功能，來協助您選取最合適的 `Features`。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-163">You can also use methods like [Feature Permutation Importance](../how-to-guides/determine-global-feature-importance-in-model.md) to help with selecting the best `Features`.</span></span>

<span data-ttu-id="c0fe6-164">在此情況下，您應該排除 `timestamp` 資料行為 `Feature`，因為時間戳記並不會實際影響使用者對特定影片的評分方式，因此無法提供更精確的預測：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-164">In this case, you should eliminate the `timestamp` column as a `Feature` because the timestamp does not really affect how a user rates a given movie and thus would not contribute to making a more accurate prediction:</span></span>

| <span data-ttu-id="c0fe6-165">功能</span><span class="sxs-lookup"><span data-stu-id="c0fe6-165">Features</span></span>      | <span data-ttu-id="c0fe6-166">ThisAddIn</span><span class="sxs-lookup"><span data-stu-id="c0fe6-166">Label</span></span>         |
| ------------- |:-------------:|
| `userId`        |    `rating`     |
| `movieId`      |               |

<span data-ttu-id="c0fe6-167">接下來，您必須定義輸入類別的資料結構。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-167">Next you must define your data structure for the input class.</span></span>

<span data-ttu-id="c0fe6-168">將新類別新增至專案：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-168">Add a new class to your project:</span></span>

1. <span data-ttu-id="c0fe6-169">在 [方案總管] 中，以滑鼠右鍵按一下專案，然後選取 [新增] > [新項目]。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-169">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="c0fe6-170">在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *MovieRatingData.cs*。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-170">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *MovieRatingData.cs*.</span></span> <span data-ttu-id="c0fe6-171">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-171">Then, select the **Add** button.</span></span>

<span data-ttu-id="c0fe6-172">*MovieRatingData.cs* 檔案隨即在程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-172">The *MovieRatingData.cs* file opens in the code editor.</span></span> <span data-ttu-id="c0fe6-173">將下列 `using` 陳述式新增至 *MovieRatingData.cs* 的最上方：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-173">Add the following `using` statement to the top of *MovieRatingData.cs*:</span></span>

```csharp
using Microsoft.ML.Data;
```

<span data-ttu-id="c0fe6-174">移除現有類別定義，並在 *MovieRatingData.cs* 中新增下列程式碼，來建立稱為 `MovieRating` 的類別：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-174">Create a class called `MovieRating` by removing the existing class definition and adding the following code in *MovieRatingData.cs*:</span></span>

[!code-csharp[MovieRatingClass](~/samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#MovieRatingClass "Add the Movie Rating class")]

<span data-ttu-id="c0fe6-175">`MovieRating` 會指定輸入資料類別。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-175">`MovieRating` specifies an input data class.</span></span> <span data-ttu-id="c0fe6-176">[LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) 屬性會指定應該載入資料集內的哪些資料行 (依資料行索引)。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-176">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span> <span data-ttu-id="c0fe6-177">`userId` 和 `movieId` 資料行是您的 `Features` (您將給予模型來預測 `Label` 的輸入)，而評等資料行是您將預測的 `Label` (模型的輸出)。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-177">The `userId` and `movieId` columns are your `Features` (the inputs you will give the model to predict the `Label`), and the rating column is the `Label` that you will predict (the output of the model).</span></span>

<span data-ttu-id="c0fe6-178">建立另一個類別 `MovieRatingPrediction`，藉由在 *MovieRatingData.cs* 中的 `MovieRating` 類別之後新增下列程式碼，以代表預測的結果：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-178">Create another class, `MovieRatingPrediction`, to represent predicted results by adding the following code after the `MovieRating` class in *MovieRatingData.cs*:</span></span>

[!code-csharp[PredictionClass](~/samples/machine-learning/tutorials/MovieRecommendation/MovieRatingData.cs#PredictionClass "Add the Movie Prediction Class")]

<span data-ttu-id="c0fe6-179">在 *Program.cs* 中，以 `Main()` 內的下列程式碼取代 `Console.WriteLine("Hello World!")`：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-179">In *Program.cs*, replace the `Console.WriteLine("Hello World!")` with the following code inside `Main()`:</span></span>

[!code-csharp[MLContext](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MLContext "Add MLContext")]

<span data-ttu-id="c0fe6-180">[MLContext 類別](xref:Microsoft.ML.MLContext)是所有 ML.NET 作業的起點，且初始化 `mlContext` 會建立新的 ML.NET 環境，其可在模型建立工作流程物件之間共用。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-180">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="c0fe6-181">就概念而言，類似於 Entity Framework 中的 `DBContext`。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-181">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="c0fe6-182">在 `Main()` 之後，建立稱為 `LoadData()` 的方法：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-182">After `Main()`, create a method called `LoadData()`:</span></span>

```csharp
public static (IDataView training, IDataView test) LoadData(MLContext mlContext)
{

}
```

> [!NOTE]
> <span data-ttu-id="c0fe6-183">此方法將給出錯誤，直到您在下列步驟中新增 return 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-183">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="c0fe6-184">初始化您的資料路徑變數、從 \*.csv 檔案載入資料，並將下列程式碼新增為 `LoadData()` 中的下一行程式碼來傳回 `Train` 和 `Test` 資料作為 `IDataView` 物件：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-184">Initialize your data path variables, load the data from the \*.csv files, and return the `Train` and `Test` data as `IDataView` objects by adding the following as the next line of code in `LoadData()`:</span></span>

[!code-csharp[LoadData](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadData "Load data from data paths")]

<span data-ttu-id="c0fe6-185">ML.NET 中的資料以 [IDataView 類別](xref:Microsoft.ML.IDataView) 表示。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-185">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="c0fe6-186">`IDataView` 是彈性且有效率的表格式資料描述方式 (數值和文字)。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-186">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="c0fe6-187">資料可以從文字或即時 (例如 SQL 資料庫或記錄檔) 載入至 `IDataView` 物件。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-187">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="c0fe6-188">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) 會定義資料結構描述並讀入檔案中。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-188">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="c0fe6-189">會接受資料路徑變數然後傳回 `IDataView`。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-189">It takes in the data path variables and returns an `IDataView`.</span></span> <span data-ttu-id="c0fe6-190">在此情況下，您提供 `Test` 和 `Train` 檔案的路徑，並指示文字檔案標頭 (以便其正確使用資料行名稱) 和逗號字元資料分隔符號 (預設的分隔符號是索引標籤)。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-190">In this case, you provide the path for your `Test` and `Train` files and indicate both the text file header (so it can use the column names properly) and the comma character data separator (the default separator is a tab).</span></span>

<span data-ttu-id="c0fe6-191">在 `Main()` 方法中新增下列程式碼以呼叫 `LoadData()` 方法並傳回 `Train` 和 `Test` 資料：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-191">Add the following code in the `Main()` method to call your `LoadData()` method and return the `Train` and `Test` data:</span></span>

[!code-csharp[LoadDataMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#LoadDataMain "Add LoadData method to Main")]

## <a name="build-and-train-your-model"></a><span data-ttu-id="c0fe6-192">建置及定型您的模型</span><span class="sxs-lookup"><span data-stu-id="c0fe6-192">Build and train your model</span></span>

<span data-ttu-id="c0fe6-193">ML.NET 有三個主要概念：[資料](../resources/glossary.md#data)、[轉換器](../resources/glossary.md#transformer)以及[估算工具](../resources/glossary.md#estimator)。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-193">There are three major concepts in ML.NET: [Data](../resources/glossary.md#data), [Transformers](../resources/glossary.md#transformer), and [Estimators](../resources/glossary.md#estimator).</span></span>

<span data-ttu-id="c0fe6-194">機器學習服務定型演算法需要特定格式的資料。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-194">Machine learning training algorithms require data in a certain format.</span></span> <span data-ttu-id="c0fe6-195">`Transformers` 用來將表格式資料轉換成相容的格式。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-195">`Transformers` are used to transform tabular data to a compatible format.</span></span>

![轉換器映像](./media/movie-recommendation/transformer.png)

<span data-ttu-id="c0fe6-197">您會建立 `Estimators` 以在 ML.NET 中建立 `Transformers`。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-197">You create `Transformers` in ML.NET by creating `Estimators`.</span></span> <span data-ttu-id="c0fe6-198">`Estimators` 會接受資料並傳回 `Transformers`。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-198">`Estimators` take in data and return `Transformers`.</span></span>

![估算工具映像](./media/movie-recommendation/estimator.png)

<span data-ttu-id="c0fe6-200">您將用於定型模型的推薦定型演算法，即為 `Estimator` 的範例。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-200">The recommendation training algorithm you will use for training your model is an example of an `Estimator`.</span></span>

<span data-ttu-id="c0fe6-201">以下列步驟來建置 `Estimator`：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-201">Build an `Estimator` with the following steps:</span></span>

<span data-ttu-id="c0fe6-202">請使用下列程式碼，在緊接著 `LoadData()` 方法之後，建立 `BuildAndTrainModel()` 方法：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-202">Create the `BuildAndTrainModel()` method, just after the `LoadData()` method, using the following code:</span></span>

```csharp
public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView trainingDataView)
{

}
```

> [!NOTE]
> <span data-ttu-id="c0fe6-203">此方法將給出錯誤，直到您在下列步驟中新增 return 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-203">This method will give you an error until you add a return statement in the following steps.</span></span>

<span data-ttu-id="c0fe6-204">將下列程式碼新增至 `BuildAndTrainModel()` 以定義資料轉換：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-204">Define the data transformations by adding the following code to `BuildAndTrainModel()`:</span></span>

[!code-csharp[DataTransformations](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#DataTransformations "Define data transformations")]

<span data-ttu-id="c0fe6-205">由於 `userId` 和 `movieId` 代表使用者與電影標題，而非真正的值，所以您會使用 [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) 方法來將每個 `userId` 和每個 `movieId` 轉換成數值索引鍵類型 `Feature` 資料行 (推薦演算法所接受的格式)，並將其新增為新的資料集資料行：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-205">Since `userId` and `movieId` represent users and movie titles, not real values, you use the [MapValueToKey()](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) method to transform each `userId` and each `movieId` into a numeric key type `Feature` column (a format accepted by recommendation algorithms) and add them as new dataset columns:</span></span>

| <span data-ttu-id="c0fe6-206">userId</span><span class="sxs-lookup"><span data-stu-id="c0fe6-206">userId</span></span> | <span data-ttu-id="c0fe6-207">movieId</span><span class="sxs-lookup"><span data-stu-id="c0fe6-207">movieId</span></span> | <span data-ttu-id="c0fe6-208">ThisAddIn</span><span class="sxs-lookup"><span data-stu-id="c0fe6-208">Label</span></span> | <span data-ttu-id="c0fe6-209">userIdEncoded</span><span class="sxs-lookup"><span data-stu-id="c0fe6-209">userIdEncoded</span></span> | <span data-ttu-id="c0fe6-210">movieIdEncoded</span><span class="sxs-lookup"><span data-stu-id="c0fe6-210">movieIdEncoded</span></span> |
| ------------- |:-------------:| -----:|-----:|-----:|
| <span data-ttu-id="c0fe6-211">1</span><span class="sxs-lookup"><span data-stu-id="c0fe6-211">1</span></span> | <span data-ttu-id="c0fe6-212">1</span><span class="sxs-lookup"><span data-stu-id="c0fe6-212">1</span></span> | <span data-ttu-id="c0fe6-213">4</span><span class="sxs-lookup"><span data-stu-id="c0fe6-213">4</span></span> | <span data-ttu-id="c0fe6-214">userKey1</span><span class="sxs-lookup"><span data-stu-id="c0fe6-214">userKey1</span></span> | <span data-ttu-id="c0fe6-215">movieKey1</span><span class="sxs-lookup"><span data-stu-id="c0fe6-215">movieKey1</span></span> |
| <span data-ttu-id="c0fe6-216">1</span><span class="sxs-lookup"><span data-stu-id="c0fe6-216">1</span></span> | <span data-ttu-id="c0fe6-217">3</span><span class="sxs-lookup"><span data-stu-id="c0fe6-217">3</span></span> | <span data-ttu-id="c0fe6-218">4</span><span class="sxs-lookup"><span data-stu-id="c0fe6-218">4</span></span> | <span data-ttu-id="c0fe6-219">userKey1</span><span class="sxs-lookup"><span data-stu-id="c0fe6-219">userKey1</span></span> | <span data-ttu-id="c0fe6-220">movieKey2</span><span class="sxs-lookup"><span data-stu-id="c0fe6-220">movieKey2</span></span> |
| <span data-ttu-id="c0fe6-221">1</span><span class="sxs-lookup"><span data-stu-id="c0fe6-221">1</span></span> | <span data-ttu-id="c0fe6-222">6</span><span class="sxs-lookup"><span data-stu-id="c0fe6-222">6</span></span> | <span data-ttu-id="c0fe6-223">4</span><span class="sxs-lookup"><span data-stu-id="c0fe6-223">4</span></span> | <span data-ttu-id="c0fe6-224">userKey1</span><span class="sxs-lookup"><span data-stu-id="c0fe6-224">userKey1</span></span> | <span data-ttu-id="c0fe6-225">movieKey3</span><span class="sxs-lookup"><span data-stu-id="c0fe6-225">movieKey3</span></span> |

<span data-ttu-id="c0fe6-226">將下列程式碼新增為 `BuildAndTrainModel()` 中的下一行程式碼，以選擇機器學習演算法，並將其附加至資料轉換定義中：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-226">Choose the machine learning algorithm and append it to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[AddAlgorithm](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#AddAlgorithm "Add the training algorithm with options")]

<span data-ttu-id="c0fe6-227">[MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) 是您的推薦定型演算法。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-227">The [MatrixFactorizationTrainer](xref:Microsoft.ML.RecommendationCatalog.RecommendationTrainers.MatrixFactorization%28Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options%29) is your recommendation training algorithm.</span></span>  <span data-ttu-id="c0fe6-228">當您擁有使用者過去如何評等產品的資料時，[矩陣分解](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems))是推薦的常見方法，此亦為本教學課程資料集的情況。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-228">[Matrix Factorization](https://en.wikipedia.org/wiki/Matrix_factorization_(recommender_systems)) is a common approach to recommendation when you have data on how users have rated products in the past, which is the case for the datasets in this tutorial.</span></span> <span data-ttu-id="c0fe6-229">當您有不同的可用資料時，也有其他推薦演算法 (請參閱[其他推薦演算法](#other-recommendation-algorithms)一節以深入了解)。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-229">There are other recommendation algorithms for when you have different data available (see the [Other recommendation algorithms](#other-recommendation-algorithms) section below to learn more).</span></span>

<span data-ttu-id="c0fe6-230">在此案例中，`Matrix Factorization` 演算法使用的方法稱為「共同篩選」，此方法假設如果使用者 1 與使用者 2 對特定問題具有相同的意見，則使用者 1 對其他問題的想法較可能與使用者 2 相同。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-230">In this case, the `Matrix Factorization` algorithm uses a method called "collaborative filtering", which assumes that if User 1 has the same opinion as User 2 on a certain issue, then User 1 is more likely to feel the same way as User 2 about a different issue.</span></span>

<span data-ttu-id="c0fe6-231">比方說，如果使用者 1 對電影的評分與使用者 2 類似，則使用者 2 較可能享受使用者 1 已觀看並給予高度評分的電影：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-231">For instance, if User 1 and User 2 rate movies similarly, then User 2 is more likely to enjoy a movie that User 1 has watched and rated highly:</span></span>

| | `Incredibles 2 (2018)` | `The Avengers (2012)` | `Guardians of the Galaxy (2014)` |
| -------------:|-------------:| -----:|-----:|
| <span data-ttu-id="c0fe6-232">使用者 1</span><span class="sxs-lookup"><span data-stu-id="c0fe6-232">User 1</span></span> | <span data-ttu-id="c0fe6-233">已觀看及已按讚的電影</span><span class="sxs-lookup"><span data-stu-id="c0fe6-233">Watched and liked movie</span></span> | <span data-ttu-id="c0fe6-234">已觀看及已按讚的電影</span><span class="sxs-lookup"><span data-stu-id="c0fe6-234">Watched and liked movie</span></span> | <span data-ttu-id="c0fe6-235">已觀看及已按讚的電影</span><span class="sxs-lookup"><span data-stu-id="c0fe6-235">Watched and liked movie</span></span> |
| <span data-ttu-id="c0fe6-236">使用者 2</span><span class="sxs-lookup"><span data-stu-id="c0fe6-236">User 2</span></span> | <span data-ttu-id="c0fe6-237">已觀看及已按讚的電影</span><span class="sxs-lookup"><span data-stu-id="c0fe6-237">Watched and liked movie</span></span> | <span data-ttu-id="c0fe6-238">已觀看及已按讚的電影</span><span class="sxs-lookup"><span data-stu-id="c0fe6-238">Watched and liked movie</span></span> | <span data-ttu-id="c0fe6-239">尚未觀看 -- 推薦電影</span><span class="sxs-lookup"><span data-stu-id="c0fe6-239">Has not watched -- RECOMMEND movie</span></span> |

<span data-ttu-id="c0fe6-240">`Matrix Factorization` 定型器具有數個[選項](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options)，您可以在以下[演算法超參數](#algorithm-hyperparameters)一節中深入了解。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-240">The `Matrix Factorization` trainer has several [Options](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options), which you can read more about in the [Algorithm hyperparameters](#algorithm-hyperparameters) section below.</span></span>

<span data-ttu-id="c0fe6-241">將下列內容新增為 `BuildAndTrainModel()` 方法中的下一行程式碼，調整模型為合適於 `Train` 資料並傳回已定型模型：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-241">Fit the model to the `Train` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[FitModel](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#FitModel "Call the Fit method and return back the trained model")]

<span data-ttu-id="c0fe6-242">[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) 方法會以所提供的定型資料集來定型模型。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-242">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model with the provided training dataset.</span></span> <span data-ttu-id="c0fe6-243">技術上來說，其會轉換資料並套用定型來執行 `Estimator` 定義，並傳回已定型模型，也就是 `Transformer`。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-243">Technically, it executes the `Estimator` definitions by transforming the data and applying the training, and it returns back the trained model, which is a `Transformer`.</span></span>

<span data-ttu-id="c0fe6-244">將下列內容新增為 `Main()` 方法中的下一行程式碼以呼叫 `BuildAndTrainModel()` 方法，並傳回已定型模型：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-244">Add the following as the next line of code in the `Main()` method to call your `BuildAndTrainModel()` method and return the trained model:</span></span>

[!code-csharp[BuildTrainModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#BuildTrainModelMain "Add BuildAndTrainModel method in Main")]

## <a name="evaluate-your-model"></a><span data-ttu-id="c0fe6-245">評估您的模型</span><span class="sxs-lookup"><span data-stu-id="c0fe6-245">Evaluate your model</span></span>

<span data-ttu-id="c0fe6-246">一旦您將模型定型後，即可將測試資料用於評估模型的執行情況。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-246">Once you have trained your model, use your test data to evaluate how your model is performing.</span></span>

<span data-ttu-id="c0fe6-247">請使用下列程式碼，在緊接著 `BuildAndTrainModel()` 方法之後，建立 `EvaluateModel()` 方法：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-247">Create the `EvaluateModel()` method, just after the `BuildAndTrainModel()` method, using the following code:</span></span>

```csharp
public static void EvaluateModel(MLContext mlContext, IDataView testDataView, ITransformer model)
{

}
```

<span data-ttu-id="c0fe6-248">將下列程式碼新增至 `EvaluateModel()` 以轉換 `Test` 資料：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-248">Transform the `Test` data by adding the following code to `EvaluateModel()`:</span></span>

[!code-csharp[Transform](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Transform "Transform the test data")]

<span data-ttu-id="c0fe6-249">[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) 方法會對測試資料集之多個提供的輸入資料列進行預測。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-249">The [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method makes predictions for multiple provided input rows of a test dataset.</span></span>

<span data-ttu-id="c0fe6-250">將下列內容新增為 `EvaluateModel()` 方法中的下一行程式碼來評估模型：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-250">Evaluate the model by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[Evaluate](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#Evaluate "Evaluate the model using predictions from the test data")]

<span data-ttu-id="c0fe6-251">在您設定好預測後，[Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) 方法會評估模型，將預測值與測試資料集中的實際 `Labels` 進行比較，並傳回模型的執行情況。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-251">Once you have the prediction set, the [Evaluate()](xref:Microsoft.ML.RecommendationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns metrics on how the model is performing.</span></span>

<span data-ttu-id="c0fe6-252">將下列內容新增為 `EvaluateModel()` 方法中的下一行程式碼，將您的評估計量列印到主控台：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-252">Print your evaluation metrics to the console by adding the following as the next line of code in the `EvaluateModel()` method:</span></span>

[!code-csharp[PrintMetrics](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintMetrics "Print the evaluation metrics")]

<span data-ttu-id="c0fe6-253">將下列內容新增為 `Main()` 方法中的下一行程式碼，來呼叫您的 `EvaluateModel()` 方法：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-253">Add the following as the next line of code in the `Main()` method to call your `EvaluateModel()` method:</span></span>

[!code-csharp[EvaluateModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#EvaluateModelMain "Add EvaluateModel method in Main")]

<span data-ttu-id="c0fe6-254">到目前為止，輸出看起來應類似下列文字：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-254">The output so far should look similar to the following text:</span></span>

```console
=============== Training the model ===============
iter      tr_rmse          obj
   0       1.5403   3.1262e+05
   1       0.9221   1.6030e+05
   2       0.8687   1.5046e+05
   3       0.8416   1.4584e+05
   4       0.8142   1.4209e+05
   5       0.7849   1.3907e+05
   6       0.7544   1.3594e+05
   7       0.7266   1.3361e+05
   8       0.6987   1.3110e+05
   9       0.6751   1.2948e+05
  10       0.6530   1.2766e+05
  11       0.6350   1.2644e+05
  12       0.6197   1.2541e+05
  13       0.6067   1.2470e+05
  14       0.5953   1.2382e+05
  15       0.5871   1.2342e+05
  16       0.5781   1.2279e+05
  17       0.5713   1.2240e+05
  18       0.5660   1.2230e+05
  19       0.5592   1.2179e+05
=============== Evaluating the model ===============
Rms: 0.994051469730769
RSquared: 0.412556298844873
```

<span data-ttu-id="c0fe6-255">在此輸出中，有 20 個反覆項目。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-255">In this output, there are 20 iterations.</span></span> <span data-ttu-id="c0fe6-256">在每個反覆項目中，錯誤的量值會減少並逐漸接近 0。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-256">In each iteration, the measure of error decreases and converges closer and closer to 0.</span></span>

<span data-ttu-id="c0fe6-257">`root of mean squared error` (RMS 或 RMSE) 被用來測量模型預測值與測試資料集觀察值之間的差異。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-257">The `root of mean squared error` (RMS or RMSE) is used to measure the differences between the model predicted values and the test dataset observed values.</span></span> <span data-ttu-id="c0fe6-258">技術上來說，其為誤差平方之平均值的平方根。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-258">Technically it's the square root of the average of the squares of the errors.</span></span> <span data-ttu-id="c0fe6-259">此計量值越低，模型就越好。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-259">The lower it is, the better the model is.</span></span>

<span data-ttu-id="c0fe6-260">`R Squared` 表示資料符合模型的程度。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-260">`R Squared` indicates how well data fits a model.</span></span> <span data-ttu-id="c0fe6-261">範圍為 0 到 1。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-261">Ranges from 0 to 1.</span></span> <span data-ttu-id="c0fe6-262">值為 0 時，表示資料是隨機的，也就是與模型不相符。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-262">A value of 0 means that the data is random or otherwise can't be fit to the model.</span></span> <span data-ttu-id="c0fe6-263">值為 1 時，表示模型與資料完全相符。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-263">A value of 1 means that the model exactly matches the data.</span></span> <span data-ttu-id="c0fe6-264">`R Squared` 分數愈接近 1 愈好。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-264">You want your `R Squared` score to be as close to 1 as possible.</span></span>

<span data-ttu-id="c0fe6-265">建立成功的模型是一個需要反覆嘗試的程序。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-265">Building successful models is an iterative process.</span></span> <span data-ttu-id="c0fe6-266">此模型一開始的品質較低，因為此教學課程是使用小型的資料集來提供快速的模型定型。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-266">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="c0fe6-267">如果您對於模型的品質感到不滿意，可以嘗試為它提供較大的定型資料集，或選擇不同的定型演算法，並針對每個演算法搭配不同的超參數來改善它。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-267">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different hyper-parameters for each algorithm.</span></span> <span data-ttu-id="c0fe6-268">如需詳細資訊，請參閱下面的[改善您的模型](#improve-your-model)一節。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-268">For more information, check out the [Improve your model](#improve-your-model) section below.</span></span>

## <a name="use-your-model"></a><span data-ttu-id="c0fe6-269">使用您的模型</span><span class="sxs-lookup"><span data-stu-id="c0fe6-269">Use your model</span></span>

<span data-ttu-id="c0fe6-270">現在您可以使用您的已定型模型對新資料進行預測。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-270">Now you can use your trained model to make predictions on new data.</span></span>

<span data-ttu-id="c0fe6-271">請使用下列程式碼，在緊接著 `EvaluateModel()` 方法之後，建立 `UseModelForSinglePrediction()` 方法：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-271">Create the `UseModelForSinglePrediction()` method, just after the `EvaluateModel()` method, using the following code:</span></span>

```csharp
public static void UseModelForSinglePrediction(MLContext mlContext, ITransformer model)
{

}
```

<span data-ttu-id="c0fe6-272">將下列程式碼新增至 `UseModelForSinglePrediction()`，使用 `PredictionEngine` 來預測評等：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-272">Use the `PredictionEngine` to predict the rating by adding the following code to `UseModelForSinglePrediction()`:</span></span>

[!code-csharp[PredictionEngine](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PredictionEngine "Create Prediction Engine")]

<span data-ttu-id="c0fe6-273">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602)是一個方便的 API，可讓您在單一資料實例上執行預測。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-273">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="c0fe6-274">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) 不是安全執行緒。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-274">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="c0fe6-275">可接受在單一執行緒或原型環境中使用。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-275">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="c0fe6-276">為了改善生產環境中的效能和執行緒安全，請使用 `PredictionEnginePool` 服務，這會建立[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)物件的[@no__t 2](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) ，以供整個應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-276">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="c0fe6-277">請參閱本指南，以瞭解如何[在 ASP.NET Core WEB API 中使用 `PredictionEnginePool`](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application)</span><span class="sxs-lookup"><span data-stu-id="c0fe6-277">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](https://docs.microsoft.com/en-us/dotnet/machine-learning/how-to-guides/serve-model-web-api-ml-net#register-predictionenginepool-for-use-in-the-application)</span></span>

> [!NOTE]
> <span data-ttu-id="c0fe6-278">`PredictionEnginePool` 服務延伸模組目前處於預覽狀態。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-278">`PredictionEnginePool` service extension is currently in preview.</span></span>

<span data-ttu-id="c0fe6-279">建立稱為 `testInput` 的 `MovieRating` 執行個體，並將下列內容新增為 `UseModelForSinglePrediction()` 方法中的後續程式碼來將其傳遞至預測引擎：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-279">Create an instance of `MovieRating` called `testInput` and pass it to the Prediction Engine by adding the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[MakeSinglePrediction](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#MakeSinglePrediction "Make a single prediction with the Prediction Engine")]

<span data-ttu-id="c0fe6-280">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) 函式會在資料的單一資料行進行預測。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-280">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single column of data.</span></span>

<span data-ttu-id="c0fe6-281">您可以接著使用 `Score` 或預測的評等，來判斷您是否想要將電影 movieId 10 推薦給使用者 6。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-281">You can then use the `Score`, or the predicted rating, to determine whether you want to recommend the movie with movieId 10 to user 6.</span></span> <span data-ttu-id="c0fe6-282">`Score` 愈高，使用者喜好特定電影的可能性愈高。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-282">The higher the `Score`, the higher the likelihood of a user liking a particular movie.</span></span> <span data-ttu-id="c0fe6-283">在此案例中，假設您推薦預測評等 > 3.5 的電影。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-283">In this case, let’s say that you recommend movies with a predicted rating of > 3.5.</span></span>

<span data-ttu-id="c0fe6-284">若要列印結果，請將下列內容新增為 `UseModelForSinglePrediction()` 方法中的後續程式碼：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-284">To print the results, add the following as the next lines of code in the `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[PrintResults](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#PrintResults "Print the recommendation prediction results")]

<span data-ttu-id="c0fe6-285">將下列內容新增為 `Main()` 方法中的下一行程式碼，來呼叫您的 `UseModelForSinglePrediction()` 方法：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-285">Add the following as the next line of code in the `Main()` method to call your `UseModelForSinglePrediction()` method:</span></span>

[!code-csharp[UseModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#UseModelMain "Add UseModelForSinglePrediction method in Main")]

<span data-ttu-id="c0fe6-286">此方法的輸出看起來應類似下列文字：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-286">The output of this method should look similar to the following text:</span></span>

```console
=============== Making a prediction ===============
Movie 10 is recommended for user 6
```

### <a name="save-your-model"></a><span data-ttu-id="c0fe6-287">儲存您的模型</span><span class="sxs-lookup"><span data-stu-id="c0fe6-287">Save your model</span></span>

<span data-ttu-id="c0fe6-288">若要使用您的模型在終端使用者應用程式中進行預測，您必須先儲存模型。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-288">To use your model to make predictions in end-user applications, you must first save the model.</span></span>

<span data-ttu-id="c0fe6-289">請使用下列程式碼，在緊接著 `UseModelForSinglePrediction()` 方法之後，建立 `SaveModel()` 方法：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-289">Create the `SaveModel()` method, just after the `UseModelForSinglePrediction()` method, using the following code:</span></span>

```csharp
public static void SaveModel(MLContext mlContext, DataViewSchema trainingDataViewSchema, ITransformer model)
{

}
```

<span data-ttu-id="c0fe6-290">在 `SaveModel()` 方法中新增下列程式碼來儲存您的已定型模型：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-290">Save your trained model by adding the following code in the `SaveModel()` method:</span></span>

[!code-csharp[SaveModel](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModel "Save the model to a zip file")]

<span data-ttu-id="c0fe6-291">此方法會將已定型模型儲存至 .zip 檔案 (在 "Data" 資料夾中)，其之後可用於其他 .NET 應用程式中來進行預測。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-291">This method saves your trained model to a .zip file (in the "Data" folder), which can then be used in other .NET applications to make predictions.</span></span>

<span data-ttu-id="c0fe6-292">將下列內容新增為 `Main()` 方法中的下一行程式碼，來呼叫您的 `SaveModel()` 方法：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-292">Add the following as the next line of code in the `Main()` method to call your `SaveModel()` method:</span></span>

[!code-csharp[SaveModelMain](~/samples/machine-learning/tutorials/MovieRecommendation/Program.cs#SaveModelMain "Create SaveModel method in Main")]

### <a name="use-your-saved-model"></a><span data-ttu-id="c0fe6-293">使用您已儲存的模型</span><span class="sxs-lookup"><span data-stu-id="c0fe6-293">Use your saved model</span></span>

<span data-ttu-id="c0fe6-294">一旦您儲存已定型模型，您即可以在不同的環境中取用模型 (請參閱[《使用說明指南》](../how-to-guides/consuming-model-ml-net.md)以了解如何在應用程式中讓已定型的機器學習模型能夠運作)。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-294">Once you have saved your trained model, you can consume the model in different environments (see the ["How-to guide"](../how-to-guides/consuming-model-ml-net.md) to learn how to operationalize a trained machine learning model in apps).</span></span>

## <a name="results"></a><span data-ttu-id="c0fe6-295">結果</span><span class="sxs-lookup"><span data-stu-id="c0fe6-295">Results</span></span>

<span data-ttu-id="c0fe6-296">完成上述步驟後，請執行主控台應用程式 (Ctrl + F5)。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-296">After following the steps above, run your console app (Ctrl + F5).</span></span> <span data-ttu-id="c0fe6-297">上述單一預測的結果應該如下所示。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-297">Your results from the single prediction above should be similar to the following.</span></span> <span data-ttu-id="c0fe6-298">您可能會看到警告或處理中訊息，但為了讓結果變得清楚，這些訊息已從下列結果中移除。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-298">You may see warnings or processing messages, but these messages have been removed from the following results for clarity.</span></span>

```console
=============== Training the model ===============
iter      tr_rmse          obj
   0       1.5382   3.1213e+05
   1       0.9223   1.6051e+05
   2       0.8691   1.5050e+05
   3       0.8413   1.4576e+05
   4       0.8145   1.4208e+05
   5       0.7848   1.3895e+05
   6       0.7552   1.3613e+05
   7       0.7259   1.3357e+05
   8       0.6987   1.3121e+05
   9       0.6747   1.2949e+05
  10       0.6533   1.2766e+05
  11       0.6353   1.2636e+05
  12       0.6209   1.2561e+05
  13       0.6072   1.2462e+05
  14       0.5965   1.2394e+05
  15       0.5868   1.2352e+05
  16       0.5782   1.2279e+05
  17       0.5713   1.2227e+05
  18       0.5637   1.2190e+05
  19       0.5604   1.2178e+05
=============== Evaluating the model ===============
Rms: 0.977175077487166
RSquared: 0.43233349213192
=============== Making a prediction ===============
Movie 10 is recommended for user 6
=============== Saving the model to a file ===============
```

<span data-ttu-id="c0fe6-299">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="c0fe6-299">Congratulations!</span></span> <span data-ttu-id="c0fe6-300">您現在已成功建置推薦電影的機器學習服務模型。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-300">You've now successfully built a machine learning model for recommending movies.</span></span> <span data-ttu-id="c0fe6-301">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-301">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/MovieRecommendation) repository.</span></span>

## <a name="improve-your-model"></a><span data-ttu-id="c0fe6-302">改善您的模型</span><span class="sxs-lookup"><span data-stu-id="c0fe6-302">Improve your model</span></span>

<span data-ttu-id="c0fe6-303">有幾種方式可讓您改善模型的效能，以便您進行更精確的預測。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-303">There are several ways that you can improve the performance of your model so that you can get more accurate predictions.</span></span>

### <a name="data"></a><span data-ttu-id="c0fe6-304">Data</span><span class="sxs-lookup"><span data-stu-id="c0fe6-304">Data</span></span>

<span data-ttu-id="c0fe6-305">為每位使用者和影片識別碼新增更多具有足夠樣本的已定型資料，有助於改善推薦模型的品質。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-305">Adding more training data that has enough samples for each user and movie id can help improve the quality of the recommendation model.</span></span>

<span data-ttu-id="c0fe6-306">[交叉驗證](../how-to-guides/train-cross-validation-ml-net.md)是一種評估模型技術，會將資料隨機分割成子集 (而不是像本教學課程從資料集擷取出測試資料)，並採用部分群組作為定型資料，以及部分群組作為測試資料。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-306">[Cross validation](../how-to-guides/train-cross-validation-ml-net.md) is a technique for evaluating models that randomly splits up data into subsets (instead of extracting out test data from the dataset like you did in this tutorial) and takes some of the groups as train data and some of the groups as test data.</span></span> <span data-ttu-id="c0fe6-307">此方法在模型品質方面的表現優於定型/測試分割。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-307">This method outperforms making a train-test split in terms of model quality.</span></span>

### <a name="features"></a><span data-ttu-id="c0fe6-308">功能</span><span class="sxs-lookup"><span data-stu-id="c0fe6-308">Features</span></span>

<span data-ttu-id="c0fe6-309">在本教學課程中，您只會使用資料集所提供的三個 `Features` (`user id`、`movie id` 和 `rating`)。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-309">In this tutorial, you only use the three `Features` (`user id`, `movie id`, and `rating`) that are provided by the dataset.</span></span>

<span data-ttu-id="c0fe6-310">雖然這是不錯的起點，但在實際操作時，建議您新增其他屬性或 `Features` (例如年齡、性別、地理位置等)，如果這些也包含在資料集內。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-310">While this is a good start, in reality you might want to add other attributes or `Features` (for example, age, gender, geo-location, etc.) if they are included in the dataset.</span></span> <span data-ttu-id="c0fe6-311">新增更多相關 `Features` 有助於改善推薦模型的效能。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-311">Adding more relevant `Features` can help improve the performance of your recommendation model.</span></span>

<span data-ttu-id="c0fe6-312">如果您不確定哪些 `Features` 可能與您的機器學習工作最相關，您也可以利用功能比重計算 (FCC) 和[功能排列重要性](../how-to-guides/determine-global-feature-importance-in-model.md)，讓 ML.NET 探索最具影響力的 `Features`。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-312">If you are unsure about which `Features` might be the most relevant for your machine learning task, you can also make use of Feature Contribution Calculation (FCC) and [Feature Permutation Importance](../how-to-guides/determine-global-feature-importance-in-model.md), which ML.NET provides to discover the most influential `Features`.</span></span>

### <a name="algorithm-hyperparameters"></a><span data-ttu-id="c0fe6-313">演算法超參數</span><span class="sxs-lookup"><span data-stu-id="c0fe6-313">Algorithm hyperparameters</span></span>

<span data-ttu-id="c0fe6-314">雖然 ML.NET 提供最佳的預設定型演算法，但您也可以變更演算法的[超參數](../resources/glossary.md#hyperparameter)來進一步微調效能。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-314">While ML.NET provides good default training algorithms, you can further fine-tune performance by changing the algorithm's [hyperparameters](../resources/glossary.md#hyperparameter).</span></span>

<span data-ttu-id="c0fe6-315">針對 `Matrix Factorization`，您可以使用 [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) 和 [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) 等超參數，查看其是否可提供您更好的結果。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-315">For `Matrix Factorization`, you can experiment with hyperparameters such as [NumberOfIterations](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.NumberOfIterations) and [ApproximationRank](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Options.ApproximationRank) to see if that gives you better results.</span></span>

<span data-ttu-id="c0fe6-316">例如，本教學課程中的演算法選項如下：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-316">For instance, in this tutorial the algorithm options are:</span></span>

```csharp
var options = new MatrixFactorizationTrainer.Options
{
    MatrixColumnIndexColumnName = "userIdEncoded",
    MatrixRowIndexColumnName = "movieIdEncoded",
    LabelColumnName = "Label",
    NumberOfIterations = 20,
    ApproximationRank = 100
};
```

### <a name="other-recommendation-algorithms"></a><span data-ttu-id="c0fe6-317">其他建議演算法</span><span class="sxs-lookup"><span data-stu-id="c0fe6-317">Other Recommendation Algorithms</span></span>

<span data-ttu-id="c0fe6-318">具備共同篩選的矩陣分解演算法，僅為執行電影推薦的其中一種方法。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-318">The matrix factorization algorithm with collaborative filtering is only one approach for performing movie recommendations.</span></span> <span data-ttu-id="c0fe6-319">在許多情況下，您可能會沒有可用的評等資料，並只有使用者的電影觀看記錄。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-319">In many cases, you may not have the ratings data available and only have movie history available from users.</span></span> <span data-ttu-id="c0fe6-320">而在其他情況下，您擁有的資料可能不只是使用者評等資料。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-320">In other cases, you may have more than just the user’s rating data.</span></span>

| <span data-ttu-id="c0fe6-321">演算法</span><span class="sxs-lookup"><span data-stu-id="c0fe6-321">Algorithm</span></span>       | <span data-ttu-id="c0fe6-322">狀況</span><span class="sxs-lookup"><span data-stu-id="c0fe6-322">Scenario</span></span>           | <span data-ttu-id="c0fe6-323">範例</span><span class="sxs-lookup"><span data-stu-id="c0fe6-323">Sample</span></span>  |
| ------------- |:-------------:| -----:|
| <span data-ttu-id="c0fe6-324">單一類別矩陣分解</span><span class="sxs-lookup"><span data-stu-id="c0fe6-324">One Class Matrix Factorization</span></span> | <span data-ttu-id="c0fe6-325">當您只需要 userId 和 movieId 時，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-325">Use this when you only have userId and movieId.</span></span> <span data-ttu-id="c0fe6-326">此推薦類型乃根據共同採購案例或經常同時購買的產品，也就是會根據客戶自己的採購訂單記錄向客戶推薦一組產品。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-326">This style of recommendation is based upon the co-purchase scenario, or products frequently bought together, which means it will recommend to customers a set of products based upon their own purchase order history.</span></span> | [<span data-ttu-id="c0fe6-327">> 現在就試試看</span><span class="sxs-lookup"><span data-stu-id="c0fe6-327">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/MatrixFactorization_ProductRecommendation) |
| <span data-ttu-id="c0fe6-328">欄位感知分解機器</span><span class="sxs-lookup"><span data-stu-id="c0fe6-328">Field Aware Factorization Machines</span></span> | <span data-ttu-id="c0fe6-329">當您所擁有的功能多於 userId、productId 和評等 (如產品描述或產品價格) 時，請使用此選項來進行推薦。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-329">Use this to make recommendations when you have more Features beyond userId, productId, and rating (such as product description or product price).</span></span> <span data-ttu-id="c0fe6-330">此方法也會使用共同作業篩選方法。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-330">This method also uses a collaborative filtering approach.</span></span> | [<span data-ttu-id="c0fe6-331">> 現在就試試看</span><span class="sxs-lookup"><span data-stu-id="c0fe6-331">>Try it out</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/Recommendation-MovieRecommender) |

### <a name="new-user-scenario"></a><span data-ttu-id="c0fe6-332">新使用者案例</span><span class="sxs-lookup"><span data-stu-id="c0fe6-332">New user scenario</span></span>

<span data-ttu-id="c0fe6-333">共同篩選的一個常見問題是冷啟動問題，也就是當您有一個不具有先前資料的新使用者，以至於無法進行推斷時。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-333">One common problem in collaborative filtering is the cold start problem, which is when you have a new user with no previous data to draw inferences from.</span></span> <span data-ttu-id="c0fe6-334">此問題的解決方法通常是要求新使用者建立設定檔，並對他們先前看過的電影評分 (舉例來說)。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-334">This problem is often solved by asking new users to create a profile and, for instance, rate movies they have seen in the past.</span></span> <span data-ttu-id="c0fe6-335">雖然此方法會對使用者造成一些負擔，但可以為沒有評等記錄的新使用者提供一些起始資料。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-335">While this method puts some burden on the user, it provides some starting data for new users with no rating history.</span></span>

## <a name="resources"></a><span data-ttu-id="c0fe6-336">資源</span><span class="sxs-lookup"><span data-stu-id="c0fe6-336">Resources</span></span>

<span data-ttu-id="c0fe6-337">本教學課程中使用的資料衍生自 [MovieLens 資料集](http://files.grouplens.org/datasets/movielens/)。</span><span class="sxs-lookup"><span data-stu-id="c0fe6-337">The data used in this tutorial is derived from [MovieLens Dataset](http://files.grouplens.org/datasets/movielens/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="c0fe6-338">後續步驟</span><span class="sxs-lookup"><span data-stu-id="c0fe6-338">Next steps</span></span>

<span data-ttu-id="c0fe6-339">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="c0fe6-339">In this tutorial, you learned how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="c0fe6-340">選取機器學習演算法</span><span class="sxs-lookup"><span data-stu-id="c0fe6-340">Select a machine learning algorithm</span></span>
> * <span data-ttu-id="c0fe6-341">準備及載入您的資料</span><span class="sxs-lookup"><span data-stu-id="c0fe6-341">Prepare and load your data</span></span>
> * <span data-ttu-id="c0fe6-342">建置及定型模型</span><span class="sxs-lookup"><span data-stu-id="c0fe6-342">Build and train a model</span></span>
> * <span data-ttu-id="c0fe6-343">評估模型</span><span class="sxs-lookup"><span data-stu-id="c0fe6-343">Evaluate a model</span></span>
> * <span data-ttu-id="c0fe6-344">部署及取用模型</span><span class="sxs-lookup"><span data-stu-id="c0fe6-344">Deploy and consume a model</span></span>

<span data-ttu-id="c0fe6-345">前進到下一個教學課程來深入了解</span><span class="sxs-lookup"><span data-stu-id="c0fe6-345">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="c0fe6-346">情感分析</span><span class="sxs-lookup"><span data-stu-id="c0fe6-346">Sentiment Analysis</span></span>](sentiment-analysis.md)
