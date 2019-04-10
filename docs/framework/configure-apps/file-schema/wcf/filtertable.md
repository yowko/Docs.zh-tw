---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 4e5c7d56e35afe3001f4c70064adbfef7702c720
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229273"
---
# <a name="filtertable"></a><span data-ttu-id="da50b-101">\<filterTable></span><span class="sxs-lookup"><span data-stu-id="da50b-101">\<filterTable></span></span>
<span data-ttu-id="da50b-102">表示路由表，其中包含篩選條件評估為 true 時評估訊息及將訊息路由至用戶端端點的篩選器清單。</span><span class="sxs-lookup"><span data-stu-id="da50b-102">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="da50b-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="da50b-103">\<system.serviceModel></span></span>  
<span data-ttu-id="da50b-104">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="da50b-104">\<routing></span></span>  
<span data-ttu-id="da50b-105">\<routingTables></span><span class="sxs-lookup"><span data-stu-id="da50b-105">\<routingTables></span></span>  
<span data-ttu-id="da50b-106">\<table></span><span class="sxs-lookup"><span data-stu-id="da50b-106">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da50b-107">語法</span><span class="sxs-lookup"><span data-stu-id="da50b-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="da50b-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="da50b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="da50b-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="da50b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="da50b-110">屬性</span><span class="sxs-lookup"><span data-stu-id="da50b-110">Attributes</span></span>  
  
|<span data-ttu-id="da50b-111">項目</span><span class="sxs-lookup"><span data-stu-id="da50b-111">Element</span></span>|<span data-ttu-id="da50b-112">描述</span><span class="sxs-lookup"><span data-stu-id="da50b-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="da50b-113">名稱</span><span class="sxs-lookup"><span data-stu-id="da50b-113">name</span></span>|<span data-ttu-id="da50b-114">字串，包含這個組態項目的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="da50b-114">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="da50b-115">子元素</span><span class="sxs-lookup"><span data-stu-id="da50b-115">Child Elements</span></span>  
  
|<span data-ttu-id="da50b-116">項目</span><span class="sxs-lookup"><span data-stu-id="da50b-116">Element</span></span>|<span data-ttu-id="da50b-117">描述</span><span class="sxs-lookup"><span data-stu-id="da50b-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="da50b-118">\<filters></span><span class="sxs-lookup"><span data-stu-id="da50b-118">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="da50b-119">當篩選條件相符時，路由篩選器與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="da50b-119">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="da50b-120">父項目</span><span class="sxs-lookup"><span data-stu-id="da50b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="da50b-121">項目</span><span class="sxs-lookup"><span data-stu-id="da50b-121">Element</span></span>|<span data-ttu-id="da50b-122">描述</span><span class="sxs-lookup"><span data-stu-id="da50b-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="da50b-123">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="da50b-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="da50b-124">包含路由表的組態區段。</span><span class="sxs-lookup"><span data-stu-id="da50b-124">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="da50b-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da50b-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
