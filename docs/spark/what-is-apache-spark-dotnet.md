---
title: 什麼是 .NET for Apache Spark？
description: 了解 .NET for Apache Spark，其為開放原始碼且跨平台的免費巨量資料分析架構，可將 Spark 帶到撰寫 .NET 程式碼的任何地方。
author: mamccrea
ms.topic: overview
ms.date: 10/09/2020
ms.openlocfilehash: 2c743cf7f88d857fb87aed123bd687c353fd8b84
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955352"
---
# <a name="what-is-net-for-apache-spark"></a>什麼是 .NET for Apache Spark？

[Apache Spark](what-is-spark.md) 是適用于大型資料集分析的一般用途分散式處理引擎，通常是 tb 或 pb 的資料。 有了 .NET for Apache Spark、開放原始碼和跨平臺的 .net 支援，適用于熱門的開放原始碼大型資料分析架構，您現在可以使用您熟悉的語言，將 Apache Spark 的強大功能新增至您的大型資料應用程式。

## <a name="why-choose-net-for-apache-spark"></a>為何選擇 .NET 進行 Apache Spark？

適用于 Apache Spark 的 .NET 可讓開發人員使用 .NET 體驗或程式碼基底，以參與大型資料分析的世界。 適用于 Apache Spark 的 .NET 提供使用 c # 和 F # Spark 的高效能 Api。 有 C# 和 F#，您就可以存取：

* 使用結構化資料的資料框架和 SparkSQL。
* Spark 結構化串流以便使用串流資料。
* 使用 SQL 語法撰寫查詢的 Spark SQL。
* 機器學習整合可加快定型和預測 (也就是，使用 .NET 來 Apache Spark 與 [ML.NET](https://dot.net/ml)) 。

.NET for Apache Spark 符合 .NET Standard 的規範，這是所有 .NET 實作都具備的 .NET API 正式規格。 這表示您可以在撰寫 .NET 程式碼的任何地方使用 .NET for Apache Spark，這讓您可以重複運用身為 .NET 開發人員已具備的所有知識、技能、程式碼和程式庫。

.NET for Apache Spark 可在使用 .NET Core 的 Windows、Linux 和 macOS 上執行。 它也可在使用 .NET Framework 的 Windows 上執行。 您可以將應用程式部署到所有主要雲端提供者，包括 Azure HDInsight Spark、Amazon EMR Spark、Azure Databricks 和 AWS 上的 Databricks。

## <a name="net-for-apache-spark-architecture"></a>適用于 Apache Spark 架構的 .NET

Spark 的 c #/F # 語言系結會以新的 Spark interop 層撰寫，以提供更輕鬆的擴充性。 這一層的 Spark interop 是使用語言延伸模組的最佳作法來撰寫，並針對 interop 與效能進行優化。 長期來說，此擴充性可用於在 Spark 中新增其他語言的支援。

> [!div class="mx-imgBorder"]
> ![適用于 Apache Spark 架構的 .NET](media/dotnet-spark-architecture.png)

您可以從 [提案](https://issues.apache.org/jira/browse/SPARK-26257)瞭解 Spark 語言延伸模組的 interop 支援。

## <a name="net-for-apache-spark-performance"></a>適用于 Apache Spark 效能的 .NET

與 Python 和 Scala 相較之下，使用 [TPC-H](http://www.tpc.org/tpch/)效能評定時，適用于 Apache Spark 的 .net 在大部分情況下都能順利執行，而且在使用者定義的函數效能很重要時，速度會比 python 快2倍。 我們會持續努力改善和基準效能。

若要進行您自己的基準測試，請參閱適用于 [.net 的 Apache Spark GitHub](https://github.com/dotnet/spark/tree/master/benchmark)的基準測試。

## <a name="net-for-apache-spark-roadmap"></a>適用于 Apache Spark 藍圖的 .NET

瞭解 [適用于 Apache Spark 藍圖](https://github.com/dotnet/spark/blob/master/ROADMAP.md)的官方 .net 的短期和長期計畫。

## <a name="net-foundation"></a>.NET Foundation

.NET for Apache Spark 專案是 [.NET Foundation](https://www.dotnetfoundation.org/) 的一部分。

## <a name="contributions"></a>參與

.NET for Apache Spark 小組鼓勵投稿，包括 GitHub 問題和提取要求。 首先，尋找[現有的問題](https://github.com/dotnet/spark/issues)。 如果找不到現有的問題，[請開啟新的問題](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+)。

## <a name="next-steps"></a>後續步驟

試用 .NET 進行 Apache Spark。
> [!div class="nextstepaction"]
> [教學課程：開始使用 .NET 進行 Apache Spark](./tutorials/get-started.md)
