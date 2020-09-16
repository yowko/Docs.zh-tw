---
title: WCF 資料服務用戶端程式庫
description: 瞭解如何使用 WCF Data Services 用戶端程式庫，從 .NET Framework 用戶端應用程式存取和變更資料。
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- DataServiceQuery class, about DataServiceQuery class
- DataServiceContext class, about DataServiceContext class
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
ms.openlocfilehash: 2ff3f63d406a260f83eaba4f2e7a8419046e1931
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559027"
---
# <a name="wcf-data-services-client-library"></a><span data-ttu-id="f0c42-103">WCF 資料服務用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="f0c42-103">WCF Data Services Client Library</span></span>
<span data-ttu-id="f0c42-104">如果應用程式可以傳送 HTTP 要求並處理資料服務傳回的 OData 摘要，則任何應用程式都可以與開放式資料通訊協定 (OData) 型資料服務互動。</span><span class="sxs-lookup"><span data-stu-id="f0c42-104">Any application can interact with an Open Data Protocol (OData)-based data service if it can send an HTTP request and process the OData feed that a data service returns.</span></span> <span data-ttu-id="f0c42-105">這個互通性可讓您從各種 Web 應用程式存取 OData 型服務。</span><span class="sxs-lookup"><span data-stu-id="f0c42-105">This interoperability enables you to access OData-based services from a broad range of Web-enabled applications.</span></span> <span data-ttu-id="f0c42-106">WCF Data Services 包含用戶端程式庫，可在您從 .NET Framework 或 Silverlight 架構應用程式使用 OData 摘要時，提供更豐富的程式設計體驗。</span><span class="sxs-lookup"><span data-stu-id="f0c42-106">WCF Data Services includes client libraries that provide a richer programming experience when you consume OData feeds from .NET Framework or Silverlight-based applications.</span></span>  
  
 <span data-ttu-id="f0c42-107">用戶端程式庫的兩個主要類別是 <xref:System.Data.Services.Client.DataServiceContext> 類別和 <xref:System.Data.Services.Client.DataServiceQuery%601> 類別。</span><span class="sxs-lookup"><span data-stu-id="f0c42-107">The two main classes of the client library are the <xref:System.Data.Services.Client.DataServiceContext> class and the <xref:System.Data.Services.Client.DataServiceQuery%601> class.</span></span> <span data-ttu-id="f0c42-108"><xref:System.Data.Services.Client.DataServiceContext> 類別會封裝針對特定資料服務支援的作業。</span><span class="sxs-lookup"><span data-stu-id="f0c42-108">The <xref:System.Data.Services.Client.DataServiceContext> class encapsulates operations that are supported against a specified data service.</span></span> <span data-ttu-id="f0c42-109">雖然 OData 服務是無狀態的，但內容卻不是。</span><span class="sxs-lookup"><span data-stu-id="f0c42-109">Although OData services are stateless, the context is not.</span></span> <span data-ttu-id="f0c42-110">因此，您可以使用類別，在 <xref:System.Data.Services.Client.DataServiceContext> 用戶端上維護與資料服務互動之間的狀態，以便支援變更管理之類的功能。</span><span class="sxs-lookup"><span data-stu-id="f0c42-110">Therefore, you can use the <xref:System.Data.Services.Client.DataServiceContext> class to maintain state on the client between interactions with the data service in order to support features such as change management.</span></span> <span data-ttu-id="f0c42-111">這個類別也可以管理識別及追蹤變更。</span><span class="sxs-lookup"><span data-stu-id="f0c42-111">This class also manages identities and tracks changes.</span></span> <span data-ttu-id="f0c42-112"><xref:System.Data.Services.Client.DataServiceQuery%601> 類別表示針對特定實體集的查詢。</span><span class="sxs-lookup"><span data-stu-id="f0c42-112">The <xref:System.Data.Services.Client.DataServiceQuery%601> class represents a query against a specific entity set.</span></span>  
  
 <span data-ttu-id="f0c42-113">本節將描述如何使用用戶端程式庫，存取和變更 .NET Framework 用戶端應用程式的資料。</span><span class="sxs-lookup"><span data-stu-id="f0c42-113">This section describes how to use client libraries to access and change data from a .NET Framework client application.</span></span> <span data-ttu-id="f0c42-114">如需如何搭配 Silverlight 架構應用程式使用 WCF Data Services 用戶端程式庫的詳細資訊，請參閱 [WCF Data Services (silverlight) ](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v=vs.95))。</span><span class="sxs-lookup"><span data-stu-id="f0c42-114">For more information about how to use the WCF Data Services client library with a Silverlight-based application, see [WCF Data Services (Silverlight)](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v=vs.95)).</span></span> <span data-ttu-id="f0c42-115">其他用戶端程式庫可讓您在其他類型的應用程式中使用 OData 摘要。</span><span class="sxs-lookup"><span data-stu-id="f0c42-115">Other client libraries are available that enable you to consume an OData feed in other kinds of applications.</span></span> <span data-ttu-id="f0c42-116">如需 OData SDK 的詳細資訊，請參閱 [ODATA sdk-範例程式碼](https://www.odata.org/ecosystem/#sdk)。</span><span class="sxs-lookup"><span data-stu-id="f0c42-116">For more information on OData SDK, see [OData SDK - Sample Code](https://www.odata.org/ecosystem/#sdk).</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="f0c42-117">本節內容</span><span class="sxs-lookup"><span data-stu-id="f0c42-117">In This Section</span></span>  
 [<span data-ttu-id="f0c42-118">產生資料服務用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="f0c42-118">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)  
 <span data-ttu-id="f0c42-119">描述如何產生以 OData 摘要為基礎的用戶端程式庫和用戶端資料服務類別。</span><span class="sxs-lookup"><span data-stu-id="f0c42-119">Describes how to generate a client library and client data service classes that are based on OData feeds.</span></span>  
  
 [<span data-ttu-id="f0c42-120">查詢資料服務</span><span class="sxs-lookup"><span data-stu-id="f0c42-120">Querying the Data Service</span></span>](querying-the-data-service-wcf-data-services.md)  
 <span data-ttu-id="f0c42-121">描述如何使用用戶端程式庫查詢 .NET Framework 架構應用程式的資料服務。</span><span class="sxs-lookup"><span data-stu-id="f0c42-121">Describes how to query a data service from a .NET Framework-based application by using client libraries.</span></span>  
  
 [<span data-ttu-id="f0c42-122">載入延後內容</span><span class="sxs-lookup"><span data-stu-id="f0c42-122">Loading Deferred Content</span></span>](loading-deferred-content-wcf-data-services.md)  
 <span data-ttu-id="f0c42-123">描述如何載入不包含在初始查詢回應中的額外內容。</span><span class="sxs-lookup"><span data-stu-id="f0c42-123">Describes how to load additional content not included in the initial query response.</span></span>  
  
 [<span data-ttu-id="f0c42-124">更新資料服務</span><span class="sxs-lookup"><span data-stu-id="f0c42-124">Updating the Data Service</span></span>](updating-the-data-service-wcf-data-services.md)  
 <span data-ttu-id="f0c42-125">描述如何使用用戶端程式庫建立、修改，以及刪除實體及關聯性。</span><span class="sxs-lookup"><span data-stu-id="f0c42-125">Describes how to create, modify, and delete entities and relationships by using the client libraries.</span></span>  
  
 [<span data-ttu-id="f0c42-126">非同步作業</span><span class="sxs-lookup"><span data-stu-id="f0c42-126">Asynchronous Operations</span></span>](asynchronous-operations-wcf-data-services.md)  
 <span data-ttu-id="f0c42-127">描述以非同步方式，搭配用戶端程式庫提供的機能與資料服務一起使用。</span><span class="sxs-lookup"><span data-stu-id="f0c42-127">Describes the facilities provided by the client libraries for working with a data service in an asynchronous manner.</span></span>  
  
 [<span data-ttu-id="f0c42-128">批次處理作業</span><span class="sxs-lookup"><span data-stu-id="f0c42-128">Batching Operations</span></span>](batching-operations-wcf-data-services.md)  
 <span data-ttu-id="f0c42-129">描述如何使用用戶端程式庫，在單一批次中將多個要求傳送至資料服務。</span><span class="sxs-lookup"><span data-stu-id="f0c42-129">Describes how to send multiple requests to the data service in a single batch by using the client libraries.</span></span>  
  
 [<span data-ttu-id="f0c42-130">將資料繫結至控制項</span><span class="sxs-lookup"><span data-stu-id="f0c42-130">Binding Data to Controls</span></span>](binding-data-to-controls-wcf-data-services.md)  
 <span data-ttu-id="f0c42-131">描述如何將控制項系結至資料服務所傳回的 OData 摘要。</span><span class="sxs-lookup"><span data-stu-id="f0c42-131">Describes how to bind controls to a OData feed returned by a data service.</span></span>  
  
 [<span data-ttu-id="f0c42-132">呼叫服務作業</span><span class="sxs-lookup"><span data-stu-id="f0c42-132">Calling Service Operations</span></span>](calling-service-operations-wcf-data-services.md)  
 <span data-ttu-id="f0c42-133">說明如何使用用戶端程式庫呼叫服務作業。</span><span class="sxs-lookup"><span data-stu-id="f0c42-133">Describes how to use the client library to call service operations.</span></span>  
  
 [<span data-ttu-id="f0c42-134">管理資料服務內容</span><span class="sxs-lookup"><span data-stu-id="f0c42-134">Managing the Data Service Context</span></span>](managing-the-data-service-context-wcf-data-services.md)  
 <span data-ttu-id="f0c42-135">說明用於管理用戶端程式庫行為的選項。</span><span class="sxs-lookup"><span data-stu-id="f0c42-135">Describes options for managing the behavior of the client library.</span></span>  
  
 [<span data-ttu-id="f0c42-136">使用二進位資料</span><span class="sxs-lookup"><span data-stu-id="f0c42-136">Working with Binary Data</span></span>](working-with-binary-data-wcf-data-services.md)  
 <span data-ttu-id="f0c42-137">說明如何存取及變更資料服務當做資料流傳回的二進位資料。</span><span class="sxs-lookup"><span data-stu-id="f0c42-137">Describes how to access and change binary data returned by the data service as a data stream.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0c42-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0c42-138">See also</span></span>

- [<span data-ttu-id="f0c42-139">定義 WCF 資料服務</span><span class="sxs-lookup"><span data-stu-id="f0c42-139">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
- [<span data-ttu-id="f0c42-140">快速入門</span><span class="sxs-lookup"><span data-stu-id="f0c42-140">Getting Started</span></span>](getting-started-with-wcf-data-services.md)
