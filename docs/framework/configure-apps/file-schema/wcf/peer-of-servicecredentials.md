---
title: <peer> 的 <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: d726ab460141b1e373a1cabf770b8958f50319eb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59219144"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="f9922-102">\<peer> of \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="f9922-102">\<peer> of \<serviceCredentials></span></span>
<span data-ttu-id="f9922-103">指定對等節點的目前認證。</span><span class="sxs-lookup"><span data-stu-id="f9922-103">Specifies the current credentials for a peer node.</span></span>  
  
 <span data-ttu-id="f9922-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f9922-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f9922-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="f9922-105">\<behaviors></span></span>  
<span data-ttu-id="f9922-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="f9922-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="f9922-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="f9922-107">\<behavior></span></span>  
<span data-ttu-id="f9922-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="f9922-108">\<serviceCredentials></span></span>  
<span data-ttu-id="f9922-109">\<peer></span><span class="sxs-lookup"><span data-stu-id="f9922-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9922-110">語法</span><span class="sxs-lookup"><span data-stu-id="f9922-110">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9922-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f9922-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f9922-112">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="f9922-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9922-113">屬性</span><span class="sxs-lookup"><span data-stu-id="f9922-113">Attributes</span></span>  
 <span data-ttu-id="f9922-114">無。</span><span class="sxs-lookup"><span data-stu-id="f9922-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f9922-115">子元素</span><span class="sxs-lookup"><span data-stu-id="f9922-115">Child Elements</span></span>  
  
|<span data-ttu-id="f9922-116">項目</span><span class="sxs-lookup"><span data-stu-id="f9922-116">Element</span></span>|<span data-ttu-id="f9922-117">描述</span><span class="sxs-lookup"><span data-stu-id="f9922-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9922-118">\<certificate></span><span class="sxs-lookup"><span data-stu-id="f9922-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-peer.md)|<span data-ttu-id="f9922-119">指定要用來簽署與加密對等服務之訊息的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="f9922-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="f9922-120">。</span><span class="sxs-lookup"><span data-stu-id="f9922-120">.</span></span>|  
|[<span data-ttu-id="f9922-121">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="f9922-121">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication.md)|<span data-ttu-id="f9922-122">指定訊息寄件者的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="f9922-122">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="f9922-123">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="f9922-123">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication.md)|<span data-ttu-id="f9922-124">指定對等服務的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="f9922-124">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f9922-125">父項目</span><span class="sxs-lookup"><span data-stu-id="f9922-125">Parent Elements</span></span>  
  
|<span data-ttu-id="f9922-126">項目</span><span class="sxs-lookup"><span data-stu-id="f9922-126">Element</span></span>|<span data-ttu-id="f9922-127">描述</span><span class="sxs-lookup"><span data-stu-id="f9922-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9922-128">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="f9922-128">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="f9922-129">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="f9922-129">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f9922-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9922-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="f9922-131">對等網路</span><span class="sxs-lookup"><span data-stu-id="f9922-131">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="f9922-132">[對等通道訊息驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="f9922-132">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="f9922-133">[對等通道自訂驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="f9922-133">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="f9922-134">保護對等通道應用程式的安全</span><span class="sxs-lookup"><span data-stu-id="f9922-134">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="f9922-135">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="f9922-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
