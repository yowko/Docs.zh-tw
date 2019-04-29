---
title: <transport> 的 <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: 9b6f548515afbba5068659bd5c6f7f2b33f80cda
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788280"
---
# <a name="transport-of-peertransport"></a><span data-ttu-id="ae38a-102">\<傳輸 > 的\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="ae38a-102">\<transport> of \<peerTransport></span></span>
<span data-ttu-id="ae38a-103">指定使用這個繫結設定之對等所傳送安全訊息的傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="ae38a-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
 <span data-ttu-id="ae38a-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ae38a-104">\<system.serviceModel></span></span>  
<span data-ttu-id="ae38a-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="ae38a-105">\<bindings></span></span>  
<span data-ttu-id="ae38a-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="ae38a-106">\<customBinding></span></span>  
<span data-ttu-id="ae38a-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="ae38a-107">\<binding></span></span>  
<span data-ttu-id="ae38a-108">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="ae38a-108">\<peerTransport></span></span>  
<span data-ttu-id="ae38a-109">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="ae38a-109">\<security></span></span>  
<span data-ttu-id="ae38a-110">\<transport></span><span class="sxs-lookup"><span data-stu-id="ae38a-110">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae38a-111">語法</span><span class="sxs-lookup"><span data-stu-id="ae38a-111">Syntax</span></span>  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ae38a-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ae38a-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ae38a-113">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="ae38a-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ae38a-114">屬性</span><span class="sxs-lookup"><span data-stu-id="ae38a-114">Attributes</span></span>  
  
|<span data-ttu-id="ae38a-115">屬性</span><span class="sxs-lookup"><span data-stu-id="ae38a-115">Attribute</span></span>|<span data-ttu-id="ae38a-116">描述</span><span class="sxs-lookup"><span data-stu-id="ae38a-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ae38a-117">credentialType</span><span class="sxs-lookup"><span data-stu-id="ae38a-117">credentialType</span></span>|<span data-ttu-id="ae38a-118">選擇性。</span><span class="sxs-lookup"><span data-stu-id="ae38a-118">Optional.</span></span> <span data-ttu-id="ae38a-119">指定認證的類型，用於驗證對等傳輸所傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="ae38a-119">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="ae38a-120">此屬性的型別為 <xref:System.ServiceModel.PeerTransportCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="ae38a-120">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="ae38a-121">credentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="ae38a-121">credentialType Attribute</span></span>  
  
|<span data-ttu-id="ae38a-122">值</span><span class="sxs-lookup"><span data-stu-id="ae38a-122">Value</span></span>|<span data-ttu-id="ae38a-123">描述</span><span class="sxs-lookup"><span data-stu-id="ae38a-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ae38a-124">憑證</span><span class="sxs-lookup"><span data-stu-id="ae38a-124">Certificate</span></span>|<span data-ttu-id="ae38a-125">對等通道傳輸的驗證作業需要 X509 憑證。</span><span class="sxs-lookup"><span data-stu-id="ae38a-125">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="ae38a-126">密碼</span><span class="sxs-lookup"><span data-stu-id="ae38a-126">Password</span></span>|<span data-ttu-id="ae38a-127">對等通道傳輸的驗證作業需要正確的密碼。</span><span class="sxs-lookup"><span data-stu-id="ae38a-127">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ae38a-128">子元素</span><span class="sxs-lookup"><span data-stu-id="ae38a-128">Child Elements</span></span>  
 <span data-ttu-id="ae38a-129">None</span><span class="sxs-lookup"><span data-stu-id="ae38a-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ae38a-130">父項目</span><span class="sxs-lookup"><span data-stu-id="ae38a-130">Parent Elements</span></span>  
  
|<span data-ttu-id="ae38a-131">項目</span><span class="sxs-lookup"><span data-stu-id="ae38a-131">Element</span></span>|<span data-ttu-id="ae38a-132">描述</span><span class="sxs-lookup"><span data-stu-id="ae38a-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ae38a-133">\<security></span><span class="sxs-lookup"><span data-stu-id="ae38a-133">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)|<span data-ttu-id="ae38a-134">定義對等傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="ae38a-134">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ae38a-135">備註</span><span class="sxs-lookup"><span data-stu-id="ae38a-135">Remarks</span></span>  
 <span data-ttu-id="ae38a-136">只有當設定這個項目的 mode 屬性[\<安全性 >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md)設定為`Transport`或`TransportWithMessageCredential`。</span><span class="sxs-lookup"><span data-stu-id="ae38a-136">This element is set only if the mode attribute of [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae38a-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae38a-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="ae38a-138">傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="ae38a-138">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)
- [<span data-ttu-id="ae38a-139">傳輸</span><span class="sxs-lookup"><span data-stu-id="ae38a-139">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)
- [<span data-ttu-id="ae38a-140">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="ae38a-140">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="ae38a-141">繫結</span><span class="sxs-lookup"><span data-stu-id="ae38a-141">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="ae38a-142">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="ae38a-142">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="ae38a-143">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="ae38a-143">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="ae38a-144">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="ae38a-144">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
