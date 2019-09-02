---
title: 對 Windows 上的 .NET for Apache Spark 應用程式進行偵錯
description: 了解如何對 Windows 上的 .NET for Apache Spark 應用程式進行偵錯。
ms.date: 08/15/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: dcaca96f6eb871c15a37adc18190b073c63c8e93
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70206151"
---
# <a name="debug-a-net-for-apache-spark-application"></a>對 .NET for Apache Spark 應用程式進行偵錯

此操作說明提供對 Windows 上的 .NET for Apache Spark 應用程式和 Scala 程式碼進行偵錯時，所需執行的命令。

## <a name="debug-your-application"></a>為您的應用程式偵錯

開啟新的命令提示字元視窗，執行下列命令：

```shell
spark-submit \
  --class org.apache.spark.deploy.dotnet.DotnetRunner \
  --master local \
  <path-to-microsoft-spark-jar> \
  debug
```

當您執行命令時，您會看到下列輸出：

```
***********************************************************************
* .NET Backend running debug mode. Press enter to exit *
***********************************************************************
```

在此偵錯模式中，`DotnetRunner` 不會啟動 .NET 應用程式，而是會等待它連線。 不要關閉此命令提示字元視窗。

現在，您可以執行 .NET 應用程式，並搭配任何偵錯工具來對應用程式進行偵錯。

## <a name="debug-scala-code"></a>對 Scala 程式碼進行偵錯

如果您需要對 Scala 端程式碼進行偵錯，例如 `DotnetRunner` 或 `DotnetBackendHandler`，請執行下列命令：

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
