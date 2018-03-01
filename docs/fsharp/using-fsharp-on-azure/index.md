---
title: "在 Azure 上使用 F#"
description: "若要使用 Azure services 和 F # 指南"
keywords: "Azure, 雲端, Visual F#, F#, 函式程式設計, .NET, .NET Core"
author: sylvanc
ms.author: phcart
ms.date: 09/22/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: FAD4D11E-703A-42D4-9F72-893D9E0F569B
ms.openlocfilehash: 8f1d5abe0412ecf72e38c7d76ef44fdc5fd4a0f7
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="using-f-on-azure"></a><span data-ttu-id="d8628-104">在 Azure 上使用 F#</span><span class="sxs-lookup"><span data-stu-id="d8628-104">Using F# on Azure</span></span>

<span data-ttu-id="d8628-105">F# 是一種優秀的雲端程式設計語言，經常用來撰寫 Web 應用程式、雲端服務、雲端託管微服務，並用於可調整的資料處理。</span><span class="sxs-lookup"><span data-stu-id="d8628-105">F# is a superb language for cloud programming and is frequently used to write web applications, cloud services, cloud-hosted microservices, and for scalable data processing.</span></span>

<span data-ttu-id="d8628-106">在下列各節中，您可以找到如何搭配 F# 使用各種 Azure 服務的資源。</span><span class="sxs-lookup"><span data-stu-id="d8628-106">In the following sections, you will find resources on how to use a range of Azure services with F#.</span></span>

> [!NOTE]
> <span data-ttu-id="d8628-107">若本文件集中未包含特定的 Azure 服務，請參閱 Azure Functions 或 .NET 文件以找出該服務。</span><span class="sxs-lookup"><span data-stu-id="d8628-107">If a particular Azure service isn't in this documentation set, please consult either the Azure Functions or .NET documentation for that service.</span></span> <span data-ttu-id="d8628-108">某些 Azure 服務與語言無關，不需要任何特定語言的文件，因此未在此處列出。</span><span class="sxs-lookup"><span data-stu-id="d8628-108">Some Azure services are language-independent and require no language-specific documentation and are not listed here.</span></span>

## <a name="using-azure-virtual-machines-with-f"></a><span data-ttu-id="d8628-109">使用 F # 中使用 Azure 虛擬機器</span><span class="sxs-lookup"><span data-stu-id="d8628-109">Using Azure Virtual Machines with F#</span></span> #

<span data-ttu-id="d8628-110">Azure 支援各種不同的虛擬機器 (VM) 組態，請參閱 [Linux 和 Azure 虛擬機器](https://azure.microsoft.com/services/virtual-machines/)。</span><span class="sxs-lookup"><span data-stu-id="d8628-110">Azure supports a wide range of virtual machine (VM) configurations, see [Linux and Azure Virtual Machines](https://azure.microsoft.com/services/virtual-machines/).</span></span>

<span data-ttu-id="d8628-111">若要在虛擬機器上安裝 F# 以執行、編譯及/或處理指令碼，請參閱 [Using F# on Linux](http://fsharp.org/use/linux) (在 Linux 上使用 F#) 和 [Using F# on Windows](http://fsharp.org/use/windows) (在 Windows 上使用 F#)。</span><span class="sxs-lookup"><span data-stu-id="d8628-111">To install F# on a virtual machine for execution, compilation and/or scripting see [Using F# on Linux](http://fsharp.org/use/linux) and [Using F# on Windows](http://fsharp.org/use/windows).</span></span>


## <a name="using-azure-functions-with-f"></a><span data-ttu-id="d8628-112">F # 搭配使用 Azure 的函數</span><span class="sxs-lookup"><span data-stu-id="d8628-112">Using Azure Functions with F#</span></span> #

<span data-ttu-id="d8628-113">[Azure Functions](https://azure.microsoft.com/services/functions/) 是用來在雲端中輕鬆執行少量程式碼片段或「函式」的解決方案。</span><span class="sxs-lookup"><span data-stu-id="d8628-113">[Azure Functions](https://azure.microsoft.com/services/functions/) is a solution for easily running small pieces of code, or "functions," in the cloud.</span></span> <span data-ttu-id="d8628-114">您只需撰寫解決問題所需的程式碼，而不必擔心用來執行程式碼的整個應用程式或基礎結構。</span><span class="sxs-lookup"><span data-stu-id="d8628-114">You can write just the code you need for the problem at hand, without worrying about a whole application or the infrastructure to run it.</span></span> <span data-ttu-id="d8628-115">您的函式會連接到 Azure 儲存體和其他雲端託管資源中的事件。</span><span class="sxs-lookup"><span data-stu-id="d8628-115">Your functions are connected to events in Azure storage and other cloud-hosted resources.</span></span> <span data-ttu-id="d8628-116">資料則透過函式引數流入您的 F# 函式。</span><span class="sxs-lookup"><span data-stu-id="d8628-116">Data flows into your F# functions via function arguments.</span></span> <span data-ttu-id="d8628-117">您可以使用選擇的開發語言，信任 Azure 以視需要進行調整。</span><span class="sxs-lookup"><span data-stu-id="d8628-117">You can use your development language of choice, trusting Azure to scale as needed.</span></span>

<span data-ttu-id="d8628-118">Azure Functions 支援 F# 作為第一級語言，可以在有效率、易於反應且可調整的情況下執行 F# 程式碼。</span><span class="sxs-lookup"><span data-stu-id="d8628-118">Azure Functions support F# as a first-class language with efficient, reactive, scalable execution of F# code.</span></span> <span data-ttu-id="d8628-119">如需如何使用 F# 搭配 Azure Functions 的參考文件，請參閱 [Azure Functions F# 開發人員參考](/azure/azure-functions/functions-reference-fsharp)。</span><span class="sxs-lookup"><span data-stu-id="d8628-119">See the [Azure Functions F# Developer Reference](/azure/azure-functions/functions-reference-fsharp) for reference documentation on how to use F# with Azure Functions.</span></span>

<span data-ttu-id="d8628-120">使用 Azure Functions 和 F# 的其他資源：</span><span class="sxs-lookup"><span data-stu-id="d8628-120">Other resources for using Azure Functions and F#:</span></span>

* <span data-ttu-id="d8628-121">[Scale Up Azure Functions in F# Using Suave](https://blog.tamizhvendan.in/blog/2016/09/19/scale-up-azure-functions-in-f-number-using-suave/) (使用 Suave 擴增 F# Azure Functions)</span><span class="sxs-lookup"><span data-stu-id="d8628-121">[Scale Up Azure Functions in F# Using Suave](https://blog.tamizhvendan.in/blog/2016/09/19/scale-up-azure-functions-in-f-number-using-suave/)</span></span>
* <span data-ttu-id="d8628-122">[How to create Azure function in F#](https://mnie.github.io/2016-09-08-AzureFunctions/) (如何使用 F# 建立 Azure Function)</span><span class="sxs-lookup"><span data-stu-id="d8628-122">[How to create Azure function in F#](https://mnie.github.io/2016-09-08-AzureFunctions/)</span></span>
* [<span data-ttu-id="d8628-123">使用 Azure 的型別提供者搭配 Azure 的函式</span><span class="sxs-lookup"><span data-stu-id="d8628-123">Using the Azure Type Provider with Azure Functions</span></span>](https://compositional-it.com/blog/2017/08-30-using-the-azure-type-provider-with-azure-functions/index.html)

## <a name="using-azure-storage-with-f"></a><span data-ttu-id="d8628-124">使用 Azure 儲存體與 F #</span><span class="sxs-lookup"><span data-stu-id="d8628-124">Using Azure Storage with F#</span></span> #

<span data-ttu-id="d8628-125">Azure 儲存體是新式應用程式的儲存體服務基礎層，這些應用程式依賴持久性、可用性和延展性來符合客戶的需求。</span><span class="sxs-lookup"><span data-stu-id="d8628-125">Azure Storage is a base layer of storage services for modern applications that rely on durability, availability, and scalability to meet the needs of customers.</span></span> <span data-ttu-id="d8628-126">透過使用下列文章中所描述的技巧，F# 程式可以直接與 Azure 儲存體服務互動。</span><span class="sxs-lookup"><span data-stu-id="d8628-126">F# programs can interact directly with Azure storage services, using the techinques described in the following articles.</span></span>

* [<span data-ttu-id="d8628-127">開始使用 F# 來使用 Azure Blob 儲存體</span><span class="sxs-lookup"><span data-stu-id="d8628-127">Get started with Azure Blob storage using F#</span></span>](blob-storage.md)
* [<span data-ttu-id="d8628-128">開始使用 F# 來使用 Azure 檔案儲存體</span><span class="sxs-lookup"><span data-stu-id="d8628-128">Get started with Azure File storage using F#</span></span>](file-storage.md)
* [<span data-ttu-id="d8628-129">開始使用 F# 來使用 Azure 佇列儲存體</span><span class="sxs-lookup"><span data-stu-id="d8628-129">Get started with Azure Queue storage using F#</span></span>](queue-storage.md)
* [<span data-ttu-id="d8628-130">開始使用 F# 來使用 Azure 資料表儲存體</span><span class="sxs-lookup"><span data-stu-id="d8628-130">Get started with Azure Table storage using F#</span></span>](table-storage.md)

<span data-ttu-id="d8628-131">Azure 儲存體也可以透過宣告式組態 (而不是明確的 API 呼叫) 與 Azure Functions 一起使用。</span><span class="sxs-lookup"><span data-stu-id="d8628-131">Azure Storage can also be used in conjunction with Azure Functions through declarative configuration rather than explicit API calls.</span></span> <span data-ttu-id="d8628-132">請參閱包含 F# 範例的 [Azure 儲存體的 Azure Functions 觸發程序和繫結](/azure/azure-functions/functions-bindings-storage)。</span><span class="sxs-lookup"><span data-stu-id="d8628-132">See [Azure Functions triggers and bindings for Azure Storage](/azure/azure-functions/functions-bindings-storage) which includes F# examples.</span></span>

## <a name="using-azure-app-service-with-f"></a><span data-ttu-id="d8628-133">使用 F # 中使用 Azure App Service</span><span class="sxs-lookup"><span data-stu-id="d8628-133">Using Azure App Service with F#</span></span> #

<span data-ttu-id="d8628-134">[Azure App Service](https://azure.microsoft.com/services/app-service/) 是一種雲端平台，用來建置功能強大的 Web 和行動應用程式，這些應用程式可在任何地方 (雲端或內部部署) 連接到資料。</span><span class="sxs-lookup"><span data-stu-id="d8628-134">[Azure App Service](https://azure.microsoft.com/services/app-service/) is a cloud platform to build powerful web and mobile apps that connect to data anywhere, in the cloud or on-premises.</span></span>

* <span data-ttu-id="d8628-135">[F# Azure Web API example](https://github.com/fsprojects/azure-webapi-example) (F# Azure Web API 範例)</span><span class="sxs-lookup"><span data-stu-id="d8628-135">[F# Azure Web API example](https://github.com/fsprojects/azure-webapi-example)</span></span>
* <span data-ttu-id="d8628-136">[Hosting F# in a web application on Azure](https://github.com/isaacabraham/fsharp-demonstrator) (在 Azure 的 Web 應用程式中裝載 F#)</span><span class="sxs-lookup"><span data-stu-id="d8628-136">[Hosting F# in a web application on Azure](https://github.com/isaacabraham/fsharp-demonstrator)</span></span>

## <a name="using-apache-spark-with-f-with-azure-hdinsight"></a><span data-ttu-id="d8628-137">在 Azure HDInsight 上使用 Apache Spark 搭配 F#</span><span class="sxs-lookup"><span data-stu-id="d8628-137">Using Apache Spark with F# with Azure HDInsight</span></span>

<span data-ttu-id="d8628-138">[Apache Spark for Azure HDInsight](https://azure.microsoft.com/services/hdinsight/apache-spark/) 是一種開放原始碼處理架構，可執行大規模的資料分析應用程式。</span><span class="sxs-lookup"><span data-stu-id="d8628-138">[Apache Spark for Azure HDInsight](https://azure.microsoft.com/services/hdinsight/apache-spark/) is an open source processing framework that runs large-scale data analytics applications.</span></span> <span data-ttu-id="d8628-139">Azure 可讓 Apache Spark 部署變得輕鬆又具成本效益。</span><span class="sxs-lookup"><span data-stu-id="d8628-139">Azure makes Apache Spark easy and cost effective to deploy.</span></span> <span data-ttu-id="d8628-140">請使用 [Mobius](https://github.com/Microsoft/Mobius)其為適用於 Spark 的 .NET API 來開發您的 F# Spark 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d8628-140">Develop your Spark application in F# using [Mobius](https://github.com/Microsoft/Mobius), a .NET API for Spark.</span></span>

* <span data-ttu-id="d8628-141">[Implementing Spark Apps in F# using Mobius](https://github.com/Microsoft/Mobius/blob/master/notes/spark-fsharp-mobius.md) (使用 Mobius 實作 F# Spark 應用程式)</span><span class="sxs-lookup"><span data-stu-id="d8628-141">[Implementing Spark Apps in F# using Mobius](https://github.com/Microsoft/Mobius/blob/master/notes/spark-fsharp-mobius.md)</span></span>
* <span data-ttu-id="d8628-142">[Example F# Spark Apps using Mobius](https://github.com/Microsoft/Mobius/tree/master/examples/fsharp) (使用 Mobius 的 F# Spark 應用程式範例)</span><span class="sxs-lookup"><span data-stu-id="d8628-142">[Example F# Spark Apps using Mobius](https://github.com/Microsoft/Mobius/tree/master/examples/fsharp)</span></span>

## <a name="using-azure-documentdb-with-f"></a><span data-ttu-id="d8628-143">使用 Azure DocumentDB with F #</span><span class="sxs-lookup"><span data-stu-id="d8628-143">Using Azure DocumentDB with F#</span></span> #

<span data-ttu-id="d8628-144">[Azure DocumentDB](https://azure.microsoft.com/services/documentdb/) 是一種 NoSQL 服務，適用於具高可用性且全域散發的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d8628-144">[Azure DocumentDB](https://azure.microsoft.com/services/documentdb/) is a NoSQL service for highly available, globally distributed apps.</span></span>

<span data-ttu-id="d8628-145">Azure DocumentDB 可以透過下列兩種方式與 F# 搭配使用：</span><span class="sxs-lookup"><span data-stu-id="d8628-145">Azure DocumentDB can be used with F# in two ways:</span></span>

1. <span data-ttu-id="d8628-146">透過建立可回應或導致變更 DocumentDB 集合的 F# Azure Functions。</span><span class="sxs-lookup"><span data-stu-id="d8628-146">Through the creation of F# Azure Functions which react to or cause changes to DocumentDB collections.</span></span> <span data-ttu-id="d8628-147">請參閱 [Azure Function DocumentDB 的觸發程序](/azure/azure-functions/functions-bindings-documentdb)，或</span><span class="sxs-lookup"><span data-stu-id="d8628-147">See [Azure Function triggers for DocumentDB](/azure/azure-functions/functions-bindings-documentdb), or</span></span>
2. <span data-ttu-id="d8628-148">透過使用 [.NET SDK for Azure](/azure/documentdb/documentdb-get-started-quickstart)。</span><span class="sxs-lookup"><span data-stu-id="d8628-148">By using the [.NET SDK for Azure](/azure/documentdb/documentdb-get-started-quickstart).</span></span> <span data-ttu-id="d8628-149">請注意，這些範例是根據 C#。</span><span class="sxs-lookup"><span data-stu-id="d8628-149">Note these examples are in C#.</span></span>

## <a name="using-azure-event-hubs-with-f"></a><span data-ttu-id="d8628-150">使用 F # 中使用 Azure 事件中樞</span><span class="sxs-lookup"><span data-stu-id="d8628-150">Using Azure Event Hubs with F#</span></span> #

<span data-ttu-id="d8628-151">[Azure 事件中樞](https://azure.microsoft.com/services/event-hubs/)可從網站、應用程式和裝置提供雲端等級的遙測數據。</span><span class="sxs-lookup"><span data-stu-id="d8628-151">[Azure Event Hubs](https://azure.microsoft.com/services/event-hubs/) provide cloud-scale telemetry ingestion from websites, apps, and devices.</span></span>

<span data-ttu-id="d8628-152">Azure 事件中樞可以透過下列兩種方式與 F# 搭配使用︰</span><span class="sxs-lookup"><span data-stu-id="d8628-152">Azure Event Hubs can be used with F# in two ways:</span></span>

1. <span data-ttu-id="d8628-153">透過建立事件所觸發的 F# Azure Functions。</span><span class="sxs-lookup"><span data-stu-id="d8628-153">Through the creation of F# Azure Functions which are triggered by events.</span></span> <span data-ttu-id="d8628-154">請參閱 [Azure Function 事件中樞的觸發程序](/azure/azure-functions/functions-bindings-event-hubs)，或</span><span class="sxs-lookup"><span data-stu-id="d8628-154">See [Azure Function triggers for Event Hubs](/azure/azure-functions/functions-bindings-event-hubs), or</span></span>
2. <span data-ttu-id="d8628-155">透過使用 [.NET SDK for Azure](/azure/event-hubs/event-hubs-csharp-ephcs-getstarted)。</span><span class="sxs-lookup"><span data-stu-id="d8628-155">By using the [.NET SDK for Azure](/azure/event-hubs/event-hubs-csharp-ephcs-getstarted).</span></span> <span data-ttu-id="d8628-156">請注意，這些範例是根據 C#。</span><span class="sxs-lookup"><span data-stu-id="d8628-156">Note these examples are in C#.</span></span>

## <a name="using-azure-notification-hubs-with-f"></a><span data-ttu-id="d8628-157">使用 F # 中使用 Azure 通知中樞</span><span class="sxs-lookup"><span data-stu-id="d8628-157">Using Azure Notification Hubs with F#</span></span> #

<span data-ttu-id="d8628-158">[Azure 通知中樞](/azure/notification-hubs/)是一種多平台、向外延展的推播基礎結構，可讓您將任何後端 (雲端或內部部署) 中的行動推播通知傳送到任何行動平台。</span><span class="sxs-lookup"><span data-stu-id="d8628-158">[Azure Notification Hubs](/azure/notification-hubs/) are multiplatform, scaled-out push infrastructure that enable you to send mobile push notifications from any backend (in the cloud or on-premises) to any mobile platform.</span></span>

<span data-ttu-id="d8628-159">Azure 通知中樞可以透過下列兩種方式與 F# 搭配使用︰</span><span class="sxs-lookup"><span data-stu-id="d8628-159">Azure Notification Hubs can be used with F# in two ways:</span></span>

1. <span data-ttu-id="d8628-160">透過建立可將結果傳送到通知中樞的 F# Azure Functions。</span><span class="sxs-lookup"><span data-stu-id="d8628-160">Through the creation of F# Azure Functions which send results to a notification hub.</span></span> <span data-ttu-id="d8628-161">請參閱 [Azure Function 通知中樞的輸出觸發程序](/azure/azure-functions/functions-bindings-notification-hubs)，或</span><span class="sxs-lookup"><span data-stu-id="d8628-161">See [Azure Function output triggers for Notification Hubs](/azure/azure-functions/functions-bindings-notification-hubs), or</span></span>
2. <span data-ttu-id="d8628-162">透過使用 [.NET SDK for Azure](https://blogs.msdn.microsoft.com/azuremobile/2014/04/08/push-notifications-using-notification-hub-and-net-backend/)。</span><span class="sxs-lookup"><span data-stu-id="d8628-162">By using the [.NET SDK for Azure](https://blogs.msdn.microsoft.com/azuremobile/2014/04/08/push-notifications-using-notification-hub-and-net-backend/).</span></span> <span data-ttu-id="d8628-163">請注意，這些範例是根據 C#。</span><span class="sxs-lookup"><span data-stu-id="d8628-163">Note these examples are in C#.</span></span>


## <a name="implementing-webhooks-on-azure-with-f"></a><span data-ttu-id="d8628-164">使用 F # 在 Azure 上實作 Webhook</span><span class="sxs-lookup"><span data-stu-id="d8628-164">Implementing WebHooks on Azure with F#</span></span> #

<span data-ttu-id="d8628-165">[Webhook](https://en.wikipedia.org/wiki/Webhook) 是透過 Web 要求觸發的回呼。</span><span class="sxs-lookup"><span data-stu-id="d8628-165">A [Webhook](https://en.wikipedia.org/wiki/Webhook) is a callback triggered via a web request.</span></span> <span data-ttu-id="d8628-166">GitHub 等網站會使用 Webhook 以訊號通知事件。</span><span class="sxs-lookup"><span data-stu-id="d8628-166">Webhooks are used by sites such as GitHub to signal events.</span></span> 

<span data-ttu-id="d8628-167">您可以使用 F# 實作 Webhook，並透過[含有 Webhook 繫結的 F# Azure Function](/azure/azure-functions/functions-bindings-http-webhook) 在 Azure 上裝載 Webhook。</span><span class="sxs-lookup"><span data-stu-id="d8628-167">Webhooks can be implemented in F# and hosted on Azure via an [Azure Function in F# with a Webhook Binding](/azure/azure-functions/functions-bindings-http-webhook).</span></span>

## <a name="using-webjobs-with-f"></a><span data-ttu-id="d8628-168">使用 F # 中使用 Webjobs</span><span class="sxs-lookup"><span data-stu-id="d8628-168">Using Webjobs with F#</span></span> #

<span data-ttu-id="d8628-169">[Webjobs](/azure/app-service-web/web-sites-create-web-jobs) 是您可以使用下列三種方式在 App Service Web 應用程式中執行的程式：依需求、連續或根據排程。</span><span class="sxs-lookup"><span data-stu-id="d8628-169">[Webjobs](/azure/app-service-web/web-sites-create-web-jobs) are programs you can run in your App Service web app in three ways: on demand, continuously, or on a schedule.</span></span>

<span data-ttu-id="d8628-170">[Example F# Webjob](https://github.com/andredublin/fsharp-azure-webjob) (F# Webjob 範例)</span><span class="sxs-lookup"><span data-stu-id="d8628-170">[Example F# Webjob](https://github.com/andredublin/fsharp-azure-webjob)</span></span>

## <a name="implementing-timers-on-azure-with-f"></a><span data-ttu-id="d8628-171">使用 F # 在 Azure 上實作計時器</span><span class="sxs-lookup"><span data-stu-id="d8628-171">Implementing Timers on Azure with F#</span></span> #

<span data-ttu-id="d8628-172">計時器會根據排程，觸發一次或重複觸發呼叫函式。</span><span class="sxs-lookup"><span data-stu-id="d8628-172">Timer triggers call functions based on a schedule, one time or recurring.</span></span>

<span data-ttu-id="d8628-173">您可以使用 F# 實作計時器，並透過[含有計時器觸發程序的 F# Azure Function](/azure/azure-functions/functions-bindings-timer) 在 Azure 上裝載計時器。</span><span class="sxs-lookup"><span data-stu-id="d8628-173">Timers can be implemented in F# and hosted on Azure via an [Azure Function in F# with a Timer Trigger](/azure/azure-functions/functions-bindings-timer).</span></span>

## <a name="deploying-and-managing-azure-resources-with-f-scripts"></a><span data-ttu-id="d8628-174">使用 F# 指令碼部署和管理 Azure 資源</span><span class="sxs-lookup"><span data-stu-id="d8628-174">Deploying and Managing Azure Resources with F# Scripts</span></span> #

<span data-ttu-id="d8628-175">Azure VM 可能會使用 Microsoft.Azure.Management 套件和 API，透過 F# 指令碼以程式設計方式部署和管理。</span><span class="sxs-lookup"><span data-stu-id="d8628-175">Azure VMs may be programmatically deployed and managed from F# scripts by using the Microsoft.Azure.Management packages and APIs.</span></span> <span data-ttu-id="d8628-176">例如，請參閱[開始使用 .NET 的管理程式庫](https://msdn.microsoft.com/library/dn722415.aspx)和[使用 Azure 資源管理員](/azure/azure-resource-manager/resource-manager-deployment-model)。</span><span class="sxs-lookup"><span data-stu-id="d8628-176">For example, see [Get Started with the Management Libraries for .NET](https://msdn.microsoft.com/library/dn722415.aspx) and [Using Azure Resource Manager](/azure/azure-resource-manager/resource-manager-deployment-model).</span></span>

<span data-ttu-id="d8628-177">同樣地，其他 Azure 資源也可以使用相同的元件，透過 F# 指令碼進行部署和管理。</span><span class="sxs-lookup"><span data-stu-id="d8628-177">Likewise, other Azure resources may also be deployed and managed from F# scripts using the same components.</span></span> <span data-ttu-id="d8628-178">例如，您可以建立儲存體帳戶、部署 Azure 雲端服務、建立 Azure DocumentDB 執行個體，並透過 F# 指令碼以程式設計方式管理 Azure 通知中樞。</span><span class="sxs-lookup"><span data-stu-id="d8628-178">For example, you can create storage accounts, deploy Azure Cloud Services, create Azure DocumentDB instances and manage Azure Notifcation Hubs programmatically from F# scripts.</span></span>

<span data-ttu-id="d8628-179">通常不需要使用 F# 指令碼來部署和管理資源。</span><span class="sxs-lookup"><span data-stu-id="d8628-179">Using F# scripts to deploy and manage resources is not normally necessary.</span></span> <span data-ttu-id="d8628-180">例如，Azure 資源也能夠透過可進行參數化的 JSON 範本描述加以部署。</span><span class="sxs-lookup"><span data-stu-id="d8628-180">For example, Azure resources may also be deployed directy from JSON template descriptions, which can be parameterized.</span></span> <span data-ttu-id="d8628-181">請參閱包含 [Azure 快速入門範本](https://azure.microsoft.com/documentation/templates/)等範例的 [Azure 資源管理員範本](/azure/azure-resource-manager/resource-manager-template-best-practices)。</span><span class="sxs-lookup"><span data-stu-id="d8628-181">See [Azure Resource Manager Templates](/azure/azure-resource-manager/resource-manager-template-best-practices) including examples such as the [Azure Quickstart Templates](https://azure.microsoft.com/documentation/templates/).</span></span>

## <a name="other-resources"></a><span data-ttu-id="d8628-182">其他資源</span><span class="sxs-lookup"><span data-stu-id="d8628-182">Other resources</span></span>

* [<span data-ttu-id="d8628-183">所有 Azure 服務的完整文件</span><span class="sxs-lookup"><span data-stu-id="d8628-183">Full documentation on all Azure services</span></span>](/azure/)
