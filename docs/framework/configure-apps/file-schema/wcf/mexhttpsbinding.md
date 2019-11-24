---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 924d68dd828622b74c5e424a695f80874391b453
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430334"
---
# <a name="mexhttpsbinding"></a><span data-ttu-id="0d50a-101">\<mexHttpsBinding></span><span class="sxs-lookup"><span data-stu-id="0d50a-101">\<mexHttpsBinding></span></span>
<span data-ttu-id="0d50a-102">指定用於 HTTPS 上 WS-MetadataExchange (WS-MEX) 訊息交換之繫結的設定。</span><span class="sxs-lookup"><span data-stu-id="0d50a-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
<span data-ttu-id="0d50a-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0d50a-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0d50a-104">&nbsp;&nbsp;[ **\<system.serviceModel>** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="0d50a-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="0d50a-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bindings>** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="0d50a-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="0d50a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexHttpsBinding>**</span><span class="sxs-lookup"><span data-stu-id="0d50a-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpsBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d50a-107">語法</span><span class="sxs-lookup"><span data-stu-id="0d50a-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d50a-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0d50a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0d50a-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0d50a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d50a-110">屬性</span><span class="sxs-lookup"><span data-stu-id="0d50a-110">Attributes</span></span>  
  
|<span data-ttu-id="0d50a-111">屬性</span><span class="sxs-lookup"><span data-stu-id="0d50a-111">Attribute</span></span>|<span data-ttu-id="0d50a-112">描述</span><span class="sxs-lookup"><span data-stu-id="0d50a-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="0d50a-113"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="0d50a-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="0d50a-114">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="0d50a-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0d50a-115">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="0d50a-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="0d50a-116">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="0d50a-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="0d50a-117">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="0d50a-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="0d50a-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span><span class="sxs-lookup"><span data-stu-id="0d50a-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="0d50a-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="0d50a-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="0d50a-120"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="0d50a-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="0d50a-121">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="0d50a-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0d50a-122">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="0d50a-122">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="0d50a-123"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="0d50a-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="0d50a-124">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="0d50a-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0d50a-125">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="0d50a-125">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="0d50a-126"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="0d50a-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="0d50a-127">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="0d50a-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="0d50a-128">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="0d50a-128">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d50a-129">子項目</span><span class="sxs-lookup"><span data-stu-id="0d50a-129">Child Elements</span></span>  
 <span data-ttu-id="0d50a-130">無。</span><span class="sxs-lookup"><span data-stu-id="0d50a-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0d50a-131">父項目</span><span class="sxs-lookup"><span data-stu-id="0d50a-131">Parent Elements</span></span>  
  
|<span data-ttu-id="0d50a-132">項目</span><span class="sxs-lookup"><span data-stu-id="0d50a-132">Element</span></span>|<span data-ttu-id="0d50a-133">描述</span><span class="sxs-lookup"><span data-stu-id="0d50a-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d50a-134">\<bindings></span><span class="sxs-lookup"><span data-stu-id="0d50a-134">\<bindings></span></span>](bindings.md)|<span data-ttu-id="0d50a-135">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="0d50a-135">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d50a-136">備註</span><span class="sxs-lookup"><span data-stu-id="0d50a-136">Remarks</span></span>  
 <span data-ttu-id="0d50a-137">這個繫結實質上為 `WSHttpBinding` 繫結，其支援使用憑證的傳輸層級安全性。</span><span class="sxs-lookup"><span data-stu-id="0d50a-137">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="0d50a-138">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="0d50a-138">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d50a-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="0d50a-139">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="0d50a-140">如何：使用組態檔發行服務的中繼資料</span><span class="sxs-lookup"><span data-stu-id="0d50a-140">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="0d50a-141">發行與擷取自訂繫結上的中繼資料</span><span class="sxs-lookup"><span data-stu-id="0d50a-141">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="0d50a-142">如何：設定自訂 WS-Metadata Exchange 繫結</span><span class="sxs-lookup"><span data-stu-id="0d50a-142">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="0d50a-143">如何：透過非 MEX 繫結擷取中繼資料</span><span class="sxs-lookup"><span data-stu-id="0d50a-143">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="0d50a-144">自訂安全中繼資料端點</span><span class="sxs-lookup"><span data-stu-id="0d50a-144">Custom Secure Metadata Endpoint</span></span>](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="0d50a-145">中繼資料</span><span class="sxs-lookup"><span data-stu-id="0d50a-145">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="0d50a-146">繫結</span><span class="sxs-lookup"><span data-stu-id="0d50a-146">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0d50a-147">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="0d50a-147">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0d50a-148">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="0d50a-148">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="0d50a-149">\<binding></span><span class="sxs-lookup"><span data-stu-id="0d50a-149">\<binding></span></span>](bindings.md)
