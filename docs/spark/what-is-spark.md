---
title: 什麼是 Apache Spark？
description: 瞭解 Apache Spark 和 big data 案例。
ms.date: 10/15/2019
ms.topic: conceptual
ms.custom: mvc
ms.openlocfilehash: 187a37897c23809d91820bd79b476e775fb5b99b
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583476"
---
# <a name="what-is-apache-spark"></a>什麼是 Apache Spark？

[Apache Spark](https://spark.apache.org/)是一種開放原始碼平行處理架構，可支援記憶體內部處理，以提升分析海量資料之應用程式的效能。 Big data 解決方案是設計用來處理對於傳統資料庫而言太大或太複雜的資料。 Spark 會處理記憶體中的大量資料，速度會比以磁片為基礎的替代專案快很多。 

## <a name="common-big-data-scenarios"></a>常見的 big data 案例

如果您需要儲存和處理大量資料、轉換非結構化資料，或處理串流資料，則可以考慮使用大型資料架構。 Spark 是一般用途的分散式處理引擎，可用於數個大型資料案例。 

### <a name="extract-transform-and-load-etl"></a>解壓縮、轉換和載入（ETL）

[[解壓縮]、[轉換] 和 [載入（ETL）](/azure/architecture/data-guide/relational-data/etl) ] 是從一個或多個來源收集資料、修改資料，以及將資料移至新資料存放區的程式。 有數種方式可以轉換資料，包括：

* 篩選
* 排序
* 匯總
* 聯結
* 走
* 刪除重復資料
* Xrml

### <a name="real-time-data-stream-processing"></a>即時資料流處理

資料流程或即時資料是移動中的資料。 IoT 裝置、weblog 和點選流的遙測全都是串流資料的範例。 可以處理即時資料，以提供有用的資訊，例如地理空間分析、遠端監視和異常偵測。 就像關聯式資料，您可以先篩選、匯總和準備串流資料，再將資料移至輸出接收。 Apache Spark 支援透過[Spark 串流](https://spark.apache.org/streaming/)[處理即時資料流](/azure/architecture/data-guide/big-data/real-time-processing)。 

### <a name="batch-processing"></a>批次處理

[批次處理](/azure/architecture/data-guide/big-data/batch-processing)是處理海量資料。 您可以使用長時間執行的作業，以平行方式篩選、匯總和準備非常大型的資料集。

### <a name="machine-learning-through-mllib"></a>透過 MLlib 的機器學習服務

機器學慣用來進行先進的分析問題。 您的電腦可以使用現有的資料來預測或預測未來的行為、結果和趨勢。 Apache Spark 的機器學習程式庫（ [MLlib](https://spark.apache.org/mllib/)）包含數個機器學習服務演算法和公用程式。

### <a name="graph-processing-through-graphx"></a>透過 GraphX 的圖形處理

圖形是以邊緣連接的節點集合。 如果您已階層資料或具有相互關聯關聯性的資料，則可以使用圖形資料庫。 您可以使用 Apache Spark 的[GraphX](https://spark.apache.org/graphx/) API 來處理此資料。

### <a name="sql-and-structured-data-processing-with-spark-sql"></a>使用 Spark SQL 進行 SQL 和結構化資料處理

如果您使用的是結構化（格式化）資料，您可以在 Spark 應用程式中使用[SPARK sql](https://spark.apache.org/sql/)來使用 SQL 查詢。

## <a name="apache-spark-architecture"></a>Apache Spark 架構

使用主要/背景工作架構的 Apache Spark 有三個主要元件：驅動程式、執行器和叢集管理員。

![Apache Spark 架構](media/spark-architecture.png)

### <a name="driver"></a>驅動器

此驅動程式是由您的程式（ C#例如主控台應用程式和 Spark 會話）所組成。 Spark 會話會採用您的程式，並將其分成執行器所處理的較小工作。

### <a name="executors"></a>執行

每個執行程式（或背景工作角色節點）都會從驅動程式接收工作，並執行該工作。 執行程式位於稱為叢集的實體上。

### <a name="cluster-manager"></a>叢集管理員

叢集管理員會與驅動程式和執行程式通訊，以進行下列動作：

* 管理資源配置
* 管理程式部門
* 管理程式執行

## <a name="language-support"></a>語言支援

Apache Spark 支援下列程式設計語言：

* Scala
* Python
* Java
* SQL
* R
* .NET

## <a name="spark-apis"></a>Spark Api

Apache Spark 支援下列 Api：

* [Spark Scala API](https://spark.apache.org/docs/2.2.0/api/scala/index.html)
* [Spark JAVA API](https://spark.apache.org/docs/2.2.0/api/java/index.html)
* [Spark Python API](https://spark.apache.org/docs/2.2.0/api/python/index.html)
* [Spark R API](https://spark.apache.org/docs/2.2.0/api/R/index.html)
* [SPARK SQL](https://spark.apache.org/docs/latest/api/sql/index.html)，內建函數

## <a name="next-steps"></a>後續步驟

瞭解您可以如何在 .NET 應用程式中使用 Apache Spark。 有了適用于 Apache Spark 的 .NET，具有 .NET 經驗和商務邏輯的開發人員可以C#在F#和中撰寫大型資料查詢。
> [!div class="nextstepaction"]
> [什麼是適用于 Apache Spark 的 .NET](what-is-apache-spark-dotnet.md)
