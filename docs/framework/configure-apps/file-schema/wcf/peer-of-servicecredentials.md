---
title: <peer> 的 <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: 50415cb9b35d2a2053efa3313a415de518b7e36e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933780"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="78b86-102">\<serviceCredentials > 的\<對等 ></span><span class="sxs-lookup"><span data-stu-id="78b86-102">\<peer> of \<serviceCredentials></span></span>
<span data-ttu-id="78b86-103">指定對等節點的目前認證。</span><span class="sxs-lookup"><span data-stu-id="78b86-103">Specifies the current credentials for a peer node.</span></span>  
  
 <span data-ttu-id="78b86-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="78b86-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="78b86-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="78b86-105">\<behaviors></span></span>  
<span data-ttu-id="78b86-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="78b86-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="78b86-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="78b86-107">\<behavior></span></span>  
<span data-ttu-id="78b86-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="78b86-108">\<serviceCredentials></span></span>  
<span data-ttu-id="78b86-109">\<對等 ></span><span class="sxs-lookup"><span data-stu-id="78b86-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78b86-110">語法</span><span class="sxs-lookup"><span data-stu-id="78b86-110">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="78b86-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="78b86-111">Attributes and Elements</span></span>  
 <span data-ttu-id="78b86-112">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="78b86-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="78b86-113">屬性</span><span class="sxs-lookup"><span data-stu-id="78b86-113">Attributes</span></span>  
 <span data-ttu-id="78b86-114">無。</span><span class="sxs-lookup"><span data-stu-id="78b86-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="78b86-115">子元素</span><span class="sxs-lookup"><span data-stu-id="78b86-115">Child Elements</span></span>  
  
|<span data-ttu-id="78b86-116">項目</span><span class="sxs-lookup"><span data-stu-id="78b86-116">Element</span></span>|<span data-ttu-id="78b86-117">描述</span><span class="sxs-lookup"><span data-stu-id="78b86-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78b86-118">\<certificate></span><span class="sxs-lookup"><span data-stu-id="78b86-118">\<certificate></span></span>](certificate-of-peer.md)|<span data-ttu-id="78b86-119">指定要用來簽署與加密對等服務之訊息的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="78b86-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="78b86-120">.</span><span class="sxs-lookup"><span data-stu-id="78b86-120">.</span></span>|  
|[<span data-ttu-id="78b86-121">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="78b86-121">\<messageSenderAuthentication></span></span>](messagesenderauthentication.md)|<span data-ttu-id="78b86-122">指定訊息寄件者的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="78b86-122">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="78b86-123">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="78b86-123">\<peerAuthentication></span></span>](peerauthentication.md)|<span data-ttu-id="78b86-124">指定對等服務的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="78b86-124">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="78b86-125">父項目</span><span class="sxs-lookup"><span data-stu-id="78b86-125">Parent Elements</span></span>  
  
|<span data-ttu-id="78b86-126">項目</span><span class="sxs-lookup"><span data-stu-id="78b86-126">Element</span></span>|<span data-ttu-id="78b86-127">描述</span><span class="sxs-lookup"><span data-stu-id="78b86-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="78b86-128">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="78b86-128">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="78b86-129">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="78b86-129">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="78b86-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78b86-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="78b86-131">對等網路</span><span class="sxs-lookup"><span data-stu-id="78b86-131">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="78b86-132">[對等通道訊息驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="78b86-132">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="78b86-133">[對等通道自訂驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="78b86-133">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="78b86-134">保護對等通道應用程式的安全</span><span class="sxs-lookup"><span data-stu-id="78b86-134">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="78b86-135">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="78b86-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
