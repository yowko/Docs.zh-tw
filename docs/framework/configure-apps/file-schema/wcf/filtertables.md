---
title: <filterTables>
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: a54386de369a11a1958e4d81ab01f053a0bc5b36
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55253973"
---
# <a name="filtertables"></a><span data-ttu-id="e9d77-101">\<filterTables></span><span class="sxs-lookup"><span data-stu-id="e9d77-101">\<filterTables></span></span>
<span data-ttu-id="e9d77-102">代表定義路由表的組態區段，該路由表包含當篩選條件符合時，路由篩選條件與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="e9d77-102">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="e9d77-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e9d77-103">\<system.serviceModel></span></span>  
<span data-ttu-id="e9d77-104">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="e9d77-104">\<routing></span></span>  
<span data-ttu-id="e9d77-105">\<routingTables></span><span class="sxs-lookup"><span data-stu-id="e9d77-105">\<routingTables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9d77-106">語法</span><span class="sxs-lookup"><span data-stu-id="e9d77-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9d77-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e9d77-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e9d77-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e9d77-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9d77-109">屬性</span><span class="sxs-lookup"><span data-stu-id="e9d77-109">Attributes</span></span>  
 <span data-ttu-id="e9d77-110">無。</span><span class="sxs-lookup"><span data-stu-id="e9d77-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e9d77-111">子元素</span><span class="sxs-lookup"><span data-stu-id="e9d77-111">Child Elements</span></span>  
  
|<span data-ttu-id="e9d77-112">項目</span><span class="sxs-lookup"><span data-stu-id="e9d77-112">Element</span></span>|<span data-ttu-id="e9d77-113">描述</span><span class="sxs-lookup"><span data-stu-id="e9d77-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9d77-114">\<filters></span><span class="sxs-lookup"><span data-stu-id="e9d77-114">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="e9d77-115">路由表，其中包含當篩選條件符合時，路由篩選條件與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="e9d77-115">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e9d77-116">父項目</span><span class="sxs-lookup"><span data-stu-id="e9d77-116">Parent Elements</span></span>  
  
|<span data-ttu-id="e9d77-117">項目</span><span class="sxs-lookup"><span data-stu-id="e9d77-117">Element</span></span>|<span data-ttu-id="e9d77-118">描述</span><span class="sxs-lookup"><span data-stu-id="e9d77-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9d77-119">\<routing></span><span class="sxs-lookup"><span data-stu-id="e9d77-119">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="e9d77-120">組態區段，其中包含路由篩選條件與路由表。</span><span class="sxs-lookup"><span data-stu-id="e9d77-120">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e9d77-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9d77-121">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>
