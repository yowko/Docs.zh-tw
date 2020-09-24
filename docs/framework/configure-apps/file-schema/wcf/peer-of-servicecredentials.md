---
title: <peer> 的 <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: 7f6669d3f53a6ee0d189786fa9ca3625fdedd127
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162474"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="c2ec1-102">\<peer> 的 \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="c2ec1-102">\<peer> of \<serviceCredentials></span></span>

<span data-ttu-id="c2ec1-103">指定對等節點的目前認證。</span><span class="sxs-lookup"><span data-stu-id="c2ec1-103">Specifies the current credentials for a peer node.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**  
  
## <a name="syntax"></a><span data-ttu-id="c2ec1-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="c2ec1-104">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2ec1-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c2ec1-105">Attributes and Elements</span></span>  

 <span data-ttu-id="c2ec1-106">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="c2ec1-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2ec1-107">屬性</span><span class="sxs-lookup"><span data-stu-id="c2ec1-107">Attributes</span></span>  

 <span data-ttu-id="c2ec1-108">無。</span><span class="sxs-lookup"><span data-stu-id="c2ec1-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c2ec1-109">子元素</span><span class="sxs-lookup"><span data-stu-id="c2ec1-109">Child Elements</span></span>  
  
|<span data-ttu-id="c2ec1-110">項目</span><span class="sxs-lookup"><span data-stu-id="c2ec1-110">Element</span></span>|<span data-ttu-id="c2ec1-111">描述</span><span class="sxs-lookup"><span data-stu-id="c2ec1-111">Description</span></span>|  
|-------------|-----------------|  
|[\<certificate>](certificate-of-peer.md)|<span data-ttu-id="c2ec1-112">指定要用來簽署與加密對等服務之訊息的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="c2ec1-112">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="c2ec1-113">.</span><span class="sxs-lookup"><span data-stu-id="c2ec1-113">.</span></span>|  
|[\<messageSenderAuthentication>](messagesenderauthentication.md)|<span data-ttu-id="c2ec1-114">指定訊息寄件者的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="c2ec1-114">Specifies authentication options for message senders.</span></span>|  
|[\<peerAuthentication>](peerauthentication.md)|<span data-ttu-id="c2ec1-115">指定對等服務的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="c2ec1-115">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c2ec1-116">父項目</span><span class="sxs-lookup"><span data-stu-id="c2ec1-116">Parent Elements</span></span>  
  
|<span data-ttu-id="c2ec1-117">項目</span><span class="sxs-lookup"><span data-stu-id="c2ec1-117">Element</span></span>|<span data-ttu-id="c2ec1-118">描述</span><span class="sxs-lookup"><span data-stu-id="c2ec1-118">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="c2ec1-119">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="c2ec1-119">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c2ec1-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2ec1-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="c2ec1-121">對等網路</span><span class="sxs-lookup"><span data-stu-id="c2ec1-121">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="c2ec1-122">[對等通道訊息驗證](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c2ec1-122">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="c2ec1-123">[對等通道自訂驗證](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c2ec1-123">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="c2ec1-124">確保對等通道應用程式安全</span><span class="sxs-lookup"><span data-stu-id="c2ec1-124">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="c2ec1-125">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="c2ec1-125">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
