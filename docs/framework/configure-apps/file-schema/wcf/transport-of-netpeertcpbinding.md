---
title: <transport> 的 <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 49b31a889d192d190125214e89ba09305114eb7f
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735969"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="77220-102">\<netPeerTcpBinding 的 \<傳輸 > ></span><span class="sxs-lookup"><span data-stu-id="77220-102">\<transport> of \<netPeerTcpBinding></span></span>
<span data-ttu-id="77220-103">指定使用[\<netPeerTcpBinding >](netpeertcpbinding.md)時的傳輸層級安全性設定。</span><span class="sxs-lookup"><span data-stu-id="77220-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>  
  
<span data-ttu-id="77220-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="77220-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="77220-105">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="77220-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="77220-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="77220-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="77220-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netPeerTcpBinding >** ](netpeertcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="77220-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)</span></span>\
<span data-ttu-id="77220-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 ></span><span class="sxs-lookup"><span data-stu-id="77220-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="77220-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-of-netpeerbinding.md)</span><span class="sxs-lookup"><span data-stu-id="77220-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netpeerbinding.md)</span></span>\
<span data-ttu-id="77220-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**傳輸 >**</span><span class="sxs-lookup"><span data-stu-id="77220-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77220-111">語法</span><span class="sxs-lookup"><span data-stu-id="77220-111">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="77220-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="77220-112">Attributes and Elements</span></span>  
 <span data-ttu-id="77220-113">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="77220-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="77220-114">屬性</span><span class="sxs-lookup"><span data-stu-id="77220-114">Attributes</span></span>  
  
|<span data-ttu-id="77220-115">屬性</span><span class="sxs-lookup"><span data-stu-id="77220-115">Attribute</span></span>|<span data-ttu-id="77220-116">描述</span><span class="sxs-lookup"><span data-stu-id="77220-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="77220-117">credentialType</span><span class="sxs-lookup"><span data-stu-id="77220-117">credentialType</span></span>|<span data-ttu-id="77220-118">選擇項。</span><span class="sxs-lookup"><span data-stu-id="77220-118">Optional.</span></span> <span data-ttu-id="77220-119">指定認證的類型，用於驗證對等傳輸所傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="77220-119">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="77220-120">此屬性的型別為 <xref:System.ServiceModel.PeerTransportCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="77220-120">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="77220-121">credentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="77220-121">credentialType Attribute</span></span>  
  
|<span data-ttu-id="77220-122">值</span><span class="sxs-lookup"><span data-stu-id="77220-122">Value</span></span>|<span data-ttu-id="77220-123">描述</span><span class="sxs-lookup"><span data-stu-id="77220-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="77220-124">憑證</span><span class="sxs-lookup"><span data-stu-id="77220-124">Certificate</span></span>|<span data-ttu-id="77220-125">對等通道傳輸的驗證作業需要 X509 憑證。</span><span class="sxs-lookup"><span data-stu-id="77220-125">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="77220-126">密碼</span><span class="sxs-lookup"><span data-stu-id="77220-126">Password</span></span>|<span data-ttu-id="77220-127">對等通道傳輸的驗證作業需要正確的密碼。</span><span class="sxs-lookup"><span data-stu-id="77220-127">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="77220-128">子項目</span><span class="sxs-lookup"><span data-stu-id="77220-128">Child Elements</span></span>  
 <span data-ttu-id="77220-129">None</span><span class="sxs-lookup"><span data-stu-id="77220-129">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="77220-130">父項目</span><span class="sxs-lookup"><span data-stu-id="77220-130">Parent Elements</span></span>  
  
|<span data-ttu-id="77220-131">項目</span><span class="sxs-lookup"><span data-stu-id="77220-131">Element</span></span>|<span data-ttu-id="77220-132">描述</span><span class="sxs-lookup"><span data-stu-id="77220-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="77220-133">\<security ></span><span class="sxs-lookup"><span data-stu-id="77220-133">\<security></span></span>](security-of-netpeerbinding.md)|<span data-ttu-id="77220-134">定義[\<netPeerTcpBinding >](netpeertcpbinding.md)的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="77220-134">Defines the security settings for the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="77220-135">請參閱</span><span class="sxs-lookup"><span data-stu-id="77220-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="77220-136">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="77220-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="77220-137">繫結</span><span class="sxs-lookup"><span data-stu-id="77220-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="77220-138">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="77220-138">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="77220-139">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="77220-139">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="77220-140">\<binding ></span><span class="sxs-lookup"><span data-stu-id="77220-140">\<binding></span></span>](bindings.md)
