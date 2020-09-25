---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: fb36feedc5fb2cbdf3827cbe44242c7ac6ab8a9b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185687"
---
# \<filterTable>

<span data-ttu-id="0c9d2-101">代表路由表，其中包含篩選條件的清單，當篩選條件評估為 true 時，可用於評估訊息及訊息的路由目標用戶端端點。</span><span class="sxs-lookup"><span data-stu-id="0c9d2-101">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTable>**  
  
## <a name="syntax"></a><span data-ttu-id="0c9d2-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="0c9d2-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0c9d2-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0c9d2-103">Attributes and Elements</span></span>  

 <span data-ttu-id="0c9d2-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0c9d2-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c9d2-105">屬性</span><span class="sxs-lookup"><span data-stu-id="0c9d2-105">Attributes</span></span>  
  
|<span data-ttu-id="0c9d2-106">項目</span><span class="sxs-lookup"><span data-stu-id="0c9d2-106">Element</span></span>|<span data-ttu-id="0c9d2-107">描述</span><span class="sxs-lookup"><span data-stu-id="0c9d2-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0c9d2-108">NAME</span><span class="sxs-lookup"><span data-stu-id="0c9d2-108">name</span></span>|<span data-ttu-id="0c9d2-109">字串，包含這個組態項目的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="0c9d2-109">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0c9d2-110">子元素</span><span class="sxs-lookup"><span data-stu-id="0c9d2-110">Child Elements</span></span>  
  
|<span data-ttu-id="0c9d2-111">項目</span><span class="sxs-lookup"><span data-stu-id="0c9d2-111">Element</span></span>|<span data-ttu-id="0c9d2-112">描述</span><span class="sxs-lookup"><span data-stu-id="0c9d2-112">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="0c9d2-113">當篩選條件相符時，路由篩選器與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="0c9d2-113">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0c9d2-114">父項目</span><span class="sxs-lookup"><span data-stu-id="0c9d2-114">Parent Elements</span></span>  
  
|<span data-ttu-id="0c9d2-115">項目</span><span class="sxs-lookup"><span data-stu-id="0c9d2-115">Element</span></span>|<span data-ttu-id="0c9d2-116">描述</span><span class="sxs-lookup"><span data-stu-id="0c9d2-116">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="0c9d2-117">包含路由表的組態區段。</span><span class="sxs-lookup"><span data-stu-id="0c9d2-117">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0c9d2-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c9d2-118">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
