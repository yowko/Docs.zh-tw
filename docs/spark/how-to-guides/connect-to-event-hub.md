---
title: 將適用于 Apache Spark 的 .NET 連接至 Azure 事件中樞
description: 瞭解如何從本機 .NET 針對 Apache Spark 實例連接至 Azure 事件中樞。
ms.author: nidutta
author: Niharikadutta
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: c8fd10992e63674032af4148e0673a5330d9086c
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223964"
---
# <a name="connect-net-for-apache-spark-to-azure-event-hubs"></a><span data-ttu-id="829bc-103">將適用于 Apache Spark 的 .NET 連接至 Azure 事件中樞</span><span class="sxs-lookup"><span data-stu-id="829bc-103">Connect .NET for Apache Spark to Azure Event Hubs</span></span>

<span data-ttu-id="829bc-104">在本文中，您將瞭解如何使用 Azure 事件中樞將 [.net for Apache Spark](https://github.com/dotnet/spark) 應用程式連線，以讀取和寫入 Apache Kafka 串流。</span><span class="sxs-lookup"><span data-stu-id="829bc-104">In this article, you will learn how to connect your [.NET for Apache Spark](https://github.com/dotnet/spark) application with Azure Event Hubs to read and write Apache Kafka streams.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="829bc-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="829bc-105">Prerequisites</span></span>

<span data-ttu-id="829bc-106">使用事件中樞備妥事件中樞命名空間。</span><span class="sxs-lookup"><span data-stu-id="829bc-106">Have an Event Hubs Namespace ready with an event hub.</span></span> <span data-ttu-id="829bc-107">如需逐步指南，請參閱 [快速入門：使用 Azure 入口網站建立事件中樞](/azure/event-hubs/event-hubs-create)。</span><span class="sxs-lookup"><span data-stu-id="829bc-107">For a step-by-step guide, refer to [Quickstart: Create an event hub using Azure portal](/azure/event-hubs/event-hubs-create).</span></span> <span data-ttu-id="829bc-108">建立事件中樞命名空間時，請務必選取標準定價層。</span><span class="sxs-lookup"><span data-stu-id="829bc-108">Make sure to select the Standard Pricing tier while creating the Event Hub Namespace.</span></span>

## <a name="what-is-azure-event-hubs"></a><span data-ttu-id="829bc-109">什麼是 Azure 事件中樞</span><span class="sxs-lookup"><span data-stu-id="829bc-109">What is Azure Event Hubs</span></span>

<span data-ttu-id="829bc-110">[Azure 事件中樞](/azure/event-hubs/event-hubs-about) 是一種大型資料串流平臺和事件內嵌服務。</span><span class="sxs-lookup"><span data-stu-id="829bc-110">[Azure Event Hubs](/azure/event-hubs/event-hubs-about) is a big-data streaming platform and event-ingestion service.</span></span> <span data-ttu-id="829bc-111">它是完全受控的平臺即服務 (PaaS) ，可輕鬆地與 [Apache Kafka](https://kafka.apache.org/) 整合，讓您無需管理、設定或執行自己的叢集，就能為您提供 PaaS Kafka 體驗。</span><span class="sxs-lookup"><span data-stu-id="829bc-111">It is a fully managed Platform-as-a-Service (PaaS) that can easily integrate with [Apache Kafka](https://kafka.apache.org/) to give you the PaaS Kafka experience without having to manage, configure, or run your own clusters.</span></span>

## <a name="connect-your-application-to-azure-event-hubs"></a><span data-ttu-id="829bc-112">將您的應用程式連接到 Azure 事件中樞</span><span class="sxs-lookup"><span data-stu-id="829bc-112">Connect your application to Azure Event Hubs</span></span>

1. <span data-ttu-id="829bc-113">請取得事件中樞連接字串和完整網域名稱 (FQDN) 以供稍後使用。</span><span class="sxs-lookup"><span data-stu-id="829bc-113">Get the Event Hubs connection string and fully qualified domain name (FQDN) for later use.</span></span> <span data-ttu-id="829bc-114">如需相關指示，請參閱[取得事件中樞連接字串](/azure/event-hubs/event-hubs-get-connection-string)。</span><span class="sxs-lookup"><span data-stu-id="829bc-114">For instructions, see [Get an Event Hubs connection string](/azure/event-hubs/event-hubs-get-connection-string).</span></span>
2. <span data-ttu-id="829bc-115">在您的程式碼中使用命名空間中的詳細資料來設定下列設定，以開始從適用于 Kafka 的事件中樞讀取：</span><span class="sxs-lookup"><span data-stu-id="829bc-115">Set the following configurations with details from your namespace in your code to start reading from Event Hubs for Kafka:</span></span>
    1. <span data-ttu-id="829bc-116">更新應用程式中的 **BOOTSTRAP_SERVERS** 和 **EH_SASL** ，如下所示：</span><span class="sxs-lookup"><span data-stu-id="829bc-116">Update **BOOTSTRAP_SERVERS** and **EH_SASL** in your application like so:</span></span>

    ```csharp
    string BOOTSTRAP_SERVERS = "hostname:9093"; // 9093 is the port used to communicate with Event Hubs, see [troubleshooting guide](https://docs.microsoft.com/azure/event-hubs/troubleshooting-guide)
    string EH_SASL = "org.apache.kafka.common.security.plain.PlainLoginModule required username=\"$ConnectionString\" password=\"<CONNECTION_STRING>\";"; // Connection string obtained from Step 1
    ```

## <a name="read-from-azure-event-hub-stream"></a><span data-ttu-id="829bc-117">從 Azure 事件中樞串流讀取</span><span class="sxs-lookup"><span data-stu-id="829bc-117">Read from Azure Event Hub stream</span></span>

<span data-ttu-id="829bc-118">您現在可以開始使用事件中樞進行串流處理，就像使用 Kafka 一樣。</span><span class="sxs-lookup"><span data-stu-id="829bc-118">You can now start streaming with Event Hubs as you would with Kafka.</span></span> <span data-ttu-id="829bc-119">範例程式碼如下所示：</span><span class="sxs-lookup"><span data-stu-id="829bc-119">Sample code as shown below:</span></span>

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

## <a name="write-to-azure-event-hub-stream"></a><span data-ttu-id="829bc-120">寫入至 Azure 事件中樞串流</span><span class="sxs-lookup"><span data-stu-id="829bc-120">Write to Azure Event Hub stream</span></span>

<span data-ttu-id="829bc-121">您也可以用相同的方式寫入事件中樞，如下所示：</span><span class="sxs-lookup"><span data-stu-id="829bc-121">You can also write to Event Hubs in the same way, as shown below:</span></span>

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

## <a name="run-your-application"></a><span data-ttu-id="829bc-122">執行您的應用程式</span><span class="sxs-lookup"><span data-stu-id="829bc-122">Run your application</span></span>

<span data-ttu-id="829bc-123">若要執行 Apache Spark 應用程式的 .NET，請在 `spark-sql-kafka-0-10` Spark 專案中將模組定義為組建定義的一部分，並 `libraryDependency` 在 `build.sbt` sbt 專案中使用。</span><span class="sxs-lookup"><span data-stu-id="829bc-123">In order to run your .NET for Apache Spark application, define the `spark-sql-kafka-0-10` module as part of the build definition in your Spark project, using `libraryDependency` in `build.sbt` for sbt projects.</span></span> <span data-ttu-id="829bc-124">針對 (或) 這類 Spark 環境 `spark-submit` `spark-shell` ，請使用 `--packages` 命令列選項，如下所示：</span><span class="sxs-lookup"><span data-stu-id="829bc-124">For Spark environments such as `spark-submit` (or `spark-shell`), use the `--packages` command-line option like so:</span></span>

```bash
spark-shell --packages org.apache.spark:spark-sql-kafka-0-10_2.12:2.4.5
```

> [!NOTE]
> <span data-ttu-id="829bc-125">請務必根據執行中的 Spark 版本包含套件版本。</span><span class="sxs-lookup"><span data-stu-id="829bc-125">Make sure to include the package version in accordance with the version of Spark being run.</span></span>
