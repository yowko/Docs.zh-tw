---
title: <transport> 的 <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: 7328d67c4649010dce3e1c866238d1e0067e4990
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157066"
---
# <a name="transport-of-peertransport"></a><span data-ttu-id="9e4e7-102">\<transport> 的 \<peerTransport></span><span class="sxs-lookup"><span data-stu-id="9e4e7-102">\<transport> of \<peerTransport></span></span>

<span data-ttu-id="9e4e7-103">指定使用這個繫結設定之對等所傳送安全訊息的傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="9e4e7-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="9e4e7-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="9e4e7-104">Syntax</span></span>  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9e4e7-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9e4e7-105">Attributes and Elements</span></span>  

 <span data-ttu-id="9e4e7-106">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="9e4e7-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9e4e7-107">屬性</span><span class="sxs-lookup"><span data-stu-id="9e4e7-107">Attributes</span></span>  
  
|<span data-ttu-id="9e4e7-108">屬性</span><span class="sxs-lookup"><span data-stu-id="9e4e7-108">Attribute</span></span>|<span data-ttu-id="9e4e7-109">描述</span><span class="sxs-lookup"><span data-stu-id="9e4e7-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9e4e7-110">credentialType</span><span class="sxs-lookup"><span data-stu-id="9e4e7-110">credentialType</span></span>|<span data-ttu-id="9e4e7-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="9e4e7-111">Optional.</span></span> <span data-ttu-id="9e4e7-112">指定認證的類型，用於驗證對等傳輸所傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="9e4e7-112">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="9e4e7-113">此屬性的型別為 <xref:System.ServiceModel.PeerTransportCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="9e4e7-113">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="9e4e7-114">credentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="9e4e7-114">credentialType Attribute</span></span>  
  
|<span data-ttu-id="9e4e7-115">值</span><span class="sxs-lookup"><span data-stu-id="9e4e7-115">Value</span></span>|<span data-ttu-id="9e4e7-116">描述</span><span class="sxs-lookup"><span data-stu-id="9e4e7-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9e4e7-117">憑證</span><span class="sxs-lookup"><span data-stu-id="9e4e7-117">Certificate</span></span>|<span data-ttu-id="9e4e7-118">對等通道傳輸的驗證作業需要 X509 憑證。</span><span class="sxs-lookup"><span data-stu-id="9e4e7-118">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="9e4e7-119">密碼</span><span class="sxs-lookup"><span data-stu-id="9e4e7-119">Password</span></span>|<span data-ttu-id="9e4e7-120">對等通道傳輸的驗證作業需要正確的密碼。</span><span class="sxs-lookup"><span data-stu-id="9e4e7-120">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9e4e7-121">子元素</span><span class="sxs-lookup"><span data-stu-id="9e4e7-121">Child Elements</span></span>  

 <span data-ttu-id="9e4e7-122">無</span><span class="sxs-lookup"><span data-stu-id="9e4e7-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9e4e7-123">父項目</span><span class="sxs-lookup"><span data-stu-id="9e4e7-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9e4e7-124">項目</span><span class="sxs-lookup"><span data-stu-id="9e4e7-124">Element</span></span>|<span data-ttu-id="9e4e7-125">描述</span><span class="sxs-lookup"><span data-stu-id="9e4e7-125">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-peertransport.md)|<span data-ttu-id="9e4e7-126">定義對等傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="9e4e7-126">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e4e7-127">備註</span><span class="sxs-lookup"><span data-stu-id="9e4e7-127">Remarks</span></span>  

 <span data-ttu-id="9e4e7-128">只有當的模式屬性設定為或時，才會設定這個元素 [\<security>](security-of-peertransport.md) `Transport` `TransportWithMessageCredential` 。</span><span class="sxs-lookup"><span data-stu-id="9e4e7-128">This element is set only if the mode attribute of [\<security>](security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e4e7-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e4e7-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="9e4e7-130">傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="9e4e7-130">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="9e4e7-131">傳輸</span><span class="sxs-lookup"><span data-stu-id="9e4e7-131">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="9e4e7-132">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="9e4e7-132">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="9e4e7-133">繫結</span><span class="sxs-lookup"><span data-stu-id="9e4e7-133">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9e4e7-134">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="9e4e7-134">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="9e4e7-135">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="9e4e7-135">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
