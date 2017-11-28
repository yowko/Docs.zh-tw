---
title: "&lt;peerTransport&gt; 的 &lt;transport&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 787d4569416203364e04898c6adcd57fb5a7aec8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportgt-of-ltpeertransportgt"></a><span data-ttu-id="6757d-102">&lt;peerTransport&gt; 的 &lt;transport&gt;</span><span class="sxs-lookup"><span data-stu-id="6757d-102">&lt;transport&gt; of &lt;peerTransport&gt;</span></span>
<span data-ttu-id="6757d-103">指定使用這個繫結設定之對等所傳送安全訊息的傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="6757d-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
 <span data-ttu-id="6757d-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="6757d-104">\<system.serviceModel></span></span>  
<span data-ttu-id="6757d-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="6757d-105">\<bindings></span></span>  
<span data-ttu-id="6757d-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="6757d-106">\<customBinding></span></span>  
<span data-ttu-id="6757d-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="6757d-107">\<binding></span></span>  
<span data-ttu-id="6757d-108">\<p ></span><span class="sxs-lookup"><span data-stu-id="6757d-108">\<peerTransport></span></span>  
<span data-ttu-id="6757d-109">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="6757d-109">\<security></span></span>  
<span data-ttu-id="6757d-110">\<傳輸 ></span><span class="sxs-lookup"><span data-stu-id="6757d-110">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6757d-111">語法</span><span class="sxs-lookup"><span data-stu-id="6757d-111">Syntax</span></span>  
  
```xml  
<security>  
   <transport credentialType="Certificate/Password" />  
</security>         
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6757d-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6757d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6757d-113">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="6757d-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6757d-114">屬性</span><span class="sxs-lookup"><span data-stu-id="6757d-114">Attributes</span></span>  
  
|<span data-ttu-id="6757d-115">屬性</span><span class="sxs-lookup"><span data-stu-id="6757d-115">Attribute</span></span>|<span data-ttu-id="6757d-116">描述</span><span class="sxs-lookup"><span data-stu-id="6757d-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6757d-117">credentialType</span><span class="sxs-lookup"><span data-stu-id="6757d-117">credentialType</span></span>|<span data-ttu-id="6757d-118">選擇項。</span><span class="sxs-lookup"><span data-stu-id="6757d-118">Optional.</span></span> <span data-ttu-id="6757d-119">指定認證的類型，用於驗證對等傳輸所傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="6757d-119">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="6757d-120">此屬性的型別為 <xref:System.ServiceModel.PeerTransportCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="6757d-120">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="6757d-121">credentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="6757d-121">credentialType Attribute</span></span>  
  
|<span data-ttu-id="6757d-122">值</span><span class="sxs-lookup"><span data-stu-id="6757d-122">Value</span></span>|<span data-ttu-id="6757d-123">描述</span><span class="sxs-lookup"><span data-stu-id="6757d-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6757d-124">憑證</span><span class="sxs-lookup"><span data-stu-id="6757d-124">Certificate</span></span>|<span data-ttu-id="6757d-125">對等通道傳輸的驗證作業需要 X509 憑證。</span><span class="sxs-lookup"><span data-stu-id="6757d-125">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="6757d-126">密碼</span><span class="sxs-lookup"><span data-stu-id="6757d-126">Password</span></span>|<span data-ttu-id="6757d-127">對等通道傳輸的驗證作業需要正確的密碼。</span><span class="sxs-lookup"><span data-stu-id="6757d-127">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6757d-128">子元素</span><span class="sxs-lookup"><span data-stu-id="6757d-128">Child Elements</span></span>  
 <span data-ttu-id="6757d-129">無</span><span class="sxs-lookup"><span data-stu-id="6757d-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6757d-130">父項目</span><span class="sxs-lookup"><span data-stu-id="6757d-130">Parent Elements</span></span>  
  
|<span data-ttu-id="6757d-131">項目</span><span class="sxs-lookup"><span data-stu-id="6757d-131">Element</span></span>|<span data-ttu-id="6757d-132">說明</span><span class="sxs-lookup"><span data-stu-id="6757d-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6757d-133">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="6757d-133">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="6757d-134">定義對等傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="6757d-134">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6757d-135">備註</span><span class="sxs-lookup"><span data-stu-id="6757d-135">Remarks</span></span>  
 <span data-ttu-id="6757d-136">只有當這個項目會設定目的 mode 屬性[\<安全性 >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)設`Transport`或`TransportWithMessageCredential`。</span><span class="sxs-lookup"><span data-stu-id="6757d-136">This element is set only if the mode attribute of [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6757d-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6757d-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="6757d-138">傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="6757d-138">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [<span data-ttu-id="6757d-139">傳輸</span><span class="sxs-lookup"><span data-stu-id="6757d-139">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="6757d-140">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="6757d-140">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="6757d-141">繫結</span><span class="sxs-lookup"><span data-stu-id="6757d-141">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="6757d-142">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="6757d-142">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="6757d-143">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="6757d-143">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="6757d-144">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="6757d-144">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
