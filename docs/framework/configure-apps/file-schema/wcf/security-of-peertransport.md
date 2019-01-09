---
title: '&lt;peerTransport&gt; 的 &lt;security&gt;'
ms.date: 03/30/2017
ms.assetid: f73634ed-f896-4968-bf74-5e5ac52d3b6b
ms.openlocfilehash: 901a1d0b29fa6ea7d9e520b379dc7c7ff1d1e522
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151952"
---
# <a name="ltsecuritygt-of-ltpeertransportgt"></a><span data-ttu-id="fbf14-102">&lt;peerTransport&gt; 的 &lt;security&gt;</span><span class="sxs-lookup"><span data-stu-id="fbf14-102">&lt;security&gt; of &lt;peerTransport&gt;</span></span>
<span data-ttu-id="fbf14-103">包含與對等通道相關聯的安全性設定，包括使用的驗證類型與訊息傳輸所用的安全性。</span><span class="sxs-lookup"><span data-stu-id="fbf14-103">Contains the security settings associated with a peer channel, including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="fbf14-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="fbf14-104">\<system.serviceModel></span></span>  
<span data-ttu-id="fbf14-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="fbf14-105">\<bindings></span></span>  
<span data-ttu-id="fbf14-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="fbf14-106">\<customBinding></span></span>  
<span data-ttu-id="fbf14-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="fbf14-107">\<binding></span></span>  
<span data-ttu-id="fbf14-108">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="fbf14-108">\<peerTransport></span></span>  
<span data-ttu-id="fbf14-109">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="fbf14-109">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbf14-110">語法</span><span class="sxs-lookup"><span data-stu-id="fbf14-110">Syntax</span></span>  
  
```xml  
<security mode="None/Transport/Message/TransportWithMessageCredential">
  <transport clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
</security
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fbf14-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fbf14-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fbf14-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="fbf14-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fbf14-113">屬性</span><span class="sxs-lookup"><span data-stu-id="fbf14-113">Attributes</span></span>  
  
|<span data-ttu-id="fbf14-114">屬性</span><span class="sxs-lookup"><span data-stu-id="fbf14-114">Attribute</span></span>|<span data-ttu-id="fbf14-115">描述</span><span class="sxs-lookup"><span data-stu-id="fbf14-115">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="fbf14-116">指定要套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="fbf14-116">Specifies the type of security to be applied.</span></span> <span data-ttu-id="fbf14-117">預設值為 Message。</span><span class="sxs-lookup"><span data-stu-id="fbf14-117">The default value is Message.</span></span> <span data-ttu-id="fbf14-118">此屬性的型別為 <xref:System.ServiceModel.SecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="fbf14-118">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="fbf14-119">mode 屬性</span><span class="sxs-lookup"><span data-stu-id="fbf14-119">mode Attribute</span></span>  
  
|<span data-ttu-id="fbf14-120">值</span><span class="sxs-lookup"><span data-stu-id="fbf14-120">Value</span></span>|<span data-ttu-id="fbf14-121">描述</span><span class="sxs-lookup"><span data-stu-id="fbf14-121">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="fbf14-122">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="fbf14-122">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="fbf14-123">系統會使用 HTTPS 來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="fbf14-123">Security is provided using HTTPS.</span></span>|  
|`Message`|<span data-ttu-id="fbf14-124">SOAP 安全性提供驗證、完整性和機密性。</span><span class="sxs-lookup"><span data-stu-id="fbf14-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="fbf14-125">HTTPS 提供驗證和機密性。</span><span class="sxs-lookup"><span data-stu-id="fbf14-125">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="fbf14-126">SOAP 訊息提供豐富的認證類型。</span><span class="sxs-lookup"><span data-stu-id="fbf14-126">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fbf14-127">子元素</span><span class="sxs-lookup"><span data-stu-id="fbf14-127">Child Elements</span></span>  
  
|<span data-ttu-id="fbf14-128">項目</span><span class="sxs-lookup"><span data-stu-id="fbf14-128">Element</span></span>|<span data-ttu-id="fbf14-129">描述</span><span class="sxs-lookup"><span data-stu-id="fbf14-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fbf14-130">\<transport></span><span class="sxs-lookup"><span data-stu-id="fbf14-130">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-peertransport.md)|<span data-ttu-id="fbf14-131">定義自訂繫結的對等傳輸。</span><span class="sxs-lookup"><span data-stu-id="fbf14-131">Defines a peer transport for a custom binding.</span></span> <span data-ttu-id="fbf14-132">此項目具有 `clientCredentialType` 屬性，可指定與服務互動時所用的認證。</span><span class="sxs-lookup"><span data-stu-id="fbf14-132">This element has a `clientCredentialType` attribute that specifies the credentials to be used when interacting with a service.</span></span> <span data-ttu-id="fbf14-133">此屬性的型別為 <xref:System.ServiceModel.PeerTransportCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="fbf14-133">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span><br /><br /> <span data-ttu-id="fbf14-134">此項目的型別為 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="fbf14-134">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fbf14-135">父項目</span><span class="sxs-lookup"><span data-stu-id="fbf14-135">Parent Elements</span></span>  
  
|<span data-ttu-id="fbf14-136">項目</span><span class="sxs-lookup"><span data-stu-id="fbf14-136">Element</span></span>|<span data-ttu-id="fbf14-137">描述</span><span class="sxs-lookup"><span data-stu-id="fbf14-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fbf14-138">\<peerTransport ></span><span class="sxs-lookup"><span data-stu-id="fbf14-138">\<peerTransport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peertransport.md)|<span data-ttu-id="fbf14-139">定義自訂繫結的對等傳輸。</span><span class="sxs-lookup"><span data-stu-id="fbf14-139">Defines a peer transport for a custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fbf14-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbf14-140">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="fbf14-141">傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="fbf14-141">Transport Security</span></span>](../../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [<span data-ttu-id="fbf14-142">傳輸</span><span class="sxs-lookup"><span data-stu-id="fbf14-142">Transports</span></span>](../../../../../docs/framework/wcf/feature-details/transports.md)  
 [<span data-ttu-id="fbf14-143">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="fbf14-143">Choosing a Transport</span></span>](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 [<span data-ttu-id="fbf14-144">繫結</span><span class="sxs-lookup"><span data-stu-id="fbf14-144">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="fbf14-145">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="fbf14-145">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="fbf14-146">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="fbf14-146">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="fbf14-147">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="fbf14-147">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
