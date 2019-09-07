---
title: <transport> 的 <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: 3b2c7716727f58abb81bf4d58b13189ac170cf7c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399294"
---
# <a name="transport-of-peertransport"></a><span data-ttu-id="7c166-102">\<peerTransport > 的\<傳輸 ></span><span class="sxs-lookup"><span data-stu-id="7c166-102">\<transport> of \<peerTransport></span></span>
<span data-ttu-id="7c166-103">指定使用這個繫結設定之對等所傳送安全訊息的傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="7c166-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
<span data-ttu-id="7c166-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7c166-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7c166-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="7c166-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7c166-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="7c166-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="7c166-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="7c166-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="7c166-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="7c166-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="7c166-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<peerTransport >** ](peertransport.md)</span><span class="sxs-lookup"><span data-stu-id="7c166-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)</span></span>\
<span data-ttu-id="7c166-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-of-peertransport.md)</span><span class="sxs-lookup"><span data-stu-id="7c166-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-peertransport.md)</span></span>\
<span data-ttu-id="7c166-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<傳輸 >**</span><span class="sxs-lookup"><span data-stu-id="7c166-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c166-112">語法</span><span class="sxs-lookup"><span data-stu-id="7c166-112">Syntax</span></span>  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c166-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7c166-113">Attributes and Elements</span></span>  
 <span data-ttu-id="7c166-114">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="7c166-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c166-115">屬性</span><span class="sxs-lookup"><span data-stu-id="7c166-115">Attributes</span></span>  
  
|<span data-ttu-id="7c166-116">屬性</span><span class="sxs-lookup"><span data-stu-id="7c166-116">Attribute</span></span>|<span data-ttu-id="7c166-117">描述</span><span class="sxs-lookup"><span data-stu-id="7c166-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7c166-118">credentialType</span><span class="sxs-lookup"><span data-stu-id="7c166-118">credentialType</span></span>|<span data-ttu-id="7c166-119">選擇性。</span><span class="sxs-lookup"><span data-stu-id="7c166-119">Optional.</span></span> <span data-ttu-id="7c166-120">指定認證的類型，用於驗證對等傳輸所傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="7c166-120">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="7c166-121">此屬性的型別為 <xref:System.ServiceModel.PeerTransportCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="7c166-121">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="7c166-122">credentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="7c166-122">credentialType Attribute</span></span>  
  
|<span data-ttu-id="7c166-123">值</span><span class="sxs-lookup"><span data-stu-id="7c166-123">Value</span></span>|<span data-ttu-id="7c166-124">描述</span><span class="sxs-lookup"><span data-stu-id="7c166-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7c166-125">憑證</span><span class="sxs-lookup"><span data-stu-id="7c166-125">Certificate</span></span>|<span data-ttu-id="7c166-126">對等通道傳輸的驗證作業需要 X509 憑證。</span><span class="sxs-lookup"><span data-stu-id="7c166-126">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="7c166-127">密碼</span><span class="sxs-lookup"><span data-stu-id="7c166-127">Password</span></span>|<span data-ttu-id="7c166-128">對等通道傳輸的驗證作業需要正確的密碼。</span><span class="sxs-lookup"><span data-stu-id="7c166-128">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c166-129">子元素</span><span class="sxs-lookup"><span data-stu-id="7c166-129">Child Elements</span></span>  
 <span data-ttu-id="7c166-130">無</span><span class="sxs-lookup"><span data-stu-id="7c166-130">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7c166-131">父項目</span><span class="sxs-lookup"><span data-stu-id="7c166-131">Parent Elements</span></span>  
  
|<span data-ttu-id="7c166-132">項目</span><span class="sxs-lookup"><span data-stu-id="7c166-132">Element</span></span>|<span data-ttu-id="7c166-133">描述</span><span class="sxs-lookup"><span data-stu-id="7c166-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c166-134">\<security></span><span class="sxs-lookup"><span data-stu-id="7c166-134">\<security></span></span>](security-of-peertransport.md)|<span data-ttu-id="7c166-135">定義對等傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="7c166-135">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c166-136">備註</span><span class="sxs-lookup"><span data-stu-id="7c166-136">Remarks</span></span>  
 <span data-ttu-id="7c166-137">只有在  [ \<安全性 >](security-of-peertransport.md)的 [模式] 屬性設定為`Transport`或`TransportWithMessageCredential`時，才會設定此元素。</span><span class="sxs-lookup"><span data-stu-id="7c166-137">This element is set only if the mode attribute of [\<security>](security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c166-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c166-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="7c166-139">傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="7c166-139">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="7c166-140">傳輸</span><span class="sxs-lookup"><span data-stu-id="7c166-140">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="7c166-141">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="7c166-141">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="7c166-142">繫結</span><span class="sxs-lookup"><span data-stu-id="7c166-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7c166-143">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="7c166-143">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="7c166-144">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="7c166-144">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="7c166-145">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="7c166-145">\<customBinding></span></span>](custombinding.md)
