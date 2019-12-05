---
title: 適用于 Apache Spark 的 .NET 的結構化串流教學課程
description: 在本教學課程中，您將瞭解如何使用適用于 Spark 結構化串流的 .NET 進行 Apache Spark。
author: mamccrea
ms.author: mamccrea
ms.date: 12/04/2019
ms.topic: tutorial
ms.openlocfilehash: d0fe79ef79125c06be9acd8ba80001a33e150adb
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802844"
---
# <a name="tutorial-structured-streaming-with-net-for-apache-spark"></a>教學課程：使用適用于 Apache Spark 的 .NET 進行結構化串流 

本教學課程會教您如何使用 .NET 為 Apache Spark 叫用 Spark 結構化串流。 Spark 結構化串流是 Apache Spark 支援處理即時資料流。 串流處理表示在即時資料產生時進行分析。

在本教學課程中，您將了解如何：

> [!div class="checklist"]
>
> * 建立並執行適用于 Apache Spark 應用程式的 .NET
> * 使用 netcat 建立資料流程
> * 使用使用者定義函數和 SparkSQL 分析串流資料

## <a name="prerequisites"></a>必要條件：

如果這是您 Apache Spark 應用程式的第一個 .NET，請從[消費者入門教學](get-started.md)課程開始，以熟悉基本概念。

## <a name="create-a-console-application"></a>建立主控台應用程式

1. 在命令提示字元中，執行下列命令以建立新的主控台應用程式：

   ```console
   dotnet new console -o mySparkStreamingApp
   cd mySparkStreamingApp
   ```

   `dotnet` 命令會為您建立類型為 `console` 的 `new` 應用程式。 `-o` 參數會建立名為*mySparkStreamingApp*的目錄，其中儲存您的應用程式，並填入所需的檔案。 `cd mySparkStreamingApp` 命令會將目錄變更為您剛才建立的應用程式目錄。

1. 若要在應用程式中使用 .NET 進行 Apache Spark，請安裝 Microsoft Spark 套件。 在您的主控台中，執行下列命令：

   ```console
   dotnet add package Microsoft.Spark
   ```

## <a name="establish-and-connect-to-a-data-stream"></a>建立並連接到資料流程

測試串流處理的其中一個常用方式是透過**netcat**。 netcat （也稱為*nc*）可讓您讀取和寫入網路連接。 您可以透過終端機視窗來建立與 netcat 的網路連線。 

### <a name="create-a-data-stream-with-netcat"></a>使用 netcat 建立資料流程

1. [下載 netcat](https://sourceforge.net/projects/nc110/files/)。 然後，從 zip 下載解壓縮檔案，並將您解壓縮的目錄附加至 "PATH" 環境變數。

2. 若要啟動新的連線，請開啟新的主控台，然後執行下列命令，以連線至埠9999上的 localhost。

   在 Windows 上：

   ```console
   nc -vvv -l -p 9999
   ```

   在 Linux 上：

   ```console
   nc -lk 9999
   ```

   您的 Spark 程式會接聽您在此命令提示字元中鍵入的輸入。

### <a name="create-a-sparksession"></a>建立 SparkSession

1. 在*mySparkStreamingApp*中，將下列額外的 `using` 語句新增至*Program.cs*檔案的頂端：

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using Microsoft.Spark.Sql.Streaming;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. 將下列程式碼新增至您的 `Main` 方法，以建立新的 `SparkSession`。 Spark 會話是使用 Dataset 和資料框架 API 來程式設計 Spark 的進入點。

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("Streaming example with a UDF")
        .GetOrCreate();
   ```

   呼叫上述所建立的*spark*物件，可讓您在整個程式中存取 Spark 和資料框架功能。

### <a name="connect-to-a-stream-with-readstream"></a>使用 ReadStream （）連接到資料流程

`ReadStream()` 方法會傳回可用來以 `DataFrame`的形式讀取串流資料的 `DataStreamReader`。 包含主機和埠資訊，告訴您的 Spark 應用程式在何處預期其串流資料。

```csharp
DataFrame lines = spark
    .ReadStream()
    .Format("socket")
    .Option("host", hostname)
    .Option("port", port)
    .Load();
```

## <a name="register-a-user-defined-function"></a>註冊使用者定義函數

您可以在 Spark 應用程式中使用 Udf、*使用者定義*的函式，對您的資料執行計算和分析。

將下列程式碼新增至您的 `Main` 方法，以註冊名為 `udfArray`的 UDF。 

```csharp
Func<Column, Column> udfArray =
    Udf<string, string[]>((str) => new string[] { str, $"{str} {str.Length}" });
```

此 UDF 會處理它從 netcat 終端機接收的每個字串，以產生陣列，其中包含原始字串（包含在*str*中），後面接著以原始字串長度串連的原始字串。 

例如，在 netcat 終端機中輸入*Hello world*會產生一個陣列，其中：

* 陣列\[0] = Hello world
* 陣列\[1] = Hello world 11

## <a name="use-sparksql"></a>使用 SparkSQL

使用 SparkSQL 對儲存在資料框架中的資料執行各種功能。 結合 Udf 和 SparkSQL 以將 UDF 套用至資料框架的每個資料列是很常見的。

```csharp
DataFrame arrayDF = lines.Select(Explode(udfArray(lines["value"])));
```

此程式碼片段會將*udfArray*套用至資料框架中的每個值，這代表從您的 netcat 終端機讀取的每個字串。 套用 SparkSQL 方法 <xref:Microsoft.Spark.Sql.Functions.Explode%2A>，將陣列的每個專案放在它自己的資料列中。 最後，使用 <xref:Microsoft.Spark.Sql.DataFrame.Select%2A>，將您在新的資料框架 ArrayDF 中所產生的資料行放在其中 *。*

## <a name="display-your-stream"></a>顯示您的串流

使用 <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> 來建立輸出的特性，例如將結果列印到主控台，以及只顯示最新的輸出。

```csharp
StreamingQuery query = arrayDf
    .WriteStream()
    .Format("console")
    .Start();
```

## <a name="run-your-code"></a>執行您的程式碼

Spark 中的結構化串流會透過一系列的小型**批次**來處理資料。  當您執行程式時，您建立 netcat 連接的命令提示字元可讓您開始輸入。 每次您在該命令提示字元中輸入資料後按下 Enter 鍵，Spark 就會將您的輸入視為批次並執行 UDF。

### <a name="use-spark-submit-to-run-your-app"></a>使用 spark-提交來執行您的應用程式

啟動新的 netcat 會話之後，請開啟新的終端機，然後執行您的 `spark-submit` 命令，類似下列命令：

```powershell
spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /path/to/microsoft-spark-<version>.jar Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkCharacterCount localhost 9999
```

> [!NOTE]
> 請務必使用 Microsoft Spark jar 檔案的實際路徑來更新上述命令。 上述命令也會假設您的 netcat 伺服器正在 localhost 通訊埠9999上執行。

## <a name="get-the-code"></a>取得程式碼

本教學課程使用[StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs)範例，但 GitHub 上有其他三個完整的串流處理範例：

* [StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)：從任何來源串流處理的資料字數統計
* [StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs)：使用視窗化邏輯對資料進行字數統計
* [StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)：從 Kafka 串流處理的資料字數統計

## <a name="next-steps"></a>後續步驟

前往下一篇文章，以瞭解如何將您的 .NET for Apache Spark 應用程式部署至 Databricks。
> [!div class="nextstepaction"]
> [教學課程：將適用于 Apache Spark 應用程式的 .NET 部署至 Databricks](databricks-deployment.md)
