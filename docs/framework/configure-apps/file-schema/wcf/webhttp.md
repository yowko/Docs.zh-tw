---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 00644d248e6fb85d7cf712620e6ac74405e6b0c3
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399156"
---
# <a name="webhttp"></a><span data-ttu-id="f63b3-101">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="f63b3-101">\<webHttp></span></span>
<span data-ttu-id="f63b3-102">此項目透過組態指定端點上的 <xref:System.ServiceModel.Description.WebHttpBehavior>。</span><span class="sxs-lookup"><span data-stu-id="f63b3-102">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="f63b3-103">這個行為與[ \<webHttpBinding >](webhttpbinding.md)標準系結搭配使用時，會啟用 Windows Communication Foundation （WCF）服務的 Web 程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="f63b3-103">This behavior, when used in conjunction with the [\<webHttpBinding>](webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
<span data-ttu-id="f63b3-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f63b3-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f63b3-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f63b3-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f63b3-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f63b3-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="f63b3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f63b3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="f63b3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f63b3-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="f63b3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webHttp >**</span><span class="sxs-lookup"><span data-stu-id="f63b3-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttp>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f63b3-110">語法</span><span class="sxs-lookup"><span data-stu-id="f63b3-110">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f63b3-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f63b3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f63b3-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f63b3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f63b3-113">屬性</span><span class="sxs-lookup"><span data-stu-id="f63b3-113">Attributes</span></span>  
  
|<span data-ttu-id="f63b3-114">屬性</span><span class="sxs-lookup"><span data-stu-id="f63b3-114">Attribute</span></span>|<span data-ttu-id="f63b3-115">描述</span><span class="sxs-lookup"><span data-stu-id="f63b3-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f63b3-116">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="f63b3-116">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="f63b3-117">當此屬性設定為 `true` 時，WCF 基礎結構會判斷要使用的最佳格式。</span><span class="sxs-lookup"><span data-stu-id="f63b3-117">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="f63b3-118">為了提供回溯相容性，自動格式選取預設為停用。</span><span class="sxs-lookup"><span data-stu-id="f63b3-118">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="f63b3-119">自動格式選取可以透過程式設計方式或透過組態啟用。</span><span class="sxs-lookup"><span data-stu-id="f63b3-119">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="f63b3-120">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="f63b3-120">defaultBodyStyle</span></span>|<span data-ttu-id="f63b3-121">指定傳回訊息的預設本文樣式。</span><span class="sxs-lookup"><span data-stu-id="f63b3-121">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="f63b3-122">如需詳細資訊， <xref:System.ServiceModel.Web.WebMessageBodyStyle>請參閱和[WCF Web HTTP 格式](../../../wcf/feature-details/wcf-web-http-formatting.md)。</span><span class="sxs-lookup"><span data-stu-id="f63b3-122">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="f63b3-123">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="f63b3-123">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="f63b3-124">指定訊息的預設傳出回應格式。</span><span class="sxs-lookup"><span data-stu-id="f63b3-124">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="f63b3-125">如需詳細資訊，請參閱[WCF WEB HTTP 格式](../../../wcf/feature-details/wcf-web-http-formatting.md)。</span><span class="sxs-lookup"><span data-stu-id="f63b3-125">For more information, see [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="f63b3-126">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="f63b3-126">faultExceptionEnabled</span></span>|<span data-ttu-id="f63b3-127">取得或設定旗標，指定是否要在內部伺服器錯誤 (HTTP 狀態碼：500) 發生時產生 FaultException。</span><span class="sxs-lookup"><span data-stu-id="f63b3-127">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="f63b3-128">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="f63b3-128">helpEnabled</span></span>|<span data-ttu-id="f63b3-129">取得或設定值，這個值會判斷是否已啟用說明頁面。</span><span class="sxs-lookup"><span data-stu-id="f63b3-129">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f63b3-130">子元素</span><span class="sxs-lookup"><span data-stu-id="f63b3-130">Child Elements</span></span>  
 <span data-ttu-id="f63b3-131">無。</span><span class="sxs-lookup"><span data-stu-id="f63b3-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f63b3-132">父項目</span><span class="sxs-lookup"><span data-stu-id="f63b3-132">Parent Elements</span></span>  
  
|<span data-ttu-id="f63b3-133">項目</span><span class="sxs-lookup"><span data-stu-id="f63b3-133">Element</span></span>|<span data-ttu-id="f63b3-134">描述</span><span class="sxs-lookup"><span data-stu-id="f63b3-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f63b3-135">\<behavior></span><span class="sxs-lookup"><span data-stu-id="f63b3-135">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="f63b3-136">指定端點行為組。</span><span class="sxs-lookup"><span data-stu-id="f63b3-136">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f63b3-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f63b3-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="f63b3-138">AJAX 整合與 JSON 支援</span><span class="sxs-lookup"><span data-stu-id="f63b3-138">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="f63b3-139">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="f63b3-139">\<webHttpBinding></span></span>](webhttpbinding.md)
