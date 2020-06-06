---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 20c0057c80b668df97379d0168bb7c005d9927ce
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400378"
---
# \<enableWebScript>
<span data-ttu-id="c4135-101">這個項目可啟用端點行為，以取用 ASP.NET AJAX 網頁上的服務。</span><span class="sxs-lookup"><span data-stu-id="c4135-101">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<enableWebScript>**  
  
## <a name="syntax"></a><span data-ttu-id="c4135-102">語法</span><span class="sxs-lookup"><span data-stu-id="c4135-102">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c4135-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c4135-103">Attributes and Elements</span></span>  
 <span data-ttu-id="c4135-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c4135-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c4135-105">屬性</span><span class="sxs-lookup"><span data-stu-id="c4135-105">Attributes</span></span>  
 <span data-ttu-id="c4135-106">無。</span><span class="sxs-lookup"><span data-stu-id="c4135-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c4135-107">子元素</span><span class="sxs-lookup"><span data-stu-id="c4135-107">Child Elements</span></span>  
 <span data-ttu-id="c4135-108">無。</span><span class="sxs-lookup"><span data-stu-id="c4135-108">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c4135-109">父項目</span><span class="sxs-lookup"><span data-stu-id="c4135-109">Parent Elements</span></span>  
  
|<span data-ttu-id="c4135-110">元素</span><span class="sxs-lookup"><span data-stu-id="c4135-110">Element</span></span>|<span data-ttu-id="c4135-111">描述</span><span class="sxs-lookup"><span data-stu-id="c4135-111">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c4135-112">指定端點行為組。</span><span class="sxs-lookup"><span data-stu-id="c4135-112">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4135-113">備註</span><span class="sxs-lookup"><span data-stu-id="c4135-113">Remarks</span></span>  
 <span data-ttu-id="c4135-114">這個行為應該只與標準系結或繫結項目搭配使用 [\<webHttpBinding>](webhttpbinding.md) [\<webMessageEncoding>](webmessageencoding.md) 。</span><span class="sxs-lookup"><span data-stu-id="c4135-114">This behavior should only be used in conjunction with either the [\<webHttpBinding>](webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="c4135-115">如需此行為的詳細資訊，請參閱 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>。</span><span class="sxs-lookup"><span data-stu-id="c4135-115">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4135-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4135-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="c4135-117">AJAX 整合與 JSON 支援</span><span class="sxs-lookup"><span data-stu-id="c4135-117">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttp>](webhttp.md)
