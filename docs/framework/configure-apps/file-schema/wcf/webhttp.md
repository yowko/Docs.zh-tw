---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: ca6d401109d14ce11dcd40c393cd079170e4d20d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259862"
---
# <a name="webhttp"></a><span data-ttu-id="bc1d0-101">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="bc1d0-101">\<webHttp></span></span>
<span data-ttu-id="bc1d0-102">此項目透過組態指定端點上的 <xref:System.ServiceModel.Description.WebHttpBehavior>。</span><span class="sxs-lookup"><span data-stu-id="bc1d0-102">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="bc1d0-103">這項行為，當搭配[ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)標準繫結，可讓 Windows Communication Foundation (WCF) 服務的 Web 程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="bc1d0-103">This behavior, when used in conjunction with the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="bc1d0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bc1d0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="bc1d0-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="bc1d0-105">\<behaviors></span></span>  
<span data-ttu-id="bc1d0-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="bc1d0-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="bc1d0-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="bc1d0-107">\<behavior></span></span>  
<span data-ttu-id="bc1d0-108">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="bc1d0-108">\<webHttp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc1d0-109">語法</span><span class="sxs-lookup"><span data-stu-id="bc1d0-109">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc1d0-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bc1d0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bc1d0-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="bc1d0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc1d0-112">屬性</span><span class="sxs-lookup"><span data-stu-id="bc1d0-112">Attributes</span></span>  
  
|<span data-ttu-id="bc1d0-113">屬性</span><span class="sxs-lookup"><span data-stu-id="bc1d0-113">Attribute</span></span>|<span data-ttu-id="bc1d0-114">描述</span><span class="sxs-lookup"><span data-stu-id="bc1d0-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bc1d0-115">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="bc1d0-115">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="bc1d0-116">當此屬性設定為 `true` 時，WCF 基礎結構會判斷要使用的最佳格式。</span><span class="sxs-lookup"><span data-stu-id="bc1d0-116">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="bc1d0-117">為了提供回溯相容性，自動格式選取預設為停用。</span><span class="sxs-lookup"><span data-stu-id="bc1d0-117">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="bc1d0-118">自動格式選取可以透過程式設計方式或透過組態啟用。</span><span class="sxs-lookup"><span data-stu-id="bc1d0-118">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="bc1d0-119">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="bc1d0-119">defaultBodyStyle</span></span>|<span data-ttu-id="bc1d0-120">指定傳回訊息的預設本文樣式。</span><span class="sxs-lookup"><span data-stu-id="bc1d0-120">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="bc1d0-121">如需詳細資訊，請參閱 <<c0> <xref:System.ServiceModel.Web.WebMessageBodyStyle> 並[WCF Web HTTP 格式化](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)。</span><span class="sxs-lookup"><span data-stu-id="bc1d0-121">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="bc1d0-122">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="bc1d0-122">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="bc1d0-123">指定訊息的預設傳出回應格式。</span><span class="sxs-lookup"><span data-stu-id="bc1d0-123">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="bc1d0-124">如需詳細資訊，請參閱 < [WCF Web HTTP 格式化](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)。</span><span class="sxs-lookup"><span data-stu-id="bc1d0-124">For more information, see [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="bc1d0-125">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="bc1d0-125">faultExceptionEnabled</span></span>|<span data-ttu-id="bc1d0-126">取得或設定旗標，指定是否要在內部伺服器錯誤 (HTTP 狀態碼：500) 發生時產生 FaultException。</span><span class="sxs-lookup"><span data-stu-id="bc1d0-126">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="bc1d0-127">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="bc1d0-127">helpEnabled</span></span>|<span data-ttu-id="bc1d0-128">取得或設定值，這個值會判斷是否已啟用說明頁面。</span><span class="sxs-lookup"><span data-stu-id="bc1d0-128">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc1d0-129">子元素</span><span class="sxs-lookup"><span data-stu-id="bc1d0-129">Child Elements</span></span>  
 <span data-ttu-id="bc1d0-130">無。</span><span class="sxs-lookup"><span data-stu-id="bc1d0-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bc1d0-131">父項目</span><span class="sxs-lookup"><span data-stu-id="bc1d0-131">Parent Elements</span></span>  
  
|<span data-ttu-id="bc1d0-132">項目</span><span class="sxs-lookup"><span data-stu-id="bc1d0-132">Element</span></span>|<span data-ttu-id="bc1d0-133">描述</span><span class="sxs-lookup"><span data-stu-id="bc1d0-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc1d0-134">\<behavior></span><span class="sxs-lookup"><span data-stu-id="bc1d0-134">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="bc1d0-135">指定端點行為組。</span><span class="sxs-lookup"><span data-stu-id="bc1d0-135">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bc1d0-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc1d0-136">See also</span></span>
- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="bc1d0-137">AJAX 整合與 JSON 支援</span><span class="sxs-lookup"><span data-stu-id="bc1d0-137">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="bc1d0-138">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="bc1d0-138">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)
