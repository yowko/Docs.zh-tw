---
title: 對 Windows 上的 .NET for Apache Spark 應用程式進行偵錯
description: 了解如何對 Windows 上的 .NET for Apache Spark 應用程式進行偵錯。
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 25f5291c47dc1cdf2668cb077fae7439e330cc1c
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "76919931"
---
# <a name="debug-a-net-for-apache-spark-application"></a>對 .NET for Apache Spark 應用程式進行偵錯

本 how to 提供在 Windows 上針對 Apache Spark 應用程式的 .NET 進行偵錯工具的步驟。

## <a name="debug-your-application"></a>偵錯應用程式

開啟新的 [命令提示字元] 視窗，然後執行下列命令：

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

在 [debug] 模式中，DotnetRunner 不會啟動 .NET 應用程式，而是會等待您啟動 .NET 應用程式。 讓此命令提示字元視窗保持開啟，並透過C#偵錯工具啟動您的 .net 應用程式，以檢查您的應用程式。 使用C#偵錯工具（ [ C# Visual Studio Code 中](https://code.visualstudio.com/Docs/editor/debugging)[的 Windows/macOS](https://visualstudio.microsoft.com/vs/)或偵錯工具擴充功能 Visual Studio 偵錯工具）啟動您的 .net 應用程式，以對應用程式進行 debug。

## <a name="debug-a-user-defined-function-udf"></a>對使用者定義函數（UDF）進行 Debug

> [!NOTE]
> 只有在具有 Visual Studio 偵錯工具的 Windows 上，才支援使用者定義函數。

在執行 `spark-submit`之前，請設定下列環境變數：

```bat
set DOTNET_WORKER_DEBUG=1
```

當您執行 Spark 應用程式時，將會顯示 [`Choose Just-In-Time Debugger`] 視窗。 選擇 Visual Studio 偵錯工具。

偵錯工具會在[TaskRunner.cs](https://github.com/dotnet/spark/blob/5e9c08b430b4bc56b5f42252c4b73437377afaed/src/csharp/Microsoft.Spark.Worker/TaskRunner.cs#L52)的下列位置中斷：

```csharp
if (EnvironmentUtils.GetEnvironmentVariableAsBool("DOTNET_WORKER_DEBUG"))
{
    Debugger.Launch(); // <-- The debugger will break here.
}
```

流覽至包含您打算進行 debug 的 UDF 的 *.cs*檔案，並[設定中斷點](https://docs.microsoft.com/visualstudio/debugger/using-breakpoints?view=vs-2019)。 中斷點會顯示 `The breakpoint will not currently be hit`，因為工作者尚未載入包含 UDF 的元件。

點擊 `F5` 以繼續您的應用程式，最後會叫用中斷點。

> [!NOTE] 
> [選擇即時偵錯工具] 視窗會針對每個工作顯示。 若要避免過多的快顯視窗，請將執行次數設定為較低的數位。 例如，您可以使用 spark 提交的 **--master local [1]** 選項，將工作數目設定為1，這會啟動單一偵錯工具實例。

## <a name="debug-scala-code"></a>對 Scala 程式碼進行偵錯

如果您需要 debug Scala 端程式碼（`DotnetRunner`、`DotnetBackendHandler`等），您可以使用下列命令，並使用[IntelliJ](https://www.jetbrains.com/help/idea/attaching-to-local-process.html)將偵錯工具附加至執行中的進程：

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
