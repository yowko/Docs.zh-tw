---
title: '&lt;webScriptEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6d847f267a0e88a16195273197876a00dd07f0df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltwebscriptendpointgt"></a><span data-ttu-id="1fc52-102">&lt;webScriptEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="1fc52-102">&lt;webScriptEndpoint&gt;</span></span>
<span data-ttu-id="1fc52-103">此組態元素定義具有固定的標準端點[ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)繫結，會自動加入[ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md)行為。</span><span class="sxs-lookup"><span data-stu-id="1fc52-103">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior.</span></span> <span data-ttu-id="1fc52-104">撰寫從 ASP.NET AJAX 應用程式呼叫的服務時，請使用這個端點。</span><span class="sxs-lookup"><span data-stu-id="1fc52-104">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="1fc52-105">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1fc52-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="1fc52-106">\<Kind ></span><span class="sxs-lookup"><span data-stu-id="1fc52-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fc52-107">語法</span><span class="sxs-lookup"><span data-stu-id="1fc52-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String"/>
    </webScriptEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1fc52-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1fc52-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1fc52-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1fc52-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1fc52-110">屬性</span><span class="sxs-lookup"><span data-stu-id="1fc52-110">Attributes</span></span>  
  
|<span data-ttu-id="1fc52-111">屬性</span><span class="sxs-lookup"><span data-stu-id="1fc52-111">Attribute</span></span>|<span data-ttu-id="1fc52-112">描述</span><span class="sxs-lookup"><span data-stu-id="1fc52-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1fc52-113">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="1fc52-113">webEndpointType</span></span>|<span data-ttu-id="1fc52-114">字串，指定端點的型別。</span><span class="sxs-lookup"><span data-stu-id="1fc52-114">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1fc52-115">子元素</span><span class="sxs-lookup"><span data-stu-id="1fc52-115">Child Elements</span></span>  
 <span data-ttu-id="1fc52-116">無。</span><span class="sxs-lookup"><span data-stu-id="1fc52-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1fc52-117">父項目</span><span class="sxs-lookup"><span data-stu-id="1fc52-117">Parent Elements</span></span>  
  
|<span data-ttu-id="1fc52-118">項目</span><span class="sxs-lookup"><span data-stu-id="1fc52-118">Element</span></span>|<span data-ttu-id="1fc52-119">說明</span><span class="sxs-lookup"><span data-stu-id="1fc52-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1fc52-120">\<Kind ></span><span class="sxs-lookup"><span data-stu-id="1fc52-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="1fc52-121">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="1fc52-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1fc52-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1fc52-122">See Also</span></span>  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
