---
title: 使用 .NET 進行 Apache Spark 和 ML.NET 教學課程的情感分析
description: 在本教學課程中，您將瞭解如何使用 ML.NET 搭配 .NET 以進行情感分析的 Apache Spark。
author: mamccrea
ms.author: mamccrea
ms.date: 10/09/2020
ms.topic: tutorial
ms.openlocfilehash: 16b4d34e4c581da2cd0ba798d87e53ccfc49f0e9
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2020
ms.locfileid: "91954889"
---
# <a name="tutorial-sentiment-analysis-with-net-for-apache-spark-and-mlnet"></a><span data-ttu-id="4a595-103">教學課程：使用 .NET 進行 Apache Spark 和 ML.NET 的情感分析</span><span class="sxs-lookup"><span data-stu-id="4a595-103">Tutorial: Sentiment analysis with .NET for Apache Spark and ML.NET</span></span>

<span data-ttu-id="4a595-104">本教學課程會教您如何使用 ML.NET 和 .NET 進行 Apache Spark 的線上審核情感分析。</span><span class="sxs-lookup"><span data-stu-id="4a595-104">This tutorial teaches you how to do sentiment analysis of online reviews using ML.NET and .NET for Apache Spark.</span></span> <span data-ttu-id="4a595-105">[ML.NET](http://dot.net/ml) 是免費的跨平臺開放原始碼機器學習架構。</span><span class="sxs-lookup"><span data-stu-id="4a595-105">[ML.NET](http://dot.net/ml) is a free, cross-platform, open-source machine learning framework.</span></span> <span data-ttu-id="4a595-106">您可以使用 ML.NET 搭配 .NET 進行 Apache Spark，以調整機器學習演算法的定型和預測。</span><span class="sxs-lookup"><span data-stu-id="4a595-106">You can use ML.NET with .NET for Apache Spark to scale the training and prediction of machine learning algorithms.</span></span>

<span data-ttu-id="4a595-107">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="4a595-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="4a595-108">在 Visual Studio 中使用 ML.NET 模型產生器建立情感分析模型。</span><span class="sxs-lookup"><span data-stu-id="4a595-108">Create a sentiment analysis model using ML.NET Model Builder in Visual Studio.</span></span>
> * <span data-ttu-id="4a595-109">為 Apache Spark 主控台應用程式建立 .NET。</span><span class="sxs-lookup"><span data-stu-id="4a595-109">Create a .NET for Apache Spark console app.</span></span>
> * <span data-ttu-id="4a595-110">撰寫和執行使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="4a595-110">Write and implement a user-defined function.</span></span>
> * <span data-ttu-id="4a595-111">針對 Apache Spark 主控台應用程式執行 .NET。</span><span class="sxs-lookup"><span data-stu-id="4a595-111">Run a .NET for Apache Spark console app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4a595-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="4a595-112">Prerequisites</span></span>

* <span data-ttu-id="4a595-113">如果您之前尚未開發 Apache Spark 應用程式的 .NET，請從 [消費者入門教學](get-started.md) 課程開始，以熟悉基本概念。</span><span class="sxs-lookup"><span data-stu-id="4a595-113">If you haven't developed a .NET for Apache Spark application before, start with the [Getting Started tutorial](get-started.md) to become familiar with the basics.</span></span> <span data-ttu-id="4a595-114">繼續進行本教學課程之前，請先完成消費者入門教學課程的所有必要條件。</span><span class="sxs-lookup"><span data-stu-id="4a595-114">Complete all of the prerequisites for the Getting Started tutorial before you continue with this tutorial.</span></span>

* <span data-ttu-id="4a595-115">本教學課程使用 ML.NET 模型產生器 (預覽) ，Visual Studio 提供視覺化介面。</span><span class="sxs-lookup"><span data-stu-id="4a595-115">This tutorial uses the ML.NET Model Builder (preview), a visual interface available in Visual Studio.</span></span> <span data-ttu-id="4a595-116">如果您還沒有 Visual Studio，可以免費 [下載 Visual Studio](https://visualstudio.microsoft.com/downloads/) 的免費版。</span><span class="sxs-lookup"><span data-stu-id="4a595-116">If you don't already have Visual Studio, you can [download the Community version of Visual Studio](https://visualstudio.microsoft.com/downloads/) for free.</span></span>

* <span data-ttu-id="4a595-117">[下載並安裝](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET 模型產生器 (預覽) 。</span><span class="sxs-lookup"><span data-stu-id="4a595-117">[Download and install](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET Model Builder (preview).</span></span>

* <span data-ttu-id="4a595-118">下載 [yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) 並 [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp 評論資料集。</span><span class="sxs-lookup"><span data-stu-id="4a595-118">Download the [yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) and [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp review datasets.</span></span>

## <a name="review-the-data"></a><span data-ttu-id="4a595-119">檢閱資料</span><span class="sxs-lookup"><span data-stu-id="4a595-119">Review the data</span></span>

<span data-ttu-id="4a595-120">Yelp 評論資料集包含有關各種服務的線上 Yelp 評論。</span><span class="sxs-lookup"><span data-stu-id="4a595-120">The Yelp reviews dataset contains online Yelp reviews about various services.</span></span> <span data-ttu-id="4a595-121">開啟 [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) 並注意資料的結構。</span><span class="sxs-lookup"><span data-stu-id="4a595-121">Open [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) and notice the structure of the data.</span></span> <span data-ttu-id="4a595-122">第一個資料行包含審核文字，而第二個數據行包含情感分數。</span><span class="sxs-lookup"><span data-stu-id="4a595-122">The first column contains review text, and the second column contains sentiment scores.</span></span> <span data-ttu-id="4a595-123">如果情感分數是1，則審核是正面的，且如果情感分數為0，則審核為負數。</span><span class="sxs-lookup"><span data-stu-id="4a595-123">If the sentiment score is 1, the review is positive, and if the sentiment score is 0, the review is negative.</span></span>

<span data-ttu-id="4a595-124">下表包含範例資料：</span><span class="sxs-lookup"><span data-stu-id="4a595-124">The following table contains sample data:</span></span>

|<span data-ttu-id="4a595-125">ReviewText</span><span class="sxs-lookup"><span data-stu-id="4a595-125">ReviewText</span></span>|<span data-ttu-id="4a595-126">情感</span><span class="sxs-lookup"><span data-stu-id="4a595-126">Sentiment</span></span>|
|-|-|
|<span data-ttu-id="4a595-127">哇。。。喜歡這個位置。</span><span class="sxs-lookup"><span data-stu-id="4a595-127">Wow... Loved this place.</span></span>|    <span data-ttu-id="4a595-128">1</span><span class="sxs-lookup"><span data-stu-id="4a595-128">1</span></span>|
|<span data-ttu-id="4a595-129">不夠酥脆。</span><span class="sxs-lookup"><span data-stu-id="4a595-129">Crust is not good.</span></span>|    <span data-ttu-id="4a595-130">0</span><span class="sxs-lookup"><span data-stu-id="4a595-130">0</span></span>|

## <a name="build-your-machine-learning-model"></a><span data-ttu-id="4a595-131">建立您的機器學習模型</span><span class="sxs-lookup"><span data-stu-id="4a595-131">Build your machine learning model</span></span>

1. <span data-ttu-id="4a595-132">開啟 Visual Studio，並 ( .NET Core) 建立新的 c # 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="4a595-132">Open Visual Studio and create a new C# Console App (.NET Core).</span></span> <span data-ttu-id="4a595-133">將專案命名為 *MLSparkModel*。</span><span class="sxs-lookup"><span data-stu-id="4a595-133">Name the project *MLSparkModel*.</span></span>

1. <span data-ttu-id="4a595-134">在 **方案總管**中，以滑鼠右鍵按一下 [ *MLSparkModel* ] 專案。</span><span class="sxs-lookup"><span data-stu-id="4a595-134">In **Solution Explorer**, right-click the *MLSparkModel* project.</span></span> <span data-ttu-id="4a595-135">然後選取 [ **新增 > Machine Learning**。</span><span class="sxs-lookup"><span data-stu-id="4a595-135">Then select **Add > Machine Learning**.</span></span>

1. <span data-ttu-id="4a595-136">從 [ML.NET 模型產生器] 中，選取 [ **情感分析** 案例] 磚。</span><span class="sxs-lookup"><span data-stu-id="4a595-136">From the ML.NET Model Builder, select the **Sentiment Analysis** scenario tile.</span></span>

1. <span data-ttu-id="4a595-137">在 [ **加入資料** ] 頁面上，上傳 *yelptrain.csv* 資料集。</span><span class="sxs-lookup"><span data-stu-id="4a595-137">On the **Add data** page, upload the *yelptrain.csv* data set.</span></span>

1. <span data-ttu-id="4a595-138">從 [**要預測**的資料行] 下拉式清單中選擇 [*情感*]。</span><span class="sxs-lookup"><span data-stu-id="4a595-138">Choose *Sentiment* from the **Columns to Predict** dropdown.</span></span>

1. <span data-ttu-id="4a595-139">在 [ **定型** ] 頁面上，將 [定型時間] 設定為 *60 秒* ，然後選取 [ **開始訓練**]。</span><span class="sxs-lookup"><span data-stu-id="4a595-139">On the **Train** page, set the time to train to *60 seconds* and select **Start training**.</span></span> <span data-ttu-id="4a595-140">請注意訓練的**狀態。**</span><span class="sxs-lookup"><span data-stu-id="4a595-140">Notice the status of your training under **Progress**.</span></span>

1. <span data-ttu-id="4a595-141">模型產生器完成定型之後，請 **評估** 定型結果。</span><span class="sxs-lookup"><span data-stu-id="4a595-141">Once Model Builder is finished training, **Evaluate** the training results.</span></span> <span data-ttu-id="4a595-142">您可以 **在下方的** 文字方塊中輸入片語，然後選取 [ **預測** ] 以查看輸出。</span><span class="sxs-lookup"><span data-stu-id="4a595-142">You can type phrases into the text box below **Try your model** and select **Predict** to see the output.</span></span>

1. <span data-ttu-id="4a595-143">選取 [程式 **代碼** ]，然後選取 [ **新增專案** ]，將 ML 模型新增至方案。</span><span class="sxs-lookup"><span data-stu-id="4a595-143">Select **Code** and then select **Add Projects** to add the ML model to the solution.</span></span>

1. <span data-ttu-id="4a595-144">請注意，您的方案中加入了兩個專案： **MLSparkModelML. consoleapp.exe**和**MLSparkModelML。**</span><span class="sxs-lookup"><span data-stu-id="4a595-144">Notice that two projects are added to your solutions: **MLSparkModelML.ConsoleApp** and **MLSparkModelML.Model**.</span></span>

1. <span data-ttu-id="4a595-145">按兩下 *MLSpark* c # 專案，並注意已加入下列專案參考。</span><span class="sxs-lookup"><span data-stu-id="4a595-145">Double-click on your *MLSpark* C# project and notice that the following project reference has been added.</span></span>

   ```xml
   <ItemGroup>
       <ProjectReference Include="..\MLSparkModelML.Model\MLSparkModelML.Model.csproj" />
   </ItemGroup>
   ```

## <a name="create-a-console-app"></a><span data-ttu-id="4a595-146">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="4a595-146">Create a console app</span></span>

<span data-ttu-id="4a595-147">模型產生器會為您建立主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="4a595-147">Model Builder creates a console app for you.</span></span>

1. <span data-ttu-id="4a595-148">以滑鼠右鍵按一下方案總管中的 [ **MLSparkModelML** ]，然後選取 [ **管理 NuGet 套件**]。</span><span class="sxs-lookup"><span data-stu-id="4a595-148">Right-click on **MLSparkModelML.Console** in Solution Explorer, and select **Manage NuGet Packages**.</span></span>

1. <span data-ttu-id="4a595-149">搜尋 **Microsoft Spark** 並安裝套件。</span><span class="sxs-lookup"><span data-stu-id="4a595-149">Search for **Microsoft.Spark** and install the package.</span></span> <span data-ttu-id="4a595-150">模型產生器會為您自動安裝**Microsoft.ML** 。</span><span class="sxs-lookup"><span data-stu-id="4a595-150">**Microsoft.ML** is automatically installed for you by Model Builder.</span></span>

### <a name="create-a-sparksession"></a><span data-ttu-id="4a595-151">建立 SparkSession</span><span class="sxs-lookup"><span data-stu-id="4a595-151">Create a SparkSession</span></span>

1. <span data-ttu-id="4a595-152">開啟**MLSparkModelML. consoleapp.exe**的*Program.cs*檔案。</span><span class="sxs-lookup"><span data-stu-id="4a595-152">Open the *Program.cs* file for **MLSparkModelML.ConsoleApp**.</span></span> <span data-ttu-id="4a595-153">此檔案是由模型產生器自動產生的。</span><span class="sxs-lookup"><span data-stu-id="4a595-153">This file was autogenerated by Model Builder.</span></span> <span data-ttu-id="4a595-154">刪除 `using` 語句、主要 ( # A1 方法的內容，以及 `CreateSingleDataSample` 區域。</span><span class="sxs-lookup"><span data-stu-id="4a595-154">Delete the `using` statements, the contents of the Main() method, and the `CreateSingleDataSample` region.</span></span>

1. <span data-ttu-id="4a595-155">將下列其他 `using` 語句新增至 *Program.cs*頂端：</span><span class="sxs-lookup"><span data-stu-id="4a595-155">Add the following additional `using` statements to the top of the *Program.cs*:</span></span>

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.ML;
   using Microsoft.ML.Data;
   using Microsoft.Spark.Sql;
   using MLSparkModelML.Model;
   ```

1. <span data-ttu-id="4a595-156">將變更 `DATA_FILEPATH` 為您 *yelptest.csv*的路徑。</span><span class="sxs-lookup"><span data-stu-id="4a595-156">Change the `DATA_FILEPATH` to the path of your *yelptest.csv*.</span></span>

1. <span data-ttu-id="4a595-157">將下列程式碼新增至您 `Main` 的方法，以建立新的 `SparkSession` 。</span><span class="sxs-lookup"><span data-stu-id="4a595-157">Add the following code to your `Main` method to create a new `SparkSession`.</span></span> <span data-ttu-id="4a595-158">Spark 會話是使用資料集和資料框架 API 對 Spark 進行程式設計的進入點。</span><span class="sxs-lookup"><span data-stu-id="4a595-158">The Spark Session is the entry point to programming Spark with the Dataset and DataFrame API.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName(".NET for Apache Spark Sentiment Analysis")
        .GetOrCreate();
   ```

   <span data-ttu-id="4a595-159">呼叫上面建立的 *spark* 物件，可讓您存取整個程式中的 Spark 和資料框架功能。</span><span class="sxs-lookup"><span data-stu-id="4a595-159">Calling the *spark* object created above allows you to access Spark and DataFrame functionality throughout your program.</span></span>

### <a name="create-a-dataframe-and-print-to-console"></a><span data-ttu-id="4a595-160">建立資料框架並列印到主控台</span><span class="sxs-lookup"><span data-stu-id="4a595-160">Create a DataFrame and print to console</span></span>

<span data-ttu-id="4a595-161">從 *yelptest.csv* 檔案讀取 Yelp 審核資料 `DataFrame` 。</span><span class="sxs-lookup"><span data-stu-id="4a595-161">Read in the Yelp review data from the *yelptest.csv* file as a `DataFrame`.</span></span> <span data-ttu-id="4a595-162">包含 `header` 和 `inferSchema` 選項。</span><span class="sxs-lookup"><span data-stu-id="4a595-162">Include `header` and `inferSchema` options.</span></span> <span data-ttu-id="4a595-163">選項會將 `header` *yelptest.csv* 的第一行讀取為數據行名稱，而不是資料。</span><span class="sxs-lookup"><span data-stu-id="4a595-163">The `header` option reads the first line of *yelptest.csv* as column names instead of data.</span></span> <span data-ttu-id="4a595-164">`inferSchema`選項會根據資料推斷資料行類型。</span><span class="sxs-lookup"><span data-stu-id="4a595-164">The `inferSchema` option infers column types based on the data.</span></span>

```csharp
DataFrame df = spark
    .ReadStream()
    .Option("header", true)
    .Option("inferSchema", true)
    .Csv(DATA_FILEPATH);

df.Show();
```

### <a name="register-a-user-defined-function"></a><span data-ttu-id="4a595-165">註冊使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="4a595-165">Register a user-defined function</span></span>

<span data-ttu-id="4a595-166">您可以在 Spark 應用程式中使用 Udf （ *使用者定義函式*）來執行資料的計算和分析。</span><span class="sxs-lookup"><span data-stu-id="4a595-166">You can use UDFs, *user-defined functions*, in Spark applications to do calculations and analysis on your data.</span></span> <span data-ttu-id="4a595-167">在本教學課程中，您會使用 ML.NET 搭配 UDF 來評估每個 Yelp 評論。</span><span class="sxs-lookup"><span data-stu-id="4a595-167">In this tutorial, you use ML.NET with a UDF to evaluate each Yelp review.</span></span>

<span data-ttu-id="4a595-168">將下列程式碼新增至您 `Main` 的方法，以註冊名為的 UDF `MLudf` 。</span><span class="sxs-lookup"><span data-stu-id="4a595-168">Add the following code to your `Main` method to register a UDF called `MLudf`.</span></span>

```csharp
spark.Udf()
    .Register<string, bool>("MLudf", predict);
```

<span data-ttu-id="4a595-169">此 UDF 會採用 Yelp 審核字串做為輸入，並分別針對正面或負面情緒輸出 true 或 false。</span><span class="sxs-lookup"><span data-stu-id="4a595-169">This UDF takes a Yelp review string as input, and outputs true or false for positive or negative sentiments, respectively.</span></span> <span data-ttu-id="4a595-170">它會使用您在稍後的步驟中定義的 \*predict ( # B1 \* 方法。</span><span class="sxs-lookup"><span data-stu-id="4a595-170">It uses the *predict()* method that you define in a later step.</span></span>

### <a name="use-spark-sql-to-call-the-udf"></a><span data-ttu-id="4a595-171">使用 Spark SQL 來呼叫 UDF</span><span class="sxs-lookup"><span data-stu-id="4a595-171">Use Spark SQL to call the UDF</span></span>

<span data-ttu-id="4a595-172">既然您已讀取資料並納入 ML，請使用 Spark SQL 來呼叫將在資料框架的每個資料列上執行情感分析的 UDF。</span><span class="sxs-lookup"><span data-stu-id="4a595-172">Now that you've read in your data and incorporated ML, use Spark SQL to call the UDF that will run sentiment analysis on each row of your DataFrame.</span></span> <span data-ttu-id="4a595-173">將下列程式碼新增至 `Main` 方法：</span><span class="sxs-lookup"><span data-stu-id="4a595-173">Add the following code to your `Main` method:</span></span>

```csharp
// Use Spark SQL to call ML.NET UDF
// Display results of sentiment analysis on reviews
df.CreateOrReplaceTempView("Reviews");
DataFrame sqlDf = spark.Sql("SELECT ReviewText, MLudf(ReviewText) FROM Reviews");
sqlDf.Show();

// Print out first 20 rows of data
// Prevent data getting cut off by setting truncate = 0
sqlDf.Show(20, 0, false);

spark.Stop();
```

### <a name="create-predict-method"></a><span data-ttu-id="4a595-174">建立 predict ( # A1 方法</span><span class="sxs-lookup"><span data-stu-id="4a595-174">Create predict() method</span></span>

<span data-ttu-id="4a595-175">在您的方法之前加入下列程式碼 `Main()` 。</span><span class="sxs-lookup"><span data-stu-id="4a595-175">Add the following code before your `Main()` method.</span></span> <span data-ttu-id="4a595-176">此程式碼類似于 *ConsumeModel.cs*中的模型產生器所產生的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4a595-176">This code is similar to what is produced by Model Builder in *ConsumeModel.cs*.</span></span> <span data-ttu-id="4a595-177">將此方法移至主控台會在您每次執行應用程式時載入模型載入。</span><span class="sxs-lookup"><span data-stu-id="4a595-177">Moving this method to your console loads the model loading each time you run your app.</span></span>

```csharp
private static readonly PredictionEngine<ModelInput, ModelOutput> _predictionEngine;

static Program()
{
    MLContext mlContext = new MLContext();
    ITransformer model = mlContext.Model.Load("MLModel.zip", out DataViewSchema schema);
    _predictionEngine = mlContext.Model.CreatePredictionEngine<ModelInput, ModelOutput>(model);
}

static bool predict(string text)
{
    ModelInput input = new ModelInput
    {
        ReviewText = text
    };

    return _predictionEngine.Predict(input).Prediction;
}
```

## <a name="add-the-model-to-your-console-app"></a><span data-ttu-id="4a595-178">將模型新增至您的主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="4a595-178">Add the model to your console app</span></span>

<span data-ttu-id="4a595-179">在方案總管中，從**MLSparkModelML**專案複製*MLModel.zip*檔案，然後將它貼入**MLSparkModelML. consoleapp.exe**專案中。</span><span class="sxs-lookup"><span data-stu-id="4a595-179">In Solution Explorer, copy the *MLModel.zip* file from the **MLSparkModelML.Model** project and paste it in the **MLSparkModelML.ConsoleApp** project.</span></span> <span data-ttu-id="4a595-180">參考會自動加入至 *MLSparkModelML. consoleapp.exe*。</span><span class="sxs-lookup"><span data-stu-id="4a595-180">A reference is automatically added in *MLSparkModelML.ConsoleApp.csproj*.</span></span>

## <a name="run-your-code"></a><span data-ttu-id="4a595-181">執行您的程式碼</span><span class="sxs-lookup"><span data-stu-id="4a595-181">Run your code</span></span>

<span data-ttu-id="4a595-182">使用 `spark-submit` 來執行您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4a595-182">Use `spark-submit` to run your code.</span></span> <span data-ttu-id="4a595-183">使用命令提示字元流覽至您的主控台應用程式根資料夾，然後執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="4a595-183">Navigate to your console app's root folder using the command prompt and run the following commands.</span></span>

<span data-ttu-id="4a595-184">首先，請清除併發布您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4a595-184">First, clean and publish your app.</span></span>

```dotnetcli
dotnet clean
dotnet publish
```

<span data-ttu-id="4a595-185">然後，流覽至主控台應用程式的 [發佈] 資料夾，然後執行下列 `spark-submit` 命令。</span><span class="sxs-lookup"><span data-stu-id="4a595-185">Then navigate to the console app's publish folder and run the following `spark-submit` command.</span></span> <span data-ttu-id="4a595-186">請記得使用您的 Microsoft Spark jar 檔案的實際路徑來更新命令。</span><span class="sxs-lookup"><span data-stu-id="4a595-186">Remember to update the command with the actual path of your Microsoft Spark jar file.</span></span>

```dotnetcli
%SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local microsoft-spark-2.4.x-0.10.0.jar dotnet MLSparkModelML.ConsoleApp.dll
```

## <a name="get-the-code"></a><span data-ttu-id="4a595-187">取得程式碼</span><span class="sxs-lookup"><span data-stu-id="4a595-187">Get the code</span></span>

<span data-ttu-id="4a595-188">本教學課程類似于 [情感分析具有 Big Data](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment) 範例的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4a595-188">This tutorial is similar to the code from the [Sentiment Analysis with Big Data](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment) example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4a595-189">後續步驟</span><span class="sxs-lookup"><span data-stu-id="4a595-189">Next steps</span></span>

<span data-ttu-id="4a595-190">前進到下一篇文章，以瞭解如何使用 .NET 進行結構化串流以進行 Apache Spark。</span><span class="sxs-lookup"><span data-stu-id="4a595-190">Advance to the next article to learn how to do Structured Streaming with .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="4a595-191">教學課程：使用 .NET 進行 Apache Spark 的結構化串流</span><span class="sxs-lookup"><span data-stu-id="4a595-191">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>](streaming.md)
