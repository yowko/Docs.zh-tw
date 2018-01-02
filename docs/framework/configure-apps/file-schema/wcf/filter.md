---
title: "&lt;篩選器&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 186c511cd8a69cef5e30e369641628a10a0972d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltfiltergt"></a><span data-ttu-id="9b110-102">&lt;篩選器&gt;</span><span class="sxs-lookup"><span data-stu-id="9b110-102">&lt;filter&gt;</span></span>

<span data-ttu-id="9b110-103">定義路由篩選條件，可判斷傳入訊息時要使用之 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> 的型別，以及篩選條件所需的任何支援資料或參數。</span><span class="sxs-lookup"><span data-stu-id="9b110-103">Defines a routing filter, which determines the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="9b110-104">\<system.serviceModel >\<路由 >\<篩選 >\<篩選 ></span><span class="sxs-lookup"><span data-stu-id="9b110-104">\<system.serviceModel> \<routing> \<filters> \<filter></span></span>

## <a name="syntax"></a><span data-ttu-id="9b110-105">語法</span><span class="sxs-lookup"><span data-stu-id="9b110-105">Syntax</span></span>

```xml
<routing>
  <filters>
    <filter customType="String" 
            filterData="String" 
            filterType="Action/Address/AddressPrefix/And/Custom/Endpoint/MatchAll/XPath" 
            name="String" />
  </filters>
</routing>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9b110-106">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="9b110-106">Attributes and elements</span></span>

<span data-ttu-id="9b110-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9b110-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9b110-108">屬性</span><span class="sxs-lookup"><span data-stu-id="9b110-108">Attributes</span></span>

| <span data-ttu-id="9b110-109">屬性</span><span class="sxs-lookup"><span data-stu-id="9b110-109">Attribute</span></span>  | <span data-ttu-id="9b110-110">描述</span><span class="sxs-lookup"><span data-stu-id="9b110-110">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="9b110-111">customType</span><span class="sxs-lookup"><span data-stu-id="9b110-111">customType</span></span> | <span data-ttu-id="9b110-112">字串，其中包含要做為篩選之自訂類型的完整類型名稱。</span><span class="sxs-lookup"><span data-stu-id="9b110-112">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="9b110-113">如果`filterType`設`custom`，這個屬性包含要建立之類別的完整限定的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="9b110-113">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="9b110-114">`filterData`也可能包含要使用的自訂型別篩選評估期間的值。</span><span class="sxs-lookup"><span data-stu-id="9b110-114">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="9b110-115">filterData</span><span class="sxs-lookup"><span data-stu-id="9b110-115">filterData</span></span> | <span data-ttu-id="9b110-116">包含篩選資料的字串。</span><span class="sxs-lookup"><span data-stu-id="9b110-116">A string containing the filter data.</span></span> <span data-ttu-id="9b110-117">如需如何指定這個屬性的詳細資訊，請參閱 <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>。</span><span class="sxs-lookup"><span data-stu-id="9b110-117">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="9b110-118">filterType</span><span class="sxs-lookup"><span data-stu-id="9b110-118">filterType</span></span> | <span data-ttu-id="9b110-119">包含篩選條件類型的字串。</span><span class="sxs-lookup"><span data-stu-id="9b110-119">A string containing the filter type.</span></span> <span data-ttu-id="9b110-120">此屬性的型別為 <xref:System.ServiceModel.Routing.Configuration.FilterType>。</span><span class="sxs-lookup"><span data-stu-id="9b110-120">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="9b110-121">如需此屬性與 `filterData` 屬性如何搭配運作的詳細資訊，請參閱 <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>。</span><span class="sxs-lookup"><span data-stu-id="9b110-121">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="9b110-122">name</span><span class="sxs-lookup"><span data-stu-id="9b110-122">name</span></span>       | <span data-ttu-id="9b110-123">字串，其中包含這個篩選項目的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="9b110-123">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="9b110-124">子元素</span><span class="sxs-lookup"><span data-stu-id="9b110-124">Child elements</span></span>

<span data-ttu-id="9b110-125">無。</span><span class="sxs-lookup"><span data-stu-id="9b110-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9b110-126">父元素</span><span class="sxs-lookup"><span data-stu-id="9b110-126">Parent elements</span></span>

| <span data-ttu-id="9b110-127">元素</span><span class="sxs-lookup"><span data-stu-id="9b110-127">Element</span></span> | <span data-ttu-id="9b110-128">描述</span><span class="sxs-lookup"><span data-stu-id="9b110-128">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="9b110-129">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="9b110-129">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="9b110-130">組態區段，用於定義一組路由篩選條件，這些篩選條件可判斷傳入訊息時要使用之 [!INCLUDE[ indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> 的型別。</span><span class="sxs-lookup"><span data-stu-id="9b110-130">A configuration section for defining a set of routing filters, which determine the type of [!INCLUDE[ indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="9b110-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b110-131">See also</span></span>

<xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>    
<xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>   
<xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>   
