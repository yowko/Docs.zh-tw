---
title: <resolver>
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: c6f5db96ded422493b819d4d75dda6abc9a1676e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558858"
---
# \<resolver>
<span data-ttu-id="3a781-101">指定對等解析程式，用於將對等網狀結構 ID 解析成一組對等節點位址，這組位址可表示參與網狀結構的數個節點。</span><span class="sxs-lookup"><span data-stu-id="3a781-101">Specifies a peer resolver that is used to resolve a peer mesh ID to a set of peer node addresses that represents several nodes that participate in the mesh.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<resolver>**  
  
## <a name="syntax"></a><span data-ttu-id="3a781-102">語法</span><span class="sxs-lookup"><span data-stu-id="3a781-102">Syntax</span></span>  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"
          referralPolicy="DoNotShare/Service/Share">
</resolver>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a781-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3a781-103">Attributes and Elements</span></span>  
 <span data-ttu-id="3a781-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3a781-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a781-105">屬性</span><span class="sxs-lookup"><span data-stu-id="3a781-105">Attributes</span></span>  
  
|<span data-ttu-id="3a781-106">屬性</span><span class="sxs-lookup"><span data-stu-id="3a781-106">Attribute</span></span>|<span data-ttu-id="3a781-107">描述</span><span class="sxs-lookup"><span data-stu-id="3a781-107">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="3a781-108">字串，指定與此服務相關聯的對等解析程式執行個體是 PNRP 專用、自訂解析程式或自動判定。</span><span class="sxs-lookup"><span data-stu-id="3a781-108">A string that specifies whether the peer resolver instance associated with this service is either PNRP-specific, a custom resolver, or automatically determined.</span></span> <span data-ttu-id="3a781-109">此屬性的型別為 <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>。</span><span class="sxs-lookup"><span data-stu-id="3a781-109">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerResolverMode>.</span></span>|  
|`referralPolicy`|<span data-ttu-id="3a781-110">字串，指定在對等之間共用轉介的方法。</span><span class="sxs-lookup"><span data-stu-id="3a781-110">A string that specifies the way referrals are shared among peers.</span></span> <span data-ttu-id="3a781-111">此屬性的型別為 <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>。</span><span class="sxs-lookup"><span data-stu-id="3a781-111">This attribute is of type <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a781-112">子元素</span><span class="sxs-lookup"><span data-stu-id="3a781-112">Child Elements</span></span>  
  
|<span data-ttu-id="3a781-113">項目</span><span class="sxs-lookup"><span data-stu-id="3a781-113">Element</span></span>|<span data-ttu-id="3a781-114">描述</span><span class="sxs-lookup"><span data-stu-id="3a781-114">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers.md)|<span data-ttu-id="3a781-115">指定自訂對等解析程式服務的設定。</span><span class="sxs-lookup"><span data-stu-id="3a781-115">Specifies settings for a custom peer resolver service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3a781-116">父項目</span><span class="sxs-lookup"><span data-stu-id="3a781-116">Parent Elements</span></span>  
  
|<span data-ttu-id="3a781-117">項目</span><span class="sxs-lookup"><span data-stu-id="3a781-117">Element</span></span>|<span data-ttu-id="3a781-118">描述</span><span class="sxs-lookup"><span data-stu-id="3a781-118">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="3a781-119">定義的所有系結功能 [\<netPeerTcpBinding>](netpeertcpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="3a781-119">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a781-120">備註</span><span class="sxs-lookup"><span data-stu-id="3a781-120">Remarks</span></span>  
 <span data-ttu-id="3a781-121">對等名稱解析程式是對等通道用來尋找參與對等網狀結構之對等節點的探索服務。</span><span class="sxs-lookup"><span data-stu-id="3a781-121">A peer name resolver is a discovery service used by peer channels to find peer nodes that participate in a peer mesh.</span></span> <span data-ttu-id="3a781-122">您也可以使用這個解析程式將節點「註冊」到對等網狀結構，透過這樣的機制使得對等節點成為已知的，並且可從對等網狀結構中取得。</span><span class="sxs-lookup"><span data-stu-id="3a781-122">It is also used to "register" a node with a peer mesh, the mechanism by which the peer node becomes known and available from the peer mesh.</span></span> <span data-ttu-id="3a781-123">如需對等解析程式的詳細資訊，請參閱 [對等解析](../../../wcf/feature-details/peer-resolvers.md)程式。</span><span class="sxs-lookup"><span data-stu-id="3a781-123">For more information on peer resolvers, see [Peer Resolvers](../../../wcf/feature-details/peer-resolvers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a781-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a781-124">See also</span></span>

- <xref:System.ServiceModel.PeerResolver>
- <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>
- <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>
- <xref:System.ServiceModel.Configuration.PeerResolverElement>
- [<span data-ttu-id="3a781-125">對等解析程式</span><span class="sxs-lookup"><span data-stu-id="3a781-125">Peer Resolvers</span></span>](../../../wcf/feature-details/peer-resolvers.md)
- <span data-ttu-id="3a781-126">[將自訂解析程式新增至 PeerChannel 應用程式](/previous-versions/ms730105(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="3a781-126">[Adding a Custom Resolver to a PeerChannel Application](/previous-versions/ms730105(v=vs.90))</span></span>
