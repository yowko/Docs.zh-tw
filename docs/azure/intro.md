---
title: 開始使用 Azure 與 .NET
description: 了解您需要知道的 Azure 和 .NET 基本概念。
ms.date: 06/20/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: b5766012b77da88ae9a696939b6e498ebc421522
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025038"
---
# <a name="introduction-to-azure-and-net"></a><span data-ttu-id="05df3-103">Azure 與 .NET 簡介</span><span class="sxs-lookup"><span data-stu-id="05df3-103">Introduction to Azure and .NET</span></span>

## <a name="what-is-azure"></a><span data-ttu-id="05df3-104">何謂 Azure？</span><span class="sxs-lookup"><span data-stu-id="05df3-104">What is Azure?</span></span>

<span data-ttu-id="05df3-105">Azure 是一個雲端平臺，旨在簡化新式應用程式的建立流程。</span><span class="sxs-lookup"><span data-stu-id="05df3-105">Azure is a cloud platform designed to simplify the process of building modern applications.</span></span>  <span data-ttu-id="05df3-106">無論您選擇將應用程式完全裝載在 Azure 中，或使用 Azure 服務擴充您的內部部署應用程式，Azure 都可協助您建立可調整、可靠且可維護的應用程式。</span><span class="sxs-lookup"><span data-stu-id="05df3-106">Whether you choose to host your applications entirely in Azure or extend your on-premises applications with Azure services, Azure helps you create applications that are scalable, reliable, and maintainable.</span></span>  <span data-ttu-id="05df3-107">透過您已經使用的工具廣泛支援，例如 Visual Studio 和 Visual Studio Code 以及全方位的 SDK 程式庫，Azure 的設計可讓您從一開始就成為 .NET 開發人員的生產力。</span><span class="sxs-lookup"><span data-stu-id="05df3-107">With extensive support in tools you already use like Visual Studio and Visual Studio Code and a comprehensive SDK library, Azure is designed to make you, the .NET developer productive right from the start.</span></span>

## <a name="application-development-scenarios-on-azure"></a><span data-ttu-id="05df3-108">Azure 上的應用程式開發案例</span><span class="sxs-lookup"><span data-stu-id="05df3-108">Application development scenarios on Azure</span></span>

<span data-ttu-id="05df3-109">您可以根據您的需求，以不同的方式將 Azure 納入您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="05df3-109">You can incorporate Azure into your application in different ways depending on your needs.</span></span>

- <span data-ttu-id="05df3-110">**裝載在 Azure 上的應用程式-** Azure 可以將整個應用程式堆疊從 web 應用程式和 Api 裝載到儲存體服務的資料庫。</span><span class="sxs-lookup"><span data-stu-id="05df3-110">**Application hosting on Azure -** Azure can host your entire application stack from web applications and APIs to databases to storage services.</span></span> <span data-ttu-id="05df3-111">Azure 支援各種不同的裝載模型，從完全受控的服務到容器到虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="05df3-111">Azure supports a variety of hosting models from fully managed services to containers to virtual machines.</span></span> <span data-ttu-id="05df3-112">使用完全受控的 Azure 服務時，您的應用程式可以利用 Azure 中內建的擴充性、高可用性和安全性。</span><span class="sxs-lookup"><span data-stu-id="05df3-112">When using fully managed Azure services, your applications can take advantage of the scalability, high-availability, and security built in to Azure.</span></span>

- <span data-ttu-id="05df3-113">**從應用程式使用雲端服務-** 現有的應用程式可以併入 Azure 服務，以擴充其功能。</span><span class="sxs-lookup"><span data-stu-id="05df3-113">**Consuming cloud services from applications -** Existing apps can incorporate Azure services to extend their capabilities.</span></span>  <span data-ttu-id="05df3-114">這可能包括使用 [Azure 認知搜尋](/azure/search/search-what-is-azure-search)新增全文檢索搜尋功能、將應用程式秘密安全地儲存在 [Azure Key Vault](/azure/key-vault/) ，或使用 [Azure 認知服務](/azure/cognitive-services/)來新增視覺、語音和語言理解功能。</span><span class="sxs-lookup"><span data-stu-id="05df3-114">This could include adding full-text searching capability with [Azure Cognitive Search](/azure/search/search-what-is-azure-search), securely storing application secrets in [Azure Key Vault](/azure/key-vault/) or adding vision, speech and language understanding capabilities with [Azure Cognitive Services](/azure/cognitive-services/).</span></span>  <span data-ttu-id="05df3-115">這些服務完全由 Azure 管理，而且可以輕鬆地新增至您的應用程式，而不需要變更您目前的應用程式架構或部署模型。</span><span class="sxs-lookup"><span data-stu-id="05df3-115">These services are fully managed by Azure and can be easily added to your application without changing your current application architecture or deployment model.</span></span>

- <span data-ttu-id="05df3-116">**新式無伺服器架構-** Azure Functions 簡化建立解決方案來處理事件驅動的工作流程、回應 HTTP 要求、處理 Blob 儲存體中的檔案上傳，或處理佇列中的事件。</span><span class="sxs-lookup"><span data-stu-id="05df3-116">**Modern serverless architectures -** Azure Functions simplify building solutions to handle event-driven workflows, whether responding to HTTP requests, handling file uploads in Blob storage, or processing events in a queue.</span></span>  <span data-ttu-id="05df3-117">您只需撰寫處理事件所需的程式碼，而不需要擔心伺服器或架構程式碼。</span><span class="sxs-lookup"><span data-stu-id="05df3-117">You write only the code necessary to handle your event without worrying about servers or framework code.</span></span>  <span data-ttu-id="05df3-118">此外，您可以利用超過250個連接器來處理其他 Azure 和協力廠商服務，以解決最棘手的整合問題。</span><span class="sxs-lookup"><span data-stu-id="05df3-118">Further, you can take advantage of over 250 connectors to other Azure and third-party services to tackle your toughest integration problems.</span></span>

## <a name="access-azure-services-from-net-applications"></a><span data-ttu-id="05df3-119">從 .NET 應用程式存取 Azure 服務</span><span class="sxs-lookup"><span data-stu-id="05df3-119">Access Azure services from .NET applications</span></span>

<span data-ttu-id="05df3-120">無論您的應用程式是裝載于 Azure 或內部部署，大部分 Azure 服務的存取都是透過 **AZURE SDK for .net** 提供。</span><span class="sxs-lookup"><span data-stu-id="05df3-120">Whether your app is hosted in Azure or on-premises, access to most Azure services is provided through the **Azure SDK for .NET**.</span></span>  <span data-ttu-id="05df3-121">Azure SDK for .NET 是以一系列 NuGet 套件的形式提供，可在 .NET Core (2.1 和更新版本) 和 .NET Framework (4.6.1 和更高的) 應用程式中使用。</span><span class="sxs-lookup"><span data-stu-id="05df3-121">The Azure SDK for .NET is provided as a series of NuGet packages and can be used in both .NET Core (2.1 and higher) and .NET Framework (4.6.1 and higher) applications.</span></span> <span data-ttu-id="05df3-122">Azure SDK for .NET 可讓您輕鬆地將 Azure 服務整合到您的應用程式中，只要安裝正確的 NuGet 套件、將用戶端物件具現化，然後呼叫適當的方法即可。</span><span class="sxs-lookup"><span data-stu-id="05df3-122">The Azure SDK for .NET makes incorporating Azure services into your application as easy as installing the correct NuGet package, instantiating a client object and calling the appropriate methods.</span></span> <span data-ttu-id="05df3-123">如需 Azure SDK for .NET 的詳細資訊，請參閱 [AZURE sdk for .Net 總覽](./sdk/azure-sdk-for-dotnet.md)。</span><span class="sxs-lookup"><span data-stu-id="05df3-123">More information on the Azure SDK for .NET can be found in the [Azure SDK for .NET Overview](./sdk/azure-sdk-for-dotnet.md).</span></span>

![顯示 .NET 應用程式如何使用 Azure SDK 來存取 Azure 服務的圖表](./media/azure-sdk-for-dotnet-overview.png)

## <a name="next-steps"></a><span data-ttu-id="05df3-125">後續步驟</span><span class="sxs-lookup"><span data-stu-id="05df3-125">Next steps</span></span>

<span data-ttu-id="05df3-126">接下來，瞭解最 [常使用的 Azure 服務](./key-azure-services.md) 以進行 .net 開發。</span><span class="sxs-lookup"><span data-stu-id="05df3-126">Next, learn about the most [commonly used Azure services](./key-azure-services.md) for .NET development.</span></span>
