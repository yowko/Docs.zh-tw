---
title: 在 Azure 上使用 F#
description: 使用 Azure 服務搭配 F 的指南#
author: sylvanc
ms.date: 07/29/2020
ms.custom: devx-track-fsharp
ms.openlocfilehash: 16599aa48776acee05edf8201cdd148a87507cdb
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/27/2021
ms.locfileid: "98899403"
---
# <a name="using-f-on-azure"></a>在 Azure 上使用 F#

F# 是一種優秀的雲端程式設計語言，經常用來撰寫 Web 應用程式、雲端服務、雲端託管微服務，並用於可調整的資料處理。

在下列各節中，您可以找到如何搭配 F# 使用各種 Azure 服務的資源。

> [!NOTE]
> 若本文件集中未包含特定的 Azure 服務，請參閱 Azure Functions 或 .NET 文件以找出該服務。 某些 Azure 服務與語言無關，不需要任何特定語言的文件，因此未在此處列出。

## <a name="using-azure-virtual-machines-with-f"></a>使用 Azure 虛擬機器搭配 F#\#

Azure 支援各種不同的虛擬機器 (VM) 組態，請參閱 [Linux 和 Azure 虛擬機器](https://azure.microsoft.com/services/virtual-machines/)。

若要在虛擬機器上安裝 F# 以執行、編譯及/或處理指令碼，請參閱 [Using F# on Linux](https://fsharp.org/use/linux) (在 Linux 上使用 F#) 和 [Using F# on Windows](https://fsharp.org/use/windows) (在 Windows 上使用 F#)。

## <a name="using-azure-functions-with-f"></a>使用 Azure Functions 搭配 F#\#

[Azure Functions](https://azure.microsoft.com/services/functions/) 是在雲端輕鬆執行一小段程式碼或「函式」的解決方案。 您可以只撰寫處理手邊問題所需的程式碼，而不需擔心要執行它的整個應用程式或基礎結構。 您的函式會連接到 Azure 儲存體和其他雲端託管資源中的事件。 資料則透過函式引數流入您的 F# 函式。 您可以使用選擇的開發語言，信任 Azure 以視需要進行調整。

Azure Functions 支援 F# 作為第一級語言，可以在有效率、易於反應且可調整的情況下執行 F# 程式碼。 如需如何使用 F# 搭配 Azure Functions 的參考文件，請參閱 [Azure Functions F# 開發人員參考](/azure/azure-functions/functions-reference-fsharp)。

使用 Azure Functions 和 F# 的其他資源：

* [Scale Up Azure Functions in F# Using Suave](https://blog.tamizhvendan.in/blog/2016/09/19/scale-up-azure-functions-in-f-number-using-suave/) (使用 Suave 擴增 F# Azure Functions)
* [How to create Azure function in F#](https://www.mnie.me/azurefunctions) (如何使用 F# 建立 Azure Function)
* [搭配 Azure Functions 使用 Azure 型別提供者](https://compositional-it.com/blog/2017/08-30-using-the-azure-type-provider-with-azure-functions/index.html)

## <a name="using-azure-storage-with-f"></a>使用 Azure 儲存體搭配 F#\#

Azure 儲存體是新式應用程式的儲存體服務基礎層，這些應用程式依賴持久性、可用性和延展性來符合客戶的需求。 您可以使用下列文章中所述的技術，直接與 Azure 儲存體服務互動 F # 程式。

* [以 F 開始使用 Azure Blob 儲存體#](blob-storage.md)
* [以 F 開始使用 Azure 檔案儲存體#](file-storage.md)
* [以 F 開始使用 Azure 佇列儲存體#](queue-storage.md)
* [以 F 開始使用 Azure 資料表儲存體#](table-storage.md)

Azure 儲存體也可以透過宣告式組態 (而不是明確的 API 呼叫) 與 Azure Functions 一起使用。 請參閱包含 F# 範例的 [Azure 儲存體的 Azure Functions 觸發程序和繫結](/azure/azure-functions/functions-bindings-storage)。

## <a name="using-azure-app-service-with-f"></a>使用 Azure App Service 搭配 F#\#

[Azure App Service](https://azure.microsoft.com/services/app-service/) 是一種雲端平台，用來建置功能強大的 Web 和行動應用程式，這些應用程式可在任何地方 (雲端或內部部署) 連接到資料。

* [F# Azure Web API example](https://github.com/fsprojects/azure-webapi-example) (F# Azure Web API 範例)
* [Hosting F# in a web application on Azure](https://github.com/isaacabraham/fsharp-demonstrator) (在 Azure 的 Web 應用程式中裝載 F#)

## <a name="using-apache-spark-with-f-on-azure-hdinsight-or-azure-databricks"></a>在 Azure HDInsight 或 Azure Databricks 上搭配 F # 使用 Apache Spark

[Apache Spark for Azure HDInsight](/azure/hdinsight/spark/apache-spark-overview) 是一種開放原始碼處理架構，可執行大規模的資料分析應用程式。 [Azure Databricks](/azure/databricks/scenarios/what-is-azure-databricks) 是一個針對 Microsoft Azure 雲端服務平台進行最佳化的 Apache Spark 分析平台。 Azure 可讓 Apache Spark 部署變得輕鬆又具成本效益。 使用 [.net 進行 Apache Spark](../../spark/what-is-apache-spark-dotnet.md)的 F # 開發 Spark 應用程式，這是一組適用于 Apache Spark 的 .net 系結。

* [適用于 Apache Spark F # 範例的 .NET](https://github.com/dotnet/spark/tree/master/examples/Microsoft.Spark.FSharp.Examples)
* [在 Azure HDInsight 中安裝 .NET Interactive Jupyter 筆記本](../../spark/how-to-guides/hdinsight-notebook-installation.md)
* [將 Apache Spark 作業提交至 Azure HDInsight](../../spark/how-to-guides/hdinsight-deploy-methods.md)
* [將 Apache Spark 作業提交至 Azure Databricks](../../spark/how-to-guides/databricks-deploy-methods.md)

## <a name="using-azure-cosmos-db-with-f"></a>使用 Azure Cosmos DB 搭配 F\#

[Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db) 是適用于高可用性、全球散發之應用程式的 NoSQL 服務。

Azure Cosmos DB 可以透過兩種方式與 F # 搭配使用：

1. 透過建立 F # Azure Functions，這會對 Azure Cosmos DB 集合進行回應或變更。 請參閱 [Azure Functions 的 Azure Cosmos DB](/azure/azure-functions/functions-bindings-cosmosdb)系結，或
2. 使用 [Azure Cosmos DB .NET SDK FOR SQL API](/azure/cosmos-db/sql-api-sdk-dotnet)。 相關的範例是以 c # 撰寫。

## <a name="using-azure-event-hubs-with-f"></a>使用 Azure 事件中樞搭配 F#\#

[Azure 事件中樞](https://azure.microsoft.com/services/event-hubs/)可從網站、應用程式和裝置提供雲端等級的遙測數據。

Azure 事件中樞可以透過下列兩種方式與 F# 搭配使用︰

1. 透過建立事件所觸發的 F# Azure Functions。 請參閱 [Azure Function 事件中樞的觸發程序](/azure/azure-functions/functions-bindings-event-hubs)，或
2. 透過使用 [.NET SDK for Azure](/azure/event-hubs/event-hubs-csharp-ephcs-getstarted)。 請注意，這些範例是根據 C#。

## <a name="using-azure-notification-hubs-with-f"></a>使用 Azure 通知中樞搭配 F#\#

[Azure 通知中樞](/azure/notification-hubs/)是一種多平台、向外延展的推播基礎結構，可讓您將任何後端 (雲端或內部部署) 中的行動推播通知傳送到任何行動平台。

Azure 通知中樞可以透過下列兩種方式與 F# 搭配使用︰

1. 透過建立可將結果傳送到通知中樞的 F# Azure Functions。 請參閱 [Azure Function 通知中樞的輸出觸發程序](/azure/azure-functions/functions-bindings-notification-hubs)，或
2. 透過使用 [.NET SDK for Azure](/archive/blogs/azuremobile/push-notifications-using-notification-hub-and-net-backend)。 請注意，這些範例是根據 C#。

## <a name="implementing-webhooks-on-azure-with-f"></a>使用 F# 在 Azure 上實作 Webhook\#

[Webhook](https://en.wikipedia.org/wiki/Webhook) 是透過 Web 要求觸發的回呼。 GitHub 等網站會使用 Webhook 以訊號通知事件。

您可以使用 F# 實作 Webhook，並透過[含有 Webhook 繫結的 F# Azure Function](/azure/azure-functions/functions-bindings-http-webhook) 在 Azure 上裝載 Webhook。

## <a name="using-webjobs-with-f"></a>使用 Webjobs 搭配 F#\#

[Webjobs](/azure/app-service-web/web-sites-create-web-jobs) 是您可以使用下列三種方式在 App Service Web 應用程式中執行的程式：依需求、連續或根據排程。

[Example F# Webjob](https://github.com/jrr/webjob-project-examples) (F# Webjob 範例)

## <a name="implementing-timers-on-azure-with-f"></a>使用 F# 在 Azure 上實作計時器\#

計時器觸發程序會根據排程，以單次或週期性方式呼叫函數。

您可以使用 F# 實作計時器，並透過[含有計時器觸發程序的 F# Azure Function](/azure/azure-functions/functions-bindings-timer) 在 Azure 上裝載計時器。

## <a name="deploying-and-managing-azure-resources-with-f-scripts"></a>使用 F# 指令碼部署和管理 Azure 資源

Azure VM 可能會使用 Microsoft.Azure.Management 套件和 API，透過 F# 指令碼以程式設計方式部署和管理。 例如，請參閱[開始使用 .NET 的管理程式庫](/previous-versions/azure/dn722415(v=azure.100))和[使用 Azure 資源管理員](/azure/azure-resource-manager/resource-manager-deployment-model)。

同樣地，其他 Azure 資源也可以使用相同的元件，透過 F# 指令碼進行部署和管理。 例如，您可以建立儲存體帳戶、部署 Azure 雲端服務、建立 Azure Cosmos DB 實例，並從 F # 腳本以程式設計方式管理 Azure 通知中樞。

通常不需要使用 F# 指令碼來部署和管理資源。 例如，Azure 資源也可以直接從 JSON 範本描述（可參數化）進行部署。 請參閱包含 [Azure 快速入門範本](https://azure.microsoft.com/resources/templates/)等範例的 [Azure 資源管理員範本](/azure/azure-resource-manager/resource-manager-template-best-practices)。

## <a name="other-resources"></a>其他資源

* [所有 Azure 服務的完整文件](/azure/)
