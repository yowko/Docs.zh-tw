---
title: <filterTables>
ms.date: 03/30/2017
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
ms.openlocfilehash: c68479737cefe542a10a404a8b31a4820a430ffb
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855208"
---
# <a name="filtertables"></a><span data-ttu-id="4d1fa-101">\<filterTables></span><span class="sxs-lookup"><span data-stu-id="4d1fa-101">\<filterTables></span></span>
<span data-ttu-id="4d1fa-102">代表定義路由表的組態區段，該路由表包含當篩選條件符合時，路由篩選條件與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="4d1fa-102">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
<span data-ttu-id="4d1fa-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4d1fa-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4d1fa-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="4d1fa-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4d1fa-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<路由 >** ](routing.md)</span><span class="sxs-lookup"><span data-stu-id="4d1fa-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="4d1fa-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<filterTables >**</span><span class="sxs-lookup"><span data-stu-id="4d1fa-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTables>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d1fa-107">語法</span><span class="sxs-lookup"><span data-stu-id="4d1fa-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d1fa-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4d1fa-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4d1fa-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4d1fa-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d1fa-110">屬性</span><span class="sxs-lookup"><span data-stu-id="4d1fa-110">Attributes</span></span>  
 <span data-ttu-id="4d1fa-111">無。</span><span class="sxs-lookup"><span data-stu-id="4d1fa-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4d1fa-112">子元素</span><span class="sxs-lookup"><span data-stu-id="4d1fa-112">Child Elements</span></span>  
  
|<span data-ttu-id="4d1fa-113">項目</span><span class="sxs-lookup"><span data-stu-id="4d1fa-113">Element</span></span>|<span data-ttu-id="4d1fa-114">描述</span><span class="sxs-lookup"><span data-stu-id="4d1fa-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d1fa-115">\<filters></span><span class="sxs-lookup"><span data-stu-id="4d1fa-115">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="4d1fa-116">路由表，其中包含當篩選條件符合時，路由篩選條件與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="4d1fa-116">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4d1fa-117">父項目</span><span class="sxs-lookup"><span data-stu-id="4d1fa-117">Parent Elements</span></span>  
  
|<span data-ttu-id="4d1fa-118">項目</span><span class="sxs-lookup"><span data-stu-id="4d1fa-118">Element</span></span>|<span data-ttu-id="4d1fa-119">描述</span><span class="sxs-lookup"><span data-stu-id="4d1fa-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d1fa-120">\<routing></span><span class="sxs-lookup"><span data-stu-id="4d1fa-120">\<routing></span></span>](routing.md)|<span data-ttu-id="4d1fa-121">組態區段，其中包含路由篩選條件與路由表。</span><span class="sxs-lookup"><span data-stu-id="4d1fa-121">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4d1fa-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d1fa-122">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>
