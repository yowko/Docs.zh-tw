---
title: <peer> 的 <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: 50db8eb381249c3b880c4b1dd96ec3813d51ce67
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556111"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="5aeff-102">\<peer> 的 \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="5aeff-102">\<peer> of \<serviceCredentials></span></span>
<span data-ttu-id="5aeff-103">指定對等節點的目前認證。</span><span class="sxs-lookup"><span data-stu-id="5aeff-103">Specifies the current credentials for a peer node.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**  
  
## <a name="syntax"></a><span data-ttu-id="5aeff-104">語法</span><span class="sxs-lookup"><span data-stu-id="5aeff-104">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5aeff-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5aeff-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5aeff-106">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="5aeff-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5aeff-107">屬性</span><span class="sxs-lookup"><span data-stu-id="5aeff-107">Attributes</span></span>  
 <span data-ttu-id="5aeff-108">無。</span><span class="sxs-lookup"><span data-stu-id="5aeff-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5aeff-109">子元素</span><span class="sxs-lookup"><span data-stu-id="5aeff-109">Child Elements</span></span>  
  
|<span data-ttu-id="5aeff-110">項目</span><span class="sxs-lookup"><span data-stu-id="5aeff-110">Element</span></span>|<span data-ttu-id="5aeff-111">描述</span><span class="sxs-lookup"><span data-stu-id="5aeff-111">Description</span></span>|  
|-------------|-----------------|  
|[\<certificate>](certificate-of-peer.md)|<span data-ttu-id="5aeff-112">指定要用來簽署與加密對等服務之訊息的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="5aeff-112">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="5aeff-113">.</span><span class="sxs-lookup"><span data-stu-id="5aeff-113">.</span></span>|  
|[\<messageSenderAuthentication>](messagesenderauthentication.md)|<span data-ttu-id="5aeff-114">指定訊息寄件者的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="5aeff-114">Specifies authentication options for message senders.</span></span>|  
|[\<peerAuthentication>](peerauthentication.md)|<span data-ttu-id="5aeff-115">指定對等服務的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="5aeff-115">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5aeff-116">父項目</span><span class="sxs-lookup"><span data-stu-id="5aeff-116">Parent Elements</span></span>  
  
|<span data-ttu-id="5aeff-117">項目</span><span class="sxs-lookup"><span data-stu-id="5aeff-117">Element</span></span>|<span data-ttu-id="5aeff-118">描述</span><span class="sxs-lookup"><span data-stu-id="5aeff-118">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="5aeff-119">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="5aeff-119">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5aeff-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5aeff-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="5aeff-121">對等網路</span><span class="sxs-lookup"><span data-stu-id="5aeff-121">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="5aeff-122">[對等通道訊息驗證](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="5aeff-122">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="5aeff-123">[對等通道自訂驗證](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="5aeff-123">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="5aeff-124">確保對等通道應用程式安全</span><span class="sxs-lookup"><span data-stu-id="5aeff-124">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="5aeff-125">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="5aeff-125">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
