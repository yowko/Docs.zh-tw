---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 3282871bf8dbd25726ada7003d3066b9a42e2366
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177978"
---
# \<webHttpEndpoint>

<span data-ttu-id="b105e-101">這個設定元素會定義具有固定系結的標準端點，此系結 [\<webHttpBinding>](webhttpbinding.md) 會自動加入 [\<webHttp>](webhttp.md) 行為。</span><span class="sxs-lookup"><span data-stu-id="b105e-101">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<webHttp>](webhttp.md) behavior.</span></span> <span data-ttu-id="b105e-102">撰寫 REST 服務時，請使用這個端點。</span><span class="sxs-lookup"><span data-stu-id="b105e-102">Use this endpoint when writing a REST service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttpEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="b105e-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="b105e-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b105e-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b105e-104">Attributes and Elements</span></span>  

 <span data-ttu-id="b105e-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b105e-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b105e-106">屬性</span><span class="sxs-lookup"><span data-stu-id="b105e-106">Attributes</span></span>  
  
|<span data-ttu-id="b105e-107">屬性</span><span class="sxs-lookup"><span data-stu-id="b105e-107">Attribute</span></span>|<span data-ttu-id="b105e-108">描述</span><span class="sxs-lookup"><span data-stu-id="b105e-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b105e-109">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="b105e-109">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="b105e-110">布林值，指出是否啟用自動格式化選取範圍。</span><span class="sxs-lookup"><span data-stu-id="b105e-110">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="b105e-111">啟用自動格式化選取範圍時，基礎結構會剖析要求訊息的 `Accept` 標頭，並且判斷最適合的回應格式。</span><span class="sxs-lookup"><span data-stu-id="b105e-111">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="b105e-112">如果 `Accept` 標頭未指定適合的回應格式，基礎結構會使用要求訊息的 `Content-Type` 或作業的預設回應格式。</span><span class="sxs-lookup"><span data-stu-id="b105e-112">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="b105e-113">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="b105e-113">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="b105e-114">屬性，用來指定預設的傳出回應格式。</span><span class="sxs-lookup"><span data-stu-id="b105e-114">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="b105e-115">此屬性的型別為 <xref:System.ServiceModel.Web.WebMessageFormat>。</span><span class="sxs-lookup"><span data-stu-id="b105e-115">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="b105e-116">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="b105e-116">helpEnabled</span></span>|<span data-ttu-id="b105e-117">布林值，指出是否啟用端點的 HTTP 說明頁。</span><span class="sxs-lookup"><span data-stu-id="b105e-117">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="b105e-118">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="b105e-118">webEndpointType</span></span>|<span data-ttu-id="b105e-119">字串，指定端點的型別。</span><span class="sxs-lookup"><span data-stu-id="b105e-119">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b105e-120">子元素</span><span class="sxs-lookup"><span data-stu-id="b105e-120">Child Elements</span></span>  

 <span data-ttu-id="b105e-121">無。</span><span class="sxs-lookup"><span data-stu-id="b105e-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b105e-122">父項目</span><span class="sxs-lookup"><span data-stu-id="b105e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b105e-123">項目</span><span class="sxs-lookup"><span data-stu-id="b105e-123">Element</span></span>|<span data-ttu-id="b105e-124">描述</span><span class="sxs-lookup"><span data-stu-id="b105e-124">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="b105e-125">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="b105e-125">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b105e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b105e-126">See also</span></span>

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
