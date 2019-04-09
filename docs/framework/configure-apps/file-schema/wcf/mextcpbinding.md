---
title: <mexTcpBinding>
ms.date: 03/30/2017
ms.assetid: 01baba8d-d784-4255-9ea2-7afff1482bf0
ms.openlocfilehash: 9e76d65a27e7732d1d62c4ba25afac76d73be167
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078885"
---
# <a name="mextcpbinding"></a><span data-ttu-id="060e5-101">\<mexTcpBinding></span><span class="sxs-lookup"><span data-stu-id="060e5-101">\<mexTcpBinding></span></span>
<span data-ttu-id="060e5-102">指定用於 TCP 上 WS-MetadataExchange (WS-MEX) 訊息交換之繫結的設定。</span><span class="sxs-lookup"><span data-stu-id="060e5-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
 <span data-ttu-id="060e5-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="060e5-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="060e5-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="060e5-104">\<bindings></span></span>  
<span data-ttu-id="060e5-105">\<mexTcpBinding></span><span class="sxs-lookup"><span data-stu-id="060e5-105">\<mexTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="060e5-106">語法</span><span class="sxs-lookup"><span data-stu-id="060e5-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="060e5-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="060e5-107">Attributes and Elements</span></span>  
 <span data-ttu-id="060e5-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="060e5-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="060e5-109">屬性</span><span class="sxs-lookup"><span data-stu-id="060e5-109">Attributes</span></span>  
  
|<span data-ttu-id="060e5-110">屬性</span><span class="sxs-lookup"><span data-stu-id="060e5-110">Attribute</span></span>|<span data-ttu-id="060e5-111">描述</span><span class="sxs-lookup"><span data-stu-id="060e5-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="060e5-112"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="060e5-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="060e5-113">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="060e5-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="060e5-114">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="060e5-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="060e5-115">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="060e5-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="060e5-116">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="060e5-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="060e5-117">每一個繫結都有一個 `name` 和 `namespace` 屬性，兩者結合在一起便可在服務的中繼資料中唯一識別各個繫結。</span><span class="sxs-lookup"><span data-stu-id="060e5-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="060e5-118">此外，這個名稱在相同型別的繫結中也是唯一的。</span><span class="sxs-lookup"><span data-stu-id="060e5-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="060e5-119">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="060e5-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="060e5-120">如需有關預設組態和無名稱繫結和行為的詳細資訊，請參閱 < [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md)並[Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="060e5-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="060e5-121"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="060e5-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="060e5-122">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="060e5-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="060e5-123">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="060e5-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="060e5-124"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="060e5-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="060e5-125">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="060e5-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="060e5-126">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="060e5-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="060e5-127"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="060e5-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="060e5-128">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="060e5-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="060e5-129">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="060e5-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="060e5-130">子元素</span><span class="sxs-lookup"><span data-stu-id="060e5-130">Child Elements</span></span>  
 <span data-ttu-id="060e5-131">無。</span><span class="sxs-lookup"><span data-stu-id="060e5-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="060e5-132">父項目</span><span class="sxs-lookup"><span data-stu-id="060e5-132">Parent Elements</span></span>  
  
|<span data-ttu-id="060e5-133">項目</span><span class="sxs-lookup"><span data-stu-id="060e5-133">Element</span></span>|<span data-ttu-id="060e5-134">描述</span><span class="sxs-lookup"><span data-stu-id="060e5-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="060e5-135">\<bindings></span><span class="sxs-lookup"><span data-stu-id="060e5-135">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="060e5-136">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="060e5-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="060e5-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="060e5-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.MexTcpBindingElement>
- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>
- [<span data-ttu-id="060e5-138">HOW TO：使用組態檔發行服務的中繼資料</span><span class="sxs-lookup"><span data-stu-id="060e5-138">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="060e5-139">發行與擷取自訂繫結上的中繼資料</span><span class="sxs-lookup"><span data-stu-id="060e5-139">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="060e5-140">中繼資料</span><span class="sxs-lookup"><span data-stu-id="060e5-140">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="060e5-141">繫結</span><span class="sxs-lookup"><span data-stu-id="060e5-141">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="060e5-142">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="060e5-142">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="060e5-143">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="060e5-143">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="060e5-144">\<binding></span><span class="sxs-lookup"><span data-stu-id="060e5-144">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
