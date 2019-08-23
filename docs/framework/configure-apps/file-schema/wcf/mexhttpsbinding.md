---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 30d1aa27ce29b6aa4091c3e7be05746ad462102a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931274"
---
# <a name="mexhttpsbinding"></a><span data-ttu-id="f7d42-101">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="f7d42-101">\<mexHttpsBinding></span></span>
<span data-ttu-id="f7d42-102">指定用於 HTTPS 上 WS-MetadataExchange (WS-MEX) 訊息交換之繫結的設定。</span><span class="sxs-lookup"><span data-stu-id="f7d42-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
 <span data-ttu-id="f7d42-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f7d42-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="f7d42-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="f7d42-104">\<bindings></span></span>  
<span data-ttu-id="f7d42-105">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="f7d42-105">\<mexHttpsBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7d42-106">語法</span><span class="sxs-lookup"><span data-stu-id="f7d42-106">Syntax</span></span>  
  
```xml  
<mexHttpsBinding>
  <binding closeTimeout="TimeSpan"
            name="string"
            openTimeout="TimeSpan"
            receiveTimeout="TimeSpan"
            sendTimeout="TimeSpan">
  </binding>
</mexHttpsBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f7d42-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f7d42-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f7d42-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f7d42-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f7d42-109">屬性</span><span class="sxs-lookup"><span data-stu-id="f7d42-109">Attributes</span></span>  
  
|<span data-ttu-id="f7d42-110">屬性</span><span class="sxs-lookup"><span data-stu-id="f7d42-110">Attribute</span></span>|<span data-ttu-id="f7d42-111">說明</span><span class="sxs-lookup"><span data-stu-id="f7d42-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="f7d42-112"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="f7d42-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="f7d42-113">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="f7d42-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f7d42-114">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="f7d42-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="f7d42-115">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="f7d42-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="f7d42-116">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="f7d42-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="f7d42-117">每一個繫結都有一個 `name` 和 `namespace` 屬性，兩者結合在一起便可在服務的中繼資料中唯一識別各個繫結。</span><span class="sxs-lookup"><span data-stu-id="f7d42-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="f7d42-118">此外，這個名稱在相同型別的繫結中也是唯一的。</span><span class="sxs-lookup"><span data-stu-id="f7d42-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="f7d42-119">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="f7d42-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="f7d42-120">如需預設設定和無相關系結和行為的詳細資訊, 請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="f7d42-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="f7d42-121"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="f7d42-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="f7d42-122">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="f7d42-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f7d42-123">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="f7d42-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="f7d42-124"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="f7d42-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="f7d42-125">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="f7d42-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f7d42-126">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="f7d42-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="f7d42-127"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="f7d42-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="f7d42-128">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="f7d42-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f7d42-129">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="f7d42-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f7d42-130">子元素</span><span class="sxs-lookup"><span data-stu-id="f7d42-130">Child Elements</span></span>  
 <span data-ttu-id="f7d42-131">無。</span><span class="sxs-lookup"><span data-stu-id="f7d42-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f7d42-132">父項目</span><span class="sxs-lookup"><span data-stu-id="f7d42-132">Parent Elements</span></span>  
  
|<span data-ttu-id="f7d42-133">項目</span><span class="sxs-lookup"><span data-stu-id="f7d42-133">Element</span></span>|<span data-ttu-id="f7d42-134">描述</span><span class="sxs-lookup"><span data-stu-id="f7d42-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f7d42-135">\<bindings></span><span class="sxs-lookup"><span data-stu-id="f7d42-135">\<bindings></span></span>](bindings.md)|<span data-ttu-id="f7d42-136">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="f7d42-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7d42-137">備註</span><span class="sxs-lookup"><span data-stu-id="f7d42-137">Remarks</span></span>  
 <span data-ttu-id="f7d42-138">這個繫結實質上為 `WSHttpBinding` 繫結，其支援使用憑證的傳輸層級安全性。</span><span class="sxs-lookup"><span data-stu-id="f7d42-138">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="f7d42-139">如需設定和使用這類中繼資料端點的詳細資訊[, 請參閱如何:設定自訂的 WS 中繼資料交換](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)系[結, how to:透過非 MEX](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)系結取得中繼資料, 以及範例[自訂安全中繼資料端點](../../../wcf/samples/custom-secure-metadata-endpoint.md)。</span><span class="sxs-lookup"><span data-stu-id="f7d42-139">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7d42-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7d42-140">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="f7d42-141">如何：使用設定檔發佈服務的中繼資料</span><span class="sxs-lookup"><span data-stu-id="f7d42-141">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="f7d42-142">發行與擷取自訂繫結上的中繼資料</span><span class="sxs-lookup"><span data-stu-id="f7d42-142">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="f7d42-143">如何：設定自訂的 WS 中繼資料交換系結</span><span class="sxs-lookup"><span data-stu-id="f7d42-143">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="f7d42-144">如何：透過非 MEX 系結取得中繼資料</span><span class="sxs-lookup"><span data-stu-id="f7d42-144">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="f7d42-145">自訂安全中繼資料端點</span><span class="sxs-lookup"><span data-stu-id="f7d42-145">Custom Secure Metadata Endpoint</span></span>](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="f7d42-146">中繼資料</span><span class="sxs-lookup"><span data-stu-id="f7d42-146">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="f7d42-147">繫結</span><span class="sxs-lookup"><span data-stu-id="f7d42-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f7d42-148">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="f7d42-148">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f7d42-149">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="f7d42-149">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="f7d42-150">\<binding></span><span class="sxs-lookup"><span data-stu-id="f7d42-150">\<binding></span></span>](../../../misc/binding.md)
