---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 795e61b9054d2ea9276970988018c50099bcbe17
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59129645"
---
# <a name="webhttp"></a><span data-ttu-id="4af12-101">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="4af12-101">\<webHttp></span></span>
<span data-ttu-id="4af12-102">此項目透過組態指定端點上的 <xref:System.ServiceModel.Description.WebHttpBehavior>。</span><span class="sxs-lookup"><span data-stu-id="4af12-102">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="4af12-103">這項行為，當搭配[ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)標準繫結，可讓 Windows Communication Foundation (WCF) 服務的 Web 程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="4af12-103">This behavior, when used in conjunction with the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="4af12-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4af12-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4af12-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="4af12-105">\<behaviors></span></span>  
<span data-ttu-id="4af12-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="4af12-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="4af12-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="4af12-107">\<behavior></span></span>  
<span data-ttu-id="4af12-108">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="4af12-108">\<webHttp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4af12-109">語法</span><span class="sxs-lookup"><span data-stu-id="4af12-109">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4af12-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4af12-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4af12-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4af12-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4af12-112">屬性</span><span class="sxs-lookup"><span data-stu-id="4af12-112">Attributes</span></span>  
  
|<span data-ttu-id="4af12-113">屬性</span><span class="sxs-lookup"><span data-stu-id="4af12-113">Attribute</span></span>|<span data-ttu-id="4af12-114">描述</span><span class="sxs-lookup"><span data-stu-id="4af12-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4af12-115">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="4af12-115">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="4af12-116">當此屬性設定為 `true` 時，WCF 基礎結構會判斷要使用的最佳格式。</span><span class="sxs-lookup"><span data-stu-id="4af12-116">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="4af12-117">為了提供回溯相容性，自動格式選取預設為停用。</span><span class="sxs-lookup"><span data-stu-id="4af12-117">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="4af12-118">自動格式選取可以透過程式設計方式或透過組態啟用。</span><span class="sxs-lookup"><span data-stu-id="4af12-118">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="4af12-119">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="4af12-119">defaultBodyStyle</span></span>|<span data-ttu-id="4af12-120">指定傳回訊息的預設本文樣式。</span><span class="sxs-lookup"><span data-stu-id="4af12-120">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="4af12-121">如需詳細資訊，請參閱 <<c0> <xref:System.ServiceModel.Web.WebMessageBodyStyle> 並[WCF Web HTTP 格式化](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)。</span><span class="sxs-lookup"><span data-stu-id="4af12-121">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="4af12-122">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="4af12-122">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="4af12-123">指定訊息的預設傳出回應格式。</span><span class="sxs-lookup"><span data-stu-id="4af12-123">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="4af12-124">如需詳細資訊，請參閱 < [WCF Web HTTP 格式化](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)。</span><span class="sxs-lookup"><span data-stu-id="4af12-124">For more information, see [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="4af12-125">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="4af12-125">faultExceptionEnabled</span></span>|<span data-ttu-id="4af12-126">取得或設定旗標，指定是否要在內部伺服器錯誤 (HTTP 狀態碼：500) 發生時產生 FaultException。</span><span class="sxs-lookup"><span data-stu-id="4af12-126">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="4af12-127">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="4af12-127">helpEnabled</span></span>|<span data-ttu-id="4af12-128">取得或設定值，這個值會判斷是否已啟用說明頁面。</span><span class="sxs-lookup"><span data-stu-id="4af12-128">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4af12-129">子元素</span><span class="sxs-lookup"><span data-stu-id="4af12-129">Child Elements</span></span>  
 <span data-ttu-id="4af12-130">無。</span><span class="sxs-lookup"><span data-stu-id="4af12-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4af12-131">父項目</span><span class="sxs-lookup"><span data-stu-id="4af12-131">Parent Elements</span></span>  
  
|<span data-ttu-id="4af12-132">項目</span><span class="sxs-lookup"><span data-stu-id="4af12-132">Element</span></span>|<span data-ttu-id="4af12-133">描述</span><span class="sxs-lookup"><span data-stu-id="4af12-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4af12-134">\<behavior></span><span class="sxs-lookup"><span data-stu-id="4af12-134">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="4af12-135">指定端點行為組。</span><span class="sxs-lookup"><span data-stu-id="4af12-135">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4af12-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4af12-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="4af12-137">AJAX 整合與 JSON 支援</span><span class="sxs-lookup"><span data-stu-id="4af12-137">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="4af12-138">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="4af12-138">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)
