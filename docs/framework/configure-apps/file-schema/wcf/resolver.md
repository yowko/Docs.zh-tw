---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: 0dc667f392595d895bd4f2773ab69777d7369446
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738736"
---
# <a name="resolver"></a><span data-ttu-id="02784-101">\<解析程式 ></span><span class="sxs-lookup"><span data-stu-id="02784-101">\<resolver></span></span>
<span data-ttu-id="02784-102">指定對等解析程式，用於將對等網狀結構 ID 解析成一組對等節點位址，這組位址可表示參與網狀結構的數個節點。</span><span class="sxs-lookup"><span data-stu-id="02784-102">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
<span data-ttu-id="02784-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="02784-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="02784-104">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="02784-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="02784-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="02784-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="02784-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netPeerTcpBinding >** ](netpeertcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="02784-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)</span></span>\
<span data-ttu-id="02784-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 ></span><span class="sxs-lookup"><span data-stu-id="02784-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="02784-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<解析程式 >**</span><span class="sxs-lookup"><span data-stu-id="02784-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<resolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02784-109">語法</span><span class="sxs-lookup"><span data-stu-id="02784-109">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02784-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="02784-110">Attributes and Elements</span></span>  
 <span data-ttu-id="02784-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="02784-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02784-112">屬性</span><span class="sxs-lookup"><span data-stu-id="02784-112">Attributes</span></span>  
  
|<span data-ttu-id="02784-113">屬性</span><span class="sxs-lookup"><span data-stu-id="02784-113">Attribute</span></span>|<span data-ttu-id="02784-114">描述</span><span class="sxs-lookup"><span data-stu-id="02784-114">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="02784-115">字串，指定與此服務相關聯的對等解析程式執行個體是 PNRP 專用、自訂解析程式或自動判定。</span><span class="sxs-lookup"><span data-stu-id="02784-115">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="02784-116">此屬性的型別為 <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>。</span><span class="sxs-lookup"><span data-stu-id="02784-116">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="02784-117">字串，指定在對等之間共用轉介的方法。</span><span class="sxs-lookup"><span data-stu-id="02784-117">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="02784-118">此屬性的型別為 <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>。</span><span class="sxs-lookup"><span data-stu-id="02784-118">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="02784-119">子項目</span><span class="sxs-lookup"><span data-stu-id="02784-119">Child Elements</span></span>  
  
|<span data-ttu-id="02784-120">項目</span><span class="sxs-lookup"><span data-stu-id="02784-120">Element</span></span>|<span data-ttu-id="02784-121">描述</span><span class="sxs-lookup"><span data-stu-id="02784-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02784-122">\<標頭 ></span><span class="sxs-lookup"><span data-stu-id="02784-122">\<headers></span></span>](headers.md)|<span data-ttu-id="02784-123">指定自訂對等解析程式服務的設定。</span><span class="sxs-lookup"><span data-stu-id="02784-123">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="02784-124">父項目</span><span class="sxs-lookup"><span data-stu-id="02784-124">Parent Elements</span></span>  
  
|<span data-ttu-id="02784-125">項目</span><span class="sxs-lookup"><span data-stu-id="02784-125">Element</span></span>|<span data-ttu-id="02784-126">描述</span><span class="sxs-lookup"><span data-stu-id="02784-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="02784-127">\<binding ></span><span class="sxs-lookup"><span data-stu-id="02784-127">\<binding></span></span>](bindings.md)|<span data-ttu-id="02784-128">定義[\<netPeerTcpBinding >](netpeertcpbinding.md)的所有系結功能。</span><span class="sxs-lookup"><span data-stu-id="02784-128">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02784-129">備註</span><span class="sxs-lookup"><span data-stu-id="02784-129">Remarks</span></span>  
 <span data-ttu-id="02784-130">對等名稱解析程式是對等通道用來尋找參與對等網狀結構之對等節點的探索服務。</span><span class="sxs-lookup"><span data-stu-id="02784-130">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="02784-131">您也可以使用這個解析程式將節點「註冊」到對等網狀結構，透過這樣的機制使得對等節點成為已知的，並且可從對等網狀結構中取得。</span><span class="sxs-lookup"><span data-stu-id="02784-131">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="02784-132">如需對等解析程式的詳細資訊，請參閱[對等解析](../../../wcf/feature-details/peer-resolvers.md)程式。</span><span class="sxs-lookup"><span data-stu-id="02784-132">For more information on peer resolvers, see [Peer Resolvers](../../../wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02784-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="02784-133">See also</span></span>

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="02784-134">對等解析程式</span><span class="sxs-lookup"><span data-stu-id="02784-134">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="02784-135">[將自訂解決器新增至 PeerChannel 應用程式](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="02784-135">[Adding a Custom Resolver to a PeerChannel Application](https://docs.microsoft.com/previous-versions/ms730105(v=vs.90))</span></span>
