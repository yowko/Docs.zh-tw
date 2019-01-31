---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: bff19f106d86c73dea80b8b57bb73442eaa2cf9f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278781"
---
# <a name="filter"></a><span data-ttu-id="0d2bc-101">\<filter></span><span class="sxs-lookup"><span data-stu-id="0d2bc-101">\<filter></span></span>

<span data-ttu-id="0d2bc-102">定義路由篩選條件，判斷類型的 Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter>傳入訊息，也可以在任何支援的資料或篩選條件所需的參數為時使用。</span><span class="sxs-lookup"><span data-stu-id="0d2bc-102">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="0d2bc-103">\<system.serviceModel> \<routing> \<filters> \<filter></span><span class="sxs-lookup"><span data-stu-id="0d2bc-103">\<system.serviceModel> \<routing> \<filters> \<filter></span></span>
  
## <a name="syntax"></a><span data-ttu-id="0d2bc-104">語法</span><span class="sxs-lookup"><span data-stu-id="0d2bc-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d2bc-105">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="0d2bc-105">Attributes and elements</span></span>

<span data-ttu-id="0d2bc-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0d2bc-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0d2bc-107">屬性</span><span class="sxs-lookup"><span data-stu-id="0d2bc-107">Attributes</span></span>

| <span data-ttu-id="0d2bc-108">屬性</span><span class="sxs-lookup"><span data-stu-id="0d2bc-108">Attribute</span></span>  | <span data-ttu-id="0d2bc-109">描述</span><span class="sxs-lookup"><span data-stu-id="0d2bc-109">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="0d2bc-110">customType</span><span class="sxs-lookup"><span data-stu-id="0d2bc-110">customType</span></span> | <span data-ttu-id="0d2bc-111">字串，其中包含要做為篩選之自訂類型的完整類型名稱。</span><span class="sxs-lookup"><span data-stu-id="0d2bc-111">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="0d2bc-112">如果`filterType`設為`custom`，這個屬性包含要建立之類別的完整型別名稱。</span><span class="sxs-lookup"><span data-stu-id="0d2bc-112">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="0d2bc-113">`filterData` 也可包含評估自訂型別篩選條件期間要使用的值。</span><span class="sxs-lookup"><span data-stu-id="0d2bc-113">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="0d2bc-114">filterData</span><span class="sxs-lookup"><span data-stu-id="0d2bc-114">filterData</span></span> | <span data-ttu-id="0d2bc-115">包含篩選資料的字串。</span><span class="sxs-lookup"><span data-stu-id="0d2bc-115">A string containing the filter data.</span></span> <span data-ttu-id="0d2bc-116">如需如何指定這個屬性的詳細資訊，請參閱 <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>。</span><span class="sxs-lookup"><span data-stu-id="0d2bc-116">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="0d2bc-117">filterType</span><span class="sxs-lookup"><span data-stu-id="0d2bc-117">filterType</span></span> | <span data-ttu-id="0d2bc-118">包含篩選條件類型的字串。</span><span class="sxs-lookup"><span data-stu-id="0d2bc-118">A string containing the filter type.</span></span> <span data-ttu-id="0d2bc-119">此屬性的型別為 <xref:System.ServiceModel.Routing.Configuration.FilterType>。</span><span class="sxs-lookup"><span data-stu-id="0d2bc-119">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="0d2bc-120">如需此屬性與 `filterData` 屬性如何搭配運作的詳細資訊，請參閱 <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>。</span><span class="sxs-lookup"><span data-stu-id="0d2bc-120">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="0d2bc-121">name</span><span class="sxs-lookup"><span data-stu-id="0d2bc-121">name</span></span>       | <span data-ttu-id="0d2bc-122">字串，其中包含這個篩選項目的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="0d2bc-122">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="0d2bc-123">子元素</span><span class="sxs-lookup"><span data-stu-id="0d2bc-123">Child elements</span></span>

<span data-ttu-id="0d2bc-124">無。</span><span class="sxs-lookup"><span data-stu-id="0d2bc-124">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0d2bc-125">父元素</span><span class="sxs-lookup"><span data-stu-id="0d2bc-125">Parent elements</span></span>

| <span data-ttu-id="0d2bc-126">元素</span><span class="sxs-lookup"><span data-stu-id="0d2bc-126">Element</span></span> | <span data-ttu-id="0d2bc-127">描述</span><span class="sxs-lookup"><span data-stu-id="0d2bc-127">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="0d2bc-128">\<routing></span><span class="sxs-lookup"><span data-stu-id="0d2bc-128">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | <span data-ttu-id="0d2bc-129">定義一組路由篩選條件，判斷類型的 Windows Communication Foundation (WCF) 的組態區段<xref:System.ServiceModel.Dispatcher.MessageFilter>傳入訊息時使用。</span><span class="sxs-lookup"><span data-stu-id="0d2bc-129">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="0d2bc-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d2bc-130">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
