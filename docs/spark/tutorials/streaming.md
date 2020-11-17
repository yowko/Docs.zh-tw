---
title: 使用 .NET 的結構化串流進行 Apache Spark 教學課程
description: 在本教學課程中，您將瞭解如何使用 .NET 進行 Spark 結構化串流的 Apache Spark。
author: mamccrea
ms.author: mamccrea
ms.date: 10/09/2020
ms.topic: tutorial
ms.openlocfilehash: 3a02ac52155971f480c7f0c338d4a2a9a7d1d81c
ms.sourcegitcommit: 34968a61e9bac0f6be23ed6ffb837f52d2390c85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2020
ms.locfileid: "94688016"
---
# <a name="tutorial-structured-streaming-with-net-for-apache-spark"></a><span data-ttu-id="26240-103">教學課程：使用 .NET 進行 Apache Spark 的結構化串流</span><span class="sxs-lookup"><span data-stu-id="26240-103">Tutorial: Structured Streaming with .NET for Apache Spark</span></span>

<span data-ttu-id="26240-104">本教學課程會教您如何使用 .NET 針對 Apache Spark 叫用 Spark 結構化串流。</span><span class="sxs-lookup"><span data-stu-id="26240-104">This tutorial teaches you how to invoke Spark Structured Streaming using .NET for Apache Spark.</span></span> <span data-ttu-id="26240-105">Spark 結構化串流是 Apache Spark 處理即時資料串流的支援。</span><span class="sxs-lookup"><span data-stu-id="26240-105">Spark Structured Streaming is Apache Spark's support for processing real-time data streams.</span></span> <span data-ttu-id="26240-106">串流處理表示在即時資料產生時進行分析。</span><span class="sxs-lookup"><span data-stu-id="26240-106">Stream processing means analyzing live data as it's being produced.</span></span>

<span data-ttu-id="26240-107">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="26240-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="26240-108">建立和執行 Apache Spark 應用程式的 .NET</span><span class="sxs-lookup"><span data-stu-id="26240-108">Create and run a .NET for Apache Spark application</span></span>
> * <span data-ttu-id="26240-109">使用 netcat 建立資料流程</span><span class="sxs-lookup"><span data-stu-id="26240-109">Use netcat to create a data stream</span></span>
> * <span data-ttu-id="26240-110">使用使用者定義函數和 SparkSQL 來分析串流資料</span><span class="sxs-lookup"><span data-stu-id="26240-110">Use user-defined functions and SparkSQL to analyze streaming data</span></span>

## <a name="prerequisites"></a><span data-ttu-id="26240-111">先決條件</span><span class="sxs-lookup"><span data-stu-id="26240-111">Prerequisites</span></span>

<span data-ttu-id="26240-112">如果這是您第一個適用于 Apache Spark 應用程式的 .NET，請從 [消費者入門教學](get-started.md) 課程開始，以熟悉基本概念。</span><span class="sxs-lookup"><span data-stu-id="26240-112">If this is your first .NET for Apache Spark application, start with the [Getting Started tutorial](get-started.md) to become familiar with the basics.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="26240-113">建立主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="26240-113">Create a console application</span></span>

1. <span data-ttu-id="26240-114">在命令提示字元中，執行下列命令以建立新的主控台應用程式：</span><span class="sxs-lookup"><span data-stu-id="26240-114">In your command prompt, run the following commands to create a new console application:</span></span>

   ```dotnetcli
   dotnet new console -o mySparkStreamingApp
   cd mySparkStreamingApp
   ```

   <span data-ttu-id="26240-115">此 `dotnet` 命令 `new` 會為您建立類型的應用程式 `console` 。</span><span class="sxs-lookup"><span data-stu-id="26240-115">The `dotnet` command creates a `new` application of type `console` for you.</span></span> <span data-ttu-id="26240-116">`-o`參數會建立名為 *mySparkStreamingApp* 的目錄，您的應用程式會儲存在此目錄中，並填入必要的檔案。</span><span class="sxs-lookup"><span data-stu-id="26240-116">The `-o` parameter creates a directory named *mySparkStreamingApp* where your app is stored and populates it with the required files.</span></span> <span data-ttu-id="26240-117">此 `cd mySparkStreamingApp` 命令會將目錄變更為您剛才建立的應用程式目錄。</span><span class="sxs-lookup"><span data-stu-id="26240-117">The `cd mySparkStreamingApp` command changes the directory to the app directory you just created.</span></span>

1. <span data-ttu-id="26240-118">若要在應用程式中使用 .NET 進行 Apache Spark，請安裝 Microsoft Spark 套件。</span><span class="sxs-lookup"><span data-stu-id="26240-118">To use .NET for Apache Spark in an app, install the Microsoft.Spark package.</span></span> <span data-ttu-id="26240-119">在主控台中，執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="26240-119">In your console, run the following command:</span></span>

   ```dotnetcli
   dotnet add package Microsoft.Spark
   ```

## <a name="establish-and-connect-to-a-data-stream"></a><span data-ttu-id="26240-120">建立並連接到資料流程</span><span class="sxs-lookup"><span data-stu-id="26240-120">Establish and connect to a data stream</span></span>

<span data-ttu-id="26240-121">測試串流處理的一種常用方法是透過 **netcat**。</span><span class="sxs-lookup"><span data-stu-id="26240-121">One popular way to test stream processing is through **netcat**.</span></span> <span data-ttu-id="26240-122">netcat (也稱為 *nc*) 可讓您讀取和寫入網路連接。</span><span class="sxs-lookup"><span data-stu-id="26240-122">netcat (also known as *nc*) allows you to read from and write to network connections.</span></span> <span data-ttu-id="26240-123">您可以透過終端機視窗與 netcat 建立網路連線。</span><span class="sxs-lookup"><span data-stu-id="26240-123">You establish a network connection with netcat through a terminal window.</span></span>

### <a name="create-a-data-stream-with-netcat"></a><span data-ttu-id="26240-124">使用 netcat 建立資料流程</span><span class="sxs-lookup"><span data-stu-id="26240-124">Create a data stream with netcat</span></span>

1. <span data-ttu-id="26240-125">[下載 netcat](https://sourceforge.net/projects/nc110/files/)。</span><span class="sxs-lookup"><span data-stu-id="26240-125">[Download netcat](https://sourceforge.net/projects/nc110/files/).</span></span> <span data-ttu-id="26240-126">然後，從 zip 下載中解壓縮檔案，並將您解壓縮的目錄附加至「路徑」環境變數。</span><span class="sxs-lookup"><span data-stu-id="26240-126">Then, extract the file from the zip download and append the directory you extracted to your "PATH" environment variable.</span></span>

2. <span data-ttu-id="26240-127">若要開始新的連線，請開啟新的主控台並執行下列命令，以連線到埠9999上的 localhost。</span><span class="sxs-lookup"><span data-stu-id="26240-127">To start a new connection, open a new console and run the following command which connects to localhost on port 9999.</span></span>

   <span data-ttu-id="26240-128">在 Windows 上：</span><span class="sxs-lookup"><span data-stu-id="26240-128">On Windows:</span></span>

   ```console
   nc -vvv -l -p 9999
   ```

   <span data-ttu-id="26240-129">在 Linux 上：</span><span class="sxs-lookup"><span data-stu-id="26240-129">On Linux:</span></span>

   ```console
   nc -lk 9999
   ```

   <span data-ttu-id="26240-130">您的 Spark 程式會接聽您在這個命令提示字元中輸入的輸入。</span><span class="sxs-lookup"><span data-stu-id="26240-130">Your Spark program listens for the input you type into this command prompt.</span></span>

### <a name="create-a-sparksession"></a><span data-ttu-id="26240-131">建立 SparkSession</span><span class="sxs-lookup"><span data-stu-id="26240-131">Create a SparkSession</span></span>

1. <span data-ttu-id="26240-132">`using`在 *mySparkStreamingApp* 中的 *Program.cs* 檔案頂端新增下列其他語句：</span><span class="sxs-lookup"><span data-stu-id="26240-132">Add the following additional `using` statements to the top of the *Program.cs* file in *mySparkStreamingApp*:</span></span>

   ```csharp
   using System;
   using Microsoft.Spark.Sql;
   using Microsoft.Spark.Sql.Streaming;
   using static Microsoft.Spark.Sql.Functions;
   ```

1. <span data-ttu-id="26240-133">將下列程式碼新增至您 `Main` 的方法，以建立新的 `SparkSession` 。</span><span class="sxs-lookup"><span data-stu-id="26240-133">Add the following code to your `Main` method to create a new `SparkSession`.</span></span> <span data-ttu-id="26240-134">Spark 會話是使用資料集和資料框架 API 對 Spark 進行程式設計的進入點。</span><span class="sxs-lookup"><span data-stu-id="26240-134">The Spark Session is the entry point to programming Spark with the Dataset and DataFrame API.</span></span>

   ```csharp
   SparkSession spark = SparkSession
        .Builder()
        .AppName("Streaming example with a UDF")
        .GetOrCreate();
   ```

   <span data-ttu-id="26240-135">呼叫上面建立的 *spark* 物件，可讓您存取整個程式中的 Spark 和資料框架功能。</span><span class="sxs-lookup"><span data-stu-id="26240-135">Calling the *spark* object created above allows you to access Spark and DataFrame functionality throughout your program.</span></span>

### <a name="connect-to-a-stream-with-readstream"></a><span data-ttu-id="26240-136">使用 ReadStream 連接到串流 ( # A1</span><span class="sxs-lookup"><span data-stu-id="26240-136">Connect to a stream with ReadStream()</span></span>

<span data-ttu-id="26240-137">`ReadStream()`方法 `DataStreamReader` 會傳回，可以用來讀取中的串流資料 `DataFrame` 。</span><span class="sxs-lookup"><span data-stu-id="26240-137">The `ReadStream()` method returns a `DataStreamReader` that can be used to read streaming data in as a `DataFrame`.</span></span> <span data-ttu-id="26240-138">包含主機和埠資訊，讓您的 Spark 應用程式知道其串流資料的預期位置。</span><span class="sxs-lookup"><span data-stu-id="26240-138">Include the host and port information to tell your Spark app where to expect its streaming data.</span></span>

```csharp
DataFrame lines = spark
    .ReadStream()
    .Format("socket")
    .Option("host", hostname)
    .Option("port", port)
    .Load();
```

## <a name="register-a-user-defined-function"></a><span data-ttu-id="26240-139">註冊使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="26240-139">Register a user-defined function</span></span>

<span data-ttu-id="26240-140">您可以在 Spark 應用程式中使用 Udf、 *使用者定義函式*，對您的資料執行計算和分析。</span><span class="sxs-lookup"><span data-stu-id="26240-140">You can use UDFs, *user-defined functions*, in Spark applications to perform calculations and analysis on your data.</span></span>

<span data-ttu-id="26240-141">將下列程式碼新增至您 `Main` 的方法，以註冊名為的 UDF `udfArray` 。</span><span class="sxs-lookup"><span data-stu-id="26240-141">Add the following code to your `Main` method to register a UDF called `udfArray`.</span></span>

```csharp
Func<Column, Column> udfArray =
    Udf<string, string[]>((str) => new string[] { str, $"{str} {str.Length}" });
```

<span data-ttu-id="26240-142">此 UDF 會處理它從 netcat 終端機收到的每個字串，以產生陣列，其中包含 *str*) 中包含的原始字串 (，後面接著以原始字串的長度串連的原始字串。</span><span class="sxs-lookup"><span data-stu-id="26240-142">This UDF processes each string it receives from the netcat terminal to produce an array that includes the original string (contained in *str*), followed by the original string concatenated with the length of the original string.</span></span>

<span data-ttu-id="26240-143">例如，在 netcat 終端機中輸入 *Hello world* 會產生陣列，其中：</span><span class="sxs-lookup"><span data-stu-id="26240-143">For example, entering *Hello world* in the netcat terminal produces an array where:</span></span>

* <span data-ttu-id="26240-144">陣列 \[ 0] = Hello world</span><span class="sxs-lookup"><span data-stu-id="26240-144">array\[0] = Hello world</span></span>
* <span data-ttu-id="26240-145">陣列 \[ 1] = Hello world 11</span><span class="sxs-lookup"><span data-stu-id="26240-145">array\[1] = Hello world 11</span></span>

## <a name="use-sparksql"></a><span data-ttu-id="26240-146">使用 SparkSQL</span><span class="sxs-lookup"><span data-stu-id="26240-146">Use SparkSQL</span></span>

<span data-ttu-id="26240-147">使用 SparkSQL 對儲存在資料框架中的資料執行各種功能。</span><span class="sxs-lookup"><span data-stu-id="26240-147">Use SparkSQL to perform various functions on the data stored in your DataFrame.</span></span> <span data-ttu-id="26240-148">通常會結合 Udf 和 SparkSQL，將 UDF 套用至資料框架的每個資料列。</span><span class="sxs-lookup"><span data-stu-id="26240-148">It's common to combine UDFs and SparkSQL to apply a UDF to each row of a DataFrame.</span></span>

```csharp
DataFrame arrayDF = lines.Select(Explode(udfArray(lines["value"])));
```

<span data-ttu-id="26240-149">此程式碼片段會將 *udfArray* 套用至資料框架中的每個值，代表從 netcat 終端機讀取的每個字串。</span><span class="sxs-lookup"><span data-stu-id="26240-149">This code snippet applies *udfArray* to each value in your DataFrame, which represents each string read from your netcat terminal.</span></span> <span data-ttu-id="26240-150">套用 SparkSQL 方法 <xref:Microsoft.Spark.Sql.Functions.Explode%2A> ，將陣列的每個專案放在它自己的資料列中。</span><span class="sxs-lookup"><span data-stu-id="26240-150">Apply the SparkSQL method <xref:Microsoft.Spark.Sql.Functions.Explode%2A> to put each entry of your array in its own row.</span></span> <span data-ttu-id="26240-151">最後，使用 <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> 來放置您在新的資料框架 arrayDF 中產生的資料行 *。*</span><span class="sxs-lookup"><span data-stu-id="26240-151">Finally, use <xref:Microsoft.Spark.Sql.DataFrame.Select%2A> to place the columns you've produced in the new DataFrame *arrayDF.*</span></span>

## <a name="display-your-stream"></a><span data-ttu-id="26240-152">顯示您的串流</span><span class="sxs-lookup"><span data-stu-id="26240-152">Display your stream</span></span>

<span data-ttu-id="26240-153">用 <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> 來建立輸出的特性，例如將結果列印到主控台，並只顯示最新的輸出。</span><span class="sxs-lookup"><span data-stu-id="26240-153">Use <xref:Microsoft.Spark.Sql.DataFrame.WriteStream> to establish characteristics of your output, such as printing results to the console and displaying only the most recent output.</span></span>

```csharp
StreamingQuery query = arrayDf
    .WriteStream()
    .Format("console")
    .Start();
```

## <a name="run-your-code"></a><span data-ttu-id="26240-154">執行您的程式碼</span><span class="sxs-lookup"><span data-stu-id="26240-154">Run your code</span></span>

<span data-ttu-id="26240-155">Spark 中的結構化串流會透過一系列的小型 **批次** 處理資料。</span><span class="sxs-lookup"><span data-stu-id="26240-155">Structured streaming in Spark processes data through a series of small **batches**.</span></span>  <span data-ttu-id="26240-156">當您執行程式時，命令提示字元可讓您建立 netcat 連線，讓您開始輸入。</span><span class="sxs-lookup"><span data-stu-id="26240-156">When you run your program, the command prompt where you establish the netcat connection allows you to start typing.</span></span> <span data-ttu-id="26240-157">每次您在命令提示字元中輸入資料後按下 Enter 鍵時，Spark 都會將您的專案視為批次，並執行 UDF。</span><span class="sxs-lookup"><span data-stu-id="26240-157">Each time you press the Enter key after typing data in that command prompt, Spark considers your entry a batch and runs the UDF.</span></span>

### <a name="use-spark-submit-to-run-your-app"></a><span data-ttu-id="26240-158">使用 spark 提交來執行您的應用程式</span><span class="sxs-lookup"><span data-stu-id="26240-158">Use spark-submit to run your app</span></span>

<span data-ttu-id="26240-159">開始新的 netcat 會話之後，請開啟新的終端機，並執行您 `spark-submit` 的命令，類似于下列命令：</span><span class="sxs-lookup"><span data-stu-id="26240-159">After starting a new netcat session, open a new terminal and run your `spark-submit` command, similar to the following command:</span></span>

```powershell
spark-submit --class org.apache.spark.deploy.dotnet.DotnetRunner --master local /path/to/microsoft-spark-<spark_majorversion-spark_minorversion>_<scala_majorversion.scala_minorversion>-<spark_dotnet_version>.jar Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkCharacterCount localhost 9999
```

> [!NOTE]
> <span data-ttu-id="26240-160">請務必使用 Microsoft Spark jar 檔案的實際路徑來更新上述命令。</span><span class="sxs-lookup"><span data-stu-id="26240-160">Be sure to update the above command with the actual path to your Microsoft Spark jar file.</span></span> <span data-ttu-id="26240-161">上述命令也會假設您的 netcat 伺服器正在 localhost 埠9999上執行。</span><span class="sxs-lookup"><span data-stu-id="26240-161">The above command also assumes your netcat server is running on localhost port 9999.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="26240-162">取得程式碼</span><span class="sxs-lookup"><span data-stu-id="26240-162">Get the code</span></span>

<span data-ttu-id="26240-163">本教學課程使用 [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) 範例，但在 GitHub 上有三個其他完整的串流處理範例：</span><span class="sxs-lookup"><span data-stu-id="26240-163">This tutorial uses the [StructuredNetworkCharacterCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkCharacterCount.cs) example, but there are three other full stream processing examples on GitHub:</span></span>

* <span data-ttu-id="26240-164">[StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)：從任何來源進行資料流程處理的字數統計</span><span class="sxs-lookup"><span data-stu-id="26240-164">[StructuredNetworkWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs): word count on data streamed from any source</span></span>
* <span data-ttu-id="26240-165">[StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs)：具有視窗邏輯之資料的字數統計</span><span class="sxs-lookup"><span data-stu-id="26240-165">[StructuredNetworkWordCountWindowed.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCountWindowed.cs): word count on data with windowing logic</span></span>
* <span data-ttu-id="26240-166">[StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)：從 Kafka 串流處理之資料的字數統計</span><span class="sxs-lookup"><span data-stu-id="26240-166">[StructuredKafkaWordCount.cs](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs): word count on data streamed from Kafka</span></span>

## <a name="next-steps"></a><span data-ttu-id="26240-167">後續步驟</span><span class="sxs-lookup"><span data-stu-id="26240-167">Next steps</span></span>

<span data-ttu-id="26240-168">前進到下一篇文章，以瞭解如何將 .NET for Apache Spark 應用程式部署至 Databricks。</span><span class="sxs-lookup"><span data-stu-id="26240-168">Advance to the next article to learn how to deploy your .NET for Apache Spark application to Databricks.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="26240-169">教學課程：將 Apache Spark 應用程式的 .NET 部署至 Databricks</span><span class="sxs-lookup"><span data-stu-id="26240-169">Tutorial: Deploy a .NET for Apache Spark application to Databricks</span></span>](databricks-deployment.md)
