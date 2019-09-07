---
title: <routing> 的 <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: 0998f4fc61de7099879ba6e122eed1e64588baec
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397737"
---
# <a name="routing-of-servicebehavior"></a><span data-ttu-id="fe524-102">\<serviceBehavior > 的\<路由 ></span><span class="sxs-lookup"><span data-stu-id="fe524-102">\<routing> of \<serviceBehavior></span></span>
<span data-ttu-id="fe524-103">提供於執行階段存取路由服務的功能，可用來動態修改路由組態。</span><span class="sxs-lookup"><span data-stu-id="fe524-103">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>  
  
<span data-ttu-id="fe524-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="fe524-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="fe524-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="fe524-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="fe524-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="fe524-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="fe524-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="fe524-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="fe524-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="fe524-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="fe524-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<路由 >**</span><span class="sxs-lookup"><span data-stu-id="fe524-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe524-110">語法</span><span class="sxs-lookup"><span data-stu-id="fe524-110">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <routing filterTable="String"
               routeOnHeadersOnly="Boolean"
               SoapProcessingEnabled="Boolean" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe524-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fe524-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fe524-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="fe524-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe524-113">屬性</span><span class="sxs-lookup"><span data-stu-id="fe524-113">Attributes</span></span>  
  
|<span data-ttu-id="fe524-114">屬性</span><span class="sxs-lookup"><span data-stu-id="fe524-114">Attribute</span></span>|<span data-ttu-id="fe524-115">描述</span><span class="sxs-lookup"><span data-stu-id="fe524-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fe524-116">filterTable</span><span class="sxs-lookup"><span data-stu-id="fe524-116">filterTable</span></span>|<span data-ttu-id="fe524-117">字串，指定路由表的名稱，該路由表包含將由路由服務評估的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="fe524-117">A string that specifies the name of the routing table that contains filters to be evaluated by the routing service.</span></span> <span data-ttu-id="fe524-118">這個值必須符合`name` [filterTables > 區段中 filterTable > 元素的屬性。 \< ](filtertables.md) [ \< ](filtertable.md)</span><span class="sxs-lookup"><span data-stu-id="fe524-118">This value must match the `name` attribute of a [\<filterTable>](filtertable.md) element in the [\<filterTables>](filtertables.md) section.</span></span>|  
|<span data-ttu-id="fe524-119">routeOnHeaderOnly</span><span class="sxs-lookup"><span data-stu-id="fe524-119">routeOnHeaderOnly</span></span>|<span data-ttu-id="fe524-120">布林值，指定篩選器會檢查訊息本文和標頭，或者只檢查標頭。</span><span class="sxs-lookup"><span data-stu-id="fe524-120">A Boolean value that specifies whether the filter will examine both the message body and the header, or the header only.</span></span> <span data-ttu-id="fe524-121">預設為 `true`。</span><span class="sxs-lookup"><span data-stu-id="fe524-121">The default is `true`.</span></span>|  
|<span data-ttu-id="fe524-122">soapProcessingEnabled</span><span class="sxs-lookup"><span data-stu-id="fe524-122">soapProcessingEnabled</span></span>|<span data-ttu-id="fe524-123">布林值，指定是否應進行 SOAP 處理。</span><span class="sxs-lookup"><span data-stu-id="fe524-123">A Boolean value that specifies whether SOAP processing should occur.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fe524-124">子元素</span><span class="sxs-lookup"><span data-stu-id="fe524-124">Child Elements</span></span>  
 <span data-ttu-id="fe524-125">無。</span><span class="sxs-lookup"><span data-stu-id="fe524-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fe524-126">父項目</span><span class="sxs-lookup"><span data-stu-id="fe524-126">Parent Elements</span></span>  
  
|<span data-ttu-id="fe524-127">項目</span><span class="sxs-lookup"><span data-stu-id="fe524-127">Element</span></span>|<span data-ttu-id="fe524-128">描述</span><span class="sxs-lookup"><span data-stu-id="fe524-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fe524-129">\<behavior></span><span class="sxs-lookup"><span data-stu-id="fe524-129">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="fe524-130">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="fe524-130">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe524-131">備註</span><span class="sxs-lookup"><span data-stu-id="fe524-131">Remarks</span></span>  
 <span data-ttu-id="fe524-132">加入至服務的行為組態時，這個組態項目會啟用服務的路由。</span><span class="sxs-lookup"><span data-stu-id="fe524-132">When added to the service’s behavior configuration, this configuration element enables routing for the service.</span></span> <span data-ttu-id="fe524-133">您可以指定這個項目中的服務使用實際的路由表。</span><span class="sxs-lookup"><span data-stu-id="fe524-133">You can specify the actual routing table to be used by the service in this element.</span></span>  
  
 <span data-ttu-id="fe524-134">使用這個組態區段時，您可以在部署模式變更時即時變更路由設定。</span><span class="sxs-lookup"><span data-stu-id="fe524-134">Using this configuration section, you can change your routing settings on the fly when your deployment pattern changes.</span></span> <span data-ttu-id="fe524-135">在執行階段中，您可以使用新的路由設定註冊自己的路由擴充，而路由服務會開始將更新後的組態資訊用於新的訊息及工作階段，同時又可以在訊息/工作階段啟動時使用現有的任何規則結束進行中的訊息/工作階段。</span><span class="sxs-lookup"><span data-stu-id="fe524-135">At runtime, you can register your own routing extension with new routing settings and the routing service will begin using the updated configuration information for new messages and sessions, while leaving in-flight messages/sessions using whatever rules were in place when they started.</span></span>  <span data-ttu-id="fe524-136">這樣您就可以在執行階段期間進行具工作階段安全且回收頻率較低的路由服務重新設定。</span><span class="sxs-lookup"><span data-stu-id="fe524-136">This gives you the ability to do session-safe, recycle-less reconfiguration of the Routing Service during runtime.</span></span>  
