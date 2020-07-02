---
title: 對 Windows 上的 .NET for Apache Spark 應用程式進行偵錯
description: 了解如何對 Windows 上的 .NET for Apache Spark 應用程式進行偵錯。
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 9209d5bdec6dd85f6d21a502fb07204effef1934
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617752"
---
# <a name="debug-a-net-for-apache-spark-application"></a><span data-ttu-id="a949d-103">對 .NET for Apache Spark 應用程式進行偵錯</span><span class="sxs-lookup"><span data-stu-id="a949d-103">Debug a .NET for Apache Spark application</span></span>

<span data-ttu-id="a949d-104">本 how to 提供在 Windows 上針對 Apache Spark 應用程式的 .NET 進行偵錯工具的步驟。</span><span class="sxs-lookup"><span data-stu-id="a949d-104">This how-to provides the steps to debug your .NET for Apache Spark application on Windows.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="debug-your-application"></a><span data-ttu-id="a949d-105">偵錯應用程式</span><span class="sxs-lookup"><span data-stu-id="a949d-105">Debug your application</span></span>

<span data-ttu-id="a949d-106">開啟新的 [命令提示字元] 視窗，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="a949d-106">Open a new command prompt window and run the following command:</span></span>

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

<span data-ttu-id="a949d-107">當您執行命令時，您會看到下列輸出：</span><span class="sxs-lookup"><span data-stu-id="a949d-107">When you run the command, you see the following output:</span></span>

```console
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

<span data-ttu-id="a949d-108">在 [debug] 模式中，DotnetRunner 不會啟動 .NET 應用程式，而是會等待您啟動 .NET 應用程式。</span><span class="sxs-lookup"><span data-stu-id="a949d-108">In debug mode, DotnetRunner does not launch the .NET application, but instead waits for you to start the .NET app.</span></span> <span data-ttu-id="a949d-109">讓此命令提示字元視窗保持開啟，並透過 c # 偵錯工具啟動您的 .NET 應用程式，以對應用程式進行 debug</span><span class="sxs-lookup"><span data-stu-id="a949d-109">Leave this command prompt window open and start your .NET application through C# debugger to debug your application.</span></span> <span data-ttu-id="a949d-110">使用 c # 偵錯工具啟動您的 .NET 應用程式（Visual Studio Code 中[適用于 Windows/macOS 的 Visual Studio 調試](https://visualstudio.microsoft.com/vs/)程式或[c # 偵錯工具擴充](https://code.visualstudio.com/Docs/editor/debugging)功能），以對應用程式進行 debug</span><span class="sxs-lookup"><span data-stu-id="a949d-110">Start your .NET application with a C# debugger ([Visual Studio Debugger for Windows/macOS](https://visualstudio.microsoft.com/vs/) or [C# Debugger Extension in Visual Studio Code](https://code.visualstudio.com/Docs/editor/debugging)) to debug your application.</span></span>

## <a name="debug-a-user-defined-function-udf"></a><span data-ttu-id="a949d-111">對使用者定義函數（UDF）進行 Debug</span><span class="sxs-lookup"><span data-stu-id="a949d-111">Debug a user-defined function (UDF)</span></span>

> [!NOTE]
> <span data-ttu-id="a949d-112">只有在具有 Visual Studio 偵錯工具的 Windows 上，才支援使用者定義函數。</span><span class="sxs-lookup"><span data-stu-id="a949d-112">User-defined functions are supported only on Windows with Visual Studio Debugger.</span></span>

<span data-ttu-id="a949d-113">在 `spark-submit` 執行之前，請設定下列環境變數：</span><span class="sxs-lookup"><span data-stu-id="a949d-113">Before running `spark-submit`, set the following environment variable:</span></span>

```bat
set DOTNET_WORKER_DEBUG=1
```

<span data-ttu-id="a949d-114">當您執行 Spark 應用程式時， `Choose Just-In-Time Debugger` 將會顯示一個視窗。</span><span class="sxs-lookup"><span data-stu-id="a949d-114">When you run your Spark application, a `Choose Just-In-Time Debugger` window will pop up.</span></span> <span data-ttu-id="a949d-115">選擇 Visual Studio 偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="a949d-115">Choose a Visual Studio debugger.</span></span>

<span data-ttu-id="a949d-116">偵錯工具會在[TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52)的下列位置中斷：</span><span class="sxs-lookup"><span data-stu-id="a949d-116">The debugger will break at the following location in [TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52):</span></span>

```csharp
if (EnvironmentUtils.GetEnvironmentVariableAsBool("DOTNET_WORKER_DEBUG"))
{
    Debugger.Launch(); // <-- The debugger will break here.
}
```

<span data-ttu-id="a949d-117">流覽至包含您打算進行 debug 的 UDF 的 *.cs*檔案，並[設定中斷點](https://docs.microsoft.com/visualstudio/debugger/using-breakpoints?view=vs-2019)。</span><span class="sxs-lookup"><span data-stu-id="a949d-117">Navigate to the *.cs* file that contains the UDF that you plan to debug, and [set a breakpoint](https://docs.microsoft.com/visualstudio/debugger/using-breakpoints?view=vs-2019).</span></span> <span data-ttu-id="a949d-118">中斷點會指出， `The breakpoint will not currently be hit` 因為背景工作尚未載入包含 UDF 的元件。</span><span class="sxs-lookup"><span data-stu-id="a949d-118">The breakpoint will say `The breakpoint will not currently be hit` because the worker hasn't loaded the assembly that contains UDF yet.</span></span>

<span data-ttu-id="a949d-119">點擊 `F5` 以繼續您的應用程式，最後會叫用中斷點。</span><span class="sxs-lookup"><span data-stu-id="a949d-119">Hit `F5` to continue your application and the breakpoint will eventually be hit.</span></span>

> [!NOTE]
> <span data-ttu-id="a949d-120">[選擇即時偵錯工具] 視窗會針對每個工作顯示。</span><span class="sxs-lookup"><span data-stu-id="a949d-120">The Choose Just-In-Time Debugger window pops up for each task.</span></span> <span data-ttu-id="a949d-121">若要避免過多的快顯視窗，請將執行次數設定為較低的數位。</span><span class="sxs-lookup"><span data-stu-id="a949d-121">To avoid excessive pop-ups, set the number of executors to a low number.</span></span> <span data-ttu-id="a949d-122">例如，您可以使用 spark 提交的 **--master local [1]** 選項，將工作數目設定為1，這會啟動單一偵錯工具實例。</span><span class="sxs-lookup"><span data-stu-id="a949d-122">For example, you can use the **--master local[1]** option for spark-submit to set the number of tasks to 1, which launches a single debugger instance.</span></span>

## <a name="debug-scala-code"></a><span data-ttu-id="a949d-123">對 Scala 程式碼進行偵錯</span><span class="sxs-lookup"><span data-stu-id="a949d-123">Debug Scala code</span></span>

<span data-ttu-id="a949d-124">如果您需要 debug Scala 端程式碼（ `DotnetRunner` 、 `DotnetBackendHandler` 等），您可以使用下列命令，並使用[IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html)將偵錯工具附加至執行中的進程：</span><span class="sxs-lookup"><span data-stu-id="a949d-124">If you need to debug the Scala-side code (`DotnetRunner`, `DotnetBackendHandler`, etc.), you can use the following command and attach a debugger to the running process using [IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html):</span></span>

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

<span data-ttu-id="a949d-125">執行命令之後，請使用 [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html) 將偵錯工具附加至執行中的處理序。</span><span class="sxs-lookup"><span data-stu-id="a949d-125">After you run the command, attach a debugger to the running process using [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html).</span></span>

## <a name="next-steps"></a><span data-ttu-id="a949d-126">後續步驟</span><span class="sxs-lookup"><span data-stu-id="a949d-126">Next steps</span></span>

* [<span data-ttu-id="a949d-127">開始使用 .NET for Apache Spark</span><span class="sxs-lookup"><span data-stu-id="a949d-127">Get started with .NET for Apache Spark</span></span>](../tutorials/get-started.md)
* [<span data-ttu-id="a949d-128">將 .NET for Apache Spark 應用程式部署到 Azure HDInsight</span><span class="sxs-lookup"><span data-stu-id="a949d-128">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="a949d-129">將 .NET for Apache Spark 應用程式部署到 Databricks</span><span class="sxs-lookup"><span data-stu-id="a949d-129">Deploy a .NET for Apache Spark application to Databricks</span></span>](../tutorials/databricks-deployment.md)
* [<span data-ttu-id="a949d-130">將 .NET for Apache Spark 應用程式部署到 Amazon EMR Spark</span><span class="sxs-lookup"><span data-stu-id="a949d-130">Deploy a .NET for Apache Spark application to Amazon EMR Spark</span></span>](../tutorials/amazon-emr-spark-deployment.md)
