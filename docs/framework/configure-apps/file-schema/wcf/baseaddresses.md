---
title: '&lt;baseAddresses&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bfe66b499eb50a058ed8b6a46769893f6dc5fd6e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltbaseaddressesgt"></a><span data-ttu-id="102c3-102">&lt;baseAddresses&gt;</span><span class="sxs-lookup"><span data-stu-id="102c3-102">&lt;baseAddresses&gt;</span></span>
<span data-ttu-id="102c3-103">代表 `baseAddress` 項目的集合，這些項目是自我裝載環境中之服務主機的基底位址。</span><span class="sxs-lookup"><span data-stu-id="102c3-103">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="102c3-104">如果基底位址存在，即可以相對於基底位址的位址設定端點。</span><span class="sxs-lookup"><span data-stu-id="102c3-104">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="102c3-105">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="102c3-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="102c3-106">\<用戶端 ></span><span class="sxs-lookup"><span data-stu-id="102c3-106">\<client></span></span>  
<span data-ttu-id="102c3-107">\<端點 ></span><span class="sxs-lookup"><span data-stu-id="102c3-107">\<endpoint></span></span>  
<span data-ttu-id="102c3-108">\<主機 ></span><span class="sxs-lookup"><span data-stu-id="102c3-108">\<host></span></span>  
<span data-ttu-id="102c3-109">\<s ></span><span class="sxs-lookup"><span data-stu-id="102c3-109">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="102c3-110">語法</span><span class="sxs-lookup"><span data-stu-id="102c3-110">Syntax</span></span>  
  
```xml  
<baseAddresses>  
   <add baseAddress="string" />  
</baseAddresses>  
```  
  
## <a name="type"></a><span data-ttu-id="102c3-111">類型</span><span class="sxs-lookup"><span data-stu-id="102c3-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="102c3-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="102c3-112">Attributes and Elements</span></span>  
 <span data-ttu-id="102c3-113">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="102c3-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="102c3-114">屬性</span><span class="sxs-lookup"><span data-stu-id="102c3-114">Attributes</span></span>  
 <span data-ttu-id="102c3-115">無。</span><span class="sxs-lookup"><span data-stu-id="102c3-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="102c3-116">子項目</span><span class="sxs-lookup"><span data-stu-id="102c3-116">Child Elements</span></span>  
  
|<span data-ttu-id="102c3-117">項目</span><span class="sxs-lookup"><span data-stu-id="102c3-117">Element</span></span>|<span data-ttu-id="102c3-118">描述</span><span class="sxs-lookup"><span data-stu-id="102c3-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="102c3-119">\<add></span><span class="sxs-lookup"><span data-stu-id="102c3-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|<span data-ttu-id="102c3-120">指定由服務主機使用之基底位址的組態項目。</span><span class="sxs-lookup"><span data-stu-id="102c3-120">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="102c3-121">父項目</span><span class="sxs-lookup"><span data-stu-id="102c3-121">Parent Elements</span></span>  
  
|<span data-ttu-id="102c3-122">項目</span><span class="sxs-lookup"><span data-stu-id="102c3-122">Element</span></span>|<span data-ttu-id="102c3-123">說明</span><span class="sxs-lookup"><span data-stu-id="102c3-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="102c3-124">\<主機 ></span><span class="sxs-lookup"><span data-stu-id="102c3-124">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="102c3-125">指定服務主機設定的組態項目。</span><span class="sxs-lookup"><span data-stu-id="102c3-125">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="102c3-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="102c3-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="102c3-127">裝載</span><span class="sxs-lookup"><span data-stu-id="102c3-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
