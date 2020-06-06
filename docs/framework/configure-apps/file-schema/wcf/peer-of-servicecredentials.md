---
title: <peer> 的 <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: b134e21d-e5b5-458e-9309-626dbf8db4ed
ms.openlocfilehash: ca97be7b1ab562382895fea4f1d1fc716151b70b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397647"
---
# <a name="peer-of-servicecredentials"></a><span data-ttu-id="09d6c-102">\<peer> 的 \<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="09d6c-102">\<peer> of \<serviceCredentials></span></span>
<span data-ttu-id="09d6c-103">指定對等節點的目前認證。</span><span class="sxs-lookup"><span data-stu-id="09d6c-103">Specifies the current credentials for a peer node.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peer>**  
  
## <a name="syntax"></a><span data-ttu-id="09d6c-104">語法</span><span class="sxs-lookup"><span data-stu-id="09d6c-104">Syntax</span></span>  
  
```xml  
<peer>
  <certificate />
  <peerAuthentication />
  <messageSenderAuthentication />
</peer>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09d6c-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="09d6c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="09d6c-106">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="09d6c-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09d6c-107">屬性</span><span class="sxs-lookup"><span data-stu-id="09d6c-107">Attributes</span></span>  
 <span data-ttu-id="09d6c-108">無。</span><span class="sxs-lookup"><span data-stu-id="09d6c-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="09d6c-109">子元素</span><span class="sxs-lookup"><span data-stu-id="09d6c-109">Child Elements</span></span>  
  
|<span data-ttu-id="09d6c-110">元素</span><span class="sxs-lookup"><span data-stu-id="09d6c-110">Element</span></span>|<span data-ttu-id="09d6c-111">描述</span><span class="sxs-lookup"><span data-stu-id="09d6c-111">Description</span></span>|  
|-------------|-----------------|  
|[\<certificate>](certificate-of-peer.md)|<span data-ttu-id="09d6c-112">指定要用來簽署與加密對等服務之訊息的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="09d6c-112">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer services.</span></span> <span data-ttu-id="09d6c-113">.</span><span class="sxs-lookup"><span data-stu-id="09d6c-113">.</span></span>|  
|[\<messageSenderAuthentication>](messagesenderauthentication.md)|<span data-ttu-id="09d6c-114">指定訊息寄件者的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="09d6c-114">Specifies authentication options for message senders.</span></span>|  
|[\<peerAuthentication>](peerauthentication.md)|<span data-ttu-id="09d6c-115">指定對等服務的驗證選項。</span><span class="sxs-lookup"><span data-stu-id="09d6c-115">Specifies authentication options for peer services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="09d6c-116">父項目</span><span class="sxs-lookup"><span data-stu-id="09d6c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="09d6c-117">元素</span><span class="sxs-lookup"><span data-stu-id="09d6c-117">Element</span></span>|<span data-ttu-id="09d6c-118">描述</span><span class="sxs-lookup"><span data-stu-id="09d6c-118">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="09d6c-119">指定要用於驗證 (Authenticate) 服務的認證，以及用戶端認證的驗證 (Validation) 相關設定。</span><span class="sxs-lookup"><span data-stu-id="09d6c-119">Specifies the credential to be used in authenticating the service, and the client credential validation-related settings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="09d6c-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09d6c-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.Peer%2A>
- <xref:System.ServiceModel.Description.ServiceCredentials.Peer%2A>
- <xref:System.ServiceModel.Security.PeerCredential>
- [<span data-ttu-id="09d6c-121">對等網路</span><span class="sxs-lookup"><span data-stu-id="09d6c-121">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="09d6c-122">[對等通道訊息驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="09d6c-122">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="09d6c-123">[對等通道自訂驗證](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="09d6c-123">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="09d6c-124">確保對等通道應用程式安全</span><span class="sxs-lookup"><span data-stu-id="09d6c-124">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
- [<span data-ttu-id="09d6c-125">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="09d6c-125">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
