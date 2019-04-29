---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 6fb31fca6ac38f6cb92ef087cc277a4d5066521c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769768"
---
# <a name="webhttpendpoint"></a><span data-ttu-id="128df-101">\<webHttpEndpoint></span><span class="sxs-lookup"><span data-stu-id="128df-101">\<webHttpEndpoint></span></span>
<span data-ttu-id="128df-102">此組態元素定義具有固定的標準端點[ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)繫結，會自動加入[ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)行為。</span><span class="sxs-lookup"><span data-stu-id="128df-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<webHttp>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="128df-103">撰寫 REST 服務時，請使用這個端點。</span><span class="sxs-lookup"><span data-stu-id="128df-103">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="128df-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="128df-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="128df-105">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="128df-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="128df-106">語法</span><span class="sxs-lookup"><span data-stu-id="128df-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint automaticFormatSelectionEnabled="String"
                        defaultOutgoingResponseFormat="Xml/Json"
                        helpEnabled="Boolean"
                        webEndpointType="String" />
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="128df-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="128df-107">Attributes and Elements</span></span>  
 <span data-ttu-id="128df-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="128df-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="128df-109">屬性</span><span class="sxs-lookup"><span data-stu-id="128df-109">Attributes</span></span>  
  
|<span data-ttu-id="128df-110">屬性</span><span class="sxs-lookup"><span data-stu-id="128df-110">Attribute</span></span>|<span data-ttu-id="128df-111">描述</span><span class="sxs-lookup"><span data-stu-id="128df-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="128df-112">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="128df-112">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="128df-113">布林值，指出是否啟用自動格式化選取範圍。</span><span class="sxs-lookup"><span data-stu-id="128df-113">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="128df-114">啟用自動格式化選取範圍時，基礎結構會剖析要求訊息的 `Accept` 標頭，並且判斷最適合的回應格式。</span><span class="sxs-lookup"><span data-stu-id="128df-114">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="128df-115">如果 `Accept` 標頭未指定適合的回應格式，基礎結構會使用要求訊息的 `Content-Type` 或作業的預設回應格式。</span><span class="sxs-lookup"><span data-stu-id="128df-115">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="128df-116">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="128df-116">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="128df-117">屬性，用來指定預設的傳出回應格式。</span><span class="sxs-lookup"><span data-stu-id="128df-117">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="128df-118">此屬性的型別為 <xref:System.ServiceModel.Web.WebMessageFormat>。</span><span class="sxs-lookup"><span data-stu-id="128df-118">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="128df-119">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="128df-119">helpEnabled</span></span>|<span data-ttu-id="128df-120">布林值，指出是否啟用端點的 HTTP 說明頁。</span><span class="sxs-lookup"><span data-stu-id="128df-120">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="128df-121">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="128df-121">webEndpointType</span></span>|<span data-ttu-id="128df-122">字串，指定端點的型別。</span><span class="sxs-lookup"><span data-stu-id="128df-122">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="128df-123">子元素</span><span class="sxs-lookup"><span data-stu-id="128df-123">Child Elements</span></span>  
 <span data-ttu-id="128df-124">無。</span><span class="sxs-lookup"><span data-stu-id="128df-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="128df-125">父項目</span><span class="sxs-lookup"><span data-stu-id="128df-125">Parent Elements</span></span>  
  
|<span data-ttu-id="128df-126">項目</span><span class="sxs-lookup"><span data-stu-id="128df-126">Element</span></span>|<span data-ttu-id="128df-127">描述</span><span class="sxs-lookup"><span data-stu-id="128df-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="128df-128">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="128df-128">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="128df-129">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="128df-129">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="128df-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="128df-130">See also</span></span>

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
