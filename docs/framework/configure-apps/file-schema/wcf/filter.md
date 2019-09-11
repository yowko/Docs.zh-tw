---
title: <filter>
ms.date: 03/30/2017
ms.assetid: 3266700b-904b-44e4-93a7-e06a1a445100
ms.openlocfilehash: 6e78275aaeb202405e327302455d56fa431d7f27
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855254"
---
# <a name="filter"></a><span data-ttu-id="8dcc9-101">\<filter></span><span class="sxs-lookup"><span data-stu-id="8dcc9-101">\<filter></span></span>

<span data-ttu-id="8dcc9-102">定義路由篩選，這會決定在評估傳入訊息時所使用<xref:System.ServiceModel.Dispatcher.MessageFilter>的 Windows Communication Foundation （WCF）類型，以及篩選準則所需的任何支援資料或參數。</span><span class="sxs-lookup"><span data-stu-id="8dcc9-102">Defines a routing filter, which determines the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well any supporting data or parameters required by the filter.</span></span>

<span data-ttu-id="8dcc9-103">[ **\<system.serviceModel>** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8dcc9-103">[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8dcc9-104">&nbsp;&nbsp;[ **\<routing>** ](routing.md)</span><span class="sxs-lookup"><span data-stu-id="8dcc9-104">&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="8dcc9-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<篩選 >** ](filters-of-routing.md)</span><span class="sxs-lookup"><span data-stu-id="8dcc9-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<filters>**](filters-of-routing.md)</span></span>\
<span data-ttu-id="8dcc9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<篩選 >**</span><span class="sxs-lookup"><span data-stu-id="8dcc9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dcc9-107">語法</span><span class="sxs-lookup"><span data-stu-id="8dcc9-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8dcc9-108">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="8dcc9-108">Attributes and elements</span></span>

<span data-ttu-id="8dcc9-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="8dcc9-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="8dcc9-110">屬性</span><span class="sxs-lookup"><span data-stu-id="8dcc9-110">Attributes</span></span>

| <span data-ttu-id="8dcc9-111">屬性</span><span class="sxs-lookup"><span data-stu-id="8dcc9-111">Attribute</span></span>  | <span data-ttu-id="8dcc9-112">說明</span><span class="sxs-lookup"><span data-stu-id="8dcc9-112">Description</span></span> |
| ---------- | ----------- |
| <span data-ttu-id="8dcc9-113">customType</span><span class="sxs-lookup"><span data-stu-id="8dcc9-113">customType</span></span> | <span data-ttu-id="8dcc9-114">字串，其中包含要做為篩選之自訂類型的完整類型名稱。</span><span class="sxs-lookup"><span data-stu-id="8dcc9-114">A string containing the fully qualified type name of the custom type to be used as a filter.</span></span> <span data-ttu-id="8dcc9-115">如果`filterType`設定為`custom`，這個屬性就會包含要建立之類別的完整型別名稱。</span><span class="sxs-lookup"><span data-stu-id="8dcc9-115">If `filterType` is set to `custom`, this attribute contains the fully qualified type name of the class to create.</span></span>  <span data-ttu-id="8dcc9-116">`filterData`也可以包含評估自訂型別篩選準則期間要使用的值。</span><span class="sxs-lookup"><span data-stu-id="8dcc9-116">`filterData` may also contain values to be used during evaluation of the custom type filter.</span></span> |
| <span data-ttu-id="8dcc9-117">filterData</span><span class="sxs-lookup"><span data-stu-id="8dcc9-117">filterData</span></span> | <span data-ttu-id="8dcc9-118">包含篩選資料的字串。</span><span class="sxs-lookup"><span data-stu-id="8dcc9-118">A string containing the filter data.</span></span> <span data-ttu-id="8dcc9-119">如需如何指定這個屬性的詳細資訊，請參閱 <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>。</span><span class="sxs-lookup"><span data-stu-id="8dcc9-119">For more information on how to specify this attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="8dcc9-120">filterType</span><span class="sxs-lookup"><span data-stu-id="8dcc9-120">filterType</span></span> | <span data-ttu-id="8dcc9-121">包含篩選條件類型的字串。</span><span class="sxs-lookup"><span data-stu-id="8dcc9-121">A string containing the filter type.</span></span> <span data-ttu-id="8dcc9-122">此屬性的型別為 <xref:System.ServiceModel.Routing.Configuration.FilterType>。</span><span class="sxs-lookup"><span data-stu-id="8dcc9-122">This attribute is of <xref:System.ServiceModel.Routing.Configuration.FilterType> type.</span></span>  <span data-ttu-id="8dcc9-123">如需此屬性與 `filterData` 屬性如何搭配運作的詳細資訊，請參閱 <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>。</span><span class="sxs-lookup"><span data-stu-id="8dcc9-123">For more information on how this works with the `filterData` attribute, see <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A>.</span></span> |
| <span data-ttu-id="8dcc9-124">NAME</span><span class="sxs-lookup"><span data-stu-id="8dcc9-124">name</span></span>       | <span data-ttu-id="8dcc9-125">字串，其中包含這個篩選項目的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="8dcc9-125">A string containing the unique name of this filter element.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="8dcc9-126">子元素</span><span class="sxs-lookup"><span data-stu-id="8dcc9-126">Child elements</span></span>

<span data-ttu-id="8dcc9-127">無。</span><span class="sxs-lookup"><span data-stu-id="8dcc9-127">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="8dcc9-128">父元素</span><span class="sxs-lookup"><span data-stu-id="8dcc9-128">Parent elements</span></span>

| <span data-ttu-id="8dcc9-129">元素</span><span class="sxs-lookup"><span data-stu-id="8dcc9-129">Element</span></span> | <span data-ttu-id="8dcc9-130">描述</span><span class="sxs-lookup"><span data-stu-id="8dcc9-130">Description</span></span> |
| ------- | ----------- |
| [<span data-ttu-id="8dcc9-131">\<routing></span><span class="sxs-lookup"><span data-stu-id="8dcc9-131">\<routing></span></span>](routing.md) | <span data-ttu-id="8dcc9-132">定義一組路由篩選的設定區段，可決定在評估傳入訊息時所使用的 Windows Communication Foundation<xref:System.ServiceModel.Dispatcher.MessageFilter> （WCF）類型。</span><span class="sxs-lookup"><span data-stu-id="8dcc9-132">A configuration section for defining a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages.</span></span> |

## <a name="see-also"></a><span data-ttu-id="8dcc9-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8dcc9-133">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.FilterElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterElement.FilterData%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterType?displayProperty=nameWithType>
