---
title: 教學課程：分析網站評論 - 二元分類
description: 本教學課程示範如何建立 .NET Core 主控台應用程式，來分類網站評論中的情感並採取適當動作。 二元情感分類器在 Visual Studio 中使用 C#。
ms.date: 05/13/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: e145e65e22c955bd547b67de545b883fb0fb3bc2
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593411"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a><span data-ttu-id="dfade-104">教學課程：在 ML.NET 中使用二元分類來分析網站評論的情感</span><span class="sxs-lookup"><span data-stu-id="dfade-104">Tutorial: Analyze sentiment of website comments with binary classification in ML.NET</span></span>

<span data-ttu-id="dfade-105">本教學課程示範如何建立 .NET Core 主控台應用程式，來分類網站評論中的情感並採取適當動作。</span><span class="sxs-lookup"><span data-stu-id="dfade-105">This tutorial shows you how to create a .NET Core console application that classifies sentiment from website comments and takes the appropriate action.</span></span> <span data-ttu-id="dfade-106">二元情感分類器在 Visual Studio 2017 中使用 C#。</span><span class="sxs-lookup"><span data-stu-id="dfade-106">The binary sentiment classifier uses C# in Visual Studio 2017.</span></span>

<span data-ttu-id="dfade-107">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="dfade-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="dfade-108">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="dfade-108">Create a console application</span></span>
> * <span data-ttu-id="dfade-109">準備資料</span><span class="sxs-lookup"><span data-stu-id="dfade-109">Prepare data</span></span>
> * <span data-ttu-id="dfade-110">載入資料</span><span class="sxs-lookup"><span data-stu-id="dfade-110">Load the data</span></span>
> * <span data-ttu-id="dfade-111">建置和定型模型</span><span class="sxs-lookup"><span data-stu-id="dfade-111">Build and train the model</span></span>
> * <span data-ttu-id="dfade-112">評估模型</span><span class="sxs-lookup"><span data-stu-id="dfade-112">Evaluate the model</span></span>
> * <span data-ttu-id="dfade-113">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="dfade-113">Use the model to make a prediction</span></span>
> * <span data-ttu-id="dfade-114">查看結果</span><span class="sxs-lookup"><span data-stu-id="dfade-114">See the results</span></span>

<span data-ttu-id="dfade-115">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="dfade-115">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dfade-116">必要條件</span><span class="sxs-lookup"><span data-stu-id="dfade-116">Prerequisites</span></span>

* <span data-ttu-id="dfade-117">已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 15.6 或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)</span><span class="sxs-lookup"><span data-stu-id="dfade-117">[Visual Studio 2017 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed</span></span>

* <span data-ttu-id="dfade-118">[UCI 情感標記句子資料集](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP 檔案)</span><span class="sxs-lookup"><span data-stu-id="dfade-118">[UCI Sentiment Labeled Sentences dataset](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP file)</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="dfade-119">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="dfade-119">Create a console application</span></span>

1. <span data-ttu-id="dfade-120">建立稱為 "SentimentAnalysis" 的 **.NET Core 主控台應用程式**。</span><span class="sxs-lookup"><span data-stu-id="dfade-120">Create a **.NET Core Console Application** called "SentimentAnalysis".</span></span>

2. <span data-ttu-id="dfade-121">在專案中建立一個名為 *Data* 的目錄以儲存資料集檔案。</span><span class="sxs-lookup"><span data-stu-id="dfade-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="dfade-122">安裝「Microsoft.ML NuGet 套件」：</span><span class="sxs-lookup"><span data-stu-id="dfade-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="dfade-123">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]。</span><span class="sxs-lookup"><span data-stu-id="dfade-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="dfade-124">選擇 "nuget.org" 作為套件來源，然後選取 [瀏覽] 索引標籤。搜尋 **Microsoft.ML**，選取您想要的套件，然後選取 [安裝] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="dfade-124">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="dfade-125">同意您所選套件的授權條款，以繼續進行安裝。</span><span class="sxs-lookup"><span data-stu-id="dfade-125">Proceed with the installation by agreeing to the the license terms for the package you choose.</span></span> <span data-ttu-id="dfade-126">對 **Microsoft.ML.FastTree** NuGet 套件執行相同的動作。</span><span class="sxs-lookup"><span data-stu-id="dfade-126">Do the same for the **Microsoft.ML.FastTree** NuGet package.</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="dfade-127">準備您的資料</span><span class="sxs-lookup"><span data-stu-id="dfade-127">Prepare your data</span></span>

> [!NOTE]
> <span data-ttu-id="dfade-128">此教學課程的資料集是來自 'From Group to Individual Labels using Deep Features' (從群組到使用深度特徵的個別標籤) (Kotzias 等人</span><span class="sxs-lookup"><span data-stu-id="dfade-128">The datasets for this tutorial are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="dfade-129">al，</span><span class="sxs-lookup"><span data-stu-id="dfade-129">al,.</span></span> <span data-ttu-id="dfade-130">KDD 2015)，而且裝載於「UCI Machine Learning Repository (UCI 機器學習存放庫)」- Dua, D. and Karra Taniskidou, E.(2017)。</span><span class="sxs-lookup"><span data-stu-id="dfade-130">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="dfade-131">「UCI Machine Learning Repository (UCI 機器學習存放庫)」[http://archive.ics.uci.edu/ml]。</span><span class="sxs-lookup"><span data-stu-id="dfade-131">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="dfade-132">爾灣，加利福尼亞州：加州大學，資訊與電腦科學學院。</span><span class="sxs-lookup"><span data-stu-id="dfade-132">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

1. <span data-ttu-id="dfade-133">下載並解壓縮 [UCI 情感標記句子資料集 ZIP 檔案](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)。</span><span class="sxs-lookup"><span data-stu-id="dfade-133">Download [UCI Sentiment Labeled Sentences dataset ZIP file](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="dfade-134">將 `yelp_labelled.txt` 檔案複製到您所建立的 *Data* 目錄。</span><span class="sxs-lookup"><span data-stu-id="dfade-134">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

3. <span data-ttu-id="dfade-135">在 [方案總管] 中，以滑鼠右鍵按一下 `yelp_labeled.txt` 檔案，並選取 [內容]。</span><span class="sxs-lookup"><span data-stu-id="dfade-135">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="dfade-136">在 [進階] 底下，將 [複製到輸出目錄] 的值變更為 [有更新時才複製]。</span><span class="sxs-lookup"><span data-stu-id="dfade-136">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="dfade-137">建立類別及定義路徑</span><span class="sxs-lookup"><span data-stu-id="dfade-137">Create classes and define paths</span></span>

1. <span data-ttu-id="dfade-138">在 *Program.cs* 檔案頂端新增下列額外的 `using` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="dfade-138">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddUsings "Add necessary usings")]

2. <span data-ttu-id="dfade-139">建立兩個全域欄位，以保存最近所下載資料集檔案路徑與儲存的模型檔案路徑：</span><span class="sxs-lookup"><span data-stu-id="dfade-139">Create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

    * <span data-ttu-id="dfade-140">`_dataPath` 包含用來將模型定型的資料集路徑。</span><span class="sxs-lookup"><span data-stu-id="dfade-140">`_dataPath` has the path to the dataset used to train the model.</span></span>
    * <span data-ttu-id="dfade-141">`_modelPath` 包含用來儲存定型模型的路徑。</span><span class="sxs-lookup"><span data-stu-id="dfade-141">`_modelPath` has the path where the trained model is saved.</span></span>

3. <span data-ttu-id="dfade-142">將下列程式碼新增至緊接在 `Main` 方法上方的一行，以指定路徑：</span><span class="sxs-lookup"><span data-stu-id="dfade-142">Add the following code to the line right above the `Main` method to specify the paths:</span></span>

    [!code-csharp[Declare global variables](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DeclareGlobalVariables "Declare global variables")]

4. <span data-ttu-id="dfade-143">接下來，為輸入資料和預測建立類別。</span><span class="sxs-lookup"><span data-stu-id="dfade-143">Next, create classes for your input data and predictions.</span></span> <span data-ttu-id="dfade-144">將新類別新增至專案：</span><span class="sxs-lookup"><span data-stu-id="dfade-144">Add a new class to your project:</span></span>

    - <span data-ttu-id="dfade-145">在 [方案總管] 中，於專案上按一下滑鼠右鍵，然後選取 [新增] > [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="dfade-145">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

    - <span data-ttu-id="dfade-146">在 [新增項目] 對話方塊中，選取 [類別]，然後將 [名稱] 欄位變更為 *SentimentData.cs*。</span><span class="sxs-lookup"><span data-stu-id="dfade-146">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="dfade-147">接著，選取 [新增] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="dfade-147">Then, select the **Add** button.</span></span>

5. <span data-ttu-id="dfade-148">*SentimentData.cs* 檔案隨即在程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="dfade-148">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="dfade-149">將以下 `using` 陳述式新增至 *SentimentData.cs* 頂端：</span><span class="sxs-lookup"><span data-stu-id="dfade-149">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp[AddUsings](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#AddUsings "Add necessary usings")]

6. <span data-ttu-id="dfade-150">移除現有的類別定義，然後將下列程式碼 (具有 `SentimentData` 和 `SentimentPrediction` 這兩個類別) 新增至 *SentimentData.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="dfade-150">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](~/samples/machine-learning/tutorials/SentimentAnalysis/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a><span data-ttu-id="dfade-151">如何準備資料</span><span class="sxs-lookup"><span data-stu-id="dfade-151">How the data was prepared</span></span>
<span data-ttu-id="dfade-152">輸入資料集類別 `SentimentData` 具有使用者評論 (`SentimentText`) 的 `string`，以及代表情感的 `bool` (`Sentiment`) 值 1 (正面) 或 0 (負面)。</span><span class="sxs-lookup"><span data-stu-id="dfade-152">The input dataset class, `SentimentData`, has a `string` for user comments (`SentimentText`) and a `bool` (`Sentiment`) value of either 1 (positive) or 0 (negative) for sentiment.</span></span> <span data-ttu-id="dfade-153">這兩個欄位都有 [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) 附加屬性，其描述每個欄位的資料檔案順序。</span><span class="sxs-lookup"><span data-stu-id="dfade-153">Both fields have [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attributes attached to them, which describes the data file order of each field.</span></span>  <span data-ttu-id="dfade-154">此外，`Sentiment` 屬性具有 [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) 屬性來將它指定為 `Label` 欄位。</span><span class="sxs-lookup"><span data-stu-id="dfade-154">In addition, the `Sentiment` property has a [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) attribute to designate it as the `Label` field.</span></span> <span data-ttu-id="dfade-155">下列範例檔案沒有標頭資料列，且看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="dfade-155">The following example file doesn't have a header row, and looks like this:</span></span>

|<span data-ttu-id="dfade-156">SentimentText</span><span class="sxs-lookup"><span data-stu-id="dfade-156">SentimentText</span></span>                         |<span data-ttu-id="dfade-157">情感 (標籤)</span><span class="sxs-lookup"><span data-stu-id="dfade-157">Sentiment (Label)</span></span> |
|--------------------------------------|----------|
|<span data-ttu-id="dfade-158">女服務生的服務速度有點慢。</span><span class="sxs-lookup"><span data-stu-id="dfade-158">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="dfade-159">0</span><span class="sxs-lookup"><span data-stu-id="dfade-159">0</span></span>     |
|<span data-ttu-id="dfade-160">不夠酥脆。</span><span class="sxs-lookup"><span data-stu-id="dfade-160">Crust is not good.</span></span>                    |    <span data-ttu-id="dfade-161">0</span><span class="sxs-lookup"><span data-stu-id="dfade-161">0</span></span>     |
|<span data-ttu-id="dfade-162">哇...喜歡這個地方。</span><span class="sxs-lookup"><span data-stu-id="dfade-162">Wow... Loved this place.</span></span>              |    <span data-ttu-id="dfade-163">1</span><span class="sxs-lookup"><span data-stu-id="dfade-163">1</span></span>     |
|<span data-ttu-id="dfade-164">服務很迅速。</span><span class="sxs-lookup"><span data-stu-id="dfade-164">Service was very prompt.</span></span>              |    <span data-ttu-id="dfade-165">1</span><span class="sxs-lookup"><span data-stu-id="dfade-165">1</span></span>     |

<span data-ttu-id="dfade-166">`SentimentPrediction` 是在模型定型後所使用的預測類別。</span><span class="sxs-lookup"><span data-stu-id="dfade-166">`SentimentPrediction` is the prediction class used after the model training.</span></span> <span data-ttu-id="dfade-167">它繼承自 `SentimentData`，用於顯示 `SentimentText` 和預測。</span><span class="sxs-lookup"><span data-stu-id="dfade-167">It inherits from `SentimentData` for displaying the `SentimentText` with the predictions.</span></span> <span data-ttu-id="dfade-168">`SentimentPrediction` 包含一個單一布林值 (`Sentiment`) 和一個 `PredictedLabel` `ColumnName` 屬性。</span><span class="sxs-lookup"><span data-stu-id="dfade-168">`SentimentPrediction` has a single boolean (`Sentiment`) and a `PredictedLabel` `ColumnName` attribute.</span></span> <span data-ttu-id="dfade-169">`Label` 會用來建立和定型模型，也會用來搭配分割出來的測試資料集來評估模型。</span><span class="sxs-lookup"><span data-stu-id="dfade-169">The `Label` is used to create and train the model, and it's also used with the split out test dataset to evaluate the model.</span></span> <span data-ttu-id="dfade-170">`PredictedLabel` 的使用時機是在進行預測和評估的期間。</span><span class="sxs-lookup"><span data-stu-id="dfade-170">The `PredictedLabel` is used during prediction and evaluation.</span></span> <span data-ttu-id="dfade-171">就評估而言，會使用定型資料、預設值及模型。</span><span class="sxs-lookup"><span data-stu-id="dfade-171">For evaluation, training data, the predicted values, and the model are used.</span></span>

<span data-ttu-id="dfade-172">[MLContext 類別](xref:Microsoft.ML.MLContext)是所有 ML.NET 作業的起點。</span><span class="sxs-lookup"><span data-stu-id="dfade-172">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="dfade-173">將 `mlContext` 初始化會建立新的 ML.NET 環境，可在模型建立工作流程物件間共用。</span><span class="sxs-lookup"><span data-stu-id="dfade-173">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="dfade-174">就概念而言，類似於 Entity Framework 中的 `DBContext`。</span><span class="sxs-lookup"><span data-stu-id="dfade-174">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="dfade-175">載入資料</span><span class="sxs-lookup"><span data-stu-id="dfade-175">Load the data</span></span>
<span data-ttu-id="dfade-176">ML.NET 中的資料以 [IDataView 類別](xref:Microsoft.ML.IDataView) 表示。</span><span class="sxs-lookup"><span data-stu-id="dfade-176">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="dfade-177">`IDataView` 是彈性且有效率的表格式資料描述方式 (數值和文字)。</span><span class="sxs-lookup"><span data-stu-id="dfade-177">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="dfade-178">資料可以從文字或即時 (例如 SQL 資料庫或記錄檔) 載入至 `IDataView` 物件。</span><span class="sxs-lookup"><span data-stu-id="dfade-178">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="dfade-179">您可以準備資料，然後載入資料：</span><span class="sxs-lookup"><span data-stu-id="dfade-179">You prepare the app, and then load data:</span></span>

1. <span data-ttu-id="dfade-180">將 `Main` 方法中的 `Console.WriteLine("Hello World!")` 程式碼行取代為下列程式碼，以宣告 mlContext 變數並將它初始化：</span><span class="sxs-lookup"><span data-stu-id="dfade-180">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

    [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateMLContext "Create the ML Context")]

2. <span data-ttu-id="dfade-181">將下列程式碼加入為 `Main()` 方法中的下一行程式碼：</span><span class="sxs-lookup"><span data-stu-id="dfade-181">Add the following as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallLoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallLoadData)]

3. <span data-ttu-id="dfade-182">請使用下列程式碼，在緊接著 `Main()` 方法之後，建立 `LoadData()` 方法：</span><span class="sxs-lookup"><span data-stu-id="dfade-182">Create the `LoadData()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    <span data-ttu-id="dfade-183">`LoadData()` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="dfade-183">The `LoadData()` method executes the following tasks:</span></span>

    * <span data-ttu-id="dfade-184">載入資料。</span><span class="sxs-lookup"><span data-stu-id="dfade-184">Loads the data.</span></span>
    * <span data-ttu-id="dfade-185">將載入的資料集分割為定型與測試資料集。</span><span class="sxs-lookup"><span data-stu-id="dfade-185">Splits the loaded dataset into train and test datasets.</span></span>
    * <span data-ttu-id="dfade-186">傳回分割的定型與測試資料集。</span><span class="sxs-lookup"><span data-stu-id="dfade-186">Returns the split train and test datasets.</span></span>

4. <span data-ttu-id="dfade-187">將下列程式碼新增為 `LoadData()` 方法的第一行：</span><span class="sxs-lookup"><span data-stu-id="dfade-187">Add the following code as the first line of the `LoadData()` method:</span></span>

    [!code-csharp[LoadData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="dfade-188">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) 會定義資料結構描述並讀入檔案中。</span><span class="sxs-lookup"><span data-stu-id="dfade-188">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="dfade-189">會接受資料路徑變數然後傳回 `IDataView`。</span><span class="sxs-lookup"><span data-stu-id="dfade-189">It takes in the data path variables and returns an `IDataView`.</span></span>

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="dfade-190">分割資料集以進行模型定型與測試</span><span class="sxs-lookup"><span data-stu-id="dfade-190">Split the dataset for model training and testing</span></span>

<span data-ttu-id="dfade-191">準備模型時，您可以使用部分資料集來定型它，並使用部分資料集來測試模型的準確度。</span><span class="sxs-lookup"><span data-stu-id="dfade-191">When preparing a model, you use part of the dataset to train it and part of the dataset to test the model's accuracy.</span></span>

1. <span data-ttu-id="dfade-192">若要將載入的資料分割成所需的資料集，請將下列程式碼加入為 `LoadData()` 方法中的下一行：</span><span class="sxs-lookup"><span data-stu-id="dfade-192">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData()` method:</span></span>

    [!code-csharp[SplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#SplitData "Split the Data")]

    <span data-ttu-id="dfade-193">上述程式碼使用 [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) 方法將載入的資料集分割為定型與測試資料集，然後將它們包含在 [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) 類別中並傳回。</span><span class="sxs-lookup"><span data-stu-id="dfade-193">The previous code uses the [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the loaded dataset into train and test datasets and return them in the [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) class.</span></span> <span data-ttu-id="dfade-194">您可以使用 `testFraction` 參數來指定資料的測試集百分比。</span><span class="sxs-lookup"><span data-stu-id="dfade-194">Specify the test set percentage of data with the `testFraction`parameter.</span></span> <span data-ttu-id="dfade-195">預設值是 10%，但您在本例中會使用 20% 以評估更多資料。</span><span class="sxs-lookup"><span data-stu-id="dfade-195">The default is 10%, in this case you use 20% to evaluate more data.</span></span>

2. <span data-ttu-id="dfade-196">在 `LoadData()` 方法的結尾傳回 `splitDataView`：</span><span class="sxs-lookup"><span data-stu-id="dfade-196">Return the `splitDataView` at the end of the `LoadData()` method:</span></span>

    [!code-csharp[ReturnSplitData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="dfade-197">建置和定型模型</span><span class="sxs-lookup"><span data-stu-id="dfade-197">Build and train the model</span></span>

1. <span data-ttu-id="dfade-198">將下列呼叫新增至 `BuildAndTrainModel` 方法作為 `Main()` 方法中的下一行程式碼：</span><span class="sxs-lookup"><span data-stu-id="dfade-198">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallBuildAndTrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallBuildAndTrainModel)]

    <span data-ttu-id="dfade-199">`BuildAndTrainModel()` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="dfade-199">The `BuildAndTrainModel()` method executes the following tasks:</span></span>

    * <span data-ttu-id="dfade-200">擷取並轉換資料。</span><span class="sxs-lookup"><span data-stu-id="dfade-200">Extracts and transforms the data.</span></span>
    * <span data-ttu-id="dfade-201">將模型定型。</span><span class="sxs-lookup"><span data-stu-id="dfade-201">Trains the model.</span></span>
    * <span data-ttu-id="dfade-202">根據測試資料預測情感。</span><span class="sxs-lookup"><span data-stu-id="dfade-202">Predicts sentiment based on test data.</span></span>
    * <span data-ttu-id="dfade-203">傳回模型。</span><span class="sxs-lookup"><span data-stu-id="dfade-203">Returns the model.</span></span>

2. <span data-ttu-id="dfade-204">請使用下列程式碼，在緊接著 `Main()` 方法之後，建立 `BuildAndTrainModel()` 方法：</span><span class="sxs-lookup"><span data-stu-id="dfade-204">Create the `BuildAndTrainModel()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a><span data-ttu-id="dfade-205">擷取並轉換資料</span><span class="sxs-lookup"><span data-stu-id="dfade-205">Extract and transform the data</span></span>

1. <span data-ttu-id="dfade-206">呼叫 `FeaturizeText` 作為下一行程式碼：</span><span class="sxs-lookup"><span data-stu-id="dfade-206">Call `FeaturizeText` as the next line of code:</span></span>

    [!code-csharp[FeaturizeText](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#FeaturizeText "Featurize the text")]

    <span data-ttu-id="dfade-207">上述程式碼中的 `FeaturizeText()` 方法會將文字資料行 (`SentimentText`) 轉換成機器學習演算法所使用的數值索引鍵類型 `Features` 資料行，並將它新增為新的資料集資料行：</span><span class="sxs-lookup"><span data-stu-id="dfade-207">The `FeaturizeText()` method in the previous code converts the text column (`SentimentText`) into a numeric key type `Features` column used by the machine learning algorithm and adds it as a new dataset column:</span></span>

    |<span data-ttu-id="dfade-208">SentimentText</span><span class="sxs-lookup"><span data-stu-id="dfade-208">SentimentText</span></span>                         |<span data-ttu-id="dfade-209">情感</span><span class="sxs-lookup"><span data-stu-id="dfade-209">Sentiment</span></span> |<span data-ttu-id="dfade-210">功能</span><span class="sxs-lookup"><span data-stu-id="dfade-210">Features</span></span>              |
    |--------------------------------------|----------|----------------------|
    |<span data-ttu-id="dfade-211">女服務生的服務速度有點慢。</span><span class="sxs-lookup"><span data-stu-id="dfade-211">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="dfade-212">0</span><span class="sxs-lookup"><span data-stu-id="dfade-212">0</span></span>     |<span data-ttu-id="dfade-213">[0.76, 0.65, 0.44, …]</span><span class="sxs-lookup"><span data-stu-id="dfade-213">[0.76, 0.65, 0.44, …]</span></span> |
    |<span data-ttu-id="dfade-214">不夠酥脆。</span><span class="sxs-lookup"><span data-stu-id="dfade-214">Crust is not good.</span></span>                    |    <span data-ttu-id="dfade-215">0</span><span class="sxs-lookup"><span data-stu-id="dfade-215">0</span></span>     |<span data-ttu-id="dfade-216">[0.98, 0.43, 0.54, …]</span><span class="sxs-lookup"><span data-stu-id="dfade-216">[0.98, 0.43, 0.54, …]</span></span> |
    |<span data-ttu-id="dfade-217">哇...喜歡這個地方。</span><span class="sxs-lookup"><span data-stu-id="dfade-217">Wow... Loved this place.</span></span>              |    <span data-ttu-id="dfade-218">1</span><span class="sxs-lookup"><span data-stu-id="dfade-218">1</span></span>     |<span data-ttu-id="dfade-219">[0.35, 0.73, 0.46, …]</span><span class="sxs-lookup"><span data-stu-id="dfade-219">[0.35, 0.73, 0.46, …]</span></span> |
    |<span data-ttu-id="dfade-220">服務很迅速。</span><span class="sxs-lookup"><span data-stu-id="dfade-220">Service was very prompt.</span></span>              |    <span data-ttu-id="dfade-221">1</span><span class="sxs-lookup"><span data-stu-id="dfade-221">1</span></span>     |<span data-ttu-id="dfade-222">[0.39, 0, 0.75, …]</span><span class="sxs-lookup"><span data-stu-id="dfade-222">[0.39, 0, 0.75, …]</span></span>    |

### <a name="add-a-learning-algorithm"></a><span data-ttu-id="dfade-223">新增學習演算法</span><span class="sxs-lookup"><span data-stu-id="dfade-223">Add a learning algorithm</span></span>

<span data-ttu-id="dfade-224">此應用程式使用分類演算法來分類多個項目或資料列。</span><span class="sxs-lookup"><span data-stu-id="dfade-224">This app uses a classification algorithm that categorizes items or rows of data.</span></span> <span data-ttu-id="dfade-225">應用程式會將網站評論分類為正面或負面，因此請使用二元分類工作。</span><span class="sxs-lookup"><span data-stu-id="dfade-225">The app categorizes website comments as either positive or negative, so use the binary classification task.</span></span>

<span data-ttu-id="dfade-226">透過將下列內容新增為 `BuildAndTrainModel()` 中的下一行程式碼，將機器學習工作附加到資料轉換定義：</span><span class="sxs-lookup"><span data-stu-id="dfade-226">Append the machine learning task to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

<span data-ttu-id="dfade-227">[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) 是您的分類定型演算法。</span><span class="sxs-lookup"><span data-stu-id="dfade-227">The [SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) is your classification training algorithm.</span></span> <span data-ttu-id="dfade-228">這會附加到 `estimator`，並接受特徵化 `SentimentText` (`Features`) 和 `Label` 輸入參數，以從歷史資料學習。</span><span class="sxs-lookup"><span data-stu-id="dfade-228">This is appended to the `estimator` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="dfade-229">將模型定型</span><span class="sxs-lookup"><span data-stu-id="dfade-229">Train the model</span></span>

<span data-ttu-id="dfade-230">將下列內容新增為 `BuildAndTrainModel()` 方法中的下一行程式碼，調整模型為合適於 `splitTrainSet` 資料並傳回已定型模型：</span><span class="sxs-lookup"><span data-stu-id="dfade-230">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TrainModel "Train the model")]

<span data-ttu-id="dfade-231">[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) 方法會透過轉換資料集和套用定型來定型模型。</span><span class="sxs-lookup"><span data-stu-id="dfade-231">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="dfade-232">傳回經訓練以供評估使用的模型</span><span class="sxs-lookup"><span data-stu-id="dfade-232">Return the model trained to use for evaluation</span></span>

 <span data-ttu-id="dfade-233">在 `BuildAndTrainModel()` 方法的結尾傳回模型：</span><span class="sxs-lookup"><span data-stu-id="dfade-233">Return the model at the end of the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="dfade-234">評估模型</span><span class="sxs-lookup"><span data-stu-id="dfade-234">Evaluate the model</span></span>

<span data-ttu-id="dfade-235">定型模型之後，使用您的測試資料來驗證模型效能。</span><span class="sxs-lookup"><span data-stu-id="dfade-235">After your model is trained, use your test data validate the model's performance.</span></span>

1. <span data-ttu-id="dfade-236">在 `BuildAndTrainModel()` 之後，使用下列程式碼建立 `Evaluate()` 方法：</span><span class="sxs-lookup"><span data-stu-id="dfade-236">Create the `Evaluate()` method, just after `BuildAndTrainModel()`, with the following code:</span></span>

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    <span data-ttu-id="dfade-237">`Evaluate()` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="dfade-237">The `Evaluate()` method executes the following tasks:</span></span>

    * <span data-ttu-id="dfade-238">載入測試資料集。</span><span class="sxs-lookup"><span data-stu-id="dfade-238">Loads the test dataset.</span></span>
    * <span data-ttu-id="dfade-239">建立 BinaryClassification 評估工具。</span><span class="sxs-lookup"><span data-stu-id="dfade-239">Creates the BinaryClassification evaluator.</span></span>
    * <span data-ttu-id="dfade-240">評估模型並建立計量。</span><span class="sxs-lookup"><span data-stu-id="dfade-240">Evaluates the model and creates metrics.</span></span>
    * <span data-ttu-id="dfade-241">顯示計量。</span><span class="sxs-lookup"><span data-stu-id="dfade-241">Displays the metrics.</span></span>

2. <span data-ttu-id="dfade-242">請使用下列程式碼，在緊接著 `BuildAndTrainModel()` 方法呼叫底下，從 `Main()` 方法新增對新方法的呼叫：</span><span class="sxs-lookup"><span data-stu-id="dfade-242">Add a call to the new method from the `Main()` method, right under the `BuildAndTrainModel()` method call, using the following code:</span></span>

    [!code-csharp[CallEvaluate](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallEvaluate "Call the Evaluate method")]

3. <span data-ttu-id="dfade-243">將下列程式碼新增至 `Evaluate()` 以轉換 `splitTestSet` 資料：</span><span class="sxs-lookup"><span data-stu-id="dfade-243">Transform the `splitTestSet` data by adding the following code to `Evaluate()`:</span></span>

    [!code-csharp[PredictWithTransformer](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#TransformData "Predict using the Transformer")]

    <span data-ttu-id="dfade-244">上述程式碼使用 [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) 方法對多個提供的測試資料集輸入資料列進行預測。</span><span class="sxs-lookup"><span data-stu-id="dfade-244">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

4. <span data-ttu-id="dfade-245">將下列內容新增為 `Evaluate()` 方法中的下一行程式碼來評估模型：</span><span class="sxs-lookup"><span data-stu-id="dfade-245">Evaluate the model by adding the following as the next line of code in the `Evaluate()` method:</span></span>

    [!code-csharp[ComputeMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Evaluate "Compute Metrics")]

<span data-ttu-id="dfade-246">在您設定好預測 (`predictions`) 後，[Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) 方法會評估模型，將預測值與測試資料集中的實際 `Labels` 進行比較，並傳回與模型執行情況相關的 [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) 物件。</span><span class="sxs-lookup"><span data-stu-id="dfade-246">Once you have the prediction set (`predictions`), the [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns a [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) object on how the model is performing.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="dfade-247">顯示模型驗證的計量</span><span class="sxs-lookup"><span data-stu-id="dfade-247">Displaying the metrics for model validation</span></span>

<span data-ttu-id="dfade-248">使用下列程式碼來顯示計量：</span><span class="sxs-lookup"><span data-stu-id="dfade-248">Use the following code to display the metrics:</span></span>

[!code-csharp[DisplayMetrics](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayMetrics "Display selected metrics")]

* <span data-ttu-id="dfade-249">`Accuracy` 計量會取得模型的準確度，這是資料集中正確預測的比例。</span><span class="sxs-lookup"><span data-stu-id="dfade-249">The `Accuracy` metric gets the accuracy of a model, which is the proportion of correct predictions in the test set.</span></span>

* <span data-ttu-id="dfade-250">`AreaUnderRocCurve` 計量會指出模型正確分類正面和負面類別的自信程度。</span><span class="sxs-lookup"><span data-stu-id="dfade-250">The `AreaUnderRocCurve` metric indicates how confident the model is correctly classifying the positive and negative classes.</span></span> <span data-ttu-id="dfade-251">您會希望 `AreaUnderRocCurve` 盡可能接近 1。</span><span class="sxs-lookup"><span data-stu-id="dfade-251">You want the `AreaUnderRocCurve` to be as close to one as possible.</span></span>

* <span data-ttu-id="dfade-252">`F1Score` 計量會取得模型的 F1 分數，這是[精確度](../resources/glossary.md#precision)與[重新叫用率](../resources/glossary.md#recall)之間的平衡量值。</span><span class="sxs-lookup"><span data-stu-id="dfade-252">The `F1Score` metric gets the model's F1 score, which is a measure of balance between [precision](../resources/glossary.md#precision) and [recall](../resources/glossary.md#recall).</span></span>  <span data-ttu-id="dfade-253">您會希望 `F1Score` 盡可能接近 1。</span><span class="sxs-lookup"><span data-stu-id="dfade-253">You want the `F1Score` to be as close to one as possible.</span></span>

### <a name="predict-the-test-data-outcome"></a><span data-ttu-id="dfade-254">預測測試資料結果</span><span class="sxs-lookup"><span data-stu-id="dfade-254">Predict the test data outcome</span></span>

1. <span data-ttu-id="dfade-255">請使用下列程式碼，在緊接著 `Evaluate()` 方法之後，建立 `UseModelWithSingleItem()` 方法：</span><span class="sxs-lookup"><span data-stu-id="dfade-255">Create the `UseModelWithSingleItem()` method, just after the `Evaluate()` method, using the following code:</span></span>

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="dfade-256">`UseModelWithSingleItem()` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="dfade-256">The `UseModelWithSingleItem()` method executes the following tasks:</span></span>

    * <span data-ttu-id="dfade-257">建立單一評論的測試資料。</span><span class="sxs-lookup"><span data-stu-id="dfade-257">Creates a single comment of test data.</span></span>
    * <span data-ttu-id="dfade-258">根據測試資料預測情感。</span><span class="sxs-lookup"><span data-stu-id="dfade-258">Predicts sentiment based on test data.</span></span>
    * <span data-ttu-id="dfade-259">合併測試資料和預測來進行報告。</span><span class="sxs-lookup"><span data-stu-id="dfade-259">Combines test data and predictions for reporting.</span></span>
    * <span data-ttu-id="dfade-260">顯示預測的結果。</span><span class="sxs-lookup"><span data-stu-id="dfade-260">Displays the predicted results.</span></span>

2. <span data-ttu-id="dfade-261">請使用下列程式碼，在緊接著 `Evaluate()` 方法呼叫底下，從 `Main()` 方法新增對新方法的呼叫：</span><span class="sxs-lookup"><span data-stu-id="dfade-261">Add a call to the new method from the `Main()` method, right under the `Evaluate()` method call, using the following code:</span></span>

    [!code-csharp[CallUseModelWithSingleItem](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. <span data-ttu-id="dfade-262">新增下列程式碼，建立作為 `Predict()` 方法中的第一行：</span><span class="sxs-lookup"><span data-stu-id="dfade-262">Add the following code to create as the first line in the `Predict()` Method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    <span data-ttu-id="dfade-263">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) 是一種便利的 API，可讓您傳遞並在單一資料執行個體上接著執行預測。</span><span class="sxs-lookup"><span data-stu-id="dfade-263">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to pass in and then perform a prediction on a single instance of data.</span></span>

4. <span data-ttu-id="dfade-264">透過建立 `SentimentData` 的執行個體，在 `Predict()` 方法中新增評論，以測試定型模型的預測：</span><span class="sxs-lookup"><span data-stu-id="dfade-264">Add a comment to test the trained model's prediction in the `Predict()` method by creating an instance of `SentimentData`:</span></span>

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. <span data-ttu-id="dfade-265">透過將下列內容新增為 `Prediction Engine` 方法中的後續幾行程式碼，將測試評論資料傳遞到 `UseModelWithSingleItem()`：</span><span class="sxs-lookup"><span data-stu-id="dfade-265">Pass the test comment data to the `Prediction Engine` by adding the following as the next lines of code in the `UseModelWithSingleItem()` method:</span></span>

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Predict "Create a prediction of sentiment")]

    <span data-ttu-id="dfade-266">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) 函式會對單一資料列進行預測。</span><span class="sxs-lookup"><span data-stu-id="dfade-266">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data.</span></span>

6. <span data-ttu-id="dfade-267">使用下列程式碼來顯示 `SentimentText` 和對應的情感預測：</span><span class="sxs-lookup"><span data-stu-id="dfade-267">Display `SentimentText` and corresponding sentiment prediction using the following code:</span></span>

    [!code-csharp[OutputPrediction](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a><span data-ttu-id="dfade-268">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="dfade-268">Use the model for prediction</span></span>

### <a name="deploy-and-predict-batch-items"></a><span data-ttu-id="dfade-269">部署並預測批次項目</span><span class="sxs-lookup"><span data-stu-id="dfade-269">Deploy and predict batch items</span></span>

1. <span data-ttu-id="dfade-270">請使用下列程式碼，在緊接著 `UseModelWithSingleItem()` 方法之後，建立 `UseModelWithBatchItems()` 方法：</span><span class="sxs-lookup"><span data-stu-id="dfade-270">Create the `UseModelWithBatchItems()` method, just after the `UseModelWithSingleItem()` method, using the following code:</span></span>

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="dfade-271">`UseModelWithBatchItems()` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="dfade-271">The `UseModelWithBatchItems()` method executes the following tasks:</span></span>

    * <span data-ttu-id="dfade-272">建立批次測試資料。</span><span class="sxs-lookup"><span data-stu-id="dfade-272">Creates batch test data.</span></span>
    * <span data-ttu-id="dfade-273">根據測試資料預測情感。</span><span class="sxs-lookup"><span data-stu-id="dfade-273">Predicts sentiment based on test data.</span></span>
    * <span data-ttu-id="dfade-274">合併測試資料和預測來進行報告。</span><span class="sxs-lookup"><span data-stu-id="dfade-274">Combines test data and predictions for reporting.</span></span>
    * <span data-ttu-id="dfade-275">顯示預測的結果。</span><span class="sxs-lookup"><span data-stu-id="dfade-275">Displays the predicted results.</span></span>

2. <span data-ttu-id="dfade-276">請使用下列程式碼，在緊接著 `UseModelWithSingleItem()` 方法呼叫底下，從 `Main` 方法新增對新方法的呼叫：</span><span class="sxs-lookup"><span data-stu-id="dfade-276">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem()` method call, using the following code:</span></span>

    [!code-csharp[CallPredictModelBatchItems](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. <span data-ttu-id="dfade-277">新增一些評論以測試 `UseModelWithBatchItems()` 方法中定型模型的預測：</span><span class="sxs-lookup"><span data-stu-id="dfade-277">Add some comments to test the trained model's predictions in the `UseModelWithBatchItems()` method:</span></span>

    [!code-csharp[PredictionData](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a><span data-ttu-id="dfade-278">預測評論情感</span><span class="sxs-lookup"><span data-stu-id="dfade-278">Predict comment sentiment</span></span>

<span data-ttu-id="dfade-279">利用 [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) 方法，使用該模型來預測評論資料情感：</span><span class="sxs-lookup"><span data-stu-id="dfade-279">Use the model to predict the comment data sentiment using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method:</span></span>

[!code-csharp[Predict](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a><span data-ttu-id="dfade-280">合併並顯示預測</span><span class="sxs-lookup"><span data-stu-id="dfade-280">Combine and display the predictions</span></span>

<span data-ttu-id="dfade-281">使用下列程式碼來為預測建立標頭：</span><span class="sxs-lookup"><span data-stu-id="dfade-281">Create a header for the predictions using the following code:</span></span>

[!code-csharp[OutputHeaders](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="dfade-282">因為 `SentimentPrediction` 繼承自 `SentimentData`，所以 `Transform()` 方法會使用預測欄位填入 `SentimentText`。</span><span class="sxs-lookup"><span data-stu-id="dfade-282">Because `SentimentPrediction` is inherited from `SentimentData`, the `Transform()` method populated `SentimentText` with the predicted fields.</span></span> <span data-ttu-id="dfade-283">隨著 ML.NET 處理的進行，每個元件都會新增資料行，使其易於顯示結果：</span><span class="sxs-lookup"><span data-stu-id="dfade-283">As the ML.NET process processes, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/SentimentAnalysis/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a><span data-ttu-id="dfade-284">結果</span><span class="sxs-lookup"><span data-stu-id="dfade-284">Results</span></span>

<span data-ttu-id="dfade-285">您的結果應該與以下類似。</span><span class="sxs-lookup"><span data-stu-id="dfade-285">Your results should be similar to the following.</span></span> <span data-ttu-id="dfade-286">處理期間會顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="dfade-286">During processing, messages are displayed.</span></span> <span data-ttu-id="dfade-287">您可能會看到警告或處理訊息。</span><span class="sxs-lookup"><span data-stu-id="dfade-287">You may see warnings, or processing messages.</span></span> <span data-ttu-id="dfade-288">為了清晰起見，下列結果中已將這些都移除。</span><span class="sxs-lookup"><span data-stu-id="dfade-288">These have been removed from the following results for clarity.</span></span>

```console
Model quality metrics evaluation
--------------------------------
Accuracy: 83.96%
Auc: 90.51%
F1Score: 84.04%

=============== End of model evaluation ===============

=============== Prediction Test of model with a single sample and test dataset ===============

Sentiment: This was a very bad steak | Prediction: Negative | Probability: 0.1027377
=============== End of Predictions ===============


=============== Prediction Test of loaded model with a multiple samples ===============

Sentiment: This was a horrible meal | Prediction: Negative | Probability: 0.1369192
Sentiment: I love this spaghetti. | Prediction: Positive | Probability: 0.9960636
=============== End of predictions ===============

=============== End of process ===============
Press any key to continue . . .

```

<span data-ttu-id="dfade-289">恭喜您！</span><span class="sxs-lookup"><span data-stu-id="dfade-289">Congratulations!</span></span> <span data-ttu-id="dfade-290">您現在已成功建置可對訊息情感進行分類和預測的機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="dfade-290">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span>

<span data-ttu-id="dfade-291">建立成功的模型是一個需要反覆嘗試的程序。</span><span class="sxs-lookup"><span data-stu-id="dfade-291">Building successful models is an iterative process.</span></span> <span data-ttu-id="dfade-292">此模型一開始的品質較低，因為此教學課程是使用小型的資料集來提供快速的模型定型。</span><span class="sxs-lookup"><span data-stu-id="dfade-292">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="dfade-293">如果您對於模型的品質感到不滿意，可以嘗試為它提供較大的定型資料集，或選擇不同的定型演算法，並針對每個演算法搭配不同[超參數](../resources/glossary.md##hyperparameter)來改善它。</span><span class="sxs-lookup"><span data-stu-id="dfade-293">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different [hyper-parameters](../resources/glossary.md##hyperparameter) for each algorithm.</span></span>

<span data-ttu-id="dfade-294">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="dfade-294">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="dfade-295">後續步驟</span><span class="sxs-lookup"><span data-stu-id="dfade-295">Next steps</span></span>

<span data-ttu-id="dfade-296">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="dfade-296">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="dfade-297">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="dfade-297">Create a console application</span></span>
> * <span data-ttu-id="dfade-298">準備資料</span><span class="sxs-lookup"><span data-stu-id="dfade-298">Prepare data</span></span>
> * <span data-ttu-id="dfade-299">載入資料</span><span class="sxs-lookup"><span data-stu-id="dfade-299">Load the data</span></span>
> * <span data-ttu-id="dfade-300">建置和定型模型</span><span class="sxs-lookup"><span data-stu-id="dfade-300">Build and train the model</span></span>
> * <span data-ttu-id="dfade-301">評估模型</span><span class="sxs-lookup"><span data-stu-id="dfade-301">Evaluate the model</span></span>
> * <span data-ttu-id="dfade-302">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="dfade-302">Use the model to make a prediction</span></span>
> * <span data-ttu-id="dfade-303">查看結果</span><span class="sxs-lookup"><span data-stu-id="dfade-303">See the results</span></span>

<span data-ttu-id="dfade-304">前進到下一個教學課程來深入了解</span><span class="sxs-lookup"><span data-stu-id="dfade-304">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="dfade-305">問題分類</span><span class="sxs-lookup"><span data-stu-id="dfade-305">Issue Classification</span></span>](github-issue-classification.md)
