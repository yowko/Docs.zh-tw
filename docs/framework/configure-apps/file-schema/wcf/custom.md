---
title: "&lt;自訂&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bcab1e8361448abfe14db8ac38a924c656b9065
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltcustomgt"></a><span data-ttu-id="2455b-102">&lt;自訂&gt;</span><span class="sxs-lookup"><span data-stu-id="2455b-102">&lt;custom&gt;</span></span>
<span data-ttu-id="2455b-103">指定自訂對等解析程式服務的設定。</span><span class="sxs-lookup"><span data-stu-id="2455b-103">Specifies settings for a custom peer resolver service.</span></span>  
  
<span data-ttu-id="2455b-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="2455b-104">\<system.serviceModel></span></span>  
<span data-ttu-id="2455b-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="2455b-105">\<bindings></span></span>  
<span data-ttu-id="2455b-106">\<netPeerBinding ></span><span class="sxs-lookup"><span data-stu-id="2455b-106">\<netPeerBinding></span></span>  
<span data-ttu-id="2455b-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="2455b-107">\<binding></span></span>  
<span data-ttu-id="2455b-108">\<解析程式 ></span><span class="sxs-lookup"><span data-stu-id="2455b-108">\<resolver></span></span>  
<span data-ttu-id="2455b-109">\<自訂 ></span><span class="sxs-lookup"><span data-stu-id="2455b-109">\<custom></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2455b-110">語法</span><span class="sxs-lookup"><span data-stu-id="2455b-110">Syntax</span></span>  
  
```xml
<custom address="Uri" 
        resolverType="String">  
  <headers/>  
  <identity/>  
</custom>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2455b-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2455b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2455b-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2455b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2455b-113">屬性</span><span class="sxs-lookup"><span data-stu-id="2455b-113">Attributes</span></span>  
  
|<span data-ttu-id="2455b-114">屬性</span><span class="sxs-lookup"><span data-stu-id="2455b-114">Attribute</span></span>|<span data-ttu-id="2455b-115">描述</span><span class="sxs-lookup"><span data-stu-id="2455b-115">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="2455b-116">URI，這個 URI 會指定裝載自訂解析程式服務之對等節點的端點位址。</span><span class="sxs-lookup"><span data-stu-id="2455b-116">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="2455b-117">字串，這個字串會指定自訂對等解析服務之型別。</span><span class="sxs-lookup"><span data-stu-id="2455b-117">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2455b-118">子元素</span><span class="sxs-lookup"><span data-stu-id="2455b-118">Child Elements</span></span>  
  
|<span data-ttu-id="2455b-119">項目</span><span class="sxs-lookup"><span data-stu-id="2455b-119">Element</span></span>|<span data-ttu-id="2455b-120">描述</span><span class="sxs-lookup"><span data-stu-id="2455b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2455b-121">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="2455b-121">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="2455b-122">指定使用這個項目設定的自訂對等解析程式的身分識別。</span><span class="sxs-lookup"><span data-stu-id="2455b-122">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="2455b-123">此項目的型別為 <xref:System.ServiceModel.Configuration.IdentityElement>。</span><span class="sxs-lookup"><span data-stu-id="2455b-123">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[<span data-ttu-id="2455b-124">\<標頭 ></span><span class="sxs-lookup"><span data-stu-id="2455b-124">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="2455b-125">位址標頭的集合，用於自訂對等解析程式所處理的 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="2455b-125">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2455b-126">父項目</span><span class="sxs-lookup"><span data-stu-id="2455b-126">Parent Elements</span></span>  
  
|<span data-ttu-id="2455b-127">項目</span><span class="sxs-lookup"><span data-stu-id="2455b-127">Element</span></span>|<span data-ttu-id="2455b-128">描述</span><span class="sxs-lookup"><span data-stu-id="2455b-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2455b-129">\<解析程式 ></span><span class="sxs-lookup"><span data-stu-id="2455b-129">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="2455b-130">對等解析程式，這個程式可用於將對等網狀結構 ID 解析成一組對等節點位址，這組位址可表示參與網狀結構的數個節點。</span><span class="sxs-lookup"><span data-stu-id="2455b-130">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2455b-131">備註</span><span class="sxs-lookup"><span data-stu-id="2455b-131">Remarks</span></span>  
 <span data-ttu-id="2455b-132">這個項目定義自訂對等解析程式服務的基本設定，包括裝載服務之對等的端點位址以及任何特定繫結設定。</span><span class="sxs-lookup"><span data-stu-id="2455b-132">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="2455b-133">如需有關如何建立自訂的解析程式的詳細資訊，請參閱[PeerChannel 應用程式中加入自訂解析程式](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419)。</span><span class="sxs-lookup"><span data-stu-id="2455b-133">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2455b-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="2455b-134">See Also</span></span>  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>  
 <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>  
 <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>  
 [<span data-ttu-id="2455b-135">對等解析程式</span><span class="sxs-lookup"><span data-stu-id="2455b-135">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [<span data-ttu-id="2455b-136">PeerChannel 應用程式中加入自訂解析程式</span><span class="sxs-lookup"><span data-stu-id="2455b-136">Adding a Custom Resolver to a PeerChannel Application</span></span>](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419)
