---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: 39dcb868bd3ff25451509616e1dac7d41f94cfa1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59075870"
---
# <a name="resolver"></a><span data-ttu-id="18ba6-101">\<resolver></span><span class="sxs-lookup"><span data-stu-id="18ba6-101">\<resolver></span></span>
<span data-ttu-id="18ba6-102">指定對等解析程式，用於將對等網狀結構 ID 解析成一組對等節點位址，這組位址可表示參與網狀結構的數個節點。</span><span class="sxs-lookup"><span data-stu-id="18ba6-102">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
 <span data-ttu-id="18ba6-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="18ba6-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="18ba6-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="18ba6-104">\<bindings></span></span>  
<span data-ttu-id="18ba6-105">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="18ba6-105">\<netPeerBinding></span></span>  
<span data-ttu-id="18ba6-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="18ba6-106">\<binding></span></span>  
<span data-ttu-id="18ba6-107">\<resolver></span><span class="sxs-lookup"><span data-stu-id="18ba6-107">\<resolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18ba6-108">語法</span><span class="sxs-lookup"><span data-stu-id="18ba6-108">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18ba6-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="18ba6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="18ba6-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="18ba6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18ba6-111">屬性</span><span class="sxs-lookup"><span data-stu-id="18ba6-111">Attributes</span></span>  
  
|<span data-ttu-id="18ba6-112">屬性</span><span class="sxs-lookup"><span data-stu-id="18ba6-112">Attribute</span></span>|<span data-ttu-id="18ba6-113">描述</span><span class="sxs-lookup"><span data-stu-id="18ba6-113">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="18ba6-114">字串，指定與此服務相關聯的對等解析程式執行個體是 PNRP 專用、自訂解析程式或自動判定。</span><span class="sxs-lookup"><span data-stu-id="18ba6-114">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="18ba6-115">此屬性的型別為 <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>。</span><span class="sxs-lookup"><span data-stu-id="18ba6-115">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="18ba6-116">字串，指定在對等之間共用轉介的方法。</span><span class="sxs-lookup"><span data-stu-id="18ba6-116">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="18ba6-117">此屬性的型別為 <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>。</span><span class="sxs-lookup"><span data-stu-id="18ba6-117">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18ba6-118">子元素</span><span class="sxs-lookup"><span data-stu-id="18ba6-118">Child Elements</span></span>  
  
|<span data-ttu-id="18ba6-119">項目</span><span class="sxs-lookup"><span data-stu-id="18ba6-119">Element</span></span>|<span data-ttu-id="18ba6-120">描述</span><span class="sxs-lookup"><span data-stu-id="18ba6-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18ba6-121">\<headers></span><span class="sxs-lookup"><span data-stu-id="18ba6-121">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="18ba6-122">指定自訂對等解析程式服務的設定。</span><span class="sxs-lookup"><span data-stu-id="18ba6-122">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="18ba6-123">父項目</span><span class="sxs-lookup"><span data-stu-id="18ba6-123">Parent Elements</span></span>  
  
|<span data-ttu-id="18ba6-124">項目</span><span class="sxs-lookup"><span data-stu-id="18ba6-124">Element</span></span>|<span data-ttu-id="18ba6-125">描述</span><span class="sxs-lookup"><span data-stu-id="18ba6-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18ba6-126">\<binding></span><span class="sxs-lookup"><span data-stu-id="18ba6-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="18ba6-127">定義的所有繫結功能[ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="18ba6-127">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18ba6-128">備註</span><span class="sxs-lookup"><span data-stu-id="18ba6-128">Remarks</span></span>  
 <span data-ttu-id="18ba6-129">對等名稱解析程式是對等通道用來尋找參與對等網狀結構之對等節點的探索服務。</span><span class="sxs-lookup"><span data-stu-id="18ba6-129">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="18ba6-130">您也可以使用這個解析程式將節點「註冊」到對等網狀結構，透過這樣的機制使得對等節點成為已知的，並且可從對等網狀結構中取得。</span><span class="sxs-lookup"><span data-stu-id="18ba6-130">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="18ba6-131">如需有關對等解析程式的詳細資訊，請參閱 <<c0> [ 對等解析程式](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)。</span><span class="sxs-lookup"><span data-stu-id="18ba6-131">For more information on peer resolvers, see [Peer Resolvers](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18ba6-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18ba6-132">See also</span></span>

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="18ba6-133">對等解析程式</span><span class="sxs-lookup"><span data-stu-id="18ba6-133">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="18ba6-134">[將自訂解析程式新增至 PeerChannel 應用程式](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="18ba6-134">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
