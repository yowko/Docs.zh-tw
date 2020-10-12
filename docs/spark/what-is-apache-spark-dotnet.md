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
# <a name="what-is-net-for-apache-spark"></a><span data-ttu-id="8e4d8-103">什麼是 .NET for Apache Spark？</span><span class="sxs-lookup"><span data-stu-id="8e4d8-103">What is .NET for Apache Spark?</span></span>

<span data-ttu-id="8e4d8-104">[Apache Spark](what-is-spark.md) 是適用于大型資料集分析的一般用途分散式處理引擎，通常是 tb 或 pb 的資料。</span><span class="sxs-lookup"><span data-stu-id="8e4d8-104">[Apache Spark](what-is-spark.md) is a general-purpose distributed processing engine for analytics over large data sets - typically terabytes or petabytes of data.</span></span> <span data-ttu-id="8e4d8-105">有了 .NET for Apache Spark、開放原始碼和跨平臺的 .net 支援，適用于熱門的開放原始碼大型資料分析架構，您現在可以使用您熟悉的語言，將 Apache Spark 的強大功能新增至您的大型資料應用程式。</span><span class="sxs-lookup"><span data-stu-id="8e4d8-105">With .NET for Apache Spark, the free, open-source, and cross-platform .NET Support for the popular open-source big data analytics framework, you can now add the power of Apache Spark to your big data applications using languages you already know.</span></span>

## <a name="why-choose-net-for-apache-spark"></a><span data-ttu-id="8e4d8-106">為何選擇 .NET 進行 Apache Spark？</span><span class="sxs-lookup"><span data-stu-id="8e4d8-106">Why choose .NET for Apache Spark?</span></span>

<span data-ttu-id="8e4d8-107">適用于 Apache Spark 的 .NET 可讓開發人員使用 .NET 體驗或程式碼基底，以參與大型資料分析的世界。</span><span class="sxs-lookup"><span data-stu-id="8e4d8-107">.NET for Apache Spark empowers developers with .NET experience or code bases to participate in the world of big data analytics.</span></span> <span data-ttu-id="8e4d8-108">適用于 Apache Spark 的 .NET 提供使用 c # 和 F # Spark 的高效能 Api。</span><span class="sxs-lookup"><span data-stu-id="8e4d8-108">.NET for Apache Spark provides high performance APIs for using Spark from C# and F#.</span></span> <span data-ttu-id="8e4d8-109">有 C# 和 F#，您就可以存取：</span><span class="sxs-lookup"><span data-stu-id="8e4d8-109">With C# and F#, you can access:</span></span>

* <span data-ttu-id="8e4d8-110">使用結構化資料的資料框架和 SparkSQL。</span><span class="sxs-lookup"><span data-stu-id="8e4d8-110">DataFrame and SparkSQL for working with structured data.</span></span>
* <span data-ttu-id="8e4d8-111">Spark 結構化串流以便使用串流資料。</span><span class="sxs-lookup"><span data-stu-id="8e4d8-111">Spark Structured Streaming for working with streaming data.</span></span>
* <span data-ttu-id="8e4d8-112">使用 SQL 語法撰寫查詢的 Spark SQL。</span><span class="sxs-lookup"><span data-stu-id="8e4d8-112">Spark SQL for writing queries with SQL syntax.</span></span>
* <span data-ttu-id="8e4d8-113">機器學習整合可加快定型和預測 (也就是，使用 .NET 來 Apache Spark 與 [ML.NET](https://dot.net/ml)) 。</span><span class="sxs-lookup"><span data-stu-id="8e4d8-113">Machine learning integration for faster training and prediction (that is, use .NET for Apache Spark alongside [ML.NET](https://dot.net/ml)).</span></span>

<span data-ttu-id="8e4d8-114">.NET for Apache Spark 符合 .NET Standard 的規範，這是所有 .NET 實作都具備的 .NET API 正式規格。</span><span class="sxs-lookup"><span data-stu-id="8e4d8-114">.NET for Apache Spark is compliant with .NET Standard, a formal specification of .NET APIs that are common across .NET implementations.</span></span> <span data-ttu-id="8e4d8-115">這表示您可以在撰寫 .NET 程式碼的任何地方使用 .NET for Apache Spark，這讓您可以重複運用身為 .NET 開發人員已具備的所有知識、技能、程式碼和程式庫。</span><span class="sxs-lookup"><span data-stu-id="8e4d8-115">This means you can use .NET for Apache Spark anywhere you write .NET code allowing you to reuse all the knowledge, skills, code, and libraries you already have as a .NET developer.</span></span>

<span data-ttu-id="8e4d8-116">.NET for Apache Spark 可在使用 .NET Core 的 Windows、Linux 和 macOS 上執行。</span><span class="sxs-lookup"><span data-stu-id="8e4d8-116">.NET for Apache Spark runs on Windows, Linux, and macOS using .NET Core.</span></span> <span data-ttu-id="8e4d8-117">它也可在使用 .NET Framework 的 Windows 上執行。</span><span class="sxs-lookup"><span data-stu-id="8e4d8-117">It also runs on Windows using .NET Framework.</span></span> <span data-ttu-id="8e4d8-118">您可以將應用程式部署到所有主要雲端提供者，包括 Azure HDInsight Spark、Amazon EMR Spark、Azure Databricks 和 AWS 上的 Databricks。</span><span class="sxs-lookup"><span data-stu-id="8e4d8-118">You can deploy your applications to all major cloud providers including Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks, and Databricks on AWS.</span></span>

## <a name="net-for-apache-spark-architecture"></a><span data-ttu-id="8e4d8-119">適用于 Apache Spark 架構的 .NET</span><span class="sxs-lookup"><span data-stu-id="8e4d8-119">.NET for Apache Spark architecture</span></span>

<span data-ttu-id="8e4d8-120">Spark 的 c #/F # 語言系結會以新的 Spark interop 層撰寫，以提供更輕鬆的擴充性。</span><span class="sxs-lookup"><span data-stu-id="8e4d8-120">The C#/ F# language binding to Spark is written on a new Spark interop layer which offers easier extensibility.</span></span> <span data-ttu-id="8e4d8-121">這一層的 Spark interop 是使用語言延伸模組的最佳作法來撰寫，並針對 interop 與效能進行優化。</span><span class="sxs-lookup"><span data-stu-id="8e4d8-121">This new layer of Spark interop was written using the best practices for language extension and optimizes for interop and performance.</span></span> <span data-ttu-id="8e4d8-122">長期來說，此擴充性可用於在 Spark 中新增其他語言的支援。</span><span class="sxs-lookup"><span data-stu-id="8e4d8-122">Long term, this extensibility can be used for adding support for other languages in Spark.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="8e4d8-123">![適用于 Apache Spark 架構的 .NET](media/dotnet-spark-architecture.png)</span><span class="sxs-lookup"><span data-stu-id="8e4d8-123">![.NET for Apache Spark architecture](media/dotnet-spark-architecture.png)</span></span>

<span data-ttu-id="8e4d8-124">您可以從 [提案](https://issues.apache.org/jira/browse/SPARK-26257)瞭解 Spark 語言延伸模組的 interop 支援。</span><span class="sxs-lookup"><span data-stu-id="8e4d8-124">You can learn about interop support for Spark language extensions from [the proposal](https://issues.apache.org/jira/browse/SPARK-26257).</span></span>

## <a name="net-for-apache-spark-performance"></a><span data-ttu-id="8e4d8-125">適用于 Apache Spark 效能的 .NET</span><span class="sxs-lookup"><span data-stu-id="8e4d8-125">.NET for Apache Spark performance</span></span>

<span data-ttu-id="8e4d8-126">與 Python 和 Scala 相較之下，使用 [TPC-H](http://www.tpc.org/tpch/)效能評定時，適用于 Apache Spark 的 .net 在大部分情況下都能順利執行，而且在使用者定義的函數效能很重要時，速度會比 python 快2倍。</span><span class="sxs-lookup"><span data-stu-id="8e4d8-126">When compared against Python and Scala using the [TPC-H benchmark](http://www.tpc.org/tpch/), .NET for Apache Spark performs well in most cases and is 2x faster than Python when user-defined function performance is critical.</span></span> <span data-ttu-id="8e4d8-127">我們會持續努力改善和基準效能。</span><span class="sxs-lookup"><span data-stu-id="8e4d8-127">There is an ongoing effort to improve and benchmark performance.</span></span>

<span data-ttu-id="8e4d8-128">若要進行您自己的基準測試，請參閱適用于 [.net 的 Apache Spark GitHub](https://github.com/dotnet/spark/tree/master/benchmark)的基準測試。</span><span class="sxs-lookup"><span data-stu-id="8e4d8-128">To do your own benchmarking, see the benchmarks available on the [.NET for Apache Spark GitHub](https://github.com/dotnet/spark/tree/master/benchmark).</span></span>

## <a name="net-for-apache-spark-roadmap"></a><span data-ttu-id="8e4d8-129">適用于 Apache Spark 藍圖的 .NET</span><span class="sxs-lookup"><span data-stu-id="8e4d8-129">.NET for Apache Spark roadmap</span></span>

<span data-ttu-id="8e4d8-130">瞭解 [適用于 Apache Spark 藍圖](https://github.com/dotnet/spark/blob/master/ROADMAP.md)的官方 .net 的短期和長期計畫。</span><span class="sxs-lookup"><span data-stu-id="8e4d8-130">Learn about short term and long term plans from the official [.NET for Apache Spark roadmap](https://github.com/dotnet/spark/blob/master/ROADMAP.md).</span></span>

## <a name="net-foundation"></a><span data-ttu-id="8e4d8-131">.NET Foundation</span><span class="sxs-lookup"><span data-stu-id="8e4d8-131">.NET Foundation</span></span>

<span data-ttu-id="8e4d8-132">.NET for Apache Spark 專案是 [.NET Foundation](https://www.dotnetfoundation.org/) 的一部分。</span><span class="sxs-lookup"><span data-stu-id="8e4d8-132">The .NET for Apache Spark project is part of the [.NET Foundation](https://www.dotnetfoundation.org/).</span></span>

## <a name="contributions"></a><span data-ttu-id="8e4d8-133">參與</span><span class="sxs-lookup"><span data-stu-id="8e4d8-133">Contributions</span></span>

<span data-ttu-id="8e4d8-134">.NET for Apache Spark 小組鼓勵投稿，包括 GitHub 問題和提取要求。</span><span class="sxs-lookup"><span data-stu-id="8e4d8-134">The .NET for Apache Spark team encourages contributions, both GitHub issues and pull requests.</span></span> <span data-ttu-id="8e4d8-135">首先，尋找[現有的問題](https://github.com/dotnet/spark/issues)。</span><span class="sxs-lookup"><span data-stu-id="8e4d8-135">First, look for an [existing issue](https://github.com/dotnet/spark/issues).</span></span> <span data-ttu-id="8e4d8-136">如果找不到現有的問題，[請開啟新的問題](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+)。</span><span class="sxs-lookup"><span data-stu-id="8e4d8-136">If you can't find an existing issue, [open a new issue](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).</span></span>

## <a name="next-steps"></a><span data-ttu-id="8e4d8-137">後續步驟</span><span class="sxs-lookup"><span data-stu-id="8e4d8-137">Next steps</span></span>

<span data-ttu-id="8e4d8-138">試用 .NET 進行 Apache Spark。</span><span class="sxs-lookup"><span data-stu-id="8e4d8-138">Try .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="8e4d8-139">教學課程：開始使用 .NET 進行 Apache Spark</span><span class="sxs-lookup"><span data-stu-id="8e4d8-139">Tutorial: Get started with .NET for Apache Spark</span></span>](./tutorials/get-started.md)
