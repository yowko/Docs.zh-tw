---
title: <filterTables>
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: faa26ca108010330475725f83dfd0c6668cfc6b1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178199"
---
# \<filterTables>

<span data-ttu-id="67b49-101">代表定義路由表的組態區段，該路由表包含當篩選條件符合時，路由篩選條件與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="67b49-101">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTables>**  
  
## <a name="syntax"></a><span data-ttu-id="67b49-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="67b49-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="67b49-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="67b49-103">Attributes and Elements</span></span>  

 <span data-ttu-id="67b49-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="67b49-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="67b49-105">屬性</span><span class="sxs-lookup"><span data-stu-id="67b49-105">Attributes</span></span>  

 <span data-ttu-id="67b49-106">無。</span><span class="sxs-lookup"><span data-stu-id="67b49-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="67b49-107">子元素</span><span class="sxs-lookup"><span data-stu-id="67b49-107">Child Elements</span></span>  
  
|<span data-ttu-id="67b49-108">項目</span><span class="sxs-lookup"><span data-stu-id="67b49-108">Element</span></span>|<span data-ttu-id="67b49-109">描述</span><span class="sxs-lookup"><span data-stu-id="67b49-109">Description</span></span>|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|<span data-ttu-id="67b49-110">路由表，其中包含當篩選條件符合時，路由篩選條件與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="67b49-110">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="67b49-111">父項目</span><span class="sxs-lookup"><span data-stu-id="67b49-111">Parent Elements</span></span>  
  
|<span data-ttu-id="67b49-112">項目</span><span class="sxs-lookup"><span data-stu-id="67b49-112">Element</span></span>|<span data-ttu-id="67b49-113">描述</span><span class="sxs-lookup"><span data-stu-id="67b49-113">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="67b49-114">組態區段，其中包含路由篩選條件與路由表。</span><span class="sxs-lookup"><span data-stu-id="67b49-114">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="67b49-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67b49-115">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>
