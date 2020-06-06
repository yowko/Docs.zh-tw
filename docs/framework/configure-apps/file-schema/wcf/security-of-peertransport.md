---
title: <security> 的 <peerTransport>
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: 270ca844f586be256b6483653c868d1cc4396657
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399774"
---
# <a name="security-of-peertransport"></a><span data-ttu-id="526d1-102">\<security> 的 \<peerTransport></span><span class="sxs-lookup"><span data-stu-id="526d1-102">\<security> of \<peerTransport></span></span>
<span data-ttu-id="526d1-103">包含與對等通道相關聯的安全性設定，包括使用的驗證類型與訊息傳輸所用的安全性。</span><span class="sxs-lookup"><span data-stu-id="526d1-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="526d1-104">語法</span><span class="sxs-lookup"><span data-stu-id="526d1-104">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="526d1-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="526d1-105">Attributes and Elements</span></span>  
 <span data-ttu-id="526d1-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="526d1-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="526d1-107">屬性</span><span class="sxs-lookup"><span data-stu-id="526d1-107">Attributes</span></span>  
  
|<span data-ttu-id="526d1-108">屬性</span><span class="sxs-lookup"><span data-stu-id="526d1-108">Attribute</span></span>|<span data-ttu-id="526d1-109">描述</span><span class="sxs-lookup"><span data-stu-id="526d1-109">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="526d1-110">指定要套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="526d1-110">Specifies the type of security to be applied.</span></span> <span data-ttu-id="526d1-111">預設值為 Message。</span><span class="sxs-lookup"><span data-stu-id="526d1-111">The default value is Message.</span></span> <span data-ttu-id="526d1-112">此屬性的型別為 <xref:System.ServiceModel.SecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="526d1-112">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="526d1-113">mode 屬性</span><span class="sxs-lookup"><span data-stu-id="526d1-113">mode Attribute</span></span>  
  
|<span data-ttu-id="526d1-114">值</span><span class="sxs-lookup"><span data-stu-id="526d1-114">Value</span></span>|<span data-ttu-id="526d1-115">描述</span><span class="sxs-lookup"><span data-stu-id="526d1-115">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="526d1-116">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="526d1-116">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="526d1-117">系統會使用 HTTPS 來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="526d1-117">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="526d1-118">SOAP 安全性提供驗證、完整性和機密性。</span><span class="sxs-lookup"><span data-stu-id="526d1-118">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="526d1-119">HTTPS 提供驗證和機密性。</span><span class="sxs-lookup"><span data-stu-id="526d1-119">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="526d1-120">SOAP 訊息提供豐富的認證類型。</span><span class="sxs-lookup"><span data-stu-id="526d1-120">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="526d1-121">子元素</span><span class="sxs-lookup"><span data-stu-id="526d1-121">Child Elements</span></span>  
  
|<span data-ttu-id="526d1-122">元素</span><span class="sxs-lookup"><span data-stu-id="526d1-122">Element</span></span>|<span data-ttu-id="526d1-123">描述</span><span class="sxs-lookup"><span data-stu-id="526d1-123">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-peertransport.md)|<span data-ttu-id="526d1-124">定義自訂繫結的對等傳輸。</span><span class="sxs-lookup"><span data-stu-id="526d1-124">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="526d1-125">此項目具有 `clientCredentialType` 屬性，可指定與服務互動時所用的認證。</span><span class="sxs-lookup"><span data-stu-id="526d1-125">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="526d1-126">此屬性的型別為 <xref:System.ServiceModel.PeerTransportCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="526d1-126">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="526d1-127">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="526d1-127">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="526d1-128">父項目</span><span class="sxs-lookup"><span data-stu-id="526d1-128">Parent Elements</span></span>  
  
|<span data-ttu-id="526d1-129">元素</span><span class="sxs-lookup"><span data-stu-id="526d1-129">Element</span></span>|<span data-ttu-id="526d1-130">描述</span><span class="sxs-lookup"><span data-stu-id="526d1-130">Description</span></span>|  
|-------------|-----------------|  
|[\<peerTransport>](peertransport.md)|<span data-ttu-id="526d1-131">定義自訂繫結的對等傳輸。</span><span class="sxs-lookup"><span data-stu-id="526d1-131">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="526d1-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="526d1-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="526d1-133">傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="526d1-133">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="526d1-134">傳輸</span><span class="sxs-lookup"><span data-stu-id="526d1-134">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="526d1-135">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="526d1-135">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="526d1-136">繫結</span><span class="sxs-lookup"><span data-stu-id="526d1-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="526d1-137">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="526d1-137">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="526d1-138">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="526d1-138">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
