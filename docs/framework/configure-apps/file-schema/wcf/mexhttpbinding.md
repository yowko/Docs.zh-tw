---
title: <mexHttpBinding>
ms.date: 03/30/2017
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
ms.openlocfilehash: 1aa9512c3d0d52f8cc3c7bd7b82bcfd37c418ce7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59151238"
---
# <a name="mexhttpbinding"></a><span data-ttu-id="25904-101">\<mexHttpBinding></span><span class="sxs-lookup"><span data-stu-id="25904-101">\<mexHttpBinding></span></span>
<span data-ttu-id="25904-102">指定用於 HTTP 上 WS-MetadataExchange (WS-MEX) 訊息交換之繫結的設定。</span><span class="sxs-lookup"><span data-stu-id="25904-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
 <span data-ttu-id="25904-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="25904-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="25904-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="25904-104">\<bindings></span></span>  
<span data-ttu-id="25904-105">\<mexHttpBinding></span><span class="sxs-lookup"><span data-stu-id="25904-105">\<mexHttpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25904-106">語法</span><span class="sxs-lookup"><span data-stu-id="25904-106">Syntax</span></span>  
  
```xml  
<mexHttpBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25904-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="25904-107">Attributes and Elements</span></span>  
 <span data-ttu-id="25904-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="25904-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25904-109">屬性</span><span class="sxs-lookup"><span data-stu-id="25904-109">Attributes</span></span>  
  
|<span data-ttu-id="25904-110">屬性</span><span class="sxs-lookup"><span data-stu-id="25904-110">Attribute</span></span>|<span data-ttu-id="25904-111">描述</span><span class="sxs-lookup"><span data-stu-id="25904-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="25904-112"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="25904-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="25904-113">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="25904-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="25904-114">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="25904-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="25904-115">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="25904-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="25904-116">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="25904-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="25904-117">每一個繫結都有一個 `name` 和 `namespace` 屬性，兩者結合在一起便可在服務的中繼資料中唯一識別各個繫結。</span><span class="sxs-lookup"><span data-stu-id="25904-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="25904-118">此外，這個名稱在相同型別的繫結中也是唯一的。</span><span class="sxs-lookup"><span data-stu-id="25904-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="25904-119">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="25904-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="25904-120">如需有關預設組態和無名稱繫結和行為的詳細資訊，請參閱 < [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md)並[Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="25904-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="25904-121"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="25904-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="25904-122">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="25904-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="25904-123">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="25904-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="25904-124"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="25904-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="25904-125">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="25904-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="25904-126">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="25904-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="25904-127"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="25904-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="25904-128">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="25904-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="25904-129">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="25904-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="25904-130">子元素</span><span class="sxs-lookup"><span data-stu-id="25904-130">Child Elements</span></span>  
 <span data-ttu-id="25904-131">無。</span><span class="sxs-lookup"><span data-stu-id="25904-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="25904-132">父項目</span><span class="sxs-lookup"><span data-stu-id="25904-132">Parent Elements</span></span>  
  
|<span data-ttu-id="25904-133">項目</span><span class="sxs-lookup"><span data-stu-id="25904-133">Element</span></span>|<span data-ttu-id="25904-134">描述</span><span class="sxs-lookup"><span data-stu-id="25904-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="25904-135">\<bindings></span><span class="sxs-lookup"><span data-stu-id="25904-135">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="25904-136">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="25904-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25904-137">備註</span><span class="sxs-lookup"><span data-stu-id="25904-137">Remarks</span></span>  
 <span data-ttu-id="25904-138">這個繫結實質上是停用安全性的 `WSHttpBinding` 繫結。</span><span class="sxs-lookup"><span data-stu-id="25904-138">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="25904-139">它支援大部分的中繼資料要求。</span><span class="sxs-lookup"><span data-stu-id="25904-139">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25904-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25904-140">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpBindingElement>
- [<span data-ttu-id="25904-141">如何：發行服務，使用組態檔的中繼資料</span><span class="sxs-lookup"><span data-stu-id="25904-141">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="25904-142">發行與擷取自訂繫結上的中繼資料</span><span class="sxs-lookup"><span data-stu-id="25904-142">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="25904-143">中繼資料</span><span class="sxs-lookup"><span data-stu-id="25904-143">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="25904-144">繫結</span><span class="sxs-lookup"><span data-stu-id="25904-144">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="25904-145">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="25904-145">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="25904-146">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="25904-146">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="25904-147">\<binding></span><span class="sxs-lookup"><span data-stu-id="25904-147">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
