---
title: <enableWebScript>
ms.date: 03/30/2017
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
ms.openlocfilehash: 9c9bbb9ccc7879510ae3e2bee2fabd604fd52f65
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266646"
---
# <a name="enablewebscript"></a><span data-ttu-id="ed513-101">\<enableWebScript></span><span class="sxs-lookup"><span data-stu-id="ed513-101">\<enableWebScript></span></span>
<span data-ttu-id="ed513-102">這個項目可啟用端點行為，以取用 ASP.NET AJAX 網頁上的服務。</span><span class="sxs-lookup"><span data-stu-id="ed513-102">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
 <span data-ttu-id="ed513-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ed513-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="ed513-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="ed513-104">\<behaviors></span></span>  
<span data-ttu-id="ed513-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="ed513-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="ed513-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="ed513-106">\<behavior></span></span>  
<span data-ttu-id="ed513-107">\<enableWebScript></span><span class="sxs-lookup"><span data-stu-id="ed513-107">\<enableWebScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed513-108">語法</span><span class="sxs-lookup"><span data-stu-id="ed513-108">Syntax</span></span>  
  
```xml  
<enableWebScript />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ed513-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ed513-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ed513-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ed513-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ed513-111">屬性</span><span class="sxs-lookup"><span data-stu-id="ed513-111">Attributes</span></span>  
 <span data-ttu-id="ed513-112">無。</span><span class="sxs-lookup"><span data-stu-id="ed513-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ed513-113">子元素</span><span class="sxs-lookup"><span data-stu-id="ed513-113">Child Elements</span></span>  
 <span data-ttu-id="ed513-114">無。</span><span class="sxs-lookup"><span data-stu-id="ed513-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ed513-115">父項目</span><span class="sxs-lookup"><span data-stu-id="ed513-115">Parent Elements</span></span>  
  
|<span data-ttu-id="ed513-116">項目</span><span class="sxs-lookup"><span data-stu-id="ed513-116">Element</span></span>|<span data-ttu-id="ed513-117">描述</span><span class="sxs-lookup"><span data-stu-id="ed513-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ed513-118">\<behavior></span><span class="sxs-lookup"><span data-stu-id="ed513-118">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="ed513-119">指定端點行為組。</span><span class="sxs-lookup"><span data-stu-id="ed513-119">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed513-120">備註</span><span class="sxs-lookup"><span data-stu-id="ed513-120">Remarks</span></span>  
 <span data-ttu-id="ed513-121">此行為只能搭配其中一個[ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)標準繫結，或有[ \<webMessageEncoding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md)繫結項目。</span><span class="sxs-lookup"><span data-stu-id="ed513-121">This behavior should only be used in conjunction with either the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="ed513-122">如需此行為的詳細資訊，請參閱 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>。</span><span class="sxs-lookup"><span data-stu-id="ed513-122">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed513-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed513-123">See also</span></span>
- <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>
- <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>
- [<span data-ttu-id="ed513-124">AJAX 整合與 JSON 支援</span><span class="sxs-lookup"><span data-stu-id="ed513-124">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)
- [<span data-ttu-id="ed513-125">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="ed513-125">\<webHttp></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)
