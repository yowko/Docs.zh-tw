---
title: <mexTcpBinding>
ms.date: 03/30/2017
ms.assetid: 01baba8d-d784-4255-9ea2-7afff1482bf0
ms.openlocfilehash: d77809ae87a28995b3f37848e19ebddd24942f22
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397760"
---
# <a name="mextcpbinding"></a><span data-ttu-id="14993-101">\<mexTcpBinding></span><span class="sxs-lookup"><span data-stu-id="14993-101">\<mexTcpBinding></span></span>
<span data-ttu-id="14993-102">指定用於 TCP 上 WS-MetadataExchange (WS-MEX) 訊息交換之繫結的設定。</span><span class="sxs-lookup"><span data-stu-id="14993-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
<span data-ttu-id="14993-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="14993-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="14993-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="14993-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="14993-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="14993-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="14993-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexTcpBinding >**</span><span class="sxs-lookup"><span data-stu-id="14993-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexTcpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14993-107">語法</span><span class="sxs-lookup"><span data-stu-id="14993-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14993-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="14993-108">Attributes and Elements</span></span>  
 <span data-ttu-id="14993-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="14993-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14993-110">屬性</span><span class="sxs-lookup"><span data-stu-id="14993-110">Attributes</span></span>  
  
|<span data-ttu-id="14993-111">屬性</span><span class="sxs-lookup"><span data-stu-id="14993-111">Attribute</span></span>|<span data-ttu-id="14993-112">描述</span><span class="sxs-lookup"><span data-stu-id="14993-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="14993-113"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="14993-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="14993-114">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="14993-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="14993-115">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="14993-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="14993-116">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="14993-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="14993-117">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="14993-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="14993-118">每一個繫結都有一個 `name` 和 `namespace` 屬性，兩者結合在一起便可在服務的中繼資料中唯一識別各個繫結。</span><span class="sxs-lookup"><span data-stu-id="14993-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="14993-119">此外，這個名稱在相同型別的繫結中也是唯一的。</span><span class="sxs-lookup"><span data-stu-id="14993-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="14993-120">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="14993-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="14993-121">如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="14993-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="14993-122"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="14993-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="14993-123">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="14993-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="14993-124">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="14993-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="14993-125"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="14993-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="14993-126">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="14993-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="14993-127">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="14993-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="14993-128"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="14993-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="14993-129">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="14993-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="14993-130">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="14993-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="14993-131">子元素</span><span class="sxs-lookup"><span data-stu-id="14993-131">Child Elements</span></span>  
 <span data-ttu-id="14993-132">無。</span><span class="sxs-lookup"><span data-stu-id="14993-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="14993-133">父項目</span><span class="sxs-lookup"><span data-stu-id="14993-133">Parent Elements</span></span>  
  
|<span data-ttu-id="14993-134">項目</span><span class="sxs-lookup"><span data-stu-id="14993-134">Element</span></span>|<span data-ttu-id="14993-135">說明</span><span class="sxs-lookup"><span data-stu-id="14993-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14993-136">\<bindings></span><span class="sxs-lookup"><span data-stu-id="14993-136">\<bindings></span></span>](bindings.md)|<span data-ttu-id="14993-137">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="14993-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="14993-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="14993-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.MexTcpBindingElement>
- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>
- [<span data-ttu-id="14993-139">如何：使用設定檔發佈服務的中繼資料</span><span class="sxs-lookup"><span data-stu-id="14993-139">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="14993-140">發行與擷取自訂繫結上的中繼資料</span><span class="sxs-lookup"><span data-stu-id="14993-140">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="14993-141">中繼資料</span><span class="sxs-lookup"><span data-stu-id="14993-141">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="14993-142">繫結</span><span class="sxs-lookup"><span data-stu-id="14993-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="14993-143">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="14993-143">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="14993-144">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="14993-144">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="14993-145">\<binding></span><span class="sxs-lookup"><span data-stu-id="14993-145">\<binding></span></span>](../../../misc/binding.md)
