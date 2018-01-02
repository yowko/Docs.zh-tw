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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 516c615248c95ef3107664b996f457fb80b46373
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltbaseaddressesgt"></a><span data-ttu-id="877ce-102">&lt;baseAddresses&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="877ce-102">&lt;add&gt; of &lt;baseAddresses&gt;</span></span>
<span data-ttu-id="877ce-103">表示組態項目，其中指定由服務主機使用的基底位址。</span><span class="sxs-lookup"><span data-stu-id="877ce-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="877ce-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="877ce-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="877ce-105">\<用戶端 ></span><span class="sxs-lookup"><span data-stu-id="877ce-105">\<client></span></span>  
<span data-ttu-id="877ce-106">\<端點 ></span><span class="sxs-lookup"><span data-stu-id="877ce-106">\<endpoint></span></span>  
<span data-ttu-id="877ce-107">\<主機 ></span><span class="sxs-lookup"><span data-stu-id="877ce-107">\<host></span></span>  
<span data-ttu-id="877ce-108">\<s ></span><span class="sxs-lookup"><span data-stu-id="877ce-108">\<baseAddresses></span></span>  
<span data-ttu-id="877ce-109">\<baseAddress ></span><span class="sxs-lookup"><span data-stu-id="877ce-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="877ce-110">語法</span><span class="sxs-lookup"><span data-stu-id="877ce-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />  
```  
  
## <a name="type"></a><span data-ttu-id="877ce-111">類型</span><span class="sxs-lookup"><span data-stu-id="877ce-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="877ce-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="877ce-112">Attributes and Elements</span></span>  
 <span data-ttu-id="877ce-113">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="877ce-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="877ce-114">屬性</span><span class="sxs-lookup"><span data-stu-id="877ce-114">Attributes</span></span>  
  
|<span data-ttu-id="877ce-115">屬性</span><span class="sxs-lookup"><span data-stu-id="877ce-115">Attribute</span></span>|<span data-ttu-id="877ce-116">描述</span><span class="sxs-lookup"><span data-stu-id="877ce-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="877ce-117">字串，指定服務主機所使用的基底位址。</span><span class="sxs-lookup"><span data-stu-id="877ce-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="877ce-118">子元素</span><span class="sxs-lookup"><span data-stu-id="877ce-118">Child Elements</span></span>  
 <span data-ttu-id="877ce-119">無。</span><span class="sxs-lookup"><span data-stu-id="877ce-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="877ce-120">父項目</span><span class="sxs-lookup"><span data-stu-id="877ce-120">Parent Elements</span></span>  
  
|<span data-ttu-id="877ce-121">項目</span><span class="sxs-lookup"><span data-stu-id="877ce-121">Element</span></span>|<span data-ttu-id="877ce-122">描述</span><span class="sxs-lookup"><span data-stu-id="877ce-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="877ce-123">\<s ></span><span class="sxs-lookup"><span data-stu-id="877ce-123">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="877ce-124">`baseAddress` 項目的集合。</span><span class="sxs-lookup"><span data-stu-id="877ce-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="877ce-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="877ce-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="877ce-126">裝載</span><span class="sxs-lookup"><span data-stu-id="877ce-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
