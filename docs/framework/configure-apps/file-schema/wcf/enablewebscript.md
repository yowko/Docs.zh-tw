---
title: '&lt;enableWebScript&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c7e96e1-af70-4e6e-ac5c-d67929dddbaa
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b7e637a744d24ed32be71d0ecf3f5d93144d32aa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltenablewebscriptgt"></a><span data-ttu-id="348c8-102">&lt;enableWebScript&gt;</span><span class="sxs-lookup"><span data-stu-id="348c8-102">&lt;enableWebScript&gt;</span></span>
<span data-ttu-id="348c8-103">這個項目可啟用端點行為，以取用 ASP.NET AJAX 網頁上的服務。</span><span class="sxs-lookup"><span data-stu-id="348c8-103">This element enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span>  
  
 <span data-ttu-id="348c8-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="348c8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="348c8-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="348c8-105">\<behaviors></span></span>  
<span data-ttu-id="348c8-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="348c8-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="348c8-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="348c8-107">\<behavior></span></span>  
<span data-ttu-id="348c8-108">\<enableWebScript ></span><span class="sxs-lookup"><span data-stu-id="348c8-108">\<enableWebScript></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="348c8-109">語法</span><span class="sxs-lookup"><span data-stu-id="348c8-109">Syntax</span></span>  
  
```xml  
<enableWebScript />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="348c8-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="348c8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="348c8-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="348c8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="348c8-112">屬性</span><span class="sxs-lookup"><span data-stu-id="348c8-112">Attributes</span></span>  
 <span data-ttu-id="348c8-113">無。</span><span class="sxs-lookup"><span data-stu-id="348c8-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="348c8-114">子元素</span><span class="sxs-lookup"><span data-stu-id="348c8-114">Child Elements</span></span>  
 <span data-ttu-id="348c8-115">無。</span><span class="sxs-lookup"><span data-stu-id="348c8-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="348c8-116">父項目</span><span class="sxs-lookup"><span data-stu-id="348c8-116">Parent Elements</span></span>  
  
|<span data-ttu-id="348c8-117">項目</span><span class="sxs-lookup"><span data-stu-id="348c8-117">Element</span></span>|<span data-ttu-id="348c8-118">描述</span><span class="sxs-lookup"><span data-stu-id="348c8-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="348c8-119">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="348c8-119">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="348c8-120">指定端點行為組。</span><span class="sxs-lookup"><span data-stu-id="348c8-120">Specifies the set of endpoint behaviors.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="348c8-121">備註</span><span class="sxs-lookup"><span data-stu-id="348c8-121">Remarks</span></span>  
 <span data-ttu-id="348c8-122">這個行為應該只用於搭配  [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)標準繫結，或[ \<webMessageEncoding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md)繫結項目。</span><span class="sxs-lookup"><span data-stu-id="348c8-122">This behavior should only be used in conjunction with either the [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) standard binding, or the [\<webMessageEncoding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webmessageencoding.md) binding element.</span></span>  <span data-ttu-id="348c8-123">如需此行為的詳細資訊，請參閱 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>。</span><span class="sxs-lookup"><span data-stu-id="348c8-123">For more information on this behavior, see <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="348c8-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="348c8-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WebScriptEnablingElement>  
 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior>  
 [<span data-ttu-id="348c8-125">AJAX 整合與 JSON 支援</span><span class="sxs-lookup"><span data-stu-id="348c8-125">AJAX Integration and JSON Support</span></span>](../../../../../docs/framework/wcf/feature-details/ajax-integration-and-json-support.md)  
 [<span data-ttu-id="348c8-126">\<webHttp ></span><span class="sxs-lookup"><span data-stu-id="348c8-126">\<webHttp></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)
