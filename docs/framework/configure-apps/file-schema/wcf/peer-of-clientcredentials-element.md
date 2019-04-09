---
title: <peer> <clientCredentials>項目
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: 7074ee992755557d7e5503035c89bdbefd678792
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107233"
---
# <a name="peer-of-clientcredentials-element"></a><span data-ttu-id="c9cce-102">\<對等個體 > 的\<clientCredentials > 項目</span><span class="sxs-lookup"><span data-stu-id="c9cce-102">\<peer> of \<clientCredentials> Element</span></span>
<span data-ttu-id="c9cce-103">指定驗證對等用戶端時所使用的認證。</span><span class="sxs-lookup"><span data-stu-id="c9cce-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="c9cce-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c9cce-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c9cce-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="c9cce-105">\<behaviors></span></span>  
<span data-ttu-id="c9cce-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="c9cce-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="c9cce-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="c9cce-107">\<behavior></span></span>  
<span data-ttu-id="c9cce-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="c9cce-108">\<clientCredentials></span></span>  
<span data-ttu-id="c9cce-109">\<peer></span><span class="sxs-lookup"><span data-stu-id="c9cce-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9cce-110">語法</span><span class="sxs-lookup"><span data-stu-id="c9cce-110">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9cce-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c9cce-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c9cce-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c9cce-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9cce-113">屬性</span><span class="sxs-lookup"><span data-stu-id="c9cce-113">Attributes</span></span>  
 <span data-ttu-id="c9cce-114">無。</span><span class="sxs-lookup"><span data-stu-id="c9cce-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c9cce-115">子元素</span><span class="sxs-lookup"><span data-stu-id="c9cce-115">Child Elements</span></span>  
  
|<span data-ttu-id="c9cce-116">項目</span><span class="sxs-lookup"><span data-stu-id="c9cce-116">Element</span></span>|<span data-ttu-id="c9cce-117">描述</span><span class="sxs-lookup"><span data-stu-id="c9cce-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9cce-118">\<certificate></span><span class="sxs-lookup"><span data-stu-id="c9cce-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)|<span data-ttu-id="c9cce-119">指定要用來簽署與加密對等用戶端之訊息的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="c9cce-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="c9cce-120">。</span><span class="sxs-lookup"><span data-stu-id="c9cce-120">.</span></span>|  
|[<span data-ttu-id="c9cce-121">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="c9cce-121">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)|<span data-ttu-id="c9cce-122">指定對等用戶端的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="c9cce-122">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="c9cce-123">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="c9cce-123">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)|<span data-ttu-id="c9cce-124">指定訊息寄件者的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="c9cce-124">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c9cce-125">父項目</span><span class="sxs-lookup"><span data-stu-id="c9cce-125">Parent Elements</span></span>  
  
|<span data-ttu-id="c9cce-126">項目</span><span class="sxs-lookup"><span data-stu-id="c9cce-126">Element</span></span>|<span data-ttu-id="c9cce-127">描述</span><span class="sxs-lookup"><span data-stu-id="c9cce-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9cce-128">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="c9cce-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="c9cce-129">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="c9cce-129">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9cce-130">備註</span><span class="sxs-lookup"><span data-stu-id="c9cce-130">Remarks</span></span>  
 <span data-ttu-id="c9cce-131">這個組態項目會指定對等節點用於向網狀結構中其他節點驗證其本身的認證，以及對等節點用來驗證其他對等節點的驗證設定。</span><span class="sxs-lookup"><span data-stu-id="c9cce-131">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="c9cce-132">如需詳細資訊，請參閱 <<c0> [ 對等通道訊息驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))並[保護的對等通道應用程式](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="c9cce-132">For more information, see [Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) and [Securing Peer Channel Applications](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9cce-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9cce-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="c9cce-134">對等網路</span><span class="sxs-lookup"><span data-stu-id="c9cce-134">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="c9cce-135">確保用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="c9cce-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="c9cce-136">對等通道訊息驗證</span><span class="sxs-lookup"><span data-stu-id="c9cce-136">Peer Channel Message Authentication</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [<span data-ttu-id="c9cce-137">對等通道自訂驗證</span><span class="sxs-lookup"><span data-stu-id="c9cce-137">Peer Channel Custom Authentication</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [<span data-ttu-id="c9cce-138">確保對等通道應用程式安全</span><span class="sxs-lookup"><span data-stu-id="c9cce-138">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="c9cce-139">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="c9cce-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
