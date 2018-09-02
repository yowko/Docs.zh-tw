---
title: '&lt;serviceCredentials&gt; 的 &lt;peer&gt;'
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: 94f93a7955af3bff1c17e59a11af3fad85c9134d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43399839"
---
# <a name="ltpeergt-of-ltservicecredentialsgt"></a><span data-ttu-id="bc421-102">&lt;serviceCredentials&gt; 的 &lt;peer&gt;</span><span class="sxs-lookup"><span data-stu-id="bc421-102">&lt;peer&gt; of &lt;serviceCredentials&gt;</span></span>
<span data-ttu-id="bc421-103">指定對等節點的目前認證。</span><span class="sxs-lookup"><span data-stu-id="bc421-103">Specifies the current credentials for a peer node.</span></span>  
  
 <span data-ttu-id="bc421-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bc421-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="bc421-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="bc421-105">\<behaviors></span></span>  
<span data-ttu-id="bc421-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="bc421-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="bc421-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="bc421-107">\<behavior></span></span>  
<span data-ttu-id="bc421-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="bc421-108">\<serviceCredentials></span></span>  
<span data-ttu-id="bc421-109">\<對等電腦 ></span><span class="sxs-lookup"><span data-stu-id="bc421-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc421-110">語法</span><span class="sxs-lookup"><span data-stu-id="bc421-110">Syntax</span></span>  
  
```xml  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc421-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bc421-111">Attributes and Elements</span></span>  
 <span data-ttu-id="bc421-112">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="bc421-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc421-113">屬性</span><span class="sxs-lookup"><span data-stu-id="bc421-113">Attributes</span></span>  
 <span data-ttu-id="bc421-114">無。</span><span class="sxs-lookup"><span data-stu-id="bc421-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bc421-115">子元素</span><span class="sxs-lookup"><span data-stu-id="bc421-115">Child Elements</span></span>  
  
|<span data-ttu-id="bc421-116">項目</span><span class="sxs-lookup"><span data-stu-id="bc421-116">Element</span></span>|<span data-ttu-id="bc421-117">描述</span><span class="sxs-lookup"><span data-stu-id="bc421-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc421-118">\<certificate></span><span class="sxs-lookup"><span data-stu-id="bc421-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-of-peer.md)|<span data-ttu-id="bc421-119">指定要用來簽署與加密對等服務之訊息的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="bc421-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="bc421-120">。</span><span class="sxs-lookup"><span data-stu-id="bc421-120">.</span></span>|  
|[<span data-ttu-id="bc421-121">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="bc421-121">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication.md)|<span data-ttu-id="bc421-122">指定訊息寄件者的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="bc421-122">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="bc421-123">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="bc421-123">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication.md)|<span data-ttu-id="bc421-124">指定對等服務的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="bc421-124">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bc421-125">父項目</span><span class="sxs-lookup"><span data-stu-id="bc421-125">Parent Elements</span></span>  
  
|<span data-ttu-id="bc421-126">項目</span><span class="sxs-lookup"><span data-stu-id="bc421-126">Element</span></span>|<span data-ttu-id="bc421-127">描述</span><span class="sxs-lookup"><span data-stu-id="bc421-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc421-128">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="bc421-128">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="bc421-129">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="bc421-129">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bc421-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc421-130">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [<span data-ttu-id="bc421-131">對等網路</span><span class="sxs-lookup"><span data-stu-id="bc421-131">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="bc421-132">對等通道訊息驗證</span><span class="sxs-lookup"><span data-stu-id="bc421-132">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="bc421-133">對等通道自訂驗證</span><span class="sxs-lookup"><span data-stu-id="bc421-133">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="bc421-134">保護對等通道應用程式的安全</span><span class="sxs-lookup"><span data-stu-id="bc421-134">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [<span data-ttu-id="bc421-135">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="bc421-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
