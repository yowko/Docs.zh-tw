---
title: 使用 .NET 進行批次處理以進行 Apache Spark 教學課程
description: 瞭解如何使用 .NET 進行 Apache Spark 的批次處理。
author: mamccrea
ms.author: mamccrea
ms.date: 10/09/2020
ms.topic: tutorial
ms.openlocfilehash: 666292fa2e9cecbd4e0aacd291f1008810eb257e
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955391"
---
# <a name="tutorial-do-batch-processing-with-net-for-apache-spark"></a><span data-ttu-id="18d2f-103">教學課程：使用 .NET 進行批次處理以進行 Apache Spark</span><span class="sxs-lookup"><span data-stu-id="18d2f-103">Tutorial: Do batch processing with .NET for Apache Spark</span></span>

<span data-ttu-id="18d2f-104">在本教學課程中，您將瞭解如何使用 .NET 進行 Apache Spark 的批次處理。</span><span class="sxs-lookup"><span data-stu-id="18d2f-104">In this tutorial, you learn how to do batch processing using .NET for Apache Spark.</span></span> <span data-ttu-id="18d2f-105">批次處理是待用資料的轉換，這表示來源資料已載入資料儲存區中。</span><span class="sxs-lookup"><span data-stu-id="18d2f-105">Batch processing is the transformation of data at rest, meaning that the source data has already been loaded into data storage.</span></span>

<span data-ttu-id="18d2f-106">批次處理通常是針對需要準備進行進一步分析的大型資料集進行。</span><span class="sxs-lookup"><span data-stu-id="18d2f-106">Batch processing is generally performed over large, flat datasets that need to be prepared for further analysis.</span></span> <span data-ttu-id="18d2f-107">記錄處理和資料倉儲是常見的批次處理案例。</span><span class="sxs-lookup"><span data-stu-id="18d2f-107">Log processing and data warehousing are common batch processing scenarios.</span></span> <span data-ttu-id="18d2f-108">在此案例中，您會分析 GitHub 專案的相關資訊，例如不同專案的分支時間或最近專案的更新方式。</span><span class="sxs-lookup"><span data-stu-id="18d2f-108">In this scenario, you analyze information about GitHub projects, such as the number of time different projects have been forked or how recently projects have been updated.</span></span>

<span data-ttu-id="18d2f-109">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="18d2f-109">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="18d2f-110">建立和執行 Apache Spark 應用程式的 .NET</span><span class="sxs-lookup"><span data-stu-id="18d2f-110">Create and run a .NET for Apache Spark application</span></span>
> * <span data-ttu-id="18d2f-111">將資料讀入資料框架並準備進行分析</span><span class="sxs-lookup"><span data-stu-id="18d2f-111">Read data into a DataFrame and prepare it for analysis</span></span>
> * <span data-ttu-id="18d2f-112">使用 Spark SQL 來處理資料</span><span class="sxs-lookup"><span data-stu-id="18d2f-112">Process the data using Spark SQL</span></span>

## <a name="prerequisites"></a><span data-ttu-id="18d2f-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="18d2f-113">Prerequisites</span></span>

<span data-ttu-id="18d2f-114">如果這是您第一次使用 .NET 進行 Apache Spark，請參閱 [開始使用 .net 進行 Apache Spark](get-started.md) 教學課程，以瞭解如何準備您的環境，並針對 Apache Spark 應用程式執行您的第一個 .net。</span><span class="sxs-lookup"><span data-stu-id="18d2f-114">If this is your first time using .NET for Apache Spark, check out the [Get started with .NET for Apache Spark](get-started.md) tutorial to learn how to prepare your environment and run your first .NET for Apache Spark application.</span></span>

## <a name="download-the-sample-data"></a><span data-ttu-id="18d2f-115">下載範例資料</span><span class="sxs-lookup"><span data-stu-id="18d2f-115">Download the sample data</span></span>

<span data-ttu-id="18d2f-116">[GHTorrent](http://ghtorrent.org/) 會監視所有的公用 GitHub 事件，例如專案、認可和監看員的相關資訊，並將事件和其結構儲存在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="18d2f-116">[GHTorrent](http://ghtorrent.org/) monitors all public GitHub events, such as info about projects, commits, and watchers, and stores the events and their structure in databases.</span></span> <span data-ttu-id="18d2f-117">在不同期間收集的資料會以可下載的封存形式提供。</span><span class="sxs-lookup"><span data-stu-id="18d2f-117">Data collected over different time periods is available as downloadable archives.</span></span> <span data-ttu-id="18d2f-118">因為傾印檔案很大，所以本指南會使用可從 GitHub 下載的傾印檔案 [截斷版本](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) 。</span><span class="sxs-lookup"><span data-stu-id="18d2f-118">Because the dump files are very large, this guide uses a [truncated version of the dump file](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) that can be downloaded from GitHub.</span></span>

> [!NOTE]
> <span data-ttu-id="18d2f-119">GHTorrent 資料集會以雙重授權配置來散發 ([創意的 Commons +](https://wiki.creativecommons.org/wiki/CCPlus)) 。</span><span class="sxs-lookup"><span data-stu-id="18d2f-119">The GHTorrent dataset is distributed under a dual licensing scheme ([Creative Commons +](https://wiki.creativecommons.org/wiki/CCPlus)).</span></span> <span data-ttu-id="18d2f-120">針對非商業用途 (包括（但不限於教育、研究或個人用途) ），資料集會以 [CC BY SA 授權](https://creativecommons.org/licenses/by-sa/4.0/)來散發。</span><span class="sxs-lookup"><span data-stu-id="18d2f-120">For non-commercial uses (including, but not limited to, educational, research or personal uses), the dataset is distributed under the [CC-BY-SA license](https://creativecommons.org/licenses/by-sa/4.0/).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="18d2f-121">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="18d2f-121">Create a console application</span></span>

1. <span data-ttu-id="18d2f-122">在命令提示字元中，執行下列命令以建立新的主控台應用程式：</span><span class="sxs-lookup"><span data-stu-id="18d2f-122">In your command prompt, run the following commands to create a new console application:</span></span>

   ```dotnetcli
   dotnet new console -o mySparkBatchApp
   cd mySparkBatchApp
   ```

   <span data-ttu-id="18d2f-123">此 `dotnet` 命令 `new` 會為您建立類型的應用程式 `console` 。</span><span class="sxs-lookup"><span data-stu-id="18d2f-123">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="18d2f-124">`-o`參數會建立名為*mySparkBatchApp*的目錄，您的應用程式會儲存在此目錄中，並填入必要的檔案。</span><span class="sxs-lookup"><span data-stu-id="18d2f-124">The `-o` parameter creates a directory named *mySparkBatchApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="18d2f-125">此 `cd mySparkBatchApp` 命令會將目錄變更為您剛才建立的應用程式目錄。</span><span class="sxs-lookup"><span data-stu-id="18d2f-125">The `cd mySparkBatchApp` command changes the directory to the app directory you just created.</span></span>

1. <span data-ttu-id="18d2f-126">若要在應用程式中使用 .NET 進行 Apache Spark，請安裝 Microsoft Spark 套件。</span><span class="sxs-lookup"><span data-stu-id="18d2f-126">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="18d2f-127">在主控台中，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="18d2f-127">In your console, run the following command:</span></span>

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="create-a-sparksession"></a><span data-ttu-id="18d2f-128">建立 SparkSession</span><span class="sxs-lookup"><span data-stu-id="18d2f-128">Create a SparkSession</span></span>

1. <span data-ttu-id="18d2f-129">`using`在*mySparkBatchApp*中的*Program.cs*檔案頂端新增下列其他語句。</span><span class="sxs-lookup"><span data-stu-id="18d2f-129">Add the following additional `using` statements to the top of the *Program.cs* file in *mySparkBatchApp*.</span></span>

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. <span data-ttu-id="18d2f-130">將下列程式碼新增至您的專案命名空間。</span><span class="sxs-lookup"><span data-stu-id="18d2f-130">Add the following code to your project namespace.</span></span> <span data-ttu-id="18d2f-131">稍後在程式中，會使用*s_referenceData*來根據日期進行篩選。</span><span class="sxs-lookup"><span data-stu-id="18d2f-131">*s_referenceData* is used later in the program to filter based on date.</span></span>

   ```csharp
   static readonly DateTime s_referenceDate = new DateTime(2015, 10, 20);
   ```

1. <span data-ttu-id="18d2f-132">在 Main 方法內新增下列程式碼，以建立新的 SparkSession。</span><span class="sxs-lookup"><span data-stu-id="18d2f-132">Add the following code inside your Main method to establish a new SparkSession.</span></span> <span data-ttu-id="18d2f-133">SparkSession 是將 Spark 與資料集和資料框架 API 進行程式設計的進入點。</span><span class="sxs-lookup"><span data-stu-id="18d2f-133">The SparkSession is the entry point to programming Spark with the Dataset and DataFrame API.</span></span> <span data-ttu-id="18d2f-134">藉由呼叫 `spark` 物件，您就可以存取整個程式中的 Spark 和資料框架功能。</span><span class="sxs-lookup"><span data-stu-id="18d2f-134">By calling the `spark` object, you can access Spark and DataFrame functionality throughout your program.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("GitHub and Spark Batch")
        .GetOrCreate();
   ```

## <a name="prepare-the-data"></a><span data-ttu-id="18d2f-135">準備資料</span><span class="sxs-lookup"><span data-stu-id="18d2f-135">Prepare the data</span></span>

1. <span data-ttu-id="18d2f-136">將輸入檔讀取到 `DataFrame` ，這是組織成命名資料行的分散式資料集合。</span><span class="sxs-lookup"><span data-stu-id="18d2f-136">Read the input file into a `DataFrame`, which is a distributed collection of data organized into named columns.</span></span> <span data-ttu-id="18d2f-137">您可以透過設定資料的資料行 <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A> 。</span><span class="sxs-lookup"><span data-stu-id="18d2f-137">You can set the columns for your data through <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>.</span></span> <span data-ttu-id="18d2f-138"><xref:Microsoft.Spark.Sql.DataFrame.Show%2A>您可以使用方法，在資料框架中顯示資料。</span><span class="sxs-lookup"><span data-stu-id="18d2f-138">Use the <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> method to display the data in your DataFrame.</span></span> <span data-ttu-id="18d2f-139">請務必將 CSV 檔案路徑更新為您下載的 GitHub 資料的位置。</span><span class="sxs-lookup"><span data-stu-id="18d2f-139">Be sure to update the CSV file path to the location of the GitHub data you downloaded.</span></span>

   ```csharp
   DataFrame projectsDf = spark
       .Read()
       .Schema("id INT, url STRING, owner_id INT, " +
       "name STRING, descriptor STRING, language STRING, " +
       "created_at STRING, forked_from INT, deleted STRING" +
       "updated_at STRING")
       .Csv("filepath");

   projectsDf.Show();
   ```

1. <span data-ttu-id="18d2f-140"><xref:Microsoft.Spark.Sql.DataFrame.Na%2A>您可以使用方法來卸載具有 NA (null) 值的資料列，並使用 <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> 方法來移除資料中的特定資料行。</span><span class="sxs-lookup"><span data-stu-id="18d2f-140">Use the <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> method to drop rows with NA (null) values, and the <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> method to remove certain columns from your data.</span></span> <span data-ttu-id="18d2f-141">如果您嘗試分析與最終分析無關的 null 資料或資料行，這有助於避免錯誤。</span><span class="sxs-lookup"><span data-stu-id="18d2f-141">This helps prevent errors if you try to analyze null data or columns that are not relevant to your final analysis.</span></span>

   ```csharp
   // Drop any rows with NA values
   DataFrameNaFunctions dropEmptyProjects = projectsDf.Na();
   DataFrame cleanedProjects = dropEmptyProjects.Drop("any");

   // Remove unnecessary columns
   cleanedProjects = cleanedProjects.Drop("id", "url", "owner_id");
   cleanedProjects.Show();
   ```

## <a name="analyze-the-data"></a><span data-ttu-id="18d2f-142">分析資料</span><span class="sxs-lookup"><span data-stu-id="18d2f-142">Analyze the data</span></span>

<span data-ttu-id="18d2f-143">Spark SQL 可讓您對資料進行 SQL 呼叫。</span><span class="sxs-lookup"><span data-stu-id="18d2f-143">Spark SQL allows you to make SQL calls on your data.</span></span> <span data-ttu-id="18d2f-144">通常會結合使用者定義函數和 Spark SQL，以將使用者定義函數套用至資料框架的所有資料列。</span><span class="sxs-lookup"><span data-stu-id="18d2f-144">It's common to combine user-defined functions and Spark SQL to apply a user-defined function to all rows of your DataFrame.</span></span>

<span data-ttu-id="18d2f-145">您可以特別呼叫 `spark.Sql` 來模擬在其他類型的應用程式中看到的標準 SQL 呼叫。</span><span class="sxs-lookup"><span data-stu-id="18d2f-145">You can specifically call `spark.Sql` to mimic standard SQL calls seen in other types of apps.</span></span> <span data-ttu-id="18d2f-146">您也可以呼叫方法（例如和）， <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> 以明確地結合、篩選和執行資料的計算。</span><span class="sxs-lookup"><span data-stu-id="18d2f-146">You can also call methods like <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> and <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> to specifically combine, filter, and perform calculations on your data.</span></span>

<span data-ttu-id="18d2f-147">此應用程式的目標是要深入瞭解 GitHub 專案資料。</span><span class="sxs-lookup"><span data-stu-id="18d2f-147">The goal of this app is to gain some insights about the GitHub projects data.</span></span> <span data-ttu-id="18d2f-148">將下列程式碼片段新增至您的程式，以分析資料。</span><span class="sxs-lookup"><span data-stu-id="18d2f-148">Add the following code snippets to your program to analyze the data.</span></span>

1. <span data-ttu-id="18d2f-149">新增下列程式碼區塊，以尋找每個語言已派生的次數。</span><span class="sxs-lookup"><span data-stu-id="18d2f-149">Add the following block of code finds the number of times each language has been forked.</span></span> <span data-ttu-id="18d2f-150">首先，資料會依語言分組。</span><span class="sxs-lookup"><span data-stu-id="18d2f-150">First, the data is grouped by language.</span></span> <span data-ttu-id="18d2f-151">然後，會取得每個語言的平均分支數目。</span><span class="sxs-lookup"><span data-stu-id="18d2f-151">Then, the average number of forks from each language is taken.</span></span>

   ```csharp
   // Average number of times each language has been forked
   DataFrame groupedDF = cleanedProjects
       .GroupBy("language")
       .Agg(Avg(cleanedProjects["forked_from"]);
   ```

1. <span data-ttu-id="18d2f-152">新增下列程式碼區塊，以遞減順序排序平均數的平均數目，以查看哪些語言最具分支。</span><span class="sxs-lookup"><span data-stu-id="18d2f-152">Add the following block of code to order the average number of forks in descending order to see which languages are the most forked.</span></span> <span data-ttu-id="18d2f-153">也就是說，會先顯示最大的分支數目。</span><span class="sxs-lookup"><span data-stu-id="18d2f-153">That is, the largest number of forks will appear first.</span></span>

   ```csharp
   // Sort by most forked languages first
   groupedDF.OrderBy(Desc("avg(forked_from)")).Show();
   ```

1. <span data-ttu-id="18d2f-154">下一個程式碼區塊會顯示最近專案的更新方式。</span><span class="sxs-lookup"><span data-stu-id="18d2f-154">The next block of code shows you how recently projects have been updated.</span></span> <span data-ttu-id="18d2f-155">您可以註冊名為 *MyUDF* 的新使用者定義函數，並將它與在教學課程開頭宣告的日期 *s_referenceDate*比較。</span><span class="sxs-lookup"><span data-stu-id="18d2f-155">You register a new user-defined function called *MyUDF* and compare it with a date, *s_referenceDate*, which was declared at the beginning of the tutorial.</span></span> <span data-ttu-id="18d2f-156">每個專案的日期會與參考日期進行比較。</span><span class="sxs-lookup"><span data-stu-id="18d2f-156">The date for each project is compared against the reference date.</span></span> <span data-ttu-id="18d2f-157">然後，Spark SQL 會用來呼叫每個資料列上的 UDF，以分析資料集中的每個專案。</span><span class="sxs-lookup"><span data-stu-id="18d2f-157">Then, Spark SQL is used to call the UDF on each row of the data to analyze each project in the data set.</span></span>

   ```csharp
   spark.Udf().Register<string, bool>(
       "MyUDF",
       (date) => DateTime.TryParse(date, out DateTime convertedDate) &&
           (convertedDate > s_referenceDate);
   cleanedProjects.CreateOrReplaceTempView("dateView");

   DataFrame dateDf = spark.Sql(
       "SELECT *, MyUDF(dateView.updated_at) AS datebefore FROM dateView");
   dateDf.Show();
   ```

1. <span data-ttu-id="18d2f-158">呼叫 `spark.Stop()` 以結束 SparkSession。</span><span class="sxs-lookup"><span data-stu-id="18d2f-158">Call `spark.Stop()` to end the SparkSession.</span></span>

## <a name="use-spark-submit-to-run-your-app"></a><span data-ttu-id="18d2f-159">使用 spark 提交來執行您的應用程式</span><span class="sxs-lookup"><span data-stu-id="18d2f-159">Use spark-submit to run your app</span></span>

1. <span data-ttu-id="18d2f-160">使用下列命令來建立您的 .NET 應用程式：</span><span class="sxs-lookup"><span data-stu-id="18d2f-160">Use the following command to build your .NET app:</span></span>

   ```dotnetcli
   dotnet build
   ```

1. <span data-ttu-id="18d2f-161">使用執行您的應用程式 `spark-submit` 。</span><span class="sxs-lookup"><span data-stu-id="18d2f-161">Run your app with `spark-submit`.</span></span> <span data-ttu-id="18d2f-162">請務必使用 Microsoft Spark jar 檔案的實際路徑來更新下列命令。</span><span class="sxs-lookup"><span data-stu-id="18d2f-162">Be sure to update the following command with the actual paths to your Microsoft Spark jar file.</span></span>

   ```console
   spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /<path>/to/microsoft-spark-<version>.jar dotnet /<path>/to/netcoreapp<version>/GitHubProjects.dll
   ```

## <a name="get-the-code"></a><span data-ttu-id="18d2f-163">取得程式碼</span><span class="sxs-lookup"><span data-stu-id="18d2f-163">Get the code</span></span>

<span data-ttu-id="18d2f-164">您可以在 GitHub 上看到 [完整的解決方案](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) 。</span><span class="sxs-lookup"><span data-stu-id="18d2f-164">You can see the [full solution](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) on GitHub.</span></span>

## <a name="next-steps"></a><span data-ttu-id="18d2f-165">後續步驟</span><span class="sxs-lookup"><span data-stu-id="18d2f-165">Next steps</span></span>

<span data-ttu-id="18d2f-166">前往下一篇文章，以瞭解如何使用 .NET 處理 Apache Spark 的串流資料。</span><span class="sxs-lookup"><span data-stu-id="18d2f-166">Advance to the next article to learn how to process streaming data with .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="18d2f-167">教學課程：使用 .NET 進行 Apache Spark 的結構化串流</span><span class="sxs-lookup"><span data-stu-id="18d2f-167">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>](streaming.md)
