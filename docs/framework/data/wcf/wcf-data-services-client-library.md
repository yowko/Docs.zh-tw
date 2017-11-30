---
title: "WCF 資料服務用戶端程式庫"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, client library
- DataServiceQuery class, about DataServiceQuery class
- DataServiceContext class, about DataServiceContext class
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1e321200ce4b3582d154c5a188584c9e0b12c10d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="wcf-data-services-client-library"></a><span data-ttu-id="a8a09-102">WCF 資料服務用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="a8a09-102">WCF Data Services Client Library</span></span>
<span data-ttu-id="a8a09-103">任何可以傳送 HTTP 要求並處理資料服務傳回之 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] 摘要的應用程式，都可以與 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 型資料服務互動。</span><span class="sxs-lookup"><span data-stu-id="a8a09-103">Any application can interact with an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]-based data service if it can send an HTTP request and process the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed that a data service returns.</span></span> <span data-ttu-id="a8a09-104">這個互通性可讓您存取許多 Web 架構應用程式的 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 型服務。</span><span class="sxs-lookup"><span data-stu-id="a8a09-104">This interoperability enables you to access [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-based services from a broad range of Web-enabled applications.</span></span> [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="a8a09-105">包含提供更豐富的程式設計體驗，當您使用的用戶端程式庫[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]從.NET Framework 或 Silverlight 架構應用程式摘要。</span><span class="sxs-lookup"><span data-stu-id="a8a09-105"> includes client libraries that provide a richer programming experience when you consume [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds from .NET Framework or Silverlight-based applications.</span></span>  
  
 <span data-ttu-id="a8a09-106">用戶端程式庫的兩個主要類別是 <xref:System.Data.Services.Client.DataServiceContext> 類別和 <xref:System.Data.Services.Client.DataServiceQuery%601> 類別。</span><span class="sxs-lookup"><span data-stu-id="a8a09-106">The two main classes of the client library are the <xref:System.Data.Services.Client.DataServiceContext> class and the <xref:System.Data.Services.Client.DataServiceQuery%601> class.</span></span> <span data-ttu-id="a8a09-107"><xref:System.Data.Services.Client.DataServiceContext> 類別會封裝針對特定資料服務支援的作業。</span><span class="sxs-lookup"><span data-stu-id="a8a09-107">The <xref:System.Data.Services.Client.DataServiceContext> class encapsulates operations that are supported against a specified data service.</span></span> <span data-ttu-id="a8a09-108">雖然 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 服務沒有狀態，但是內容具有狀態。</span><span class="sxs-lookup"><span data-stu-id="a8a09-108">Although [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] services are stateless, the context is not.</span></span> <span data-ttu-id="a8a09-109">因此，您可以使用<xref:System.Data.Services.Client.DataServiceContext>類別上的用戶端以支援資料服務互動之間維護狀態的功能變更管理之類。</span><span class="sxs-lookup"><span data-stu-id="a8a09-109">Therefore, you can use the <xref:System.Data.Services.Client.DataServiceContext> class to maintain state on the client between interactions with the data service in order to support features such as change management.</span></span> <span data-ttu-id="a8a09-110">這個類別也可以管理識別及追蹤變更。</span><span class="sxs-lookup"><span data-stu-id="a8a09-110">This class also manages identities and tracks changes.</span></span> <span data-ttu-id="a8a09-111"><xref:System.Data.Services.Client.DataServiceQuery%601> 類別表示針對特定實體集的查詢。</span><span class="sxs-lookup"><span data-stu-id="a8a09-111">The <xref:System.Data.Services.Client.DataServiceQuery%601> class represents a query against a specific entity set.</span></span>  
  
 <span data-ttu-id="a8a09-112">本節將描述如何使用用戶端程式庫，存取和變更 .NET Framework 用戶端應用程式的資料。</span><span class="sxs-lookup"><span data-stu-id="a8a09-112">This section describes how to use client libraries to access and change data from a .NET Framework client application.</span></span> <span data-ttu-id="a8a09-113">如需有關如何使用[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]用戶端程式庫，與以 Silverlight 為基礎的應用程式，請參閱[WCF Data Services (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=186016)。</span><span class="sxs-lookup"><span data-stu-id="a8a09-113">For more information about how to use the [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] client library with a Silverlight-based application, see [WCF Data Services (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=186016).</span></span> <span data-ttu-id="a8a09-114">其他用戶端程式庫，可讓您使用[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]其他種類的應用程式中的摘要。</span><span class="sxs-lookup"><span data-stu-id="a8a09-114">Other client libraries are available that enable you to consume an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed in other kinds of applications.</span></span> <span data-ttu-id="a8a09-115">如需詳細資訊，請參閱[OData SDK](http://go.microsoft.com/fwlink/?LinkID=185796)。</span><span class="sxs-lookup"><span data-stu-id="a8a09-115">For more information, see the [OData SDK](http://go.microsoft.com/fwlink/?LinkID=185796).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a8a09-116">本章節內容</span><span class="sxs-lookup"><span data-stu-id="a8a09-116">In This Section</span></span>  
 [<span data-ttu-id="a8a09-117">產生資料服務用戶端程式庫</span><span class="sxs-lookup"><span data-stu-id="a8a09-117">Generating the Data Service Client Library</span></span>](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 <span data-ttu-id="a8a09-118">描述如何產生用戶端程式庫和用戶端資料服務類別為基礎的[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]摘要。</span><span class="sxs-lookup"><span data-stu-id="a8a09-118">Describes how to generate a client library and client data service classes that are based on [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feeds.</span></span>  
  
 [<span data-ttu-id="a8a09-119">查詢資料服務</span><span class="sxs-lookup"><span data-stu-id="a8a09-119">Querying the Data Service</span></span>](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 <span data-ttu-id="a8a09-120">描述如何使用用戶端程式庫查詢 .NET Framework 架構應用程式的資料服務。</span><span class="sxs-lookup"><span data-stu-id="a8a09-120">Describes how to query a data service from a .NET Framework-based application by using client libraries.</span></span>  
  
 [<span data-ttu-id="a8a09-121">載入延後內容</span><span class="sxs-lookup"><span data-stu-id="a8a09-121">Loading Deferred Content</span></span>](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 <span data-ttu-id="a8a09-122">描述如何載入不包含在初始查詢回應中的額外內容。</span><span class="sxs-lookup"><span data-stu-id="a8a09-122">Describes how to load additional content not included in the initial query response.</span></span>  
  
 [<span data-ttu-id="a8a09-123">更新資料服務</span><span class="sxs-lookup"><span data-stu-id="a8a09-123">Updating the Data Service</span></span>](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)  
 <span data-ttu-id="a8a09-124">描述如何使用用戶端程式庫建立、修改，以及刪除實體及關聯性。</span><span class="sxs-lookup"><span data-stu-id="a8a09-124">Describes how to create, modify, and delete entities and relationships by using the client libraries.</span></span>  
  
 [<span data-ttu-id="a8a09-125">非同步作業</span><span class="sxs-lookup"><span data-stu-id="a8a09-125">Asynchronous Operations</span></span>](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)  
 <span data-ttu-id="a8a09-126">描述以非同步方式，搭配用戶端程式庫提供的機能與資料服務一起使用。</span><span class="sxs-lookup"><span data-stu-id="a8a09-126">Describes the facilities provided by the client libraries for working with a data service in an asynchronous manner.</span></span>  
  
 [<span data-ttu-id="a8a09-127">批次處理作業</span><span class="sxs-lookup"><span data-stu-id="a8a09-127">Batching Operations</span></span>](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)  
 <span data-ttu-id="a8a09-128">描述如何使用用戶端程式庫，在單一批次中將多個要求傳送至資料服務。</span><span class="sxs-lookup"><span data-stu-id="a8a09-128">Describes how to send multiple requests to the data service in a single batch by using the client libraries.</span></span>  
  
 [<span data-ttu-id="a8a09-129">資料繫結至控制項</span><span class="sxs-lookup"><span data-stu-id="a8a09-129">Binding Data to Controls</span></span>](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)  
 <span data-ttu-id="a8a09-130">描述如何將繫結控制項至[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]資料服務所傳回的摘要。</span><span class="sxs-lookup"><span data-stu-id="a8a09-130">Describes how to bind controls to a [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed returned by a data service.</span></span>  
  
 [<span data-ttu-id="a8a09-131">呼叫服務作業</span><span class="sxs-lookup"><span data-stu-id="a8a09-131">Calling Service Operations</span></span>](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md)  
 <span data-ttu-id="a8a09-132">說明如何使用用戶端程式庫呼叫服務作業。</span><span class="sxs-lookup"><span data-stu-id="a8a09-132">Describes how to use the client library to call service operations.</span></span>  
  
 [<span data-ttu-id="a8a09-133">管理資料服務內容</span><span class="sxs-lookup"><span data-stu-id="a8a09-133">Managing the Data Service Context</span></span>](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)  
 <span data-ttu-id="a8a09-134">說明用於管理用戶端程式庫行為的選項。</span><span class="sxs-lookup"><span data-stu-id="a8a09-134">Describes options for managing the behavior of the client library.</span></span>  
  
 [<span data-ttu-id="a8a09-135">使用二進位資料</span><span class="sxs-lookup"><span data-stu-id="a8a09-135">Working with Binary Data</span></span>](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md)  
 <span data-ttu-id="a8a09-136">說明如何存取及變更資料服務當做資料流傳回的二進位資料。</span><span class="sxs-lookup"><span data-stu-id="a8a09-136">Describes how to access and change binary data returned by the data service as a data stream.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8a09-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8a09-137">See Also</span></span>  
 [<span data-ttu-id="a8a09-138">定義 WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="a8a09-138">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [<span data-ttu-id="a8a09-139">快速入門</span><span class="sxs-lookup"><span data-stu-id="a8a09-139">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
