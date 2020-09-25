---
title: <transport> 的 <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 5df47b1bfc149b524fc9b90eacffa832817f653c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172862"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="8a9a5-102">\<transport> 的 \<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="8a9a5-102">\<transport> of \<netPeerTcpBinding></span></span>

<span data-ttu-id="8a9a5-103">當使用時，指定傳輸層級安全性的設定 [\<netPeerTcpBinding>](netpeertcpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="8a9a5-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netpeerbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="8a9a5-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="8a9a5-104">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8a9a5-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8a9a5-105">Attributes and Elements</span></span>  

 <span data-ttu-id="8a9a5-106">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="8a9a5-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8a9a5-107">屬性</span><span class="sxs-lookup"><span data-stu-id="8a9a5-107">Attributes</span></span>  
  
|<span data-ttu-id="8a9a5-108">屬性</span><span class="sxs-lookup"><span data-stu-id="8a9a5-108">Attribute</span></span>|<span data-ttu-id="8a9a5-109">描述</span><span class="sxs-lookup"><span data-stu-id="8a9a5-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8a9a5-110">credentialType</span><span class="sxs-lookup"><span data-stu-id="8a9a5-110">credentialType</span></span>|<span data-ttu-id="8a9a5-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="8a9a5-111">Optional.</span></span> <span data-ttu-id="8a9a5-112">指定認證的類型，用於驗證對等傳輸所傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="8a9a5-112">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="8a9a5-113">此屬性的型別為 <xref:System.ServiceModel.PeerTransportCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="8a9a5-113">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="8a9a5-114">credentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="8a9a5-114">credentialType Attribute</span></span>  
  
|<span data-ttu-id="8a9a5-115">值</span><span class="sxs-lookup"><span data-stu-id="8a9a5-115">Value</span></span>|<span data-ttu-id="8a9a5-116">描述</span><span class="sxs-lookup"><span data-stu-id="8a9a5-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8a9a5-117">憑證</span><span class="sxs-lookup"><span data-stu-id="8a9a5-117">Certificate</span></span>|<span data-ttu-id="8a9a5-118">對等通道傳輸的驗證作業需要 X509 憑證。</span><span class="sxs-lookup"><span data-stu-id="8a9a5-118">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="8a9a5-119">密碼</span><span class="sxs-lookup"><span data-stu-id="8a9a5-119">Password</span></span>|<span data-ttu-id="8a9a5-120">對等通道傳輸的驗證作業需要正確的密碼。</span><span class="sxs-lookup"><span data-stu-id="8a9a5-120">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8a9a5-121">子元素</span><span class="sxs-lookup"><span data-stu-id="8a9a5-121">Child Elements</span></span>  

 <span data-ttu-id="8a9a5-122">無</span><span class="sxs-lookup"><span data-stu-id="8a9a5-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8a9a5-123">父項目</span><span class="sxs-lookup"><span data-stu-id="8a9a5-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8a9a5-124">項目</span><span class="sxs-lookup"><span data-stu-id="8a9a5-124">Element</span></span>|<span data-ttu-id="8a9a5-125">描述</span><span class="sxs-lookup"><span data-stu-id="8a9a5-125">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netpeerbinding.md)|<span data-ttu-id="8a9a5-126">定義的安全性設定 [\<netPeerTcpBinding>](netpeertcpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="8a9a5-126">Defines the security settings for the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8a9a5-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a9a5-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="8a9a5-128">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="8a9a5-128">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8a9a5-129">繫結</span><span class="sxs-lookup"><span data-stu-id="8a9a5-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8a9a5-130">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="8a9a5-130">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="8a9a5-131">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="8a9a5-131">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
