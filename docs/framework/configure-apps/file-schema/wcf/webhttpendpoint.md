---
title: '&lt;webHttpEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ee055be8c4d2e53dc22a101529e5521add9b54a4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltwebhttpendpointgt"></a><span data-ttu-id="c74d0-102">&lt;webHttpEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="c74d0-102">&lt;webHttpEndpoint&gt;</span></span>
<span data-ttu-id="c74d0-103">此組態元素定義具有固定的標準端點[ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)繫結，會自動加入[ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)行為。</span><span class="sxs-lookup"><span data-stu-id="c74d0-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<webHttp>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="c74d0-104">撰寫 REST 服務時，請使用這個端點。</span><span class="sxs-lookup"><span data-stu-id="c74d0-104">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="c74d0-105">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c74d0-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="c74d0-106">\<Kind ></span><span class="sxs-lookup"><span data-stu-id="c74d0-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c74d0-107">語法</span><span class="sxs-lookup"><span data-stu-id="c74d0-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint automaticFormatSelectionEnabled="String" 
                        defaultOutgoingResponseFormat="Xml/Json" 
                        helpEnabled="Boolean" 
                        webEndpointType="String"/>
    </webHttpEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c74d0-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c74d0-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c74d0-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c74d0-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c74d0-110">屬性</span><span class="sxs-lookup"><span data-stu-id="c74d0-110">Attributes</span></span>  
  
|<span data-ttu-id="c74d0-111">屬性</span><span class="sxs-lookup"><span data-stu-id="c74d0-111">Attribute</span></span>|<span data-ttu-id="c74d0-112">描述</span><span class="sxs-lookup"><span data-stu-id="c74d0-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c74d0-113">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="c74d0-113">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="c74d0-114">布林值，指出是否啟用自動格式化選取範圍。</span><span class="sxs-lookup"><span data-stu-id="c74d0-114">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="c74d0-115">啟用自動格式化選取範圍時，基礎結構會剖析要求訊息的 `Accept` 標頭，並且判斷最適合的回應格式。</span><span class="sxs-lookup"><span data-stu-id="c74d0-115">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="c74d0-116">如果 `Accept` 標頭未指定適合的回應格式，基礎結構會使用要求訊息的 `Content-Type` 或作業的預設回應格式。</span><span class="sxs-lookup"><span data-stu-id="c74d0-116">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="c74d0-117">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="c74d0-117">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="c74d0-118">屬性，用來指定預設的傳出回應格式。</span><span class="sxs-lookup"><span data-stu-id="c74d0-118">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="c74d0-119">此屬性的型別為 <xref:System.ServiceModel.Web.WebMessageFormat>。</span><span class="sxs-lookup"><span data-stu-id="c74d0-119">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="c74d0-120">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="c74d0-120">helpEnabled</span></span>|<span data-ttu-id="c74d0-121">布林值，指出是否啟用端點的 HTTP 說明頁。</span><span class="sxs-lookup"><span data-stu-id="c74d0-121">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="c74d0-122">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="c74d0-122">webEndpointType</span></span>|<span data-ttu-id="c74d0-123">字串，指定端點的型別。</span><span class="sxs-lookup"><span data-stu-id="c74d0-123">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c74d0-124">子元素</span><span class="sxs-lookup"><span data-stu-id="c74d0-124">Child Elements</span></span>  
 <span data-ttu-id="c74d0-125">無。</span><span class="sxs-lookup"><span data-stu-id="c74d0-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c74d0-126">父項目</span><span class="sxs-lookup"><span data-stu-id="c74d0-126">Parent Elements</span></span>  
  
|<span data-ttu-id="c74d0-127">項目</span><span class="sxs-lookup"><span data-stu-id="c74d0-127">Element</span></span>|<span data-ttu-id="c74d0-128">說明</span><span class="sxs-lookup"><span data-stu-id="c74d0-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c74d0-129">\<Kind ></span><span class="sxs-lookup"><span data-stu-id="c74d0-129">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="c74d0-130">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="c74d0-130">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c74d0-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c74d0-131">See Also</span></span>  
 <xref:System.ServiceModel.Description.WebHttpEndpoint>  
 <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
