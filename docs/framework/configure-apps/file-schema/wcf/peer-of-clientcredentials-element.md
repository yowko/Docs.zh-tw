---
title: "&lt;clientCredentials&gt; 的 &lt;peer&gt; 項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f26321afdbe53c4ab3750eae4a7a730bcb5ae4e4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltpeergt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="e9e6e-102">&lt;clientCredentials&gt; 的 &lt;peer&gt; 項目</span><span class="sxs-lookup"><span data-stu-id="e9e6e-102">&lt;peer&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="e9e6e-103">指定驗證對等用戶端時所使用的認證。</span><span class="sxs-lookup"><span data-stu-id="e9e6e-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="e9e6e-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e9e6e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e9e6e-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="e9e6e-105">\<behaviors></span></span>  
<span data-ttu-id="e9e6e-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e9e6e-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="e9e6e-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="e9e6e-107">\<behavior></span></span>  
<span data-ttu-id="e9e6e-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="e9e6e-108">\<clientCredentials></span></span>  
<span data-ttu-id="e9e6e-109">\<對等 ></span><span class="sxs-lookup"><span data-stu-id="e9e6e-109">\<peer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9e6e-110">語法</span><span class="sxs-lookup"><span data-stu-id="e9e6e-110">Syntax</span></span>  
  
```xml  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9e6e-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e9e6e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e9e6e-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e9e6e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9e6e-113">屬性</span><span class="sxs-lookup"><span data-stu-id="e9e6e-113">Attributes</span></span>  
 <span data-ttu-id="e9e6e-114">無。</span><span class="sxs-lookup"><span data-stu-id="e9e6e-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e9e6e-115">子項目</span><span class="sxs-lookup"><span data-stu-id="e9e6e-115">Child Elements</span></span>  
  
|<span data-ttu-id="e9e6e-116">項目</span><span class="sxs-lookup"><span data-stu-id="e9e6e-116">Element</span></span>|<span data-ttu-id="e9e6e-117">說明</span><span class="sxs-lookup"><span data-stu-id="e9e6e-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9e6e-118">\<憑證 ></span><span class="sxs-lookup"><span data-stu-id="e9e6e-118">\<certificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)|<span data-ttu-id="e9e6e-119">指定要用來簽署與加密對等用戶端之訊息的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="e9e6e-119">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="e9e6e-120">。</span><span class="sxs-lookup"><span data-stu-id="e9e6e-120">.</span></span>|  
|[<span data-ttu-id="e9e6e-121">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="e9e6e-121">\<peerAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)|<span data-ttu-id="e9e6e-122">指定對等用戶端的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="e9e6e-122">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="e9e6e-123">\<messageSenderAuthentication ></span><span class="sxs-lookup"><span data-stu-id="e9e6e-123">\<messageSenderAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)|<span data-ttu-id="e9e6e-124">指定訊息寄件者的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="e9e6e-124">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e9e6e-125">父項目</span><span class="sxs-lookup"><span data-stu-id="e9e6e-125">Parent Elements</span></span>  
  
|<span data-ttu-id="e9e6e-126">項目</span><span class="sxs-lookup"><span data-stu-id="e9e6e-126">Element</span></span>|<span data-ttu-id="e9e6e-127">說明</span><span class="sxs-lookup"><span data-stu-id="e9e6e-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e9e6e-128">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="e9e6e-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="e9e6e-129">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="e9e6e-129">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9e6e-130">備註</span><span class="sxs-lookup"><span data-stu-id="e9e6e-130">Remarks</span></span>  
 <span data-ttu-id="e9e6e-131">這個組態項目會指定對等節點用於向網狀結構中其他節點驗證其本身的認證，以及對等節點用來驗證其他對等節點的驗證設定。</span><span class="sxs-lookup"><span data-stu-id="e9e6e-131">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="e9e6e-132">如需詳細資訊，請參閱[對等通道訊息驗證](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)和[保護對等通道應用程式](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="e9e6e-132">For more information, see [Peer Channel Message Authentication](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95) and [Securing Peer Channel Applications](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9e6e-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e9e6e-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [<span data-ttu-id="e9e6e-134">對等網路功能</span><span class="sxs-lookup"><span data-stu-id="e9e6e-134">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="e9e6e-135">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="e9e6e-135">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="e9e6e-136">對等通道訊息驗證</span><span class="sxs-lookup"><span data-stu-id="e9e6e-136">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="e9e6e-137">對等通道自訂驗證</span><span class="sxs-lookup"><span data-stu-id="e9e6e-137">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="e9e6e-138">保護對等通道應用程式</span><span class="sxs-lookup"><span data-stu-id="e9e6e-138">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [<span data-ttu-id="e9e6e-139">保護服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="e9e6e-139">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
