---
title: 將適用于 Apache Spark 的 .NET 連接至 Azure 事件中樞
description: 瞭解如何從本機 .NET 針對 Apache Spark 實例連接至 Azure 事件中樞。
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 3956a8152feb743f205f29334f0d42b3165cb27b
ms.sourcegitcommit: eb7e87496f42361b1da98562dd75b516c9d58bbc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2020
ms.locfileid: "91877840"
---
# <a name="connect-net-for-apache-spark-to-azure-event-hubs"></a><span data-ttu-id="5d12a-103">將適用于 Apache Spark 的 .NET 連接至 Azure 事件中樞</span><span class="sxs-lookup"><span data-stu-id="5d12a-103">Connect .NET for Apache Spark to Azure Event Hubs</span></span>

<span data-ttu-id="5d12a-104">在本文中，您將瞭解如何使用 Azure 事件中樞將 [.net for Apache Spark](https://github.com/dotnet/spark) 應用程式連線，以讀取和寫入 Apache Kafka 串流。</span><span class="sxs-lookup"><span data-stu-id="5d12a-104">In this article, you will learn how to connect your [.NET for Apache Spark](https://github.com/dotnet/spark) application with Azure Event Hubs to read and write Apache Kafka streams.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5d12a-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="5d12a-105">Prerequisites</span></span>

1. <span data-ttu-id="5d12a-106">讓事件中樞命名空間準備好使用事件中樞，請參閱 [這份檔](https://docs.microsoft.com/azure/event-hubs/event-hubs-create) ，以取得如何執行此作業的逐步指南。</span><span class="sxs-lookup"><span data-stu-id="5d12a-106">Have an Event Hubs Namespace ready with an event hub, refer to [this document](https://docs.microsoft.com/azure/event-hubs/event-hubs-create) for a step-by-step guide on how to do that.</span></span> <span data-ttu-id="5d12a-107">建立事件中樞命名空間時，請務必選取標準定價層。</span><span class="sxs-lookup"><span data-stu-id="5d12a-107">Make sure to select the Standard Pricing tier while creating the Event Hub Namespace.</span></span>

## <a name="what-is-azure-event-hubs"></a><span data-ttu-id="5d12a-108">什麼是 Azure 事件中樞</span><span class="sxs-lookup"><span data-stu-id="5d12a-108">What is Azure Event Hubs</span></span>

<span data-ttu-id="5d12a-109">[Azure 事件中樞](https://docs.microsoft.com/en-us/azure/event-hubs/event-hubs-about) 是大型的資料串流平臺和事件內嵌服務。</span><span class="sxs-lookup"><span data-stu-id="5d12a-109">[Azure Event Hubs](https://docs.microsoft.com/en-us/azure/event-hubs/event-hubs-about) is a big data streaming platform and event ingestion service.</span></span> <span data-ttu-id="5d12a-110">它是完全受控的平臺即服務 (PaaS) ，可輕鬆地與 [Apache Kafka](https://kafka.apache.org/) 整合，讓您無需管理、設定或執行自己的叢集，就能為您提供 PaaS Kafka 體驗。</span><span class="sxs-lookup"><span data-stu-id="5d12a-110">It is a fully managed Platform-as-a-Service (PaaS), that can easily integrate with [Apache Kafka](https://kafka.apache.org/) to give you the PaaS Kafka experience without having to manage, configure or run your own clusters.</span></span>

## <a name="connect-your-application-to-azure-event-hubs"></a><span data-ttu-id="5d12a-111">將您的應用程式連接到 Azure 事件中樞</span><span class="sxs-lookup"><span data-stu-id="5d12a-111">Connect your application to Azure Event Hubs</span></span>

1. <span data-ttu-id="5d12a-112">請取得事件中樞連接字串和完整網域名稱 (FQDN) 以供稍後使用。</span><span class="sxs-lookup"><span data-stu-id="5d12a-112">Get the Event Hubs connection string and fully qualified domain name (FQDN) for later use.</span></span> <span data-ttu-id="5d12a-113">如需相關指示，請參閱[取得事件中樞連接字串](https://docs.microsoft.com/azure/event-hubs/event-hubs-get-connection-string)。</span><span class="sxs-lookup"><span data-stu-id="5d12a-113">For instructions, see [Get an Event Hubs connection string](https://docs.microsoft.com/azure/event-hubs/event-hubs-get-connection-string).</span></span>
2. <span data-ttu-id="5d12a-114">在您的程式碼中使用命名空間中的詳細資料來設定下列設定，以開始從適用于 Kafka 的事件中樞讀取：</span><span class="sxs-lookup"><span data-stu-id="5d12a-114">Set the following configurations with details from your namespace in your code to start reading from Event Hubs for Kafka:</span></span>
    1. <span data-ttu-id="5d12a-115">更新應用程式中的 **BOOTSTRAP_SERVERS** 和 **EH_SASL** ，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5d12a-115">Update **BOOTSTRAP_SERVERS** and **EH_SASL** in your application like so:</span></span>

    ```csharp
    string BOOTSTRAP_SERVERS = "hostname:9093"; // 9093 is the port used to communicate with Event Hubs, see [troubleshooting guide](https://docs.microsoft.com/azure/event-hubs/troubleshooting-guide)
    string EH_SASL = "org.apache.kafka.common.security.plain.PlainLoginModule required username=\"$ConnectionString\" password=\"<CONNECTION_STRING>\";"; // Connection string obtained from Step 1
    ```

## <a name="read-from-azure-event-hub-stream"></a><span data-ttu-id="5d12a-116">從 Azure 事件中樞串流讀取</span><span class="sxs-lookup"><span data-stu-id="5d12a-116">Read from Azure Event Hub stream</span></span>

<span data-ttu-id="5d12a-117">您現在可以開始使用事件中樞進行串流處理，就像使用 Kafka 一樣。</span><span class="sxs-lookup"><span data-stu-id="5d12a-117">You can now start streaming with Event Hubs as you would with Kafka.</span></span> <span data-ttu-id="5d12a-118">範例程式碼如下所示：</span><span class="sxs-lookup"><span data-stu-id="5d12a-118">Sample code as shown below:</span></span>

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

## <a name="write-to-azure-event-hub-stream"></a><span data-ttu-id="5d12a-119">寫入至 Azure 事件中樞串流</span><span class="sxs-lookup"><span data-stu-id="5d12a-119">Write to Azure Event Hub stream</span></span>

<span data-ttu-id="5d12a-120">您也可以用相同的方式寫入事件中樞，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5d12a-120">You can also write to Event Hubs in the same way, as shown below:</span></span>

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

## <a name="run-your-application"></a><span data-ttu-id="5d12a-121">執行您的應用程式</span><span class="sxs-lookup"><span data-stu-id="5d12a-121">Run your application</span></span>

<span data-ttu-id="5d12a-122">若要執行 Apache Spark 應用程式的 .NET，您應該在 `spark-sql-kafka-0-10` Spark 專案中將模組定義為組建定義的一部分，並 `libraryDependency` 在 `build.sbt` sbt 專案中使用。</span><span class="sxs-lookup"><span data-stu-id="5d12a-122">In order to run your .NET for Apache Spark application, you should define the `spark-sql-kafka-0-10` module as part of the build definition in your Spark project, using `libraryDependency` in `build.sbt` for sbt projects.</span></span> <span data-ttu-id="5d12a-123">針對 (或) 這類 Spark 環境 `spark-submit` `spark-shell` ，您應該使用 `--packages` 命令列選項，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5d12a-123">For Spark environments such as `spark-submit` (or `spark-shell`) you should use the `--packages` command-line option like so:</span></span>

```bash
spark-shell --packages org.apache.spark:spark-sql-kafka-0-10_2.12:2.4.5
```

> [!NOTE]
> <span data-ttu-id="5d12a-124">請務必根據執行中的 Spark 版本包含套件版本。</span><span class="sxs-lookup"><span data-stu-id="5d12a-124">Make sure to include the package version in accordance with the version of Spark being run.</span></span>
