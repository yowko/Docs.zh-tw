---
title: "&lt;scopes&gt; 的 &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4771c519edda36541034d9256beb858ef17763c5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltscopesgt"></a><span data-ttu-id="fb393-102">&lt;scopes&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="fb393-102">&lt;add&gt; of &lt;scopes&gt;</span></span>
<span data-ttu-id="fb393-103">加入自訂的範圍 URI，這個 URI 可用於在查詢期間篩選服務端點。</span><span class="sxs-lookup"><span data-stu-id="fb393-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="fb393-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="fb393-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fb393-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="fb393-105">\<behaviors></span></span>  
<span data-ttu-id="fb393-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="fb393-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="fb393-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="fb393-107">\<behavior></span></span>  
<span data-ttu-id="fb393-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="fb393-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="fb393-109">\<範圍 ></span><span class="sxs-lookup"><span data-stu-id="fb393-109">\<scopes></span></span>  
<span data-ttu-id="fb393-110">\<add></span><span class="sxs-lookup"><span data-stu-id="fb393-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb393-111">語法</span><span class="sxs-lookup"><span data-stu-id="fb393-111">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb393-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fb393-112">Attributes and Elements</span></span>  
 <span data-ttu-id="fb393-113">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="fb393-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb393-114">屬性</span><span class="sxs-lookup"><span data-stu-id="fb393-114">Attributes</span></span>  
  
|<span data-ttu-id="fb393-115">屬性</span><span class="sxs-lookup"><span data-stu-id="fb393-115">Attribute</span></span>|<span data-ttu-id="fb393-116">描述</span><span class="sxs-lookup"><span data-stu-id="fb393-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fb393-117">範圍</span><span class="sxs-lookup"><span data-stu-id="fb393-117">scope</span></span>|<span data-ttu-id="fb393-118">URI，其中包含端點的範圍資訊，可用於比對尋找服務的準則。</span><span class="sxs-lookup"><span data-stu-id="fb393-118">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb393-119">子元素</span><span class="sxs-lookup"><span data-stu-id="fb393-119">Child Elements</span></span>  
 <span data-ttu-id="fb393-120">無。</span><span class="sxs-lookup"><span data-stu-id="fb393-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fb393-121">父項目</span><span class="sxs-lookup"><span data-stu-id="fb393-121">Parent Elements</span></span>  
  
|<span data-ttu-id="fb393-122">項目</span><span class="sxs-lookup"><span data-stu-id="fb393-122">Element</span></span>|<span data-ttu-id="fb393-123">說明</span><span class="sxs-lookup"><span data-stu-id="fb393-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fb393-124">\<範圍 ></span><span class="sxs-lookup"><span data-stu-id="fb393-124">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="fb393-125">包含組態項目的集合，這些項目會指定可用於在查詢期間篩選服務端點的自訂範圍 URI。</span><span class="sxs-lookup"><span data-stu-id="fb393-125">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fb393-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb393-126">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
