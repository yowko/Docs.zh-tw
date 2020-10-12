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
# <a name="tutorial-do-batch-processing-with-net-for-apache-spark"></a>教學課程：使用 .NET 進行批次處理以進行 Apache Spark

在本教學課程中，您將瞭解如何使用 .NET 進行 Apache Spark 的批次處理。 批次處理是待用資料的轉換，這表示來源資料已載入資料儲存區中。

批次處理通常是針對需要準備進行進一步分析的大型資料集進行。 記錄處理和資料倉儲是常見的批次處理案例。 在此案例中，您會分析 GitHub 專案的相關資訊，例如不同專案的分支時間或最近專案的更新方式。

在本教學課程中，您會了解如何：

> [!div class="checklist"]
>
> * 建立和執行 Apache Spark 應用程式的 .NET
> * 將資料讀入資料框架並準備進行分析
> * 使用 Spark SQL 來處理資料

## <a name="prerequisites"></a>必要條件

如果這是您第一次使用 .NET 進行 Apache Spark，請參閱 [開始使用 .net 進行 Apache Spark](get-started.md) 教學課程，以瞭解如何準備您的環境，並針對 Apache Spark 應用程式執行您的第一個 .net。

## <a name="download-the-sample-data"></a>下載範例資料

[GHTorrent](http://ghtorrent.org/) 會監視所有的公用 GitHub 事件，例如專案、認可和監看員的相關資訊，並將事件和其結構儲存在資料庫中。 在不同期間收集的資料會以可下載的封存形式提供。 因為傾印檔案很大，所以本指南會使用可從 GitHub 下載的傾印檔案 [截斷版本](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv) 。

> [!NOTE]
> GHTorrent 資料集會以雙重授權配置來散發 ([創意的 Commons +](https://wiki.creativecommons.org/wiki/CCPlus)) 。 針對非商業用途 (包括（但不限於教育、研究或個人用途) ），資料集會以 [CC BY SA 授權](https://creativecommons.org/licenses/by-sa/4.0/)來散發。

## <a name="create-a-console-application"></a>建立主控台應用程式

1. 在命令提示字元中，執行下列命令以建立新的主控台應用程式：

   ```dotnetcli
   dotnet new console -o mySparkBatchApp
   cd mySparkBatchApp
   ```

   此 `dotnet` 命令 `new` 會為您建立類型的應用程式 `console` 。 `-o`參數會建立名為*mySparkBatchApp*的目錄，您的應用程式會儲存在此目錄中，並填入必要的檔案。 此 `cd mySparkBatchApp` 命令會將目錄變更為您剛才建立的應用程式目錄。

1. 若要在應用程式中使用 .NET 進行 Apache Spark，請安裝 Microsoft Spark 套件。 在主控台中，執行下列命令：

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="create-a-sparksession"></a>建立 SparkSession

1. `using`在*mySparkBatchApp*中的*Program.cs*檔案頂端新增下列其他語句。

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. 將下列程式碼新增至您的專案命名空間。 稍後在程式中，會使用*s_referenceData*來根據日期進行篩選。

   ```csharp
   static readonly DateTime s_referenceDate = new DateTime(2015, 10, 20);
   ```

1. 在 Main 方法內新增下列程式碼，以建立新的 SparkSession。 SparkSession 是將 Spark 與資料集和資料框架 API 進行程式設計的進入點。 藉由呼叫 `spark` 物件，您就可以存取整個程式中的 Spark 和資料框架功能。

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("GitHub and Spark Batch")
        .GetOrCreate();
   ```

## <a name="prepare-the-data"></a>準備資料

1. 將輸入檔讀取到 `DataFrame` ，這是組織成命名資料行的分散式資料集合。 您可以透過設定資料的資料行 <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A> 。 <xref:Microsoft.Spark.Sql.DataFrame.Show%2A>您可以使用方法，在資料框架中顯示資料。 請務必將 CSV 檔案路徑更新為您下載的 GitHub 資料的位置。

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

1. <xref:Microsoft.Spark.Sql.DataFrame.Na%2A>您可以使用方法來卸載具有 NA (null) 值的資料列，並使用 <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> 方法來移除資料中的特定資料行。 如果您嘗試分析與最終分析無關的 null 資料或資料行，這有助於避免錯誤。

   ```csharp
   // Drop any rows with NA values
   DataFrameNaFunctions dropEmptyProjects = projectsDf.Na();
   DataFrame cleanedProjects = dropEmptyProjects.Drop("any");

   // Remove unnecessary columns
   cleanedProjects = cleanedProjects.Drop("id", "url", "owner_id");
   cleanedProjects.Show();
   ```

## <a name="analyze-the-data"></a>分析資料

Spark SQL 可讓您對資料進行 SQL 呼叫。 通常會結合使用者定義函數和 Spark SQL，以將使用者定義函數套用至資料框架的所有資料列。

您可以特別呼叫 `spark.Sql` 來模擬在其他類型的應用程式中看到的標準 SQL 呼叫。 您也可以呼叫方法（例如和）， <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> 以明確地結合、篩選和執行資料的計算。

此應用程式的目標是要深入瞭解 GitHub 專案資料。 將下列程式碼片段新增至您的程式，以分析資料。

1. 新增下列程式碼區塊，以尋找每個語言已派生的次數。 首先，資料會依語言分組。 然後，會取得每個語言的平均分支數目。

   ```csharp
   // Average number of times each language has been forked
   DataFrame groupedDF = cleanedProjects
       .GroupBy("language")
       .Agg(Avg(cleanedProjects["forked_from"]);
   ```

1. 新增下列程式碼區塊，以遞減順序排序平均數的平均數目，以查看哪些語言最具分支。 也就是說，會先顯示最大的分支數目。

   ```csharp
   // Sort by most forked languages first
   groupedDF.OrderBy(Desc("avg(forked_from)")).Show();
   ```

1. 下一個程式碼區塊會顯示最近專案的更新方式。 您可以註冊名為 *MyUDF* 的新使用者定義函數，並將它與在教學課程開頭宣告的日期 *s_referenceDate*比較。 每個專案的日期會與參考日期進行比較。 然後，Spark SQL 會用來呼叫每個資料列上的 UDF，以分析資料集中的每個專案。

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

1. 呼叫 `spark.Stop()` 以結束 SparkSession。

## <a name="use-spark-submit-to-run-your-app"></a>使用 spark 提交來執行您的應用程式

1. 使用下列命令來建立您的 .NET 應用程式：

   ```dotnetcli
   dotnet build
   ```

1. 使用執行您的應用程式 `spark-submit` 。 請務必使用 Microsoft Spark jar 檔案的實際路徑來更新下列命令。

   ```console
   spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /<path>/to/microsoft-spark-<version>.jar dotnet /<path>/to/netcoreapp<version>/GitHubProjects.dll
   ```

## <a name="get-the-code"></a>取得程式碼

您可以在 GitHub 上看到 [完整的解決方案](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs) 。

## <a name="next-steps"></a>後續步驟

前往下一篇文章，以瞭解如何使用 .NET 處理 Apache Spark 的串流資料。
> [!div class="nextstepaction"]
> [教學課程：使用 .NET 進行 Apache Spark 的結構化串流](streaming.md)
