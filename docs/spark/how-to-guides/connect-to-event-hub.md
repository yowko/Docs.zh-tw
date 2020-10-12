---
title: 將適用于 Apache Spark 的 .NET 連接至 Azure 事件中樞
description: 瞭解如何從本機 .NET 針對 Apache Spark 實例連接至 Azure 事件中樞。
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 4de4836ba2b63429e29ae819afac09c7a3998480
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2020
ms.locfileid: "91954967"
---
# <a name="connect-net-for-apache-spark-to-azure-event-hubs"></a>將適用于 Apache Spark 的 .NET 連接至 Azure 事件中樞

在本文中，您將瞭解如何使用 Azure 事件中樞將 [.net for Apache Spark](https://github.com/dotnet/spark) 應用程式連線，以讀取和寫入 Apache Kafka 串流。

## <a name="prerequisites"></a>必要條件

使用事件中樞備妥事件中樞命名空間。 如需逐步指南，請參閱 [快速入門：使用 Azure 入口網站建立事件中樞](/azure/event-hubs/event-hubs-create)。 建立事件中樞命名空間時，請務必選取標準定價層。

## <a name="what-is-azure-event-hubs"></a>什麼是 Azure 事件中樞

[Azure 事件中樞](/azure/event-hubs/event-hubs-about) 是一種大型資料串流平臺和事件內嵌服務。 它是完全受控的平臺即服務 (PaaS) ，可輕鬆地與 [Apache Kafka](https://kafka.apache.org/) 整合，讓您無需管理、設定或執行自己的叢集，就能為您提供 PaaS Kafka 體驗。

## <a name="connect-your-application-to-azure-event-hubs"></a>將您的應用程式連接到 Azure 事件中樞

1. 請取得事件中樞連接字串和完整網域名稱 (FQDN) 以供稍後使用。 如需相關指示，請參閱[取得事件中樞連接字串](/azure/event-hubs/event-hubs-get-connection-string)。
2. 在您的程式碼中使用命名空間中的詳細資料來設定下列設定，以開始從適用于 Kafka 的事件中樞讀取：
    1. 更新應用程式中的 **BOOTSTRAP_SERVERS** 和 **EH_SASL** ，如下所示：

    ```csharp
    string BOOTSTRAP_SERVERS = "hostname:9093"; // 9093 is the port used to communicate with Event Hubs, see [troubleshooting guide](https://docs.microsoft.com/azure/event-hubs/troubleshooting-guide)
    string EH_SASL = "org.apache.kafka.common.security.plain.PlainLoginModule required username=\"$ConnectionString\" password=\"<CONNECTION_STRING>\";"; // Connection string obtained from Step 1
    ```

## <a name="read-from-azure-event-hub-stream"></a>從 Azure 事件中樞串流讀取

您現在可以開始使用事件中樞進行串流處理，就像使用 Kafka 一樣。 範例程式碼如下所示：

```csharp
SparkSession spark = SparkSession
    .Builder()
    .AppName("Connect Event Hub")
    .GetOrCreate();

DataFrame df = spark
    .ReadStream()
    .Format("kafka")
    .Option("kafka.bootstrap.servers", BOOTSTRAP_SERVERS)
    .Option("subscribe", "spark-test")
    .Option("kafka.sasl.mechanism", "PLAIN")
    .Option("kafka.security.protocol", "SASL_SSL")
    .Option("kafka.sasl.jaas.config", EH_SASL)
    .Option("kafka.request.timeout.ms", "60000")
    .Option("kafka.session.timeout.ms", "60000")
    .Option("failOnDataLoss", "false")
    .Load();

DataFrame dfWrite = df
    .WriteStream()
    .OutputMode("append")
    .Format("console")
    .Start();
```

## <a name="write-to-azure-event-hub-stream"></a>寫入至 Azure 事件中樞串流

您也可以用相同的方式寫入事件中樞，如下所示：

```csharp
// df is the DataFrame to write

df.WriteStream()
    .Format("kafka")
    .Option("topic", topics)
    .Option("kafka.bootstrap.servers", BOOTSTRAP_SERVERS)
    .Option("kafka.sasl.mechanism", "PLAIN")
    .Option("kafka.security.protocol", "SASL_SSL")
    .Option("kafka.sasl.jaas.config", EH_SASL)
    .Option("checkpointLocation", "./checkpoint")
    .Start();
```

## <a name="run-your-application"></a>執行您的應用程式

若要執行 Apache Spark 應用程式的 .NET，請在 `spark-sql-kafka-0-10` Spark 專案中將模組定義為組建定義的一部分，並 `libraryDependency` 在 `build.sbt` sbt 專案中使用。 針對 (或) 這類 Spark 環境 `spark-submit` `spark-shell` ，請使用 `--packages` 命令列選項，如下所示：

```bash
spark-shell --packages org.apache.spark:spark-sql-kafka-0-10_2.12:2.4.5
```

> [!NOTE]
> 請務必根據執行中的 Spark 版本包含套件版本。
