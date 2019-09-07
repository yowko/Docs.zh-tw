---
title: <security> 的 <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: 88aa2898472c20c9e52cfd5830c0e41e8ea9ba21
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399809"
---
# <a name="security-of-netpeerbinding"></a><span data-ttu-id="b1bb8-102">\<netPeerBinding > 的\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="b1bb8-102">\<security> of \<netPeerBinding></span></span>
<span data-ttu-id="b1bb8-103">定義[ \<netPeerTcpBinding >](netpeertcpbinding.md)的安全性設定，包括使用的驗證類型，以及用於訊息傳輸的安全性。</span><span class="sxs-lookup"><span data-stu-id="b1bb8-103">Defines the security settings of the [\<netPeerTcpBinding>](netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
<span data-ttu-id="b1bb8-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b1bb8-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b1bb8-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b1bb8-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b1bb8-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="b1bb8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="b1bb8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netPeerTcpBinding >** ](netpeertcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="b1bb8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)</span></span>\
<span data-ttu-id="b1bb8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="b1bb8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="b1bb8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<安全性 >**</span><span class="sxs-lookup"><span data-stu-id="b1bb8-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1bb8-110">語法</span><span class="sxs-lookup"><span data-stu-id="b1bb8-110">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1bb8-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b1bb8-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b1bb8-112">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="b1bb8-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1bb8-113">屬性</span><span class="sxs-lookup"><span data-stu-id="b1bb8-113">Attributes</span></span>  
  
|<span data-ttu-id="b1bb8-114">屬性</span><span class="sxs-lookup"><span data-stu-id="b1bb8-114">Attribute</span></span>|<span data-ttu-id="b1bb8-115">描述</span><span class="sxs-lookup"><span data-stu-id="b1bb8-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b1bb8-116">模式</span><span class="sxs-lookup"><span data-stu-id="b1bb8-116">mode</span></span>|<span data-ttu-id="b1bb8-117">選擇性。</span><span class="sxs-lookup"><span data-stu-id="b1bb8-117">Optional.</span></span> <span data-ttu-id="b1bb8-118">指定此繫結所設定之對等要使用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="b1bb8-118">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="b1bb8-119">預設值為 `Message`。</span><span class="sxs-lookup"><span data-stu-id="b1bb8-119">The default value is `Message`.</span></span> <span data-ttu-id="b1bb8-120">此屬性的型別為 <xref:System.ServiceModel.SecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="b1bb8-120">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="b1bb8-121">mode 屬性</span><span class="sxs-lookup"><span data-stu-id="b1bb8-121">mode Attribute</span></span>  
  
|<span data-ttu-id="b1bb8-122">值</span><span class="sxs-lookup"><span data-stu-id="b1bb8-122">Value</span></span>|<span data-ttu-id="b1bb8-123">描述</span><span class="sxs-lookup"><span data-stu-id="b1bb8-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b1bb8-124">訊息</span><span class="sxs-lookup"><span data-stu-id="b1bb8-124">Message</span></span>|<span data-ttu-id="b1bb8-125">SOAP 安全性提供驗證、完整性和機密性。</span><span class="sxs-lookup"><span data-stu-id="b1bb8-125">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="b1bb8-126">無</span><span class="sxs-lookup"><span data-stu-id="b1bb8-126">None</span></span>|<span data-ttu-id="b1bb8-127">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="b1bb8-127">Security is disabled.</span></span>|  
|<span data-ttu-id="b1bb8-128">Transport</span><span class="sxs-lookup"><span data-stu-id="b1bb8-128">Transport</span></span>|<span data-ttu-id="b1bb8-129">系統會使用 HTTPS 來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="b1bb8-129">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="b1bb8-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="b1bb8-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="b1bb8-131">HTTPS 提供驗證和機密性。</span><span class="sxs-lookup"><span data-stu-id="b1bb8-131">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="b1bb8-132">SOAP 訊息提供豐富的認證類型。</span><span class="sxs-lookup"><span data-stu-id="b1bb8-132">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1bb8-133">子元素</span><span class="sxs-lookup"><span data-stu-id="b1bb8-133">Child Elements</span></span>  
  
|<span data-ttu-id="b1bb8-134">項目</span><span class="sxs-lookup"><span data-stu-id="b1bb8-134">Element</span></span>|<span data-ttu-id="b1bb8-135">描述</span><span class="sxs-lookup"><span data-stu-id="b1bb8-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1bb8-136">\<transport></span><span class="sxs-lookup"><span data-stu-id="b1bb8-136">\<transport></span></span>](transport-of-netpeertcpbinding.md)|<span data-ttu-id="b1bb8-137">定義使用這個繫結設定之對等所傳送安全訊息的傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="b1bb8-137">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="b1bb8-138">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="b1bb8-138">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b1bb8-139">父項目</span><span class="sxs-lookup"><span data-stu-id="b1bb8-139">Parent Elements</span></span>  
  
|<span data-ttu-id="b1bb8-140">項目</span><span class="sxs-lookup"><span data-stu-id="b1bb8-140">Element</span></span>|<span data-ttu-id="b1bb8-141">說明</span><span class="sxs-lookup"><span data-stu-id="b1bb8-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1bb8-142">\<binding></span><span class="sxs-lookup"><span data-stu-id="b1bb8-142">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="b1bb8-143">定義[ \<netPeerTcpBinding >](netpeertcpbinding.md)的所有系結功能。</span><span class="sxs-lookup"><span data-stu-id="b1bb8-143">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1bb8-144">備註</span><span class="sxs-lookup"><span data-stu-id="b1bb8-144">Remarks</span></span>  
 <span data-ttu-id="b1bb8-145">安全性可以是訊息特定或傳輸特定。</span><span class="sxs-lookup"><span data-stu-id="b1bb8-145">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1bb8-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1bb8-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [<span data-ttu-id="b1bb8-147">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="b1bb8-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b1bb8-148">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="b1bb8-148">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="b1bb8-149">繫結</span><span class="sxs-lookup"><span data-stu-id="b1bb8-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b1bb8-150">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="b1bb8-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b1bb8-151">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="b1bb8-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="b1bb8-152">\<binding></span><span class="sxs-lookup"><span data-stu-id="b1bb8-152">\<binding></span></span>](../../../misc/binding.md)
