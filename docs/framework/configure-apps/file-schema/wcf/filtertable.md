---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 918a365004efea82f4ef4c8868f6821d4bb6da18
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855186"
---
# \<filterTable>
<span data-ttu-id="93d31-101">代表路由表，其中包含篩選條件的清單，當篩選條件評估為 true 時，可用於評估訊息及訊息的路由目標用戶端端點。</span><span class="sxs-lookup"><span data-stu-id="93d31-101">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTable>**  
  
## <a name="syntax"></a><span data-ttu-id="93d31-102">語法</span><span class="sxs-lookup"><span data-stu-id="93d31-102">Syntax</span></span>  
  
```xml  
<routing>
  <filterTables>
     name="String">
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93d31-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="93d31-103">Attributes and Elements</span></span>  
 <span data-ttu-id="93d31-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="93d31-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93d31-105">屬性</span><span class="sxs-lookup"><span data-stu-id="93d31-105">Attributes</span></span>  
  
|<span data-ttu-id="93d31-106">元素</span><span class="sxs-lookup"><span data-stu-id="93d31-106">Element</span></span>|<span data-ttu-id="93d31-107">描述</span><span class="sxs-lookup"><span data-stu-id="93d31-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="93d31-108">NAME</span><span class="sxs-lookup"><span data-stu-id="93d31-108">name</span></span>|<span data-ttu-id="93d31-109">字串，包含這個組態項目的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="93d31-109">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="93d31-110">子元素</span><span class="sxs-lookup"><span data-stu-id="93d31-110">Child Elements</span></span>  
  
|<span data-ttu-id="93d31-111">元素</span><span class="sxs-lookup"><span data-stu-id="93d31-111">Element</span></span>|<span data-ttu-id="93d31-112">描述</span><span class="sxs-lookup"><span data-stu-id="93d31-112">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="93d31-113">當篩選條件相符時，路由篩選器與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="93d31-113">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="93d31-114">父項目</span><span class="sxs-lookup"><span data-stu-id="93d31-114">Parent Elements</span></span>  
  
|<span data-ttu-id="93d31-115">元素</span><span class="sxs-lookup"><span data-stu-id="93d31-115">Element</span></span>|<span data-ttu-id="93d31-116">描述</span><span class="sxs-lookup"><span data-stu-id="93d31-116">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="93d31-117">包含路由表的組態區段。</span><span class="sxs-lookup"><span data-stu-id="93d31-117">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="93d31-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93d31-118">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
