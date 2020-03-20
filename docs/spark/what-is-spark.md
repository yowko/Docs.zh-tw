---
title: 什麼是 Apache Spark？
description: 瞭解 Apache Spark 和大資料方案。
ms.date: 10/15/2019
ms.topic: conceptual
ms.custom: mvc
ms.openlocfilehash: 653f355d09a045feabb3dee0f5737cb691cf2dc4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "73458172"
---
# <a name="what-is-apache-spark"></a><span data-ttu-id="3861f-103">什麼是 Apache Spark？</span><span class="sxs-lookup"><span data-stu-id="3861f-103">What is Apache Spark?</span></span>

<span data-ttu-id="3861f-104">[Apache Spark](https://spark.apache.org/)是一個開源並行處理框架，支援記憶體處理，以提高分析大資料的應用程式的性能。</span><span class="sxs-lookup"><span data-stu-id="3861f-104">[Apache Spark](https://spark.apache.org/) is an open-source parallel processing framework that supports in-memory processing to boost the performance of applications that analyze big data.</span></span> <span data-ttu-id="3861f-105">大資料解決方案旨在處理傳統資料庫過大或過於複雜的資料。</span><span class="sxs-lookup"><span data-stu-id="3861f-105">Big data solutions are designed to handle data that is too large or complex for traditional databases.</span></span> <span data-ttu-id="3861f-106">Spark 在記憶體中處理大量資料，這比基於磁片的替代方法要快得多。</span><span class="sxs-lookup"><span data-stu-id="3861f-106">Spark processes large amounts of data in memory, which is much faster than disk-based alternatives.</span></span>

## <a name="common-big-data-scenarios"></a><span data-ttu-id="3861f-107">常見的大資料方案</span><span class="sxs-lookup"><span data-stu-id="3861f-107">Common big data scenarios</span></span>

<span data-ttu-id="3861f-108">如果需要存儲和處理大量資料、轉換非結構化資料或處理流資料，則可以考慮大資料體系結構。</span><span class="sxs-lookup"><span data-stu-id="3861f-108">You might consider a big data architecture if you need to store and process large volumes of data, transform unstructured data, or processes streaming data.</span></span> <span data-ttu-id="3861f-109">Spark 是一個通用分散式處理引擎，可用於多個大資料方案。</span><span class="sxs-lookup"><span data-stu-id="3861f-109">Spark is a general-purpose distributed processing engine that can be used for several big data scenarios.</span></span>

### <a name="extract-transform-and-load-etl"></a><span data-ttu-id="3861f-110">擷取、轉換和載入 (ETL)</span><span class="sxs-lookup"><span data-stu-id="3861f-110">Extract, transform, and load (ETL)</span></span>

<span data-ttu-id="3861f-111">[擷取、轉換和下載 （ETL）](/azure/architecture/data-guide/relational-data/etl)是從一個或多個源收集資料、修改資料並將資料移動到新資料存儲的過程。</span><span class="sxs-lookup"><span data-stu-id="3861f-111">[Extract, transform, and load (ETL)](/azure/architecture/data-guide/relational-data/etl) is the process of collecting data from one or multiple sources, modifying the data, and moving the data to a new data store.</span></span> <span data-ttu-id="3861f-112">轉換資料的方法有多種，包括：</span><span class="sxs-lookup"><span data-stu-id="3861f-112">There are several ways to transform data, including:</span></span>

* <span data-ttu-id="3861f-113">Filtering</span><span class="sxs-lookup"><span data-stu-id="3861f-113">Filtering</span></span>
* <span data-ttu-id="3861f-114">排序</span><span class="sxs-lookup"><span data-stu-id="3861f-114">Sorting</span></span>
* <span data-ttu-id="3861f-115">聚合</span><span class="sxs-lookup"><span data-stu-id="3861f-115">Aggregating</span></span>
* <span data-ttu-id="3861f-116">加入</span><span class="sxs-lookup"><span data-stu-id="3861f-116">Joining</span></span>
* <span data-ttu-id="3861f-117">清洗</span><span class="sxs-lookup"><span data-stu-id="3861f-117">Cleaning</span></span>
* <span data-ttu-id="3861f-118">分化</span><span class="sxs-lookup"><span data-stu-id="3861f-118">Deduplicating</span></span>
* <span data-ttu-id="3861f-119">Validating</span><span class="sxs-lookup"><span data-stu-id="3861f-119">Validating</span></span>

### <a name="real-time-data-stream-processing"></a><span data-ttu-id="3861f-120">即時資料流處理</span><span class="sxs-lookup"><span data-stu-id="3861f-120">Real-time data stream processing</span></span>

<span data-ttu-id="3861f-121">流資料或即時資料是動態資料。</span><span class="sxs-lookup"><span data-stu-id="3861f-121">Streaming, or real-time, data is data in motion.</span></span> <span data-ttu-id="3861f-122">來自 IoT 設備、網路日誌和點擊流的遙測都是流資料的示例。</span><span class="sxs-lookup"><span data-stu-id="3861f-122">Telemetry from IoT devices, weblogs, and clickstreams are all examples of streaming data.</span></span> <span data-ttu-id="3861f-123">可以處理即時資料以提供有用的資訊，如地理空間分析、遠端監視和異常檢測。</span><span class="sxs-lookup"><span data-stu-id="3861f-123">Real-time data can be processed to provide useful information, such as geospatial analysis, remote monitoring, and anomaly detection.</span></span> <span data-ttu-id="3861f-124">與關係資料一樣，在將資料移動到輸出接收器之前，您可以篩選、聚合和準備流資料。</span><span class="sxs-lookup"><span data-stu-id="3861f-124">Just like relational data, you can filter, aggregate, and prepare streaming data before moving the data to an output sink.</span></span> <span data-ttu-id="3861f-125">Apache Spark 支援通過[Spark](https://spark.apache.org/streaming/)[流進行即時資料流處理](/azure/architecture/data-guide/big-data/real-time-processing)。</span><span class="sxs-lookup"><span data-stu-id="3861f-125">Apache Spark supports [real-time data stream processing](/azure/architecture/data-guide/big-data/real-time-processing) through [Spark Streaming](https://spark.apache.org/streaming/).</span></span>

### <a name="batch-processing"></a><span data-ttu-id="3861f-126">批次處理</span><span class="sxs-lookup"><span data-stu-id="3861f-126">Batch processing</span></span>

<span data-ttu-id="3861f-127">[批次處理](/azure/architecture/data-guide/big-data/batch-processing)是處理靜止的大資料。</span><span class="sxs-lookup"><span data-stu-id="3861f-127">[Batch processing](/azure/architecture/data-guide/big-data/batch-processing) is the processing of big data at rest.</span></span> <span data-ttu-id="3861f-128">您可以使用長時間運行的作業並行篩選、聚合和準備非常大的資料集。</span><span class="sxs-lookup"><span data-stu-id="3861f-128">You can filter, aggregate, and prepare very large datasets using long-running jobs in parallel.</span></span>

### <a name="machine-learning-through-mllib"></a><span data-ttu-id="3861f-129">通過 MLlib 進行機器學習</span><span class="sxs-lookup"><span data-stu-id="3861f-129">Machine learning through MLlib</span></span>

<span data-ttu-id="3861f-130">機器學慣用于高級分析問題。</span><span class="sxs-lookup"><span data-stu-id="3861f-130">Machine learning is used for advanced analytical problems.</span></span> <span data-ttu-id="3861f-131">您的電腦可以使用現有資料來預測或預測未來的行為、結果和趨勢。</span><span class="sxs-lookup"><span data-stu-id="3861f-131">Your computer can use existing data to forecast or predict future behaviors, outcomes, and trends.</span></span> <span data-ttu-id="3861f-132">Apache Spark 的機器學習庫[MLlib](https://spark.apache.org/mllib/)包含多個機器學習演算法和實用程式。</span><span class="sxs-lookup"><span data-stu-id="3861f-132">Apache Spark's machine learning library, [MLlib](https://spark.apache.org/mllib/), contains several machine learning algorithms and utilities.</span></span>

### <a name="graph-processing-through-graphx"></a><span data-ttu-id="3861f-133">通過圖形X進行圖形處理</span><span class="sxs-lookup"><span data-stu-id="3861f-133">Graph processing through GraphX</span></span>

<span data-ttu-id="3861f-134">圖形是按邊緣連接的節點的集合。</span><span class="sxs-lookup"><span data-stu-id="3861f-134">A graph is a collection of nodes connected by edges.</span></span> <span data-ttu-id="3861f-135">如果您有層次結構資料或具有互連關係的資料，則可以使用圖形資料庫。</span><span class="sxs-lookup"><span data-stu-id="3861f-135">You might use a graph database if you have hierarchial data or data with interconnected relationships.</span></span> <span data-ttu-id="3861f-136">您可以使用 Apache Spark 的[GraphX](https://spark.apache.org/graphx/) API 處理此資料。</span><span class="sxs-lookup"><span data-stu-id="3861f-136">You can process this data using Apache Spark's [GraphX](https://spark.apache.org/graphx/) API.</span></span>

### <a name="sql-and-structured-data-processing-with-spark-sql"></a><span data-ttu-id="3861f-137">使用 Spark SQL 進行 SQL 和結構化資料處理</span><span class="sxs-lookup"><span data-stu-id="3861f-137">SQL and structured data processing with Spark SQL</span></span>

<span data-ttu-id="3861f-138">如果您正在使用結構化（格式化）資料，則可以使用[Spark SQL](https://spark.apache.org/sql/)在 Spark 應用程式中使用 SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="3861f-138">If you're working with structured (formatted) data, you can use SQL queries in your Spark application using [Spark SQL](https://spark.apache.org/sql/).</span></span>

## <a name="apache-spark-architecture"></a><span data-ttu-id="3861f-139">阿帕奇火花架構</span><span class="sxs-lookup"><span data-stu-id="3861f-139">Apache Spark architecture</span></span>

<span data-ttu-id="3861f-140">Apache Spark 使用主/輔助體系結構，它有三個主要元件：驅動程式、執行器和群集管理器。</span><span class="sxs-lookup"><span data-stu-id="3861f-140">Apache Spark, which uses the master/worker architecture, has three main components: the driver, executors, and cluster manager.</span></span>

![阿帕奇火花架構](media/spark-architecture.png)

### <a name="driver"></a><span data-ttu-id="3861f-142">驅動程式</span><span class="sxs-lookup"><span data-stu-id="3861f-142">Driver</span></span>

<span data-ttu-id="3861f-143">驅動程式由程式（如 C# 主控台應用）和 Spark 會話組成。</span><span class="sxs-lookup"><span data-stu-id="3861f-143">The driver consists of your program, like a C# console app, and a Spark session.</span></span> <span data-ttu-id="3861f-144">Spark 會話將程式劃分為較小的任務，由執行器處理。</span><span class="sxs-lookup"><span data-stu-id="3861f-144">The Spark session takes your program and divides it into smaller tasks that are handled by the executors.</span></span>

### <a name="executors"></a><span data-ttu-id="3861f-145">執行程式</span><span class="sxs-lookup"><span data-stu-id="3861f-145">Executors</span></span>

<span data-ttu-id="3861f-146">每個執行器或輔助節點從驅動程式接收任務並執行該任務。</span><span class="sxs-lookup"><span data-stu-id="3861f-146">Each executor, or worker node, receives a task from the driver and executes that task.</span></span> <span data-ttu-id="3861f-147">執行器駐留在稱為群集的實體上。</span><span class="sxs-lookup"><span data-stu-id="3861f-147">The executors reside on an entity known as a cluster.</span></span>

### <a name="cluster-manager"></a><span data-ttu-id="3861f-148">群集管理器</span><span class="sxs-lookup"><span data-stu-id="3861f-148">Cluster manager</span></span>

<span data-ttu-id="3861f-149">群集管理器與驅動程式和執行器進行通信，以便：</span><span class="sxs-lookup"><span data-stu-id="3861f-149">The cluster manager communicates with both the driver and the executors to:</span></span>

* <span data-ttu-id="3861f-150">管理資源配置</span><span class="sxs-lookup"><span data-stu-id="3861f-150">Manage resource allocation</span></span>
* <span data-ttu-id="3861f-151">管理計畫部門</span><span class="sxs-lookup"><span data-stu-id="3861f-151">Manage program division</span></span>
* <span data-ttu-id="3861f-152">管理程式執行</span><span class="sxs-lookup"><span data-stu-id="3861f-152">Manage program execution</span></span>

## <a name="language-support"></a><span data-ttu-id="3861f-153">語言支援</span><span class="sxs-lookup"><span data-stu-id="3861f-153">Language support</span></span>

<span data-ttu-id="3861f-154">Apache Spark 支援以下程式設計語言：</span><span class="sxs-lookup"><span data-stu-id="3861f-154">Apache Spark supports the following programming languages:</span></span>

* <span data-ttu-id="3861f-155">Scala</span><span class="sxs-lookup"><span data-stu-id="3861f-155">Scala</span></span>
* <span data-ttu-id="3861f-156">Python</span><span class="sxs-lookup"><span data-stu-id="3861f-156">Python</span></span>
* <span data-ttu-id="3861f-157">Java</span><span class="sxs-lookup"><span data-stu-id="3861f-157">Java</span></span>
* <span data-ttu-id="3861f-158">SQL</span><span class="sxs-lookup"><span data-stu-id="3861f-158">SQL</span></span>
* <span data-ttu-id="3861f-159">R</span><span class="sxs-lookup"><span data-stu-id="3861f-159">R</span></span>
* <span data-ttu-id="3861f-160">.NET</span><span class="sxs-lookup"><span data-stu-id="3861f-160">.NET</span></span>

## <a name="spark-apis"></a><span data-ttu-id="3861f-161">火花 API</span><span class="sxs-lookup"><span data-stu-id="3861f-161">Spark APIs</span></span>

<span data-ttu-id="3861f-162">Apache Spark 支援以下 API：</span><span class="sxs-lookup"><span data-stu-id="3861f-162">Apache Spark supports the following APIs:</span></span>

* [<span data-ttu-id="3861f-163">火花斯卡拉 API</span><span class="sxs-lookup"><span data-stu-id="3861f-163">Spark Scala API</span></span>](https://spark.apache.org/docs/2.2.0/api/scala/index.html)
* [<span data-ttu-id="3861f-164">火花JAVA API</span><span class="sxs-lookup"><span data-stu-id="3861f-164">Spark Java API</span></span>](https://spark.apache.org/docs/2.2.0/api/java/index.html)
* [<span data-ttu-id="3861f-165">火花 Python API</span><span class="sxs-lookup"><span data-stu-id="3861f-165">Spark Python API</span></span>](https://spark.apache.org/docs/2.2.0/api/python/index.html)
* [<span data-ttu-id="3861f-166">火花 R API</span><span class="sxs-lookup"><span data-stu-id="3861f-166">Spark R API</span></span>](https://spark.apache.org/docs/2.2.0/api/R/index.html)
* <span data-ttu-id="3861f-167">[火花 SQL，](https://spark.apache.org/docs/latest/api/sql/index.html)內置功能</span><span class="sxs-lookup"><span data-stu-id="3861f-167">[Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), built-in functions</span></span>

## <a name="next-steps"></a><span data-ttu-id="3861f-168">後續步驟</span><span class="sxs-lookup"><span data-stu-id="3861f-168">Next steps</span></span>

<span data-ttu-id="3861f-169">瞭解如何在 .NET 應用程式中使用 Apache Spark。</span><span class="sxs-lookup"><span data-stu-id="3861f-169">Learn how you can use Apache Spark in your .NET application.</span></span> <span data-ttu-id="3861f-170">使用 .NET 表示 Apache Spark，具有 .NET 經驗和業務邏輯的開發人員可以在 C# 和 F# 中編寫大資料查詢。</span><span class="sxs-lookup"><span data-stu-id="3861f-170">With .NET for Apache Spark, developers with .NET experience and business logic can write big data queries in C# and F#.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="3861f-171">什麼是阿帕奇火花的 .NET</span><span class="sxs-lookup"><span data-stu-id="3861f-171">What is .NET for Apache Spark</span></span>](what-is-apache-spark-dotnet.md)
