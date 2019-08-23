---
title: <security> 的 <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: be5ebacec466caf8d8a77bf552f42da1861e77a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936619"
---
# <a name="security-of-netpeerbinding"></a><span data-ttu-id="99c24-102">\<netPeerBinding > 的\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="99c24-102">\<security> of \<netPeerBinding></span></span>
<span data-ttu-id="99c24-103">定義[ \<netPeerTcpBinding >](netpeertcpbinding.md)的安全性設定, 包括使用的驗證類型, 以及用於訊息傳輸的安全性。</span><span class="sxs-lookup"><span data-stu-id="99c24-103">Defines the security settings of the [\<netPeerTcpBinding>](netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="99c24-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="99c24-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="99c24-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="99c24-105">\<bindings></span></span>  
<span data-ttu-id="99c24-106">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="99c24-106">\<netPeerBinding></span></span>  
<span data-ttu-id="99c24-107">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="99c24-107">\<binding></span></span>  
<span data-ttu-id="99c24-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="99c24-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99c24-109">語法</span><span class="sxs-lookup"><span data-stu-id="99c24-109">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99c24-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="99c24-110">Attributes and Elements</span></span>  
 <span data-ttu-id="99c24-111">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="99c24-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99c24-112">屬性</span><span class="sxs-lookup"><span data-stu-id="99c24-112">Attributes</span></span>  
  
|<span data-ttu-id="99c24-113">屬性</span><span class="sxs-lookup"><span data-stu-id="99c24-113">Attribute</span></span>|<span data-ttu-id="99c24-114">描述</span><span class="sxs-lookup"><span data-stu-id="99c24-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="99c24-115">模式</span><span class="sxs-lookup"><span data-stu-id="99c24-115">mode</span></span>|<span data-ttu-id="99c24-116">選擇性。</span><span class="sxs-lookup"><span data-stu-id="99c24-116">Optional.</span></span> <span data-ttu-id="99c24-117">指定此繫結所設定之對等要使用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="99c24-117">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="99c24-118">預設值為 `Message`。</span><span class="sxs-lookup"><span data-stu-id="99c24-118">The default value is `Message`.</span></span> <span data-ttu-id="99c24-119">此屬性的型別為 <xref:System.ServiceModel.SecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="99c24-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="99c24-120">mode 屬性</span><span class="sxs-lookup"><span data-stu-id="99c24-120">mode Attribute</span></span>  
  
|<span data-ttu-id="99c24-121">值</span><span class="sxs-lookup"><span data-stu-id="99c24-121">Value</span></span>|<span data-ttu-id="99c24-122">描述</span><span class="sxs-lookup"><span data-stu-id="99c24-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="99c24-123">訊息</span><span class="sxs-lookup"><span data-stu-id="99c24-123">Message</span></span>|<span data-ttu-id="99c24-124">SOAP 安全性提供驗證、完整性和機密性。</span><span class="sxs-lookup"><span data-stu-id="99c24-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="99c24-125">無</span><span class="sxs-lookup"><span data-stu-id="99c24-125">None</span></span>|<span data-ttu-id="99c24-126">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="99c24-126">Security is disabled.</span></span>|  
|<span data-ttu-id="99c24-127">Transport</span><span class="sxs-lookup"><span data-stu-id="99c24-127">Transport</span></span>|<span data-ttu-id="99c24-128">系統會使用 HTTPS 來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="99c24-128">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="99c24-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="99c24-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="99c24-130">HTTPS 提供驗證和機密性。</span><span class="sxs-lookup"><span data-stu-id="99c24-130">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="99c24-131">SOAP 訊息提供豐富的認證類型。</span><span class="sxs-lookup"><span data-stu-id="99c24-131">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99c24-132">子元素</span><span class="sxs-lookup"><span data-stu-id="99c24-132">Child Elements</span></span>  
  
|<span data-ttu-id="99c24-133">項目</span><span class="sxs-lookup"><span data-stu-id="99c24-133">Element</span></span>|<span data-ttu-id="99c24-134">描述</span><span class="sxs-lookup"><span data-stu-id="99c24-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99c24-135">\<transport></span><span class="sxs-lookup"><span data-stu-id="99c24-135">\<transport></span></span>](transport-of-netpeertcpbinding.md)|<span data-ttu-id="99c24-136">定義使用這個繫結設定之對等所傳送安全訊息的傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="99c24-136">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="99c24-137">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="99c24-137">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="99c24-138">父項目</span><span class="sxs-lookup"><span data-stu-id="99c24-138">Parent Elements</span></span>  
  
|<span data-ttu-id="99c24-139">項目</span><span class="sxs-lookup"><span data-stu-id="99c24-139">Element</span></span>|<span data-ttu-id="99c24-140">說明</span><span class="sxs-lookup"><span data-stu-id="99c24-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99c24-141">\<binding></span><span class="sxs-lookup"><span data-stu-id="99c24-141">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="99c24-142">定義[ \<netPeerTcpBinding >](netpeertcpbinding.md)的所有系結功能。</span><span class="sxs-lookup"><span data-stu-id="99c24-142">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99c24-143">備註</span><span class="sxs-lookup"><span data-stu-id="99c24-143">Remarks</span></span>  
 <span data-ttu-id="99c24-144">安全性可以是訊息特定或傳輸特定。</span><span class="sxs-lookup"><span data-stu-id="99c24-144">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99c24-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99c24-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [<span data-ttu-id="99c24-146">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="99c24-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="99c24-147">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="99c24-147">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="99c24-148">繫結</span><span class="sxs-lookup"><span data-stu-id="99c24-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="99c24-149">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="99c24-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="99c24-150">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="99c24-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="99c24-151">\<binding></span><span class="sxs-lookup"><span data-stu-id="99c24-151">\<binding></span></span>](../../../misc/binding.md)
