---
title: 教程：分析網站評論 - 二進位分類
description: 本教學課程示範如何建立 .NET Core 主控台應用程式，來分類網站評論中的情感並採取適當動作。 二元情感分類器在 Visual Studio 中使用 C#。
ms.date: 09/30/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 47b9a9fe37cbcacab3797ed7fb1398b0c524d746
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "78241126"
---
# <a name="tutorial-analyze-sentiment-of-website-comments-with-binary-classification-in-mlnet"></a><span data-ttu-id="2aee5-104">教程：在ML.NET中用二進位分類分析網站評論的情緒</span><span class="sxs-lookup"><span data-stu-id="2aee5-104">Tutorial: Analyze sentiment of website comments with binary classification in ML.NET</span></span>

<span data-ttu-id="2aee5-105">本教學課程示範如何建立 .NET Core 主控台應用程式，來分類網站評論中的情感並採取適當動作。</span><span class="sxs-lookup"><span data-stu-id="2aee5-105">This tutorial shows you how to create a .NET Core console application that classifies sentiment from website comments and takes the appropriate action.</span></span> <span data-ttu-id="2aee5-106">二元情感分類器在 Visual Studio 2017 中使用 C#。</span><span class="sxs-lookup"><span data-stu-id="2aee5-106">The binary sentiment classifier uses C# in Visual Studio 2017.</span></span>

<span data-ttu-id="2aee5-107">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="2aee5-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="2aee5-108">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="2aee5-108">Create a console application</span></span>
> - <span data-ttu-id="2aee5-109">準備資料</span><span class="sxs-lookup"><span data-stu-id="2aee5-109">Prepare data</span></span>
> - <span data-ttu-id="2aee5-110">載入資料</span><span class="sxs-lookup"><span data-stu-id="2aee5-110">Load the data</span></span>
> - <span data-ttu-id="2aee5-111">建置和定型模型</span><span class="sxs-lookup"><span data-stu-id="2aee5-111">Build and train the model</span></span>
> - <span data-ttu-id="2aee5-112">評估模型</span><span class="sxs-lookup"><span data-stu-id="2aee5-112">Evaluate the model</span></span>
> - <span data-ttu-id="2aee5-113">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="2aee5-113">Use the model to make a prediction</span></span>
> - <span data-ttu-id="2aee5-114">查看結果</span><span class="sxs-lookup"><span data-stu-id="2aee5-114">See the results</span></span>

<span data-ttu-id="2aee5-115">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="2aee5-115">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2aee5-116">必要條件</span><span class="sxs-lookup"><span data-stu-id="2aee5-116">Prerequisites</span></span>

- <span data-ttu-id="2aee5-117">[Visual Studio 2017 版本 15.6 或更高版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)，安裝了".NET 核心跨平臺開發"工作負載</span><span class="sxs-lookup"><span data-stu-id="2aee5-117">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed</span></span>

- <span data-ttu-id="2aee5-118">[UCI 情感標記句子資料集](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP 檔案)</span><span class="sxs-lookup"><span data-stu-id="2aee5-118">[UCI Sentiment Labeled Sentences dataset](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip) (ZIP file)</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="2aee5-119">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="2aee5-119">Create a console application</span></span>

1. <span data-ttu-id="2aee5-120">建立稱為 "SentimentAnalysis" 的 **.NET Core 主控台應用程式**。</span><span class="sxs-lookup"><span data-stu-id="2aee5-120">Create a **.NET Core Console Application** called "SentimentAnalysis".</span></span>

2. <span data-ttu-id="2aee5-121">在專案中創建名為*Data*的目錄以保存資料集檔。</span><span class="sxs-lookup"><span data-stu-id="2aee5-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="2aee5-122">安裝「Microsoft.ML NuGet 套件」\*\*\*\*：</span><span class="sxs-lookup"><span data-stu-id="2aee5-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="2aee5-123">在 [方案總管] 中，於您的專案上按一下滑鼠右鍵，然後選取 [管理 NuGet 套件]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2aee5-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="2aee5-124">選擇"nuget.org"作為包源，然後選擇 **"流覽**"選項卡。搜索**Microsoft.ML，** 選擇所需的包，然後選擇"**安裝**"按鈕。</span><span class="sxs-lookup"><span data-stu-id="2aee5-124">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="2aee5-125">同意您所選套件的授權條款，以繼續進行安裝。</span><span class="sxs-lookup"><span data-stu-id="2aee5-125">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="2aee5-126">對**Microsoft.ML.FastTree** NuGet 包執行相同的操作。</span><span class="sxs-lookup"><span data-stu-id="2aee5-126">Do the same for the **Microsoft.ML.FastTree** NuGet package.</span></span>

## <a name="prepare-your-data"></a><span data-ttu-id="2aee5-127">準備您的資料</span><span class="sxs-lookup"><span data-stu-id="2aee5-127">Prepare your data</span></span>

> [!NOTE]
> <span data-ttu-id="2aee5-128">此教學課程的資料集是來自 'From Group to Individual Labels using Deep Features' (從群組到使用深度特徵的個別標籤) (Kotzias 等人</span><span class="sxs-lookup"><span data-stu-id="2aee5-128">The datasets for this tutorial are from the 'From Group to Individual Labels using Deep Features', Kotzias et.</span></span> <span data-ttu-id="2aee5-129">al，</span><span class="sxs-lookup"><span data-stu-id="2aee5-129">al,.</span></span> <span data-ttu-id="2aee5-130">KDD 2015，並在UCI機器學習存儲庫託管 - Dua，D.和卡拉塔尼斯基杜，E.（2017年）。</span><span class="sxs-lookup"><span data-stu-id="2aee5-130">KDD 2015, and hosted at the UCI Machine Learning Repository - Dua, D. and Karra Taniskidou, E. (2017).</span></span> <span data-ttu-id="2aee5-131">「UCI Machine Learning Repository (UCI 機器學習存放庫)」[http://archive.ics.uci.edu/ml]。</span><span class="sxs-lookup"><span data-stu-id="2aee5-131">UCI Machine Learning Repository [http://archive.ics.uci.edu/ml].</span></span> <span data-ttu-id="2aee5-132">Irvine, CA: University of California, School of Information and Computer Science.</span><span class="sxs-lookup"><span data-stu-id="2aee5-132">Irvine, CA: University of California, School of Information and Computer Science.</span></span>

1. <span data-ttu-id="2aee5-133">下載並解壓縮 [UCI 情感標記句子資料集 ZIP 檔案](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip)。</span><span class="sxs-lookup"><span data-stu-id="2aee5-133">Download [UCI Sentiment Labeled Sentences dataset ZIP file](https://archive.ics.uci.edu/ml/machine-learning-databases/00331/sentiment%20labelled%20sentences.zip), and unzip.</span></span>

2. <span data-ttu-id="2aee5-134">將 `yelp_labelled.txt` 檔案複製到您所建立的 *Data* 目錄。</span><span class="sxs-lookup"><span data-stu-id="2aee5-134">Copy the `yelp_labelled.txt` file into the *Data* directory you created.</span></span>

3. <span data-ttu-id="2aee5-135">在 [方案總管] 中，以滑鼠右鍵按一下 `yelp_labeled.txt` 檔案，並選取 [內容]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2aee5-135">In Solution Explorer, right-click the `yelp_labeled.txt` file and select **Properties**.</span></span> <span data-ttu-id="2aee5-136">在 **"高級"** 下，將 **"複製到輸出目錄**"的值更改為 **"如果更新"，則將其更改為"複製**"。</span><span class="sxs-lookup"><span data-stu-id="2aee5-136">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="2aee5-137">建立類別及定義路徑</span><span class="sxs-lookup"><span data-stu-id="2aee5-137">Create classes and define paths</span></span>

1. <span data-ttu-id="2aee5-138">在 *Program.cs* 檔案頂端新增下列額外的 `using` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="2aee5-138">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="2aee5-139">將以下代碼添加到方法的正行，`Main`以創建一個欄位來保存最近下載的資料集檔路徑：</span><span class="sxs-lookup"><span data-stu-id="2aee5-139">Add the following code to the line right above the `Main` method, to create a field to hold the recently downloaded dataset file path:</span></span>

    [!code-csharp[Declare global variables](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

1. <span data-ttu-id="2aee5-140">接下來，為輸入資料和預測建立類別。</span><span class="sxs-lookup"><span data-stu-id="2aee5-140">Next, create classes for your input data and predictions.</span></span> <span data-ttu-id="2aee5-141">將新類別新增至專案：</span><span class="sxs-lookup"><span data-stu-id="2aee5-141">Add a new class to your project:</span></span>

    - <span data-ttu-id="2aee5-142">在 [方案總管]\*\*\*\* 中，以滑鼠右鍵按一下專案，然後選取 [新增]\*\*\*\* > [新項目]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="2aee5-142">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

    - <span data-ttu-id="2aee5-143">在 [新增項目]\*\*\*\* 對話方塊中，選取 [類別]\*\*\*\*，然後將 [名稱]\*\*\*\* 欄位變更為 *SentimentData.cs*。</span><span class="sxs-lookup"><span data-stu-id="2aee5-143">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="2aee5-144">接著，選取 [新增]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="2aee5-144">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="2aee5-145">*SentimentData.cs* 檔案隨即在程式碼編輯器中開啟。</span><span class="sxs-lookup"><span data-stu-id="2aee5-145">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="2aee5-146">將以下 `using` 陳述式新增至 *SentimentData.cs* 頂端：</span><span class="sxs-lookup"><span data-stu-id="2aee5-146">Add the following `using` statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp[AddUsings](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="2aee5-147">移除現有的類別定義，然後將下列程式碼 (具有 `SentimentData` 和 `SentimentPrediction` 這兩個類別) 新增至 *SentimentData.cs* 檔案：</span><span class="sxs-lookup"><span data-stu-id="2aee5-147">Remove the existing class definition and add the following code, which has two classes `SentimentData` and `SentimentPrediction`, to the *SentimentData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/SentimentData.cs#DeclareTypes "Declare data record types")]

### <a name="how-the-data-was-prepared"></a><span data-ttu-id="2aee5-148">如何準備資料</span><span class="sxs-lookup"><span data-stu-id="2aee5-148">How the data was prepared</span></span>

<span data-ttu-id="2aee5-149">輸入資料集類別 `SentimentData` 具有使用者評論 (`SentimentText`) 的 `string`，以及代表情感的 `bool` (`Sentiment`) 值 1 (正面) 或 0 (負面)。</span><span class="sxs-lookup"><span data-stu-id="2aee5-149">The input dataset class, `SentimentData`, has a `string` for user comments (`SentimentText`) and a `bool` (`Sentiment`) value of either 1 (positive) or 0 (negative) for sentiment.</span></span> <span data-ttu-id="2aee5-150">這兩個欄位都有 [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) 附加屬性，其描述每個欄位的資料檔案順序。</span><span class="sxs-lookup"><span data-stu-id="2aee5-150">Both fields have [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attributes attached to them, which describes the data file order of each field.</span></span>  <span data-ttu-id="2aee5-151">此外，`Sentiment` 屬性具有 [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) 屬性來將它指定為 `Label` 欄位。</span><span class="sxs-lookup"><span data-stu-id="2aee5-151">In addition, the `Sentiment` property has a [ColumnName](xref:Microsoft.ML.Data.ColumnNameAttribute.%23ctor%2A) attribute to designate it as the `Label` field.</span></span> <span data-ttu-id="2aee5-152">下列範例檔案沒有標頭資料列，且看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="2aee5-152">The following example file doesn't have a header row, and looks like this:</span></span>

|<span data-ttu-id="2aee5-153">SentimentText</span><span class="sxs-lookup"><span data-stu-id="2aee5-153">SentimentText</span></span>                         |<span data-ttu-id="2aee5-154">情感 (標籤)</span><span class="sxs-lookup"><span data-stu-id="2aee5-154">Sentiment (Label)</span></span> |
|--------------------------------------|----------|
|<span data-ttu-id="2aee5-155">女服務生的服務速度有點慢。</span><span class="sxs-lookup"><span data-stu-id="2aee5-155">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="2aee5-156">0</span><span class="sxs-lookup"><span data-stu-id="2aee5-156">0</span></span>     |
|<span data-ttu-id="2aee5-157">不夠酥脆。</span><span class="sxs-lookup"><span data-stu-id="2aee5-157">Crust is not good.</span></span>                    |    <span data-ttu-id="2aee5-158">0</span><span class="sxs-lookup"><span data-stu-id="2aee5-158">0</span></span>     |
|<span data-ttu-id="2aee5-159">哇。。。喜歡這個地方</span><span class="sxs-lookup"><span data-stu-id="2aee5-159">Wow... Loved this place.</span></span>              |    <span data-ttu-id="2aee5-160">1</span><span class="sxs-lookup"><span data-stu-id="2aee5-160">1</span></span>     |
|<span data-ttu-id="2aee5-161">服務很迅速。</span><span class="sxs-lookup"><span data-stu-id="2aee5-161">Service was very prompt.</span></span>              |    <span data-ttu-id="2aee5-162">1</span><span class="sxs-lookup"><span data-stu-id="2aee5-162">1</span></span>     |

<span data-ttu-id="2aee5-163">`SentimentPrediction` 是在模型定型後所使用的預測類別。</span><span class="sxs-lookup"><span data-stu-id="2aee5-163">`SentimentPrediction` is the prediction class used after model training.</span></span> <span data-ttu-id="2aee5-164">它繼承自 `SentimentData`，以便輸入 `SentimentText` 可以和輸出預測一起顯示。</span><span class="sxs-lookup"><span data-stu-id="2aee5-164">It inherits from `SentimentData` so that the input `SentimentText` can be displayed along with the output prediction.</span></span> <span data-ttu-id="2aee5-165">`Prediction` 布林值是在提供新輸入 `SentimentText` 時，模型預測的值。</span><span class="sxs-lookup"><span data-stu-id="2aee5-165">The `Prediction` boolean is the value that the model predicts when supplied with new input `SentimentText`.</span></span>

<span data-ttu-id="2aee5-166">輸出類別 `SentimentPrediction` 包含模型計算的兩個其他屬性：`Score` - 模型計算的原始分數，和 `Probability` - 針對文字具有正面情感之可能性所校正的分數。</span><span class="sxs-lookup"><span data-stu-id="2aee5-166">The output class `SentimentPrediction` contains two other properties calculated by the model: `Score` - the raw score calculated by the model, and `Probability` - the score calibrated to the likelihood of the text having positive sentiment.</span></span>

<span data-ttu-id="2aee5-167">本教學課程中最重要的屬性是 `Prediction`。</span><span class="sxs-lookup"><span data-stu-id="2aee5-167">For this tutorial, the most important property is `Prediction`.</span></span>

## <a name="load-the-data"></a><span data-ttu-id="2aee5-168">載入資料</span><span class="sxs-lookup"><span data-stu-id="2aee5-168">Load the data</span></span>

<span data-ttu-id="2aee5-169">ML.NET 中的資料以 [IDataView 類別](xref:Microsoft.ML.IDataView) 表示。</span><span class="sxs-lookup"><span data-stu-id="2aee5-169">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="2aee5-170">`IDataView` 是彈性且有效率的表格式資料描述方式 (數值和文字)。</span><span class="sxs-lookup"><span data-stu-id="2aee5-170">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="2aee5-171">資料可以從文字或即時 (例如 SQL 資料庫或記錄檔) 載入至 `IDataView` 物件。</span><span class="sxs-lookup"><span data-stu-id="2aee5-171">Data can be loaded from a text file or in real time (for example, SQL database or log files) to an `IDataView` object.</span></span>

<span data-ttu-id="2aee5-172">[MLContext 類別](xref:Microsoft.ML.MLContext)是所有 ML.NET 作業的起點。</span><span class="sxs-lookup"><span data-stu-id="2aee5-172">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="2aee5-173">將 `mlContext` 初始化會建立新的 ML.NET 環境，可在模型建立工作流程物件間共用。</span><span class="sxs-lookup"><span data-stu-id="2aee5-173">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="2aee5-174">就概念而言，類似於 Entity Framework 中的 `DBContext`。</span><span class="sxs-lookup"><span data-stu-id="2aee5-174">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

<span data-ttu-id="2aee5-175">您可以準備資料，然後載入資料：</span><span class="sxs-lookup"><span data-stu-id="2aee5-175">You prepare the app, and then load data:</span></span>

1. <span data-ttu-id="2aee5-176">將 `Main` 方法中的 `Console.WriteLine("Hello World!")` 程式碼行取代為下列程式碼，以宣告 mlContext 變數並將它初始化：</span><span class="sxs-lookup"><span data-stu-id="2aee5-176">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

    [!code-csharp[CreateMLContext](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateMLContext "Create the ML Context")]

2. <span data-ttu-id="2aee5-177">將下列程式碼加入為 `Main()` 方法中的下一行程式碼：</span><span class="sxs-lookup"><span data-stu-id="2aee5-177">Add the following as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallLoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallLoadData)]

3. <span data-ttu-id="2aee5-178">請使用下列程式碼，在緊接著 `Main()` 方法之後，建立 `LoadData()` 方法：</span><span class="sxs-lookup"><span data-stu-id="2aee5-178">Create the `LoadData()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static TrainTestData LoadData(MLContext mlContext)
    {

    }
    ```

    <span data-ttu-id="2aee5-179">`LoadData()` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="2aee5-179">The `LoadData()` method executes the following tasks:</span></span>

    - <span data-ttu-id="2aee5-180">載入資料。</span><span class="sxs-lookup"><span data-stu-id="2aee5-180">Loads the data.</span></span>
    - <span data-ttu-id="2aee5-181">將載入的資料集分割為定型與測試資料集。</span><span class="sxs-lookup"><span data-stu-id="2aee5-181">Splits the loaded dataset into train and test datasets.</span></span>
    - <span data-ttu-id="2aee5-182">傳回分割的定型與測試資料集。</span><span class="sxs-lookup"><span data-stu-id="2aee5-182">Returns the split train and test datasets.</span></span>

4. <span data-ttu-id="2aee5-183">將下列程式碼新增為 `LoadData()` 方法的第一行：</span><span class="sxs-lookup"><span data-stu-id="2aee5-183">Add the following code as the first line of the `LoadData()` method:</span></span>

    [!code-csharp[LoadData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="2aee5-184">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) 會定義資料結構描述並讀入檔案中。</span><span class="sxs-lookup"><span data-stu-id="2aee5-184">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="2aee5-185">會接受資料路徑變數然後傳回 `IDataView`。</span><span class="sxs-lookup"><span data-stu-id="2aee5-185">It takes in the data path variables and returns an `IDataView`.</span></span>

### <a name="split-the-dataset-for-model-training-and-testing"></a><span data-ttu-id="2aee5-186">分割資料集以進行模型定型與測試</span><span class="sxs-lookup"><span data-stu-id="2aee5-186">Split the dataset for model training and testing</span></span>

<span data-ttu-id="2aee5-187">準備模型時，您可以使用部分資料集來定型它，並使用部分資料集來測試模型的準確度。</span><span class="sxs-lookup"><span data-stu-id="2aee5-187">When preparing a model, you use part of the dataset to train it and part of the dataset to test the model's accuracy.</span></span>

1. <span data-ttu-id="2aee5-188">若要將載入的資料分割成所需的資料集，請將下列程式碼加入為 `LoadData()` 方法中的下一行：</span><span class="sxs-lookup"><span data-stu-id="2aee5-188">To split the loaded data into the needed datasets, add the following code as the next line in the `LoadData()` method:</span></span>

    [!code-csharp[SplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#SplitData "Split the Data")]

    <span data-ttu-id="2aee5-189">上述程式碼使用 [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) 方法將載入的資料集分割為定型與測試資料集，然後將它們包含在 [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) 類別中並傳回。</span><span class="sxs-lookup"><span data-stu-id="2aee5-189">The previous code uses the [TrainTestSplit()](xref:Microsoft.ML.DataOperationsCatalog.TrainTestSplit%2A) method to split the loaded dataset into train and test datasets and return them in the [TrainTestData](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) class.</span></span> <span data-ttu-id="2aee5-190">您可以使用 `testFraction` 參數來指定資料的測試集百分比。</span><span class="sxs-lookup"><span data-stu-id="2aee5-190">Specify the test set percentage of data with the `testFraction`parameter.</span></span> <span data-ttu-id="2aee5-191">預設值是 10%，但您在本例中會使用 20% 以評估更多資料。</span><span class="sxs-lookup"><span data-stu-id="2aee5-191">The default is 10%, in this case you use 20% to evaluate more data.</span></span>

2. <span data-ttu-id="2aee5-192">在 `LoadData()` 方法的結尾傳回 `splitDataView`：</span><span class="sxs-lookup"><span data-stu-id="2aee5-192">Return the `splitDataView` at the end of the `LoadData()` method:</span></span>

    [!code-csharp[ReturnSplitData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnSplitData)]

## <a name="build-and-train-the-model"></a><span data-ttu-id="2aee5-193">建置和定型模型</span><span class="sxs-lookup"><span data-stu-id="2aee5-193">Build and train the model</span></span>

1. <span data-ttu-id="2aee5-194">將下列呼叫新增至 `BuildAndTrainModel` 方法作為 `Main()` 方法中的下一行程式碼：</span><span class="sxs-lookup"><span data-stu-id="2aee5-194">Add the following call to the `BuildAndTrainModel`method as the next line of code in the `Main()` method:</span></span>

    [!code-csharp[CallBuildAndTrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallBuildAndTrainModel)]

    <span data-ttu-id="2aee5-195">`BuildAndTrainModel()` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="2aee5-195">The `BuildAndTrainModel()` method executes the following tasks:</span></span>

    - <span data-ttu-id="2aee5-196">擷取並轉換資料。</span><span class="sxs-lookup"><span data-stu-id="2aee5-196">Extracts and transforms the data.</span></span>
    - <span data-ttu-id="2aee5-197">將模型定型。</span><span class="sxs-lookup"><span data-stu-id="2aee5-197">Trains the model.</span></span>
    - <span data-ttu-id="2aee5-198">根據測試資料預測情感。</span><span class="sxs-lookup"><span data-stu-id="2aee5-198">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="2aee5-199">傳回模型。</span><span class="sxs-lookup"><span data-stu-id="2aee5-199">Returns the model.</span></span>

2. <span data-ttu-id="2aee5-200">請使用下列程式碼，在緊接著 `Main()` 方法之後，建立 `BuildAndTrainModel()` 方法：</span><span class="sxs-lookup"><span data-stu-id="2aee5-200">Create the `BuildAndTrainModel()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    public static ITransformer BuildAndTrainModel(MLContext mlContext, IDataView splitTrainSet)
    {

    }
    ```

### <a name="extract-and-transform-the-data"></a><span data-ttu-id="2aee5-201">擷取並轉換資料</span><span class="sxs-lookup"><span data-stu-id="2aee5-201">Extract and transform the data</span></span>

1. <span data-ttu-id="2aee5-202">呼叫 `FeaturizeText` 作為下一行程式碼：</span><span class="sxs-lookup"><span data-stu-id="2aee5-202">Call `FeaturizeText` as the next line of code:</span></span>

    [!code-csharp[FeaturizeText](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#FeaturizeText "Featurize the text")]

    <span data-ttu-id="2aee5-203">上述程式碼中的 `FeaturizeText()` 方法會將文字資料行 (`SentimentText`) 轉換成機器學習演算法所使用的數值索引鍵類型 `Features` 資料行，並將它新增為新的資料集資料行：</span><span class="sxs-lookup"><span data-stu-id="2aee5-203">The `FeaturizeText()` method in the previous code converts the text column (`SentimentText`) into a numeric key type `Features` column used by the machine learning algorithm and adds it as a new dataset column:</span></span>

    |<span data-ttu-id="2aee5-204">SentimentText</span><span class="sxs-lookup"><span data-stu-id="2aee5-204">SentimentText</span></span>                         |<span data-ttu-id="2aee5-205">情感</span><span class="sxs-lookup"><span data-stu-id="2aee5-205">Sentiment</span></span> |<span data-ttu-id="2aee5-206">特性</span><span class="sxs-lookup"><span data-stu-id="2aee5-206">Features</span></span>              |
    |--------------------------------------|----------|----------------------|
    |<span data-ttu-id="2aee5-207">女服務生的服務速度有點慢。</span><span class="sxs-lookup"><span data-stu-id="2aee5-207">Waitress was a little slow in service.</span></span>|    <span data-ttu-id="2aee5-208">0</span><span class="sxs-lookup"><span data-stu-id="2aee5-208">0</span></span>     |<span data-ttu-id="2aee5-209">[0.76, 0.65, 0.44, …]</span><span class="sxs-lookup"><span data-stu-id="2aee5-209">[0.76, 0.65, 0.44, …]</span></span> |
    |<span data-ttu-id="2aee5-210">不夠酥脆。</span><span class="sxs-lookup"><span data-stu-id="2aee5-210">Crust is not good.</span></span>                    |    <span data-ttu-id="2aee5-211">0</span><span class="sxs-lookup"><span data-stu-id="2aee5-211">0</span></span>     |<span data-ttu-id="2aee5-212">[0.98, 0.43, 0.54, …]</span><span class="sxs-lookup"><span data-stu-id="2aee5-212">[0.98, 0.43, 0.54, …]</span></span> |
    |<span data-ttu-id="2aee5-213">哇。。。喜歡這個地方</span><span class="sxs-lookup"><span data-stu-id="2aee5-213">Wow... Loved this place.</span></span>              |    <span data-ttu-id="2aee5-214">1</span><span class="sxs-lookup"><span data-stu-id="2aee5-214">1</span></span>     |<span data-ttu-id="2aee5-215">[0.35, 0.73, 0.46, …]</span><span class="sxs-lookup"><span data-stu-id="2aee5-215">[0.35, 0.73, 0.46, …]</span></span> |
    |<span data-ttu-id="2aee5-216">服務很迅速。</span><span class="sxs-lookup"><span data-stu-id="2aee5-216">Service was very prompt.</span></span>              |    <span data-ttu-id="2aee5-217">1</span><span class="sxs-lookup"><span data-stu-id="2aee5-217">1</span></span>     |<span data-ttu-id="2aee5-218">[0.39, 0, 0.75, …]</span><span class="sxs-lookup"><span data-stu-id="2aee5-218">[0.39, 0, 0.75, …]</span></span>    |

### <a name="add-a-learning-algorithm"></a><span data-ttu-id="2aee5-219">新增學習演算法</span><span class="sxs-lookup"><span data-stu-id="2aee5-219">Add a learning algorithm</span></span>

<span data-ttu-id="2aee5-220">此應用程式使用分類演算法來分類多個項目或資料列。</span><span class="sxs-lookup"><span data-stu-id="2aee5-220">This app uses a classification algorithm that categorizes items or rows of data.</span></span> <span data-ttu-id="2aee5-221">應用程式會將網站評論分類為正面或負面，因此請使用二元分類工作。</span><span class="sxs-lookup"><span data-stu-id="2aee5-221">The app categorizes website comments as either positive or negative, so use the binary classification task.</span></span>

<span data-ttu-id="2aee5-222">透過將下列內容新增為 `BuildAndTrainModel()` 中的下一行程式碼，將機器學習工作附加到資料轉換定義：</span><span class="sxs-lookup"><span data-stu-id="2aee5-222">Append the machine learning task to the data transformation definitions by adding the following as the next line of code in `BuildAndTrainModel()`:</span></span>

[!code-csharp[SdcaLogisticRegressionBinaryTrainer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddTrainer "Add a SdcaLogisticRegressionBinaryTrainer")]

<span data-ttu-id="2aee5-223">[SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) 是您的分類定型演算法。</span><span class="sxs-lookup"><span data-stu-id="2aee5-223">The [SdcaLogisticRegressionBinaryTrainer](xref:Microsoft.ML.Trainers.SdcaLogisticRegressionBinaryTrainer) is your classification training algorithm.</span></span> <span data-ttu-id="2aee5-224">這會附加到 `estimator`，並接受特徵化 `SentimentText` (`Features`) 和 `Label` 輸入參數，以從歷史資料學習。</span><span class="sxs-lookup"><span data-stu-id="2aee5-224">This is appended to the `estimator` and accepts the featurized `SentimentText` (`Features`) and the `Label` input parameters to learn from the historic data.</span></span>

### <a name="train-the-model"></a><span data-ttu-id="2aee5-225">將模型定型</span><span class="sxs-lookup"><span data-stu-id="2aee5-225">Train the model</span></span>

<span data-ttu-id="2aee5-226">將下列內容新增為 `BuildAndTrainModel()` 方法中的下一行程式碼，調整模型為合適於 `splitTrainSet` 資料並傳回已定型模型：</span><span class="sxs-lookup"><span data-stu-id="2aee5-226">Fit the model to the `splitTrainSet` data and return the trained model by adding the following as the next line of code in the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[TrainModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TrainModel "Train the model")]

<span data-ttu-id="2aee5-227">[Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) 方法透過轉換資料集和套用定型來定型模型。</span><span class="sxs-lookup"><span data-stu-id="2aee5-227">The [Fit()](xref:Microsoft.ML.Trainers.MatrixFactorizationTrainer.Fit%28Microsoft.ML.IDataView,Microsoft.ML.IDataView%29) method trains your model by transforming the dataset and applying the training.</span></span>

### <a name="return-the-model-trained-to-use-for-evaluation"></a><span data-ttu-id="2aee5-228">傳回經訓練以供評估使用的模型</span><span class="sxs-lookup"><span data-stu-id="2aee5-228">Return the model trained to use for evaluation</span></span>

 <span data-ttu-id="2aee5-229">在 `BuildAndTrainModel()` 方法的結尾傳回模型：</span><span class="sxs-lookup"><span data-stu-id="2aee5-229">Return the model at the end of the `BuildAndTrainModel()` method:</span></span>

[!code-csharp[ReturnModel](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#ReturnModel "Return the model")]

## <a name="evaluate-the-model"></a><span data-ttu-id="2aee5-230">評估模型</span><span class="sxs-lookup"><span data-stu-id="2aee5-230">Evaluate the model</span></span>

<span data-ttu-id="2aee5-231">定型模型之後，使用您的測試資料來驗證模型效能。</span><span class="sxs-lookup"><span data-stu-id="2aee5-231">After your model is trained, use your test data validate the model's performance.</span></span>

1. <span data-ttu-id="2aee5-232">在 `BuildAndTrainModel()` 之後，使用下列程式碼建立 `Evaluate()` 方法：</span><span class="sxs-lookup"><span data-stu-id="2aee5-232">Create the `Evaluate()` method, just after `BuildAndTrainModel()`, with the following code:</span></span>

    ```csharp
    public static void Evaluate(MLContext mlContext, ITransformer model, IDataView splitTestSet)
    {

    }
    ```

    <span data-ttu-id="2aee5-233">`Evaluate()` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="2aee5-233">The `Evaluate()` method executes the following tasks:</span></span>

    - <span data-ttu-id="2aee5-234">載入測試資料集。</span><span class="sxs-lookup"><span data-stu-id="2aee5-234">Loads the test dataset.</span></span>
    - <span data-ttu-id="2aee5-235">建立 BinaryClassification 評估工具。</span><span class="sxs-lookup"><span data-stu-id="2aee5-235">Creates the BinaryClassification evaluator.</span></span>
    - <span data-ttu-id="2aee5-236">評估模型並建立計量。</span><span class="sxs-lookup"><span data-stu-id="2aee5-236">Evaluates the model and creates metrics.</span></span>
    - <span data-ttu-id="2aee5-237">顯示計量。</span><span class="sxs-lookup"><span data-stu-id="2aee5-237">Displays the metrics.</span></span>

2. <span data-ttu-id="2aee5-238">請使用下列程式碼，在緊接著 `BuildAndTrainModel()` 方法呼叫底下，從 `Main()` 方法新增對新方法的呼叫：</span><span class="sxs-lookup"><span data-stu-id="2aee5-238">Add a call to the new method from the `Main()` method, right under the `BuildAndTrainModel()` method call, using the following code:</span></span>

    [!code-csharp[CallEvaluate](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallEvaluate "Call the Evaluate method")]

3. <span data-ttu-id="2aee5-239">將下列程式碼新增至 `Evaluate()` 以轉換 `splitTestSet` 資料：</span><span class="sxs-lookup"><span data-stu-id="2aee5-239">Transform the `splitTestSet` data by adding the following code to `Evaluate()`:</span></span>

    [!code-csharp[PredictWithTransformer](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#TransformData "Predict using the Transformer")]

    <span data-ttu-id="2aee5-240">之前的程式碼使用 [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) 方法會對測試資料集多個所提供的輸入資料列進行預測。</span><span class="sxs-lookup"><span data-stu-id="2aee5-240">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple provided input rows of a test dataset.</span></span>

4. <span data-ttu-id="2aee5-241">將下列內容新增為 `Evaluate()` 方法中的下一行程式碼來評估模型：</span><span class="sxs-lookup"><span data-stu-id="2aee5-241">Evaluate the model by adding the following as the next line of code in the `Evaluate()` method:</span></span>

    [!code-csharp[ComputeMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Evaluate "Compute Metrics")]

<span data-ttu-id="2aee5-242">在您設定好預測 (`predictions`) 後，[Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) 方法會評估模型，將預測值與測試資料集中的實際 `Labels` 進行比較，並傳回與模型執行情況相關的 [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) 物件。</span><span class="sxs-lookup"><span data-stu-id="2aee5-242">Once you have the prediction set (`predictions`), the [Evaluate()](xref:Microsoft.ML.BinaryClassificationCatalog.Evaluate%2A) method assesses the model, which compares the predicted values with the actual `Labels` in the test dataset and returns a [CalibratedBinaryClassificationMetrics](xref:Microsoft.ML.Data.CalibratedBinaryClassificationMetrics) object on how the model is performing.</span></span>

### <a name="displaying-the-metrics-for-model-validation"></a><span data-ttu-id="2aee5-243">顯示模型驗證的計量</span><span class="sxs-lookup"><span data-stu-id="2aee5-243">Displaying the metrics for model validation</span></span>

<span data-ttu-id="2aee5-244">使用下列程式碼來顯示計量：</span><span class="sxs-lookup"><span data-stu-id="2aee5-244">Use the following code to display the metrics:</span></span>

[!code-csharp[DisplayMetrics](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayMetrics "Display selected metrics")]

- <span data-ttu-id="2aee5-245">`Accuracy` 計量會取得模型的準確度，這是資料集中正確預測的比例。</span><span class="sxs-lookup"><span data-stu-id="2aee5-245">The `Accuracy` metric gets the accuracy of a model, which is the proportion of correct predictions in the test set.</span></span>

- <span data-ttu-id="2aee5-246">`AreaUnderRocCurve` 計量會指出模型正確分類正面和負面類別的自信程度。</span><span class="sxs-lookup"><span data-stu-id="2aee5-246">The `AreaUnderRocCurve` metric indicates how confident the model is correctly classifying the positive and negative classes.</span></span> <span data-ttu-id="2aee5-247">您會希望 `AreaUnderRocCurve` 盡可能接近 1。</span><span class="sxs-lookup"><span data-stu-id="2aee5-247">You want the `AreaUnderRocCurve` to be as close to one as possible.</span></span>

- <span data-ttu-id="2aee5-248">`F1Score` 計量會取得模型的 F1 分數，這是[精確度](../resources/glossary.md#precision)與[重新叫用率](../resources/glossary.md#recall)之間的平衡量值。</span><span class="sxs-lookup"><span data-stu-id="2aee5-248">The `F1Score` metric gets the model's F1 score, which is a measure of balance between [precision](../resources/glossary.md#precision) and [recall](../resources/glossary.md#recall).</span></span>  <span data-ttu-id="2aee5-249">您會希望 `F1Score` 盡可能接近 1。</span><span class="sxs-lookup"><span data-stu-id="2aee5-249">You want the `F1Score` to be as close to one as possible.</span></span>

### <a name="predict-the-test-data-outcome"></a><span data-ttu-id="2aee5-250">預測測試資料結果</span><span class="sxs-lookup"><span data-stu-id="2aee5-250">Predict the test data outcome</span></span>

1. <span data-ttu-id="2aee5-251">請使用下列程式碼，在緊接著 `Evaluate()` 方法之後，建立 `UseModelWithSingleItem()` 方法：</span><span class="sxs-lookup"><span data-stu-id="2aee5-251">Create the `UseModelWithSingleItem()` method, just after the `Evaluate()` method, using the following code:</span></span>

    ```csharp
    private static void UseModelWithSingleItem(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="2aee5-252">`UseModelWithSingleItem()` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="2aee5-252">The `UseModelWithSingleItem()` method executes the following tasks:</span></span>

    - <span data-ttu-id="2aee5-253">建立單一評論的測試資料。</span><span class="sxs-lookup"><span data-stu-id="2aee5-253">Creates a single comment of test data.</span></span>
    - <span data-ttu-id="2aee5-254">根據測試資料預測情感。</span><span class="sxs-lookup"><span data-stu-id="2aee5-254">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="2aee5-255">合併測試資料和預測來進行報告。</span><span class="sxs-lookup"><span data-stu-id="2aee5-255">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="2aee5-256">顯示預測的結果。</span><span class="sxs-lookup"><span data-stu-id="2aee5-256">Displays the predicted results.</span></span>

2. <span data-ttu-id="2aee5-257">請使用下列程式碼，在緊接著 `Evaluate()` 方法呼叫底下，從 `Main()` 方法新增對新方法的呼叫：</span><span class="sxs-lookup"><span data-stu-id="2aee5-257">Add a call to the new method from the `Main()` method, right under the `Evaluate()` method call, using the following code:</span></span>

    [!code-csharp[CallUseModelWithSingleItem](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithSingleItem "Call the UseModelWithSingleItem method")]

3. <span data-ttu-id="2aee5-258">新增下列程式碼，建立作為 `UseModelWithSingleItem()` 方法中的第一行：</span><span class="sxs-lookup"><span data-stu-id="2aee5-258">Add the following code to create as the first line in the `UseModelWithSingleItem()` Method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreatePredictionEngine1 "Create the PredictionEngine")]

    <span data-ttu-id="2aee5-259">[預測引擎](xref:Microsoft.ML.PredictionEngine%602)是一個方便的 API，它允許您對單個資料實例執行預測。</span><span class="sxs-lookup"><span data-stu-id="2aee5-259">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="2aee5-260">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)不是執行緒安全的。</span><span class="sxs-lookup"><span data-stu-id="2aee5-260">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="2aee5-261">在單線程或原型環境中使用是可以接受的。</span><span class="sxs-lookup"><span data-stu-id="2aee5-261">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="2aee5-262">為提高生產環境中的性能和執行緒安全性，請使用`PredictionEnginePool`該服務，該服務創建一個[`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601)[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)物件，供整個應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="2aee5-262">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="2aee5-263">請參閱有關如何[`PredictionEnginePool`在 ASP.NET核心 Web API 中使用](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)的本指南。</span><span class="sxs-lookup"><span data-stu-id="2aee5-263">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="2aee5-264">`PredictionEnginePool` 服務延伸模組目前處於預覽狀態。</span><span class="sxs-lookup"><span data-stu-id="2aee5-264">`PredictionEnginePool` service extension is currently in preview.</span></span>

4. <span data-ttu-id="2aee5-265">透過建立 `SentimentData` 的執行個體，在 `UseModelWithSingleItem()` 方法中新增評論，以測試定型模型的預測：</span><span class="sxs-lookup"><span data-stu-id="2aee5-265">Add a comment to test the trained model's prediction in the `UseModelWithSingleItem()` method by creating an instance of `SentimentData`:</span></span>

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssue1 "Create test data for single prediction")]

5. <span data-ttu-id="2aee5-266">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602)通過將以下內容添加為 方法中的下一行代碼，`UseModelWithSingleItem()`將測試注釋資料傳遞給 ：</span><span class="sxs-lookup"><span data-stu-id="2aee5-266">Pass the test comment data to the [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) by adding the following as the next lines of code in the `UseModelWithSingleItem()` method:</span></span>

    [!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Predict "Create a prediction of sentiment")]

    <span data-ttu-id="2aee5-267">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) 函式會對單一資料列進行預測。</span><span class="sxs-lookup"><span data-stu-id="2aee5-267">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data.</span></span>

6. <span data-ttu-id="2aee5-268">使用下列程式碼來顯示 `SentimentText` 和對應的情感預測：</span><span class="sxs-lookup"><span data-stu-id="2aee5-268">Display `SentimentText` and corresponding sentiment prediction using the following code:</span></span>

    [!code-csharp[OutputPrediction](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#OutputPrediction "Display prediction output")]

## <a name="use-the-model-for-prediction"></a><span data-ttu-id="2aee5-269">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="2aee5-269">Use the model for prediction</span></span>

### <a name="deploy-and-predict-batch-items"></a><span data-ttu-id="2aee5-270">部署並預測批次項目</span><span class="sxs-lookup"><span data-stu-id="2aee5-270">Deploy and predict batch items</span></span>

1. <span data-ttu-id="2aee5-271">請使用下列程式碼，在緊接著 `UseModelWithSingleItem()` 方法之後，建立 `UseModelWithBatchItems()` 方法：</span><span class="sxs-lookup"><span data-stu-id="2aee5-271">Create the `UseModelWithBatchItems()` method, just after the `UseModelWithSingleItem()` method, using the following code:</span></span>

    ```csharp
    public static void UseModelWithBatchItems(MLContext mlContext, ITransformer model)
    {

    }
    ```

    <span data-ttu-id="2aee5-272">`UseModelWithBatchItems()` 方法會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="2aee5-272">The `UseModelWithBatchItems()` method executes the following tasks:</span></span>

    - <span data-ttu-id="2aee5-273">建立批次測試資料。</span><span class="sxs-lookup"><span data-stu-id="2aee5-273">Creates batch test data.</span></span>
    - <span data-ttu-id="2aee5-274">根據測試資料預測情感。</span><span class="sxs-lookup"><span data-stu-id="2aee5-274">Predicts sentiment based on test data.</span></span>
    - <span data-ttu-id="2aee5-275">合併測試資料和預測來進行報告。</span><span class="sxs-lookup"><span data-stu-id="2aee5-275">Combines test data and predictions for reporting.</span></span>
    - <span data-ttu-id="2aee5-276">顯示預測的結果。</span><span class="sxs-lookup"><span data-stu-id="2aee5-276">Displays the predicted results.</span></span>

2. <span data-ttu-id="2aee5-277">請使用下列程式碼，在緊接著 `UseModelWithSingleItem()` 方法呼叫底下，從 `Main` 方法新增對新方法的呼叫：</span><span class="sxs-lookup"><span data-stu-id="2aee5-277">Add a call to the new method from the `Main` method, right under the `UseModelWithSingleItem()` method call, using the following code:</span></span>

    [!code-csharp[CallPredictModelBatchItems](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CallUseModelWithBatchItems "Call the CallUseModelWithBatchItems method")]

3. <span data-ttu-id="2aee5-278">新增一些評論以測試 `UseModelWithBatchItems()` 方法中定型模型的預測：</span><span class="sxs-lookup"><span data-stu-id="2aee5-278">Add some comments to test the trained model's predictions in the `UseModelWithBatchItems()` method:</span></span>

    [!code-csharp[PredictionData](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#CreateTestIssues "Create test data for predictions")]

### <a name="predict-comment-sentiment"></a><span data-ttu-id="2aee5-279">預測評論情感</span><span class="sxs-lookup"><span data-stu-id="2aee5-279">Predict comment sentiment</span></span>

<span data-ttu-id="2aee5-280">利用 [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) 方法，使用該模型來預測評論資料情感：</span><span class="sxs-lookup"><span data-stu-id="2aee5-280">Use the model to predict the comment data sentiment using the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method:</span></span>

[!code-csharp[Predict](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#Prediction "Create predictions of sentiments")]

### <a name="combine-and-display-the-predictions"></a><span data-ttu-id="2aee5-281">合併並顯示預測</span><span class="sxs-lookup"><span data-stu-id="2aee5-281">Combine and display the predictions</span></span>

<span data-ttu-id="2aee5-282">使用下列程式碼來為預測建立標頭：</span><span class="sxs-lookup"><span data-stu-id="2aee5-282">Create a header for the predictions using the following code:</span></span>

[!code-csharp[OutputHeaders](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#AddInfoMessage "Display prediction outputs")]

<span data-ttu-id="2aee5-283">因為 `SentimentPrediction` 繼承自 `SentimentData`，所以 `Transform()` 方法會使用預測欄位填入 `SentimentText`。</span><span class="sxs-lookup"><span data-stu-id="2aee5-283">Because `SentimentPrediction` is inherited from `SentimentData`, the `Transform()` method populated `SentimentText` with the predicted fields.</span></span> <span data-ttu-id="2aee5-284">隨著 ML.NET 處理的進行，每個元件都會新增資料行，使其易於顯示結果：</span><span class="sxs-lookup"><span data-stu-id="2aee5-284">As the ML.NET process processes, each component adds columns, and this makes it easy to display the results:</span></span>

[!code-csharp[DisplayPredictions](~/samples/snippets/machine-learning/SentimentAnalysis/csharp/Program.cs#DisplayResults "Display the predictions")]

## <a name="results"></a><span data-ttu-id="2aee5-285">結果</span><span class="sxs-lookup"><span data-stu-id="2aee5-285">Results</span></span>

<span data-ttu-id="2aee5-286">您的結果應該與以下類似。</span><span class="sxs-lookup"><span data-stu-id="2aee5-286">Your results should be similar to the following.</span></span> <span data-ttu-id="2aee5-287">處理期間會顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="2aee5-287">During processing, messages are displayed.</span></span> <span data-ttu-id="2aee5-288">您可能會看到警告或處理訊息。</span><span class="sxs-lookup"><span data-stu-id="2aee5-288">You may see warnings, or processing messages.</span></span> <span data-ttu-id="2aee5-289">為了清晰起見，下列結果中已將這些都移除。</span><span class="sxs-lookup"><span data-stu-id="2aee5-289">These have been removed from the following results for clarity.</span></span>

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

<span data-ttu-id="2aee5-290">恭喜！</span><span class="sxs-lookup"><span data-stu-id="2aee5-290">Congratulations!</span></span> <span data-ttu-id="2aee5-291">您現在已成功建置可對訊息情感進行分類和預測的機器學習模型。</span><span class="sxs-lookup"><span data-stu-id="2aee5-291">You've now successfully built a machine learning model for classifying and predicting messages sentiment.</span></span>

<span data-ttu-id="2aee5-292">建立成功的模型是一個需要反覆嘗試的程序。</span><span class="sxs-lookup"><span data-stu-id="2aee5-292">Building successful models is an iterative process.</span></span> <span data-ttu-id="2aee5-293">此模型一開始的品質較低，因為此教學課程是使用小型的資料集來提供快速的模型定型。</span><span class="sxs-lookup"><span data-stu-id="2aee5-293">This model has initial lower quality as the tutorial uses small datasets to provide quick model training.</span></span> <span data-ttu-id="2aee5-294">如果您對模型品質不滿意，則可以嘗試通過提供較大的訓練資料集或為每個演算法選擇具有不同[超參數](../resources/glossary.md#hyperparameter)的不同訓練演算法來改進模型品質。</span><span class="sxs-lookup"><span data-stu-id="2aee5-294">If you aren't satisfied with the model quality, you can try to improve it by providing larger training datasets or by choosing different training algorithms with different [hyper-parameters](../resources/glossary.md#hyperparameter) for each algorithm.</span></span>

<span data-ttu-id="2aee5-295">您可以在 [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) 存放庫中找到本教學課程的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="2aee5-295">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) repository.</span></span>

## <a name="next-steps"></a><span data-ttu-id="2aee5-296">後續步驟</span><span class="sxs-lookup"><span data-stu-id="2aee5-296">Next steps</span></span>

<span data-ttu-id="2aee5-297">在本教學課程中，您已了解如何：</span><span class="sxs-lookup"><span data-stu-id="2aee5-297">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="2aee5-298">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="2aee5-298">Create a console application</span></span>
> - <span data-ttu-id="2aee5-299">準備資料</span><span class="sxs-lookup"><span data-stu-id="2aee5-299">Prepare data</span></span>
> - <span data-ttu-id="2aee5-300">載入資料</span><span class="sxs-lookup"><span data-stu-id="2aee5-300">Load the data</span></span>
> - <span data-ttu-id="2aee5-301">建置和定型模型</span><span class="sxs-lookup"><span data-stu-id="2aee5-301">Build and train the model</span></span>
> - <span data-ttu-id="2aee5-302">評估模型</span><span class="sxs-lookup"><span data-stu-id="2aee5-302">Evaluate the model</span></span>
> - <span data-ttu-id="2aee5-303">使用模型來進行預測</span><span class="sxs-lookup"><span data-stu-id="2aee5-303">Use the model to make a prediction</span></span>
> - <span data-ttu-id="2aee5-304">查看結果</span><span class="sxs-lookup"><span data-stu-id="2aee5-304">See the results</span></span>

<span data-ttu-id="2aee5-305">前進到下一個教學課程來深入了解</span><span class="sxs-lookup"><span data-stu-id="2aee5-305">Advance to the next tutorial to learn more</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="2aee5-306">問題分類</span><span class="sxs-lookup"><span data-stu-id="2aee5-306">Issue Classification</span></span>](github-issue-classification.md)
