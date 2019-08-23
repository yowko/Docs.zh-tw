---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: e3a9ee00aab6ab48a1ba891565b63824e62b20fe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934220"
---
# <a name="resolver"></a><span data-ttu-id="73164-101">\<resolver></span><span class="sxs-lookup"><span data-stu-id="73164-101">\<resolver></span></span>
<span data-ttu-id="73164-102">指定對等解析程式，用於將對等網狀結構 ID 解析成一組對等節點位址，這組位址可表示參與網狀結構的數個節點。</span><span class="sxs-lookup"><span data-stu-id="73164-102">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
 <span data-ttu-id="73164-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="73164-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="73164-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="73164-104">\<bindings></span></span>  
<span data-ttu-id="73164-105">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="73164-105">\<netPeerBinding></span></span>  
<span data-ttu-id="73164-106">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="73164-106">\<binding></span></span>  
<span data-ttu-id="73164-107">\<resolver></span><span class="sxs-lookup"><span data-stu-id="73164-107">\<resolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73164-108">語法</span><span class="sxs-lookup"><span data-stu-id="73164-108">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73164-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="73164-109">Attributes and Elements</span></span>  
 <span data-ttu-id="73164-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="73164-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73164-111">屬性</span><span class="sxs-lookup"><span data-stu-id="73164-111">Attributes</span></span>  
  
|<span data-ttu-id="73164-112">屬性</span><span class="sxs-lookup"><span data-stu-id="73164-112">Attribute</span></span>|<span data-ttu-id="73164-113">描述</span><span class="sxs-lookup"><span data-stu-id="73164-113">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="73164-114">字串，指定與此服務相關聯的對等解析程式執行個體是 PNRP 專用、自訂解析程式或自動判定。</span><span class="sxs-lookup"><span data-stu-id="73164-114">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="73164-115">此屬性的型別為 <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>。</span><span class="sxs-lookup"><span data-stu-id="73164-115">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="73164-116">字串，指定在對等之間共用轉介的方法。</span><span class="sxs-lookup"><span data-stu-id="73164-116">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="73164-117">此屬性的型別為 <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>。</span><span class="sxs-lookup"><span data-stu-id="73164-117">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73164-118">子元素</span><span class="sxs-lookup"><span data-stu-id="73164-118">Child Elements</span></span>  
  
|<span data-ttu-id="73164-119">項目</span><span class="sxs-lookup"><span data-stu-id="73164-119">Element</span></span>|<span data-ttu-id="73164-120">描述</span><span class="sxs-lookup"><span data-stu-id="73164-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73164-121">\<headers></span><span class="sxs-lookup"><span data-stu-id="73164-121">\<headers></span></span>](headers.md)|<span data-ttu-id="73164-122">指定自訂對等解析程式服務的設定。</span><span class="sxs-lookup"><span data-stu-id="73164-122">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="73164-123">父項目</span><span class="sxs-lookup"><span data-stu-id="73164-123">Parent Elements</span></span>  
  
|<span data-ttu-id="73164-124">項目</span><span class="sxs-lookup"><span data-stu-id="73164-124">Element</span></span>|<span data-ttu-id="73164-125">說明</span><span class="sxs-lookup"><span data-stu-id="73164-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73164-126">\<binding></span><span class="sxs-lookup"><span data-stu-id="73164-126">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="73164-127">定義[ \<netPeerTcpBinding >](netpeertcpbinding.md)的所有系結功能。</span><span class="sxs-lookup"><span data-stu-id="73164-127">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73164-128">備註</span><span class="sxs-lookup"><span data-stu-id="73164-128">Remarks</span></span>  
 <span data-ttu-id="73164-129">對等名稱解析程式是對等通道用來尋找參與對等網狀結構之對等節點的探索服務。</span><span class="sxs-lookup"><span data-stu-id="73164-129">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="73164-130">您也可以使用這個解析程式將節點「註冊」到對等網狀結構，透過這樣的機制使得對等節點成為已知的，並且可從對等網狀結構中取得。</span><span class="sxs-lookup"><span data-stu-id="73164-130">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="73164-131">如需對等解析程式的詳細資訊, 請參閱[對等解析](../../../wcf/feature-details/peer-resolvers.md)程式。</span><span class="sxs-lookup"><span data-stu-id="73164-131">For more information on peer resolvers, see [Peer Resolvers](../../../wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73164-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73164-132">See also</span></span>

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="73164-133">對等解析程式</span><span class="sxs-lookup"><span data-stu-id="73164-133">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="73164-134">[將自訂解決器新增至 PeerChannel 應用程式](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="73164-134">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
