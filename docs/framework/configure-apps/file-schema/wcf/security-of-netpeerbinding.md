---
title: <security> 的 <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: 6348bc6f6c0d3a9656fbe57bf71f531d1287a949
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170088"
---
# <a name="security-of-netpeerbinding"></a><span data-ttu-id="0e3d8-102">\<security> of \<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="0e3d8-102">\<security> of \<netPeerBinding></span></span>
<span data-ttu-id="0e3d8-103">定義的安全性設定[ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)、 包括的驗證類型使用，以及使用訊息傳輸的安全性。</span><span class="sxs-lookup"><span data-stu-id="0e3d8-103">Defines the security settings of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="0e3d8-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0e3d8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0e3d8-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="0e3d8-105">\<bindings></span></span>  
<span data-ttu-id="0e3d8-106">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="0e3d8-106">\<netPeerBinding></span></span>  
<span data-ttu-id="0e3d8-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="0e3d8-107">\<binding></span></span>  
<span data-ttu-id="0e3d8-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="0e3d8-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e3d8-109">語法</span><span class="sxs-lookup"><span data-stu-id="0e3d8-109">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e3d8-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0e3d8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0e3d8-111">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="0e3d8-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e3d8-112">屬性</span><span class="sxs-lookup"><span data-stu-id="0e3d8-112">Attributes</span></span>  
  
|<span data-ttu-id="0e3d8-113">屬性</span><span class="sxs-lookup"><span data-stu-id="0e3d8-113">Attribute</span></span>|<span data-ttu-id="0e3d8-114">描述</span><span class="sxs-lookup"><span data-stu-id="0e3d8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0e3d8-115">模式</span><span class="sxs-lookup"><span data-stu-id="0e3d8-115">mode</span></span>|<span data-ttu-id="0e3d8-116">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0e3d8-116">Optional.</span></span> <span data-ttu-id="0e3d8-117">指定此繫結所設定之對等要使用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="0e3d8-117">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="0e3d8-118">預設值為 `Message`。</span><span class="sxs-lookup"><span data-stu-id="0e3d8-118">The default value is `Message`.</span></span> <span data-ttu-id="0e3d8-119">此屬性的型別為 <xref:System.ServiceModel.SecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="0e3d8-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="0e3d8-120">mode 屬性</span><span class="sxs-lookup"><span data-stu-id="0e3d8-120">mode Attribute</span></span>  
  
|<span data-ttu-id="0e3d8-121">值</span><span class="sxs-lookup"><span data-stu-id="0e3d8-121">Value</span></span>|<span data-ttu-id="0e3d8-122">描述</span><span class="sxs-lookup"><span data-stu-id="0e3d8-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0e3d8-123">訊息</span><span class="sxs-lookup"><span data-stu-id="0e3d8-123">Message</span></span>|<span data-ttu-id="0e3d8-124">SOAP 安全性提供驗證、完整性和機密性。</span><span class="sxs-lookup"><span data-stu-id="0e3d8-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="0e3d8-125">None</span><span class="sxs-lookup"><span data-stu-id="0e3d8-125">None</span></span>|<span data-ttu-id="0e3d8-126">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="0e3d8-126">Security is disabled.</span></span>|  
|<span data-ttu-id="0e3d8-127">Transport</span><span class="sxs-lookup"><span data-stu-id="0e3d8-127">Transport</span></span>|<span data-ttu-id="0e3d8-128">系統會使用 HTTPS 來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="0e3d8-128">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="0e3d8-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="0e3d8-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="0e3d8-130">HTTPS 提供驗證和機密性。</span><span class="sxs-lookup"><span data-stu-id="0e3d8-130">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="0e3d8-131">SOAP 訊息提供豐富的認證類型。</span><span class="sxs-lookup"><span data-stu-id="0e3d8-131">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0e3d8-132">子元素</span><span class="sxs-lookup"><span data-stu-id="0e3d8-132">Child Elements</span></span>  
  
|<span data-ttu-id="0e3d8-133">項目</span><span class="sxs-lookup"><span data-stu-id="0e3d8-133">Element</span></span>|<span data-ttu-id="0e3d8-134">描述</span><span class="sxs-lookup"><span data-stu-id="0e3d8-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e3d8-135">\<transport></span><span class="sxs-lookup"><span data-stu-id="0e3d8-135">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netpeertcpbinding.md)|<span data-ttu-id="0e3d8-136">定義使用這個繫結設定之對等所傳送安全訊息的傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="0e3d8-136">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="0e3d8-137">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="0e3d8-137">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0e3d8-138">父項目</span><span class="sxs-lookup"><span data-stu-id="0e3d8-138">Parent Elements</span></span>  
  
|<span data-ttu-id="0e3d8-139">項目</span><span class="sxs-lookup"><span data-stu-id="0e3d8-139">Element</span></span>|<span data-ttu-id="0e3d8-140">描述</span><span class="sxs-lookup"><span data-stu-id="0e3d8-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e3d8-141">\<binding></span><span class="sxs-lookup"><span data-stu-id="0e3d8-141">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="0e3d8-142">定義的所有繫結功能[ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="0e3d8-142">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e3d8-143">備註</span><span class="sxs-lookup"><span data-stu-id="0e3d8-143">Remarks</span></span>  
 <span data-ttu-id="0e3d8-144">安全性可以是訊息特定或傳輸特定。</span><span class="sxs-lookup"><span data-stu-id="0e3d8-144">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e3d8-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e3d8-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [<span data-ttu-id="0e3d8-146">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="0e3d8-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="0e3d8-147">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="0e3d8-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="0e3d8-148">繫結</span><span class="sxs-lookup"><span data-stu-id="0e3d8-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="0e3d8-149">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="0e3d8-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0e3d8-150">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="0e3d8-150">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="0e3d8-151">\<binding></span><span class="sxs-lookup"><span data-stu-id="0e3d8-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
