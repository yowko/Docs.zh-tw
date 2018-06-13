---
title: '&lt;enableWebScript&gt;'
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: b14923c1b9a80bcd1c47db0e4fad6a6224b95329
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751892"
---
# <a name="ltenablewebscriptgt"></a><span data-ttu-id="d13bb-102">&lt;enableWebScript&gt;</span><span class="sxs-lookup"><span data-stu-id="d13bb-102">&lt;enableWebScript&gt;</span></span>
<span data-ttu-id="d13bb-103">這個項目可啟用端點行為，以取用 ASP.NET AJAX 網頁上的服務。</span><span class="sxs-lookup"><span data-stu-id="d13bb-103">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
 <span data-ttu-id="d13bb-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d13bb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d13bb-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="d13bb-105">\<behaviors></span></span>  
<span data-ttu-id="d13bb-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="d13bb-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="d13bb-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="d13bb-107">\<behavior></span></span>  
<span data-ttu-id="d13bb-108">\<enableWebScript ></span><span class="sxs-lookup"><span data-stu-id="d13bb-108">\<enableWebScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d13bb-109">語法</span><span class="sxs-lookup"><span data-stu-id="d13bb-109">Syntax</span></span>  
  
```xml  
<enableWebScript />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d13bb-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d13bb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d13bb-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d13bb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d13bb-112">屬性</span><span class="sxs-lookup"><span data-stu-id="d13bb-112">Attributes</span></span>  
 <span data-ttu-id="d13bb-113">無。</span><span class="sxs-lookup"><span data-stu-id="d13bb-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d13bb-114">子項目</span><span class="sxs-lookup"><span data-stu-id="d13bb-114">Child Elements</span></span>  
 <span data-ttu-id="d13bb-115">無。</span><span class="sxs-lookup"><span data-stu-id="d13bb-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d13bb-116">父項目</span><span class="sxs-lookup"><span data-stu-id="d13bb-116">Parent Elements</span></span>  
  
|<span data-ttu-id="d13bb-117">項目</span><span class="sxs-lookup"><span data-stu-id="d13bb-117">Element</span></span>|<span data-ttu-id="d13bb-118">描述</span><span class="sxs-lookup"><span data-stu-id="d13bb-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d13bb-119">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="d13bb-119">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="d13bb-120">指定端點行為組。</span><span class="sxs-lookup"><span data-stu-id="d13bb-120">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d13bb-121">備註</span><span class="sxs-lookup"><span data-stu-id="d13bb-121">Remarks</span></span>  
 <span data-ttu-id="d13bb-122">這個行為應該只用於搭配  [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)標準繫結，或[ \<webMessageEncoding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md)繫結項目。</span><span class="sxs-lookup"><span data-stu-id="d13bb-122">This behavior should only be used in conjunction with either the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="d13bb-123">如需此行為的詳細資訊，請參閱 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>。</span><span class="sxs-lookup"><span data-stu-id="d13bb-123">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d13bb-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d13bb-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>  
 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>  
 [<span data-ttu-id="d13bb-125">AJAX 整合與 JSON 支援</span><span class="sxs-lookup"><span data-stu-id="d13bb-125">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [<span data-ttu-id="d13bb-126">\<webHttp ></span><span class="sxs-lookup"><span data-stu-id="d13bb-126">\<webHttp></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)
