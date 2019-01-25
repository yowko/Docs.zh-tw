---
title: '&lt;filterTables&gt;'
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: d73a3c25dbb4d2de41007149ef5864fcf37ad883
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573055"
---
# <a name="ltfiltertablesgt"></a><span data-ttu-id="c267f-102">&lt;filterTables&gt;</span><span class="sxs-lookup"><span data-stu-id="c267f-102">&lt;filterTables&gt;</span></span>
<span data-ttu-id="c267f-103">代表定義路由表的組態區段，該路由表包含當篩選條件符合時，路由篩選條件與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="c267f-103">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="c267f-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c267f-104">\<system.serviceModel></span></span>  
<span data-ttu-id="c267f-105">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="c267f-105">\<routing></span></span>  
<span data-ttu-id="c267f-106">\<routingTables></span><span class="sxs-lookup"><span data-stu-id="c267f-106">\<routingTables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c267f-107">語法</span><span class="sxs-lookup"><span data-stu-id="c267f-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c267f-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c267f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c267f-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c267f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c267f-110">屬性</span><span class="sxs-lookup"><span data-stu-id="c267f-110">Attributes</span></span>  
 <span data-ttu-id="c267f-111">無。</span><span class="sxs-lookup"><span data-stu-id="c267f-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c267f-112">子元素</span><span class="sxs-lookup"><span data-stu-id="c267f-112">Child Elements</span></span>  
  
|<span data-ttu-id="c267f-113">項目</span><span class="sxs-lookup"><span data-stu-id="c267f-113">Element</span></span>|<span data-ttu-id="c267f-114">描述</span><span class="sxs-lookup"><span data-stu-id="c267f-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c267f-115">\<filters></span><span class="sxs-lookup"><span data-stu-id="c267f-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="c267f-116">路由表，其中包含當篩選條件符合時，路由篩選條件與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="c267f-116">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c267f-117">父項目</span><span class="sxs-lookup"><span data-stu-id="c267f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c267f-118">項目</span><span class="sxs-lookup"><span data-stu-id="c267f-118">Element</span></span>|<span data-ttu-id="c267f-119">描述</span><span class="sxs-lookup"><span data-stu-id="c267f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c267f-120">\<routing></span><span class="sxs-lookup"><span data-stu-id="c267f-120">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="c267f-121">組態區段，其中包含路由篩選條件與路由表。</span><span class="sxs-lookup"><span data-stu-id="c267f-121">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c267f-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c267f-122">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>
