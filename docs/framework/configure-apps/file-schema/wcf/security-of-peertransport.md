---
title: <security> 的 <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: 1aff79bf5867a3a1ebe05e3f812475dac4b413e9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670491"
---
# <a name="security-of-peertransport"></a><span data-ttu-id="1f9c2-102">\<安全性 > 的\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="1f9c2-102">\<security> of \<peerTransport></span></span>
<span data-ttu-id="1f9c2-103">包含與對等通道相關聯的安全性設定，包括使用的驗證類型與訊息傳輸所用的安全性。</span><span class="sxs-lookup"><span data-stu-id="1f9c2-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="1f9c2-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1f9c2-104">\<system.serviceModel></span></span>  
<span data-ttu-id="1f9c2-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="1f9c2-105">\<bindings></span></span>  
<span data-ttu-id="1f9c2-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="1f9c2-106">\<customBinding></span></span>  
<span data-ttu-id="1f9c2-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="1f9c2-107">\<binding></span></span>  
<span data-ttu-id="1f9c2-108">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="1f9c2-108">\<peerTransport></span></span>  
<span data-ttu-id="1f9c2-109">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="1f9c2-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f9c2-110">語法</span><span class="sxs-lookup"><span data-stu-id="1f9c2-110">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f9c2-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1f9c2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1f9c2-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1f9c2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f9c2-113">屬性</span><span class="sxs-lookup"><span data-stu-id="1f9c2-113">Attributes</span></span>  
  
|<span data-ttu-id="1f9c2-114">屬性</span><span class="sxs-lookup"><span data-stu-id="1f9c2-114">Attribute</span></span>|<span data-ttu-id="1f9c2-115">描述</span><span class="sxs-lookup"><span data-stu-id="1f9c2-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="1f9c2-116">指定要套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="1f9c2-116">Specifies the type of security to be applied.</span></span> <span data-ttu-id="1f9c2-117">預設值為 Message。</span><span class="sxs-lookup"><span data-stu-id="1f9c2-117">The default value is Message.</span></span> <span data-ttu-id="1f9c2-118">此屬性的型別為 <xref:System.ServiceModel.SecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="1f9c2-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="1f9c2-119">mode 屬性</span><span class="sxs-lookup"><span data-stu-id="1f9c2-119">mode Attribute</span></span>  
  
|<span data-ttu-id="1f9c2-120">值</span><span class="sxs-lookup"><span data-stu-id="1f9c2-120">Value</span></span>|<span data-ttu-id="1f9c2-121">描述</span><span class="sxs-lookup"><span data-stu-id="1f9c2-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="1f9c2-122">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="1f9c2-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="1f9c2-123">系統會使用 HTTPS 來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="1f9c2-123">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="1f9c2-124">SOAP 安全性提供驗證、完整性和機密性。</span><span class="sxs-lookup"><span data-stu-id="1f9c2-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="1f9c2-125">HTTPS 提供驗證和機密性。</span><span class="sxs-lookup"><span data-stu-id="1f9c2-125">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="1f9c2-126">SOAP 訊息提供豐富的認證類型。</span><span class="sxs-lookup"><span data-stu-id="1f9c2-126">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1f9c2-127">子元素</span><span class="sxs-lookup"><span data-stu-id="1f9c2-127">Child Elements</span></span>  
  
|<span data-ttu-id="1f9c2-128">項目</span><span class="sxs-lookup"><span data-stu-id="1f9c2-128">Element</span></span>|<span data-ttu-id="1f9c2-129">描述</span><span class="sxs-lookup"><span data-stu-id="1f9c2-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1f9c2-130">\<transport></span><span class="sxs-lookup"><span data-stu-id="1f9c2-130">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-peertransport.md)|<span data-ttu-id="1f9c2-131">定義自訂繫結的對等傳輸。</span><span class="sxs-lookup"><span data-stu-id="1f9c2-131">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="1f9c2-132">此項目具有 `clientCredentialType` 屬性，可指定與服務互動時所用的認證。</span><span class="sxs-lookup"><span data-stu-id="1f9c2-132">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="1f9c2-133">此屬性的型別為 <xref:System.ServiceModel.PeerTransportCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="1f9c2-133">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="1f9c2-134">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="1f9c2-134">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1f9c2-135">父項目</span><span class="sxs-lookup"><span data-stu-id="1f9c2-135">Parent Elements</span></span>  
  
|<span data-ttu-id="1f9c2-136">項目</span><span class="sxs-lookup"><span data-stu-id="1f9c2-136">Element</span></span>|<span data-ttu-id="1f9c2-137">描述</span><span class="sxs-lookup"><span data-stu-id="1f9c2-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1f9c2-138">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="1f9c2-138">\<peerTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peertransport.md)|<span data-ttu-id="1f9c2-139">定義自訂繫結的對等傳輸。</span><span class="sxs-lookup"><span data-stu-id="1f9c2-139">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1f9c2-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f9c2-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="1f9c2-141">傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="1f9c2-141">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)
- [<span data-ttu-id="1f9c2-142">傳輸</span><span class="sxs-lookup"><span data-stu-id="1f9c2-142">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="1f9c2-143">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="1f9c2-143">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="1f9c2-144">繫結</span><span class="sxs-lookup"><span data-stu-id="1f9c2-144">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="1f9c2-145">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="1f9c2-145">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="1f9c2-146">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="1f9c2-146">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="1f9c2-147">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="1f9c2-147">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
