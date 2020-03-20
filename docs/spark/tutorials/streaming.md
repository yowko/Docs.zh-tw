---
title: 結構化流與 .NET 的 Apache Spark 教程
description: 在本教程中，您將瞭解如何將 .NET 用於 Apache Spark 進行 Spark 結構化流式處理。
author: mamccrea
ms.author: mamccrea
ms.date: 12/04/2019
ms.topic: tutorial
ms.openlocfilehash: 125ef834da8e42c99c8080a3d5414a7927ce7636
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79186504"
---
# <a name="tutorial-structured-streaming-with-net-for-apache-spark"></a><span data-ttu-id="d6ca8-103">教程：結構化流與 .NET 的 Apache Spark</span><span class="sxs-lookup"><span data-stu-id="d6ca8-103">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>

<span data-ttu-id="d6ca8-104">本教程教您如何使用 .NET 為 Apache Spark 調用 Spark 結構化流。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-104">This tutorial teaches you how to invoke Spark Structured Streaming using .NET for Apache Spark.</span></span> <span data-ttu-id="d6ca8-105">Spark 結構化流是 Apache Spark 對處理即時資料流的支援。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-105">Spark Structured Streaming is Apache Spark's support for processing real-time data streams.</span></span> <span data-ttu-id="d6ca8-106">流處理意味著在生成即時資料時對其進行分析。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-106">Stream processing means analyzing live data as it's being produced.</span></span>

<span data-ttu-id="d6ca8-107">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="d6ca8-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="d6ca8-108">為 Apache Spark 應用程式創建和運行 .NET</span><span class="sxs-lookup"><span data-stu-id="d6ca8-108">Create and run a .NET for Apache Spark application</span></span>
> * <span data-ttu-id="d6ca8-109">使用 netcat 創建資料流程</span><span class="sxs-lookup"><span data-stu-id="d6ca8-109">Use netcat to create a data stream</span></span>
> * <span data-ttu-id="d6ca8-110">使用使用者定義的函數和 SparkSQL 分析流資料</span><span class="sxs-lookup"><span data-stu-id="d6ca8-110">Use user-defined functions and SparkSQL to analyze streaming data</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d6ca8-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="d6ca8-111">Prerequisites</span></span>

<span data-ttu-id="d6ca8-112">如果這是您的第一個 .NET 用於 Apache Spark 應用程式，請從[入門教程](get-started.md)開始，瞭解基礎知識。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-112">If this is your first .NET for Apache Spark application, start with the [Getting Started tutorial](get-started.md) to become familiar with the basics.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="d6ca8-113">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="d6ca8-113">Create a console application</span></span>

1. <span data-ttu-id="d6ca8-114">在命令提示符中，運行以下命令以創建新的主控台應用程式：</span><span class="sxs-lookup"><span data-stu-id="d6ca8-114">In your command prompt, run the following commands to create a new console application:</span></span>

   ```dotnetcli
   dotnet new console -o mySparkStreamingApp
   cd mySparkStreamingApp
   ```

   <span data-ttu-id="d6ca8-115">該`dotnet`命令為您創建`new`類型`console`應用程式。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-115">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="d6ca8-116">該`-o`參數創建一個名為*mySparkStreamingApp*的目錄，其中存儲你的應用，並將其填充到所需的檔中。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-116">The `-o` parameter creates a directory named *mySparkStreamingApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="d6ca8-117">該`cd mySparkStreamingApp`命令將目錄更改為您剛剛創建的應用目錄。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-117">The `cd mySparkStreamingApp` command changes the directory to the app directory you just created.</span></span>

1. <span data-ttu-id="d6ca8-118">要在應用中使用的阿帕奇 Spark 的 .NET，請安裝 Microsoft.Spark 包。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-118">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="d6ca8-119">在主控台中，運行以下命令：</span><span class="sxs-lookup"><span data-stu-id="d6ca8-119">In your console, run the following command:</span></span>

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="establish-and-connect-to-a-data-stream"></a><span data-ttu-id="d6ca8-120">建立並連接到資料流程</span><span class="sxs-lookup"><span data-stu-id="d6ca8-120">Establish and connect to a data stream</span></span>

<span data-ttu-id="d6ca8-121">測試流處理的一種流行方法是通過**netcat。**</span><span class="sxs-lookup"><span data-stu-id="d6ca8-121">One popular way to test stream processing is through **netcat**.</span></span> <span data-ttu-id="d6ca8-122">netcat（也稱為*nc*）允許您從網路連接讀取和寫入網路連接。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-122">netcat (also known as *nc*) allows you to read from and write to network connections.</span></span> <span data-ttu-id="d6ca8-123">通過終端視窗與網貓建立網路連接。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-123">You establish a network connection with netcat through a terminal window.</span></span>

### <a name="create-a-data-stream-with-netcat"></a><span data-ttu-id="d6ca8-124">使用網貓創建資料流程</span><span class="sxs-lookup"><span data-stu-id="d6ca8-124">Create a data stream with netcat</span></span>

1. <span data-ttu-id="d6ca8-125">[下載網貓](https://sourceforge.net/projects/nc110/files/)。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-125">[Download netcat](https://sourceforge.net/projects/nc110/files/).</span></span> <span data-ttu-id="d6ca8-126">然後，從 zip 下載中提取檔，並將提取的目錄追加到"PATH"環境變數。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-126">Then, extract the file from the zip download and append the directory you extracted to your "PATH" environment variable.</span></span>

2. <span data-ttu-id="d6ca8-127">要啟動新連接，請打開一個新主控台並運行以下命令，該命令連接到埠 9999 上的本地主機。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-127">To start a new connection, open a new console and run the following command which connects to localhost on port 9999.</span></span>

   <span data-ttu-id="d6ca8-128">在 Windows 上：</span><span class="sxs-lookup"><span data-stu-id="d6ca8-128">On Windows:</span></span>

   ```console
   nc -vvv -l -p 9999
   ```

   <span data-ttu-id="d6ca8-129">在 Linux 上：</span><span class="sxs-lookup"><span data-stu-id="d6ca8-129">On Linux:</span></span>

   ```console
   nc -lk 9999
   ```

   <span data-ttu-id="d6ca8-130">Spark 程式偵聽您在此命令提示符中鍵入的輸入。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-130">Your Spark program listens for the input you type into this command prompt.</span></span>

### <a name="create-a-sparksession"></a><span data-ttu-id="d6ca8-131">創建火花會話</span><span class="sxs-lookup"><span data-stu-id="d6ca8-131">Create a SparkSession</span></span>

1. <span data-ttu-id="d6ca8-132">將以下附加`using`語句添加到*mySparkStreamingApp*中*Program.cs*檔的頂部 ：</span><span class="sxs-lookup"><span data-stu-id="d6ca8-132">Add the following additional `using` statements to the top of the *Program.cs* file in *mySparkStreamingApp*:</span></span>

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using Microsoft.Spark.Sql.Streaming;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. <span data-ttu-id="d6ca8-133">將以下代碼添加到方法`Main`以創建新的`SparkSession`。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-133">Add the following code to your `Main` method to create a new `SparkSession`.</span></span> <span data-ttu-id="d6ca8-134">Spark 會話是使用資料集和資料幀 API 程式設計 Spark 的進入點。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-134">The Spark Session is the entry point to programming Spark with the Dataset and DataFrame API.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("Streaming example with a UDF")
        .GetOrCreate();
   ```

   <span data-ttu-id="d6ca8-135">調用上面創建的*火花*物件允許您在整個程式中訪問 Spark 和 DataFrame 功能。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-135">Calling the *spark* object created above allows you to access Spark and DataFrame functionality throughout your program.</span></span>

### <a name="connect-to-a-stream-with-readstream"></a><span data-ttu-id="d6ca8-136">使用 ReadStream 連接到流（）</span><span class="sxs-lookup"><span data-stu-id="d6ca8-136">Connect to a stream with ReadStream()</span></span>

<span data-ttu-id="d6ca8-137">該方法`ReadStream()`返回 可用於`DataStreamReader`讀取流資料作為`DataFrame`的 。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-137">The `ReadStream()` method returns a `DataStreamReader` that can be used to read streaming data in as a `DataFrame`.</span></span> <span data-ttu-id="d6ca8-138">包括主機和埠資訊，告訴 Spark 應用在何處預期其流資料。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-138">Include the host and port information to tell your Spark app where to expect its streaming data.</span></span>

```csharp
DataFrame lines = spark
    .ReadStream()
    .Format("socket")
    .Option("host", hostname)
    .Option("port", port)
    .Load();
```

## <a name="register-a-user-defined-function"></a><span data-ttu-id="d6ca8-139">註冊使用者定義的函數</span><span class="sxs-lookup"><span data-stu-id="d6ca8-139">Register a user-defined function</span></span>

<span data-ttu-id="d6ca8-140">您可以在 Spark 應用程式中使用*使用者定義的函數*UdF 對資料執行計算和分析。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-140">You can use UDFs, *user-defined functions*, in Spark applications to perform calculations and analysis on your data.</span></span>

<span data-ttu-id="d6ca8-141">將以下代碼添加到方法`Main`以註冊稱為`udfArray`的 UDF。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-141">Add the following code to your `Main` method to register a UDF called `udfArray`.</span></span>

```csharp
Func<Column, Column> udfArray =
    Udf<string, string[]>((str) => new string[] { str, $"{str} {str.Length}" });
```

<span data-ttu-id="d6ca8-142">此 UDF 處理它從 netcat 終端接收的每個字串以生成包含原始字串（包含在*str*中）的陣列，然後是與原始字串長度串聯的原始字串。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-142">This UDF processes each string it receives from the netcat terminal to produce an array that includes the original string (contained in *str*), followed by the original string concatenated with the length of the original string.</span></span>

<span data-ttu-id="d6ca8-143">例如，在 netcat 終端中輸入*Hello 世界*會產生一個陣列，其中：</span><span class="sxs-lookup"><span data-stu-id="d6ca8-143">For example, entering *Hello world* in the netcat terminal produces an array where:</span></span>

* <span data-ttu-id="d6ca8-144">陣列\[0+ = 你好世界</span><span class="sxs-lookup"><span data-stu-id="d6ca8-144">array\[0] = Hello world</span></span>
* <span data-ttu-id="d6ca8-145">陣列\[1] = 您世界 11</span><span class="sxs-lookup"><span data-stu-id="d6ca8-145">array\[1] = Hello world 11</span></span>

## <a name="use-sparksql"></a><span data-ttu-id="d6ca8-146">使用 SparkSQL</span><span class="sxs-lookup"><span data-stu-id="d6ca8-146">Use SparkSQL</span></span>

<span data-ttu-id="d6ca8-147">使用 SparkSQL 對存儲在資料幀中的資料執行各種功能。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-147">Use SparkSQL to perform various functions on the data stored in your DataFrame.</span></span> <span data-ttu-id="d6ca8-148">通常將 UDF 和 SparkSQL 組合在一起，將 UDF 應用於 DataFrame 的每一行。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-148">It's common to combine UDFs and SparkSQL to apply a UDF to each row of a DataFrame.</span></span>

```csharp
DataFrame arrayDF = lines.Select(Explode(udfArray(lines["value"])));
```

<span data-ttu-id="d6ca8-149">此程式碼片段將*udfArray*應用於 DataFrame 中的每個值，該值表示從 netcat 終端讀取的每個字串。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-149">This code snippet applies *udfArray* to each value in your DataFrame, which represents each string read from your netcat terminal.</span></span> <span data-ttu-id="d6ca8-150">應用 SparkSQL<xref:Microsoft.Spark.Sql.Functions.Explode%2A>方法將陣列的每個條目放在自己的行中。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-150">Apply the SparkSQL method <xref:Microsoft.Spark.Sql.Functions.Explode%2A> to put each entry of your array in its own row.</span></span> <span data-ttu-id="d6ca8-151">最後，使用<xref:Microsoft.Spark.Sql.DataFrame.Select%2A>將已生成的列放在新的 DataFrame*陣列DF*中。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-151">Finally, use <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> to place the columns you've produced in the new DataFrame *arrayDF.*</span></span>

## <a name="display-your-stream"></a><span data-ttu-id="d6ca8-152">顯示流</span><span class="sxs-lookup"><span data-stu-id="d6ca8-152">Display your stream</span></span>

<span data-ttu-id="d6ca8-153">用於<xref:Microsoft.Spark.Sql.DataFrame.WriteStream>建立輸出的特徵，例如將結果列印到主控台並僅顯示最新的輸出。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-153">Use <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> to establish characteristics of your output, such as printing results to the console and displaying only the most recent output.</span></span>

```csharp
StreamingQuery query = arrayDf
    .WriteStream()
    .Format("console")
    .Start();
```

## <a name="run-your-code"></a><span data-ttu-id="d6ca8-154">運行代碼</span><span class="sxs-lookup"><span data-stu-id="d6ca8-154">Run your code</span></span>

<span data-ttu-id="d6ca8-155">Spark 中的結構化流通過一系列小**批量**處理資料。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-155">Structured streaming in Spark processes data through a series of small **batches**.</span></span>  <span data-ttu-id="d6ca8-156">運行程式時，建立 netcat 連接的命令提示允許您開始鍵入。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-156">When you run your program, the command prompt where you establish the netcat connection allows you to start typing.</span></span> <span data-ttu-id="d6ca8-157">每次在命令提示符中鍵入資料後按 Enter 鍵時，Spark 都會將您的條目視為一個批次處理並運行 UDF。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-157">Each time you press the Enter key after typing data in that command prompt, Spark considers your entry a batch and runs the UDF.</span></span>

### <a name="use-spark-submit-to-run-your-app"></a><span data-ttu-id="d6ca8-158">使用火花提交運行應用</span><span class="sxs-lookup"><span data-stu-id="d6ca8-158">Use spark-submit to run your app</span></span>

<span data-ttu-id="d6ca8-159">啟動新的 netcat 會話後，打開一個新終端並運行`spark-submit`命令，類似于以下命令：</span><span class="sxs-lookup"><span data-stu-id="d6ca8-159">After starting a new netcat session, open a new terminal and run your `spark-submit` command, similar to the following command:</span></span>

```powershell
spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /path/to/microsoft-spark-<version>.jar Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkCharacterCount localhost 9999
```

> [!NOTE]
> <span data-ttu-id="d6ca8-160">請務必使用 Microsoft Spark jar 檔的實際路徑更新上述命令。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-160">Be sure to update the above command with the actual path to your Microsoft Spark jar file.</span></span> <span data-ttu-id="d6ca8-161">上述命令還假定您的 netcat 伺服器正在本地主機埠 9999 上運行。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-161">The above command also assumes your netcat server is running on localhost port 9999.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="d6ca8-162">取得程式碼</span><span class="sxs-lookup"><span data-stu-id="d6ca8-162">Get the code</span></span>

<span data-ttu-id="d6ca8-163">本教程使用[StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs)示例，但 GitHub 上還有三個完整的流處理示例：</span><span class="sxs-lookup"><span data-stu-id="d6ca8-163">This tutorial uses the [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) example, but there are three other full stream processing examples on GitHub:</span></span>

* <span data-ttu-id="d6ca8-164">[StructuredNetworkWordCount.cs：](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)字計數從任何源資料流的資料</span><span class="sxs-lookup"><span data-stu-id="d6ca8-164">[StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): word count on data streamed from any source</span></span>
* <span data-ttu-id="d6ca8-165">[StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs)： 具有視窗邏輯的資料的字數</span><span class="sxs-lookup"><span data-stu-id="d6ca8-165">[StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): word count on data with windowing logic</span></span>
* <span data-ttu-id="d6ca8-166">[StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)： 字計數從卡夫卡流的資料</span><span class="sxs-lookup"><span data-stu-id="d6ca8-166">[StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): word count on data streamed from Kafka</span></span>

## <a name="next-steps"></a><span data-ttu-id="d6ca8-167">後續步驟</span><span class="sxs-lookup"><span data-stu-id="d6ca8-167">Next steps</span></span>

<span data-ttu-id="d6ca8-168">進入下一篇文章，瞭解如何將用於 Apache Spark 的 .NET 應用程式部署到 Databricks。</span><span class="sxs-lookup"><span data-stu-id="d6ca8-168">Advance to the next article to learn how to deploy your .NET for Apache Spark application to Databricks.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="d6ca8-169">教程：將用於 Apache Spark 應用程式的 .NET 部署到資料磚塊</span><span class="sxs-lookup"><span data-stu-id="d6ca8-169">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>](databricks-deployment.md)
