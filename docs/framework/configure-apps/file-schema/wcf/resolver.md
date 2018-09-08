---
title: '&lt;resolver&gt;'
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: 48b6b6ca315f7ab63a8f7a64b97167fa04fe1e4e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180796"
---
# <a name="ltresolvergt"></a><span data-ttu-id="b1f99-102">&lt;resolver&gt;</span><span class="sxs-lookup"><span data-stu-id="b1f99-102">&lt;resolver&gt;</span></span>
<span data-ttu-id="b1f99-103">指定對等解析程式，用於將對等網狀結構 ID 解析成一組對等節點位址，這組位址可表示參與網狀結構的數個節點。</span><span class="sxs-lookup"><span data-stu-id="b1f99-103">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
 <span data-ttu-id="b1f99-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b1f99-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b1f99-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="b1f99-105">\<bindings></span></span>  
<span data-ttu-id="b1f99-106">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="b1f99-106">\<netPeerBinding></span></span>  
<span data-ttu-id="b1f99-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="b1f99-107">\<binding></span></span>  
<span data-ttu-id="b1f99-108">\<resolver></span><span class="sxs-lookup"><span data-stu-id="b1f99-108">\<resolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1f99-109">語法</span><span class="sxs-lookup"><span data-stu-id="b1f99-109">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"  
   referralPolicy="DoNotShare/Service/Share">  
</resolver>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1f99-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b1f99-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b1f99-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b1f99-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1f99-112">屬性</span><span class="sxs-lookup"><span data-stu-id="b1f99-112">Attributes</span></span>  
  
|<span data-ttu-id="b1f99-113">屬性</span><span class="sxs-lookup"><span data-stu-id="b1f99-113">Attribute</span></span>|<span data-ttu-id="b1f99-114">描述</span><span class="sxs-lookup"><span data-stu-id="b1f99-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="b1f99-115">字串，指定與此服務相關聯的對等解析程式執行個體是 PNRP 專用、自訂解析程式或自動判定。</span><span class="sxs-lookup"><span data-stu-id="b1f99-115">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="b1f99-116">此屬性的型別為 <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>。</span><span class="sxs-lookup"><span data-stu-id="b1f99-116">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="b1f99-117">字串，指定在對等之間共用轉介的方法。</span><span class="sxs-lookup"><span data-stu-id="b1f99-117">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="b1f99-118">此屬性的型別為 <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>。</span><span class="sxs-lookup"><span data-stu-id="b1f99-118">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1f99-119">子元素</span><span class="sxs-lookup"><span data-stu-id="b1f99-119">Child Elements</span></span>  
  
|<span data-ttu-id="b1f99-120">項目</span><span class="sxs-lookup"><span data-stu-id="b1f99-120">Element</span></span>|<span data-ttu-id="b1f99-121">描述</span><span class="sxs-lookup"><span data-stu-id="b1f99-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1f99-122">\<headers></span><span class="sxs-lookup"><span data-stu-id="b1f99-122">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="b1f99-123">指定自訂對等解析程式服務的設定。</span><span class="sxs-lookup"><span data-stu-id="b1f99-123">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b1f99-124">父項目</span><span class="sxs-lookup"><span data-stu-id="b1f99-124">Parent Elements</span></span>  
  
|<span data-ttu-id="b1f99-125">項目</span><span class="sxs-lookup"><span data-stu-id="b1f99-125">Element</span></span>|<span data-ttu-id="b1f99-126">描述</span><span class="sxs-lookup"><span data-stu-id="b1f99-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1f99-127">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="b1f99-127">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="b1f99-128">定義的所有繫結功能[ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="b1f99-128">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1f99-129">備註</span><span class="sxs-lookup"><span data-stu-id="b1f99-129">Remarks</span></span>  
 <span data-ttu-id="b1f99-130">對等名稱解析程式是對等通道用來尋找參與對等網狀結構之對等節點的探索服務。</span><span class="sxs-lookup"><span data-stu-id="b1f99-130">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="b1f99-131">您也可以使用這個解析程式將節點「註冊」到對等網狀結構，透過這樣的機制使得對等節點成為已知的，並且可從對等網狀結構中取得。</span><span class="sxs-lookup"><span data-stu-id="b1f99-131">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="b1f99-132">如需有關對等解析程式的詳細資訊，請參閱 <<c0> [ 對等解析程式](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)。</span><span class="sxs-lookup"><span data-stu-id="b1f99-132">For more information on peer resolvers, see [Peer Resolvers](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1f99-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1f99-133">See Also</span></span>  
 <xref:System.ServiceModel.PeerResolver>  
 <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement>  
 [<span data-ttu-id="b1f99-134">對等解析程式</span><span class="sxs-lookup"><span data-stu-id="b1f99-134">Peer Resolvers</span></span>](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [<span data-ttu-id="b1f99-135">將自訂解析程式新增至 PeerChannel 應用程式</span><span class="sxs-lookup"><span data-stu-id="b1f99-135">Adding a Custom Resolver to a PeerChannel Application</span></span>](https://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)
