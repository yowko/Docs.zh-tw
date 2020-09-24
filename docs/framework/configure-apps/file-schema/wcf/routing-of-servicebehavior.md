---
title: <routing> 的 <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: cd53b720bad5752189f1c30d9e4acd3a66830396
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150878"
---
# <a name="routing-of-servicebehavior"></a><span data-ttu-id="6d315-102">\<routing> 的 \<serviceBehavior></span><span class="sxs-lookup"><span data-stu-id="6d315-102">\<routing> of \<serviceBehavior></span></span>

<span data-ttu-id="6d315-103">提供於執行階段存取路由服務的功能，可用來動態修改路由組態。</span><span class="sxs-lookup"><span data-stu-id="6d315-103">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**  
  
## <a name="syntax"></a><span data-ttu-id="6d315-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="6d315-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d315-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6d315-105">Attributes and Elements</span></span>  

 <span data-ttu-id="6d315-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6d315-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d315-107">屬性</span><span class="sxs-lookup"><span data-stu-id="6d315-107">Attributes</span></span>  
  
|<span data-ttu-id="6d315-108">屬性</span><span class="sxs-lookup"><span data-stu-id="6d315-108">Attribute</span></span>|<span data-ttu-id="6d315-109">描述</span><span class="sxs-lookup"><span data-stu-id="6d315-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6d315-110">filterTable</span><span class="sxs-lookup"><span data-stu-id="6d315-110">filterTable</span></span>|<span data-ttu-id="6d315-111">字串，指定路由表的名稱，該路由表包含將由路由服務評估的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="6d315-111">A string that specifies the name of the routing table that contains filters to be evaluated by the routing service.</span></span> <span data-ttu-id="6d315-112">這個值必須符合 `name` [\<filterTable>](filtertable.md) 區段中元素的屬性 [\<filterTables>](filtertables.md) 。</span><span class="sxs-lookup"><span data-stu-id="6d315-112">This value must match the `name` attribute of a [\<filterTable>](filtertable.md) element in the [\<filterTables>](filtertables.md) section.</span></span>|  
|<span data-ttu-id="6d315-113">routeOnHeaderOnly</span><span class="sxs-lookup"><span data-stu-id="6d315-113">routeOnHeaderOnly</span></span>|<span data-ttu-id="6d315-114">布林值，指定篩選器會檢查訊息本文和標頭，或者只檢查標頭。</span><span class="sxs-lookup"><span data-stu-id="6d315-114">A Boolean value that specifies whether the filter will examine both the message body and the header, or the header only.</span></span> <span data-ttu-id="6d315-115">預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="6d315-115">The default is `true`.</span></span>|  
|<span data-ttu-id="6d315-116">soapProcessingEnabled</span><span class="sxs-lookup"><span data-stu-id="6d315-116">soapProcessingEnabled</span></span>|<span data-ttu-id="6d315-117">布林值，指定是否應進行 SOAP 處理。</span><span class="sxs-lookup"><span data-stu-id="6d315-117">A Boolean value that specifies whether SOAP processing should occur.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6d315-118">子元素</span><span class="sxs-lookup"><span data-stu-id="6d315-118">Child Elements</span></span>  

 <span data-ttu-id="6d315-119">無。</span><span class="sxs-lookup"><span data-stu-id="6d315-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6d315-120">父項目</span><span class="sxs-lookup"><span data-stu-id="6d315-120">Parent Elements</span></span>  
  
|<span data-ttu-id="6d315-121">項目</span><span class="sxs-lookup"><span data-stu-id="6d315-121">Element</span></span>|<span data-ttu-id="6d315-122">描述</span><span class="sxs-lookup"><span data-stu-id="6d315-122">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="6d315-123">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="6d315-123">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d315-124">備註</span><span class="sxs-lookup"><span data-stu-id="6d315-124">Remarks</span></span>  

 <span data-ttu-id="6d315-125">加入至服務的行為組態時，這個組態項目會啟用服務的路由。</span><span class="sxs-lookup"><span data-stu-id="6d315-125">When added to the service’s behavior configuration, this configuration element enables routing for the service.</span></span> <span data-ttu-id="6d315-126">您可以指定這個項目中的服務使用實際的路由表。</span><span class="sxs-lookup"><span data-stu-id="6d315-126">You can specify the actual routing table to be used by the service in this element.</span></span>  
  
 <span data-ttu-id="6d315-127">使用這個組態區段時，您可以在部署模式變更時即時變更路由設定。</span><span class="sxs-lookup"><span data-stu-id="6d315-127">Using this configuration section, you can change your routing settings on the fly when your deployment pattern changes.</span></span> <span data-ttu-id="6d315-128">在執行階段中，您可以使用新的路由設定註冊自己的路由擴充，而路由服務會開始將更新後的組態資訊用於新的訊息及工作階段，同時又可以在訊息/工作階段啟動時使用現有的任何規則結束進行中的訊息/工作階段。</span><span class="sxs-lookup"><span data-stu-id="6d315-128">At runtime, you can register your own routing extension with new routing settings and the routing service will begin using the updated configuration information for new messages and sessions, while leaving in-flight messages/sessions using whatever rules were in place when they started.</span></span>  <span data-ttu-id="6d315-129">這樣您就可以在執行階段期間進行具工作階段安全且回收頻率較低的路由服務重新設定。</span><span class="sxs-lookup"><span data-stu-id="6d315-129">This gives you the ability to do session-safe, recycle-less reconfiguration of the Routing Service during runtime.</span></span>  
