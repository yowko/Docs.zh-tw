---
title: '&lt;serviceBehavior&gt; 的 &lt;routing&gt;'
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: 5fb7febe365f73acf09ba74b07215fe9cc659efb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750748"
---
# <a name="ltroutinggt-of-ltservicebehaviorgt"></a><span data-ttu-id="12935-102">&lt;serviceBehavior&gt; 的 &lt;routing&gt;</span><span class="sxs-lookup"><span data-stu-id="12935-102">&lt;routing&gt; of &lt;serviceBehavior&gt;</span></span>
<span data-ttu-id="12935-103">提供於執行階段存取路由服務的功能，可用來動態修改路由組態。</span><span class="sxs-lookup"><span data-stu-id="12935-103">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>  
  
 <span data-ttu-id="12935-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="12935-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="12935-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="12935-105">\<behaviors></span></span>  
<span data-ttu-id="12935-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="12935-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="12935-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="12935-107">\<behavior></span></span>  
<span data-ttu-id="12935-108">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="12935-108">\<routing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12935-109">語法</span><span class="sxs-lookup"><span data-stu-id="12935-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12935-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="12935-110">Attributes and Elements</span></span>  
 <span data-ttu-id="12935-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="12935-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="12935-112">屬性</span><span class="sxs-lookup"><span data-stu-id="12935-112">Attributes</span></span>  
  
|<span data-ttu-id="12935-113">屬性</span><span class="sxs-lookup"><span data-stu-id="12935-113">Attribute</span></span>|<span data-ttu-id="12935-114">描述</span><span class="sxs-lookup"><span data-stu-id="12935-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="12935-115">filterTable</span><span class="sxs-lookup"><span data-stu-id="12935-115">filterTable</span></span>|<span data-ttu-id="12935-116">字串，指定路由表的名稱，該路由表包含將由路由服務評估的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="12935-116">A string that specifies the name of the routing table that contains filters to be evaluated by the routing service.</span></span> <span data-ttu-id="12935-117">此值必須符合`name`屬性[ \<filterTable >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertable.md)中的項目[ \<filterTables >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) > 一節。</span><span class="sxs-lookup"><span data-stu-id="12935-117">This value must match the `name` attribute of a [\<filterTable>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertable.md) element in the [\<filterTables>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) section.</span></span>|  
|<span data-ttu-id="12935-118">routeOnHeaderOnly</span><span class="sxs-lookup"><span data-stu-id="12935-118">routeOnHeaderOnly</span></span>|<span data-ttu-id="12935-119">布林值，指定篩選器會檢查訊息本文和標頭，或者只檢查標頭。</span><span class="sxs-lookup"><span data-stu-id="12935-119">A Boolean value that specifies whether the filter will examine both the message body and the header, or the header only.</span></span> <span data-ttu-id="12935-120">預設值為 `true`。</span><span class="sxs-lookup"><span data-stu-id="12935-120">The default is `true`.</span></span>|  
|<span data-ttu-id="12935-121">soapProcessingEnabled</span><span class="sxs-lookup"><span data-stu-id="12935-121">soapProcessingEnabled</span></span>|<span data-ttu-id="12935-122">布林值，指定是否應進行 SOAP 處理。</span><span class="sxs-lookup"><span data-stu-id="12935-122">A Boolean value that specifies whether SOAP processing should occur.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="12935-123">子項目</span><span class="sxs-lookup"><span data-stu-id="12935-123">Child Elements</span></span>  
 <span data-ttu-id="12935-124">無。</span><span class="sxs-lookup"><span data-stu-id="12935-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="12935-125">父項目</span><span class="sxs-lookup"><span data-stu-id="12935-125">Parent Elements</span></span>  
  
|<span data-ttu-id="12935-126">項目</span><span class="sxs-lookup"><span data-stu-id="12935-126">Element</span></span>|<span data-ttu-id="12935-127">描述</span><span class="sxs-lookup"><span data-stu-id="12935-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12935-128">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="12935-128">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="12935-129">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="12935-129">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12935-130">備註</span><span class="sxs-lookup"><span data-stu-id="12935-130">Remarks</span></span>  
 <span data-ttu-id="12935-131">加入至服務的行為組態時，這個組態項目會啟用服務的路由。</span><span class="sxs-lookup"><span data-stu-id="12935-131">When added to the service’s behavior configuration, this configuration element enables routing for the service.</span></span> <span data-ttu-id="12935-132">您可以指定這個項目中的服務使用實際的路由表。</span><span class="sxs-lookup"><span data-stu-id="12935-132">You can specify the actual routing table to be used by the service in this element.</span></span>  
  
 <span data-ttu-id="12935-133">使用這個組態區段時，您可以在部署模式變更時即時變更路由設定。</span><span class="sxs-lookup"><span data-stu-id="12935-133">Using this configuration section, you can change your routing settings on the fly when your deployment pattern changes.</span></span> <span data-ttu-id="12935-134">在執行階段中，您可以使用新的路由設定註冊自己的路由擴充，而路由服務會開始將更新後的組態資訊用於新的訊息及工作階段，同時又可以在訊息/工作階段啟動時使用現有的任何規則結束進行中的訊息/工作階段。</span><span class="sxs-lookup"><span data-stu-id="12935-134">At runtime, you can register your own routing extension with new routing settings and the routing service will begin using the updated configuration information for new messages and sessions, while leaving in-flight messages/sessions using whatever rules were in place when they started.</span></span>  <span data-ttu-id="12935-135">這樣您就可以在執行階段期間進行具工作階段安全且回收頻率較低的路由服務重新設定。</span><span class="sxs-lookup"><span data-stu-id="12935-135">This gives you the ability to do session-safe, recycle-less reconfiguration of the Routing Service during runtime.</span></span>  
  
