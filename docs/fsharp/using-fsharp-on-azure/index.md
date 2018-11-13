---
title: 在 Azure 上使用 F#
description: 若要使用 Azure 服務搭配 F# 指南
author: sylvanc
ms.date: 09/22/2016
ms.openlocfilehash: 1fbb85a07fc057c1b89a4c4a1ad356066cebf2b8
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "50201500"
---
# <a name="using-f-on-azure"></a><span data-ttu-id="e0a56-103">在 Azure 上使用 F#</span><span class="sxs-lookup"><span data-stu-id="e0a56-103">Using F# on Azure</span></span>

<span data-ttu-id="e0a56-104">F# 是一種優秀的雲端程式設計語言，經常用來撰寫 Web 應用程式、雲端服務、雲端託管微服務，並用於可調整的資料處理。</span><span class="sxs-lookup"><span data-stu-id="e0a56-104">F# is a superb language for cloud programming and is frequently used to write web applications, cloud services, cloud-hosted microservices, and for scalable data processing.</span></span>

<span data-ttu-id="e0a56-105">在下列各節中，您可以找到如何搭配 F# 使用各種 Azure 服務的資源。</span><span class="sxs-lookup"><span data-stu-id="e0a56-105">In the following sections, you will find resources on how to use a range of Azure services with F#.</span></span>

> [!NOTE]
> <span data-ttu-id="e0a56-106">若本文件集中未包含特定的 Azure 服務，請參閱 Azure Functions 或 .NET 文件以找出該服務。</span><span class="sxs-lookup"><span data-stu-id="e0a56-106">If a particular Azure service isn't in this documentation set, please consult either the Azure Functions or .NET documentation for that service.</span></span> <span data-ttu-id="e0a56-107">某些 Azure 服務與語言無關，不需要任何特定語言的文件，因此未在此處列出。</span><span class="sxs-lookup"><span data-stu-id="e0a56-107">Some Azure services are language-independent and require no language-specific documentation and are not listed here.</span></span>

## <a name="using-azure-virtual-machines-with-f"></a><span data-ttu-id="e0a56-108">使用 Azure 虛擬機器搭配 F#</span><span class="sxs-lookup"><span data-stu-id="e0a56-108">Using Azure Virtual Machines with F#</span></span> #

<span data-ttu-id="e0a56-109">Azure 支援各種不同的虛擬機器 (VM) 組態，請參閱 [Linux 和 Azure 虛擬機器](https://azure.microsoft.com/services/virtual-machines/)。</span><span class="sxs-lookup"><span data-stu-id="e0a56-109">Azure supports a wide range of virtual machine (VM) configurations, see [Linux and Azure Virtual Machines](https://azure.microsoft.com/services/virtual-machines/).</span></span>

<span data-ttu-id="e0a56-110">若要在虛擬機器上安裝 F# 以執行、編譯及/或處理指令碼，請參閱 [Using F# on Linux](https://fsharp.org/use/linux) (在 Linux 上使用 F#) 和 [Using F# on Windows](https://fsharp.org/use/windows) (在 Windows 上使用 F#)。</span><span class="sxs-lookup"><span data-stu-id="e0a56-110">To install F# on a virtual machine for execution, compilation and/or scripting see [Using F# on Linux](https://fsharp.org/use/linux) and [Using F# on Windows](https://fsharp.org/use/windows).</span></span>


## <a name="using-azure-functions-with-f"></a><span data-ttu-id="e0a56-111">使用 F# 搭配使用 Azure Functions</span><span class="sxs-lookup"><span data-stu-id="e0a56-111">Using Azure Functions with F#</span></span> #

<span data-ttu-id="e0a56-112">[Azure Functions](https://azure.microsoft.com/services/functions/) 是用來在雲端中輕鬆執行少量程式碼片段或「函式」的解決方案。</span><span class="sxs-lookup"><span data-stu-id="e0a56-112">[Azure Functions](https://azure.microsoft.com/services/functions/) is a solution for easily running small pieces of code, or "functions," in the cloud.</span></span> <span data-ttu-id="e0a56-113">您只需撰寫解決問題所需的程式碼，而不必擔心用來執行程式碼的整個應用程式或基礎結構。</span><span class="sxs-lookup"><span data-stu-id="e0a56-113">You can write just the code you need for the problem at hand, without worrying about a whole application or the infrastructure to run it.</span></span> <span data-ttu-id="e0a56-114">您的函式會連接到 Azure 儲存體和其他雲端託管資源中的事件。</span><span class="sxs-lookup"><span data-stu-id="e0a56-114">Your functions are connected to events in Azure storage and other cloud-hosted resources.</span></span> <span data-ttu-id="e0a56-115">資料則透過函式引數流入您的 F# 函式。</span><span class="sxs-lookup"><span data-stu-id="e0a56-115">Data flows into your F# functions via function arguments.</span></span> <span data-ttu-id="e0a56-116">您可以使用選擇的開發語言，信任 Azure 以視需要進行調整。</span><span class="sxs-lookup"><span data-stu-id="e0a56-116">You can use your development language of choice, trusting Azure to scale as needed.</span></span>

<span data-ttu-id="e0a56-117">Azure Functions 支援 F# 作為第一級語言，可以在有效率、易於反應且可調整的情況下執行 F# 程式碼。</span><span class="sxs-lookup"><span data-stu-id="e0a56-117">Azure Functions support F# as a first-class language with efficient, reactive, scalable execution of F# code.</span></span> <span data-ttu-id="e0a56-118">如需如何使用 F# 搭配 Azure Functions 的參考文件，請參閱 [Azure Functions F# 開發人員參考](/azure/azure-functions/functions-reference-fsharp)。</span><span class="sxs-lookup"><span data-stu-id="e0a56-118">See the [Azure Functions F# Developer Reference](/azure/azure-functions/functions-reference-fsharp) for reference documentation on how to use F# with Azure Functions.</span></span>

<span data-ttu-id="e0a56-119">使用 Azure Functions 和 F# 的其他資源：</span><span class="sxs-lookup"><span data-stu-id="e0a56-119">Other resources for using Azure Functions and F#:</span></span>

* <span data-ttu-id="e0a56-120">[Scale Up Azure Functions in F# Using Suave](https://blog.tamizhvendan.in/blog/2016/09/19/scale-up-azure-functions-in-f-number-using-suave/) (使用 Suave 擴增 F# Azure Functions)</span><span class="sxs-lookup"><span data-stu-id="e0a56-120">[Scale Up Azure Functions in F# Using Suave](https://blog.tamizhvendan.in/blog/2016/09/19/scale-up-azure-functions-in-f-number-using-suave/)</span></span>
* <span data-ttu-id="e0a56-121">[How to create Azure function in F#](https://mnie.github.io/2016-09-08-AzureFunctions/) (如何使用 F# 建立 Azure Function)</span><span class="sxs-lookup"><span data-stu-id="e0a56-121">[How to create Azure function in F#](https://mnie.github.io/2016-09-08-AzureFunctions/)</span></span>
* [<span data-ttu-id="e0a56-122">使用 Azure Functions 使用 Azure 的型別提供者</span><span class="sxs-lookup"><span data-stu-id="e0a56-122">Using the Azure Type Provider with Azure Functions</span></span>](https://compositional-it.com/blog/2017/08-30-using-the-azure-type-provider-with-azure-functions/index.html)

## <a name="using-azure-storage-with-f"></a><span data-ttu-id="e0a56-123">使用 Azure 儲存體搭配 F#</span><span class="sxs-lookup"><span data-stu-id="e0a56-123">Using Azure Storage with F#</span></span> #

<span data-ttu-id="e0a56-124">Azure 儲存體是新式應用程式的儲存體服務基礎層，這些應用程式依賴持久性、可用性和延展性來符合客戶的需求。</span><span class="sxs-lookup"><span data-stu-id="e0a56-124">Azure Storage is a base layer of storage services for modern applications that rely on durability, availability, and scalability to meet the needs of customers.</span></span> <span data-ttu-id="e0a56-125">F#程式可直接與 Azure 儲存體服務，使用下列文章中所述的技巧互動。</span><span class="sxs-lookup"><span data-stu-id="e0a56-125">F# programs can interact directly with Azure storage services, using the techniques described in the following articles.</span></span>

* [<span data-ttu-id="e0a56-126">開始使用 F# 來使用 Azure Blob 儲存體</span><span class="sxs-lookup"><span data-stu-id="e0a56-126">Get started with Azure Blob storage using F#</span></span>](blob-storage.md)
* [<span data-ttu-id="e0a56-127">開始使用 F# 來使用 Azure 檔案儲存體</span><span class="sxs-lookup"><span data-stu-id="e0a56-127">Get started with Azure File storage using F#</span></span>](file-storage.md)
* [<span data-ttu-id="e0a56-128">開始使用 F# 來使用 Azure 佇列儲存體</span><span class="sxs-lookup"><span data-stu-id="e0a56-128">Get started with Azure Queue storage using F#</span></span>](queue-storage.md)
* [<span data-ttu-id="e0a56-129">開始使用 F# 來使用 Azure 資料表儲存體</span><span class="sxs-lookup"><span data-stu-id="e0a56-129">Get started with Azure Table storage using F#</span></span>](table-storage.md)

<span data-ttu-id="e0a56-130">Azure 儲存體也可以透過宣告式組態 (而不是明確的 API 呼叫) 與 Azure Functions 一起使用。</span><span class="sxs-lookup"><span data-stu-id="e0a56-130">Azure Storage can also be used in conjunction with Azure Functions through declarative configuration rather than explicit API calls.</span></span> <span data-ttu-id="e0a56-131">請參閱包含 F# 範例的 [Azure 儲存體的 Azure Functions 觸發程序和繫結](/azure/azure-functions/functions-bindings-storage)。</span><span class="sxs-lookup"><span data-stu-id="e0a56-131">See [Azure Functions triggers and bindings for Azure Storage](/azure/azure-functions/functions-bindings-storage) which includes F# examples.</span></span>

## <a name="using-azure-app-service-with-f"></a><span data-ttu-id="e0a56-132">使用 Azure App Service 搭配 F#</span><span class="sxs-lookup"><span data-stu-id="e0a56-132">Using Azure App Service with F#</span></span> #

<span data-ttu-id="e0a56-133">[Azure App Service](https://azure.microsoft.com/services/app-service/) 是一種雲端平台，用來建置功能強大的 Web 和行動應用程式，這些應用程式可在任何地方 (雲端或內部部署) 連接到資料。</span><span class="sxs-lookup"><span data-stu-id="e0a56-133">[Azure App Service](https://azure.microsoft.com/services/app-service/) is a cloud platform to build powerful web and mobile apps that connect to data anywhere, in the cloud or on-premises.</span></span>

* <span data-ttu-id="e0a56-134">[F# Azure Web API example](https://github.com/fsprojects/azure-webapi-example) (F# Azure Web API 範例)</span><span class="sxs-lookup"><span data-stu-id="e0a56-134">[F# Azure Web API example](https://github.com/fsprojects/azure-webapi-example)</span></span>
* <span data-ttu-id="e0a56-135">[Hosting F# in a web application on Azure](https://github.com/isaacabraham/fsharp-demonstrator) (在 Azure 的 Web 應用程式中裝載 F#)</span><span class="sxs-lookup"><span data-stu-id="e0a56-135">[Hosting F# in a web application on Azure](https://github.com/isaacabraham/fsharp-demonstrator)</span></span>

## <a name="using-apache-spark-with-f-with-azure-hdinsight"></a><span data-ttu-id="e0a56-136">在 Azure HDInsight 上使用 Apache Spark 搭配 F#</span><span class="sxs-lookup"><span data-stu-id="e0a56-136">Using Apache Spark with F# with Azure HDInsight</span></span>

<span data-ttu-id="e0a56-137">[Apache Spark for Azure HDInsight](https://azure.microsoft.com/services/hdinsight/apache-spark/) 是一種開放原始碼處理架構，可執行大規模的資料分析應用程式。</span><span class="sxs-lookup"><span data-stu-id="e0a56-137">[Apache Spark for Azure HDInsight](https://azure.microsoft.com/services/hdinsight/apache-spark/) is an open source processing framework that runs large-scale data analytics applications.</span></span> <span data-ttu-id="e0a56-138">Azure 可讓 Apache Spark 部署變得輕鬆又具成本效益。</span><span class="sxs-lookup"><span data-stu-id="e0a56-138">Azure makes Apache Spark easy and cost effective to deploy.</span></span> <span data-ttu-id="e0a56-139">請使用 [Mobius](https://github.com/Microsoft/Mobius)其為適用於 Spark 的 .NET API 來開發您的 F# Spark 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e0a56-139">Develop your Spark application in F# using [Mobius](https://github.com/Microsoft/Mobius), a .NET API for Spark.</span></span>

* <span data-ttu-id="e0a56-140">[Implementing Spark Apps in F# using Mobius](https://github.com/Microsoft/Mobius/blob/master/notes/spark-fsharp-mobius.md) (使用 Mobius 實作 F# Spark 應用程式)</span><span class="sxs-lookup"><span data-stu-id="e0a56-140">[Implementing Spark Apps in F# using Mobius](https://github.com/Microsoft/Mobius/blob/master/notes/spark-fsharp-mobius.md)</span></span>
* <span data-ttu-id="e0a56-141">[Example F# Spark Apps using Mobius](https://github.com/Microsoft/Mobius/tree/master/examples/fsharp) (使用 Mobius 的 F# Spark 應用程式範例)</span><span class="sxs-lookup"><span data-stu-id="e0a56-141">[Example F# Spark Apps using Mobius](https://github.com/Microsoft/Mobius/tree/master/examples/fsharp)</span></span>

## <a name="using-azure-cosmos-db-with-f"></a><span data-ttu-id="e0a56-142">使用 Azure Cosmos DB 搭配 F#</span><span class="sxs-lookup"><span data-stu-id="e0a56-142">Using Azure Cosmos DB with F#</span></span> #

<span data-ttu-id="e0a56-143">[Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db)是高度可用、 全域散發的應用程式的 NoSQL 服務。</span><span class="sxs-lookup"><span data-stu-id="e0a56-143">[Azure Cosmos DB](https://azure.microsoft.com/services/cosmos-db) is a NoSQL service for highly available, globally distributed apps.</span></span>

<span data-ttu-id="e0a56-144">Azure Cosmos DB 可以兩種方式與 F# 搭配使用：</span><span class="sxs-lookup"><span data-stu-id="e0a56-144">Azure Cosmos DB can be used with F# in two ways:</span></span>

1. <span data-ttu-id="e0a56-145">透過 F# Azure Functions 建立回應或導致變更 Azure Cosmos DB 集合。</span><span class="sxs-lookup"><span data-stu-id="e0a56-145">Through the creation of F# Azure Functions which react to or cause changes to Azure Cosmos DB collections.</span></span> <span data-ttu-id="e0a56-146">請參閱[適用於 Azure Functions 的 Azure Cosmos DB 繫結](/azure/azure-functions/functions-bindings-cosmosdb)，或</span><span class="sxs-lookup"><span data-stu-id="e0a56-146">See [Azure Cosmos DB bindings for Azure Functions](/azure/azure-functions/functions-bindings-cosmosdb), or</span></span>
2. <span data-ttu-id="e0a56-147">藉由使用[Azure Cosmos DB.NET SDK for SQL API](/azure/cosmos-db/sql-api-sdk-dotnet)。</span><span class="sxs-lookup"><span data-stu-id="e0a56-147">By using the [Azure Cosmos DB .NET SDK for SQL API](/azure/cosmos-db/sql-api-sdk-dotnet).</span></span> <span data-ttu-id="e0a56-148">相關的範例是以 C#。</span><span class="sxs-lookup"><span data-stu-id="e0a56-148">The related samples are in C#.</span></span>

## <a name="using-azure-event-hubs-with-f"></a><span data-ttu-id="e0a56-149">使用 Azure 事件中樞搭配 F#</span><span class="sxs-lookup"><span data-stu-id="e0a56-149">Using Azure Event Hubs with F#</span></span> #

<span data-ttu-id="e0a56-150">[Azure 事件中樞](https://azure.microsoft.com/services/event-hubs/)可從網站、應用程式和裝置提供雲端等級的遙測數據。</span><span class="sxs-lookup"><span data-stu-id="e0a56-150">[Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/) provide cloud-scale telemetry ingestion from websites, apps, and devices.</span></span>

<span data-ttu-id="e0a56-151">Azure 事件中樞可以透過下列兩種方式與 F# 搭配使用︰</span><span class="sxs-lookup"><span data-stu-id="e0a56-151">Azure Event Hubs can be used with F# in two ways:</span></span>

1. <span data-ttu-id="e0a56-152">透過建立事件所觸發的 F# Azure Functions。</span><span class="sxs-lookup"><span data-stu-id="e0a56-152">Through the creation of F# Azure Functions which are triggered by events.</span></span> <span data-ttu-id="e0a56-153">請參閱 [Azure Function 事件中樞的觸發程序](/azure/azure-functions/functions-bindings-event-hubs)，或</span><span class="sxs-lookup"><span data-stu-id="e0a56-153">See [Azure Function triggers for Event Hubs](/azure/azure-functions/functions-bindings-event-hubs), or</span></span>
2. <span data-ttu-id="e0a56-154">透過使用 [.NET SDK for Azure](/azure/event-hubs/event-hubs-csharp-ephcs-getstarted)。</span><span class="sxs-lookup"><span data-stu-id="e0a56-154">By using the [.NET SDK for Azure](/azure/event-hubs/event-hubs-csharp-ephcs-getstarted).</span></span> <span data-ttu-id="e0a56-155">請注意，這些範例是根據 C#。</span><span class="sxs-lookup"><span data-stu-id="e0a56-155">Note these examples are in C#.</span></span>

## <a name="using-azure-notification-hubs-with-f"></a><span data-ttu-id="e0a56-156">使用 Azure 通知中樞搭配 F#</span><span class="sxs-lookup"><span data-stu-id="e0a56-156">Using Azure Notification Hubs with F#</span></span> #

<span data-ttu-id="e0a56-157">[Azure 通知中樞](/azure/notification-hubs/)是一種多平台、向外延展的推播基礎結構，可讓您將任何後端 (雲端或內部部署) 中的行動推播通知傳送到任何行動平台。</span><span class="sxs-lookup"><span data-stu-id="e0a56-157">[Azure Notification Hubs](/azure/notification-hubs/) are multiplatform, scaled-out push infrastructure that enable you to send mobile push notifications from any backend (in the cloud or on-premises) to any mobile platform.</span></span>

<span data-ttu-id="e0a56-158">Azure 通知中樞可以透過下列兩種方式與 F# 搭配使用︰</span><span class="sxs-lookup"><span data-stu-id="e0a56-158">Azure Notification Hubs can be used with F# in two ways:</span></span>

1. <span data-ttu-id="e0a56-159">透過建立可將結果傳送到通知中樞的 F# Azure Functions。</span><span class="sxs-lookup"><span data-stu-id="e0a56-159">Through the creation of F# Azure Functions which send results to a notification hub.</span></span> <span data-ttu-id="e0a56-160">請參閱 [Azure Function 通知中樞的輸出觸發程序](/azure/azure-functions/functions-bindings-notification-hubs)，或</span><span class="sxs-lookup"><span data-stu-id="e0a56-160">See [Azure Function output triggers for Notification Hubs](/azure/azure-functions/functions-bindings-notification-hubs), or</span></span>
2. <span data-ttu-id="e0a56-161">透過使用 [.NET SDK for Azure](https://blogs.msdn.microsoft.com/azuremobile/2014/04/08/push-notifications-using-notification-hub-and-net-backend/)。</span><span class="sxs-lookup"><span data-stu-id="e0a56-161">By using the [.NET SDK for Azure](https://blogs.msdn.microsoft.com/azuremobile/2014/04/08/push-notifications-using-notification-hub-and-net-backend/).</span></span> <span data-ttu-id="e0a56-162">請注意，這些範例是根據 C#。</span><span class="sxs-lookup"><span data-stu-id="e0a56-162">Note these examples are in C#.</span></span>


## <a name="implementing-webhooks-on-azure-with-f"></a><span data-ttu-id="e0a56-163">Azure 上使用 F# 實作 Webhook</span><span class="sxs-lookup"><span data-stu-id="e0a56-163">Implementing WebHooks on Azure with F#</span></span> #

<span data-ttu-id="e0a56-164">[Webhook](https://en.wikipedia.org/wiki/Webhook) 是透過 Web 要求觸發的回呼。</span><span class="sxs-lookup"><span data-stu-id="e0a56-164">A [Webhook](https://en.wikipedia.org/wiki/Webhook) is a callback triggered via a web request.</span></span> <span data-ttu-id="e0a56-165">GitHub 等網站會使用 Webhook 以訊號通知事件。</span><span class="sxs-lookup"><span data-stu-id="e0a56-165">Webhooks are used by sites such as GitHub to signal events.</span></span> 

<span data-ttu-id="e0a56-166">您可以使用 F# 實作 Webhook，並透過[含有 Webhook 繫結的 F# Azure Function](/azure/azure-functions/functions-bindings-http-webhook) 在 Azure 上裝載 Webhook。</span><span class="sxs-lookup"><span data-stu-id="e0a56-166">Webhooks can be implemented in F# and hosted on Azure via an [Azure Function in F# with a Webhook Binding](/azure/azure-functions/functions-bindings-http-webhook).</span></span>

## <a name="using-webjobs-with-f"></a><span data-ttu-id="e0a56-167">使用 Webjobs 搭配 F#</span><span class="sxs-lookup"><span data-stu-id="e0a56-167">Using Webjobs with F#</span></span> #

<span data-ttu-id="e0a56-168">[Webjobs](/azure/app-service-web/web-sites-create-web-jobs) 是您可以使用下列三種方式在 App Service Web 應用程式中執行的程式：依需求、連續或根據排程。</span><span class="sxs-lookup"><span data-stu-id="e0a56-168">[Webjobs](/azure/app-service-web/web-sites-create-web-jobs) are programs you can run in your App Service web app in three ways: on demand, continuously, or on a schedule.</span></span>

<span data-ttu-id="e0a56-169">[Example F# Webjob](https://github.com/jrr/webjob-project-examples) (F# Webjob 範例)</span><span class="sxs-lookup"><span data-stu-id="e0a56-169">[Example F# Webjob](https://github.com/jrr/webjob-project-examples)</span></span>

## <a name="implementing-timers-on-azure-with-f"></a><span data-ttu-id="e0a56-170">Azure 上使用 F# 實作計時器</span><span class="sxs-lookup"><span data-stu-id="e0a56-170">Implementing Timers on Azure with F#</span></span> #

<span data-ttu-id="e0a56-171">計時器會根據排程，觸發一次或重複觸發呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="e0a56-171">Timer triggers call functions based on a schedule, one time or recurring.</span></span>

<span data-ttu-id="e0a56-172">您可以使用 F# 實作計時器，並透過[含有計時器觸發程序的 F# Azure Function](/azure/azure-functions/functions-bindings-timer) 在 Azure 上裝載計時器。</span><span class="sxs-lookup"><span data-stu-id="e0a56-172">Timers can be implemented in F# and hosted on Azure via an [Azure Function in F# with a Timer Trigger](/azure/azure-functions/functions-bindings-timer).</span></span>

## <a name="deploying-and-managing-azure-resources-with-f-scripts"></a><span data-ttu-id="e0a56-173">使用 F# 指令碼部署和管理 Azure 資源</span><span class="sxs-lookup"><span data-stu-id="e0a56-173">Deploying and Managing Azure Resources with F# Scripts</span></span> #

<span data-ttu-id="e0a56-174">Azure VM 可能會使用 Microsoft.Azure.Management 套件和 API，透過 F# 指令碼以程式設計方式部署和管理。</span><span class="sxs-lookup"><span data-stu-id="e0a56-174">Azure VMs may be programmatically deployed and managed from F# scripts by using the Microsoft.Azure.Management packages and APIs.</span></span> <span data-ttu-id="e0a56-175">例如，請參閱[開始使用 .NET 的管理程式庫](https://msdn.microsoft.com/library/dn722415.aspx)和[使用 Azure 資源管理員](/azure/azure-resource-manager/resource-manager-deployment-model)。</span><span class="sxs-lookup"><span data-stu-id="e0a56-175">For example, see [Get Started with the Management Libraries for .NET](https://msdn.microsoft.com/library/dn722415.aspx) and [Using Azure Resource Manager](/azure/azure-resource-manager/resource-manager-deployment-model).</span></span>

<span data-ttu-id="e0a56-176">同樣地，其他 Azure 資源也可以使用相同的元件，透過 F# 指令碼進行部署和管理。</span><span class="sxs-lookup"><span data-stu-id="e0a56-176">Likewise, other Azure resources may also be deployed and managed from F# scripts using the same components.</span></span> <span data-ttu-id="e0a56-177">例如，您可以建立儲存體帳戶、 部署 Azure 雲端服務、 建立 Azure Cosmos DB 執行個體和透過 F# 指令碼，以程式設計方式管理 Azure 通知中樞。</span><span class="sxs-lookup"><span data-stu-id="e0a56-177">For example, you can create storage accounts, deploy Azure Cloud Services, create Azure Cosmos DB instances and manage Azure Notifcation Hubs programmatically from F# scripts.</span></span>

<span data-ttu-id="e0a56-178">通常不需要使用 F# 指令碼來部署和管理資源。</span><span class="sxs-lookup"><span data-stu-id="e0a56-178">Using F# scripts to deploy and manage resources is not normally necessary.</span></span> <span data-ttu-id="e0a56-179">例如，Azure 資源也能夠透過可進行參數化的 JSON 範本描述加以部署。</span><span class="sxs-lookup"><span data-stu-id="e0a56-179">For example, Azure resources may also be deployed directy from JSON template descriptions, which can be parameterized.</span></span> <span data-ttu-id="e0a56-180">請參閱包含 [Azure 快速入門範本](https://azure.microsoft.com/resources/templates/)等範例的 [Azure 資源管理員範本](/azure/azure-resource-manager/resource-manager-template-best-practices)。</span><span class="sxs-lookup"><span data-stu-id="e0a56-180">See [Azure Resource Manager Templates](/azure/azure-resource-manager/resource-manager-template-best-practices) including examples such as the [Azure Quickstart Templates](https://azure.microsoft.com/resources/templates/).</span></span>

## <a name="other-resources"></a><span data-ttu-id="e0a56-181">其他資源</span><span class="sxs-lookup"><span data-stu-id="e0a56-181">Other resources</span></span>

* [<span data-ttu-id="e0a56-182">所有 Azure 服務的完整文件</span><span class="sxs-lookup"><span data-stu-id="e0a56-182">Full documentation on all Azure services</span></span>](/azure/)
