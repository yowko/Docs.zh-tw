---
title: <add> 的 <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 156d8b8d9d0eb05efbf306434ab4555a98bc317e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149045"
---
# <a name="add-of-entries"></a><span data-ttu-id="53922-102">\<add> 的 \<entries></span><span class="sxs-lookup"><span data-stu-id="53922-102">\<add> of \<entries></span></span>

<span data-ttu-id="53922-103">代表將篩選條件對應至先前定義之用戶端端點的路由項目。</span><span class="sxs-lookup"><span data-stu-id="53922-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="53922-104">將符合此篩選條件的訊息傳送至這個目的地。</span><span class="sxs-lookup"><span data-stu-id="53922-104">Messages matching this filter will be sent to this destination.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTable>**](filtertable.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<entries>**](entries.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="53922-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="53922-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53922-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="53922-106">Attributes and Elements</span></span>  

 <span data-ttu-id="53922-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="53922-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53922-108">屬性</span><span class="sxs-lookup"><span data-stu-id="53922-108">Attributes</span></span>  
  
|<span data-ttu-id="53922-109">屬性</span><span class="sxs-lookup"><span data-stu-id="53922-109">Attribute</span></span>|<span data-ttu-id="53922-110">描述</span><span class="sxs-lookup"><span data-stu-id="53922-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="53922-111">backupList</span><span class="sxs-lookup"><span data-stu-id="53922-111">backupList</span></span>|<span data-ttu-id="53922-112">字串，指定端點備份清單的參考。</span><span class="sxs-lookup"><span data-stu-id="53922-112">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="53922-113">端點</span><span class="sxs-lookup"><span data-stu-id="53922-113">endpoint</span></span>|<span data-ttu-id="53922-114">字串，指定對用戶端端點的參考，該端點會接收與 `filterName` 屬性指定之篩選條件相符的訊息。</span><span class="sxs-lookup"><span data-stu-id="53922-114">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="53922-115">filterName</span><span class="sxs-lookup"><span data-stu-id="53922-115">filterName</span></span>|<span data-ttu-id="53922-116">字串，指定對篩選條件項目的參考。</span><span class="sxs-lookup"><span data-stu-id="53922-116">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="53922-117">priority</span><span class="sxs-lookup"><span data-stu-id="53922-117">priority</span></span>|<span data-ttu-id="53922-118">整數，指定這個項目的優先權。</span><span class="sxs-lookup"><span data-stu-id="53922-118">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="53922-119">路由表中的項目會根據優先權進行評估，其中 0 表示優先順序最低。</span><span class="sxs-lookup"><span data-stu-id="53922-119">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="53922-120">具有特定優先順序的所有項目會同時評估，如果找不到符合目前優先順序的項目，則會評估下一個優先順序層級。</span><span class="sxs-lookup"><span data-stu-id="53922-120">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="53922-121">這是選擇性的值。</span><span class="sxs-lookup"><span data-stu-id="53922-121">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="53922-122">子元素</span><span class="sxs-lookup"><span data-stu-id="53922-122">Child Elements</span></span>  

 <span data-ttu-id="53922-123">無。</span><span class="sxs-lookup"><span data-stu-id="53922-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="53922-124">父項目</span><span class="sxs-lookup"><span data-stu-id="53922-124">Parent Elements</span></span>  
  
|<span data-ttu-id="53922-125">項目</span><span class="sxs-lookup"><span data-stu-id="53922-125">Element</span></span>|<span data-ttu-id="53922-126">描述</span><span class="sxs-lookup"><span data-stu-id="53922-126">Description</span></span>|  
|-------------|-----------------|  
|[\<routing>](routing.md)|<span data-ttu-id="53922-127">包含路由組態項目的組態區段。</span><span class="sxs-lookup"><span data-stu-id="53922-127">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="53922-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53922-128">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
