---
title: 情緒分析與 .NET 的 Apache Spark 和ML.NET教程
description: 在本教程中，您將學習如何將 ML.NET與 .NET 一起用於 Apache Spark 進行情緒分析。
author: mamccrea
ms.author: mamccrea
ms.date: 03/25/2019
ms.topic: tutorial
ms.openlocfilehash: cdd1214c26a5d5a4b159df3a396ec6f36b9fc0dd
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391255"
---
# <a name="tutorial-sentiment-analysis-with-net-for-apache-spark-and-mlnet"></a><span data-ttu-id="ded66-103">教程：使用 .NET 進行情緒分析，用於 Apache Spark 和ML.NET</span><span class="sxs-lookup"><span data-stu-id="ded66-103">Tutorial: Sentiment analysis with .NET for Apache Spark and ML.NET</span></span>

<span data-ttu-id="ded66-104">本教程教您如何使用ML.NET和 .NET 進行 Apache Spark 的線上評論情緒分析。</span><span class="sxs-lookup"><span data-stu-id="ded66-104">This tutorial teaches you how to do sentiment analysis of online reviews using ML.NET and .NET for Apache Spark.</span></span> <span data-ttu-id="ded66-105">[ML.NET](http://dot.net/ml)是一個免費的跨平臺、開源機器學習框架。</span><span class="sxs-lookup"><span data-stu-id="ded66-105">[ML.NET](http://dot.net/ml) is a free, cross-platform, open-source machine learning framework.</span></span> <span data-ttu-id="ded66-106">您可以使用 ML.NET 與 .NET 的 Apache Spark 一起擴展機器學習演算法的訓練和預測。</span><span class="sxs-lookup"><span data-stu-id="ded66-106">You can use ML.NET with .NET for Apache Spark to scale the training and prediction of machine learning algorithms.</span></span>

<span data-ttu-id="ded66-107">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="ded66-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="ded66-108">在視覺化工作室中使用ML.NET模型產生器創建情緒分析模型。</span><span class="sxs-lookup"><span data-stu-id="ded66-108">Create a sentiment analysis model using ML.NET Model Builder in Visual Studio.</span></span>
> * <span data-ttu-id="ded66-109">為 Apache Spark 主控台應用創建 .NET。</span><span class="sxs-lookup"><span data-stu-id="ded66-109">Create a .NET for Apache Spark console app.</span></span>
> * <span data-ttu-id="ded66-110">編寫並實現使用者定義的函數。</span><span class="sxs-lookup"><span data-stu-id="ded66-110">Write and implement a user-defined function.</span></span>
> * <span data-ttu-id="ded66-111">為 Apache Spark 主控台應用運行 .NET。</span><span class="sxs-lookup"><span data-stu-id="ded66-111">Run a .NET for Apache Spark console app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ded66-112">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="ded66-112">Prerequisites</span></span>

* <span data-ttu-id="ded66-113">如果您以前沒有為 Apache Spark 應用程式開發 .NET，請從[入門教程](get-started.md)開始熟悉基礎知識。</span><span class="sxs-lookup"><span data-stu-id="ded66-113">If you haven't developed a .NET for Apache Spark application before, start with the [Getting Started tutorial](get-started.md) to become familiar with the basics.</span></span> <span data-ttu-id="ded66-114">在繼續本教程之前，請完成入門教程的所有先決條件。</span><span class="sxs-lookup"><span data-stu-id="ded66-114">Complete all of the prerequisites for the Getting Started tutorial before you continue with this tutorial.</span></span>

* <span data-ttu-id="ded66-115">本教程使用ML.NET模型產生器（預覽），視覺化工作室中提供的視覺介面。</span><span class="sxs-lookup"><span data-stu-id="ded66-115">This tutorial uses the ML.NET Model Builder (preview), a visual interface available in Visual Studio.</span></span> <span data-ttu-id="ded66-116">如果您還沒有 Visual Studio，您可以免費[下載視覺工作室的社區版本](https://visualstudio.microsoft.com/downloads/)。</span><span class="sxs-lookup"><span data-stu-id="ded66-116">If you don't already have Visual Studio, you can [download the Community version of Visual Studio](https://visualstudio.microsoft.com/downloads/) for free.</span></span>

* <span data-ttu-id="ded66-117">[下載並安裝](https://marketplace.visualstudio.com/items?itemName=MLNET.07)ML.NET模型產生器（預覽）。</span><span class="sxs-lookup"><span data-stu-id="ded66-117">[Download and install](https://marketplace.visualstudio.com/items?itemName=MLNET.07) ML.NET Model Builder (preview).</span></span>

* <span data-ttu-id="ded66-118">下載[yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv)和[yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp 審核資料集。</span><span class="sxs-lookup"><span data-stu-id="ded66-118">Download the [yelptest.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptest.csv) and [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) Yelp review datasets.</span></span>

## <a name="review-the-data"></a><span data-ttu-id="ded66-119">檢閱資料</span><span class="sxs-lookup"><span data-stu-id="ded66-119">Review the data</span></span>

<span data-ttu-id="ded66-120">Yelp 評論資料集包含有關各種服務的線上 Yelp 評論。</span><span class="sxs-lookup"><span data-stu-id="ded66-120">The Yelp reviews dataset contains online Yelp reviews about various services.</span></span> <span data-ttu-id="ded66-121">打開[yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv)並注意資料的結構。</span><span class="sxs-lookup"><span data-stu-id="ded66-121">Open [yelptrain.csv](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment/Resources/yelptrain.csv) and notice the structure of the data.</span></span> <span data-ttu-id="ded66-122">第一列包含審閱文本，第二列包含情緒分數。</span><span class="sxs-lookup"><span data-stu-id="ded66-122">The first column contains review text, and the second column contains sentiment scores.</span></span> <span data-ttu-id="ded66-123">如果情緒評分為 1，則審核為正值，如果情緒評分為 0，則審核為負數。</span><span class="sxs-lookup"><span data-stu-id="ded66-123">If the sentiment score is 1, the review is positive, and if the sentiment score is 0, the review is negative.</span></span>

<span data-ttu-id="ded66-124">下表包含示例資料：</span><span class="sxs-lookup"><span data-stu-id="ded66-124">The following table contains sample data:</span></span>

|<span data-ttu-id="ded66-125">評論文本</span><span class="sxs-lookup"><span data-stu-id="ded66-125">ReviewText</span></span>|<span data-ttu-id="ded66-126">情感</span><span class="sxs-lookup"><span data-stu-id="ded66-126">Sentiment</span></span>|
|-|-|
|<span data-ttu-id="ded66-127">哇。。。喜歡這個地方</span><span class="sxs-lookup"><span data-stu-id="ded66-127">Wow... Loved this place.</span></span>|    <span data-ttu-id="ded66-128">1</span><span class="sxs-lookup"><span data-stu-id="ded66-128">1</span></span>|
|<span data-ttu-id="ded66-129">不夠酥脆。</span><span class="sxs-lookup"><span data-stu-id="ded66-129">Crust is not good.</span></span>|    <span data-ttu-id="ded66-130">0</span><span class="sxs-lookup"><span data-stu-id="ded66-130">0</span></span>|

## <a name="build-your-machine-learning-model"></a><span data-ttu-id="ded66-131">構建機器學習模型</span><span class="sxs-lookup"><span data-stu-id="ded66-131">Build your machine learning model</span></span>

1. <span data-ttu-id="ded66-132">打開視覺化工作室並創建新的 C# 主控台應用程式 （.NET 核心）。</span><span class="sxs-lookup"><span data-stu-id="ded66-132">Open Visual Studio and create a new C# Console App (.NET Core).</span></span> <span data-ttu-id="ded66-133">命名專案*MLSparkModel。*</span><span class="sxs-lookup"><span data-stu-id="ded66-133">Name the project *MLSparkModel*.</span></span>

1. <span data-ttu-id="ded66-134">在**解決方案資源管理器中**，按右鍵*MLSparkModel*專案。</span><span class="sxs-lookup"><span data-stu-id="ded66-134">In **Solution Explorer**, right-click the *MLSparkModel* project.</span></span> <span data-ttu-id="ded66-135">然後選擇 **"添加>機器學習**"。</span><span class="sxs-lookup"><span data-stu-id="ded66-135">Then select **Add > Machine Learning**.</span></span>

1. <span data-ttu-id="ded66-136">在模型產生器ML.NET，選擇**情緒分析**方案磁貼。</span><span class="sxs-lookup"><span data-stu-id="ded66-136">From the ML.NET Model Builder, select the **Sentiment Analysis** scenario tile.</span></span>

1. <span data-ttu-id="ded66-137">在 **"添加資料"** 頁上，上載*yelptrain.csv*資料集。</span><span class="sxs-lookup"><span data-stu-id="ded66-137">On the **Add data** page, upload the *yelptrain.csv* data set.</span></span>

1. <span data-ttu-id="ded66-138">從"列 \*"中選擇"情緒"\***以預測**下拉清單。</span><span class="sxs-lookup"><span data-stu-id="ded66-138">Choose *Sentiment* from the **Columns to Predict** dropdown.</span></span>

1. <span data-ttu-id="ded66-139">在 **"火車"** 頁上，將訓練時間設置為*60 秒*，然後選擇 **"開始訓練**"。</span><span class="sxs-lookup"><span data-stu-id="ded66-139">On the **Train** page, set the time to train to *60 seconds* and select **Start training**.</span></span> <span data-ttu-id="ded66-140">請注意"**進度**"下的培訓狀態。</span><span class="sxs-lookup"><span data-stu-id="ded66-140">Notice the status of your training under **Progress**.</span></span>

1. <span data-ttu-id="ded66-141">模型產生器完成培訓後，**評估**培訓結果。</span><span class="sxs-lookup"><span data-stu-id="ded66-141">Once Model Builder is finished training, **Evaluate** the training results.</span></span> <span data-ttu-id="ded66-142">您可以在下面的文字方塊中鍵入短語 **"嘗試模型\*\*\*\*"，然後選擇"預測"** 以查看輸出。</span><span class="sxs-lookup"><span data-stu-id="ded66-142">You can type phrases into the text box below **Try your model** and select **Predict** to see the output.</span></span>

1. <span data-ttu-id="ded66-143">選擇 **"代碼"，** 然後選擇 **"添加專案**"以將 ML 模型添加到解決方案。</span><span class="sxs-lookup"><span data-stu-id="ded66-143">Select **Code** and then select **Add Projects** to add the ML model to the solution.</span></span>

1. <span data-ttu-id="ded66-144">請注意，您的解決方案中添加了兩個專案 **：MLSparkModelML.ConsoleApp**和**MLSparkModelML.Model.Model.Model.**</span><span class="sxs-lookup"><span data-stu-id="ded66-144">Notice that two projects are added to your solutions: **MLSparkModelML.ConsoleApp** and **MLSparkModelML.Model**.</span></span>

1. <span data-ttu-id="ded66-145">按兩下*您的 MLSpark* C++ 專案，並注意到添加了以下專案參考。</span><span class="sxs-lookup"><span data-stu-id="ded66-145">Double-click on your *MLSpark* C# project and notice that the following project reference has been added.</span></span>

   ```xml
   <ItemGroup>
       <ProjectReference Include="..\MLSparkModelML.Model\MLSparkModelML.Model.csproj" />
   </ItemGroup>
   ```

## <a name="create-a-console-app"></a><span data-ttu-id="ded66-146">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="ded66-146">Create a console app</span></span>

<span data-ttu-id="ded66-147">模型產生器為您創建一個主控台應用。</span><span class="sxs-lookup"><span data-stu-id="ded66-147">Model Builder creates a console app for you.</span></span>

1. <span data-ttu-id="ded66-148">按右鍵解決方案資源管理器中的**MLSparkModelML.主控台**，然後選擇 **"管理 NuGet 包**"。</span><span class="sxs-lookup"><span data-stu-id="ded66-148">Right-click on **MLSparkModelML.Console** in Solution Explorer, and select **Manage NuGet Packages**.</span></span>

1. <span data-ttu-id="ded66-149">搜索**Microsoft.Spark**並安裝套裝軟體。</span><span class="sxs-lookup"><span data-stu-id="ded66-149">Search for **Microsoft.Spark** and install the package.</span></span> <span data-ttu-id="ded66-150">模型產生器會自動為您安裝**Microsoft.ML。**</span><span class="sxs-lookup"><span data-stu-id="ded66-150">**Microsoft.ML** is automatically installed for you by Model Builder.</span></span>

### <a name="create-a-sparksession"></a><span data-ttu-id="ded66-151">創建火花會話</span><span class="sxs-lookup"><span data-stu-id="ded66-151">Create a SparkSession</span></span>

1. <span data-ttu-id="ded66-152">打開**MLSparkModelML.ConsoleApp**的*Program.cs*檔。</span><span class="sxs-lookup"><span data-stu-id="ded66-152">Open the *Program.cs* file for **MLSparkModelML.ConsoleApp**.</span></span> <span data-ttu-id="ded66-153">此檔由模型產生器自動生成。</span><span class="sxs-lookup"><span data-stu-id="ded66-153">This file was autogenerated by Model Builder.</span></span> <span data-ttu-id="ded66-154">刪除語句`using`、Main（） 方法的內容以及`CreateSingleDataSample`區域。</span><span class="sxs-lookup"><span data-stu-id="ded66-154">Delete the `using` statements, the contents of the Main() method, and the `CreateSingleDataSample` region.</span></span>

1. <span data-ttu-id="ded66-155">將以下附加`using`語句添加到*Program.cs*的頂部：</span><span class="sxs-lookup"><span data-stu-id="ded66-155">Add the following additional `using` statements to the top of the *Program.cs*:</span></span>

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.ML;
   using Microsoft.ML.Data;
   using Microsoft.Spark.Sql;
   using MLSparkModelML.Model;
   ```

1. <span data-ttu-id="ded66-156">將`DATA_FILEPATH`更改為*yelptest.csv*的路徑。</span><span class="sxs-lookup"><span data-stu-id="ded66-156">Change the `DATA_FILEPATH` to the path of your *yelptest.csv*.</span></span>

1. <span data-ttu-id="ded66-157">將以下代碼添加到方法`Main`以創建新的`SparkSession`。</span><span class="sxs-lookup"><span data-stu-id="ded66-157">Add the following code to your `Main` method to create a new `SparkSession`.</span></span> <span data-ttu-id="ded66-158">Spark 會話是使用資料集和資料幀 API 程式設計 Spark 的進入點。</span><span class="sxs-lookup"><span data-stu-id="ded66-158">The Spark Session is the entry point to programming Spark with the Dataset and DataFrame API.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName(".NET for Apache Spark Sentiment Analysis")
        .GetOrCreate();
   ```

   <span data-ttu-id="ded66-159">調用上面創建的*火花*物件允許您在整個程式中訪問 Spark 和 DataFrame 功能。</span><span class="sxs-lookup"><span data-stu-id="ded66-159">Calling the *spark* object created above allows you to access Spark and DataFrame functionality throughout your program.</span></span>

### <a name="create-a-dataframe-and-print-to-console"></a><span data-ttu-id="ded66-160">創建資料幀並列印到主控台</span><span class="sxs-lookup"><span data-stu-id="ded66-160">Create a DataFrame and print to console</span></span>

<span data-ttu-id="ded66-161">在 Yelp 審查資料中從*yelptest.csv*檔中`DataFrame`讀取為 。</span><span class="sxs-lookup"><span data-stu-id="ded66-161">Read in the Yelp review data from the *yelptest.csv* file as a `DataFrame`.</span></span> <span data-ttu-id="ded66-162">包括`header`和`inferSchema`選項。</span><span class="sxs-lookup"><span data-stu-id="ded66-162">Include `header` and `inferSchema` options.</span></span> <span data-ttu-id="ded66-163">該`header`選項將*yelptest.csv*的第一行顯示為列名稱而不是資料。</span><span class="sxs-lookup"><span data-stu-id="ded66-163">The `header` option reads the first line of *yelptest.csv* as column names instead of data.</span></span> <span data-ttu-id="ded66-164">選項`inferSchema`根據資料推斷列類型。</span><span class="sxs-lookup"><span data-stu-id="ded66-164">The `inferSchema` option infers column types based on the data.</span></span>

```csharp
DataFrame df = spark
    .ReadStream()
    .Option("header", true)
    .Option("inferSchema", true)
    .Csv(DATA_FILEPATH);

df.Show();
```

### <a name="register-a-user-defined-function"></a><span data-ttu-id="ded66-165">註冊使用者定義的函數</span><span class="sxs-lookup"><span data-stu-id="ded66-165">Register a user-defined function</span></span>

<span data-ttu-id="ded66-166">您可以在 Spark 應用程式中使用*使用者定義的函數*UdF 對資料進行計算和分析。</span><span class="sxs-lookup"><span data-stu-id="ded66-166">You can use UDFs, *user-defined functions*, in Spark applications to do calculations and analysis on your data.</span></span> <span data-ttu-id="ded66-167">在本教程中，您將ML.NET與 UDF 一起評估每個 Yelp 審核。</span><span class="sxs-lookup"><span data-stu-id="ded66-167">In this tutorial, you use ML.NET with a UDF to evaluate each Yelp review.</span></span>

<span data-ttu-id="ded66-168">將以下代碼添加到方法`Main`以註冊稱為`MLudf`的 UDF。</span><span class="sxs-lookup"><span data-stu-id="ded66-168">Add the following code to your `Main` method to register a UDF called `MLudf`.</span></span>

```csharp
spark.Udf()
    .Register<string, bool>("MLudf", predict);
```

<span data-ttu-id="ded66-169">此 UDF 將 Yelp 審核字串作為輸入，並分別輸出正或負情緒的真或假。</span><span class="sxs-lookup"><span data-stu-id="ded66-169">This UDF takes a Yelp review string as input, and outputs true or false for positive or negative sentiments, respectively.</span></span> <span data-ttu-id="ded66-170">它使用在後面的步驟中定義的*預測（）方法*。</span><span class="sxs-lookup"><span data-stu-id="ded66-170">It uses the *predict()* method that you define in a later step.</span></span>

### <a name="use-spark-sql-to-call-the-udf"></a><span data-ttu-id="ded66-171">使用 Spark SQL 調用 UDF</span><span class="sxs-lookup"><span data-stu-id="ded66-171">Use Spark SQL to call the UDF</span></span>

<span data-ttu-id="ded66-172">現在，您已讀取資料併合並 ML，請使用 Spark SQL 調用 UDF，該 UDF 將在 DataFrame 的每一行上運行情緒分析。</span><span class="sxs-lookup"><span data-stu-id="ded66-172">Now that you've read in your data and incorporated ML, use Spark SQL to call the UDF that will run sentiment analysis on each row of your DataFrame.</span></span> <span data-ttu-id="ded66-173">將下列程式碼新增至 `Main` 方法：</span><span class="sxs-lookup"><span data-stu-id="ded66-173">Add the following code to your `Main` method:</span></span>

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

### <a name="create-predict-method"></a><span data-ttu-id="ded66-174">創建預測（）方法</span><span class="sxs-lookup"><span data-stu-id="ded66-174">Create predict() method</span></span>

<span data-ttu-id="ded66-175">在方法`Main()`之前添加以下代碼。</span><span class="sxs-lookup"><span data-stu-id="ded66-175">Add the following code before your `Main()` method.</span></span> <span data-ttu-id="ded66-176">此代碼類似于模型產生器在*ConsumeModel.cs*中生成的代碼。</span><span class="sxs-lookup"><span data-stu-id="ded66-176">This code is similar to what is produced by Model Builder in *ConsumeModel.cs*.</span></span> <span data-ttu-id="ded66-177">將此方法移動到主控台會載入每次運行應用時載入模型。</span><span class="sxs-lookup"><span data-stu-id="ded66-177">Moving this method to your console loads the model loading each time you run your app.</span></span>

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

## <a name="add-the-model-to-your-console-app"></a><span data-ttu-id="ded66-178">將模型添加到主控台應用</span><span class="sxs-lookup"><span data-stu-id="ded66-178">Add the model to your console app</span></span>

<span data-ttu-id="ded66-179">在解決方案資源管理器中，從**MLSparkModelML.Model.Model**專案複製*MLModel.zip*檔，並將其粘貼到**MLSparkModelML.ConsoleApp**專案中。</span><span class="sxs-lookup"><span data-stu-id="ded66-179">In Solution Explorer, copy the *MLModel.zip* file from the **MLSparkModelML.Model** project and paste it in the **MLSparkModelML.ConsoleApp** project.</span></span> <span data-ttu-id="ded66-180">引用將自動添加到*MLSparkModelML.ConsoleApp.csproj*中。</span><span class="sxs-lookup"><span data-stu-id="ded66-180">A reference is automatically added in *MLSparkModelML.ConsoleApp.csproj*.</span></span>

## <a name="run-your-code"></a><span data-ttu-id="ded66-181">運行代碼</span><span class="sxs-lookup"><span data-stu-id="ded66-181">Run your code</span></span>

<span data-ttu-id="ded66-182">用於`spark-submit`運行代碼。</span><span class="sxs-lookup"><span data-stu-id="ded66-182">Use `spark-submit` to run your code.</span></span> <span data-ttu-id="ded66-183">使用命令提示導航到主控台應用的根資料夾並運行以下命令。</span><span class="sxs-lookup"><span data-stu-id="ded66-183">Navigate to your console app's root folder using the command prompt and run the following commands.</span></span>

<span data-ttu-id="ded66-184">首先，清理併發布應用。</span><span class="sxs-lookup"><span data-stu-id="ded66-184">First, clean and publish your app.</span></span>

```dotnetcli
dotnet clean
dotnet publish
```

<span data-ttu-id="ded66-185">然後導航到主控台應用的發佈資料夾並運行以下`spark-submit`命令。</span><span class="sxs-lookup"><span data-stu-id="ded66-185">Then navigate to the console app's publish folder and run the following `spark-submit` command.</span></span> <span data-ttu-id="ded66-186">請記住使用 Microsoft Spark jar 檔的實際路徑更新該命令。</span><span class="sxs-lookup"><span data-stu-id="ded66-186">Remember to update the command with the actual path of your Microsoft Spark jar file.</span></span>

```dotnetcli
%SPARK_HOME%\bin\spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local microsoft-spark-2.4.x-0.10.0.jar dotnet MLSparkModelML.ConsoleApp.dll
```

## <a name="get-the-code"></a><span data-ttu-id="ded66-187">取得程式碼</span><span class="sxs-lookup"><span data-stu-id="ded66-187">Get the code</span></span>

<span data-ttu-id="ded66-188">本教程類似于["使用大資料進行情緒分析"](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment)示例中的代碼。</span><span class="sxs-lookup"><span data-stu-id="ded66-188">This tutorial is similar to the code from the [Sentiment Analysis with Big Data](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/MachineLearning/Sentiment) example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ded66-189">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ded66-189">Next steps</span></span>

<span data-ttu-id="ded66-190">前進到下一篇文章，瞭解如何使用 .NET 為 Apache Spark 進行結構化流式處理。</span><span class="sxs-lookup"><span data-stu-id="ded66-190">Advance to the next article to learn how to do Structured Streaming with .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="ded66-191">教程：結構化流與 .NET 的 Apache Spark</span><span class="sxs-lookup"><span data-stu-id="ded66-191">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>](streaming.md)
