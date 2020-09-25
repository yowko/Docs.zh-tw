---
title: <security> 的 <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: 543c57d6b2dba1ff5934b49e0e219cf2e5cad153
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170021"
---
# <a name="security-of-netpeerbinding"></a><span data-ttu-id="29690-102">\<security> 的 \<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="29690-102">\<security> of \<netPeerBinding></span></span>

<span data-ttu-id="29690-103">定義的安全性設定 [\<netPeerTcpBinding>](netpeertcpbinding.md) ，包括使用的驗證類型，以及用於訊息傳輸的安全性。</span><span class="sxs-lookup"><span data-stu-id="29690-103">Defines the security settings of the [\<netPeerTcpBinding>](netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="29690-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="29690-104">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29690-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="29690-105">Attributes and Elements</span></span>  

 <span data-ttu-id="29690-106">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="29690-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29690-107">屬性</span><span class="sxs-lookup"><span data-stu-id="29690-107">Attributes</span></span>  
  
|<span data-ttu-id="29690-108">屬性</span><span class="sxs-lookup"><span data-stu-id="29690-108">Attribute</span></span>|<span data-ttu-id="29690-109">描述</span><span class="sxs-lookup"><span data-stu-id="29690-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="29690-110">mode</span><span class="sxs-lookup"><span data-stu-id="29690-110">mode</span></span>|<span data-ttu-id="29690-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="29690-111">Optional.</span></span> <span data-ttu-id="29690-112">指定此繫結所設定之對等要使用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="29690-112">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="29690-113">預設值是 `Message`。</span><span class="sxs-lookup"><span data-stu-id="29690-113">The default value is `Message`.</span></span> <span data-ttu-id="29690-114">此屬性的型別為 <xref:System.ServiceModel.SecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="29690-114">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="29690-115">mode 屬性</span><span class="sxs-lookup"><span data-stu-id="29690-115">mode Attribute</span></span>  
  
|<span data-ttu-id="29690-116">值</span><span class="sxs-lookup"><span data-stu-id="29690-116">Value</span></span>|<span data-ttu-id="29690-117">描述</span><span class="sxs-lookup"><span data-stu-id="29690-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="29690-118">訊息</span><span class="sxs-lookup"><span data-stu-id="29690-118">Message</span></span>|<span data-ttu-id="29690-119">SOAP 安全性提供驗證、完整性和機密性。</span><span class="sxs-lookup"><span data-stu-id="29690-119">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="29690-120">無</span><span class="sxs-lookup"><span data-stu-id="29690-120">None</span></span>|<span data-ttu-id="29690-121">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="29690-121">Security is disabled.</span></span>|  
|<span data-ttu-id="29690-122">傳輸</span><span class="sxs-lookup"><span data-stu-id="29690-122">Transport</span></span>|<span data-ttu-id="29690-123">系統會使用 HTTPS 來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="29690-123">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="29690-124">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="29690-124">TransportWithMessageCredential</span></span>|<span data-ttu-id="29690-125">HTTPS 提供驗證和機密性。</span><span class="sxs-lookup"><span data-stu-id="29690-125">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="29690-126">SOAP 訊息提供豐富的認證類型。</span><span class="sxs-lookup"><span data-stu-id="29690-126">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29690-127">子元素</span><span class="sxs-lookup"><span data-stu-id="29690-127">Child Elements</span></span>  
  
|<span data-ttu-id="29690-128">項目</span><span class="sxs-lookup"><span data-stu-id="29690-128">Element</span></span>|<span data-ttu-id="29690-129">描述</span><span class="sxs-lookup"><span data-stu-id="29690-129">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-netpeertcpbinding.md)|<span data-ttu-id="29690-130">定義使用這個繫結設定之對等所傳送安全訊息的傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="29690-130">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="29690-131">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="29690-131">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="29690-132">父項目</span><span class="sxs-lookup"><span data-stu-id="29690-132">Parent Elements</span></span>  
  
|<span data-ttu-id="29690-133">項目</span><span class="sxs-lookup"><span data-stu-id="29690-133">Element</span></span>|<span data-ttu-id="29690-134">描述</span><span class="sxs-lookup"><span data-stu-id="29690-134">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="29690-135">定義的所有系結功能 [\<netPeerTcpBinding>](netpeertcpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="29690-135">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29690-136">備註</span><span class="sxs-lookup"><span data-stu-id="29690-136">Remarks</span></span>  

 <span data-ttu-id="29690-137">安全性可以是訊息特定或傳輸特定。</span><span class="sxs-lookup"><span data-stu-id="29690-137">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29690-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29690-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [<span data-ttu-id="29690-139">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="29690-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="29690-140">選取認證類型</span><span class="sxs-lookup"><span data-stu-id="29690-140">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="29690-141">繫結</span><span class="sxs-lookup"><span data-stu-id="29690-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="29690-142">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="29690-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="29690-143">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="29690-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
