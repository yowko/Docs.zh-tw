---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: f9e64e667befb70d617574b2a03c3e6bebb2a143
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925595"
---
# <a name="filtertable"></a><span data-ttu-id="57b10-101">\<filterTable></span><span class="sxs-lookup"><span data-stu-id="57b10-101">\<filterTable></span></span>
<span data-ttu-id="57b10-102">表示路由表, 其中包含用來評估訊息的篩選器清單, 以及當篩選準則評估為 true 時, 要將訊息路由傳送至其中的用戶端端點。</span><span class="sxs-lookup"><span data-stu-id="57b10-102">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="57b10-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="57b10-103">\<system.serviceModel></span></span>  
<span data-ttu-id="57b10-104">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="57b10-104">\<routing></span></span>  
<span data-ttu-id="57b10-105">\<routingTables></span><span class="sxs-lookup"><span data-stu-id="57b10-105">\<routingTables></span></span>  
<span data-ttu-id="57b10-106">\<資料表 ></span><span class="sxs-lookup"><span data-stu-id="57b10-106">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57b10-107">語法</span><span class="sxs-lookup"><span data-stu-id="57b10-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57b10-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="57b10-108">Attributes and Elements</span></span>  
 <span data-ttu-id="57b10-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="57b10-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57b10-110">屬性</span><span class="sxs-lookup"><span data-stu-id="57b10-110">Attributes</span></span>  
  
|<span data-ttu-id="57b10-111">項目</span><span class="sxs-lookup"><span data-stu-id="57b10-111">Element</span></span>|<span data-ttu-id="57b10-112">描述</span><span class="sxs-lookup"><span data-stu-id="57b10-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="57b10-113">NAME</span><span class="sxs-lookup"><span data-stu-id="57b10-113">name</span></span>|<span data-ttu-id="57b10-114">字串，包含這個組態項目的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="57b10-114">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="57b10-115">子元素</span><span class="sxs-lookup"><span data-stu-id="57b10-115">Child Elements</span></span>  
  
|<span data-ttu-id="57b10-116">項目</span><span class="sxs-lookup"><span data-stu-id="57b10-116">Element</span></span>|<span data-ttu-id="57b10-117">描述</span><span class="sxs-lookup"><span data-stu-id="57b10-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57b10-118">\<filters></span><span class="sxs-lookup"><span data-stu-id="57b10-118">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="57b10-119">當篩選條件相符時，路由篩選器與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="57b10-119">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="57b10-120">父項目</span><span class="sxs-lookup"><span data-stu-id="57b10-120">Parent Elements</span></span>  
  
|<span data-ttu-id="57b10-121">項目</span><span class="sxs-lookup"><span data-stu-id="57b10-121">Element</span></span>|<span data-ttu-id="57b10-122">描述</span><span class="sxs-lookup"><span data-stu-id="57b10-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="57b10-123">\<routing></span><span class="sxs-lookup"><span data-stu-id="57b10-123">\<routing></span></span>](routing.md)|<span data-ttu-id="57b10-124">包含路由表的組態區段。</span><span class="sxs-lookup"><span data-stu-id="57b10-124">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="57b10-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57b10-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
