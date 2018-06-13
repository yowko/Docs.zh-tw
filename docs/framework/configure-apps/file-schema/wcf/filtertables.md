---
title: '&lt;filterTables&gt;'
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: 966556a1a8bde72e33640dcc6fd37ae7a044ceef
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753410"
---
# <a name="ltfiltertablesgt"></a><span data-ttu-id="1e237-102">&lt;filterTables&gt;</span><span class="sxs-lookup"><span data-stu-id="1e237-102">&lt;filterTables&gt;</span></span>
<span data-ttu-id="1e237-103">代表定義路由表的組態區段，該路由表包含當篩選條件符合時，路由篩選條件與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="1e237-103">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="1e237-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1e237-104">\<system.serviceModel></span></span>  
<span data-ttu-id="1e237-105">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="1e237-105">\<routing></span></span>  
<span data-ttu-id="1e237-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="1e237-106">\<routingTables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e237-107">語法</span><span class="sxs-lookup"><span data-stu-id="1e237-107">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1e237-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1e237-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1e237-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1e237-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e237-110">屬性</span><span class="sxs-lookup"><span data-stu-id="1e237-110">Attributes</span></span>  
 <span data-ttu-id="1e237-111">無。</span><span class="sxs-lookup"><span data-stu-id="1e237-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1e237-112">子項目</span><span class="sxs-lookup"><span data-stu-id="1e237-112">Child Elements</span></span>  
  
|<span data-ttu-id="1e237-113">項目</span><span class="sxs-lookup"><span data-stu-id="1e237-113">Element</span></span>|<span data-ttu-id="1e237-114">描述</span><span class="sxs-lookup"><span data-stu-id="1e237-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e237-115">\<篩選條件 ></span><span class="sxs-lookup"><span data-stu-id="1e237-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="1e237-116">路由表，其中包含當篩選條件符合時，路由篩選條件與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="1e237-116">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1e237-117">父項目</span><span class="sxs-lookup"><span data-stu-id="1e237-117">Parent Elements</span></span>  
  
|<span data-ttu-id="1e237-118">項目</span><span class="sxs-lookup"><span data-stu-id="1e237-118">Element</span></span>|<span data-ttu-id="1e237-119">描述</span><span class="sxs-lookup"><span data-stu-id="1e237-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e237-120">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="1e237-120">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="1e237-121">組態區段，其中包含路由篩選條件與路由表。</span><span class="sxs-lookup"><span data-stu-id="1e237-121">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1e237-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e237-122">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>    
