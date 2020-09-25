---
title: <mexHttpsBinding>
ms.date: 03/30/2017
ms.assetid: f2ed3774-78b9-4a15-b79b-655f1ad68b86
ms.openlocfilehash: 8025f5ed42325963aa4b695890caa5031f6bb6a6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204719"
---
# \<mexHttpsBinding>

<span data-ttu-id="24036-101">指定用於 HTTPS 上 WS-MetadataExchange (WS-MEX) 訊息交換之繫結的設定。</span><span class="sxs-lookup"><span data-stu-id="24036-101">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTPS.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpsBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="24036-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="24036-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24036-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="24036-103">Attributes and Elements</span></span>  

 <span data-ttu-id="24036-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="24036-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24036-105">屬性</span><span class="sxs-lookup"><span data-stu-id="24036-105">Attributes</span></span>  
  
|<span data-ttu-id="24036-106">屬性</span><span class="sxs-lookup"><span data-stu-id="24036-106">Attribute</span></span>|<span data-ttu-id="24036-107">描述</span><span class="sxs-lookup"><span data-stu-id="24036-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="24036-108"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="24036-108">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="24036-109">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="24036-109">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="24036-110">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="24036-110">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="24036-111">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="24036-111">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="24036-112">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="24036-112">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="24036-113">從 .NET Framework 4 開始，系結和行為不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="24036-113">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="24036-114">如需預設設定和無值系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)[的 WCF 服務設定和簡化的](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="24036-114">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="24036-115"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="24036-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="24036-116">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="24036-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="24036-117">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="24036-117">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="24036-118"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="24036-118">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="24036-119">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="24036-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="24036-120">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="24036-120">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="24036-121"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="24036-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="24036-122">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="24036-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="24036-123">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="24036-123">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="24036-124">子元素</span><span class="sxs-lookup"><span data-stu-id="24036-124">Child Elements</span></span>  

 <span data-ttu-id="24036-125">無。</span><span class="sxs-lookup"><span data-stu-id="24036-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="24036-126">父項目</span><span class="sxs-lookup"><span data-stu-id="24036-126">Parent Elements</span></span>  
  
|<span data-ttu-id="24036-127">項目</span><span class="sxs-lookup"><span data-stu-id="24036-127">Element</span></span>|<span data-ttu-id="24036-128">描述</span><span class="sxs-lookup"><span data-stu-id="24036-128">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="24036-129">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="24036-129">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24036-130">備註</span><span class="sxs-lookup"><span data-stu-id="24036-130">Remarks</span></span>  

 <span data-ttu-id="24036-131">這個繫結實質上為 `WSHttpBinding` 繫結，其支援使用憑證的傳輸層級安全性。</span><span class="sxs-lookup"><span data-stu-id="24036-131">This binding is essentially a `WSHttpBinding` binding that supports transport-level security using certificates.</span></span> <span data-ttu-id="24036-132">如需設定和使用此類中繼資料端點的詳細資訊，請參閱 [如何：設定自訂 WS-Metadata Exchange](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)系結、 [如何：透過非 MEX 系結取得中繼資料](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)，以及 [自訂安全中繼資料端點](../../../wcf/samples/custom-secure-metadata-endpoint.md)範例。</span><span class="sxs-lookup"><span data-stu-id="24036-132">For more information about configuring and using such a metadata endpoint, see [How to: Configure a Custom WS-Metadata Exchange Binding](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md), [How to: Retrieve Metadata Over a non-MEX Binding](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md), and the sample [Custom Secure Metadata Endpoint](../../../wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24036-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24036-133">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpsBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpsBindingElement>
- [<span data-ttu-id="24036-134">作法：使用組態檔發行服務的中繼資料</span><span class="sxs-lookup"><span data-stu-id="24036-134">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="24036-135">發行與擷取自訂繫結上的中繼資料</span><span class="sxs-lookup"><span data-stu-id="24036-135">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="24036-136">作法：設定自訂 WS-Metadata Exchange 繫結</span><span class="sxs-lookup"><span data-stu-id="24036-136">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [<span data-ttu-id="24036-137">作法：透過非 MEX 繫結擷取中繼資料</span><span class="sxs-lookup"><span data-stu-id="24036-137">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
- [<span data-ttu-id="24036-138">自訂安全中繼資料端點</span><span class="sxs-lookup"><span data-stu-id="24036-138">Custom Secure Metadata Endpoint</span></span>](../../../wcf/samples/custom-secure-metadata-endpoint.md)
- [<span data-ttu-id="24036-139">中繼資料</span><span class="sxs-lookup"><span data-stu-id="24036-139">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="24036-140">繫結</span><span class="sxs-lookup"><span data-stu-id="24036-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="24036-141">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="24036-141">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="24036-142">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="24036-142">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
