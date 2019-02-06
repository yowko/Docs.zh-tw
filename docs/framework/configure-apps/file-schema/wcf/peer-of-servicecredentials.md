---
title: <peer> 的 <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: c1df586916ebf165942c66ff2113c3199e31c3aa
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/06/2019
ms.locfileid: "55758517"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="cc7a0-102">\<peer> of \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="cc7a0-102">\<peer> of \<serviceCredentials></span></span>
<span data-ttu-id="cc7a0-103">指定對等節點的目前認證。</span><span class="sxs-lookup"><span data-stu-id="cc7a0-103">Specifies the current credentials for a peer node.</span></span>  
  
 <span data-ttu-id="cc7a0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cc7a0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cc7a0-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="cc7a0-105">\<behaviors></span></span>  
<span data-ttu-id="cc7a0-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="cc7a0-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="cc7a0-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="cc7a0-107">\<behavior></span></span>  
<span data-ttu-id="cc7a0-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="cc7a0-108">\<serviceCredentials></span></span>  
<span data-ttu-id="cc7a0-109">\<peer></span><span class="sxs-lookup"><span data-stu-id="cc7a0-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc7a0-110">語法</span><span class="sxs-lookup"><span data-stu-id="cc7a0-110">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cc7a0-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cc7a0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cc7a0-112">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="cc7a0-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cc7a0-113">屬性</span><span class="sxs-lookup"><span data-stu-id="cc7a0-113">Attributes</span></span>  
 <span data-ttu-id="cc7a0-114">無。</span><span class="sxs-lookup"><span data-stu-id="cc7a0-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cc7a0-115">子元素</span><span class="sxs-lookup"><span data-stu-id="cc7a0-115">Child Elements</span></span>  
  
|<span data-ttu-id="cc7a0-116">項目</span><span class="sxs-lookup"><span data-stu-id="cc7a0-116">Element</span></span>|<span data-ttu-id="cc7a0-117">描述</span><span class="sxs-lookup"><span data-stu-id="cc7a0-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc7a0-118">\<certificate></span><span class="sxs-lookup"><span data-stu-id="cc7a0-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-peer.md)|<span data-ttu-id="cc7a0-119">指定要用來簽署與加密對等服務之訊息的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="cc7a0-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="cc7a0-120">。</span><span class="sxs-lookup"><span data-stu-id="cc7a0-120">.</span></span>|  
|[<span data-ttu-id="cc7a0-121">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="cc7a0-121">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication.md)|<span data-ttu-id="cc7a0-122">指定訊息寄件者的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="cc7a0-122">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="cc7a0-123">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="cc7a0-123">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication.md)|<span data-ttu-id="cc7a0-124">指定對等服務的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="cc7a0-124">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cc7a0-125">父項目</span><span class="sxs-lookup"><span data-stu-id="cc7a0-125">Parent Elements</span></span>  
  
|<span data-ttu-id="cc7a0-126">項目</span><span class="sxs-lookup"><span data-stu-id="cc7a0-126">Element</span></span>|<span data-ttu-id="cc7a0-127">描述</span><span class="sxs-lookup"><span data-stu-id="cc7a0-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cc7a0-128">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="cc7a0-128">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="cc7a0-129">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="cc7a0-129">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cc7a0-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc7a0-130">See also</span></span>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="cc7a0-131">對等網路</span><span class="sxs-lookup"><span data-stu-id="cc7a0-131">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="cc7a0-132">[對等通道訊息驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="cc7a0-132">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="cc7a0-133">[對等通道自訂驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="cc7a0-133">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="cc7a0-134">保護對等通道應用程式的安全</span><span class="sxs-lookup"><span data-stu-id="cc7a0-134">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="cc7a0-135">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="cc7a0-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
