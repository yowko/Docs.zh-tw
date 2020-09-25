---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: d3dae510ac62735138a24b8fb97a8acfffde1a98
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189963"
---
# \<entries>

<span data-ttu-id="087e6-101">這個路由項目會包含當篩選條件符合時，路由篩選條件與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="087e6-101">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<entries>**  
  
## <a name="syntax"></a><span data-ttu-id="087e6-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="087e6-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="087e6-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="087e6-103">Attributes and Elements</span></span>  

 <span data-ttu-id="087e6-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="087e6-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="087e6-105">屬性</span><span class="sxs-lookup"><span data-stu-id="087e6-105">Attributes</span></span>  

 <span data-ttu-id="087e6-106">無。</span><span class="sxs-lookup"><span data-stu-id="087e6-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="087e6-107">子元素</span><span class="sxs-lookup"><span data-stu-id="087e6-107">Child Elements</span></span>  
  
|<span data-ttu-id="087e6-108">項目</span><span class="sxs-lookup"><span data-stu-id="087e6-108">Element</span></span>|<span data-ttu-id="087e6-109">描述</span><span class="sxs-lookup"><span data-stu-id="087e6-109">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="087e6-110">將篩選條件對應至先前定義的用戶端端點。</span><span class="sxs-lookup"><span data-stu-id="087e6-110">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="087e6-111">將符合此篩選條件的訊息傳送至這個目的地。</span><span class="sxs-lookup"><span data-stu-id="087e6-111">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="087e6-112">父項目</span><span class="sxs-lookup"><span data-stu-id="087e6-112">Parent Elements</span></span>  
  
|<span data-ttu-id="087e6-113">項目</span><span class="sxs-lookup"><span data-stu-id="087e6-113">Element</span></span>|<span data-ttu-id="087e6-114">描述</span><span class="sxs-lookup"><span data-stu-id="087e6-114">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="087e6-115">包含路由表的組態區段。</span><span class="sxs-lookup"><span data-stu-id="087e6-115">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="087e6-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="087e6-116">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
