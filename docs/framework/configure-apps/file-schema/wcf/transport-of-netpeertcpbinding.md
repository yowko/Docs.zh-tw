---
title: '&lt;netPeerTcpBinding&gt; 的 &lt;transport&gt;'
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: b929c97d0b5d9e021a71e4b88dd3d8a5f2f909a7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677000"
---
# <a name="lttransportgt-of-ltnetpeertcpbindinggt"></a><span data-ttu-id="71959-102">&lt;netPeerTcpBinding&gt; 的 &lt;transport&gt;</span><span class="sxs-lookup"><span data-stu-id="71959-102">&lt;transport&gt; of &lt;netPeerTcpBinding&gt;</span></span>
<span data-ttu-id="71959-103">使用時，指定傳輸層級安全性設定[ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="71959-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="71959-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="71959-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="71959-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="71959-105">\<bindings></span></span>  
<span data-ttu-id="71959-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="71959-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="71959-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="71959-107">\<binding></span></span>  
<span data-ttu-id="71959-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="71959-108">\<security></span></span>  
<span data-ttu-id="71959-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="71959-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71959-110">語法</span><span class="sxs-lookup"><span data-stu-id="71959-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71959-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="71959-111">Attributes and Elements</span></span>  
 <span data-ttu-id="71959-112">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="71959-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71959-113">屬性</span><span class="sxs-lookup"><span data-stu-id="71959-113">Attributes</span></span>  
  
|<span data-ttu-id="71959-114">屬性</span><span class="sxs-lookup"><span data-stu-id="71959-114">Attribute</span></span>|<span data-ttu-id="71959-115">描述</span><span class="sxs-lookup"><span data-stu-id="71959-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="71959-116">credentialType</span><span class="sxs-lookup"><span data-stu-id="71959-116">credentialType</span></span>|<span data-ttu-id="71959-117">選擇項。</span><span class="sxs-lookup"><span data-stu-id="71959-117">Optional.</span></span> <span data-ttu-id="71959-118">指定認證的類型，用於驗證對等傳輸所傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="71959-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="71959-119">此屬性的型別為 <xref:System.ServiceModel.PeerTransportCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="71959-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="71959-120">credentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="71959-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="71959-121">值</span><span class="sxs-lookup"><span data-stu-id="71959-121">Value</span></span>|<span data-ttu-id="71959-122">描述</span><span class="sxs-lookup"><span data-stu-id="71959-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="71959-123">憑證</span><span class="sxs-lookup"><span data-stu-id="71959-123">Certificate</span></span>|<span data-ttu-id="71959-124">對等通道傳輸的驗證作業需要 X509 憑證。</span><span class="sxs-lookup"><span data-stu-id="71959-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="71959-125">密碼</span><span class="sxs-lookup"><span data-stu-id="71959-125">Password</span></span>|<span data-ttu-id="71959-126">對等通道傳輸的驗證作業需要正確的密碼。</span><span class="sxs-lookup"><span data-stu-id="71959-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="71959-127">子元素</span><span class="sxs-lookup"><span data-stu-id="71959-127">Child Elements</span></span>  
 <span data-ttu-id="71959-128">無</span><span class="sxs-lookup"><span data-stu-id="71959-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="71959-129">父項目</span><span class="sxs-lookup"><span data-stu-id="71959-129">Parent Elements</span></span>  
  
|<span data-ttu-id="71959-130">項目</span><span class="sxs-lookup"><span data-stu-id="71959-130">Element</span></span>|<span data-ttu-id="71959-131">描述</span><span class="sxs-lookup"><span data-stu-id="71959-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="71959-132">\<security></span><span class="sxs-lookup"><span data-stu-id="71959-132">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="71959-133">定義的安全性設定[ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="71959-133">Defines the security settings for the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="71959-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71959-134">See also</span></span>
- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="71959-135">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="71959-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="71959-136">繫結</span><span class="sxs-lookup"><span data-stu-id="71959-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="71959-137">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="71959-137">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="71959-138">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="71959-138">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="71959-139">\<binding></span><span class="sxs-lookup"><span data-stu-id="71959-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
