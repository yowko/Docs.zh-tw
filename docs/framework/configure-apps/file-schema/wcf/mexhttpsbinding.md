---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 924d68dd828622b74c5e424a695f80874391b453
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "74430334"
---
# \<mexHttpsBinding>
<span data-ttu-id="a65ea-101">指定用於 HTTPS 上 WS-MetadataExchange (WS-MEX) 訊息交換之繫結的設定。</span><span class="sxs-lookup"><span data-stu-id="a65ea-101">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpsBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="a65ea-102">語法</span><span class="sxs-lookup"><span data-stu-id="a65ea-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a65ea-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a65ea-103">Attributes and Elements</span></span>  
 <span data-ttu-id="a65ea-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a65ea-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a65ea-105">屬性</span><span class="sxs-lookup"><span data-stu-id="a65ea-105">Attributes</span></span>  
  
|<span data-ttu-id="a65ea-106">屬性</span><span class="sxs-lookup"><span data-stu-id="a65ea-106">Attribute</span></span>|<span data-ttu-id="a65ea-107">描述</span><span class="sxs-lookup"><span data-stu-id="a65ea-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="a65ea-108"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="a65ea-108">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="a65ea-109">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="a65ea-109">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a65ea-110">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="a65ea-110">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="a65ea-111">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="a65ea-111">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="a65ea-112">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="a65ea-112">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="a65ea-113">從 .NET Framework 4 開始，系結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="a65ea-113">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="a65ea-114">如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="a65ea-114">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="a65ea-115"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="a65ea-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="a65ea-116">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="a65ea-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a65ea-117">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="a65ea-117">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="a65ea-118"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="a65ea-118">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="a65ea-119">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="a65ea-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a65ea-120">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="a65ea-120">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="a65ea-121"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="a65ea-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="a65ea-122">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="a65ea-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="a65ea-123">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="a65ea-123">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a65ea-124">子元素</span><span class="sxs-lookup"><span data-stu-id="a65ea-124">Child Elements</span></span>  
 <span data-ttu-id="a65ea-125">無。</span><span class="sxs-lookup"><span data-stu-id="a65ea-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a65ea-126">父項目</span><span class="sxs-lookup"><span data-stu-id="a65ea-126">Parent Elements</span></span>  
  
|<span data-ttu-id="a65ea-127">元素</span><span class="sxs-lookup"><span data-stu-id="a65ea-127">Element</span></span>|<span data-ttu-id="a65ea-128">描述</span><span class="sxs-lookup"><span data-stu-id="a65ea-128">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="a65ea-129">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="a65ea-129">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a65ea-130">備註</span><span class="sxs-lookup"><span data-stu-id="a65ea-130">Remarks</span></span>  
 <span data-ttu-id="a65ea-131">這個繫結實質上為 `WSHttpBinding` 繫結，其支援使用憑證的傳輸層級安全性。</span><span class="sxs-lookup"><span data-stu-id="a65ea-131">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="a65ea-132">如需有關設定和使用這類中繼資料端點的詳細資訊，請參閱[如何：設定自訂的 WS 中繼資料交換](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)系結、[如何：透過非 MEX 系結捕獲中繼資料](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)和範例[自訂安全中繼資料端點](../../../wcf/samples/custom-secure-metadata-endpoint.md)。</span><span class="sxs-lookup"><span data-stu-id="a65ea-132">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a65ea-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a65ea-133">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="a65ea-134">HOW TO：使用組態檔發行服務的中繼資料</span><span class="sxs-lookup"><span data-stu-id="a65ea-134">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="a65ea-135">發行與擷取自訂繫結上的中繼資料</span><span class="sxs-lookup"><span data-stu-id="a65ea-135">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="a65ea-136">HOW TO：設定自訂 WS-Metadata Exchange 繫結</span><span class="sxs-lookup"><span data-stu-id="a65ea-136">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="a65ea-137">HOW TO：透過非 MEX 繫結擷取中繼資料</span><span class="sxs-lookup"><span data-stu-id="a65ea-137">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="a65ea-138">自訂安全中繼資料端點</span><span class="sxs-lookup"><span data-stu-id="a65ea-138">Custom Secure Metadata Endpoint</span></span>](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="a65ea-139">中繼資料</span><span class="sxs-lookup"><span data-stu-id="a65ea-139">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="a65ea-140">繫結</span><span class="sxs-lookup"><span data-stu-id="a65ea-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a65ea-141">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="a65ea-141">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a65ea-142">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="a65ea-142">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
