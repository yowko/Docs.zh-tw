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
# <a name="what-is-apache-spark"></a>什麼是 Apache Spark？

[Apache Spark](https://spark.apache.org/)是一個開源並行處理框架，支援記憶體處理，以提高分析大資料的應用程式的性能。 大資料解決方案旨在處理傳統資料庫過大或過於複雜的資料。 Spark 在記憶體中處理大量資料，這比基於磁片的替代方法要快得多。

## <a name="common-big-data-scenarios"></a>常見的大資料方案

如果需要存儲和處理大量資料、轉換非結構化資料或處理流資料，則可以考慮大資料體系結構。 Spark 是一個通用分散式處理引擎，可用於多個大資料方案。

### <a name="extract-transform-and-load-etl"></a>擷取、轉換和載入 (ETL)

[擷取、轉換和下載 （ETL）](/azure/architecture/data-guide/relational-data/etl)是從一個或多個源收集資料、修改資料並將資料移動到新資料存儲的過程。 轉換資料的方法有多種，包括：

* Filtering
* 排序
* 聚合
* 加入
* 清洗
* 分化
* Validating

### <a name="real-time-data-stream-processing"></a>即時資料流處理

流資料或即時資料是動態資料。 來自 IoT 設備、網路日誌和點擊流的遙測都是流資料的示例。 可以處理即時資料以提供有用的資訊，如地理空間分析、遠端監視和異常檢測。 與關係資料一樣，在將資料移動到輸出接收器之前，您可以篩選、聚合和準備流資料。 Apache Spark 支援通過[Spark](https://spark.apache.org/streaming/)[流進行即時資料流處理](/azure/architecture/data-guide/big-data/real-time-processing)。

### <a name="batch-processing"></a>批次處理

[批次處理](/azure/architecture/data-guide/big-data/batch-processing)是處理靜止的大資料。 您可以使用長時間運行的作業並行篩選、聚合和準備非常大的資料集。

### <a name="machine-learning-through-mllib"></a>通過 MLlib 進行機器學習

機器學慣用于高級分析問題。 您的電腦可以使用現有資料來預測或預測未來的行為、結果和趨勢。 Apache Spark 的機器學習庫[MLlib](https://spark.apache.org/mllib/)包含多個機器學習演算法和實用程式。

### <a name="graph-processing-through-graphx"></a>通過圖形X進行圖形處理

圖形是按邊緣連接的節點的集合。 如果您有層次結構資料或具有互連關係的資料，則可以使用圖形資料庫。 您可以使用 Apache Spark 的[GraphX](https://spark.apache.org/graphx/) API 處理此資料。

### <a name="sql-and-structured-data-processing-with-spark-sql"></a>使用 Spark SQL 進行 SQL 和結構化資料處理

如果您正在使用結構化（格式化）資料，則可以使用[Spark SQL](https://spark.apache.org/sql/)在 Spark 應用程式中使用 SQL 查詢。

## <a name="apache-spark-architecture"></a>阿帕奇火花架構

Apache Spark 使用主/輔助體系結構，它有三個主要元件：驅動程式、執行器和群集管理器。

![阿帕奇火花架構](media/spark-architecture.png)

### <a name="driver"></a>驅動程式

驅動程式由程式（如 C# 主控台應用）和 Spark 會話組成。 Spark 會話將程式劃分為較小的任務，由執行器處理。

### <a name="executors"></a>執行程式

每個執行器或輔助節點從驅動程式接收任務並執行該任務。 執行器駐留在稱為群集的實體上。

### <a name="cluster-manager"></a>群集管理器

群集管理器與驅動程式和執行器進行通信，以便：

* 管理資源配置
* 管理計畫部門
* 管理程式執行

## <a name="language-support"></a>語言支援

Apache Spark 支援以下程式設計語言：

* Scala
* Python
* Java
* SQL
* R
* .NET

## <a name="spark-apis"></a>火花 API

Apache Spark 支援以下 API：

* [火花斯卡拉 API](https://spark.apache.org/docs/2.2.0/api/scala/index.html)
* [火花JAVA API](https://spark.apache.org/docs/2.2.0/api/java/index.html)
* [火花 Python API](https://spark.apache.org/docs/2.2.0/api/python/index.html)
* [火花 R API](https://spark.apache.org/docs/2.2.0/api/R/index.html)
* [火花 SQL，](https://spark.apache.org/docs/latest/api/sql/index.html)內置功能

## <a name="next-steps"></a>後續步驟

瞭解如何在 .NET 應用程式中使用 Apache Spark。 使用 .NET 表示 Apache Spark，具有 .NET 經驗和業務邏輯的開發人員可以在 C# 和 F# 中編寫大資料查詢。
> [!div class="nextstepaction"]
> [什麼是阿帕奇火花的 .NET](what-is-apache-spark-dotnet.md)
