---
title: <peer> 項目的 <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: dce7ef64de1e3eb248e3553c97cbce8e9b205b4c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400104"
---
# <a name="peer-of-clientcredentials-element"></a><span data-ttu-id="7b9ab-102">\<clientCredentials > 元素\<的對等 ></span><span class="sxs-lookup"><span data-stu-id="7b9ab-102">\<peer> of \<clientCredentials> Element</span></span>
<span data-ttu-id="7b9ab-103">指定驗證對等用戶端時所使用的認證。</span><span class="sxs-lookup"><span data-stu-id="7b9ab-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
<span data-ttu-id="7b9ab-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7b9ab-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7b9ab-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7b9ab-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7b9ab-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="7b9ab-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="7b9ab-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="7b9ab-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="7b9ab-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="7b9ab-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="7b9ab-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="7b9ab-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="7b9ab-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<對等 >**</span><span class="sxs-lookup"><span data-stu-id="7b9ab-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b9ab-111">語法</span><span class="sxs-lookup"><span data-stu-id="7b9ab-111">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b9ab-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7b9ab-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7b9ab-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7b9ab-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b9ab-114">屬性</span><span class="sxs-lookup"><span data-stu-id="7b9ab-114">Attributes</span></span>  
 <span data-ttu-id="7b9ab-115">無。</span><span class="sxs-lookup"><span data-stu-id="7b9ab-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7b9ab-116">子元素</span><span class="sxs-lookup"><span data-stu-id="7b9ab-116">Child Elements</span></span>  
  
|<span data-ttu-id="7b9ab-117">項目</span><span class="sxs-lookup"><span data-stu-id="7b9ab-117">Element</span></span>|<span data-ttu-id="7b9ab-118">說明</span><span class="sxs-lookup"><span data-stu-id="7b9ab-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b9ab-119">\<certificate></span><span class="sxs-lookup"><span data-stu-id="7b9ab-119">\<certificate></span></span>](certificate-element.md)|<span data-ttu-id="7b9ab-120">指定要用來簽署與加密對等用戶端之訊息的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="7b9ab-120">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="7b9ab-121">.</span><span class="sxs-lookup"><span data-stu-id="7b9ab-121">.</span></span>|  
|[<span data-ttu-id="7b9ab-122">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="7b9ab-122">\<peerAuthentication></span></span>](peerauthentication-element.md)|<span data-ttu-id="7b9ab-123">指定對等用戶端的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="7b9ab-123">Specifies authentication options for peer clients.</span></span>|  
|[<span data-ttu-id="7b9ab-124">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="7b9ab-124">\<messageSenderAuthentication></span></span>](messagesenderauthentication-element.md)|<span data-ttu-id="7b9ab-125">指定訊息寄件者的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="7b9ab-125">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7b9ab-126">父項目</span><span class="sxs-lookup"><span data-stu-id="7b9ab-126">Parent Elements</span></span>  
  
|<span data-ttu-id="7b9ab-127">項目</span><span class="sxs-lookup"><span data-stu-id="7b9ab-127">Element</span></span>|<span data-ttu-id="7b9ab-128">說明</span><span class="sxs-lookup"><span data-stu-id="7b9ab-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b9ab-129">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="7b9ab-129">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="7b9ab-130">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="7b9ab-130">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b9ab-131">備註</span><span class="sxs-lookup"><span data-stu-id="7b9ab-131">Remarks</span></span>  
 <span data-ttu-id="7b9ab-132">這個組態項目會指定對等節點用於向網狀結構中其他節點驗證其本身的認證，以及對等節點用來驗證其他對等節點的驗證設定。</span><span class="sxs-lookup"><span data-stu-id="7b9ab-132">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="7b9ab-133">如需詳細資訊，請參閱[對等通道訊息驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))和[保護對等通道應用程式](../../../wcf/feature-details/securing-peer-channel-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="7b9ab-133">For more information, see [Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) and [Securing Peer Channel Applications](../../../wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b9ab-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b9ab-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="7b9ab-135">對等網路</span><span class="sxs-lookup"><span data-stu-id="7b9ab-135">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="7b9ab-136">保護用戶端安全</span><span class="sxs-lookup"><span data-stu-id="7b9ab-136">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- <span data-ttu-id="7b9ab-137">[對等通道訊息驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="7b9ab-137">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="7b9ab-138">[對等通道自訂驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="7b9ab-138">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="7b9ab-139">保護對等通道應用程式的安全</span><span class="sxs-lookup"><span data-stu-id="7b9ab-139">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="7b9ab-140">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="7b9ab-140">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
