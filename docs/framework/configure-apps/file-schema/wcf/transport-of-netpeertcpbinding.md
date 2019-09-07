---
title: <transport> 的 <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 08be5d752f8422ebe6442b295195f21b16a274c0
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399324"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="29ff9-102">\<netPeerTcpBinding > 的\<傳輸 ></span><span class="sxs-lookup"><span data-stu-id="29ff9-102">\<transport> of \<netPeerTcpBinding></span></span>
<span data-ttu-id="29ff9-103">指定使用[ \<netPeerTcpBinding >](netpeertcpbinding.md)時的傳輸層級安全性設定。</span><span class="sxs-lookup"><span data-stu-id="29ff9-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>  
  
<span data-ttu-id="29ff9-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="29ff9-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="29ff9-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="29ff9-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="29ff9-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="29ff9-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="29ff9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netPeerTcpBinding >** ](netpeertcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="29ff9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)</span></span>\
<span data-ttu-id="29ff9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="29ff9-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="29ff9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-of-netpeerbinding.md)</span><span class="sxs-lookup"><span data-stu-id="29ff9-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netpeerbinding.md)</span></span>\
<span data-ttu-id="29ff9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<傳輸 >**</span><span class="sxs-lookup"><span data-stu-id="29ff9-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29ff9-111">語法</span><span class="sxs-lookup"><span data-stu-id="29ff9-111">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="29ff9-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="29ff9-112">Attributes and Elements</span></span>  
 <span data-ttu-id="29ff9-113">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="29ff9-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="29ff9-114">屬性</span><span class="sxs-lookup"><span data-stu-id="29ff9-114">Attributes</span></span>  
  
|<span data-ttu-id="29ff9-115">屬性</span><span class="sxs-lookup"><span data-stu-id="29ff9-115">Attribute</span></span>|<span data-ttu-id="29ff9-116">描述</span><span class="sxs-lookup"><span data-stu-id="29ff9-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="29ff9-117">credentialType</span><span class="sxs-lookup"><span data-stu-id="29ff9-117">credentialType</span></span>|<span data-ttu-id="29ff9-118">選擇性。</span><span class="sxs-lookup"><span data-stu-id="29ff9-118">Optional.</span></span> <span data-ttu-id="29ff9-119">指定認證的類型，用於驗證對等傳輸所傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="29ff9-119">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="29ff9-120">此屬性的型別為 <xref:System.ServiceModel.PeerTransportCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="29ff9-120">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="29ff9-121">credentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="29ff9-121">credentialType Attribute</span></span>  
  
|<span data-ttu-id="29ff9-122">值</span><span class="sxs-lookup"><span data-stu-id="29ff9-122">Value</span></span>|<span data-ttu-id="29ff9-123">描述</span><span class="sxs-lookup"><span data-stu-id="29ff9-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="29ff9-124">憑證</span><span class="sxs-lookup"><span data-stu-id="29ff9-124">Certificate</span></span>|<span data-ttu-id="29ff9-125">對等通道傳輸的驗證作業需要 X509 憑證。</span><span class="sxs-lookup"><span data-stu-id="29ff9-125">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="29ff9-126">密碼</span><span class="sxs-lookup"><span data-stu-id="29ff9-126">Password</span></span>|<span data-ttu-id="29ff9-127">對等通道傳輸的驗證作業需要正確的密碼。</span><span class="sxs-lookup"><span data-stu-id="29ff9-127">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="29ff9-128">子元素</span><span class="sxs-lookup"><span data-stu-id="29ff9-128">Child Elements</span></span>  
 <span data-ttu-id="29ff9-129">無</span><span class="sxs-lookup"><span data-stu-id="29ff9-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="29ff9-130">父項目</span><span class="sxs-lookup"><span data-stu-id="29ff9-130">Parent Elements</span></span>  
  
|<span data-ttu-id="29ff9-131">項目</span><span class="sxs-lookup"><span data-stu-id="29ff9-131">Element</span></span>|<span data-ttu-id="29ff9-132">說明</span><span class="sxs-lookup"><span data-stu-id="29ff9-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="29ff9-133">\<security></span><span class="sxs-lookup"><span data-stu-id="29ff9-133">\<security></span></span>](security-of-netpeerbinding.md)|<span data-ttu-id="29ff9-134">定義[ \<netPeerTcpBinding >](netpeertcpbinding.md)的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="29ff9-134">Defines the security settings for the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="29ff9-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29ff9-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="29ff9-136">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="29ff9-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="29ff9-137">繫結</span><span class="sxs-lookup"><span data-stu-id="29ff9-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="29ff9-138">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="29ff9-138">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="29ff9-139">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="29ff9-139">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="29ff9-140">\<binding></span><span class="sxs-lookup"><span data-stu-id="29ff9-140">\<binding></span></span>](../../../misc/binding.md)
