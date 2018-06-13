---
title: '&lt;netPeerBinding&gt; 的 &lt;security&gt;'
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7413820f1a1f38b3d533573715267df3b85c9d9a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749136"
---
# <a name="ltsecuritygt-of-ltnetpeerbindinggt"></a><span data-ttu-id="2428a-102">&lt;netPeerBinding&gt; 的 &lt;security&gt;</span><span class="sxs-lookup"><span data-stu-id="2428a-102">&lt;security&gt; of &lt;netPeerBinding&gt;</span></span>
<span data-ttu-id="2428a-103">定義的安全性設定[ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)，包括使用的驗證類型使用，並使用訊息傳輸的安全性。</span><span class="sxs-lookup"><span data-stu-id="2428a-103">Defines the security settings of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="2428a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2428a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2428a-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="2428a-105">\<bindings></span></span>  
<span data-ttu-id="2428a-106">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="2428a-106">\<netPeerBinding></span></span>  
<span data-ttu-id="2428a-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="2428a-107">\<binding></span></span>  
<span data-ttu-id="2428a-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="2428a-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2428a-109">語法</span><span class="sxs-lookup"><span data-stu-id="2428a-109">Syntax</span></span>  
  
```xml  
<netPeerBinding>  
    <binding>  
        <security mode="Message/None/Transport//TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2428a-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2428a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2428a-111">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="2428a-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2428a-112">屬性</span><span class="sxs-lookup"><span data-stu-id="2428a-112">Attributes</span></span>  
  
|<span data-ttu-id="2428a-113">屬性</span><span class="sxs-lookup"><span data-stu-id="2428a-113">Attribute</span></span>|<span data-ttu-id="2428a-114">描述</span><span class="sxs-lookup"><span data-stu-id="2428a-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2428a-115">模式</span><span class="sxs-lookup"><span data-stu-id="2428a-115">mode</span></span>|<span data-ttu-id="2428a-116">選擇項。</span><span class="sxs-lookup"><span data-stu-id="2428a-116">Optional.</span></span> <span data-ttu-id="2428a-117">指定此繫結所設定之對等要使用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="2428a-117">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="2428a-118">預設值是 `Message`。</span><span class="sxs-lookup"><span data-stu-id="2428a-118">The default value is `Message`.</span></span> <span data-ttu-id="2428a-119">此屬性的型別為 <xref:System.ServiceModel.SecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="2428a-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="2428a-120">mode 屬性</span><span class="sxs-lookup"><span data-stu-id="2428a-120">mode Attribute</span></span>  
  
|<span data-ttu-id="2428a-121">值</span><span class="sxs-lookup"><span data-stu-id="2428a-121">Value</span></span>|<span data-ttu-id="2428a-122">描述</span><span class="sxs-lookup"><span data-stu-id="2428a-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2428a-123">訊息</span><span class="sxs-lookup"><span data-stu-id="2428a-123">Message</span></span>|<span data-ttu-id="2428a-124">SOAP 安全性提供驗證、完整性和機密性。</span><span class="sxs-lookup"><span data-stu-id="2428a-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="2428a-125">無</span><span class="sxs-lookup"><span data-stu-id="2428a-125">None</span></span>|<span data-ttu-id="2428a-126">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="2428a-126">Security is disabled.</span></span>|  
|<span data-ttu-id="2428a-127">Transport</span><span class="sxs-lookup"><span data-stu-id="2428a-127">Transport</span></span>|<span data-ttu-id="2428a-128">系統會使用 HTTPS 來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="2428a-128">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="2428a-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="2428a-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="2428a-130">HTTPS 提供驗證和機密性。</span><span class="sxs-lookup"><span data-stu-id="2428a-130">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="2428a-131">SOAP 訊息提供豐富的認證類型。</span><span class="sxs-lookup"><span data-stu-id="2428a-131">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2428a-132">子項目</span><span class="sxs-lookup"><span data-stu-id="2428a-132">Child Elements</span></span>  
  
|<span data-ttu-id="2428a-133">項目</span><span class="sxs-lookup"><span data-stu-id="2428a-133">Element</span></span>|<span data-ttu-id="2428a-134">描述</span><span class="sxs-lookup"><span data-stu-id="2428a-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2428a-135">\<transport></span><span class="sxs-lookup"><span data-stu-id="2428a-135">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netpeertcpbinding.md)|<span data-ttu-id="2428a-136">定義使用這個繫結設定之對等所傳送安全訊息的傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="2428a-136">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="2428a-137">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="2428a-137">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2428a-138">父項目</span><span class="sxs-lookup"><span data-stu-id="2428a-138">Parent Elements</span></span>  
  
|<span data-ttu-id="2428a-139">項目</span><span class="sxs-lookup"><span data-stu-id="2428a-139">Element</span></span>|<span data-ttu-id="2428a-140">描述</span><span class="sxs-lookup"><span data-stu-id="2428a-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2428a-141">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="2428a-141">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="2428a-142">定義的所有繫結功能[ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="2428a-142">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2428a-143">備註</span><span class="sxs-lookup"><span data-stu-id="2428a-143">Remarks</span></span>  
 <span data-ttu-id="2428a-144">安全性可以是訊息特定或傳輸特定。</span><span class="sxs-lookup"><span data-stu-id="2428a-144">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2428a-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2428a-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.PeerSecuritySettings>  
 [<span data-ttu-id="2428a-146">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="2428a-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="2428a-147">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="2428a-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="2428a-148">繫結</span><span class="sxs-lookup"><span data-stu-id="2428a-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="2428a-149">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="2428a-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="2428a-150">使用繫結來設定 Windows Communication Foundation 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="2428a-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="2428a-151">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="2428a-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
