---
title: '&lt;filterTables&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 05c8d3f5ce5a01e5a88f37fce43f3b4f8d260812
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltfiltertablesgt"></a><span data-ttu-id="d1309-102">&lt;filterTables&gt;</span><span class="sxs-lookup"><span data-stu-id="d1309-102">&lt;filterTables&gt;</span></span>
<span data-ttu-id="d1309-103">代表定義路由表的組態區段，該路由表包含當篩選條件符合時，路由篩選條件與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="d1309-103">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="d1309-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="d1309-104">\<system.serviceModel></span></span>  
<span data-ttu-id="d1309-105">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="d1309-105">\<routing></span></span>  
<span data-ttu-id="d1309-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="d1309-106">\<routingTables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1309-107">語法</span><span class="sxs-lookup"><span data-stu-id="d1309-107">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d1309-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d1309-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d1309-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d1309-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1309-110">屬性</span><span class="sxs-lookup"><span data-stu-id="d1309-110">Attributes</span></span>  
 <span data-ttu-id="d1309-111">無。</span><span class="sxs-lookup"><span data-stu-id="d1309-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d1309-112">子元素</span><span class="sxs-lookup"><span data-stu-id="d1309-112">Child Elements</span></span>  
  
|<span data-ttu-id="d1309-113">項目</span><span class="sxs-lookup"><span data-stu-id="d1309-113">Element</span></span>|<span data-ttu-id="d1309-114">描述</span><span class="sxs-lookup"><span data-stu-id="d1309-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1309-115">\<篩選條件 ></span><span class="sxs-lookup"><span data-stu-id="d1309-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="d1309-116">路由表，其中包含當篩選條件符合時，路由篩選條件與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="d1309-116">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d1309-117">父項目</span><span class="sxs-lookup"><span data-stu-id="d1309-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d1309-118">項目</span><span class="sxs-lookup"><span data-stu-id="d1309-118">Element</span></span>|<span data-ttu-id="d1309-119">描述</span><span class="sxs-lookup"><span data-stu-id="d1309-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1309-120">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="d1309-120">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="d1309-121">組態區段，其中包含路由篩選條件與路由表。</span><span class="sxs-lookup"><span data-stu-id="d1309-121">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1309-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="d1309-122">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>    
