---
title: <transport> 的 <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 49b31a889d192d190125214e89ba09305114eb7f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73735969"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="8e087-102">\<transport> 的 \<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="8e087-102">\<transport> of \<netPeerTcpBinding></span></span>
<span data-ttu-id="8e087-103">指定使用時的傳輸層級安全性設定 [\<netPeerTcpBinding>](netpeertcpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="8e087-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netpeerbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="8e087-104">語法</span><span class="sxs-lookup"><span data-stu-id="8e087-104">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e087-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8e087-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8e087-106">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="8e087-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e087-107">屬性</span><span class="sxs-lookup"><span data-stu-id="8e087-107">Attributes</span></span>  
  
|<span data-ttu-id="8e087-108">屬性</span><span class="sxs-lookup"><span data-stu-id="8e087-108">Attribute</span></span>|<span data-ttu-id="8e087-109">描述</span><span class="sxs-lookup"><span data-stu-id="8e087-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8e087-110">credentialType</span><span class="sxs-lookup"><span data-stu-id="8e087-110">credentialType</span></span>|<span data-ttu-id="8e087-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="8e087-111">Optional.</span></span> <span data-ttu-id="8e087-112">指定認證的類型，用於驗證對等傳輸所傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="8e087-112">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="8e087-113">此屬性的型別為 <xref:System.ServiceModel.PeerTransportCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="8e087-113">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="8e087-114">credentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="8e087-114">credentialType Attribute</span></span>  
  
|<span data-ttu-id="8e087-115">值</span><span class="sxs-lookup"><span data-stu-id="8e087-115">Value</span></span>|<span data-ttu-id="8e087-116">描述</span><span class="sxs-lookup"><span data-stu-id="8e087-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8e087-117">憑證</span><span class="sxs-lookup"><span data-stu-id="8e087-117">Certificate</span></span>|<span data-ttu-id="8e087-118">對等通道傳輸的驗證作業需要 X509 憑證。</span><span class="sxs-lookup"><span data-stu-id="8e087-118">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="8e087-119">密碼</span><span class="sxs-lookup"><span data-stu-id="8e087-119">Password</span></span>|<span data-ttu-id="8e087-120">對等通道傳輸的驗證作業需要正確的密碼。</span><span class="sxs-lookup"><span data-stu-id="8e087-120">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8e087-121">子元素</span><span class="sxs-lookup"><span data-stu-id="8e087-121">Child Elements</span></span>  
 <span data-ttu-id="8e087-122">無</span><span class="sxs-lookup"><span data-stu-id="8e087-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8e087-123">父項目</span><span class="sxs-lookup"><span data-stu-id="8e087-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8e087-124">元素</span><span class="sxs-lookup"><span data-stu-id="8e087-124">Element</span></span>|<span data-ttu-id="8e087-125">描述</span><span class="sxs-lookup"><span data-stu-id="8e087-125">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netpeerbinding.md)|<span data-ttu-id="8e087-126">定義的安全性設定 [\<netPeerTcpBinding>](netpeertcpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="8e087-126">Defines the security settings for the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8e087-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e087-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="8e087-128">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="8e087-128">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="8e087-129">繫結</span><span class="sxs-lookup"><span data-stu-id="8e087-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="8e087-130">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="8e087-130">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="8e087-131">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="8e087-131">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
