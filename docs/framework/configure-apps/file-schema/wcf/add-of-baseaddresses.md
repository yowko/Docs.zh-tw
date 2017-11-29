---
title: "&lt;baseAddresses&gt; 的 &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9e941b63e42af9237388df6be8223acbad8db745
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltbaseaddressesgt"></a><span data-ttu-id="542e8-102">&lt;baseAddresses&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="542e8-102">&lt;add&gt; of &lt;baseAddresses&gt;</span></span>
<span data-ttu-id="542e8-103">表示組態項目，其中指定由服務主機使用的基底位址。</span><span class="sxs-lookup"><span data-stu-id="542e8-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="542e8-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="542e8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="542e8-105">\<用戶端 ></span><span class="sxs-lookup"><span data-stu-id="542e8-105">\<client></span></span>  
<span data-ttu-id="542e8-106">\<端點 ></span><span class="sxs-lookup"><span data-stu-id="542e8-106">\<endpoint></span></span>  
<span data-ttu-id="542e8-107">\<主機 ></span><span class="sxs-lookup"><span data-stu-id="542e8-107">\<host></span></span>  
<span data-ttu-id="542e8-108">\<s ></span><span class="sxs-lookup"><span data-stu-id="542e8-108">\<baseAddresses></span></span>  
<span data-ttu-id="542e8-109">\<baseAddress ></span><span class="sxs-lookup"><span data-stu-id="542e8-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="542e8-110">語法</span><span class="sxs-lookup"><span data-stu-id="542e8-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />  
```  
  
## <a name="type"></a><span data-ttu-id="542e8-111">類型</span><span class="sxs-lookup"><span data-stu-id="542e8-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="542e8-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="542e8-112">Attributes and Elements</span></span>  
 <span data-ttu-id="542e8-113">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="542e8-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="542e8-114">屬性</span><span class="sxs-lookup"><span data-stu-id="542e8-114">Attributes</span></span>  
  
|<span data-ttu-id="542e8-115">屬性</span><span class="sxs-lookup"><span data-stu-id="542e8-115">Attribute</span></span>|<span data-ttu-id="542e8-116">描述</span><span class="sxs-lookup"><span data-stu-id="542e8-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="542e8-117">字串，指定服務主機所使用的基底位址。</span><span class="sxs-lookup"><span data-stu-id="542e8-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="542e8-118">子元素</span><span class="sxs-lookup"><span data-stu-id="542e8-118">Child Elements</span></span>  
 <span data-ttu-id="542e8-119">無。</span><span class="sxs-lookup"><span data-stu-id="542e8-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="542e8-120">父項目</span><span class="sxs-lookup"><span data-stu-id="542e8-120">Parent Elements</span></span>  
  
|<span data-ttu-id="542e8-121">項目</span><span class="sxs-lookup"><span data-stu-id="542e8-121">Element</span></span>|<span data-ttu-id="542e8-122">說明</span><span class="sxs-lookup"><span data-stu-id="542e8-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="542e8-123">\<s ></span><span class="sxs-lookup"><span data-stu-id="542e8-123">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="542e8-124">`baseAddress` 項目的集合。</span><span class="sxs-lookup"><span data-stu-id="542e8-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="542e8-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="542e8-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="542e8-126">裝載</span><span class="sxs-lookup"><span data-stu-id="542e8-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
