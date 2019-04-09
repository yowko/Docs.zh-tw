---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 4e96c28ac9b372092d06538d24d165dde6c5fe48
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59203128"
---
# <a name="mexhttpsbinding"></a><span data-ttu-id="e557d-101">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="e557d-101">\<mexHttpsBinding></span></span>
<span data-ttu-id="e557d-102">指定用於 HTTPS 上 WS-MetadataExchange (WS-MEX) 訊息交換之繫結的設定。</span><span class="sxs-lookup"><span data-stu-id="e557d-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
 <span data-ttu-id="e557d-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e557d-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="e557d-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="e557d-104">\<bindings></span></span>  
<span data-ttu-id="e557d-105">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="e557d-105">\<mexHttpsBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e557d-106">語法</span><span class="sxs-lookup"><span data-stu-id="e557d-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e557d-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e557d-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e557d-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e557d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e557d-109">屬性</span><span class="sxs-lookup"><span data-stu-id="e557d-109">Attributes</span></span>  
  
|<span data-ttu-id="e557d-110">屬性</span><span class="sxs-lookup"><span data-stu-id="e557d-110">Attribute</span></span>|<span data-ttu-id="e557d-111">描述</span><span class="sxs-lookup"><span data-stu-id="e557d-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="e557d-112"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="e557d-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="e557d-113">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="e557d-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e557d-114">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="e557d-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="e557d-115">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="e557d-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="e557d-116">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="e557d-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="e557d-117">每一個繫結都有一個 `name` 和 `namespace` 屬性，兩者結合在一起便可在服務的中繼資料中唯一識別各個繫結。</span><span class="sxs-lookup"><span data-stu-id="e557d-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="e557d-118">此外，這個名稱在相同型別的繫結中也是唯一的。</span><span class="sxs-lookup"><span data-stu-id="e557d-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="e557d-119">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="e557d-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="e557d-120">如需有關預設組態和無名稱繫結和行為的詳細資訊，請參閱 < [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md)並[Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e557d-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="e557d-121"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="e557d-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="e557d-122">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="e557d-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e557d-123">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="e557d-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="e557d-124"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="e557d-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="e557d-125">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="e557d-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e557d-126">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="e557d-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="e557d-127"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="e557d-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="e557d-128">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="e557d-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="e557d-129">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="e557d-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e557d-130">子元素</span><span class="sxs-lookup"><span data-stu-id="e557d-130">Child Elements</span></span>  
 <span data-ttu-id="e557d-131">無。</span><span class="sxs-lookup"><span data-stu-id="e557d-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e557d-132">父項目</span><span class="sxs-lookup"><span data-stu-id="e557d-132">Parent Elements</span></span>  
  
|<span data-ttu-id="e557d-133">項目</span><span class="sxs-lookup"><span data-stu-id="e557d-133">Element</span></span>|<span data-ttu-id="e557d-134">描述</span><span class="sxs-lookup"><span data-stu-id="e557d-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e557d-135">\<bindings></span><span class="sxs-lookup"><span data-stu-id="e557d-135">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="e557d-136">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="e557d-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e557d-137">備註</span><span class="sxs-lookup"><span data-stu-id="e557d-137">Remarks</span></span>  
 <span data-ttu-id="e557d-138">這個繫結實質上為 `WSHttpBinding` 繫結，其支援使用憑證的傳輸層級安全性。</span><span class="sxs-lookup"><span data-stu-id="e557d-138">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="e557d-139">如需有關設定和使用這類中繼資料端點的詳細資訊，請參閱[How to:設定自訂 Ws-metadata Exchange 繫結](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)， [How to:擷取透過非 MEX 繫結中繼資料](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)，和範例[自訂安全中繼資料端點](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)。</span><span class="sxs-lookup"><span data-stu-id="e557d-139">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e557d-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e557d-140">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="e557d-141">HOW TO：使用組態檔發行服務的中繼資料</span><span class="sxs-lookup"><span data-stu-id="e557d-141">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="e557d-142">發行與擷取自訂繫結上的中繼資料</span><span class="sxs-lookup"><span data-stu-id="e557d-142">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="e557d-143">HOW TO：設定自訂 WS-Metadata Exchange 繫結</span><span class="sxs-lookup"><span data-stu-id="e557d-143">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="e557d-144">HOW TO：透過非 MEX 繫結擷取中繼資料</span><span class="sxs-lookup"><span data-stu-id="e557d-144">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="e557d-145">自訂安全中繼資料端點</span><span class="sxs-lookup"><span data-stu-id="e557d-145">Custom Secure Metadata Endpoint</span></span>](../../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="e557d-146">中繼資料</span><span class="sxs-lookup"><span data-stu-id="e557d-146">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="e557d-147">繫結</span><span class="sxs-lookup"><span data-stu-id="e557d-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="e557d-148">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="e557d-148">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="e557d-149">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="e557d-149">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="e557d-150">\<binding></span><span class="sxs-lookup"><span data-stu-id="e557d-150">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
