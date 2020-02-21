---
title: 適用于 Apache Spark 的 .NET 的結構化串流教學課程
description: 在本教學課程中，您將瞭解如何使用適用于 Spark 結構化串流的 .NET 進行 Apache Spark。
author: mamccrea
ms.author: mamccrea
ms.date: 12/04/2019
ms.topic: tutorial
ms.openlocfilehash: 83d44af080d95ab6f9311ddd3ca4860806757436
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77504038"
---
# <a name="tutorial-structured-streaming-with-net-for-apache-spark"></a><span data-ttu-id="e7036-103">教學課程：使用適用于 Apache Spark 的 .NET 進行結構化串流</span><span class="sxs-lookup"><span data-stu-id="e7036-103">Tutorial: Structured Streaming with .NET for Apache Spark</span></span> 

<span data-ttu-id="e7036-104">本教學課程會教您如何使用 .NET 為 Apache Spark 叫用 Spark 結構化串流。</span><span class="sxs-lookup"><span data-stu-id="e7036-104">This tutorial teaches you how to invoke Spark Structured Streaming using .NET for Apache Spark.</span></span> <span data-ttu-id="e7036-105">Spark 結構化串流是 Apache Spark 支援處理即時資料流。</span><span class="sxs-lookup"><span data-stu-id="e7036-105">Spark Structured Streaming is Apache Spark's support for processing real-time data streams.</span></span> <span data-ttu-id="e7036-106">串流處理表示在即時資料產生時進行分析。</span><span class="sxs-lookup"><span data-stu-id="e7036-106">Stream processing means analyzing live data as it's being produced.</span></span>

<span data-ttu-id="e7036-107">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="e7036-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="e7036-108">建立並執行適用于 Apache Spark 應用程式的 .NET</span><span class="sxs-lookup"><span data-stu-id="e7036-108">Create and run a .NET for Apache Spark application</span></span>
> * <span data-ttu-id="e7036-109">使用 netcat 建立資料流程</span><span class="sxs-lookup"><span data-stu-id="e7036-109">Use netcat to create a data stream</span></span>
> * <span data-ttu-id="e7036-110">使用使用者定義函數和 SparkSQL 分析串流資料</span><span class="sxs-lookup"><span data-stu-id="e7036-110">Use user-defined functions and SparkSQL to analyze streaming data</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e7036-111">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="e7036-111">Prerequisites</span></span>

<span data-ttu-id="e7036-112">如果這是您 Apache Spark 應用程式的第一個 .NET，請從[消費者入門教學](get-started.md)課程開始，以熟悉基本概念。</span><span class="sxs-lookup"><span data-stu-id="e7036-112">If this is your first .NET for Apache Spark application, start with the [Getting Started tutorial](get-started.md) to become familiar with the basics.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="e7036-113">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="e7036-113">Create a console application</span></span>

1. <span data-ttu-id="e7036-114">在命令提示字元中，執行下列命令以建立新的主控台應用程式：</span><span class="sxs-lookup"><span data-stu-id="e7036-114">In your command prompt, run the following commands to create a new console application:</span></span>

   ```dotnetcli
   dotnet new console -o mySparkStreamingApp
   cd mySparkStreamingApp
   ```

   <span data-ttu-id="e7036-115">`dotnet` 命令會為您建立類型為 `console` 的 `new` 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e7036-115">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="e7036-116">`-o` 參數會建立名為*mySparkStreamingApp*的目錄，其中儲存您的應用程式，並填入所需的檔案。</span><span class="sxs-lookup"><span data-stu-id="e7036-116">The `-o` parameter creates a directory named *mySparkStreamingApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="e7036-117">`cd mySparkStreamingApp` 命令會將目錄變更為您剛才建立的應用程式目錄。</span><span class="sxs-lookup"><span data-stu-id="e7036-117">The `cd mySparkStreamingApp` command changes the directory to the app directory you just created.</span></span>

1. <span data-ttu-id="e7036-118">若要在應用程式中使用 .NET 進行 Apache Spark，請安裝 Microsoft Spark 套件。</span><span class="sxs-lookup"><span data-stu-id="e7036-118">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="e7036-119">在您的主控台中，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="e7036-119">In your console, run the following command:</span></span>

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="establish-and-connect-to-a-data-stream"></a><span data-ttu-id="e7036-120">建立並連接到資料流程</span><span class="sxs-lookup"><span data-stu-id="e7036-120">Establish and connect to a data stream</span></span>

<span data-ttu-id="e7036-121">測試串流處理的其中一個常用方式是透過**netcat**。</span><span class="sxs-lookup"><span data-stu-id="e7036-121">One popular way to test stream processing is through **netcat**.</span></span> <span data-ttu-id="e7036-122">netcat （也稱為*nc*）可讓您讀取和寫入網路連接。</span><span class="sxs-lookup"><span data-stu-id="e7036-122">netcat (also known as *nc*) allows you to read from and write to network connections.</span></span> <span data-ttu-id="e7036-123">您可以透過終端機視窗來建立與 netcat 的網路連線。</span><span class="sxs-lookup"><span data-stu-id="e7036-123">You establish a network connection with netcat through a terminal window.</span></span> 

### <a name="create-a-data-stream-with-netcat"></a><span data-ttu-id="e7036-124">使用 netcat 建立資料流程</span><span class="sxs-lookup"><span data-stu-id="e7036-124">Create a data stream with netcat</span></span>

1. <span data-ttu-id="e7036-125">[下載 netcat](https://sourceforge.net/projects/nc110/files/)。</span><span class="sxs-lookup"><span data-stu-id="e7036-125">[Download netcat](https://sourceforge.net/projects/nc110/files/).</span></span> <span data-ttu-id="e7036-126">然後，從 zip 下載解壓縮檔案，並將您解壓縮的目錄附加至 "PATH" 環境變數。</span><span class="sxs-lookup"><span data-stu-id="e7036-126">Then, extract the file from the zip download and append the directory you extracted to your "PATH" environment variable.</span></span>

2. <span data-ttu-id="e7036-127">若要啟動新的連線，請開啟新的主控台，然後執行下列命令，以連線至埠9999上的 localhost。</span><span class="sxs-lookup"><span data-stu-id="e7036-127">To start a new connection, open a new console and run the following command which connects to localhost on port 9999.</span></span>

   <span data-ttu-id="e7036-128">在 Windows 上：</span><span class="sxs-lookup"><span data-stu-id="e7036-128">On Windows:</span></span>

   ```console
   nc -vvv -l -p 9999
   ```

   <span data-ttu-id="e7036-129">在 Linux 上：</span><span class="sxs-lookup"><span data-stu-id="e7036-129">On Linux:</span></span>

   ```console
   nc -lk 9999
   ```

   <span data-ttu-id="e7036-130">您的 Spark 程式會接聽您在此命令提示字元中鍵入的輸入。</span><span class="sxs-lookup"><span data-stu-id="e7036-130">Your Spark program listens for the input you type into this command prompt.</span></span>

### <a name="create-a-sparksession"></a><span data-ttu-id="e7036-131">建立 SparkSession</span><span class="sxs-lookup"><span data-stu-id="e7036-131">Create a SparkSession</span></span>

1. <span data-ttu-id="e7036-132">在*mySparkStreamingApp*中，將下列額外的 `using` 語句新增至*Program.cs*檔案的頂端：</span><span class="sxs-lookup"><span data-stu-id="e7036-132">Add the following additional `using` statements to the top of the *Program.cs* file in *mySparkStreamingApp*:</span></span>

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using Microsoft.Spark.Sql.Streaming;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. <span data-ttu-id="e7036-133">將下列程式碼新增至您的 `Main` 方法，以建立新的 `SparkSession`。</span><span class="sxs-lookup"><span data-stu-id="e7036-133">Add the following code to your `Main` method to create a new `SparkSession`.</span></span> <span data-ttu-id="e7036-134">Spark 會話是使用 Dataset 和資料框架 API 來程式設計 Spark 的進入點。</span><span class="sxs-lookup"><span data-stu-id="e7036-134">The Spark Session is the entry point to programming Spark with the Dataset and DataFrame API.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("Streaming example with a UDF")
        .GetOrCreate();
   ```

   <span data-ttu-id="e7036-135">呼叫上述所建立的*spark*物件，可讓您在整個程式中存取 Spark 和資料框架功能。</span><span class="sxs-lookup"><span data-stu-id="e7036-135">Calling the *spark* object created above allows you to access Spark and DataFrame functionality throughout your program.</span></span>

### <a name="connect-to-a-stream-with-readstream"></a><span data-ttu-id="e7036-136">使用 ReadStream （）連接到資料流程</span><span class="sxs-lookup"><span data-stu-id="e7036-136">Connect to a stream with ReadStream()</span></span>

<span data-ttu-id="e7036-137">`ReadStream()` 方法會傳回可用來以 `DataFrame`的形式讀取串流資料的 `DataStreamReader`。</span><span class="sxs-lookup"><span data-stu-id="e7036-137">The `ReadStream()` method returns a `DataStreamReader` that can be used to read streaming data in as a `DataFrame`.</span></span> <span data-ttu-id="e7036-138">包含主機和埠資訊，告訴您的 Spark 應用程式在何處預期其串流資料。</span><span class="sxs-lookup"><span data-stu-id="e7036-138">Include the host and port information to tell your Spark app where to expect its streaming data.</span></span>

```csharp
DataFrame lines = spark
    .ReadStream()
    .Format("socket")
    .Option("host", hostname)
    .Option("port", port)
    .Load();
```

## <a name="register-a-user-defined-function"></a><span data-ttu-id="e7036-139">註冊使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="e7036-139">Register a user-defined function</span></span>

<span data-ttu-id="e7036-140">您可以在 Spark 應用程式中使用 Udf、*使用者定義*的函式，對您的資料執行計算和分析。</span><span class="sxs-lookup"><span data-stu-id="e7036-140">You can use UDFs, *user-defined functions*, in Spark applications to perform calculations and analysis on your data.</span></span>

<span data-ttu-id="e7036-141">將下列程式碼新增至您的 `Main` 方法，以註冊名為 `udfArray`的 UDF。</span><span class="sxs-lookup"><span data-stu-id="e7036-141">Add the following code to your `Main` method to register a UDF called `udfArray`.</span></span> 

```csharp
Func<Column, Column> udfArray =
    Udf<string, string[]>((str) => new string[] { str, $"{str} {str.Length}" });
```

<span data-ttu-id="e7036-142">此 UDF 會處理它從 netcat 終端機接收的每個字串，以產生陣列，其中包含原始字串（包含在*str*中），後面接著以原始字串長度串連的原始字串。</span><span class="sxs-lookup"><span data-stu-id="e7036-142">This UDF processes each string it receives from the netcat terminal to produce an array that includes the original string (contained in *str*), followed by the original string concatenated with the length of the original string.</span></span> 

<span data-ttu-id="e7036-143">例如，在 netcat 終端機中輸入*Hello world*會產生一個陣列，其中：</span><span class="sxs-lookup"><span data-stu-id="e7036-143">For example, entering *Hello world* in the netcat terminal produces an array where:</span></span>

* <span data-ttu-id="e7036-144">陣列\[0] = Hello world</span><span class="sxs-lookup"><span data-stu-id="e7036-144">array\[0] = Hello world</span></span>
* <span data-ttu-id="e7036-145">陣列\[1] = Hello world 11</span><span class="sxs-lookup"><span data-stu-id="e7036-145">array\[1] = Hello world 11</span></span>

## <a name="use-sparksql"></a><span data-ttu-id="e7036-146">使用 SparkSQL</span><span class="sxs-lookup"><span data-stu-id="e7036-146">Use SparkSQL</span></span>

<span data-ttu-id="e7036-147">使用 SparkSQL 對儲存在資料框架中的資料執行各種功能。</span><span class="sxs-lookup"><span data-stu-id="e7036-147">Use SparkSQL to perform various functions on the data stored in your DataFrame.</span></span> <span data-ttu-id="e7036-148">結合 Udf 和 SparkSQL 以將 UDF 套用至資料框架的每個資料列是很常見的。</span><span class="sxs-lookup"><span data-stu-id="e7036-148">It's common to combine UDFs and SparkSQL to apply a UDF to each row of a DataFrame.</span></span>

```csharp
DataFrame arrayDF = lines.Select(Explode(udfArray(lines["value"])));
```

<span data-ttu-id="e7036-149">此程式碼片段會將*udfArray*套用至資料框架中的每個值，這代表從您的 netcat 終端機讀取的每個字串。</span><span class="sxs-lookup"><span data-stu-id="e7036-149">This code snippet applies *udfArray* to each value in your DataFrame, which represents each string read from your netcat terminal.</span></span> <span data-ttu-id="e7036-150">套用 SparkSQL 方法 <xref:Microsoft.Spark.Sql.Functions.Explode%2A>，將陣列的每個專案放在它自己的資料列中。</span><span class="sxs-lookup"><span data-stu-id="e7036-150">Apply the SparkSQL method <xref:Microsoft.Spark.Sql.Functions.Explode%2A> to put each entry of your array in its own row.</span></span> <span data-ttu-id="e7036-151">最後，使用 <xref:Microsoft.Spark.Sql.DataFrame.Select%2A>，將您在新的資料框架 ArrayDF 中所產生的資料行放在其中 *。*</span><span class="sxs-lookup"><span data-stu-id="e7036-151">Finally, use <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> to place the columns you've produced in the new DataFrame *arrayDF.*</span></span>

## <a name="display-your-stream"></a><span data-ttu-id="e7036-152">顯示您的串流</span><span class="sxs-lookup"><span data-stu-id="e7036-152">Display your stream</span></span>

<span data-ttu-id="e7036-153">使用 <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> 來建立輸出的特性，例如將結果列印到主控台，以及只顯示最新的輸出。</span><span class="sxs-lookup"><span data-stu-id="e7036-153">Use <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> to establish characteristics of your output, such as printing results to the console and displaying only the most recent output.</span></span>

```csharp
StreamingQuery query = arrayDf
    .WriteStream()
    .Format("console")
    .Start();
```

## <a name="run-your-code"></a><span data-ttu-id="e7036-154">執行您的程式碼</span><span class="sxs-lookup"><span data-stu-id="e7036-154">Run your code</span></span>

<span data-ttu-id="e7036-155">Spark 中的結構化串流會透過一系列的小型**批次**來處理資料。</span><span class="sxs-lookup"><span data-stu-id="e7036-155">Structured streaming in Spark processes data through a series of small **batches**.</span></span>  <span data-ttu-id="e7036-156">當您執行程式時，您建立 netcat 連接的命令提示字元可讓您開始輸入。</span><span class="sxs-lookup"><span data-stu-id="e7036-156">When you run your program, the command prompt where you establish the netcat connection allows you to start typing.</span></span> <span data-ttu-id="e7036-157">每次您在該命令提示字元中輸入資料後按下 Enter 鍵，Spark 就會將您的輸入視為批次並執行 UDF。</span><span class="sxs-lookup"><span data-stu-id="e7036-157">Each time you press the Enter key after typing data in that command prompt, Spark considers your entry a batch and runs the UDF.</span></span>

### <a name="use-spark-submit-to-run-your-app"></a><span data-ttu-id="e7036-158">使用 spark-提交來執行您的應用程式</span><span class="sxs-lookup"><span data-stu-id="e7036-158">Use spark-submit to run your app</span></span>

<span data-ttu-id="e7036-159">啟動新的 netcat 會話之後，請開啟新的終端機，然後執行您的 `spark-submit` 命令，類似下列命令：</span><span class="sxs-lookup"><span data-stu-id="e7036-159">After starting a new netcat session, open a new terminal and run your `spark-submit` command, similar to the following command:</span></span>

```powershell
spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /path/to/microsoft-spark-<version>.jar Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkCharacterCount localhost 9999
```

> [!NOTE]
> <span data-ttu-id="e7036-160">請務必使用 Microsoft Spark jar 檔案的實際路徑來更新上述命令。</span><span class="sxs-lookup"><span data-stu-id="e7036-160">Be sure to update the above command with the actual path to your Microsoft Spark jar file.</span></span> <span data-ttu-id="e7036-161">上述命令也會假設您的 netcat 伺服器正在 localhost 通訊埠9999上執行。</span><span class="sxs-lookup"><span data-stu-id="e7036-161">The above command also assumes your netcat server is running on localhost port 9999.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="e7036-162">取得程式碼</span><span class="sxs-lookup"><span data-stu-id="e7036-162">Get the code</span></span>

<span data-ttu-id="e7036-163">本教學課程使用[StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs)範例，但 GitHub 上有其他三個完整的串流處理範例：</span><span class="sxs-lookup"><span data-stu-id="e7036-163">This tutorial uses the [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) example, but there are three other full stream processing examples on GitHub:</span></span>

* <span data-ttu-id="e7036-164">[StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)：從任何來源串流處理的資料字數統計</span><span class="sxs-lookup"><span data-stu-id="e7036-164">[StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): word count on data streamed from any source</span></span>
* <span data-ttu-id="e7036-165">[StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs)：使用視窗化邏輯對資料進行字數統計</span><span class="sxs-lookup"><span data-stu-id="e7036-165">[StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): word count on data with windowing logic</span></span>
* <span data-ttu-id="e7036-166">[StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)：從 Kafka 串流處理的資料字數統計</span><span class="sxs-lookup"><span data-stu-id="e7036-166">[StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): word count on data streamed from Kafka</span></span>

## <a name="next-steps"></a><span data-ttu-id="e7036-167">後續步驟</span><span class="sxs-lookup"><span data-stu-id="e7036-167">Next steps</span></span>

<span data-ttu-id="e7036-168">前往下一篇文章，以瞭解如何將您的 .NET for Apache Spark 應用程式部署至 Databricks。</span><span class="sxs-lookup"><span data-stu-id="e7036-168">Advance to the next article to learn how to deploy your .NET for Apache Spark application to Databricks.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="e7036-169">教學課程：將適用于 Apache Spark 應用程式的 .NET 部署至 Databricks</span><span class="sxs-lookup"><span data-stu-id="e7036-169">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>](databricks-deployment.md)
