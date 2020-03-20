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
# <a name="debug-a-net-for-apache-spark-application"></a>對 .NET for Apache Spark 應用程式進行偵錯

此手如何提供在 Windows 上調試的 apache Spark 應用程式 .NET 的步驟。

## <a name="debug-your-application"></a>為您的應用程式偵錯

打開新的命令提示視窗並運行以下命令：

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

當您執行命令時，您會看到下列輸出：

```console
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

在偵錯模式下，DotnetRunner 不會啟動 .NET 應用程式，而是等待您啟動 .NET 應用。 保持此命令提示視窗打開，並通過 C# 調試器啟動 .NET 應用程式以調試應用程式。 使用 C# 調試器啟動 .NET 應用程式[（Windows/macOS 的視覺化工作室調試器](https://visualstudio.microsoft.com/vs/)或[視覺化工作室代碼中的 C# 調試器擴展](https://code.visualstudio.com/Docs/editor/debugging)器），以調試應用程式。

## <a name="debug-a-user-defined-function-udf"></a>調試使用者定義的函數 （UDF）

> [!NOTE]
> 使用者定義的功能僅在具有視覺化工作室調試器的 Windows 上受支援。

在運行`spark-submit`之前，設置以下環境變數：

```bat
set DOTNET_WORKER_DEBUG=1
```

運行 Spark 應用程式時，將`Choose Just-In-Time Debugger`彈出一個視窗。 選擇視覺化工作室調試器。

調試器將在[TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52)中的以下位置中斷：

```csharp
if (EnvironmentUtils.GetEnvironmentVariableAsBool("DOTNET_WORKER_DEBUG"))
{
    Debugger.Launch(); // <-- The debugger will break here.
}
```

導航到包含計畫調試的 UDF 的 *.cs*檔，並[設置中斷點](https://docs.microsoft.com/visualstudio/debugger/using-breakpoints?view=vs-2019)。 中斷點將說`The breakpoint will not currently be hit`，因為工作人員尚未載入包含 UDF 的程式集。

命中`F5`以繼續您的應用程式，中斷點最終將被擊中。

> [!NOTE]
> 為每個任務彈出"選擇即時調試器"視窗。 為避免快顯視窗過多，請將執行器數設置為低數。 例如，可以使用 **--master local{1}** 選項進行火花提交，將任務數設置為 1，從而啟動單個調試器實例。

## <a name="debug-scala-code"></a>對 Scala 程式碼進行偵錯

如果需要調試 Scala 端代碼 （`DotnetRunner`等`DotnetBackendHandler`），可以使用以下命令並使用[IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html)將調試器附加到正在運行的進程：

```shell
spark-submit \
  --driver-java-options -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=5005 \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  <path-to-your-app-exe> <argument(s)-to-your-app>
```

執行命令之後，請使用 [Intellij](https://www.jetbrains.com/help/idea/attaching-to-local-process.html) 將偵錯工具附加至執行中的處理序。

## <a name="next-steps"></a>後續步驟

* [開始使用 .NET for Apache Spark](../tutorials/get-started.md)
* [將 .NET for Apache Spark 應用程式部署到 Azure HDInsight](../tutorials/hdinsight-deployment.md)
* [將 .NET for Apache Spark 應用程式部署到 Databricks](../tutorials/databricks-deployment.md)
* [將 .NET for Apache Spark 應用程式部署到 Amazon EMR Spark](../tutorials/amazon-emr-spark-deployment.md)
