---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 68de255b9f11dc4377159d1cc3efa575633db316
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918887"
---
# <a name="filter"></a><span data-ttu-id="9a81a-101">\<filter></span><span class="sxs-lookup"><span data-stu-id="9a81a-101">\<filter></span></span>

<span data-ttu-id="9a81a-102">定義路由篩選, 這會決定在評估傳入訊息時所使用<xref:System.ServiceModel.Dispatcher.MessageFilter>的 Windows Communication Foundation (WCF) 類型, 以及篩選準則所需的任何支援資料或參數。</span><span class="sxs-lookup"><span data-stu-id="9a81a-102">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="9a81a-103">\<system.serviceModel> \<routing> \<filters> \<filter></span><span class="sxs-lookup"><span data-stu-id="9a81a-103">\<system.serviceModel> \<routing> \<filters> \<filter></span></span>
  
## <a name="syntax"></a><span data-ttu-id="9a81a-104">語法</span><span class="sxs-lookup"><span data-stu-id="9a81a-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9a81a-105">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="9a81a-105">Attributes and elements</span></span>

<span data-ttu-id="9a81a-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9a81a-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9a81a-107">屬性</span><span class="sxs-lookup"><span data-stu-id="9a81a-107">Attributes</span></span>

| <span data-ttu-id="9a81a-108">屬性</span><span class="sxs-lookup"><span data-stu-id="9a81a-108">Attribute</span></span>  | <span data-ttu-id="9a81a-109">說明</span><span class="sxs-lookup"><span data-stu-id="9a81a-109">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="9a81a-110">customType</span><span class="sxs-lookup"><span data-stu-id="9a81a-110">customType</span></span> | <span data-ttu-id="9a81a-111">字串，其中包含要做為篩選之自訂類型的完整類型名稱。</span><span class="sxs-lookup"><span data-stu-id="9a81a-111">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="9a81a-112">如果`filterType`設定為`custom`, 這個屬性就會包含要建立之類別的完整型別名稱。</span><span class="sxs-lookup"><span data-stu-id="9a81a-112">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="9a81a-113">`filterData`也可以包含評估自訂型別篩選準則期間要使用的值。</span><span class="sxs-lookup"><span data-stu-id="9a81a-113">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="9a81a-114">filterData</span><span class="sxs-lookup"><span data-stu-id="9a81a-114">filterData</span></span> | <span data-ttu-id="9a81a-115">包含篩選資料的字串。</span><span class="sxs-lookup"><span data-stu-id="9a81a-115">A string containing the filter data.</span></span> <span data-ttu-id="9a81a-116">如需如何指定這個屬性的詳細資訊，請參閱 <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>。</span><span class="sxs-lookup"><span data-stu-id="9a81a-116">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="9a81a-117">filterType</span><span class="sxs-lookup"><span data-stu-id="9a81a-117">filterType</span></span> | <span data-ttu-id="9a81a-118">包含篩選條件類型的字串。</span><span class="sxs-lookup"><span data-stu-id="9a81a-118">A string containing the filter type.</span></span> <span data-ttu-id="9a81a-119">此屬性的型別為 <xref:System.ServiceModel.Routing.Configuration.FilterType>。</span><span class="sxs-lookup"><span data-stu-id="9a81a-119">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="9a81a-120">如需此屬性與 `filterData` 屬性如何搭配運作的詳細資訊，請參閱 <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>。</span><span class="sxs-lookup"><span data-stu-id="9a81a-120">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="9a81a-121">NAME</span><span class="sxs-lookup"><span data-stu-id="9a81a-121">name</span></span>       | <span data-ttu-id="9a81a-122">字串，其中包含這個篩選項目的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="9a81a-122">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="9a81a-123">子元素</span><span class="sxs-lookup"><span data-stu-id="9a81a-123">Child elements</span></span>

<span data-ttu-id="9a81a-124">無。</span><span class="sxs-lookup"><span data-stu-id="9a81a-124">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9a81a-125">父元素</span><span class="sxs-lookup"><span data-stu-id="9a81a-125">Parent elements</span></span>

| <span data-ttu-id="9a81a-126">元素</span><span class="sxs-lookup"><span data-stu-id="9a81a-126">Element</span></span> | <span data-ttu-id="9a81a-127">描述</span><span class="sxs-lookup"><span data-stu-id="9a81a-127">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="9a81a-128">\<routing></span><span class="sxs-lookup"><span data-stu-id="9a81a-128">\<routing></span></span>](routing.md) | <span data-ttu-id="9a81a-129">定義一組路由篩選的設定區段, 可決定在評估傳入訊息時所使用的 Windows Communication Foundation<xref:System.ServiceModel.Dispatcher.MessageFilter> (WCF) 類型。</span><span class="sxs-lookup"><span data-stu-id="9a81a-129">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="9a81a-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a81a-130">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
