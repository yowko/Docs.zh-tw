---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 6e78275aaeb202405e327302455d56fa431d7f27
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855254"
---
# \<filter>

<span data-ttu-id="70cd7-101">定義路由篩選，這會決定在評估傳入訊息時所使用的 Windows Communication Foundation （WCF）類型 <xref:System.ServiceModel.Dispatcher.MessageFilter> ，以及篩選準則所需的任何支援資料或參數。</span><span class="sxs-lookup"><span data-stu-id="70cd7-101">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;[**\<routing>**](routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters-of-routing.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**  
  
## <a name="syntax"></a><span data-ttu-id="70cd7-102">語法</span><span class="sxs-lookup"><span data-stu-id="70cd7-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70cd7-103">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="70cd7-103">Attributes and elements</span></span>

<span data-ttu-id="70cd7-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="70cd7-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="70cd7-105">屬性</span><span class="sxs-lookup"><span data-stu-id="70cd7-105">Attributes</span></span>

| <span data-ttu-id="70cd7-106">屬性</span><span class="sxs-lookup"><span data-stu-id="70cd7-106">Attribute</span></span>  | <span data-ttu-id="70cd7-107">描述</span><span class="sxs-lookup"><span data-stu-id="70cd7-107">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="70cd7-108">customType</span><span class="sxs-lookup"><span data-stu-id="70cd7-108">customType</span></span> | <span data-ttu-id="70cd7-109">字串，其中包含要做為篩選之自訂類型的完整類型名稱。</span><span class="sxs-lookup"><span data-stu-id="70cd7-109">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="70cd7-110">如果 `filterType` 設定為 `custom` ，這個屬性就會包含要建立之類別的完整型別名稱。</span><span class="sxs-lookup"><span data-stu-id="70cd7-110">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="70cd7-111">`filterData`也可以包含評估自訂型別篩選準則期間要使用的值。</span><span class="sxs-lookup"><span data-stu-id="70cd7-111">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="70cd7-112">filterData</span><span class="sxs-lookup"><span data-stu-id="70cd7-112">filterData</span></span> | <span data-ttu-id="70cd7-113">包含篩選資料的字串。</span><span class="sxs-lookup"><span data-stu-id="70cd7-113">A string containing the filter data.</span></span> <span data-ttu-id="70cd7-114">如需如何指定這個屬性的詳細資訊，請參閱 <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>。</span><span class="sxs-lookup"><span data-stu-id="70cd7-114">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="70cd7-115">filterType</span><span class="sxs-lookup"><span data-stu-id="70cd7-115">filterType</span></span> | <span data-ttu-id="70cd7-116">包含篩選條件類型的字串。</span><span class="sxs-lookup"><span data-stu-id="70cd7-116">A string containing the filter type.</span></span> <span data-ttu-id="70cd7-117">此屬性的型別為 <xref:System.ServiceModel.Routing.Configuration.FilterType>。</span><span class="sxs-lookup"><span data-stu-id="70cd7-117">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="70cd7-118">如需此屬性與 `filterData` 屬性如何搭配運作的詳細資訊，請參閱 <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>。</span><span class="sxs-lookup"><span data-stu-id="70cd7-118">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="70cd7-119">NAME</span><span class="sxs-lookup"><span data-stu-id="70cd7-119">name</span></span>       | <span data-ttu-id="70cd7-120">字串，其中包含這個篩選項目的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="70cd7-120">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="70cd7-121">子元素</span><span class="sxs-lookup"><span data-stu-id="70cd7-121">Child elements</span></span>

<span data-ttu-id="70cd7-122">無。</span><span class="sxs-lookup"><span data-stu-id="70cd7-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="70cd7-123">父元素</span><span class="sxs-lookup"><span data-stu-id="70cd7-123">Parent elements</span></span>

| <span data-ttu-id="70cd7-124">元素</span><span class="sxs-lookup"><span data-stu-id="70cd7-124">Element</span></span> | <span data-ttu-id="70cd7-125">描述</span><span class="sxs-lookup"><span data-stu-id="70cd7-125">Description</span></span> |
| ------- | ----------- |
| [\<routing>](routing.md) | <span data-ttu-id="70cd7-126">定義一組路由篩選的設定區段，可決定在 <xref:System.ServiceModel.Dispatcher.MessageFilter> 評估傳入訊息時所使用的 Windows Communication Foundation （WCF）類型。</span><span class="sxs-lookup"><span data-stu-id="70cd7-126">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="70cd7-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="70cd7-127">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
