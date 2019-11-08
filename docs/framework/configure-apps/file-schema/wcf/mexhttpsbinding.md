---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 79c3c68d69bf3cf5a018e6cf62f34e5ec2ce0cd5
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738931"
---
# <a name="mexhttpsbinding"></a><span data-ttu-id="0969a-101">\<mexHttpsBinding ></span><span class="sxs-lookup"><span data-stu-id="0969a-101">\<mexHttpsBinding></span></span>
<span data-ttu-id="0969a-102">指定用於 HTTPS 上 WS-MetadataExchange (WS-MEX) 訊息交換之繫結的設定。</span><span class="sxs-lookup"><span data-stu-id="0969a-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
<span data-ttu-id="0969a-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0969a-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0969a-104">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="0969a-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0969a-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="0969a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="0969a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexHttpsBinding >**</span><span class="sxs-lookup"><span data-stu-id="0969a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpsBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0969a-107">語法</span><span class="sxs-lookup"><span data-stu-id="0969a-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0969a-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0969a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0969a-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0969a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0969a-110">屬性</span><span class="sxs-lookup"><span data-stu-id="0969a-110">Attributes</span></span>  
  
|<span data-ttu-id="0969a-111">屬性</span><span class="sxs-lookup"><span data-stu-id="0969a-111">Attribute</span></span>|<span data-ttu-id="0969a-112">描述</span><span class="sxs-lookup"><span data-stu-id="0969a-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="0969a-113"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="0969a-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="0969a-114">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="0969a-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0969a-115">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="0969a-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="0969a-116">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="0969a-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="0969a-117">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="0969a-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="0969a-118">每一個繫結都有一個 `name` 和 `namespace` 屬性，兩者結合在一起便可在服務的中繼資料中唯一識別各個繫結。</span><span class="sxs-lookup"><span data-stu-id="0969a-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="0969a-119">此外，這個名稱在相同型別的繫結中也是唯一的。</span><span class="sxs-lookup"><span data-stu-id="0969a-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="0969a-120">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="0969a-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="0969a-121">如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="0969a-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="0969a-122"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="0969a-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="0969a-123">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="0969a-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0969a-124">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="0969a-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="0969a-125"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="0969a-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="0969a-126">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="0969a-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0969a-127">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="0969a-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="0969a-128"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="0969a-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="0969a-129">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="0969a-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0969a-130">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="0969a-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0969a-131">子項目</span><span class="sxs-lookup"><span data-stu-id="0969a-131">Child Elements</span></span>  
 <span data-ttu-id="0969a-132">無。</span><span class="sxs-lookup"><span data-stu-id="0969a-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0969a-133">父項目</span><span class="sxs-lookup"><span data-stu-id="0969a-133">Parent Elements</span></span>  
  
|<span data-ttu-id="0969a-134">項目</span><span class="sxs-lookup"><span data-stu-id="0969a-134">Element</span></span>|<span data-ttu-id="0969a-135">描述</span><span class="sxs-lookup"><span data-stu-id="0969a-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0969a-136">\<bindings ></span><span class="sxs-lookup"><span data-stu-id="0969a-136">\<bindings></span></span>](bindings.md)|<span data-ttu-id="0969a-137">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="0969a-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0969a-138">備註</span><span class="sxs-lookup"><span data-stu-id="0969a-138">Remarks</span></span>  
 <span data-ttu-id="0969a-139">這個繫結實質上為 `WSHttpBinding` 繫結，其支援使用憑證的傳輸層級安全性。</span><span class="sxs-lookup"><span data-stu-id="0969a-139">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="0969a-140">如需有關設定和使用這類中繼資料端點的詳細資訊，請參閱[如何：設定自訂的 WS 中繼資料交換](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)系結、[如何：透過非 MEX 系結捕獲中繼資料](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)和範例[自訂安全中繼資料端點](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="0969a-140">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0969a-141">請參閱</span><span class="sxs-lookup"><span data-stu-id="0969a-141">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="0969a-142">如何：使用組態檔發行服務的中繼資料</span><span class="sxs-lookup"><span data-stu-id="0969a-142">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="0969a-143">發行與擷取自訂繫結上的中繼資料</span><span class="sxs-lookup"><span data-stu-id="0969a-143">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="0969a-144">如何：設定自訂 WS-Metadata Exchange 繫結</span><span class="sxs-lookup"><span data-stu-id="0969a-144">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="0969a-145">如何：透過非 MEX 繫結擷取中繼資料</span><span class="sxs-lookup"><span data-stu-id="0969a-145">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="0969a-146">自訂安全中繼資料端點</span><span class="sxs-lookup"><span data-stu-id="0969a-146">Custom Secure Metadata Endpoint</span></span>](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="0969a-147">中繼資料</span><span class="sxs-lookup"><span data-stu-id="0969a-147">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="0969a-148">繫結</span><span class="sxs-lookup"><span data-stu-id="0969a-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0969a-149">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="0969a-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0969a-150">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="0969a-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="0969a-151">\<binding ></span><span class="sxs-lookup"><span data-stu-id="0969a-151">\<binding></span></span>](bindings.md)
