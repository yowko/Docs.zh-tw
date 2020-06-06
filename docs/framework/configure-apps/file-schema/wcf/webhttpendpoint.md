---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 8d4f55fd5b51ea77839b7fdbb930e937f5700417
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854793"
---
# \<webHttpEndpoint>
<span data-ttu-id="30ff4-101">此設定元素會定義具有固定系結的標準端點，此系結 [\<webHttpBinding>](webhttpbinding.md) 會自動新增 [\<webHttp>](webhttp.md) 行為。</span><span class="sxs-lookup"><span data-stu-id="30ff4-101">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<webHttp>](webhttp.md) behavior.</span></span> <span data-ttu-id="30ff4-102">撰寫 REST 服務時，請使用這個端點。</span><span class="sxs-lookup"><span data-stu-id="30ff4-102">Use this endpoint when writing a REST service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttpEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="30ff4-103">語法</span><span class="sxs-lookup"><span data-stu-id="30ff4-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30ff4-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="30ff4-104">Attributes and Elements</span></span>  
 <span data-ttu-id="30ff4-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="30ff4-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30ff4-106">屬性</span><span class="sxs-lookup"><span data-stu-id="30ff4-106">Attributes</span></span>  
  
|<span data-ttu-id="30ff4-107">屬性</span><span class="sxs-lookup"><span data-stu-id="30ff4-107">Attribute</span></span>|<span data-ttu-id="30ff4-108">描述</span><span class="sxs-lookup"><span data-stu-id="30ff4-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="30ff4-109">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="30ff4-109">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="30ff4-110">布林值，指出是否啟用自動格式化選取範圍。</span><span class="sxs-lookup"><span data-stu-id="30ff4-110">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="30ff4-111">啟用自動格式化選取範圍時，基礎結構會剖析要求訊息的 `Accept` 標頭，並且判斷最適合的回應格式。</span><span class="sxs-lookup"><span data-stu-id="30ff4-111">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="30ff4-112">如果 `Accept` 標頭未指定適合的回應格式，基礎結構會使用要求訊息的 `Content-Type` 或作業的預設回應格式。</span><span class="sxs-lookup"><span data-stu-id="30ff4-112">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="30ff4-113">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="30ff4-113">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="30ff4-114">屬性，用來指定預設的傳出回應格式。</span><span class="sxs-lookup"><span data-stu-id="30ff4-114">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="30ff4-115">此屬性的型別為 <xref:System.ServiceModel.Web.WebMessageFormat>。</span><span class="sxs-lookup"><span data-stu-id="30ff4-115">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="30ff4-116">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="30ff4-116">helpEnabled</span></span>|<span data-ttu-id="30ff4-117">布林值，指出是否啟用端點的 HTTP 說明頁。</span><span class="sxs-lookup"><span data-stu-id="30ff4-117">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="30ff4-118">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="30ff4-118">webEndpointType</span></span>|<span data-ttu-id="30ff4-119">字串，指定端點的型別。</span><span class="sxs-lookup"><span data-stu-id="30ff4-119">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30ff4-120">子元素</span><span class="sxs-lookup"><span data-stu-id="30ff4-120">Child Elements</span></span>  
 <span data-ttu-id="30ff4-121">無。</span><span class="sxs-lookup"><span data-stu-id="30ff4-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="30ff4-122">父項目</span><span class="sxs-lookup"><span data-stu-id="30ff4-122">Parent Elements</span></span>  
  
|<span data-ttu-id="30ff4-123">元素</span><span class="sxs-lookup"><span data-stu-id="30ff4-123">Element</span></span>|<span data-ttu-id="30ff4-124">描述</span><span class="sxs-lookup"><span data-stu-id="30ff4-124">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="30ff4-125">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="30ff4-125">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30ff4-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30ff4-126">See also</span></span>

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
