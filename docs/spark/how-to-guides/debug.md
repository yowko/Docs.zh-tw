---
title: 對 Windows 上的 .NET for Apache Spark 應用程式進行偵錯
description: 了解如何對 Windows 上的 .NET for Apache Spark 應用程式進行偵錯。
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: dac6aed1f7faba7f07b722a6dac0da930ab9ec66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79185814"
---
# <a name="debug-a-net-for-apache-spark-application"></a><span data-ttu-id="5cbd1-103">對 .NET for Apache Spark 應用程式進行偵錯</span><span class="sxs-lookup"><span data-stu-id="5cbd1-103">Debug a .NET for Apache Spark application</span></span>

<span data-ttu-id="5cbd1-104">此手如何提供在 Windows 上調試的 apache Spark 應用程式 .NET 的步驟。</span><span class="sxs-lookup"><span data-stu-id="5cbd1-104">This how-to provides the steps to debug your .NET for Apache Spark application on Windows.</span></span>

## <a name="debug-your-application"></a><span data-ttu-id="5cbd1-105">為您的應用程式偵錯</span><span class="sxs-lookup"><span data-stu-id="5cbd1-105">Debug your application</span></span>

<span data-ttu-id="5cbd1-106">打開新的命令提示視窗並運行以下命令：</span><span class="sxs-lookup"><span data-stu-id="5cbd1-106">Open a new command prompt window and run the following command:</span></span>

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

<span data-ttu-id="5cbd1-107">當您執行命令時，您會看到下列輸出：</span><span class="sxs-lookup"><span data-stu-id="5cbd1-107">When you run the command, you see the following output:</span></span>

```console
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

<span data-ttu-id="5cbd1-108">在偵錯模式下，DotnetRunner 不會啟動 .NET 應用程式，而是等待您啟動 .NET 應用。</span><span class="sxs-lookup"><span data-stu-id="5cbd1-108">In debug mode, DotnetRunner does not launch the .NET application, but instead waits for you to start the .NET app.</span></span> <span data-ttu-id="5cbd1-109">保持此命令提示視窗打開，並通過 C# 調試器啟動 .NET 應用程式以調試應用程式。</span><span class="sxs-lookup"><span data-stu-id="5cbd1-109">Leave this command prompt window open and start your .NET application through C# debugger to debug your application.</span></span> <span data-ttu-id="5cbd1-110">使用 C# 調試器啟動 .NET 應用程式[（Windows/macOS 的視覺化工作室調試器](https://visualstudio.microsoft.com/vs/)或[視覺化工作室代碼中的 C# 調試器擴展](https://code.visualstudio.com/Docs/editor/debugging)器），以調試應用程式。</span><span class="sxs-lookup"><span data-stu-id="5cbd1-110">Start your .NET application with a C# debugger ([Visual Studio Debugger for Windows/macOS](https://visualstudio.microsoft.com/vs/) or [C# Debugger Extension in Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)) to debug your application.</span></span>

## <a name="debug-a-user-defined-function-udf"></a><span data-ttu-id="5cbd1-111">調試使用者定義的函數 （UDF）</span><span class="sxs-lookup"><span data-stu-id="5cbd1-111">Debug a user-defined function (UDF)</span></span>

> [!NOTE]
> <span data-ttu-id="5cbd1-112">使用者定義的功能僅在具有視覺化工作室調試器的 Windows 上受支援。</span><span class="sxs-lookup"><span data-stu-id="5cbd1-112">User-defined functions are supported only on Windows with Visual Studio Debugger.</span></span>

<span data-ttu-id="5cbd1-113">在運行`spark-submit`之前，設置以下環境變數：</span><span class="sxs-lookup"><span data-stu-id="5cbd1-113">Before running `spark-submit`, set the following environment variable:</span></span>

```bat
set DOTNET_WORKER_DEBUG=1
```

<span data-ttu-id="5cbd1-114">運行 Spark 應用程式時，將`Choose Just-In-Time Debugger`彈出一個視窗。</span><span class="sxs-lookup"><span data-stu-id="5cbd1-114">When you run your Spark application, a `Choose Just-In-Time Debugger` window will pop up.</span></span> <span data-ttu-id="5cbd1-115">選擇視覺化工作室調試器。</span><span class="sxs-lookup"><span data-stu-id="5cbd1-115">Choose a Visual Studio debugger.</span></span>

<span data-ttu-id="5cbd1-116">調試器將在[TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52)中的以下位置中斷：</span><span class="sxs-lookup"><span data-stu-id="5cbd1-116">The debugger will break at the following location in [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52):</span></span>

```csharp
if (EnvironmentUtils.GetEnvironmentVariableAsBool("DOTNET_WORKER_DEBUG"))
{
    Debugger.Launch(); // <-- The debugger will break here.
}
```

<span data-ttu-id="5cbd1-117">導航到包含計畫調試的 UDF 的 *.cs*檔，並[設置中斷點](https://docs.microsoft.com/visualstudio/debugger/using-breakpoints?view=vs-2019)。</span><span class="sxs-lookup"><span data-stu-id="5cbd1-117">Navigate to the *.cs* file that contains the UDF that you plan to debug, and [set a breakpoint](https://docs.microsoft.com/visualstudio/debugger/using-breakpoints?view=vs-2019).</span></span> <span data-ttu-id="5cbd1-118">中斷點將說`The breakpoint will not currently be hit`，因為工作人員尚未載入包含 UDF 的程式集。</span><span class="sxs-lookup"><span data-stu-id="5cbd1-118">The breakpoint will say `The breakpoint will not currently be hit` because the worker hasn't loaded the assembly that contains UDF yet.</span></span>

<span data-ttu-id="5cbd1-119">命中`F5`以繼續您的應用程式，中斷點最終將被擊中。</span><span class="sxs-lookup"><span data-stu-id="5cbd1-119">Hit `F5` to continue your application and the breakpoint will eventually be hit.</span></span>

> [!NOTE]
> <span data-ttu-id="5cbd1-120">為每個任務彈出"選擇即時調試器"視窗。</span><span class="sxs-lookup"><span data-stu-id="5cbd1-120">The Choose Just-In-Time Debugger window pops up for each task.</span></span> <span data-ttu-id="5cbd1-121">為避免快顯視窗過多，請將執行器數設置為低數。</span><span class="sxs-lookup"><span data-stu-id="5cbd1-121">To avoid excessive pop-ups, set the number of executors to a low number.</span></span> <span data-ttu-id="5cbd1-122">例如，可以使用 **--master local{1}** 選項進行火花提交，將任務數設置為 1，從而啟動單個調試器實例。</span><span class="sxs-lookup"><span data-stu-id="5cbd1-122">For example, you can use the **--master local[1]** option for spark-submit to set the number of tasks to 1, which launches a single debugger instance.</span></span>

## <a name="debug-scala-code"></a><span data-ttu-id="5cbd1-123">對 Scala 程式碼進行偵錯</span><span class="sxs-lookup"><span data-stu-id="5cbd1-123">Debug Scala code</span></span>

<span data-ttu-id="5cbd1-124">如果需要調試 Scala 端代碼 （`DotnetRunner`等`DotnetBackendHandler`），可以使用以下命令並使用[IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html)將調試器附加到正在運行的進程：</span><span class="sxs-lookup"><span data-stu-id="5cbd1-124">If you need to debug the Scala-side code (`DotnetRunner`, `DotnetBackendHandler`, etc.), you can use the following command and attach a debugger to the running process using [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html):</span></span>

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

<span data-ttu-id="5cbd1-125">執行命令之後，請使用 [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html) 將偵錯工具附加至執行中的處理序。</span><span class="sxs-lookup"><span data-stu-id="5cbd1-125">After you run the command, attach a debugger to the running process using [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span></span>

## <a name="next-steps"></a><span data-ttu-id="5cbd1-126">後續步驟</span><span class="sxs-lookup"><span data-stu-id="5cbd1-126">Next steps</span></span>

* [<span data-ttu-id="5cbd1-127">開始使用 .NET for Apache Spark</span><span class="sxs-lookup"><span data-stu-id="5cbd1-127">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="5cbd1-128">將 .NET for Apache Spark 應用程式部署到 Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="5cbd1-128">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="5cbd1-129">將 .NET for Apache Spark 應用程式部署到 Databricks</span><span class="sxs-lookup"><span data-stu-id="5cbd1-129">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="5cbd1-130">將 .NET for Apache Spark 應用程式部署到 Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="5cbd1-130">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>](../tutorials/amazon-emr-spark-deployment.md)
