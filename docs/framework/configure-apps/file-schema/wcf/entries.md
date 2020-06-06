---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: ffe2538fa2c3cb680285cfaa68c975c0f9d4b1bd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855285"
---
# \<entries>
<span data-ttu-id="0896e-101">這個路由項目會包含當篩選條件符合時，路由篩選條件與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="0896e-101">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<entries>**  
  
## <a name="syntax"></a><span data-ttu-id="0896e-102">語法</span><span class="sxs-lookup"><span data-stu-id="0896e-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0896e-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0896e-103">Attributes and Elements</span></span>  
 <span data-ttu-id="0896e-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0896e-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0896e-105">屬性</span><span class="sxs-lookup"><span data-stu-id="0896e-105">Attributes</span></span>  
 <span data-ttu-id="0896e-106">無。</span><span class="sxs-lookup"><span data-stu-id="0896e-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0896e-107">子元素</span><span class="sxs-lookup"><span data-stu-id="0896e-107">Child Elements</span></span>  
  
|<span data-ttu-id="0896e-108">元素</span><span class="sxs-lookup"><span data-stu-id="0896e-108">Element</span></span>|<span data-ttu-id="0896e-109">描述</span><span class="sxs-lookup"><span data-stu-id="0896e-109">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="0896e-110">將篩選條件對應至先前定義的用戶端端點。</span><span class="sxs-lookup"><span data-stu-id="0896e-110">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="0896e-111">將符合此篩選條件的訊息傳送至這個目的地。</span><span class="sxs-lookup"><span data-stu-id="0896e-111">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0896e-112">父項目</span><span class="sxs-lookup"><span data-stu-id="0896e-112">Parent Elements</span></span>  
  
|<span data-ttu-id="0896e-113">元素</span><span class="sxs-lookup"><span data-stu-id="0896e-113">Element</span></span>|<span data-ttu-id="0896e-114">描述</span><span class="sxs-lookup"><span data-stu-id="0896e-114">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="0896e-115">包含路由表的組態區段。</span><span class="sxs-lookup"><span data-stu-id="0896e-115">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0896e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0896e-116">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
