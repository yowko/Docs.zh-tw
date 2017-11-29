---
title: "自訂資料服務提供者 (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF Data Services, providers
ms.assetid: e702ecdb-3419-4743-92a9-c3c0e7d44082
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 90e837739edc74ee469f42720f52789ee1c8f6fc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="custom-data-service-providers-wcf-data-services"></a><span data-ttu-id="6f43a-102">自訂資料服務提供者 (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="6f43a-102">Custom Data Service Providers (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="6f43a-103"> 包含一組提供者，可讓您根據晚期繫結的資料型別定義資料模型。</span><span class="sxs-lookup"><span data-stu-id="6f43a-103"> includes a set of providers that enables you to define a data model based on late-bound data types.</span></span>  
  
|<span data-ttu-id="6f43a-104">提供者</span><span class="sxs-lookup"><span data-stu-id="6f43a-104">Provider</span></span>|<span data-ttu-id="6f43a-105">描述</span><span class="sxs-lookup"><span data-stu-id="6f43a-105">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="6f43a-106">中繼資料提供者</span><span class="sxs-lookup"><span data-stu-id="6f43a-106">Metadata provider</span></span>|<span data-ttu-id="6f43a-107">這是核心自訂資料服務提供者，可讓您透過實作 <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> 介面，在執行階段定義自訂的資料模型。</span><span class="sxs-lookup"><span data-stu-id="6f43a-107">This is the core custom data service provider that enables you to define a custom data model at runtime by implementing the <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> interface.</span></span>|  
|<span data-ttu-id="6f43a-108">查詢提供者</span><span class="sxs-lookup"><span data-stu-id="6f43a-108">Query provider</span></span>|<span data-ttu-id="6f43a-109">此提供者可讓您針對使用 <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> 介面定義的自訂資料模型執行查詢。</span><span class="sxs-lookup"><span data-stu-id="6f43a-109">This provider enables you to execute queries against a custom data model that is defined by using the <xref:System.Data.Services.Providers.IDataServiceMetadataProvider> interface.</span></span> <span data-ttu-id="6f43a-110">查詢提供者是透過實作 <xref:System.Data.Services.Providers.IDataServiceQueryProvider> 介面而建立的。</span><span class="sxs-lookup"><span data-stu-id="6f43a-110">The query provider is created by implementing the <xref:System.Data.Services.Providers.IDataServiceQueryProvider> interface.</span></span>|  
|<span data-ttu-id="6f43a-111">更新提供者</span><span class="sxs-lookup"><span data-stu-id="6f43a-111">Update provider</span></span>|<span data-ttu-id="6f43a-112">此提供者可讓您更新在自訂資料服務提供者中公開的型別，並且管理並行。</span><span class="sxs-lookup"><span data-stu-id="6f43a-112">This provider enables you to make updates to types that are exposed in a custom data service provider and to manage concurrency.</span></span> <span data-ttu-id="6f43a-113">更新提供者是透過實作 <xref:System.Data.Services.Providers.IDataServiceUpdateProvider> 介面建立的</span><span class="sxs-lookup"><span data-stu-id="6f43a-113">An update provider is created by implementing the <xref:System.Data.Services.Providers.IDataServiceUpdateProvider> interface</span></span>|  
|<span data-ttu-id="6f43a-114">分頁提供者</span><span class="sxs-lookup"><span data-stu-id="6f43a-114">Paging provider</span></span>|<span data-ttu-id="6f43a-115">此提供者可搭配自訂資料服務提供者使用，以啟用伺服器驅動的分頁支援。</span><span class="sxs-lookup"><span data-stu-id="6f43a-115">This provider is used with the custom data service provider to enable server-driven paging support.</span></span> <span data-ttu-id="6f43a-116">自訂資料服務的分頁提供者是透過實作 <xref:System.Data.Services.Providers.IDataServicePagingProvider> 介面而建立的。</span><span class="sxs-lookup"><span data-stu-id="6f43a-116">A paging provider for a custom data service is created by implementing the <xref:System.Data.Services.Providers.IDataServicePagingProvider> interface.</span></span>|  
|<span data-ttu-id="6f43a-117">資料流處理提供者</span><span class="sxs-lookup"><span data-stu-id="6f43a-117">Streaming provider</span></span>|<span data-ttu-id="6f43a-118">此提供者可讓您將二進位大型物件資料型別公開為資料流。</span><span class="sxs-lookup"><span data-stu-id="6f43a-118">This provider enables you to expose binary large object data types as a stream.</span></span> <span data-ttu-id="6f43a-119">資料流處理提供者是透過實作 <xref:System.Data.Services.Providers.IDataServiceStreamProvider> 介面而建立的。</span><span class="sxs-lookup"><span data-stu-id="6f43a-119">A streaming provider is created by implementing the <xref:System.Data.Services.Providers.IDataServiceStreamProvider> interface.</span></span> <span data-ttu-id="6f43a-120">資料流處理提供者也可以搭配 Entity Framework 和反映資料來源提供者使用。</span><span class="sxs-lookup"><span data-stu-id="6f43a-120">The streaming provider can also be used with Entity Framework and reflection data source providers.</span></span> <span data-ttu-id="6f43a-121">如需詳細資訊，請參閱[資料流處理提供者](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="6f43a-121">For more information, see [Streaming Provider](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md).</span></span>|  
  
 <span data-ttu-id="6f43a-122">如需詳細資訊，請參閱文章[自訂資料服務提供者](http://go.microsoft.com/fwlink/?LinkID=186850)和[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]提供者中的工具組[OData SDK](http://go.microsoft.com/fwlink/?LinkId=186069)。</span><span class="sxs-lookup"><span data-stu-id="6f43a-122">For more information, see the article [Custom Data Service Providers](http://go.microsoft.com/fwlink/?LinkID=186850) and the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Provider Toolkit in the [OData SDK](http://go.microsoft.com/fwlink/?LinkId=186069).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f43a-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f43a-123">See Also</span></span>  
 [<span data-ttu-id="6f43a-124">資料服務提供者</span><span class="sxs-lookup"><span data-stu-id="6f43a-124">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [<span data-ttu-id="6f43a-125">Entity Framework 提供者</span><span class="sxs-lookup"><span data-stu-id="6f43a-125">Entity Framework Provider</span></span>](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)  
 [<span data-ttu-id="6f43a-126">反映提供者</span><span class="sxs-lookup"><span data-stu-id="6f43a-126">Reflection Provider</span></span>](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
