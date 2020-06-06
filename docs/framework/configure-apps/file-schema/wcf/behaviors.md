---
title: <behaviors>
ms.date: 03/30/2017
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
ms.openlocfilehash: bcdd26f038b343040d81b0add83bf166a5e3151f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139698"
---
# \<behaviors>
<span data-ttu-id="abda0-101">這個項目會定義兩個名稱為 `endpointBehaviors` 和 `serviceBehaviors` 的子集合。</span><span class="sxs-lookup"><span data-stu-id="abda0-101">This element defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="abda0-102">每個集合會定義分別由端點和服務使用的行為項目。</span><span class="sxs-lookup"><span data-stu-id="abda0-102">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="abda0-103">每個行為項目都由其唯一的 `name` 屬性所識別。</span><span class="sxs-lookup"><span data-stu-id="abda0-103">Each behavior element is identified by its unique `name` attribute.</span></span> <span data-ttu-id="abda0-104">從 .NET Framework 4 開始，系結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="abda0-104">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="abda0-105">如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="abda0-105">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**  
  
## <a name="syntax"></a><span data-ttu-id="abda0-106">語法</span><span class="sxs-lookup"><span data-stu-id="abda0-106">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
  </serviceBehaviors>
  <endpointBehaviors>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="abda0-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="abda0-107">Attributes and Elements</span></span>  
 <span data-ttu-id="abda0-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="abda0-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="abda0-109">屬性</span><span class="sxs-lookup"><span data-stu-id="abda0-109">Attributes</span></span>  
 <span data-ttu-id="abda0-110">無</span><span class="sxs-lookup"><span data-stu-id="abda0-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="abda0-111">子元素</span><span class="sxs-lookup"><span data-stu-id="abda0-111">Child Elements</span></span>  
  
|<span data-ttu-id="abda0-112">元素</span><span class="sxs-lookup"><span data-stu-id="abda0-112">Element</span></span>|<span data-ttu-id="abda0-113">描述</span><span class="sxs-lookup"><span data-stu-id="abda0-113">Description</span></span>|  
|-------------|-----------------|  
|[\<endpointBehaviors>](endpointbehaviors.md)|<span data-ttu-id="abda0-114">這個組態區段表示為特定端點定義的所有行為。</span><span class="sxs-lookup"><span data-stu-id="abda0-114">This configuration section represents all the behaviors defined for a specific endpoint.</span></span>|  
|[\<serviceBehaviors>](servicebehaviors.md)|<span data-ttu-id="abda0-115">這個組態區段表示為特定服務定義的所有行為。</span><span class="sxs-lookup"><span data-stu-id="abda0-115">This configuration section represents all the behaviors defined for a specific service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="abda0-116">父項目</span><span class="sxs-lookup"><span data-stu-id="abda0-116">Parent Elements</span></span>  
  
|<span data-ttu-id="abda0-117">元素</span><span class="sxs-lookup"><span data-stu-id="abda0-117">Element</span></span>|<span data-ttu-id="abda0-118">描述</span><span class="sxs-lookup"><span data-stu-id="abda0-118">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|<span data-ttu-id="abda0-119">所有 Windows Communication Foundation (WCF) 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="abda0-119">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abda0-120">備註</span><span class="sxs-lookup"><span data-stu-id="abda0-120">Remarks</span></span>  
 <span data-ttu-id="abda0-121">您可以使用 `<remove>` 項目移除集合中的特定行為。</span><span class="sxs-lookup"><span data-stu-id="abda0-121">You can use the `<remove>` element to remove a particular behavior from the collection.</span></span> <span data-ttu-id="abda0-122">若要這麼做，只需在 `name` 項目的 `<remove>` 屬性中提供要移除之行為的名稱。</span><span class="sxs-lookup"><span data-stu-id="abda0-122">To do so, simply supply the name of the behavior to remove in the `name` attribute of the `<remove>` element.</span></span>  <span data-ttu-id="abda0-123">您也可以使用 `<clear>` 項目來清除行為集合的所有內容，確保該行為集合在啟始時就是空的。</span><span class="sxs-lookup"><span data-stu-id="abda0-123">You can also use the `<clear>` element to insure that a behavior collection starts empty by clearing out all the content of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abda0-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abda0-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="abda0-125">使用行為來設定與擴充執行階段</span><span class="sxs-lookup"><span data-stu-id="abda0-125">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
- [<span data-ttu-id="abda0-126">設定用戶端行為</span><span class="sxs-lookup"><span data-stu-id="abda0-126">Configuring Client Behaviors</span></span>](../../../wcf/configuring-client-behaviors.md)
- [<span data-ttu-id="abda0-127">指定用端執行階段行為</span><span class="sxs-lookup"><span data-stu-id="abda0-127">Specifying Client Run-Time Behavior</span></span>](../../../wcf/specifying-client-run-time-behavior.md)
- [<span data-ttu-id="abda0-128">指定服務執行階段行為</span><span class="sxs-lookup"><span data-stu-id="abda0-128">Specifying Service Run-Time Behavior</span></span>](../../../wcf/specifying-service-run-time-behavior.md)
- [<span data-ttu-id="abda0-129">安全性行為</span><span class="sxs-lookup"><span data-stu-id="abda0-129">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
