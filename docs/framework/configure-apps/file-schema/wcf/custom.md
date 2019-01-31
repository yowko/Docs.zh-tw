---
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 2b268d9d040bbeed2b3563783226f7ca8c18e3b5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254284"
---
# <a name="custom"></a><span data-ttu-id="d88dc-101">\<custom></span><span class="sxs-lookup"><span data-stu-id="d88dc-101">\<custom></span></span>
<span data-ttu-id="d88dc-102">指定自訂對等解析程式服務的設定。</span><span class="sxs-lookup"><span data-stu-id="d88dc-102">Specifies settings for a custom peer resolver service.</span></span>  
  
<span data-ttu-id="d88dc-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="d88dc-103">\<system.serviceModel></span></span>  
<span data-ttu-id="d88dc-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="d88dc-104">\<bindings></span></span>  
<span data-ttu-id="d88dc-105">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="d88dc-105">\<netPeerBinding></span></span>  
<span data-ttu-id="d88dc-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="d88dc-106">\<binding></span></span>  
<span data-ttu-id="d88dc-107">\<resolver></span><span class="sxs-lookup"><span data-stu-id="d88dc-107">\<resolver></span></span>  
<span data-ttu-id="d88dc-108">\<custom></span><span class="sxs-lookup"><span data-stu-id="d88dc-108">\<custom></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d88dc-109">語法</span><span class="sxs-lookup"><span data-stu-id="d88dc-109">Syntax</span></span>  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d88dc-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d88dc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d88dc-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d88dc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d88dc-112">屬性</span><span class="sxs-lookup"><span data-stu-id="d88dc-112">Attributes</span></span>  
  
|<span data-ttu-id="d88dc-113">屬性</span><span class="sxs-lookup"><span data-stu-id="d88dc-113">Attribute</span></span>|<span data-ttu-id="d88dc-114">描述</span><span class="sxs-lookup"><span data-stu-id="d88dc-114">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="d88dc-115">URI，這個 URI 會指定裝載自訂解析程式服務之對等節點的端點位址。</span><span class="sxs-lookup"><span data-stu-id="d88dc-115">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="d88dc-116">字串，這個字串會指定自訂對等解析服務之型別。</span><span class="sxs-lookup"><span data-stu-id="d88dc-116">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d88dc-117">子元素</span><span class="sxs-lookup"><span data-stu-id="d88dc-117">Child Elements</span></span>  
  
|<span data-ttu-id="d88dc-118">項目</span><span class="sxs-lookup"><span data-stu-id="d88dc-118">Element</span></span>|<span data-ttu-id="d88dc-119">描述</span><span class="sxs-lookup"><span data-stu-id="d88dc-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d88dc-120">\<identity></span><span class="sxs-lookup"><span data-stu-id="d88dc-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="d88dc-121">指定使用這個項目設定的自訂對等解析程式的身分識別。</span><span class="sxs-lookup"><span data-stu-id="d88dc-121">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="d88dc-122">此項目的型別為 <xref:System.ServiceModel.Configuration.IdentityElement>。</span><span class="sxs-lookup"><span data-stu-id="d88dc-122">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[<span data-ttu-id="d88dc-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="d88dc-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="d88dc-124">位址標頭的集合，用於自訂對等解析程式所處理的 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="d88dc-124">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d88dc-125">父項目</span><span class="sxs-lookup"><span data-stu-id="d88dc-125">Parent Elements</span></span>  
  
|<span data-ttu-id="d88dc-126">項目</span><span class="sxs-lookup"><span data-stu-id="d88dc-126">Element</span></span>|<span data-ttu-id="d88dc-127">描述</span><span class="sxs-lookup"><span data-stu-id="d88dc-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d88dc-128">\<resolver></span><span class="sxs-lookup"><span data-stu-id="d88dc-128">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="d88dc-129">對等解析程式，這個程式可用於將對等網狀結構 ID 解析成一組對等節點位址，這組位址可表示參與網狀結構的數個節點。</span><span class="sxs-lookup"><span data-stu-id="d88dc-129">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d88dc-130">備註</span><span class="sxs-lookup"><span data-stu-id="d88dc-130">Remarks</span></span>  
 <span data-ttu-id="d88dc-131">這個項目定義自訂對等解析程式服務的基本設定，包括裝載服務之對等的端點位址以及任何特定繫結設定。</span><span class="sxs-lookup"><span data-stu-id="d88dc-131">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="d88dc-132">如需有關如何建立自訂解析程式的詳細資訊，請參閱 <<c0> [ 新增至 PeerChannel 應用程式的自訂解析程式](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)。</span><span class="sxs-lookup"><span data-stu-id="d88dc-132">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d88dc-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d88dc-133">See also</span></span>
- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [<span data-ttu-id="d88dc-134">對等解析程式</span><span class="sxs-lookup"><span data-stu-id="d88dc-134">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
- [<span data-ttu-id="d88dc-135">將自訂解析程式新增至 PeerChannel 應用程式</span><span class="sxs-lookup"><span data-stu-id="d88dc-135">Adding a Custom Resolver to a PeerChannel Application</span></span>](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)
