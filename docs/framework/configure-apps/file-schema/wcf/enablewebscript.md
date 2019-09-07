---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 20c0057c80b668df97379d0168bb7c005d9927ce
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400378"
---
# <a name="enablewebscript"></a><span data-ttu-id="81e76-101">\<enableWebScript></span><span class="sxs-lookup"><span data-stu-id="81e76-101">\<enableWebScript></span></span>
<span data-ttu-id="81e76-102">這個項目可啟用端點行為，以取用 ASP.NET AJAX 網頁上的服務。</span><span class="sxs-lookup"><span data-stu-id="81e76-102">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
<span data-ttu-id="81e76-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="81e76-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="81e76-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="81e76-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="81e76-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="81e76-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="81e76-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="81e76-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="81e76-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="81e76-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="81e76-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<enableWebScript >**</span><span class="sxs-lookup"><span data-stu-id="81e76-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<enableWebScript>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81e76-109">語法</span><span class="sxs-lookup"><span data-stu-id="81e76-109">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81e76-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="81e76-110">Attributes and Elements</span></span>  
 <span data-ttu-id="81e76-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="81e76-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81e76-112">屬性</span><span class="sxs-lookup"><span data-stu-id="81e76-112">Attributes</span></span>  
 <span data-ttu-id="81e76-113">無。</span><span class="sxs-lookup"><span data-stu-id="81e76-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="81e76-114">子元素</span><span class="sxs-lookup"><span data-stu-id="81e76-114">Child Elements</span></span>  
 <span data-ttu-id="81e76-115">無。</span><span class="sxs-lookup"><span data-stu-id="81e76-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="81e76-116">父項目</span><span class="sxs-lookup"><span data-stu-id="81e76-116">Parent Elements</span></span>  
  
|<span data-ttu-id="81e76-117">項目</span><span class="sxs-lookup"><span data-stu-id="81e76-117">Element</span></span>|<span data-ttu-id="81e76-118">描述</span><span class="sxs-lookup"><span data-stu-id="81e76-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="81e76-119">\<behavior></span><span class="sxs-lookup"><span data-stu-id="81e76-119">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="81e76-120">指定端點行為組。</span><span class="sxs-lookup"><span data-stu-id="81e76-120">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81e76-121">備註</span><span class="sxs-lookup"><span data-stu-id="81e76-121">Remarks</span></span>  
 <span data-ttu-id="81e76-122">這個行為只能與[ \<webHttpBinding >](webhttpbinding.md)標準系結或[ \<webMessageEncoding >](webmessageencoding.md)繫結項目搭配使用。</span><span class="sxs-lookup"><span data-stu-id="81e76-122">This behavior should only be used in conjunction with either the [\<webHttpBinding>](webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="81e76-123">如需此行為的詳細資訊，請參閱 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>。</span><span class="sxs-lookup"><span data-stu-id="81e76-123">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81e76-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81e76-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="81e76-125">AJAX 整合與 JSON 支援</span><span class="sxs-lookup"><span data-stu-id="81e76-125">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="81e76-126">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="81e76-126">\<webHttp></span></span>](webhttp.md)
