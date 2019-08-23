---
title: <transport> 的 <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 837d01540fa63579877ab4085bd8034c78f2fbe0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915567"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="0286a-102">\<netPeerTcpBinding > 的\<傳輸 ></span><span class="sxs-lookup"><span data-stu-id="0286a-102">\<transport> of \<netPeerTcpBinding></span></span>
<span data-ttu-id="0286a-103">指定使用[ \<netPeerTcpBinding >](netpeertcpbinding.md)時的傳輸層級安全性設定。</span><span class="sxs-lookup"><span data-stu-id="0286a-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="0286a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0286a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0286a-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="0286a-105">\<bindings></span></span>  
<span data-ttu-id="0286a-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="0286a-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="0286a-107">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="0286a-107">\<binding></span></span>  
<span data-ttu-id="0286a-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="0286a-108">\<security></span></span>  
<span data-ttu-id="0286a-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="0286a-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0286a-110">語法</span><span class="sxs-lookup"><span data-stu-id="0286a-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0286a-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0286a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0286a-112">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="0286a-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0286a-113">屬性</span><span class="sxs-lookup"><span data-stu-id="0286a-113">Attributes</span></span>  
  
|<span data-ttu-id="0286a-114">屬性</span><span class="sxs-lookup"><span data-stu-id="0286a-114">Attribute</span></span>|<span data-ttu-id="0286a-115">說明</span><span class="sxs-lookup"><span data-stu-id="0286a-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0286a-116">credentialType</span><span class="sxs-lookup"><span data-stu-id="0286a-116">credentialType</span></span>|<span data-ttu-id="0286a-117">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0286a-117">Optional.</span></span> <span data-ttu-id="0286a-118">指定認證的類型，用於驗證對等傳輸所傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="0286a-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="0286a-119">此屬性的型別為 <xref:System.ServiceModel.PeerTransportCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="0286a-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="0286a-120">credentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="0286a-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="0286a-121">值</span><span class="sxs-lookup"><span data-stu-id="0286a-121">Value</span></span>|<span data-ttu-id="0286a-122">描述</span><span class="sxs-lookup"><span data-stu-id="0286a-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0286a-123">憑證</span><span class="sxs-lookup"><span data-stu-id="0286a-123">Certificate</span></span>|<span data-ttu-id="0286a-124">對等通道傳輸的驗證作業需要 X509 憑證。</span><span class="sxs-lookup"><span data-stu-id="0286a-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="0286a-125">密碼</span><span class="sxs-lookup"><span data-stu-id="0286a-125">Password</span></span>|<span data-ttu-id="0286a-126">對等通道傳輸的驗證作業需要正確的密碼。</span><span class="sxs-lookup"><span data-stu-id="0286a-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0286a-127">子元素</span><span class="sxs-lookup"><span data-stu-id="0286a-127">Child Elements</span></span>  
 <span data-ttu-id="0286a-128">無</span><span class="sxs-lookup"><span data-stu-id="0286a-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0286a-129">父項目</span><span class="sxs-lookup"><span data-stu-id="0286a-129">Parent Elements</span></span>  
  
|<span data-ttu-id="0286a-130">項目</span><span class="sxs-lookup"><span data-stu-id="0286a-130">Element</span></span>|<span data-ttu-id="0286a-131">說明</span><span class="sxs-lookup"><span data-stu-id="0286a-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0286a-132">\<security></span><span class="sxs-lookup"><span data-stu-id="0286a-132">\<security></span></span>](security-of-netpeerbinding.md)|<span data-ttu-id="0286a-133">定義[ \<netPeerTcpBinding >](netpeertcpbinding.md)的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="0286a-133">Defines the security settings for the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0286a-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0286a-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="0286a-135">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="0286a-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="0286a-136">繫結</span><span class="sxs-lookup"><span data-stu-id="0286a-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0286a-137">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="0286a-137">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0286a-138">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="0286a-138">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="0286a-139">\<binding></span><span class="sxs-lookup"><span data-stu-id="0286a-139">\<binding></span></span>](../../../misc/binding.md)
