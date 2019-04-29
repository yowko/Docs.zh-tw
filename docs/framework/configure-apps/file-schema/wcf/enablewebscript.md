---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: b2cdd29cda7f82ce555b0f6c1a963567b41ff81b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673247"
---
# <a name="enablewebscript"></a><span data-ttu-id="42d71-101">\<enableWebScript></span><span class="sxs-lookup"><span data-stu-id="42d71-101">\<enableWebScript></span></span>
<span data-ttu-id="42d71-102">這個項目可啟用端點行為，以取用 ASP.NET AJAX 網頁上的服務。</span><span class="sxs-lookup"><span data-stu-id="42d71-102">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
 <span data-ttu-id="42d71-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="42d71-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="42d71-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="42d71-104">\<behaviors></span></span>  
<span data-ttu-id="42d71-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="42d71-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="42d71-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="42d71-106">\<behavior></span></span>  
<span data-ttu-id="42d71-107">\<enableWebScript></span><span class="sxs-lookup"><span data-stu-id="42d71-107">\<enableWebScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42d71-108">語法</span><span class="sxs-lookup"><span data-stu-id="42d71-108">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="42d71-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="42d71-109">Attributes and Elements</span></span>  
 <span data-ttu-id="42d71-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="42d71-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="42d71-111">屬性</span><span class="sxs-lookup"><span data-stu-id="42d71-111">Attributes</span></span>  
 <span data-ttu-id="42d71-112">無。</span><span class="sxs-lookup"><span data-stu-id="42d71-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="42d71-113">子元素</span><span class="sxs-lookup"><span data-stu-id="42d71-113">Child Elements</span></span>  
 <span data-ttu-id="42d71-114">無。</span><span class="sxs-lookup"><span data-stu-id="42d71-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="42d71-115">父項目</span><span class="sxs-lookup"><span data-stu-id="42d71-115">Parent Elements</span></span>  
  
|<span data-ttu-id="42d71-116">項目</span><span class="sxs-lookup"><span data-stu-id="42d71-116">Element</span></span>|<span data-ttu-id="42d71-117">描述</span><span class="sxs-lookup"><span data-stu-id="42d71-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="42d71-118">\<behavior></span><span class="sxs-lookup"><span data-stu-id="42d71-118">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="42d71-119">指定端點行為組。</span><span class="sxs-lookup"><span data-stu-id="42d71-119">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42d71-120">備註</span><span class="sxs-lookup"><span data-stu-id="42d71-120">Remarks</span></span>  
 <span data-ttu-id="42d71-121">此行為只能搭配其中一個[ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)標準繫結，或有[ \<webMessageEncoding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md)繫結項目。</span><span class="sxs-lookup"><span data-stu-id="42d71-121">This behavior should only be used in conjunction with either the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="42d71-122">如需此行為的詳細資訊，請參閱 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>。</span><span class="sxs-lookup"><span data-stu-id="42d71-122">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42d71-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="42d71-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="42d71-124">AJAX 整合與 JSON 支援</span><span class="sxs-lookup"><span data-stu-id="42d71-124">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="42d71-125">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="42d71-125">\<webHttp></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)
