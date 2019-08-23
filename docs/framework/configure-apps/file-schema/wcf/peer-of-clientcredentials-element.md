---
title: <peer> 項目的 <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: 2f1cb5689125e2483a74dcac515beb07abbb7c70
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934040"
---
# <a name="peer-of-clientcredentials-element"></a><span data-ttu-id="824c7-102">\<clientCredentials > 元素\<的對等 ></span><span class="sxs-lookup"><span data-stu-id="824c7-102">\<peer> of \<clientCredentials> Element</span></span>
<span data-ttu-id="824c7-103">指定驗證對等用戶端時所使用的認證。</span><span class="sxs-lookup"><span data-stu-id="824c7-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="824c7-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="824c7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="824c7-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="824c7-105">\<behaviors></span></span>  
<span data-ttu-id="824c7-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="824c7-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="824c7-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="824c7-107">\<behavior></span></span>  
<span data-ttu-id="824c7-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="824c7-108">\<clientCredentials></span></span>  
<span data-ttu-id="824c7-109">\<對等 ></span><span class="sxs-lookup"><span data-stu-id="824c7-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="824c7-110">語法</span><span class="sxs-lookup"><span data-stu-id="824c7-110">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="824c7-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="824c7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="824c7-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="824c7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="824c7-113">屬性</span><span class="sxs-lookup"><span data-stu-id="824c7-113">Attributes</span></span>  
 <span data-ttu-id="824c7-114">無。</span><span class="sxs-lookup"><span data-stu-id="824c7-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="824c7-115">子元素</span><span class="sxs-lookup"><span data-stu-id="824c7-115">Child Elements</span></span>  
  
|<span data-ttu-id="824c7-116">項目</span><span class="sxs-lookup"><span data-stu-id="824c7-116">Element</span></span>|<span data-ttu-id="824c7-117">說明</span><span class="sxs-lookup"><span data-stu-id="824c7-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="824c7-118">\<certificate></span><span class="sxs-lookup"><span data-stu-id="824c7-118">\<certificate></span></span>](certificate-element.md)|<span data-ttu-id="824c7-119">指定要用來簽署與加密對等用戶端之訊息的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="824c7-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="824c7-120">.</span><span class="sxs-lookup"><span data-stu-id="824c7-120">.</span></span>|  
|[<span data-ttu-id="824c7-121">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="824c7-121">\<peerAuthentication></span></span>](peerauthentication-element.md)|<span data-ttu-id="824c7-122">指定對等用戶端的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="824c7-122">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="824c7-123">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="824c7-123">\<messageSenderAuthentication></span></span>](messagesenderauthentication-element.md)|<span data-ttu-id="824c7-124">指定訊息寄件者的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="824c7-124">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="824c7-125">父項目</span><span class="sxs-lookup"><span data-stu-id="824c7-125">Parent Elements</span></span>  
  
|<span data-ttu-id="824c7-126">項目</span><span class="sxs-lookup"><span data-stu-id="824c7-126">Element</span></span>|<span data-ttu-id="824c7-127">描述</span><span class="sxs-lookup"><span data-stu-id="824c7-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="824c7-128">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="824c7-128">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="824c7-129">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="824c7-129">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="824c7-130">備註</span><span class="sxs-lookup"><span data-stu-id="824c7-130">Remarks</span></span>  
 <span data-ttu-id="824c7-131">這個組態項目會指定對等節點用於向網狀結構中其他節點驗證其本身的認證，以及對等節點用來驗證其他對等節點的驗證設定。</span><span class="sxs-lookup"><span data-stu-id="824c7-131">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="824c7-132">如需詳細資訊, 請參閱[對等通道訊息驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))和[保護對等通道應用程式](../../../wcf/feature-details/securing-peer-channel-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="824c7-132">For more information, see [Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) and [Securing Peer Channel Applications](../../../wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="824c7-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="824c7-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="824c7-134">對等網路</span><span class="sxs-lookup"><span data-stu-id="824c7-134">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="824c7-135">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="824c7-135">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- <span data-ttu-id="824c7-136">[對等通道訊息驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="824c7-136">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="824c7-137">[對等通道自訂驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="824c7-137">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="824c7-138">保護對等通道應用程式的安全</span><span class="sxs-lookup"><span data-stu-id="824c7-138">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="824c7-139">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="824c7-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
