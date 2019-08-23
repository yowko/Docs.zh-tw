---
title: <transport> 的 <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: 5dbc55db25c0c49d72ec2cd8dd1041a3f8705d8e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940638"
---
# <a name="transport-of-peertransport"></a><span data-ttu-id="94206-102">\<peerTransport > 的\<傳輸 ></span><span class="sxs-lookup"><span data-stu-id="94206-102">\<transport> of \<peerTransport></span></span>
<span data-ttu-id="94206-103">指定使用這個繫結設定之對等所傳送安全訊息的傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="94206-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
 <span data-ttu-id="94206-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="94206-104">\<system.serviceModel></span></span>  
<span data-ttu-id="94206-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="94206-105">\<bindings></span></span>  
<span data-ttu-id="94206-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="94206-106">\<customBinding></span></span>  
<span data-ttu-id="94206-107">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="94206-107">\<binding></span></span>  
<span data-ttu-id="94206-108">\<peerTransport></span><span class="sxs-lookup"><span data-stu-id="94206-108">\<peerTransport></span></span>  
<span data-ttu-id="94206-109">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="94206-109">\<security></span></span>  
<span data-ttu-id="94206-110">\<transport></span><span class="sxs-lookup"><span data-stu-id="94206-110">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94206-111">語法</span><span class="sxs-lookup"><span data-stu-id="94206-111">Syntax</span></span>  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94206-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="94206-112">Attributes and Elements</span></span>  
 <span data-ttu-id="94206-113">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="94206-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94206-114">屬性</span><span class="sxs-lookup"><span data-stu-id="94206-114">Attributes</span></span>  
  
|<span data-ttu-id="94206-115">屬性</span><span class="sxs-lookup"><span data-stu-id="94206-115">Attribute</span></span>|<span data-ttu-id="94206-116">描述</span><span class="sxs-lookup"><span data-stu-id="94206-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="94206-117">credentialType</span><span class="sxs-lookup"><span data-stu-id="94206-117">credentialType</span></span>|<span data-ttu-id="94206-118">選擇性。</span><span class="sxs-lookup"><span data-stu-id="94206-118">Optional.</span></span> <span data-ttu-id="94206-119">指定認證的類型，用於驗證對等傳輸所傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="94206-119">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="94206-120">此屬性的型別為 <xref:System.ServiceModel.PeerTransportCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="94206-120">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="94206-121">credentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="94206-121">credentialType Attribute</span></span>  
  
|<span data-ttu-id="94206-122">值</span><span class="sxs-lookup"><span data-stu-id="94206-122">Value</span></span>|<span data-ttu-id="94206-123">說明</span><span class="sxs-lookup"><span data-stu-id="94206-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="94206-124">憑證</span><span class="sxs-lookup"><span data-stu-id="94206-124">Certificate</span></span>|<span data-ttu-id="94206-125">對等通道傳輸的驗證作業需要 X509 憑證。</span><span class="sxs-lookup"><span data-stu-id="94206-125">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="94206-126">密碼</span><span class="sxs-lookup"><span data-stu-id="94206-126">Password</span></span>|<span data-ttu-id="94206-127">對等通道傳輸的驗證作業需要正確的密碼。</span><span class="sxs-lookup"><span data-stu-id="94206-127">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="94206-128">子元素</span><span class="sxs-lookup"><span data-stu-id="94206-128">Child Elements</span></span>  
 <span data-ttu-id="94206-129">無</span><span class="sxs-lookup"><span data-stu-id="94206-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="94206-130">父項目</span><span class="sxs-lookup"><span data-stu-id="94206-130">Parent Elements</span></span>  
  
|<span data-ttu-id="94206-131">項目</span><span class="sxs-lookup"><span data-stu-id="94206-131">Element</span></span>|<span data-ttu-id="94206-132">描述</span><span class="sxs-lookup"><span data-stu-id="94206-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="94206-133">\<security></span><span class="sxs-lookup"><span data-stu-id="94206-133">\<security></span></span>](security-of-peertransport.md)|<span data-ttu-id="94206-134">定義對等傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="94206-134">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94206-135">備註</span><span class="sxs-lookup"><span data-stu-id="94206-135">Remarks</span></span>  
 <span data-ttu-id="94206-136">只有在  [ \<安全性 >](security-of-peertransport.md)的 [模式] 屬性設定為`Transport`或`TransportWithMessageCredential`時, 才會設定此元素。</span><span class="sxs-lookup"><span data-stu-id="94206-136">This element is set only if the mode attribute of [\<security>](security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94206-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94206-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="94206-138">傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="94206-138">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="94206-139">傳輸</span><span class="sxs-lookup"><span data-stu-id="94206-139">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="94206-140">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="94206-140">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="94206-141">繫結</span><span class="sxs-lookup"><span data-stu-id="94206-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="94206-142">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="94206-142">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="94206-143">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="94206-143">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="94206-144">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="94206-144">\<customBinding></span></span>](custombinding.md)
