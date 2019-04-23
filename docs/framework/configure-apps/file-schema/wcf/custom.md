---
title: <custom>
ms.date: 03/30/2017
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
ms.openlocfilehash: 18359e871feed17a11006d0b2998907faf25c158
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59106583"
---
# <a name="custom"></a><span data-ttu-id="e5b64-101">\<custom></span><span class="sxs-lookup"><span data-stu-id="e5b64-101">\<custom></span></span>
<span data-ttu-id="e5b64-102">指定自訂對等解析程式服務的設定。</span><span class="sxs-lookup"><span data-stu-id="e5b64-102">Specifies settings for a custom peer resolver service.</span></span>  
  
<span data-ttu-id="e5b64-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e5b64-103">\<system.serviceModel></span></span>  
<span data-ttu-id="e5b64-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="e5b64-104">\<bindings></span></span>  
<span data-ttu-id="e5b64-105">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="e5b64-105">\<netPeerBinding></span></span>  
<span data-ttu-id="e5b64-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="e5b64-106">\<binding></span></span>  
<span data-ttu-id="e5b64-107">\<resolver></span><span class="sxs-lookup"><span data-stu-id="e5b64-107">\<resolver></span></span>  
<span data-ttu-id="e5b64-108">\<custom></span><span class="sxs-lookup"><span data-stu-id="e5b64-108">\<custom></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5b64-109">語法</span><span class="sxs-lookup"><span data-stu-id="e5b64-109">Syntax</span></span>  
  
```xml  
<custom address="Uri"
        resolverType="String">
  <headers/>
  <identity/>
</custom>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5b64-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e5b64-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e5b64-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e5b64-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5b64-112">屬性</span><span class="sxs-lookup"><span data-stu-id="e5b64-112">Attributes</span></span>  
  
|<span data-ttu-id="e5b64-113">屬性</span><span class="sxs-lookup"><span data-stu-id="e5b64-113">Attribute</span></span>|<span data-ttu-id="e5b64-114">描述</span><span class="sxs-lookup"><span data-stu-id="e5b64-114">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="e5b64-115">URI，這個 URI 會指定裝載自訂解析程式服務之對等節點的端點位址。</span><span class="sxs-lookup"><span data-stu-id="e5b64-115">A URI that specifies the endpoint address of the peer node that hosts the custom peer resolver service.</span></span>|  
|`resolverType`|<span data-ttu-id="e5b64-116">字串，這個字串會指定自訂對等解析服務之型別。</span><span class="sxs-lookup"><span data-stu-id="e5b64-116">A string that specifies the type of the custom peer resolver service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e5b64-117">子元素</span><span class="sxs-lookup"><span data-stu-id="e5b64-117">Child Elements</span></span>  
  
|<span data-ttu-id="e5b64-118">項目</span><span class="sxs-lookup"><span data-stu-id="e5b64-118">Element</span></span>|<span data-ttu-id="e5b64-119">描述</span><span class="sxs-lookup"><span data-stu-id="e5b64-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5b64-120">\<identity></span><span class="sxs-lookup"><span data-stu-id="e5b64-120">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="e5b64-121">指定使用這個項目設定的自訂對等解析程式的身分識別。</span><span class="sxs-lookup"><span data-stu-id="e5b64-121">Specifies the identity for custom peer resolvers configured with this element.</span></span> <span data-ttu-id="e5b64-122">此項目的型別為 <xref:System.ServiceModel.Configuration.IdentityElement>。</span><span class="sxs-lookup"><span data-stu-id="e5b64-122">This element is of type <xref:System.ServiceModel.Configuration.IdentityElement>.</span></span>|  
|[<span data-ttu-id="e5b64-123">\<headers></span><span class="sxs-lookup"><span data-stu-id="e5b64-123">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|<span data-ttu-id="e5b64-124">位址標頭的集合，用於自訂對等解析程式所處理的 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="e5b64-124">A collection of address header used for SOAP messages handled by the custom peer resolver.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e5b64-125">父項目</span><span class="sxs-lookup"><span data-stu-id="e5b64-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e5b64-126">項目</span><span class="sxs-lookup"><span data-stu-id="e5b64-126">Element</span></span>|<span data-ttu-id="e5b64-127">描述</span><span class="sxs-lookup"><span data-stu-id="e5b64-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e5b64-128">\<resolver></span><span class="sxs-lookup"><span data-stu-id="e5b64-128">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="e5b64-129">對等解析程式，這個程式可用於將對等網狀結構 ID 解析成一組對等節點位址，這組位址可表示參與網狀結構的數個節點。</span><span class="sxs-lookup"><span data-stu-id="e5b64-129">A peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5b64-130">備註</span><span class="sxs-lookup"><span data-stu-id="e5b64-130">Remarks</span></span>  
 <span data-ttu-id="e5b64-131">這個項目定義自訂對等解析程式服務的基本設定，包括裝載服務之對等的端點位址以及任何特定繫結設定。</span><span class="sxs-lookup"><span data-stu-id="e5b64-131">This element defines the basic settings for a custom peer resolver service, including the endpoint address of the peer hosting the service and any specific binding settings.</span></span> <span data-ttu-id="e5b64-132">如需有關如何建立自訂解析程式的詳細資訊，請參閱 <<c0> [ 新增至 PeerChannel 應用程式的自訂解析程式](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))。</span><span class="sxs-lookup"><span data-stu-id="e5b64-132">For more information on creating a custom resolver, see [Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5b64-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5b64-133">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>
- <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>
- <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>
- <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>
- [<span data-ttu-id="e5b64-134">對等解析程式</span><span class="sxs-lookup"><span data-stu-id="e5b64-134">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="e5b64-135">[將自訂解析程式新增至 PeerChannel 應用程式](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="e5b64-135">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
