---
title: 使用 .NET 進行批次處理以進行 Apache Spark 教學課程
description: 瞭解如何使用適用于 Apache Spark 的 .NET 進行批次處理。
author: mamccrea
ms.author: mamccrea
ms.date: 12/13/2019
ms.topic: tutorial
ms.openlocfilehash: bd91fb401b9beb6ae74c4599b25e43284473f8b0
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75466410"
---
# <a name="tutorial-do-batch-processing-with-net-for-apache-spark"></a>教學課程：使用 .NET 進行批次處理以進行 Apache Spark

在本教學課程中，您將瞭解如何使用 .NET 進行 Apache Spark 的批次處理。 批次處理是指待用資料的轉換，這表示來源資料已經載入資料儲存區中。 

批次處理通常是針對需要準備進行進一步分析的大型一般資料集來執行。 記錄處理和資料倉儲是常見的批次處理案例。 在此案例中，您會分析 GitHub 專案的相關資訊，例如不同專案已分叉的時間，或最近的專案已更新的次數。 

在本教學課程中，您將了解如何：

> [!div class="checklist"]
>
> * 建立並執行適用于 Apache Spark 應用程式的 .NET
> * 將資料讀取至資料框架，並準備好進行分析
> * 使用 Spark SQL 處理資料

## <a name="prerequisites"></a>必要條件： 

如果這是您第一次使用 .NET 進行 Apache Spark，請參閱[開始使用 .net for Apache Spark](../tutorials/get-started.md)教學課程，以瞭解如何準備您的環境，並針對 Apache Spark 應用程式執行您的第一個 .net。

## <a name="download-the-sample-data"></a>下載範例資料

[GHTorrent](http://ghtorrent.org/)會監視所有公用 GitHub 事件（例如專案、認可和監看員的相關資訊），並將事件和其結構儲存在資料庫中。 在不同時間週期內收集的資料可作為可下載的封存。 因為傾印檔案非常大，所以本指南會使用可從 GitHub 下載的已[截斷版本的](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv)傾印檔案。

> [!NOTE]
> GHTorrent 資料集會以雙重授權配置（[創意 Commons +](https://wiki.creativecommons.org/wiki/CCPlus)）散發。 對於非商業用途（包括但不限於教育、研究或個人用途），資料集會以「[依 SA](https://creativecommons.org/licenses/by-sa/4.0/)的副本」授權來散發。

## <a name="create-a-console-application"></a>建立主控台應用程式

1. 在命令提示字元中，執行下列命令以建立新的主控台應用程式：

   ```dotnetcli
   dotnet new console -o mySparkBatchApp
   cd mySparkBatchApp
   ```

   `dotnet` 命令會為您建立類型為 `console` 的 `new` 應用程式。 `-o` 參數會建立名為*mySparkBatchApp*的目錄，其中儲存您的應用程式，並填入所需的檔案。 `cd mySparkBatchApp` 命令會將目錄變更為您剛才建立的應用程式目錄。

1. 若要在應用程式中使用 .NET 進行 Apache Spark，請安裝 Microsoft Spark 套件。 在您的主控台中，執行下列命令：

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="create-a-sparksession"></a>建立 SparkSession

1. 在*mySparkBatchApp*中的*Program.cs*檔案頂端新增下列額外的 `using` 語句。

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. 將下列程式碼新增至您的專案命名空間。 稍後在程式中使用*s_referenceData* ，根據日期進行篩選。

   ```csharp
   static readonly DateTime s_referenceDate = new DateTime(2015, 10, 20);
   ```

1. 在 Main 方法內新增下列程式碼，以建立新的 SparkSession。 SparkSession 是使用 Dataset 和資料框架 API 來程式設計 Spark 的進入點。 藉由呼叫 `spark` 物件，您可以在整個程式中存取 Spark 和資料框架功能。

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("GitHub and Spark Batch")
        .GetOrCreate();
   ```

## <a name="prepare-the-data"></a>準備資料

1. 將輸入檔案讀入 `DataFrame`，這是組織成命名資料行的分散式資料集合。 您可以透過 <xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>設定資料的資料行。 使用 <xref:Microsoft.Spark.Sql.DataFrame.Show%2A> 方法，在您的資料框架中顯示資料。 請務必將 CSV 檔案路徑更新為您所下載之 GitHub 資料的位置。

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

1. 您可以使用 <xref:Microsoft.Spark.Sql.DataFrame.Na%2A> 方法來卸載具有 NA （null）值的資料列，而 <xref:Microsoft.Spark.Sql.DataFrame.Drop%2A> 方法則會從您的資料中移除特定資料行。 如果您嘗試分析與最終分析無關的 null 資料或資料行，這有助於避免錯誤。

   ```csharp
   // Drop any rows with NA values
   DataFrameNaFunctions dropEmptyProjects = projectsDf.Na();
   DataFrame cleanedProjects = dropEmptyProjects.Drop("any");

   // Remove unnecessary columns
   cleanedProjects = cleanedProjects.Drop("id", "url", "owner_id");
   cleanedProjects.Show();
   ```

## <a name="analyze-the-data"></a>分析資料

Spark SQL 可讓您對資料進行 SQL 呼叫。 結合使用者定義函式和 Spark SQL 通常是為了將使用者定義函數套用至資料框架的所有資料列。

您可以特別呼叫 `spark.Sql` 來模擬在其他類型的應用程式中所看到的標準 SQL 呼叫。 您也可以呼叫 <xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A> 和 <xref:Microsoft.Spark.Sql.DataFrame.Agg%2A> 等方法，以明確地結合、篩選及執行資料的計算。

此應用程式的目標是要取得關於 GitHub 專案資料的一些見解。 將下列程式碼片段新增至您的程式，以分析資料。

1. 新增下列程式碼區塊，以尋找每個語言已分叉的次數。 首先，資料會依語言分組。 然後會採用每個語言的平均分支數目。

   ```csharp
   // Average number of times each language has been forked
   DataFrame groupedDF = cleanedProjects
       .GroupBy("language")
       .Agg(Avg(cleanedProjects["forked_from"]);
   ```

1. 新增下列程式碼區塊，以遞減順序排序分支的平均數目，以查看哪些語言最具分叉。 也就是，會先顯示最大的分支數目。

   ```csharp
   // Sort by most forked languages first
   groupedDF.OrderBy(Desc("avg(forked_from)")).Show(); 
   ```

1. 下一個程式碼區塊會顯示最近專案的更新方式。 您註冊名為*MyUDF*的新使用者定義函數，並將它與在教學課程開頭所宣告的日期*s_referenceDate*做比較。 每個專案的日期會與參考日期進行比較。 然後，Spark SQL 會用來在資料的每個資料列上呼叫 UDF，以分析資料集中的每個專案。

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

## <a name="use-spark-submit-to-run-your-app"></a>使用 spark-提交來執行您的應用程式

1. 使用下列命令來建立您的 .NET 應用程式：

   ```dotnetcli
   dotnet build
   ```

1. 使用 `spark-submit`執行您的應用程式。 請務必使用 Microsoft Spark jar 檔案的實際路徑來更新下列命令。

   ```console
   spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /<path>/to/microsoft-spark-<version>.jar dotnet /<path>/to/netcoreapp<version>/GitHubProjects.dll
   ```

## <a name="get-the-code"></a>取得程式碼

您可以在 GitHub 上看到[完整的解決方案](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs)。

## <a name="next-steps"></a>後續步驟

前往下一篇文章，以瞭解如何使用 .NET 來處理串流資料，以進行 Apache Spark。
> [!div class="nextstepaction"]
> [教學課程：使用適用于 Apache Spark 的 .NET 進行結構化串流](streaming.md)
