---
title: 使用 .NET 進行批次處理以進行 Apache Spark 教學課程
description: 瞭解如何使用適用于 Apache Spark 的 .NET 進行批次處理。
author: mamccrea
ms.author: mamccrea
ms.date: 12/13/2019
ms.topic: tutorial
ms.openlocfilehash: b00f560317c085058d791e17954603670fccf60f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594513"
---
# <a name="tutorial-do-batch-processing-with-net-for-apache-spark"></a><span data-ttu-id="28f26-103">教學課程：使用 .NET 進行批次處理以進行 Apache Spark</span><span class="sxs-lookup"><span data-stu-id="28f26-103">Tutorial: Do batch processing with .NET for Apache Spark</span></span>

<span data-ttu-id="28f26-104">在本教學課程中，您將瞭解如何使用 .NET 進行 Apache Spark 的批次處理。</span><span class="sxs-lookup"><span data-stu-id="28f26-104">In this tutorial, you learn how to do batch processing using .NET for Apache Spark.</span></span> <span data-ttu-id="28f26-105">批次處理是指待用資料的轉換，這表示來源資料已經載入資料儲存區中。</span><span class="sxs-lookup"><span data-stu-id="28f26-105">Batch processing is the transformation of data at rest, meaning that the source data has already been loaded into data storage.</span></span>

<span data-ttu-id="28f26-106">批次處理通常是針對需要準備進行進一步分析的大型一般資料集來執行。</span><span class="sxs-lookup"><span data-stu-id="28f26-106">Batch processing is generally performed over large, flat datasets that need to be prepared for further analysis.</span></span> <span data-ttu-id="28f26-107">記錄處理和資料倉儲是常見的批次處理案例。</span><span class="sxs-lookup"><span data-stu-id="28f26-107">Log processing and data warehousing are common batch processing scenarios.</span></span> <span data-ttu-id="28f26-108">在此案例中，您會分析 GitHub 專案的相關資訊，例如不同專案已分叉的時間，或最近的專案已更新的次數。</span><span class="sxs-lookup"><span data-stu-id="28f26-108">In this scenario, you analyze information about GitHub projects, such as the number of time different projects have been forked or how recently projects have been updated.</span></span>

<span data-ttu-id="28f26-109">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="28f26-109">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="28f26-110">建立並執行適用于 Apache Spark 應用程式的 .NET</span><span class="sxs-lookup"><span data-stu-id="28f26-110">Create and run a .NET for Apache Spark application</span></span>
> * <span data-ttu-id="28f26-111">將資料讀取至資料框架，並準備好進行分析</span><span class="sxs-lookup"><span data-stu-id="28f26-111">Read data into a DataFrame and prepare it for analysis</span></span>
> * <span data-ttu-id="28f26-112">使用 Spark SQL 處理資料</span><span class="sxs-lookup"><span data-stu-id="28f26-112">Process the data using Spark SQL</span></span>

## <a name="prerequisites"></a><span data-ttu-id="28f26-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="28f26-113">Prerequisites</span></span>

<span data-ttu-id="28f26-114">如果這是您第一次使用 .NET 進行 Apache Spark，請參閱[開始使用 .net for Apache Spark](get-started.md)教學課程，以瞭解如何準備您的環境，並針對 Apache Spark 應用程式執行您的第一個 .net。</span><span class="sxs-lookup"><span data-stu-id="28f26-114">If this is your first time using .NET for Apache Spark, check out the [Get started with .NET for Apache Spark](get-started.md) tutorial to learn how to prepare your environment and run your first .NET for Apache Spark application.</span></span>

## <a name="download-the-sample-data"></a><span data-ttu-id="28f26-115">下載範例資料</span><span class="sxs-lookup"><span data-stu-id="28f26-115">Download the sample data</span></span>

<span data-ttu-id="28f26-116">[GHTorrent](http://ghtorrent.org/)會監視所有公用 GitHub 事件（例如專案、認可和監看員的相關資訊），並將事件和其結構儲存在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="28f26-116">[GHTorrent](http://ghtorrent.org/) monitors all public GitHub events, such as info about projects, commits, and watchers, and stores the events and their structure in databases.</span></span> <span data-ttu-id="28f26-117">在不同時間週期內收集的資料可作為可下載的封存。</span><span class="sxs-lookup"><span data-stu-id="28f26-117">Data collected over different time periods is available as downloadable archives.</span></span> <span data-ttu-id="28f26-118">因為傾印檔案非常大，所以本指南會使用可從 GitHub 下載的已[截斷版本的](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv)傾印檔案。</span><span class="sxs-lookup"><span data-stu-id="28f26-118">Because the dump files are very large, this guide uses a [truncated version of the dump file](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) that can be downloaded from GitHub.</span></span>

> [!NOTE]
> <span data-ttu-id="28f26-119">GHTorrent 資料集會以雙重授權配置（[創意 Commons +](https://wiki.creativecommons.org/wiki/CCPlus)）散發。</span><span class="sxs-lookup"><span data-stu-id="28f26-119">The GHTorrent dataset is distributed under a dual licensing scheme ([Creative Commons +](https://wiki.creativecommons.org/wiki/CCPlus)).</span></span> <span data-ttu-id="28f26-120">對於非商業用途（包括但不限於教育、研究或個人用途），資料集會以「[依 SA](https://creativecommons.org/licenses/by-sa/4.0/)的副本」授權來散發。</span><span class="sxs-lookup"><span data-stu-id="28f26-120">For non-commercial uses (including, but not limited to, educational, research or personal uses), the dataset is distributed under the [CC-BY-SA license](https://creativecommons.org/licenses/by-sa/4.0/).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="28f26-121">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="28f26-121">Create a console application</span></span>

1. <span data-ttu-id="28f26-122">在命令提示字元中，執行下列命令以建立新的主控台應用程式：</span><span class="sxs-lookup"><span data-stu-id="28f26-122">In your command prompt, run the following commands to create a new console application:</span></span>

   ```dotnetcli
   dotnet new console -o mySparkBatchApp
   cd mySparkBatchApp
   ```

   <span data-ttu-id="28f26-123">`dotnet`命令 `new` 會為您建立類型的應用程式 `console` 。</span><span class="sxs-lookup"><span data-stu-id="28f26-123">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="28f26-124">`-o`參數會建立名為*mySparkBatchApp*的目錄，其中儲存您的應用程式，並填入所需的檔案。</span><span class="sxs-lookup"><span data-stu-id="28f26-124">The `-o` parameter creates a directory named *mySparkBatchApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="28f26-125">此 `cd mySparkBatchApp` 命令會將目錄變更為您剛才建立的應用程式目錄。</span><span class="sxs-lookup"><span data-stu-id="28f26-125">The `cd mySparkBatchApp` command changes the directory to the app directory you just created.</span></span>

1. <span data-ttu-id="28f26-126">若要在應用程式中使用 .NET 進行 Apache Spark，請安裝 Microsoft Spark 套件。</span><span class="sxs-lookup"><span data-stu-id="28f26-126">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="28f26-127">在您的主控台中，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="28f26-127">In your console, run the following command:</span></span>

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="create-a-sparksession"></a><span data-ttu-id="28f26-128">建立 SparkSession</span><span class="sxs-lookup"><span data-stu-id="28f26-128">Create a SparkSession</span></span>

1. <span data-ttu-id="28f26-129">將下列額外的 `using` 語句新增至*mySparkBatchApp*中*Program.cs*檔案的頂端。</span><span class="sxs-lookup"><span data-stu-id="28f26-129">Add the following additional `using` statements to the top of the *Program.cs* file in *mySparkBatchApp*.</span></span>

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. <span data-ttu-id="28f26-130">將下列程式碼新增至您的專案命名空間。</span><span class="sxs-lookup"><span data-stu-id="28f26-130">Add the following code to your project namespace.</span></span> <span data-ttu-id="28f26-131">稍後在程式中使用*s_referenceData* ，根據日期進行篩選。</span><span class="sxs-lookup"><span data-stu-id="28f26-131">*s_referenceData* is used later in the program to filter based on date.</span></span>

   ```csharp
   static readonly DateTime s_referenceDate = new DateTime(2015, 10, 20);
   ```

1. <span data-ttu-id="28f26-132">在 Main 方法內新增下列程式碼，以建立新的 SparkSession。</span><span class="sxs-lookup"><span data-stu-id="28f26-132">Add the following code inside your Main method to establish a new SparkSession.</span></span> <span data-ttu-id="28f26-133">SparkSession 是使用 Dataset 和資料框架 API 來程式設計 Spark 的進入點。</span><span class="sxs-lookup"><span data-stu-id="28f26-133">The SparkSession is the entry point to programming Spark with the Dataset and DataFrame API.</span></span> <span data-ttu-id="28f26-134">藉由呼叫 `spark` 物件，您可以在整個程式中存取 Spark 和資料框架功能。</span><span class="sxs-lookup"><span data-stu-id="28f26-134">By calling the `spark` object, you can access Spark and DataFrame functionality throughout your program.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("GitHub and Spark Batch")
        .GetOrCreate();
   ```

## <a name="prepare-the-data"></a><span data-ttu-id="28f26-135">準備資料</span><span class="sxs-lookup"><span data-stu-id="28f26-135">Prepare the data</span></span>

1. <span data-ttu-id="28f26-136">將輸入檔案讀入 `DataFrame` ，這是組織成命名資料行的分散式資料集合。</span><span class="sxs-lookup"><span data-stu-id="28f26-136">Read the input file into a `DataFrame`, which is a distributed collection of data organized into named columns.</span></span> <span data-ttu-id="28f26-137">您可以透過設定資料的資料行 <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A> 。</span><span class="sxs-lookup"><span data-stu-id="28f26-137">You can set the columns for your data through <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>.</span></span> <span data-ttu-id="28f26-138">使用 <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> 方法，在您的資料框架中顯示資料。</span><span class="sxs-lookup"><span data-stu-id="28f26-138">Use the <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> method to display the data in your DataFrame.</span></span> <span data-ttu-id="28f26-139">請務必將 CSV 檔案路徑更新為您所下載之 GitHub 資料的位置。</span><span class="sxs-lookup"><span data-stu-id="28f26-139">Be sure to update the CSV file path to the location of the GitHub data you downloaded.</span></span>

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

1. <span data-ttu-id="28f26-140">使用 <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> 方法來卸載具有 NA （null）值的資料列，以及 <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> 從您的資料中移除特定資料行的方法。</span><span class="sxs-lookup"><span data-stu-id="28f26-140">Use the <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> method to drop rows with NA (null) values, and the <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> method to remove certain columns from your data.</span></span> <span data-ttu-id="28f26-141">如果您嘗試分析與最終分析無關的 null 資料或資料行，這有助於避免錯誤。</span><span class="sxs-lookup"><span data-stu-id="28f26-141">This helps prevent errors if you try to analyze null data or columns that are not relevant to your final analysis.</span></span>

   ```csharp
   // Drop any rows with NA values
   DataFrameNaFunctions dropEmptyProjects = projectsDf.Na();
   DataFrame cleanedProjects = dropEmptyProjects.Drop("any");

   // Remove unnecessary columns
   cleanedProjects = cleanedProjects.Drop("id", "url", "owner_id");
   cleanedProjects.Show();
   ```

## <a name="analyze-the-data"></a><span data-ttu-id="28f26-142">分析資料</span><span class="sxs-lookup"><span data-stu-id="28f26-142">Analyze the data</span></span>

<span data-ttu-id="28f26-143">Spark SQL 可讓您對資料進行 SQL 呼叫。</span><span class="sxs-lookup"><span data-stu-id="28f26-143">Spark SQL allows you to make SQL calls on your data.</span></span> <span data-ttu-id="28f26-144">結合使用者定義函式和 Spark SQL 通常是為了將使用者定義函數套用至資料框架的所有資料列。</span><span class="sxs-lookup"><span data-stu-id="28f26-144">It's common to combine user-defined functions and Spark SQL to apply a user-defined function to all rows of your DataFrame.</span></span>

<span data-ttu-id="28f26-145">您可以特別呼叫 `spark.Sql` 來模擬在其他類型的應用程式中所看到的標準 SQL 呼叫。</span><span class="sxs-lookup"><span data-stu-id="28f26-145">You can specifically call `spark.Sql` to mimic standard SQL calls seen in other types of apps.</span></span> <span data-ttu-id="28f26-146">您也可以呼叫和之類的方法， <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> 以明確地結合、篩選及執行資料的計算。</span><span class="sxs-lookup"><span data-stu-id="28f26-146">You can also call methods like <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> and <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> to specifically combine, filter, and perform calculations on your data.</span></span>

<span data-ttu-id="28f26-147">此應用程式的目標是要取得關於 GitHub 專案資料的一些見解。</span><span class="sxs-lookup"><span data-stu-id="28f26-147">The goal of this app is to gain some insights about the GitHub projects data.</span></span> <span data-ttu-id="28f26-148">將下列程式碼片段新增至您的程式，以分析資料。</span><span class="sxs-lookup"><span data-stu-id="28f26-148">Add the following code snippets to your program to analyze the data.</span></span>

1. <span data-ttu-id="28f26-149">新增下列程式碼區塊，以尋找每個語言已分叉的次數。</span><span class="sxs-lookup"><span data-stu-id="28f26-149">Add the following block of code finds the number of times each language has been forked.</span></span> <span data-ttu-id="28f26-150">首先，資料會依語言分組。</span><span class="sxs-lookup"><span data-stu-id="28f26-150">First, the data is grouped by language.</span></span> <span data-ttu-id="28f26-151">然後會採用每個語言的平均分支數目。</span><span class="sxs-lookup"><span data-stu-id="28f26-151">Then, the average number of forks from each language is taken.</span></span>

   ```csharp
   // Average number of times each language has been forked
   DataFrame groupedDF = cleanedProjects
       .GroupBy("language")
       .Agg(Avg(cleanedProjects["forked_from"]);
   ```

1. <span data-ttu-id="28f26-152">新增下列程式碼區塊，以遞減順序排序分支的平均數目，以查看哪些語言最具分叉。</span><span class="sxs-lookup"><span data-stu-id="28f26-152">Add the following block of code to order the average number of forks in descending order to see which languages are the most forked.</span></span> <span data-ttu-id="28f26-153">也就是，會先顯示最大的分支數目。</span><span class="sxs-lookup"><span data-stu-id="28f26-153">That is, the largest number of forks will appear first.</span></span>

   ```csharp
   // Sort by most forked languages first
   groupedDF.OrderBy(Desc("avg(forked_from)")).Show();
   ```

1. <span data-ttu-id="28f26-154">下一個程式碼區塊會顯示最近專案的更新方式。</span><span class="sxs-lookup"><span data-stu-id="28f26-154">The next block of code shows you how recently projects have been updated.</span></span> <span data-ttu-id="28f26-155">您註冊名為*MyUDF*的新使用者定義函數，並將它與在教學課程開頭所宣告的日期*s_referenceDate*做比較。</span><span class="sxs-lookup"><span data-stu-id="28f26-155">You register a new user-defined function called *MyUDF* and compare it with a date, *s_referenceDate*, which was declared at the beginning of the tutorial.</span></span> <span data-ttu-id="28f26-156">每個專案的日期會與參考日期進行比較。</span><span class="sxs-lookup"><span data-stu-id="28f26-156">The date for each project is compared against the reference date.</span></span> <span data-ttu-id="28f26-157">然後，Spark SQL 會用來在資料的每個資料列上呼叫 UDF，以分析資料集中的每個專案。</span><span class="sxs-lookup"><span data-stu-id="28f26-157">Then, Spark SQL is used to call the UDF on each row of the data to analyze each project in the data set.</span></span>

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

1. <span data-ttu-id="28f26-158">呼叫 `spark.Stop()` 以結束 SparkSession。</span><span class="sxs-lookup"><span data-stu-id="28f26-158">Call `spark.Stop()` to end the SparkSession.</span></span>

## <a name="use-spark-submit-to-run-your-app"></a><span data-ttu-id="28f26-159">使用 spark-提交來執行您的應用程式</span><span class="sxs-lookup"><span data-stu-id="28f26-159">Use spark-submit to run your app</span></span>

1. <span data-ttu-id="28f26-160">使用下列命令來建立您的 .NET 應用程式：</span><span class="sxs-lookup"><span data-stu-id="28f26-160">Use the following command to build your .NET app:</span></span>

   ```dotnetcli
   dotnet build
   ```

1. <span data-ttu-id="28f26-161">使用執行您的應用程式 `spark-submit` 。</span><span class="sxs-lookup"><span data-stu-id="28f26-161">Run your app with `spark-submit`.</span></span> <span data-ttu-id="28f26-162">請務必使用 Microsoft Spark jar 檔案的實際路徑來更新下列命令。</span><span class="sxs-lookup"><span data-stu-id="28f26-162">Be sure to update the following command with the actual paths to your Microsoft Spark jar file.</span></span>

   ```console
   spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /<path>/to/microsoft-spark-<version>.jar dotnet /<path>/to/netcoreapp<version>/GitHubProjects.dll
   ```

## <a name="get-the-code"></a><span data-ttu-id="28f26-163">取得程式碼</span><span class="sxs-lookup"><span data-stu-id="28f26-163">Get the code</span></span>

<span data-ttu-id="28f26-164">您可以在 GitHub 上看到[完整的解決方案](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs)。</span><span class="sxs-lookup"><span data-stu-id="28f26-164">You can see the [full solution](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) on GitHub.</span></span>

## <a name="next-steps"></a><span data-ttu-id="28f26-165">後續步驟</span><span class="sxs-lookup"><span data-stu-id="28f26-165">Next steps</span></span>

<span data-ttu-id="28f26-166">前往下一篇文章，以瞭解如何使用 .NET 來處理串流資料，以進行 Apache Spark。</span><span class="sxs-lookup"><span data-stu-id="28f26-166">Advance to the next article to learn how to process streaming data with .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="28f26-167">教學課程：使用適用于 Apache Spark 的 .NET 進行結構化串流</span><span class="sxs-lookup"><span data-stu-id="28f26-167">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>](streaming.md)
