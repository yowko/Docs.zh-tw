---
title: '&lt;mexTcpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 01baba8d-d784-4255-9ea2-7afff1482bf0
ms.openlocfilehash: 4c3858ee0dc7fd20bd1269c74a4499998d530f03
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54733983"
---
# <a name="ltmextcpbindinggt"></a><span data-ttu-id="9279d-102">&lt;mexTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="9279d-102">&lt;mexTcpBinding&gt;</span></span>
<span data-ttu-id="9279d-103">指定用於 TCP 上 WS-MetadataExchange (WS-MEX) 訊息交換之繫結的設定。</span><span class="sxs-lookup"><span data-stu-id="9279d-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
 <span data-ttu-id="9279d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9279d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9279d-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="9279d-105">\<bindings></span></span>  
<span data-ttu-id="9279d-106">\<mexTcpBinding></span><span class="sxs-lookup"><span data-stu-id="9279d-106">\<mexTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9279d-107">語法</span><span class="sxs-lookup"><span data-stu-id="9279d-107">Syntax</span></span>  
  
```xml  
<mexTcpBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9279d-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9279d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9279d-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9279d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9279d-110">屬性</span><span class="sxs-lookup"><span data-stu-id="9279d-110">Attributes</span></span>  
  
|<span data-ttu-id="9279d-111">屬性</span><span class="sxs-lookup"><span data-stu-id="9279d-111">Attribute</span></span>|<span data-ttu-id="9279d-112">描述</span><span class="sxs-lookup"><span data-stu-id="9279d-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="9279d-113"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="9279d-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="9279d-114">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="9279d-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9279d-115">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="9279d-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="9279d-116">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="9279d-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="9279d-117">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="9279d-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="9279d-118">每一個繫結都有一個 `name` 和 `namespace` 屬性，兩者結合在一起便可在服務的中繼資料中唯一識別各個繫結。</span><span class="sxs-lookup"><span data-stu-id="9279d-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="9279d-119">此外，這個名稱在相同型別的繫結中也是唯一的。</span><span class="sxs-lookup"><span data-stu-id="9279d-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="9279d-120">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="9279d-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="9279d-121">如需有關預設組態和無名稱繫結和行為的詳細資訊，請參閱 < [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md)並[Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="9279d-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="9279d-122"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="9279d-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="9279d-123">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="9279d-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9279d-124">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="9279d-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="9279d-125"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="9279d-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="9279d-126">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="9279d-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9279d-127">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="9279d-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="9279d-128"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="9279d-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="9279d-129">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="9279d-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9279d-130">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="9279d-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9279d-131">子元素</span><span class="sxs-lookup"><span data-stu-id="9279d-131">Child Elements</span></span>  
 <span data-ttu-id="9279d-132">無。</span><span class="sxs-lookup"><span data-stu-id="9279d-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9279d-133">父項目</span><span class="sxs-lookup"><span data-stu-id="9279d-133">Parent Elements</span></span>  
  
|<span data-ttu-id="9279d-134">項目</span><span class="sxs-lookup"><span data-stu-id="9279d-134">Element</span></span>|<span data-ttu-id="9279d-135">描述</span><span class="sxs-lookup"><span data-stu-id="9279d-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9279d-136">\<bindings></span><span class="sxs-lookup"><span data-stu-id="9279d-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="9279d-137">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="9279d-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9279d-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9279d-138">See also</span></span>
- <xref:System.ServiceModel.Configuration.MexTcpBindingElement>
- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>
- [<span data-ttu-id="9279d-139">如何：發行服務，使用組態檔的中繼資料</span><span class="sxs-lookup"><span data-stu-id="9279d-139">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="9279d-140">發行與擷取自訂繫結上的中繼資料</span><span class="sxs-lookup"><span data-stu-id="9279d-140">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="9279d-141">中繼資料</span><span class="sxs-lookup"><span data-stu-id="9279d-141">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="9279d-142">繫結</span><span class="sxs-lookup"><span data-stu-id="9279d-142">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="9279d-143">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="9279d-143">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9279d-144">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="9279d-144">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="9279d-145">\<binding></span><span class="sxs-lookup"><span data-stu-id="9279d-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
