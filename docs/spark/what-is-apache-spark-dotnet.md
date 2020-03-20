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
# <a name="what-is-net-for-apache-spark"></a><span data-ttu-id="46c74-103">什麼是 .NET for Apache Spark？</span><span class="sxs-lookup"><span data-stu-id="46c74-103">What is .NET for Apache Spark?</span></span>

<span data-ttu-id="46c74-104">[Apache Spark](what-is-spark.md)是一個通用分散式處理引擎，用於分析大型資料集（通常為 TB 或 PB 的資料）。</span><span class="sxs-lookup"><span data-stu-id="46c74-104">[Apache Spark](what-is-spark.md) is a general-purpose distributed processing engine for analytics over large data sets - typically terabytes or petabytes of data.</span></span> <span data-ttu-id="46c74-105">借助 .NET 用於 Apache Spark，免費、開源和跨平臺 .NET 支援，適用于流行的開源大資料分析框架，現在您可以使用您已經知道的語言將 Apache Spark 的強大功能添加到大資料應用程式中。</span><span class="sxs-lookup"><span data-stu-id="46c74-105">With .NET for Apache Spark, the free, open-source, and cross-platform .NET Support for the popular open-source big data analytics framework, you can now add the power of Apache Spark to your big data applications using languages you already know.</span></span>

## <a name="why-choose-net-for-apache-spark"></a><span data-ttu-id="46c74-106">為什麼選擇 .NET 作為阿帕奇火花？</span><span class="sxs-lookup"><span data-stu-id="46c74-106">Why choose .NET for Apache Spark?</span></span>

<span data-ttu-id="46c74-107">阿帕奇 Spark 的 .NET 使開發人員能夠擁有 .NET 體驗或代碼庫，從而參與大資料分析領域。</span><span class="sxs-lookup"><span data-stu-id="46c74-107">.NET for Apache Spark empowers developers with .NET experience or code bases to participate in the world of big data analytics.</span></span> <span data-ttu-id="46c74-108">阿帕奇 Spark 的 .NET 提供高性能 API，用於使用來自 C# 和 F# 的 Spark。</span><span class="sxs-lookup"><span data-stu-id="46c74-108">.NET for Apache Spark provides high performance APIs for using Spark from C# and F#.</span></span> <span data-ttu-id="46c74-109">有 C# 和 F#，您就可以存取：</span><span class="sxs-lookup"><span data-stu-id="46c74-109">With C# and F#, you can access:</span></span>

* <span data-ttu-id="46c74-110">用於處理結構化資料的資料框架和 SparkSQL。</span><span class="sxs-lookup"><span data-stu-id="46c74-110">DataFrame and SparkSQL for working with structured data.</span></span>
* <span data-ttu-id="46c74-111">Spark 結構化串流以便使用串流資料。</span><span class="sxs-lookup"><span data-stu-id="46c74-111">Spark Structured Streaming for working with streaming data.</span></span>
* <span data-ttu-id="46c74-112">用於使用 SQL 語法編寫查詢的 Spark SQL。</span><span class="sxs-lookup"><span data-stu-id="46c74-112">Spark SQL for writing queries with SQL syntax.</span></span>
* <span data-ttu-id="46c74-113">機器學習集成，用於更快的培訓和預測（即，將 .NET 用於 Apache Spark[以及ML.NET](https://dot.net/ml)）。</span><span class="sxs-lookup"><span data-stu-id="46c74-113">Machine learning integration for faster training and prediction (that is, use .NET for Apache Spark alongside [ML.NET](https://dot.net/ml)).</span></span>

<span data-ttu-id="46c74-114">.NET for Apache Spark 符合 .NET Standard 的規範，這是所有 .NET 實作都具備的 .NET API 正式規格。</span><span class="sxs-lookup"><span data-stu-id="46c74-114">.NET for Apache Spark is compliant with .NET Standard, a formal specification of .NET APIs that are common across .NET implementations.</span></span> <span data-ttu-id="46c74-115">這表示您可以在撰寫 .NET 程式碼的任何地方使用 .NET for Apache Spark，這讓您可以重複運用身為 .NET 開發人員已具備的所有知識、技能、程式碼和程式庫。</span><span class="sxs-lookup"><span data-stu-id="46c74-115">This means you can use .NET for Apache Spark anywhere you write .NET code allowing you to reuse all the knowledge, skills, code, and libraries you already have as a .NET developer.</span></span>

<span data-ttu-id="46c74-116">.NET for Apache Spark 可在使用 .NET Core 的 Windows、Linux 和 macOS 上執行。</span><span class="sxs-lookup"><span data-stu-id="46c74-116">.NET for Apache Spark runs on Windows, Linux, and macOS using .NET Core.</span></span> <span data-ttu-id="46c74-117">它也可在使用 .NET Framework 的 Windows 上執行。</span><span class="sxs-lookup"><span data-stu-id="46c74-117">It also runs on Windows using .NET Framework.</span></span> <span data-ttu-id="46c74-118">您可以將應用程式部署到所有主要雲端提供者，包括 Azure HDInsight Spark、Amazon EMR Spark、Azure Databricks 和 AWS 上的 Databricks。</span><span class="sxs-lookup"><span data-stu-id="46c74-118">You can deploy your applications to all major cloud providers including Azure HDInsight Spark, Amazon EMR Spark, Azure Databricks, and Databricks on AWS.</span></span>

## <a name="net-for-apache-spark-architecture"></a><span data-ttu-id="46c74-119">阿帕奇火花架構的 .NET</span><span class="sxs-lookup"><span data-stu-id="46c74-119">.NET for Apache Spark architecture</span></span>

<span data-ttu-id="46c74-120">綁定到 Spark 的 C#/ F++ 語言寫入新的 Spark 互通層，該層提供更輕鬆的可擴充性。</span><span class="sxs-lookup"><span data-stu-id="46c74-120">The C#/ F# language binding to Spark is written on a new Spark interop layer which offers easier extensibility.</span></span> <span data-ttu-id="46c74-121">這一新的 Spark 交互操作層是使用語言擴展的最佳實踐編寫的，並優化了交互操作和性能。</span><span class="sxs-lookup"><span data-stu-id="46c74-121">This new layer of Spark interop was written using the best practices for language extension and optimizes for interop and performance.</span></span> <span data-ttu-id="46c74-122">長期來看，這種可擴充性可用於添加 Spark 中其他語言的支援。</span><span class="sxs-lookup"><span data-stu-id="46c74-122">Long term, this extensibility can be used for adding support for other languages in Spark.</span></span>

> [!div class="mx-imgBorder"]
> <span data-ttu-id="46c74-123">![阿帕奇火花架構的 .NET](media/dotnet-spark-architecture.png)</span><span class="sxs-lookup"><span data-stu-id="46c74-123">![.NET for Apache Spark architecture](media/dotnet-spark-architecture.png)</span></span>

<span data-ttu-id="46c74-124">你可以從[建議](https://issues.apache.org/jira/browse/SPARK-26257)中瞭解對 Spark 語言擴展的交互操作支援。</span><span class="sxs-lookup"><span data-stu-id="46c74-124">You can learn about interop support for Spark language extensions from [the proposal](https://issues.apache.org/jira/browse/SPARK-26257).</span></span>

## <a name="net-for-apache-spark-performance"></a><span data-ttu-id="46c74-125">阿帕奇火花性能 .NET</span><span class="sxs-lookup"><span data-stu-id="46c74-125">.NET for Apache Spark performance</span></span>

<span data-ttu-id="46c74-126">與使用[TPC-H 基準](http://www.tpc.org/tpch/)的 Python 和 Scala 相比，阿帕奇 Spark 的 .NET 在大多數情況下表現良好，在使用者定義的功能性能至關重要時，其速度比 Python 快 2 倍。</span><span class="sxs-lookup"><span data-stu-id="46c74-126">When compared against Python and Scala using the [TPC-H benchmark](http://www.tpc.org/tpch/), .NET for Apache Spark performs well in most cases and is 2x faster than Python when user-defined function performance is critical.</span></span> <span data-ttu-id="46c74-127">不斷努力改進績效並衡量績效。</span><span class="sxs-lookup"><span data-stu-id="46c74-127">There is an ongoing effort to improve and benchmark performance.</span></span>

<span data-ttu-id="46c74-128">要執行自己的基準測試，請參閱[Apache Spark GitHub](https://github.com/dotnet/spark/tree/master/benchmark)的 .NET 上提供的基準測試。</span><span class="sxs-lookup"><span data-stu-id="46c74-128">To do your own benchmarking, see the benchmarks available on the [.NET for Apache Spark GitHub](https://github.com/dotnet/spark/tree/master/benchmark).</span></span>

## <a name="net-for-apache-spark-roadmap"></a><span data-ttu-id="46c74-129">阿帕奇火花路線圖的 .NET</span><span class="sxs-lookup"><span data-stu-id="46c74-129">.NET for Apache Spark roadmap</span></span>

<span data-ttu-id="46c74-130">從官方[.NET 瞭解阿帕奇 Spark 路線圖](https://github.com/dotnet/spark/blob/master/ROADMAP.md)的短期和長期計畫。</span><span class="sxs-lookup"><span data-stu-id="46c74-130">Learn about short term and long term plans from the official [.NET for Apache Spark roadmap](https://github.com/dotnet/spark/blob/master/ROADMAP.md).</span></span>

## <a name="net-foundation"></a><span data-ttu-id="46c74-131">.NET Foundation</span><span class="sxs-lookup"><span data-stu-id="46c74-131">.NET Foundation</span></span>

<span data-ttu-id="46c74-132">.NET for Apache Spark 專案是 [.NET Foundation](https://www.dotnetfoundation.org/) 的一部分。</span><span class="sxs-lookup"><span data-stu-id="46c74-132">The .NET for Apache Spark project is part of the [.NET Foundation](https://www.dotnetfoundation.org/).</span></span>

## <a name="contributions"></a><span data-ttu-id="46c74-133">投稿文章</span><span class="sxs-lookup"><span data-stu-id="46c74-133">Contributions</span></span>

<span data-ttu-id="46c74-134">.NET for Apache Spark 小組鼓勵投稿，包括 GitHub 問題和提取要求。</span><span class="sxs-lookup"><span data-stu-id="46c74-134">The .NET for Apache Spark team encourages contributions, both GitHub issues and pull requests.</span></span> <span data-ttu-id="46c74-135">首先，尋找[現有的問題](https://github.com/dotnet/spark/issues)。</span><span class="sxs-lookup"><span data-stu-id="46c74-135">First, look for an [existing issue](https://github.com/dotnet/spark/issues).</span></span> <span data-ttu-id="46c74-136">如果找不到現有的問題，[請開啟新的問題](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+)。</span><span class="sxs-lookup"><span data-stu-id="46c74-136">If you can't find an existing issue, [open a new issue](https://github.com/dotnet/spark/issues?utf8=%E2%9C%93&q=is%3Aissue+is%3Aopen+).</span></span>

## <a name="next-steps"></a><span data-ttu-id="46c74-137">後續步驟</span><span class="sxs-lookup"><span data-stu-id="46c74-137">Next steps</span></span>

<span data-ttu-id="46c74-138">嘗試 .NET 的阿帕奇火花。</span><span class="sxs-lookup"><span data-stu-id="46c74-138">Try .NET for Apache Spark.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="46c74-139">教程： 開始與 .NET 的阿帕奇火花</span><span class="sxs-lookup"><span data-stu-id="46c74-139">Tutorial: Get started with .NET for Apache Spark</span></span>](./tutorials/get-started.md)
