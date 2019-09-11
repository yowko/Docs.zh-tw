---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: ffe2538fa2c3cb680285cfaa68c975c0f9d4b1bd
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855285"
---
# <a name="entries"></a><span data-ttu-id="832c8-101">\<專案 ></span><span class="sxs-lookup"><span data-stu-id="832c8-101">\<entries></span></span>
<span data-ttu-id="832c8-102">這個路由項目會包含當篩選條件符合時，路由篩選條件與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="832c8-102">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
<span data-ttu-id="832c8-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="832c8-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="832c8-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="832c8-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="832c8-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<路由 >** ](routing.md)</span><span class="sxs-lookup"><span data-stu-id="832c8-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="832c8-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<filterTables >** ](filtertables.md)</span><span class="sxs-lookup"><span data-stu-id="832c8-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)</span></span>\
<span data-ttu-id="832c8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<filterTable >** ](filtertable.md)</span><span class="sxs-lookup"><span data-stu-id="832c8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)</span></span>\
<span data-ttu-id="832c8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<專案 >**</span><span class="sxs-lookup"><span data-stu-id="832c8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<entries>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="832c8-109">語法</span><span class="sxs-lookup"><span data-stu-id="832c8-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="832c8-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="832c8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="832c8-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="832c8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="832c8-112">屬性</span><span class="sxs-lookup"><span data-stu-id="832c8-112">Attributes</span></span>  
 <span data-ttu-id="832c8-113">無。</span><span class="sxs-lookup"><span data-stu-id="832c8-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="832c8-114">子元素</span><span class="sxs-lookup"><span data-stu-id="832c8-114">Child Elements</span></span>  
  
|<span data-ttu-id="832c8-115">項目</span><span class="sxs-lookup"><span data-stu-id="832c8-115">Element</span></span>|<span data-ttu-id="832c8-116">描述</span><span class="sxs-lookup"><span data-stu-id="832c8-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="832c8-117">\<filters></span><span class="sxs-lookup"><span data-stu-id="832c8-117">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="832c8-118">將篩選條件對應至先前定義的用戶端端點。</span><span class="sxs-lookup"><span data-stu-id="832c8-118">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="832c8-119">將符合此篩選條件的訊息傳送至這個目的地。</span><span class="sxs-lookup"><span data-stu-id="832c8-119">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="832c8-120">父項目</span><span class="sxs-lookup"><span data-stu-id="832c8-120">Parent Elements</span></span>  
  
|<span data-ttu-id="832c8-121">項目</span><span class="sxs-lookup"><span data-stu-id="832c8-121">Element</span></span>|<span data-ttu-id="832c8-122">描述</span><span class="sxs-lookup"><span data-stu-id="832c8-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="832c8-123">\<routing></span><span class="sxs-lookup"><span data-stu-id="832c8-123">\<routing></span></span>](routing.md)|<span data-ttu-id="832c8-124">包含路由表的組態區段。</span><span class="sxs-lookup"><span data-stu-id="832c8-124">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="832c8-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="832c8-125">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
