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
# <a name="tutorial-do-batch-processing-with-net-for-apache-spark"></a>教程：使用 .NET 進行批次處理，用於 Apache Spark

在本教程中，您將瞭解如何使用 .NET 進行 Apache Spark 的批次處理。 批次處理是靜止資料轉換，這意味著來源資料已載入到資料存儲中。

批次處理通常通過大型平面資料集執行，這些資料集需要準備進行進一步分析。 日誌處理和資料倉儲是常見的批次處理方案。 在此方案中，您可以分析有關 GitHub 專案的資訊，例如不同專案分叉的時間數或最近專案的更新時間。

在本教學課程中，您會了解如何：

> [!div class="checklist"]
>
> * 為 Apache Spark 應用程式創建和運行 .NET
> * 將資料讀取到資料框架中並準備進行分析
> * 使用 Spark SQL 處理資料

## <a name="prerequisites"></a>必要條件

如果這是您第一次使用 .NET 進行 Apache Spark，請查看[.NET 開始為 Apache Spark](../tutorials/get-started.md)教程，瞭解如何準備您的環境並運行您的第一個 .NET 用於 Apache Spark 應用程式。

## <a name="download-the-sample-data"></a>下載範例資料

[GHTorrent](http://ghtorrent.org/)監視所有公共 GitHub 事件，例如有關專案、提交和觀察程式的資訊，並將事件及其結構存儲在資料庫中。 在不同時間段收集的資料可作為可下載的存檔提供。 由於轉儲檔非常大，本指南使用可從 GitHub 下載[的轉儲檔的截斷版本](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/projects_smaller.csv)。

> [!NOTE]
> GHTorrent 資料集在雙重許可計畫 （[知識共用 +](https://wiki.creativecommons.org/wiki/CCPlus)） 下分發。 對於非商業用途（包括但不限於教育、研究或個人用途），資料集在[CC-BY-SA 許可證](https://creativecommons.org/licenses/by-sa/4.0/)下分發。

## <a name="create-a-console-application"></a>建立主控台應用程式

1. 在命令提示符中，運行以下命令以創建新的主控台應用程式：

   ```dotnetcli
   dotnet new console -o mySparkBatchApp
   cd mySparkBatchApp
   ```

   該`dotnet`命令為您創建`new`類型`console`應用程式。 該`-o`參數創建一個名為*mySparkBatchApp*的目錄，其中存儲你的應用，並將其填充到所需的檔中。 該`cd mySparkBatchApp`命令將目錄更改為您剛剛創建的應用目錄。

1. 要在應用中使用的阿帕奇 Spark 的 .NET，請安裝 Microsoft.Spark 包。 在主控台中，運行以下命令：

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="create-a-sparksession"></a>創建火花會話

1. 將以下附加`using`語句添加到*mySparkBatchApp*中*Program.cs*檔的頂部。

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. 將以下代碼添加到專案命名空間。 *s_referenceData*在程式中稍後用於根據日期進行篩選。

   ```csharp
   static readonly DateTime s_referenceDate = new DateTime(2015, 10, 20);
   ```

1. 在 Main 方法中添加以下代碼，以建立新的 SparkSession。 SparkSession 是使用資料集和資料幀 API 程式設計 Spark 的進入點。 通過調用物件`spark`，您可以在整個程式中訪問 Spark 和 DataFrame 功能。

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("GitHub and Spark Batch")
        .GetOrCreate();
   ```

## <a name="prepare-the-data"></a>準備資料

1. 將輸入檔讀入`DataFrame`中，這是組織到命名列中的分散式資料集合。 您可以通過 設置資料的列<xref:Microsoft.Spark.Sql.DataFrame.Schema%2A>。 使用<xref:Microsoft.Spark.Sql.DataFrame.Show%2A>方法在資料框架中顯示資料。 請務必將 CSV 檔路徑更新到您下載的 GitHub 資料的位置。

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

1. 使用<xref:Microsoft.Spark.Sql.DataFrame.Na%2A>方法刪除具有 NA（空）值的行，<xref:Microsoft.Spark.Sql.DataFrame.Drop%2A>以及從資料中刪除某些列的方法。 如果您嘗試分析與最終分析無關的空資料或列，這有助於防止錯誤。

   ```csharp
   // Drop any rows with NA values
   DataFrameNaFunctions dropEmptyProjects = projectsDf.Na();
   DataFrame cleanedProjects = dropEmptyProjects.Drop("any");

   // Remove unnecessary columns
   cleanedProjects = cleanedProjects.Drop("id", "url", "owner_id");
   cleanedProjects.Show();
   ```

## <a name="analyze-the-data"></a>分析資料

Spark SQL 允許您對資料進行 SQL 調用。 通常將使用者定義的函數和 Spark SQL 組合在一起，將使用者定義的函數應用於 DataFrame 的所有行。

您可以專門調用`spark.Sql`以類比其他類型的應用中看到的標準 SQL 調用。 您還可以調用方法，如<xref:Microsoft.Spark.Sql.DataFrame.GroupBy%2A>和<xref:Microsoft.Spark.Sql.DataFrame.Agg%2A>專門組合、篩選和執行對資料的計算。

此應用程式的目標是獲取有關 GitHub 專案資料的一些見解。 向程式添加以下程式碼片段以分析資料。

1. 添加以下代碼塊可查找每種語言分叉的次數。 首先，資料按語言分組。 然後，從每種語言的平均分叉數被取走。

   ```csharp
   // Average number of times each language has been forked
   DataFrame groupedDF = cleanedProjects
       .GroupBy("language")
       .Agg(Avg(cleanedProjects["forked_from"]);
   ```

1. 添加以下代碼塊以按降冪排列叉的平均數量，以查看哪些語言是分叉最多的。 也就是說，將首先出現最多數量的分叉。

   ```csharp
   // Sort by most forked languages first
   groupedDF.OrderBy(Desc("avg(forked_from)")).Show();
   ```

1. 下一個代碼塊顯示最近專案的更新方式。 註冊名為*MyUDF*的新使用者定義的函數，並將其與在本教程開頭聲明的日期*s_referenceDate*進行比較。 將每個專案的日期與參考日期進行比較。 然後，Spark SQL 用於調用資料每行上的 UDF 來分析資料集中的每個專案。

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

1. 調用`spark.Stop()`結束 SparkSession。

## <a name="use-spark-submit-to-run-your-app"></a>使用火花提交運行應用

1. 使用以下命令生成 .NET 應用：

   ```dotnetcli
   dotnet build
   ```

1. 使用`spark-submit`運行應用。 請務必使用 Microsoft Spark jar 檔的實際路徑更新以下命令。

   ```console
   spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /<path>/to/microsoft-spark-<version>.jar dotnet /<path>/to/netcoreapp<version>/GitHubProjects.dll
   ```

## <a name="get-the-code"></a>取得程式碼

您可以在 GitHub 上看到[完整的解決方案](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/GitHubProjects.cs)。

## <a name="next-steps"></a>後續步驟

進入下一篇文章，瞭解如何使用 .NET 處理 Apache Spark 的流資料。
> [!div class="nextstepaction"]
> [教程：結構化流與 .NET 的 Apache Spark](streaming.md)
