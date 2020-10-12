---
title: 使用 .NET 的結構化串流進行 Apache Spark 教學課程
description: 在本教學課程中，您將瞭解如何使用 .NET 進行 Spark 結構化串流的 Apache Spark。
author: mamccrea
ms.author: mamccrea
ms.date: 10/09/2020
ms.topic: tutorial
ms.openlocfilehash: 47c716db931dc912b80844fe69283b12d030c238
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955573"
---
# <a name="tutorial-structured-streaming-with-net-for-apache-spark"></a>教學課程：使用 .NET 進行 Apache Spark 的結構化串流

本教學課程會教您如何使用 .NET 針對 Apache Spark 叫用 Spark 結構化串流。 Spark 結構化串流是 Apache Spark 處理即時資料串流的支援。 串流處理表示在即時資料產生時進行分析。

在本教學課程中，您會了解如何：

> [!div class="checklist"]
>
> * 建立和執行 Apache Spark 應用程式的 .NET
> * 使用 netcat 建立資料流程
> * 使用使用者定義函數和 SparkSQL 來分析串流資料

## <a name="prerequisites"></a>必要條件

如果這是您第一個適用于 Apache Spark 應用程式的 .NET，請從 [消費者入門教學](get-started.md) 課程開始，以熟悉基本概念。

## <a name="create-a-console-application"></a>建立主控台應用程式

1. 在命令提示字元中，執行下列命令以建立新的主控台應用程式：

   ```dotnetcli
   dotnet new console -o mySparkStreamingApp
   cd mySparkStreamingApp
   ```

   此 `dotnet` 命令 `new` 會為您建立類型的應用程式 `console` 。 `-o`參數會建立名為*mySparkStreamingApp*的目錄，您的應用程式會儲存在此目錄中，並填入必要的檔案。 此 `cd mySparkStreamingApp` 命令會將目錄變更為您剛才建立的應用程式目錄。

1. 若要在應用程式中使用 .NET 進行 Apache Spark，請安裝 Microsoft Spark 套件。 在主控台中，執行下列命令：

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="establish-and-connect-to-a-data-stream"></a>建立並連接到資料流程

測試串流處理的一種常用方法是透過 **netcat**。 netcat (也稱為 *nc*) 可讓您讀取和寫入網路連接。 您可以透過終端機視窗與 netcat 建立網路連線。

### <a name="create-a-data-stream-with-netcat"></a>使用 netcat 建立資料流程

1. [下載 netcat](https://sourceforge.net/projects/nc110/files/)。 然後，從 zip 下載中解壓縮檔案，並將您解壓縮的目錄附加至「路徑」環境變數。

2. 若要開始新的連線，請開啟新的主控台並執行下列命令，以連線到埠9999上的 localhost。

   在 Windows 上：

   ```console
   nc -vvv -l -p 9999
   ```

   在 Linux 上：

   ```console
   nc -lk 9999
   ```

   您的 Spark 程式會接聽您在這個命令提示字元中輸入的輸入。

### <a name="create-a-sparksession"></a>建立 SparkSession

1. `using`在*mySparkStreamingApp*中的*Program.cs*檔案頂端新增下列其他語句：

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using Microsoft.Spark.Sql.Streaming;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. 將下列程式碼新增至您 `Main` 的方法，以建立新的 `SparkSession` 。 Spark 會話是使用資料集和資料框架 API 對 Spark 進行程式設計的進入點。

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("Streaming example with a UDF")
        .GetOrCreate();
   ```

   呼叫上面建立的 *spark* 物件，可讓您存取整個程式中的 Spark 和資料框架功能。

### <a name="connect-to-a-stream-with-readstream"></a>使用 ReadStream 連接到串流 ( # A1

`ReadStream()`方法 `DataStreamReader` 會傳回，可以用來讀取中的串流資料 `DataFrame` 。 包含主機和埠資訊，讓您的 Spark 應用程式知道其串流資料的預期位置。

```csharp
DataFrame lines = spark
    .ReadStream()
    .Format("socket")
    .Option("host", hostname)
    .Option("port", port)
    .Load();
```

## <a name="register-a-user-defined-function"></a>註冊使用者定義函數

您可以在 Spark 應用程式中使用 Udf、 *使用者定義函式*，對您的資料執行計算和分析。

將下列程式碼新增至您 `Main` 的方法，以註冊名為的 UDF `udfArray` 。

```csharp
Func<Column, Column> udfArray =
    Udf<string, string[]>((str) => new string[] { str, $"{str} {str.Length}" });
```

此 UDF 會處理它從 netcat 終端機收到的每個字串，以產生陣列，其中包含 *str*) 中包含的原始字串 (，後面接著以原始字串的長度串連的原始字串。

例如，在 netcat 終端機中輸入 *Hello world* 會產生陣列，其中：

* 陣列 \[ 0] = Hello world
* 陣列 \[ 1] = Hello world 11

## <a name="use-sparksql"></a>使用 SparkSQL

使用 SparkSQL 對儲存在資料框架中的資料執行各種功能。 通常會結合 Udf 和 SparkSQL，將 UDF 套用至資料框架的每個資料列。

```csharp
DataFrame arrayDF = lines.Select(Explode(udfArray(lines["value"])));
```

此程式碼片段會將 *udfArray* 套用至資料框架中的每個值，代表從 netcat 終端機讀取的每個字串。 套用 SparkSQL 方法 <xref:Microsoft.Spark.Sql.Functions.Explode%2A> ，將陣列的每個專案放在它自己的資料列中。 最後，使用 <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> 來放置您在新的資料框架 arrayDF 中產生的資料行 *。*

## <a name="display-your-stream"></a>顯示您的串流

用 <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> 來建立輸出的特性，例如將結果列印到主控台，並只顯示最新的輸出。

```csharp
StreamingQuery query = arrayDf
    .WriteStream()
    .Format("console")
    .Start();
```

## <a name="run-your-code"></a>執行您的程式碼

Spark 中的結構化串流會透過一系列的小型 **批次**處理資料。  當您執行程式時，命令提示字元可讓您建立 netcat 連線，讓您開始輸入。 每次您在命令提示字元中輸入資料後按下 Enter 鍵時，Spark 都會將您的專案視為批次，並執行 UDF。

### <a name="use-spark-submit-to-run-your-app"></a>使用 spark 提交來執行您的應用程式

開始新的 netcat 會話之後，請開啟新的終端機，並執行您 `spark-submit` 的命令，類似于下列命令：

```powershell
spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /path/to/microsoft-spark-<version>.jar Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkCharacterCount localhost 9999
```

> [!NOTE]
> 請務必使用 Microsoft Spark jar 檔案的實際路徑來更新上述命令。 上述命令也會假設您的 netcat 伺服器正在 localhost 埠9999上執行。

## <a name="get-the-code"></a>取得程式碼

本教學課程使用 [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) 範例，但在 GitHub 上有三個其他完整的串流處理範例：

* [StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)：從任何來源進行資料流程處理的字數統計
* [StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs)：具有視窗邏輯之資料的字數統計
* [StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)：從 Kafka 串流處理之資料的字數統計

## <a name="next-steps"></a>後續步驟

前進到下一篇文章，以瞭解如何將 .NET for Apache Spark 應用程式部署至 Databricks。
> [!div class="nextstepaction"]
> [教學課程：將 Apache Spark 應用程式的 .NET 部署至 Databricks](databricks-deployment.md)
