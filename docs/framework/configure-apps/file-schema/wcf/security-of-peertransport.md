---
title: <security> 的 <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: 270ca844f586be256b6483653c868d1cc4396657
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399774"
---
# <a name="security-of-peertransport"></a><span data-ttu-id="556e6-102">\<peerTransport > 的\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="556e6-102">\<security> of \<peerTransport></span></span>
<span data-ttu-id="556e6-103">包含與對等通道相關聯的安全性設定，包括使用的驗證類型與訊息傳輸所用的安全性。</span><span class="sxs-lookup"><span data-stu-id="556e6-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
<span data-ttu-id="556e6-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="556e6-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="556e6-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="556e6-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="556e6-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="556e6-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="556e6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="556e6-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="556e6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="556e6-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="556e6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<peerTransport >** ](peertransport.md)</span><span class="sxs-lookup"><span data-stu-id="556e6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)</span></span>\
<span data-ttu-id="556e6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<安全性 >**</span><span class="sxs-lookup"><span data-stu-id="556e6-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="556e6-111">語法</span><span class="sxs-lookup"><span data-stu-id="556e6-111">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="556e6-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="556e6-112">Attributes and Elements</span></span>  
 <span data-ttu-id="556e6-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="556e6-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="556e6-114">屬性</span><span class="sxs-lookup"><span data-stu-id="556e6-114">Attributes</span></span>  
  
|<span data-ttu-id="556e6-115">屬性</span><span class="sxs-lookup"><span data-stu-id="556e6-115">Attribute</span></span>|<span data-ttu-id="556e6-116">描述</span><span class="sxs-lookup"><span data-stu-id="556e6-116">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="556e6-117">指定要套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="556e6-117">Specifies the type of security to be applied.</span></span> <span data-ttu-id="556e6-118">預設值為 Message。</span><span class="sxs-lookup"><span data-stu-id="556e6-118">The default value is Message.</span></span> <span data-ttu-id="556e6-119">此屬性的型別為 <xref:System.ServiceModel.SecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="556e6-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="556e6-120">mode 屬性</span><span class="sxs-lookup"><span data-stu-id="556e6-120">mode Attribute</span></span>  
  
|<span data-ttu-id="556e6-121">值</span><span class="sxs-lookup"><span data-stu-id="556e6-121">Value</span></span>|<span data-ttu-id="556e6-122">描述</span><span class="sxs-lookup"><span data-stu-id="556e6-122">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="556e6-123">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="556e6-123">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="556e6-124">系統會使用 HTTPS 來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="556e6-124">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="556e6-125">SOAP 安全性提供驗證、完整性和機密性。</span><span class="sxs-lookup"><span data-stu-id="556e6-125">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="556e6-126">HTTPS 提供驗證和機密性。</span><span class="sxs-lookup"><span data-stu-id="556e6-126">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="556e6-127">SOAP 訊息提供豐富的認證類型。</span><span class="sxs-lookup"><span data-stu-id="556e6-127">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="556e6-128">子元素</span><span class="sxs-lookup"><span data-stu-id="556e6-128">Child Elements</span></span>  
  
|<span data-ttu-id="556e6-129">項目</span><span class="sxs-lookup"><span data-stu-id="556e6-129">Element</span></span>|<span data-ttu-id="556e6-130">描述</span><span class="sxs-lookup"><span data-stu-id="556e6-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="556e6-131">\<transport></span><span class="sxs-lookup"><span data-stu-id="556e6-131">\<transport></span></span>](transport-of-peertransport.md)|<span data-ttu-id="556e6-132">定義自訂繫結的對等傳輸。</span><span class="sxs-lookup"><span data-stu-id="556e6-132">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="556e6-133">此項目具有 `clientCredentialType` 屬性，可指定與服務互動時所用的認證。</span><span class="sxs-lookup"><span data-stu-id="556e6-133">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="556e6-134">此屬性的型別為 <xref:System.ServiceModel.PeerTransportCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="556e6-134">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="556e6-135">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="556e6-135">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="556e6-136">父項目</span><span class="sxs-lookup"><span data-stu-id="556e6-136">Parent Elements</span></span>  
  
|<span data-ttu-id="556e6-137">項目</span><span class="sxs-lookup"><span data-stu-id="556e6-137">Element</span></span>|<span data-ttu-id="556e6-138">說明</span><span class="sxs-lookup"><span data-stu-id="556e6-138">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="556e6-139">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="556e6-139">\<peerTransport></span></span>](peertransport.md)|<span data-ttu-id="556e6-140">定義自訂繫結的對等傳輸。</span><span class="sxs-lookup"><span data-stu-id="556e6-140">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="556e6-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="556e6-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="556e6-142">傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="556e6-142">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="556e6-143">傳輸</span><span class="sxs-lookup"><span data-stu-id="556e6-143">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="556e6-144">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="556e6-144">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="556e6-145">繫結</span><span class="sxs-lookup"><span data-stu-id="556e6-145">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="556e6-146">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="556e6-146">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="556e6-147">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="556e6-147">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="556e6-148">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="556e6-148">\<customBinding></span></span>](custombinding.md)
