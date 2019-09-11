---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 8d4f55fd5b51ea77839b7fdbb930e937f5700417
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854793"
---
# <a name="webhttpendpoint"></a><span data-ttu-id="d28e0-101">\<webHttpEndpoint></span><span class="sxs-lookup"><span data-stu-id="d28e0-101">\<webHttpEndpoint></span></span>
<span data-ttu-id="d28e0-102">此設定元素會定義標準端點，其中具有固定[ \<的 webHttpBinding >](webhttpbinding.md)系結[ \< ](webhttp.md) ，會自動新增 webHttp > 行為。</span><span class="sxs-lookup"><span data-stu-id="d28e0-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<webHttp>](webhttp.md) behavior.</span></span> <span data-ttu-id="d28e0-103">撰寫 REST 服務時，請使用這個端點。</span><span class="sxs-lookup"><span data-stu-id="d28e0-103">Use this endpoint when writing a REST service.</span></span>  
  
<span data-ttu-id="d28e0-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d28e0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d28e0-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d28e0-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d28e0-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="d28e0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="d28e0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webHttpEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="d28e0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webHttpEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d28e0-108">語法</span><span class="sxs-lookup"><span data-stu-id="d28e0-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d28e0-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d28e0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d28e0-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d28e0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d28e0-111">屬性</span><span class="sxs-lookup"><span data-stu-id="d28e0-111">Attributes</span></span>  
  
|<span data-ttu-id="d28e0-112">屬性</span><span class="sxs-lookup"><span data-stu-id="d28e0-112">Attribute</span></span>|<span data-ttu-id="d28e0-113">說明</span><span class="sxs-lookup"><span data-stu-id="d28e0-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d28e0-114">automaticFormatSelectionEnabled</span><span class="sxs-lookup"><span data-stu-id="d28e0-114">automaticFormatSelectionEnabled</span></span>|<span data-ttu-id="d28e0-115">布林值，指出是否啟用自動格式化選取範圍。</span><span class="sxs-lookup"><span data-stu-id="d28e0-115">A Boolean value that indicates whether automatic format selection is enabled.</span></span><br /><br /> <span data-ttu-id="d28e0-116">啟用自動格式化選取範圍時，基礎結構會剖析要求訊息的 `Accept` 標頭，並且判斷最適合的回應格式。</span><span class="sxs-lookup"><span data-stu-id="d28e0-116">When automatic format selection is enabled, the infrastructure parses the `Accept` header of the request message and determines the most appropriate response format.</span></span> <span data-ttu-id="d28e0-117">如果 `Accept` 標頭未指定適合的回應格式，基礎結構會使用要求訊息的 `Content-Type` 或作業的預設回應格式。</span><span class="sxs-lookup"><span data-stu-id="d28e0-117">If the `Accept` header does not specify a suitable response format, the infrastructure uses the `Content-Type` of the request message or the default response format of the operation.</span></span>|  
|<span data-ttu-id="d28e0-118">defaultOutgoingResponseFormat</span><span class="sxs-lookup"><span data-stu-id="d28e0-118">defaultOutgoingResponseFormat</span></span>|<span data-ttu-id="d28e0-119">屬性，用來指定預設的傳出回應格式。</span><span class="sxs-lookup"><span data-stu-id="d28e0-119">An attribute that specifies the default outgoing response format.</span></span> <span data-ttu-id="d28e0-120">此屬性的型別為 <xref:System.ServiceModel.Web.WebMessageFormat>。</span><span class="sxs-lookup"><span data-stu-id="d28e0-120">This attribute is of the <xref:System.ServiceModel.Web.WebMessageFormat> type</span></span>|  
|<span data-ttu-id="d28e0-121">helpEnabled</span><span class="sxs-lookup"><span data-stu-id="d28e0-121">helpEnabled</span></span>|<span data-ttu-id="d28e0-122">布林值，指出是否啟用端點的 HTTP 說明頁。</span><span class="sxs-lookup"><span data-stu-id="d28e0-122">A Boolean value that indicates whether the HTTP help page is enabled for the endpoint.</span></span>|  
|<span data-ttu-id="d28e0-123">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="d28e0-123">webEndpointType</span></span>|<span data-ttu-id="d28e0-124">字串，指定端點的型別。</span><span class="sxs-lookup"><span data-stu-id="d28e0-124">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d28e0-125">子元素</span><span class="sxs-lookup"><span data-stu-id="d28e0-125">Child Elements</span></span>  
 <span data-ttu-id="d28e0-126">無。</span><span class="sxs-lookup"><span data-stu-id="d28e0-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d28e0-127">父項目</span><span class="sxs-lookup"><span data-stu-id="d28e0-127">Parent Elements</span></span>  
  
|<span data-ttu-id="d28e0-128">項目</span><span class="sxs-lookup"><span data-stu-id="d28e0-128">Element</span></span>|<span data-ttu-id="d28e0-129">描述</span><span class="sxs-lookup"><span data-stu-id="d28e0-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d28e0-130">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="d28e0-130">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="d28e0-131">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="d28e0-131">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d28e0-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d28e0-132">See also</span></span>

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
