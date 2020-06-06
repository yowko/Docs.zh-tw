---
title: <mexTcpBinding>
ms.date: 03/30/2017
ms.assetid: 01baba8d-d784-4255-9ea2-7afff1482bf0
ms.openlocfilehash: 8d0ae2a1848eaf28c2e408542b8209cf968de4c1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "74430299"
---
# \<mexTcpBinding>
<span data-ttu-id="fb301-101">指定用於 TCP 上 WS-MetadataExchange (WS-MEX) 訊息交換之繫結的設定。</span><span class="sxs-lookup"><span data-stu-id="fb301-101">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexTcpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="fb301-102">語法</span><span class="sxs-lookup"><span data-stu-id="fb301-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fb301-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fb301-103">Attributes and Elements</span></span>  
 <span data-ttu-id="fb301-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="fb301-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fb301-105">屬性</span><span class="sxs-lookup"><span data-stu-id="fb301-105">Attributes</span></span>  
  
|<span data-ttu-id="fb301-106">屬性</span><span class="sxs-lookup"><span data-stu-id="fb301-106">Attribute</span></span>|<span data-ttu-id="fb301-107">描述</span><span class="sxs-lookup"><span data-stu-id="fb301-107">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="fb301-108"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="fb301-108">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="fb301-109">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="fb301-109">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="fb301-110">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="fb301-110">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="fb301-111">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="fb301-111">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="fb301-112">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="fb301-112">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="fb301-113">從 .NET Framework 4 開始，系結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="fb301-113">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="fb301-114">如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="fb301-114">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="fb301-115"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="fb301-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="fb301-116">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="fb301-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="fb301-117">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="fb301-117">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="fb301-118"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="fb301-118">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="fb301-119">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="fb301-119">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="fb301-120">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="fb301-120">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="fb301-121"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="fb301-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="fb301-122">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="fb301-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="fb301-123">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="fb301-123">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fb301-124">子元素</span><span class="sxs-lookup"><span data-stu-id="fb301-124">Child Elements</span></span>  
 <span data-ttu-id="fb301-125">無。</span><span class="sxs-lookup"><span data-stu-id="fb301-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fb301-126">父項目</span><span class="sxs-lookup"><span data-stu-id="fb301-126">Parent Elements</span></span>  
  
|<span data-ttu-id="fb301-127">元素</span><span class="sxs-lookup"><span data-stu-id="fb301-127">Element</span></span>|<span data-ttu-id="fb301-128">描述</span><span class="sxs-lookup"><span data-stu-id="fb301-128">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="fb301-129">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="fb301-129">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fb301-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb301-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.MexTcpBindingElement>
- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>
- [<span data-ttu-id="fb301-131">HOW TO：使用組態檔發行服務的中繼資料</span><span class="sxs-lookup"><span data-stu-id="fb301-131">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="fb301-132">發行與擷取自訂繫結上的中繼資料</span><span class="sxs-lookup"><span data-stu-id="fb301-132">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="fb301-133">中繼資料</span><span class="sxs-lookup"><span data-stu-id="fb301-133">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="fb301-134">繫結</span><span class="sxs-lookup"><span data-stu-id="fb301-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="fb301-135">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="fb301-135">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="fb301-136">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="fb301-136">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
