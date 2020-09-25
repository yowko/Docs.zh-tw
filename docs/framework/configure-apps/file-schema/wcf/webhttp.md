---
title: <webHttp>
ms.date: 03/30/2017
ms.assetid: 1f9d0754-d41e-44ce-a298-e51cb3096c64
ms.openlocfilehash: 716d960e2d5f896976c22a60d419d9b165b36178
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202457"
---
# \<webHttp>

<span data-ttu-id="4209c-101">此項目透過組態指定端點上的 <xref:System.ServiceModel.Description.WebHttpBehavior>。</span><span class="sxs-lookup"><span data-stu-id="4209c-101">This element specifies the <xref:System.ServiceModel.Description.WebHttpBehavior> on an endpoint through configuration.</span></span> <span data-ttu-id="4209c-102">這種行為與標準系結搭配使用時 [\<webHttpBinding>](webhttpbinding.md) ，會啟用 Windows Communication Foundation (WCF) 服務的 Web 程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="4209c-102">This behavior, when used in conjunction with the [\<webHttpBinding>](webhttpbinding.md) standard binding, enables the Web programming model for a Windows Communication Foundation (WCF) service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttp>**  
  
## <a name="syntax"></a><span data-ttu-id="4209c-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="4209c-103">Syntax</span></span>  
  
```xml  
<webHttp />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4209c-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4209c-104">Attributes and Elements</span></span>  

 <span data-ttu-id="4209c-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4209c-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4209c-106">屬性</span><span class="sxs-lookup"><span data-stu-id="4209c-106">Attributes</span></span>  
  
|<span data-ttu-id="4209c-107">屬性</span><span class="sxs-lookup"><span data-stu-id="4209c-107">Attribute</span></span>|<span data-ttu-id="4209c-108">描述</span><span class="sxs-lookup"><span data-stu-id="4209c-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4209c-109">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="4209c-109">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="4209c-110">當此屬性設定為 `true` 時，WCF 基礎結構會判斷要使用的最佳格式。</span><span class="sxs-lookup"><span data-stu-id="4209c-110">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="4209c-111">為了提供回溯相容性，自動格式選取預設為停用。</span><span class="sxs-lookup"><span data-stu-id="4209c-111">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="4209c-112">自動格式選取可以透過程式設計方式或透過組態啟用。</span><span class="sxs-lookup"><span data-stu-id="4209c-112">Automatic format selection can be enabled programmatically or through configuration.</span></span>|  
|<span data-ttu-id="4209c-113">defaultBodyStyle</span><span class="sxs-lookup"><span data-stu-id="4209c-113">defaultBodyStyle</span></span>|<span data-ttu-id="4209c-114">指定傳回訊息的預設本文樣式。</span><span class="sxs-lookup"><span data-stu-id="4209c-114">Specifies the default body style of returned messages.</span></span> <span data-ttu-id="4209c-115">如需詳細資訊，請參閱 <xref:System.ServiceModel.Web.WebMessageBodyStyle> 和 [WCF Web HTTP 格式](../../../wcf/feature-details/wcf-web-http-formatting.md)。</span><span class="sxs-lookup"><span data-stu-id="4209c-115">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle> and [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="4209c-116">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="4209c-116">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="4209c-117">指定訊息的預設傳出回應格式。</span><span class="sxs-lookup"><span data-stu-id="4209c-117">Specifies the default outgoing response format for messages.</span></span> <span data-ttu-id="4209c-118">如需詳細資訊，請參閱 [WCF WEB HTTP 格式](../../../wcf/feature-details/wcf-web-http-formatting.md)。</span><span class="sxs-lookup"><span data-stu-id="4209c-118">For more information, see [WCF Web HTTP Formatting](../../../wcf/feature-details/wcf-web-http-formatting.md).</span></span>|  
|<span data-ttu-id="4209c-119">faultExceptionEnabled</span><span class="sxs-lookup"><span data-stu-id="4209c-119">faultExceptionEnabled</span></span>|<span data-ttu-id="4209c-120">取得或設定旗標，指定內部伺服器錯誤 (HTTP 狀態碼：500) 發生時，是否產生 FaultException。</span><span class="sxs-lookup"><span data-stu-id="4209c-120">Gets or sets the flag that specifies whether a FaultException is generated when an internal server error (HTTP status code: 500) occurs.</span></span>|  
|<span data-ttu-id="4209c-121">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="4209c-121">helpEnabled</span></span>|<span data-ttu-id="4209c-122">取得或設定值，這個值會判斷是否已啟用說明頁面。</span><span class="sxs-lookup"><span data-stu-id="4209c-122">Gets or sets a value that determines if the Help page is enabled.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4209c-123">子元素</span><span class="sxs-lookup"><span data-stu-id="4209c-123">Child Elements</span></span>  

 <span data-ttu-id="4209c-124">無。</span><span class="sxs-lookup"><span data-stu-id="4209c-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4209c-125">父項目</span><span class="sxs-lookup"><span data-stu-id="4209c-125">Parent Elements</span></span>  
  
|<span data-ttu-id="4209c-126">項目</span><span class="sxs-lookup"><span data-stu-id="4209c-126">Element</span></span>|<span data-ttu-id="4209c-127">描述</span><span class="sxs-lookup"><span data-stu-id="4209c-127">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="4209c-128">指定端點行為組。</span><span class="sxs-lookup"><span data-stu-id="4209c-128">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4209c-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4209c-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebHttpElement>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="4209c-130">AJAX 整合與 JSON 支援</span><span class="sxs-lookup"><span data-stu-id="4209c-130">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttpBinding>](webhttpbinding.md)
