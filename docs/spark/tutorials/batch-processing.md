---
title: 批次處理與 .NET 的 Apache Spark 教程
description: 瞭解如何使用 .NET 進行阿帕奇 Spark 的批次處理。
author: mamccrea
ms.author: mamccrea
ms.date: 12/13/2019
ms.topic: tutorial
ms.openlocfilehash: 460c37e66c2c0a8a9b197a9abaff9eead842bdeb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187558"
---
# <a name="tutorial-do-batch-processing-with-net-for-apache-spark"></a><span data-ttu-id="e71cf-103">教程：使用 .NET 進行批次處理，用於 Apache Spark</span><span class="sxs-lookup"><span data-stu-id="e71cf-103">Tutorial: Do batch processing with .NET for Apache Spark</span></span>

<span data-ttu-id="e71cf-104">在本教程中，您將瞭解如何使用 .NET 進行 Apache Spark 的批次處理。</span><span class="sxs-lookup"><span data-stu-id="e71cf-104">In this tutorial, you learn how to do batch processing using .NET for Apache Spark.</span></span> <span data-ttu-id="e71cf-105">批次處理是靜止資料轉換，這意味著來源資料已載入到資料存儲中。</span><span class="sxs-lookup"><span data-stu-id="e71cf-105">Batch processing is the transformation of data at rest, meaning that the source data has already been loaded into data storage.</span></span>

<span data-ttu-id="e71cf-106">批次處理通常通過大型平面資料集執行，這些資料集需要準備進行進一步分析。</span><span class="sxs-lookup"><span data-stu-id="e71cf-106">Batch processing is generally performed over large, flat datasets that need to be prepared for further analysis.</span></span> <span data-ttu-id="e71cf-107">日誌處理和資料倉儲是常見的批次處理方案。</span><span class="sxs-lookup"><span data-stu-id="e71cf-107">Log processing and data warehousing are common batch processing scenarios.</span></span> <span data-ttu-id="e71cf-108">在此方案中，您可以分析有關 GitHub 專案的資訊，例如不同專案分叉的時間數或最近專案的更新時間。</span><span class="sxs-lookup"><span data-stu-id="e71cf-108">In this scenario, you analyze information about GitHub projects, such as the number of time different projects have been forked or how recently projects have been updated.</span></span>

<span data-ttu-id="e71cf-109">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="e71cf-109">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="e71cf-110">為 Apache Spark 應用程式創建和運行 .NET</span><span class="sxs-lookup"><span data-stu-id="e71cf-110">Create and run a .NET for Apache Spark application</span></span>
> * <span data-ttu-id="e71cf-111">將資料讀取到資料框架中並準備進行分析</span><span class="sxs-lookup"><span data-stu-id="e71cf-111">Read data into a DataFrame and prepare it for analysis</span></span>
> * <span data-ttu-id="e71cf-112">使用 Spark SQL 處理資料</span><span class="sxs-lookup"><span data-stu-id="e71cf-112">Process the data using Spark SQL</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e71cf-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="e71cf-113">Prerequisites</span></span>

<span data-ttu-id="e71cf-114">如果這是您第一次使用 .NET 進行 Apache Spark，請查看[.NET 開始為 Apache Spark](../tutorials/get-started.md)教程，瞭解如何準備您的環境並運行您的第一個 .NET 用於 Apache Spark 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e71cf-114">If this is your first time using .NET for Apache Spark, check out the [Get started with .NET for Apache Spark](../tutorials/get-started.md) tutorial to learn how to prepare your environment and run your first .NET for Apache Spark application.</span></span>

## <a name="download-the-sample-data"></a><span data-ttu-id="e71cf-115">下載範例資料</span><span class="sxs-lookup"><span data-stu-id="e71cf-115">Download the sample data</span></span>

<span data-ttu-id="e71cf-116">[GHTorrent](http://ghtorrent.org/)監視所有公共 GitHub 事件，例如有關專案、提交和觀察程式的資訊，並將事件及其結構存儲在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="e71cf-116">[GHTorrent](http://ghtorrent.org/) monitors all public GitHub events, such as info about projects, commits, and watchers, and stores the events and their structure in databases.</span></span> <span data-ttu-id="e71cf-117">在不同時間段收集的資料可作為可下載的存檔提供。</span><span class="sxs-lookup"><span data-stu-id="e71cf-117">Data collected over different time periods is available as downloadable archives.</span></span> <span data-ttu-id="e71cf-118">由於轉儲檔非常大，本指南使用可從 GitHub 下載[的轉儲檔的截斷版本](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv)。</span><span class="sxs-lookup"><span data-stu-id="e71cf-118">Because the dump files are very large, this guide uses a [truncated version of the dump file](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) that can be downloaded from GitHub.</span></span>

> [!NOTE]
> <span data-ttu-id="e71cf-119">GHTorrent 資料集在雙重許可計畫 （[知識共用 +](https://wiki.creativecommons.org/wiki/CCPlus)） 下分發。</span><span class="sxs-lookup"><span data-stu-id="e71cf-119">The GHTorrent dataset is distributed under a dual licensing scheme ([Creative Commons +](https://wiki.creativecommons.org/wiki/CCPlus)).</span></span> <span data-ttu-id="e71cf-120">對於非商業用途（包括但不限於教育、研究或個人用途），資料集在[CC-BY-SA 許可證](https://creativecommons.org/licenses/by-sa/4.0/)下分發。</span><span class="sxs-lookup"><span data-stu-id="e71cf-120">For non-commercial uses (including, but not limited to, educational, research or personal uses), the dataset is distributed under the [CC-BY-SA license](https://creativecommons.org/licenses/by-sa/4.0/).</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="e71cf-121">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="e71cf-121">Create a console application</span></span>

1. <span data-ttu-id="e71cf-122">在命令提示符中，運行以下命令以創建新的主控台應用程式：</span><span class="sxs-lookup"><span data-stu-id="e71cf-122">In your command prompt, run the following commands to create a new console application:</span></span>

   ```dotnetcli
   dotnet new console -o mySparkBatchApp
   cd mySparkBatchApp
   ```

   <span data-ttu-id="e71cf-123">該`dotnet`命令為您創建`new`類型`console`應用程式。</span><span class="sxs-lookup"><span data-stu-id="e71cf-123">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="e71cf-124">該`-o`參數創建一個名為*mySparkBatchApp*的目錄，其中存儲你的應用，並將其填充到所需的檔中。</span><span class="sxs-lookup"><span data-stu-id="e71cf-124">The `-o` parameter creates a directory named *mySparkBatchApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="e71cf-125">該`cd mySparkBatchApp`命令將目錄更改為您剛剛創建的應用目錄。</span><span class="sxs-lookup"><span data-stu-id="e71cf-125">The `cd mySparkBatchApp` command changes the directory to the app directory you just created.</span></span>

1. <span data-ttu-id="e71cf-126">要在應用中使用的阿帕奇 Spark 的 .NET，請安裝 Microsoft.Spark 包。</span><span class="sxs-lookup"><span data-stu-id="e71cf-126">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="e71cf-127">在主控台中，運行以下命令：</span><span class="sxs-lookup"><span data-stu-id="e71cf-127">In your console, run the following command:</span></span>

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="create-a-sparksession"></a><span data-ttu-id="e71cf-128">創建火花會話</span><span class="sxs-lookup"><span data-stu-id="e71cf-128">Create a SparkSession</span></span>

1. <span data-ttu-id="e71cf-129">將以下附加`using`語句添加到*mySparkBatchApp*中*Program.cs*檔的頂部。</span><span class="sxs-lookup"><span data-stu-id="e71cf-129">Add the following additional `using` statements to the top of the *Program.cs* file in *mySparkBatchApp*.</span></span>

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. <span data-ttu-id="e71cf-130">將以下代碼添加到專案命名空間。</span><span class="sxs-lookup"><span data-stu-id="e71cf-130">Add the following code to your project namespace.</span></span> <span data-ttu-id="e71cf-131">*s_referenceData*在程式中稍後用於根據日期進行篩選。</span><span class="sxs-lookup"><span data-stu-id="e71cf-131">*s_referenceData* is used later in the program to filter based on date.</span></span>

   ```csharp
   static readonly DateTime s_referenceDate = new DateTime(2015, 10, 20);
   ```

1. <span data-ttu-id="e71cf-132">在 Main 方法中添加以下代碼，以建立新的 SparkSession。</span><span class="sxs-lookup"><span data-stu-id="e71cf-132">Add the following code inside your Main method to establish a new SparkSession.</span></span> <span data-ttu-id="e71cf-133">SparkSession 是使用資料集和資料幀 API 程式設計 Spark 的進入點。</span><span class="sxs-lookup"><span data-stu-id="e71cf-133">The SparkSession is the entry point to programming Spark with the Dataset and DataFrame API.</span></span> <span data-ttu-id="e71cf-134">通過調用物件`spark`，您可以在整個程式中訪問 Spark 和 DataFrame 功能。</span><span class="sxs-lookup"><span data-stu-id="e71cf-134">By calling the `spark` object, you can access Spark and DataFrame functionality throughout your program.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("GitHub and Spark Batch")
        .GetOrCreate();
   ```

## <a name="prepare-the-data"></a><span data-ttu-id="e71cf-135">準備資料</span><span class="sxs-lookup"><span data-stu-id="e71cf-135">Prepare the data</span></span>

1. <span data-ttu-id="e71cf-136">將輸入檔讀入`DataFrame`中，這是組織到命名列中的分散式資料集合。</span><span class="sxs-lookup"><span data-stu-id="e71cf-136">Read the input file into a `DataFrame`, which is a distributed collection of data organized into named columns.</span></span> <span data-ttu-id="e71cf-137">您可以通過 設置資料的列<xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>。</span><span class="sxs-lookup"><span data-stu-id="e71cf-137">You can set the columns for your data through <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>.</span></span> <span data-ttu-id="e71cf-138">使用<xref:Microsoft.Spark.Sql.DataFrame.Show%2A>方法在資料框架中顯示資料。</span><span class="sxs-lookup"><span data-stu-id="e71cf-138">Use the <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> method to display the data in your DataFrame.</span></span> <span data-ttu-id="e71cf-139">請務必將 CSV 檔路徑更新到您下載的 GitHub 資料的位置。</span><span class="sxs-lookup"><span data-stu-id="e71cf-139">Be sure to update the CSV file path to the location of the GitHub data you downloaded.</span></span>

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

1. <span data-ttu-id="e71cf-140">使用<xref:Microsoft.Spark.Sql.DataFrame.Na%2A>方法刪除具有 NA（空）值的行，<xref:Microsoft.Spark.Sql.DataFrame.Drop%2A>以及從資料中刪除某些列的方法。</span><span class="sxs-lookup"><span data-stu-id="e71cf-140">Use the <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> method to drop rows with NA (null) values, and the <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> method to remove certain columns from your data.</span></span> <span data-ttu-id="e71cf-141">如果您嘗試分析與最終分析無關的空資料或列，這有助於防止錯誤。</span><span class="sxs-lookup"><span data-stu-id="e71cf-141">This helps prevent errors if you try to analyze null data or columns that are not relevant to your final analysis.</span></span>

   ```csharp
   // Drop any rows with NA values
   DataFrameNaFunctions dropEmptyProjects = projectsDf.Na();
   DataFrame cleanedProjects = dropEmptyProjects.Drop("any");

   // Remove unnecessary columns
   cleanedProjects = cleanedProjects.Drop("id", "url", "owner_id");
   cleanedProjects.Show();
   ```

## <a name="analyze-the-data"></a><span data-ttu-id="e71cf-142">分析資料</span><span class="sxs-lookup"><span data-stu-id="e71cf-142">Analyze the data</span></span>

<span data-ttu-id="e71cf-143">Spark SQL 允許您對資料進行 SQL 調用。</span><span class="sxs-lookup"><span data-stu-id="e71cf-143">Spark SQL allows you to make SQL calls on your data.</span></span> <span data-ttu-id="e71cf-144">通常將使用者定義的函數和 Spark SQL 組合在一起，將使用者定義的函數應用於 DataFrame 的所有行。</span><span class="sxs-lookup"><span data-stu-id="e71cf-144">It's common to combine user-defined functions and Spark SQL to apply a user-defined function to all rows of your DataFrame.</span></span>

<span data-ttu-id="e71cf-145">您可以專門調用`spark.Sql`以類比其他類型的應用中看到的標準 SQL 調用。</span><span class="sxs-lookup"><span data-stu-id="e71cf-145">You can specifically call `spark.Sql` to mimic standard SQL calls seen in other types of apps.</span></span> <span data-ttu-id="e71cf-146">您還可以調用方法，如<xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A>和<xref:Microsoft.Spark.Sql.DataFrame.Agg%2A>專門組合、篩選和執行對資料的計算。</span><span class="sxs-lookup"><span data-stu-id="e71cf-146">You can also call methods like <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> and <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> to specifically combine, filter, and perform calculations on your data.</span></span>

<span data-ttu-id="e71cf-147">此應用程式的目標是獲取有關 GitHub 專案資料的一些見解。</span><span class="sxs-lookup"><span data-stu-id="e71cf-147">The goal of this app is to gain some insights about the GitHub projects data.</span></span> <span data-ttu-id="e71cf-148">向程式添加以下程式碼片段以分析資料。</span><span class="sxs-lookup"><span data-stu-id="e71cf-148">Add the following code snippets to your program to analyze the data.</span></span>

1. <span data-ttu-id="e71cf-149">添加以下代碼塊可查找每種語言分叉的次數。</span><span class="sxs-lookup"><span data-stu-id="e71cf-149">Add the following block of code finds the number of times each language has been forked.</span></span> <span data-ttu-id="e71cf-150">首先，資料按語言分組。</span><span class="sxs-lookup"><span data-stu-id="e71cf-150">First, the data is grouped by language.</span></span> <span data-ttu-id="e71cf-151">然後，從每種語言的平均分叉數被取走。</span><span class="sxs-lookup"><span data-stu-id="e71cf-151">Then, the average number of forks from each language is taken.</span></span>

   ```csharp
   // Average number of times each language has been forked
   DataFrame groupedDF = cleanedProjects
       .GroupBy("language")
       .Agg(Avg(cleanedProjects["forked_from"]);
   ```

1. <span data-ttu-id="e71cf-152">添加以下代碼塊以按降冪排列叉的平均數量，以查看哪些語言是分叉最多的。</span><span class="sxs-lookup"><span data-stu-id="e71cf-152">Add the following block of code to order the average number of forks in descending order to see which languages are the most forked.</span></span> <span data-ttu-id="e71cf-153">也就是說，將首先出現最多數量的分叉。</span><span class="sxs-lookup"><span data-stu-id="e71cf-153">That is, the largest number of forks will appear first.</span></span>

   ```csharp
   // Sort by most forked languages first
   groupedDF.OrderBy(Desc("avg(forked_from)")).Show();
   ```

1. <span data-ttu-id="e71cf-154">下一個代碼塊顯示最近專案的更新方式。</span><span class="sxs-lookup"><span data-stu-id="e71cf-154">The next block of code shows you how recently projects have been updated.</span></span> <span data-ttu-id="e71cf-155">註冊名為*MyUDF*的新使用者定義的函數，並將其與在本教程開頭聲明的日期*s_referenceDate*進行比較。</span><span class="sxs-lookup"><span data-stu-id="e71cf-155">You register a new user-defined function called *MyUDF* and compare it with a date, *s_referenceDate*, which was declared at the beginning of the tutorial.</span></span> <span data-ttu-id="e71cf-156">將每個專案的日期與參考日期進行比較。</span><span class="sxs-lookup"><span data-stu-id="e71cf-156">The date for each project is compared against the reference date.</span></span> <span data-ttu-id="e71cf-157">然後，Spark SQL 用於調用資料每行上的 UDF 來分析資料集中的每個專案。</span><span class="sxs-lookup"><span data-stu-id="e71cf-157">Then, Spark SQL is used to call the UDF on each row of the data to analyze each project in the data set.</span></span>

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

1. <span data-ttu-id="e71cf-158">調用`spark.Stop()`結束 SparkSession。</span><span class="sxs-lookup"><span data-stu-id="e71cf-158">Call `spark.Stop()` to end the SparkSession.</span></span>

## <a name="use-spark-submit-to-run-your-app"></a><span data-ttu-id="e71cf-159">使用火花提交運行應用</span><span class="sxs-lookup"><span data-stu-id="e71cf-159">Use spark-submit to run your app</span></span>

1. <span data-ttu-id="e71cf-160">使用以下命令生成 .NET 應用：</span><span class="sxs-lookup"><span data-stu-id="e71cf-160">Use the following command to build your .NET app:</span></span>

   ```dotnetcli
   dotnet build
   ```

1. <span data-ttu-id="e71cf-161">使用`spark-submit`運行應用。</span><span class="sxs-lookup"><span data-stu-id="e71cf-161">Run your app with `spark-submit`.</span></span> <span data-ttu-id="e71cf-162">請務必使用 Microsoft Spark jar 檔的實際路徑更新以下命令。</span><span class="sxs-lookup"><span data-stu-id="e71cf-162">Be sure to update the following command with the actual paths to your Microsoft Spark jar file.</span></span>

   ```console
   spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /<path>/to/microsoft-spark-<version>.jar dotnet /<path>/to/netcoreapp<version>/GitHubProjects.dll
   ```

## <a name="get-the-code"></a><span data-ttu-id="e71cf-163">取得程式碼</span><span class="sxs-lookup"><span data-stu-id="e71cf-163">Get the code</span></span>

<span data-ttu-id="e71cf-164">您可以在 GitHub 上看到[完整的解決方案](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs)。</span><span class="sxs-lookup"><span data-stu-id="e71cf-164">You can see the [full solution](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) on GitHub.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e71cf-165">後續步驟</span><span class="sxs-lookup"><span data-stu-id="e71cf-165">Next steps</span></span>

<span data-ttu-id="e71cf-166">進入下一篇文章，瞭解如何使用 .NET 處理 Apache Spark 的流資料。</span><span class="sxs-lookup"><span data-stu-id="e71cf-166">Advance to the next article to learn how to process streaming data with .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="e71cf-167">教程：結構化流與 .NET 的 Apache Spark</span><span class="sxs-lookup"><span data-stu-id="e71cf-167">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>](streaming.md)
