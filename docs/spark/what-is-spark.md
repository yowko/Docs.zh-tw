---
title: 什麼是 Apache Spark？
description: 瞭解 Apache Spark 和 big data 案例。
ms.date: 10/15/2019
ms.topic: conceptual
ms.custom: mvc
ms.openlocfilehash: 653f355d09a045feabb3dee0f5737cb691cf2dc4
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458172"
---
# <a name="what-is-apache-spark"></a><span data-ttu-id="0a380-103">什麼是 Apache Spark？</span><span class="sxs-lookup"><span data-stu-id="0a380-103">What is Apache Spark?</span></span>

<span data-ttu-id="0a380-104">[Apache Spark](https://spark.apache.org/)是一種開放原始碼平行處理架構，可支援記憶體內部處理，以提升分析海量資料之應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="0a380-104">[Apache Spark](https://spark.apache.org/) is an open-source parallel processing framework that supports in-memory processing to boost the performance of applications that analyze big data.</span></span> <span data-ttu-id="0a380-105">Big data 解決方案是設計用來處理對於傳統資料庫而言太大或太複雜的資料。</span><span class="sxs-lookup"><span data-stu-id="0a380-105">Big data solutions are designed to handle data that is too large or complex for traditional databases.</span></span> <span data-ttu-id="0a380-106">Spark 會處理記憶體中的大量資料，速度會比以磁片為基礎的替代專案快很多。</span><span class="sxs-lookup"><span data-stu-id="0a380-106">Spark processes large amounts of data in memory, which is much faster than disk-based alternatives.</span></span>

## <a name="common-big-data-scenarios"></a><span data-ttu-id="0a380-107">常見的 big data 案例</span><span class="sxs-lookup"><span data-stu-id="0a380-107">Common big data scenarios</span></span>

<span data-ttu-id="0a380-108">如果您需要儲存和處理大量資料、轉換非結構化資料，或處理串流資料，則可以考慮使用大型資料架構。</span><span class="sxs-lookup"><span data-stu-id="0a380-108">You might consider a big data architecture if you need to store and process large volumes of data, transform unstructured data, or processes streaming data.</span></span> <span data-ttu-id="0a380-109">Spark 是一般用途的分散式處理引擎，可用於數個大型資料案例。</span><span class="sxs-lookup"><span data-stu-id="0a380-109">Spark is a general-purpose distributed processing engine that can be used for several big data scenarios.</span></span>

### <a name="extract-transform-and-load-etl"></a><span data-ttu-id="0a380-110">解壓縮、轉換和載入（ETL）</span><span class="sxs-lookup"><span data-stu-id="0a380-110">Extract, transform, and load (ETL)</span></span>

<span data-ttu-id="0a380-111">[[解壓縮]、[轉換] 和 [載入（ETL）](/azure/architecture/data-guide/relational-data/etl) ] 是從一個或多個來源收集資料、修改資料，以及將資料移至新資料存放區的程式。</span><span class="sxs-lookup"><span data-stu-id="0a380-111">[Extract, transform, and load (ETL)](/azure/architecture/data-guide/relational-data/etl) is the process of collecting data from one or multiple sources, modifying the data, and moving the data to a new data store.</span></span> <span data-ttu-id="0a380-112">有數種方式可以轉換資料，包括：</span><span class="sxs-lookup"><span data-stu-id="0a380-112">There are several ways to transform data, including:</span></span>

* <span data-ttu-id="0a380-113">篩選</span><span class="sxs-lookup"><span data-stu-id="0a380-113">Filtering</span></span>
* <span data-ttu-id="0a380-114">排序</span><span class="sxs-lookup"><span data-stu-id="0a380-114">Sorting</span></span>
* <span data-ttu-id="0a380-115">匯總</span><span class="sxs-lookup"><span data-stu-id="0a380-115">Aggregating</span></span>
* <span data-ttu-id="0a380-116">聯結</span><span class="sxs-lookup"><span data-stu-id="0a380-116">Joining</span></span>
* <span data-ttu-id="0a380-117">走</span><span class="sxs-lookup"><span data-stu-id="0a380-117">Cleaning</span></span>
* <span data-ttu-id="0a380-118">刪除重復資料</span><span class="sxs-lookup"><span data-stu-id="0a380-118">Deduplicating</span></span>
* <span data-ttu-id="0a380-119">Xrml</span><span class="sxs-lookup"><span data-stu-id="0a380-119">Validating</span></span>

### <a name="real-time-data-stream-processing"></a><span data-ttu-id="0a380-120">即時資料流處理</span><span class="sxs-lookup"><span data-stu-id="0a380-120">Real-time data stream processing</span></span>

<span data-ttu-id="0a380-121">資料流程或即時資料是移動中的資料。</span><span class="sxs-lookup"><span data-stu-id="0a380-121">Streaming, or real-time, data is data in motion.</span></span> <span data-ttu-id="0a380-122">IoT 裝置、weblog 和點選流的遙測全都是串流資料的範例。</span><span class="sxs-lookup"><span data-stu-id="0a380-122">Telemetry from IoT devices, weblogs, and clickstreams are all examples of streaming data.</span></span> <span data-ttu-id="0a380-123">可以處理即時資料，以提供有用的資訊，例如地理空間分析、遠端監視和異常偵測。</span><span class="sxs-lookup"><span data-stu-id="0a380-123">Real-time data can be processed to provide useful information, such as geospatial analysis, remote monitoring, and anomaly detection.</span></span> <span data-ttu-id="0a380-124">就像關聯式資料，您可以先篩選、匯總和準備串流資料，再將資料移至輸出接收。</span><span class="sxs-lookup"><span data-stu-id="0a380-124">Just like relational data, you can filter, aggregate, and prepare streaming data before moving the data to an output sink.</span></span> <span data-ttu-id="0a380-125">Apache Spark 支援透過[Spark 串流](https://spark.apache.org/streaming/)[處理即時資料流](/azure/architecture/data-guide/big-data/real-time-processing)。</span><span class="sxs-lookup"><span data-stu-id="0a380-125">Apache Spark supports [real-time data stream processing](/azure/architecture/data-guide/big-data/real-time-processing) through [Spark Streaming](https://spark.apache.org/streaming/).</span></span>

### <a name="batch-processing"></a><span data-ttu-id="0a380-126">批次處理</span><span class="sxs-lookup"><span data-stu-id="0a380-126">Batch processing</span></span>

<span data-ttu-id="0a380-127">[批次處理](/azure/architecture/data-guide/big-data/batch-processing)是處理海量資料。</span><span class="sxs-lookup"><span data-stu-id="0a380-127">[Batch processing](/azure/architecture/data-guide/big-data/batch-processing) is the processing of big data at rest.</span></span> <span data-ttu-id="0a380-128">您可以使用長時間執行的作業，以平行方式篩選、匯總和準備非常大型的資料集。</span><span class="sxs-lookup"><span data-stu-id="0a380-128">You can filter, aggregate, and prepare very large datasets using long-running jobs in parallel.</span></span>

### <a name="machine-learning-through-mllib"></a><span data-ttu-id="0a380-129">透過 MLlib 的機器學習服務</span><span class="sxs-lookup"><span data-stu-id="0a380-129">Machine learning through MLlib</span></span>

<span data-ttu-id="0a380-130">機器學慣用來進行先進的分析問題。</span><span class="sxs-lookup"><span data-stu-id="0a380-130">Machine learning is used for advanced analytical problems.</span></span> <span data-ttu-id="0a380-131">您的電腦可以使用現有的資料來預測或預測未來的行為、結果和趨勢。</span><span class="sxs-lookup"><span data-stu-id="0a380-131">Your computer can use existing data to forecast or predict future behaviors, outcomes, and trends.</span></span> <span data-ttu-id="0a380-132">Apache Spark 的機器學習程式庫（ [MLlib](https://spark.apache.org/mllib/)）包含數個機器學習服務演算法和公用程式。</span><span class="sxs-lookup"><span data-stu-id="0a380-132">Apache Spark's machine learning library, [MLlib](https://spark.apache.org/mllib/), contains several machine learning algorithms and utilities.</span></span>

### <a name="graph-processing-through-graphx"></a><span data-ttu-id="0a380-133">透過 GraphX 的圖形處理</span><span class="sxs-lookup"><span data-stu-id="0a380-133">Graph processing through GraphX</span></span>

<span data-ttu-id="0a380-134">圖形是以邊緣連接的節點集合。</span><span class="sxs-lookup"><span data-stu-id="0a380-134">A graph is a collection of nodes connected by edges.</span></span> <span data-ttu-id="0a380-135">如果您已階層資料或具有相互關聯關聯性的資料，則可以使用圖形資料庫。</span><span class="sxs-lookup"><span data-stu-id="0a380-135">You might use a graph database if you have hierarchial data or data with interconnected relationships.</span></span> <span data-ttu-id="0a380-136">您可以使用 Apache Spark 的[GraphX](https://spark.apache.org/graphx/) API 來處理此資料。</span><span class="sxs-lookup"><span data-stu-id="0a380-136">You can process this data using Apache Spark's [GraphX](https://spark.apache.org/graphx/) API.</span></span>

### <a name="sql-and-structured-data-processing-with-spark-sql"></a><span data-ttu-id="0a380-137">使用 Spark SQL 進行 SQL 和結構化資料處理</span><span class="sxs-lookup"><span data-stu-id="0a380-137">SQL and structured data processing with Spark SQL</span></span>

<span data-ttu-id="0a380-138">如果您使用的是結構化（格式化）資料，您可以在 Spark 應用程式中使用[SPARK sql](https://spark.apache.org/sql/)來使用 SQL 查詢。</span><span class="sxs-lookup"><span data-stu-id="0a380-138">If you're working with structured (formatted) data, you can use SQL queries in your Spark application using [Spark SQL](https://spark.apache.org/sql/).</span></span>

## <a name="apache-spark-architecture"></a><span data-ttu-id="0a380-139">Apache Spark 架構</span><span class="sxs-lookup"><span data-stu-id="0a380-139">Apache Spark architecture</span></span>

<span data-ttu-id="0a380-140">使用主要/背景工作架構的 Apache Spark 有三個主要元件：驅動程式、執行器和叢集管理員。</span><span class="sxs-lookup"><span data-stu-id="0a380-140">Apache Spark, which uses the master/worker architecture, has three main components: the driver, executors, and cluster manager.</span></span>

![Apache Spark 架構](media/spark-architecture.png)

### <a name="driver"></a><span data-ttu-id="0a380-142">驅動器</span><span class="sxs-lookup"><span data-stu-id="0a380-142">Driver</span></span>

<span data-ttu-id="0a380-143">此驅動程式是由您的程式（ C#例如主控台應用程式和 Spark 會話）所組成。</span><span class="sxs-lookup"><span data-stu-id="0a380-143">The driver consists of your program, like a C# console app, and a Spark session.</span></span> <span data-ttu-id="0a380-144">Spark 會話會採用您的程式，並將其分成執行器所處理的較小工作。</span><span class="sxs-lookup"><span data-stu-id="0a380-144">The Spark session takes your program and divides it into smaller tasks that are handled by the executors.</span></span>

### <a name="executors"></a><span data-ttu-id="0a380-145">執行</span><span class="sxs-lookup"><span data-stu-id="0a380-145">Executors</span></span>

<span data-ttu-id="0a380-146">每個執行程式（或背景工作角色節點）都會從驅動程式接收工作，並執行該工作。</span><span class="sxs-lookup"><span data-stu-id="0a380-146">Each executor, or worker node, receives a task from the driver and executes that task.</span></span> <span data-ttu-id="0a380-147">執行程式位於稱為叢集的實體上。</span><span class="sxs-lookup"><span data-stu-id="0a380-147">The executors reside on an entity known as a cluster.</span></span>

### <a name="cluster-manager"></a><span data-ttu-id="0a380-148">叢集管理員</span><span class="sxs-lookup"><span data-stu-id="0a380-148">Cluster manager</span></span>

<span data-ttu-id="0a380-149">叢集管理員會與驅動程式和執行程式通訊，以進行下列動作：</span><span class="sxs-lookup"><span data-stu-id="0a380-149">The cluster manager communicates with both the driver and the executors to:</span></span>

* <span data-ttu-id="0a380-150">管理資源配置</span><span class="sxs-lookup"><span data-stu-id="0a380-150">Manage resource allocation</span></span>
* <span data-ttu-id="0a380-151">管理程式部門</span><span class="sxs-lookup"><span data-stu-id="0a380-151">Manage program division</span></span>
* <span data-ttu-id="0a380-152">管理程式執行</span><span class="sxs-lookup"><span data-stu-id="0a380-152">Manage program execution</span></span>

## <a name="language-support"></a><span data-ttu-id="0a380-153">語言支援</span><span class="sxs-lookup"><span data-stu-id="0a380-153">Language support</span></span>

<span data-ttu-id="0a380-154">Apache Spark 支援下列程式設計語言：</span><span class="sxs-lookup"><span data-stu-id="0a380-154">Apache Spark supports the following programming languages:</span></span>

* <span data-ttu-id="0a380-155">Scala</span><span class="sxs-lookup"><span data-stu-id="0a380-155">Scala</span></span>
* <span data-ttu-id="0a380-156">Python</span><span class="sxs-lookup"><span data-stu-id="0a380-156">Python</span></span>
* <span data-ttu-id="0a380-157">Java</span><span class="sxs-lookup"><span data-stu-id="0a380-157">Java</span></span>
* <span data-ttu-id="0a380-158">SQL</span><span class="sxs-lookup"><span data-stu-id="0a380-158">SQL</span></span>
* <span data-ttu-id="0a380-159">R</span><span class="sxs-lookup"><span data-stu-id="0a380-159">R</span></span>
* <span data-ttu-id="0a380-160">.NET</span><span class="sxs-lookup"><span data-stu-id="0a380-160">.NET</span></span>

## <a name="spark-apis"></a><span data-ttu-id="0a380-161">Spark Api</span><span class="sxs-lookup"><span data-stu-id="0a380-161">Spark APIs</span></span>

<span data-ttu-id="0a380-162">Apache Spark 支援下列 Api：</span><span class="sxs-lookup"><span data-stu-id="0a380-162">Apache Spark supports the following APIs:</span></span>

* [<span data-ttu-id="0a380-163">Spark Scala API</span><span class="sxs-lookup"><span data-stu-id="0a380-163">Spark Scala API</span></span>](https://spark.apache.org/docs/2.2.0/api/scala/index.html)
* [<span data-ttu-id="0a380-164">Spark JAVA API</span><span class="sxs-lookup"><span data-stu-id="0a380-164">Spark Java API</span></span>](https://spark.apache.org/docs/2.2.0/api/java/index.html)
* [<span data-ttu-id="0a380-165">Spark Python API</span><span class="sxs-lookup"><span data-stu-id="0a380-165">Spark Python API</span></span>](https://spark.apache.org/docs/2.2.0/api/python/index.html)
* [<span data-ttu-id="0a380-166">Spark R API</span><span class="sxs-lookup"><span data-stu-id="0a380-166">Spark R API</span></span>](https://spark.apache.org/docs/2.2.0/api/R/index.html)
* <span data-ttu-id="0a380-167">[SPARK SQL](https://spark.apache.org/docs/latest/api/sql/index.html)，內建函數</span><span class="sxs-lookup"><span data-stu-id="0a380-167">[Spark SQL](https://spark.apache.org/docs/latest/api/sql/index.html), built-in functions</span></span>

## <a name="next-steps"></a><span data-ttu-id="0a380-168">後續步驟</span><span class="sxs-lookup"><span data-stu-id="0a380-168">Next steps</span></span>

<span data-ttu-id="0a380-169">瞭解您可以如何在 .NET 應用程式中使用 Apache Spark。</span><span class="sxs-lookup"><span data-stu-id="0a380-169">Learn how you can use Apache Spark in your .NET application.</span></span> <span data-ttu-id="0a380-170">有了適用于 Apache Spark 的 .NET，具有 .NET 經驗和商務邏輯的開發人員可以C#在F#和中撰寫大型資料查詢。</span><span class="sxs-lookup"><span data-stu-id="0a380-170">With .NET for Apache Spark, developers with .NET experience and business logic can write big data queries in C# and F#.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="0a380-171">什麼是適用于 Apache Spark 的 .NET</span><span class="sxs-lookup"><span data-stu-id="0a380-171">What is .NET for Apache Spark</span></span>](what-is-apache-spark-dotnet.md)
