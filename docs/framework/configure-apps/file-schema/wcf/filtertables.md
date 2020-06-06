---
title: <filterTables>
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: c68479737cefe542a10a404a8b31a4820a430ffb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855208"
---
# \<filterTables>
<span data-ttu-id="cec95-101">代表定義路由表的組態區段，該路由表包含當篩選條件符合時，路由篩選條件與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="cec95-101">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTables>**  
  
## <a name="syntax"></a><span data-ttu-id="cec95-102">語法</span><span class="sxs-lookup"><span data-stu-id="cec95-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cec95-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cec95-103">Attributes and Elements</span></span>  
 <span data-ttu-id="cec95-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="cec95-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cec95-105">屬性</span><span class="sxs-lookup"><span data-stu-id="cec95-105">Attributes</span></span>  
 <span data-ttu-id="cec95-106">無。</span><span class="sxs-lookup"><span data-stu-id="cec95-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cec95-107">子元素</span><span class="sxs-lookup"><span data-stu-id="cec95-107">Child Elements</span></span>  
  
|<span data-ttu-id="cec95-108">元素</span><span class="sxs-lookup"><span data-stu-id="cec95-108">Element</span></span>|<span data-ttu-id="cec95-109">描述</span><span class="sxs-lookup"><span data-stu-id="cec95-109">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="cec95-110">路由表，其中包含當篩選條件符合時，路由篩選條件與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="cec95-110">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cec95-111">父項目</span><span class="sxs-lookup"><span data-stu-id="cec95-111">Parent Elements</span></span>  
  
|<span data-ttu-id="cec95-112">元素</span><span class="sxs-lookup"><span data-stu-id="cec95-112">Element</span></span>|<span data-ttu-id="cec95-113">描述</span><span class="sxs-lookup"><span data-stu-id="cec95-113">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="cec95-114">組態區段，其中包含路由篩選條件與路由表。</span><span class="sxs-lookup"><span data-stu-id="cec95-114">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cec95-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cec95-115">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>
