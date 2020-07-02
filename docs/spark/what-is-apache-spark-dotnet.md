---
title: 什麼是 .NET for Apache Spark？
description: 了解 .NET for Apache Spark，其為開放原始碼且跨平台的免費巨量資料分析架構，可將 Spark 帶到撰寫 .NET 程式碼的任何地方。
author: mamccrea
ms.topic: overview
ms.date: 06/25/2020
ms.openlocfilehash: 2c04861dabe604b52df583cd5a7eecc5ff8e5481
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621856"
---
# <a name="what-is-net-for-apache-spark"></a>什麼是 .NET for Apache Spark？

[Apache Spark](what-is-spark.md)是一般用途的分散式處理引擎，用於分析大型資料集，通常是 tb 或數 pb 的資料。 使用適用于 Apache Spark 的 .NET、適用于熱門開放原始碼海量資料分析架構的免費、開放原始碼和跨平臺 .NET 支援，您現在可以使用您熟悉的語言，將 Apache Spark 功能新增到您的 big data 應用程式。

[!INCLUDE [spark-preview-note](../../includes/spark-preview-note.md)]

## <a name="why-choose-net-for-apache-spark"></a>為何選擇適用于 Apache Spark 的 .NET？

適用于 Apache Spark 的 .NET 可讓開發人員使用 .NET 體驗或程式碼基底，以參與 big data analytics 的世界。 適用于 Apache Spark 的 .NET 可提供高效能 Api，以便從 c # 和 F # 使用 Spark。 有 C# 和 F#，您就可以存取：

* 使用結構化資料的資料框架和 SparkSQL。
* Spark 結構化串流以便使用串流資料。
* 使用 SQL 語法撰寫查詢的 Spark SQL。
* 機器學習服務整合可加速定型和預測（也就是使用 .NET 做為 Apache Spark 與[ML.NET](https://dot.net/ml)）。

.NET for Apache Spark 符合 .NET Standard 的規範，這是所有 .NET 實作都具備的 .NET API 正式規格。 這表示您可以在撰寫 .NET 程式碼的任何地方使用 .NET for Apache Spark，這讓您可以重複運用身為 .NET 開發人員已具備的所有知識、技能、程式碼和程式庫。

.NET for Apache Spark 可在使用 .NET Core 的 Windows、Linux 和 macOS 上執行。 它也可在使用 .NET Framework 的 Windows 上執行。 您可以將應用程式部署到所有主要雲端提供者，包括 Azure HDInsight Spark、Amazon EMR Spark、Azure Databricks 和 AWS 上的 Databricks。

## <a name="net-for-apache-spark-architecture"></a>適用于 Apache Spark 架構的 .NET

Spark 的 c #/F # 語言系結是以新的 Spark interop 層撰寫，可提供更輕鬆的擴充性。 這個新一層的 Spark interop 是使用語言擴充功能的最佳做法所撰寫，並可針對 interop 和效能進行優化。 長期而言，此擴充性可用於在 Spark 中新增其他語言的支援。

> [!div class="mx-imgBorder"]
> ![適用于 Apache Spark 架構的 .NET](media/dotnet-spark-architecture.png)

您可以從[提案](https://issues.apache.org/jira/browse/SPARK-26257)瞭解 Spark 語言延伸模組的 interop 支援。

## <a name="net-for-apache-spark-performance"></a>適用于 Apache Spark 效能的 .NET

相較于使用[TPC-H 基準測試](http://www.tpc.org/tpch/)的 Python 和 Scala，適用于 Apache Spark 的 .net 在大多數情況下都能順利執行，而且在使用者定義的函數效能很重要時，速度會比 python 快2倍。 我們持續致力於改善和基準效能。

若要執行您自己的基準測試，請參閱適用于[Apache Spark GitHub 的 .net](https://github.com/dotnet/spark/tree/master/benchmark)上的效能評定。

## <a name="net-for-apache-spark-roadmap"></a>適用于 Apache Spark 藍圖的 .NET

瞭解[適用于 Apache Spark 藍圖](https://github.com/dotnet/spark/blob/master/ROADMAP.md)之官方 .net 的短期和長期計畫。

## <a name="net-foundation"></a>.NET Foundation

.NET for Apache Spark 專案是 [.NET Foundation](https://www.dotnetfoundation.org/) 的一部分。

## <a name="contributions"></a>參與

.NET for Apache Spark 小組鼓勵投稿，包括 GitHub 問題和提取要求。 首先，尋找[現有的問題](https://github.com/dotnet/spark/issues)。 如果找不到現有的問題，[請開啟新的問題](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+)。

## <a name="next-steps"></a>後續步驟

試用 .NET for Apache Spark。
> [!div class="nextstepaction"]
> [教學課程：開始使用適用于 Apache Spark 的 .NET](./tutorials/get-started.md)
