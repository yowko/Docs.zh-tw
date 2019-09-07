---
title: <peer> 的 <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: ca97be7b1ab562382895fea4f1d1fc716151b70b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397647"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="83218-102">\<serviceCredentials > 的\<對等 ></span><span class="sxs-lookup"><span data-stu-id="83218-102">\<peer> of \<serviceCredentials></span></span>
<span data-ttu-id="83218-103">指定對等節點的目前認證。</span><span class="sxs-lookup"><span data-stu-id="83218-103">Specifies the current credentials for a peer node.</span></span>  
  
<span data-ttu-id="83218-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="83218-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="83218-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="83218-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="83218-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="83218-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="83218-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="83218-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="83218-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="83218-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="83218-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="83218-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="83218-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<對等 >**</span><span class="sxs-lookup"><span data-stu-id="83218-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83218-111">語法</span><span class="sxs-lookup"><span data-stu-id="83218-111">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83218-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="83218-112">Attributes and Elements</span></span>  
 <span data-ttu-id="83218-113">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="83218-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83218-114">屬性</span><span class="sxs-lookup"><span data-stu-id="83218-114">Attributes</span></span>  
 <span data-ttu-id="83218-115">無。</span><span class="sxs-lookup"><span data-stu-id="83218-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="83218-116">子元素</span><span class="sxs-lookup"><span data-stu-id="83218-116">Child Elements</span></span>  
  
|<span data-ttu-id="83218-117">項目</span><span class="sxs-lookup"><span data-stu-id="83218-117">Element</span></span>|<span data-ttu-id="83218-118">描述</span><span class="sxs-lookup"><span data-stu-id="83218-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="83218-119">\<certificate></span><span class="sxs-lookup"><span data-stu-id="83218-119">\<certificate></span></span>](certificate-of-peer.md)|<span data-ttu-id="83218-120">指定要用來簽署與加密對等服務之訊息的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="83218-120">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="83218-121">.</span><span class="sxs-lookup"><span data-stu-id="83218-121">.</span></span>|  
|[<span data-ttu-id="83218-122">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="83218-122">\<messageSenderAuthentication></span></span>](messagesenderauthentication.md)|<span data-ttu-id="83218-123">指定訊息寄件者的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="83218-123">Specifies authentication options for message senders.</span></span>|  
|[<span data-ttu-id="83218-124">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="83218-124">\<peerAuthentication></span></span>](peerauthentication.md)|<span data-ttu-id="83218-125">指定對等服務的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="83218-125">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="83218-126">父項目</span><span class="sxs-lookup"><span data-stu-id="83218-126">Parent Elements</span></span>  
  
|<span data-ttu-id="83218-127">項目</span><span class="sxs-lookup"><span data-stu-id="83218-127">Element</span></span>|<span data-ttu-id="83218-128">描述</span><span class="sxs-lookup"><span data-stu-id="83218-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="83218-129">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="83218-129">\<serviceCredentials></span></span>](servicecredentials.md)|<span data-ttu-id="83218-130">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="83218-130">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="83218-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83218-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="83218-132">對等網路</span><span class="sxs-lookup"><span data-stu-id="83218-132">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="83218-133">[對等通道訊息驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="83218-133">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="83218-134">[對等通道自訂驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="83218-134">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="83218-135">保護對等通道應用程式的安全</span><span class="sxs-lookup"><span data-stu-id="83218-135">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="83218-136">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="83218-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
