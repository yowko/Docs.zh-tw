---
title: '&lt;filterTable&gt;'
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: f790e294b832f43a595d0636c60a8a67da5ad56a
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147881"
---
# <a name="ltfiltertablegt"></a><span data-ttu-id="da8e7-102">&lt;filterTable&gt;</span><span class="sxs-lookup"><span data-stu-id="da8e7-102">&lt;filterTable&gt;</span></span>
<span data-ttu-id="da8e7-103">表示路由表，其中包含篩選條件評估為 true 時評估訊息及將訊息路由至用戶端端點的篩選器清單。</span><span class="sxs-lookup"><span data-stu-id="da8e7-103">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="da8e7-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="da8e7-104">\<system.serviceModel></span></span>  
<span data-ttu-id="da8e7-105">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="da8e7-105">\<routing></span></span>  
<span data-ttu-id="da8e7-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="da8e7-106">\<routingTables></span></span>  
<span data-ttu-id="da8e7-107">\<資料表 ></span><span class="sxs-lookup"><span data-stu-id="da8e7-107">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da8e7-108">語法</span><span class="sxs-lookup"><span data-stu-id="da8e7-108">Syntax</span></span>  
  
```xml  
<routing>
  <filterTables>
    <filterTable name="String">
      <entries>
        <add backupList="String"
             endpointName="String"
             filterName="String"
             priority="Integer" />
      </entries>
    </filterTable>
  </filterTables>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="da8e7-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="da8e7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="da8e7-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="da8e7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="da8e7-111">屬性</span><span class="sxs-lookup"><span data-stu-id="da8e7-111">Attributes</span></span>  
  
|<span data-ttu-id="da8e7-112">元素</span><span class="sxs-lookup"><span data-stu-id="da8e7-112">Element</span></span>|<span data-ttu-id="da8e7-113">描述</span><span class="sxs-lookup"><span data-stu-id="da8e7-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="da8e7-114">name</span><span class="sxs-lookup"><span data-stu-id="da8e7-114">name</span></span>|<span data-ttu-id="da8e7-115">字串，包含這個組態項目的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="da8e7-115">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="da8e7-116">子元素</span><span class="sxs-lookup"><span data-stu-id="da8e7-116">Child Elements</span></span>  
  
|<span data-ttu-id="da8e7-117">項目</span><span class="sxs-lookup"><span data-stu-id="da8e7-117">Element</span></span>|<span data-ttu-id="da8e7-118">描述</span><span class="sxs-lookup"><span data-stu-id="da8e7-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="da8e7-119">\<篩選條件 ></span><span class="sxs-lookup"><span data-stu-id="da8e7-119">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="da8e7-120">當篩選條件相符時，路由篩選器與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="da8e7-120">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="da8e7-121">父項目</span><span class="sxs-lookup"><span data-stu-id="da8e7-121">Parent Elements</span></span>  
  
|<span data-ttu-id="da8e7-122">項目</span><span class="sxs-lookup"><span data-stu-id="da8e7-122">Element</span></span>|<span data-ttu-id="da8e7-123">描述</span><span class="sxs-lookup"><span data-stu-id="da8e7-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="da8e7-124">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="da8e7-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="da8e7-125">包含路由表的組態區段。</span><span class="sxs-lookup"><span data-stu-id="da8e7-125">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="da8e7-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da8e7-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>    
