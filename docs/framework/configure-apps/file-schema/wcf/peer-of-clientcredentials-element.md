---
title: <peer> 項目的 <clientCredentials>
ms.date: 03/30/2017
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
ms.openlocfilehash: a8144ca7bad5654bf8f77259ea1717442665fc81
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555454"
---
# <a name="peer-of-clientcredentials-element"></a><span data-ttu-id="395d8-102">\<peer> 項目的 \<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="395d8-102">\<peer> of \<clientCredentials> Element</span></span>
<span data-ttu-id="395d8-103">指定驗證對等用戶端時所使用的認證。</span><span class="sxs-lookup"><span data-stu-id="395d8-103">Specifies credentials used when authenticating peer-to-peer clients.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**  
  
## <a name="syntax"></a><span data-ttu-id="395d8-104">語法</span><span class="sxs-lookup"><span data-stu-id="395d8-104">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="395d8-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="395d8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="395d8-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="395d8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="395d8-107">屬性</span><span class="sxs-lookup"><span data-stu-id="395d8-107">Attributes</span></span>  
 <span data-ttu-id="395d8-108">無。</span><span class="sxs-lookup"><span data-stu-id="395d8-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="395d8-109">子元素</span><span class="sxs-lookup"><span data-stu-id="395d8-109">Child Elements</span></span>  
  
|<span data-ttu-id="395d8-110">項目</span><span class="sxs-lookup"><span data-stu-id="395d8-110">Element</span></span>|<span data-ttu-id="395d8-111">描述</span><span class="sxs-lookup"><span data-stu-id="395d8-111">Description</span></span>|  
|-------------|-----------------|  
|[\<certificate>](certificate-element.md)|<span data-ttu-id="395d8-112">指定要用來簽署與加密對等用戶端之訊息的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="395d8-112">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span> <span data-ttu-id="395d8-113">.</span><span class="sxs-lookup"><span data-stu-id="395d8-113">.</span></span>|  
|[\<peerAuthentication>](peerauthentication-element.md)|<span data-ttu-id="395d8-114">指定對等用戶端的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="395d8-114">Specifies authentication options for peer clients.</span></span>|  
|[\<messageSenderAuthentication>](messagesenderauthentication-element.md)|<span data-ttu-id="395d8-115">指定訊息寄件者的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="395d8-115">Specifies authentication options for message senders.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="395d8-116">父項目</span><span class="sxs-lookup"><span data-stu-id="395d8-116">Parent Elements</span></span>  
  
|<span data-ttu-id="395d8-117">項目</span><span class="sxs-lookup"><span data-stu-id="395d8-117">Element</span></span>|<span data-ttu-id="395d8-118">描述</span><span class="sxs-lookup"><span data-stu-id="395d8-118">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="395d8-119">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="395d8-119">Specifies the credentials used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="395d8-120">備註</span><span class="sxs-lookup"><span data-stu-id="395d8-120">Remarks</span></span>  
 <span data-ttu-id="395d8-121">這個組態項目會指定對等節點用於向網狀結構中其他節點驗證其本身的認證，以及對等節點用來驗證其他對等節點的驗證設定。</span><span class="sxs-lookup"><span data-stu-id="395d8-121">This configuration element specifies the credentials that a peer node uses to authenticate itself to other nodes in the mesh, as well as authentication settings that a peer node uses to authenticate other peer nodes.</span></span> <span data-ttu-id="395d8-122">如需詳細資訊，請參閱 [對等通道訊息驗證](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) 和 [保護對等通道應用程式](../../../wcf/feature-details/securing-peer-channel-applications.md)。</span><span class="sxs-lookup"><span data-stu-id="395d8-122">For more information, see [Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90)) and [Securing Peer Channel Applications](../../../wcf/feature-details/securing-peer-channel-applications.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="395d8-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="395d8-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="395d8-124">對等網路</span><span class="sxs-lookup"><span data-stu-id="395d8-124">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="395d8-125">確保用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="395d8-125">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- <span data-ttu-id="395d8-126">[對等通道訊息驗證](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="395d8-126">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="395d8-127">[對等通道自訂驗證](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="395d8-127">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="395d8-128">確保對等通道應用程式安全</span><span class="sxs-lookup"><span data-stu-id="395d8-128">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="395d8-129">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="395d8-129">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
