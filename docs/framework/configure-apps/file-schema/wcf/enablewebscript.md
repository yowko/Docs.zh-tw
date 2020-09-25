---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 11378e6cc8cbe8e631fd77ab74c91a616099df52
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190081"
---
# \<enableWebScript>

<span data-ttu-id="5a9d8-101">這個項目可啟用端點行為，以取用 ASP.NET AJAX 網頁上的服務。</span><span class="sxs-lookup"><span data-stu-id="5a9d8-101">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<enableWebScript>**  
  
## <a name="syntax"></a><span data-ttu-id="5a9d8-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="5a9d8-102">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a9d8-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5a9d8-103">Attributes and Elements</span></span>  

 <span data-ttu-id="5a9d8-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5a9d8-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a9d8-105">屬性</span><span class="sxs-lookup"><span data-stu-id="5a9d8-105">Attributes</span></span>  

 <span data-ttu-id="5a9d8-106">無。</span><span class="sxs-lookup"><span data-stu-id="5a9d8-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5a9d8-107">子元素</span><span class="sxs-lookup"><span data-stu-id="5a9d8-107">Child Elements</span></span>  

 <span data-ttu-id="5a9d8-108">無。</span><span class="sxs-lookup"><span data-stu-id="5a9d8-108">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5a9d8-109">父項目</span><span class="sxs-lookup"><span data-stu-id="5a9d8-109">Parent Elements</span></span>  
  
|<span data-ttu-id="5a9d8-110">項目</span><span class="sxs-lookup"><span data-stu-id="5a9d8-110">Element</span></span>|<span data-ttu-id="5a9d8-111">描述</span><span class="sxs-lookup"><span data-stu-id="5a9d8-111">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="5a9d8-112">指定端點行為組。</span><span class="sxs-lookup"><span data-stu-id="5a9d8-112">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a9d8-113">備註</span><span class="sxs-lookup"><span data-stu-id="5a9d8-113">Remarks</span></span>  

 <span data-ttu-id="5a9d8-114">此行為只能與標準系結或繫結項目一起使用 [\<webHttpBinding>](webhttpbinding.md) [\<webMessageEncoding>](webmessageencoding.md) 。</span><span class="sxs-lookup"><span data-stu-id="5a9d8-114">This behavior should only be used in conjunction with either the [\<webHttpBinding>](webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="5a9d8-115">如需此行為的詳細資訊，請參閱 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>。</span><span class="sxs-lookup"><span data-stu-id="5a9d8-115">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a9d8-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a9d8-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="5a9d8-117">AJAX 整合與 JSON 支援</span><span class="sxs-lookup"><span data-stu-id="5a9d8-117">AJAX Integration and JSON Support</span></span>](../../../wcf/feature-details/ajax-integration-and-json-support.md)
- [\<webHttp>](webhttp.md)
