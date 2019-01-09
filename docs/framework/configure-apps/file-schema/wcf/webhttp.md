---
title: '&lt;webHttp&gt;'
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 9ba54dc1744751efe4efad04f829cccce1244e0d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145666"
---
# <a name="ltwebhttpgt"></a><span data-ttu-id="baa4d-102">&lt;webHttp&gt;</span><span class="sxs-lookup"><span data-stu-id="baa4d-102">&lt;webHttp&gt;</span></span>
<span data-ttu-id="baa4d-103">此項目透過組態指定端點上的 <xref:System.ServiceModel.Description.WebHttpBehavior>。</span><span class="sxs-lookup"><span data-stu-id="baa4d-103">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="baa4d-104">這項行為，當搭配[ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)標準繫結，可讓 Windows Communication Foundation (WCF) 服務的 Web 程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="baa4d-104">This behavior, when used in conjunction with the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="baa4d-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="baa4d-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="baa4d-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="baa4d-106">\<behaviors></span></span>  
<span data-ttu-id="baa4d-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="baa4d-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="baa4d-108">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="baa4d-108">\<behavior></span></span>  
<span data-ttu-id="baa4d-109">\<webHttp ></span><span class="sxs-lookup"><span data-stu-id="baa4d-109">\<webHttp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baa4d-110">語法</span><span class="sxs-lookup"><span data-stu-id="baa4d-110">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="baa4d-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="baa4d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="baa4d-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="baa4d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="baa4d-113">屬性</span><span class="sxs-lookup"><span data-stu-id="baa4d-113">Attributes</span></span>  
  
|<span data-ttu-id="baa4d-114">屬性</span><span class="sxs-lookup"><span data-stu-id="baa4d-114">Attribute</span></span>|<span data-ttu-id="baa4d-115">描述</span><span class="sxs-lookup"><span data-stu-id="baa4d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="baa4d-116">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="baa4d-116">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="baa4d-117">當此屬性設定為 `true` 時，WCF 基礎結構會判斷要使用的最佳格式。</span><span class="sxs-lookup"><span data-stu-id="baa4d-117">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="baa4d-118">為了提供回溯相容性，自動格式選取預設為停用。</span><span class="sxs-lookup"><span data-stu-id="baa4d-118">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="baa4d-119">自動格式選取可以透過程式設計方式或透過組態啟用。</span><span class="sxs-lookup"><span data-stu-id="baa4d-119">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="baa4d-120">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="baa4d-120">defaultBodyStyle</span></span>|<span data-ttu-id="baa4d-121">指定傳回訊息的預設本文樣式。</span><span class="sxs-lookup"><span data-stu-id="baa4d-121">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="baa4d-122">如需詳細資訊，請參閱 <<c0> <xref:System.ServiceModel.Web.WebMessageBodyStyle> 並[WCF Web HTTP 格式化](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)。</span><span class="sxs-lookup"><span data-stu-id="baa4d-122">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="baa4d-123">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="baa4d-123">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="baa4d-124">指定訊息的預設傳出回應格式。</span><span class="sxs-lookup"><span data-stu-id="baa4d-124">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="baa4d-125">如需詳細資訊，請參閱 < [WCF Web HTTP 格式化](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)。</span><span class="sxs-lookup"><span data-stu-id="baa4d-125">For more information, see [WCF Web HTTP Formatting](../../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="baa4d-126">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="baa4d-126">faultExceptionEnabled</span></span>|<span data-ttu-id="baa4d-127">取得或設定旗標，指定是否要在內部伺服器錯誤 (HTTP 狀態碼：500) 發生時產生 FaultException。</span><span class="sxs-lookup"><span data-stu-id="baa4d-127">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="baa4d-128">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="baa4d-128">helpEnabled</span></span>|<span data-ttu-id="baa4d-129">取得或設定值，這個值會判斷是否已啟用說明頁面。</span><span class="sxs-lookup"><span data-stu-id="baa4d-129">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="baa4d-130">子元素</span><span class="sxs-lookup"><span data-stu-id="baa4d-130">Child Elements</span></span>  
 <span data-ttu-id="baa4d-131">無。</span><span class="sxs-lookup"><span data-stu-id="baa4d-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="baa4d-132">父項目</span><span class="sxs-lookup"><span data-stu-id="baa4d-132">Parent Elements</span></span>  
  
|<span data-ttu-id="baa4d-133">項目</span><span class="sxs-lookup"><span data-stu-id="baa4d-133">Element</span></span>|<span data-ttu-id="baa4d-134">描述</span><span class="sxs-lookup"><span data-stu-id="baa4d-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="baa4d-135">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="baa4d-135">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="baa4d-136">指定端點行為組。</span><span class="sxs-lookup"><span data-stu-id="baa4d-136">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="baa4d-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="baa4d-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebHttpElement>  
 <xref:System.ServiceModel.Description.WebHttpBehavior>  
 [<span data-ttu-id="baa4d-138">AJAX 整合與 JSON 支援</span><span class="sxs-lookup"><span data-stu-id="baa4d-138">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [<span data-ttu-id="baa4d-139">\<webHttpBinding></span><span class="sxs-lookup"><span data-stu-id="baa4d-139">\<webHttpBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)
