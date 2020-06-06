---
title: <security> 的 <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: 3d1ac85073c44f683fe0c054737c5ec7ed1cbf52
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738655"
---
# <a name="security-of-netpeerbinding"></a><span data-ttu-id="cd7c3-102">\<security> 的 \<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="cd7c3-102">\<security> of \<netPeerBinding></span></span>
<span data-ttu-id="cd7c3-103">定義的安全性設定 [\<netPeerTcpBinding>](netpeertcpbinding.md) ，包括使用的驗證類型，以及用於訊息傳輸的安全性。</span><span class="sxs-lookup"><span data-stu-id="cd7c3-103">Defines the security settings of the [\<netPeerTcpBinding>](netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="cd7c3-104">語法</span><span class="sxs-lookup"><span data-stu-id="cd7c3-104">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd7c3-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cd7c3-105">Attributes and Elements</span></span>  
 <span data-ttu-id="cd7c3-106">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="cd7c3-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd7c3-107">屬性</span><span class="sxs-lookup"><span data-stu-id="cd7c3-107">Attributes</span></span>  
  
|<span data-ttu-id="cd7c3-108">屬性</span><span class="sxs-lookup"><span data-stu-id="cd7c3-108">Attribute</span></span>|<span data-ttu-id="cd7c3-109">描述</span><span class="sxs-lookup"><span data-stu-id="cd7c3-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cd7c3-110">mode</span><span class="sxs-lookup"><span data-stu-id="cd7c3-110">mode</span></span>|<span data-ttu-id="cd7c3-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="cd7c3-111">Optional.</span></span> <span data-ttu-id="cd7c3-112">指定此繫結所設定之對等要使用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="cd7c3-112">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="cd7c3-113">預設值是 `Message`。</span><span class="sxs-lookup"><span data-stu-id="cd7c3-113">The default value is `Message`.</span></span> <span data-ttu-id="cd7c3-114">此屬性的型別為 <xref:System.ServiceModel.SecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="cd7c3-114">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="cd7c3-115">mode 屬性</span><span class="sxs-lookup"><span data-stu-id="cd7c3-115">mode Attribute</span></span>  
  
|<span data-ttu-id="cd7c3-116">值</span><span class="sxs-lookup"><span data-stu-id="cd7c3-116">Value</span></span>|<span data-ttu-id="cd7c3-117">描述</span><span class="sxs-lookup"><span data-stu-id="cd7c3-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="cd7c3-118">訊息</span><span class="sxs-lookup"><span data-stu-id="cd7c3-118">Message</span></span>|<span data-ttu-id="cd7c3-119">SOAP 安全性提供驗證、完整性和機密性。</span><span class="sxs-lookup"><span data-stu-id="cd7c3-119">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="cd7c3-120">無</span><span class="sxs-lookup"><span data-stu-id="cd7c3-120">None</span></span>|<span data-ttu-id="cd7c3-121">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="cd7c3-121">Security is disabled.</span></span>|  
|<span data-ttu-id="cd7c3-122">傳輸</span><span class="sxs-lookup"><span data-stu-id="cd7c3-122">Transport</span></span>|<span data-ttu-id="cd7c3-123">系統會使用 HTTPS 來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="cd7c3-123">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="cd7c3-124">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="cd7c3-124">TransportWithMessageCredential</span></span>|<span data-ttu-id="cd7c3-125">HTTPS 提供驗證和機密性。</span><span class="sxs-lookup"><span data-stu-id="cd7c3-125">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="cd7c3-126">SOAP 訊息提供豐富的認證類型。</span><span class="sxs-lookup"><span data-stu-id="cd7c3-126">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd7c3-127">子元素</span><span class="sxs-lookup"><span data-stu-id="cd7c3-127">Child Elements</span></span>  
  
|<span data-ttu-id="cd7c3-128">元素</span><span class="sxs-lookup"><span data-stu-id="cd7c3-128">Element</span></span>|<span data-ttu-id="cd7c3-129">描述</span><span class="sxs-lookup"><span data-stu-id="cd7c3-129">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-netpeertcpbinding.md)|<span data-ttu-id="cd7c3-130">定義使用這個繫結設定之對等所傳送安全訊息的傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="cd7c3-130">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="cd7c3-131">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="cd7c3-131">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cd7c3-132">父項目</span><span class="sxs-lookup"><span data-stu-id="cd7c3-132">Parent Elements</span></span>  
  
|<span data-ttu-id="cd7c3-133">元素</span><span class="sxs-lookup"><span data-stu-id="cd7c3-133">Element</span></span>|<span data-ttu-id="cd7c3-134">描述</span><span class="sxs-lookup"><span data-stu-id="cd7c3-134">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="cd7c3-135">定義的所有系結功能 [\<netPeerTcpBinding>](netpeertcpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="cd7c3-135">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd7c3-136">備註</span><span class="sxs-lookup"><span data-stu-id="cd7c3-136">Remarks</span></span>  
 <span data-ttu-id="cd7c3-137">安全性可以是訊息特定或傳輸特定。</span><span class="sxs-lookup"><span data-stu-id="cd7c3-137">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd7c3-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd7c3-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [<span data-ttu-id="cd7c3-139">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="cd7c3-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="cd7c3-140">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="cd7c3-140">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="cd7c3-141">繫結</span><span class="sxs-lookup"><span data-stu-id="cd7c3-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="cd7c3-142">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="cd7c3-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="cd7c3-143">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="cd7c3-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
