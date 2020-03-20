---
title: 什麼是 .NET for Apache Spark？
description: 了解 .NET for Apache Spark，其為開放原始碼且跨平台的免費巨量資料分析架構，可將 Spark 帶到撰寫 .NET 程式碼的任何地方。
author: mamccrea
ms.topic: overview
ms.date: 10/15/2019
ms.openlocfilehash: 12fccd478cedaccf455043feb3afa7b12221bf0e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "73458196"
---
# <a name="what-is-net-for-apache-spark"></a>什麼是 .NET for Apache Spark？

[Apache Spark](what-is-spark.md)是一個通用分散式處理引擎，用於分析大型資料集（通常為 TB 或 PB 的資料）。 借助 .NET 用於 Apache Spark，免費、開源和跨平臺 .NET 支援，適用于流行的開源大資料分析框架，現在您可以使用您已經知道的語言將 Apache Spark 的強大功能添加到大資料應用程式中。

## <a name="why-choose-net-for-apache-spark"></a>為什麼選擇 .NET 作為阿帕奇火花？

阿帕奇 Spark 的 .NET 使開發人員能夠擁有 .NET 體驗或代碼庫，從而參與大資料分析領域。 阿帕奇 Spark 的 .NET 提供高性能 API，用於使用來自 C# 和 F# 的 Spark。 有 C# 和 F#，您就可以存取：

* 用於處理結構化資料的資料框架和 SparkSQL。
* Spark 結構化串流以便使用串流資料。
* 用於使用 SQL 語法編寫查詢的 Spark SQL。
* 機器學習集成，用於更快的培訓和預測（即，將 .NET 用於 Apache Spark[以及ML.NET](https://dot.net/ml)）。

.NET for Apache Spark 符合 .NET Standard 的規範，這是所有 .NET 實作都具備的 .NET API 正式規格。 這表示您可以在撰寫 .NET 程式碼的任何地方使用 .NET for Apache Spark，這讓您可以重複運用身為 .NET 開發人員已具備的所有知識、技能、程式碼和程式庫。

.NET for Apache Spark 可在使用 .NET Core 的 Windows、Linux 和 macOS 上執行。 它也可在使用 .NET Framework 的 Windows 上執行。 您可以將應用程式部署到所有主要雲端提供者，包括 Azure HDInsight Spark、Amazon EMR Spark、Azure Databricks 和 AWS 上的 Databricks。

## <a name="net-for-apache-spark-architecture"></a>阿帕奇火花架構的 .NET

綁定到 Spark 的 C#/ F++ 語言寫入新的 Spark 互通層，該層提供更輕鬆的可擴充性。 這一新的 Spark 交互操作層是使用語言擴展的最佳實踐編寫的，並優化了交互操作和性能。 長期來看，這種可擴充性可用於添加 Spark 中其他語言的支援。

> [!div class="mx-imgBorder"]
> ![阿帕奇火花架構的 .NET](media/dotnet-spark-architecture.png)

你可以從[建議](https://issues.apache.org/jira/browse/SPARK-26257)中瞭解對 Spark 語言擴展的交互操作支援。

## <a name="net-for-apache-spark-performance"></a>阿帕奇火花性能 .NET

與使用[TPC-H 基準](http://www.tpc.org/tpch/)的 Python 和 Scala 相比，阿帕奇 Spark 的 .NET 在大多數情況下表現良好，在使用者定義的功能性能至關重要時，其速度比 Python 快 2 倍。 不斷努力改進績效並衡量績效。

要執行自己的基準測試，請參閱[Apache Spark GitHub](https://github.com/dotnet/spark/tree/master/benchmark)的 .NET 上提供的基準測試。

## <a name="net-for-apache-spark-roadmap"></a>阿帕奇火花路線圖的 .NET

從官方[.NET 瞭解阿帕奇 Spark 路線圖](https://github.com/dotnet/spark/blob/master/ROADMAP.md)的短期和長期計畫。

## <a name="net-foundation"></a>.NET Foundation

.NET for Apache Spark 專案是 [.NET Foundation](https://www.dotnetfoundation.org/) 的一部分。

## <a name="contributions"></a>投稿文章

.NET for Apache Spark 小組鼓勵投稿，包括 GitHub 問題和提取要求。 首先，尋找[現有的問題](https://github.com/dotnet/spark/issues)。 如果找不到現有的問題，[請開啟新的問題](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+)。

## <a name="next-steps"></a>後續步驟

嘗試 .NET 的阿帕奇火花。
> [!div class="nextstepaction"]
> [教程： 開始與 .NET 的阿帕奇火花](./tutorials/get-started.md)
