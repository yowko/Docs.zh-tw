---
title: <security> 的 <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
ms.openlocfilehash: 971b1ea979877f631766e438cc41bc0bdabfd346
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399794"
---
# <a name="security-of-nettcpbinding"></a><span data-ttu-id="6eb89-102">\<netTcpBinding > 的\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="6eb89-102">\<security> of \<netTcpBinding></span></span>
<span data-ttu-id="6eb89-103">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="6eb89-103">Defines the security settings for a binding.</span></span>  
  
<span data-ttu-id="6eb89-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6eb89-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6eb89-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="6eb89-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6eb89-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="6eb89-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="6eb89-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netTcpBinding >** ](nettcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="6eb89-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)</span></span>\
<span data-ttu-id="6eb89-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="6eb89-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="6eb89-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<安全性 >**</span><span class="sxs-lookup"><span data-stu-id="6eb89-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eb89-110">語法</span><span class="sxs-lookup"><span data-stu-id="6eb89-110">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             protectionLevel="None/Sign/EncryptAndSign" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6eb89-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6eb89-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6eb89-112">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="6eb89-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6eb89-113">屬性</span><span class="sxs-lookup"><span data-stu-id="6eb89-113">Attributes</span></span>  
  
|<span data-ttu-id="6eb89-114">屬性</span><span class="sxs-lookup"><span data-stu-id="6eb89-114">Attribute</span></span>|<span data-ttu-id="6eb89-115">說明</span><span class="sxs-lookup"><span data-stu-id="6eb89-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6eb89-116">模式</span><span class="sxs-lookup"><span data-stu-id="6eb89-116">mode</span></span>|<span data-ttu-id="6eb89-117">選擇性。</span><span class="sxs-lookup"><span data-stu-id="6eb89-117">Optional.</span></span> <span data-ttu-id="6eb89-118">指定套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="6eb89-118">Specifies the type of security that is applied.</span></span> <span data-ttu-id="6eb89-119">有效值如下所示。</span><span class="sxs-lookup"><span data-stu-id="6eb89-119">Valid values are shown below.</span></span> <span data-ttu-id="6eb89-120">預設值為 `Transport`。</span><span class="sxs-lookup"><span data-stu-id="6eb89-120">The default value is `Transport`.</span></span><br /><br /> <span data-ttu-id="6eb89-121">此屬性的型別為 <xref:System.ServiceModel.SecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="6eb89-121">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="6eb89-122">mode 屬性</span><span class="sxs-lookup"><span data-stu-id="6eb89-122">mode Attribute</span></span>  
  
|<span data-ttu-id="6eb89-123">值</span><span class="sxs-lookup"><span data-stu-id="6eb89-123">Value</span></span>|<span data-ttu-id="6eb89-124">說明</span><span class="sxs-lookup"><span data-stu-id="6eb89-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6eb89-125">None</span><span class="sxs-lookup"><span data-stu-id="6eb89-125">None</span></span>|<span data-ttu-id="6eb89-126">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="6eb89-126">Security is disabled.</span></span>|  
|<span data-ttu-id="6eb89-127">Transport</span><span class="sxs-lookup"><span data-stu-id="6eb89-127">Transport</span></span>|<span data-ttu-id="6eb89-128">使用 TLS over TCP 或 SPNego 來提供傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="6eb89-128">Transport security is provided using TLS over TCP or SPNego.</span></span> <span data-ttu-id="6eb89-129">服務必須使用 SSL 憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="6eb89-129">The service may need to be configured with SSL certificates.</span></span> <span data-ttu-id="6eb89-130">可使用這個模式控制保護層級。</span><span class="sxs-lookup"><span data-stu-id="6eb89-130">It is possible to control the protection level with this mode.</span></span>|  
|<span data-ttu-id="6eb89-131">訊息</span><span class="sxs-lookup"><span data-stu-id="6eb89-131">Message</span></span>|<span data-ttu-id="6eb89-132">系統會使用 SOAP 訊息安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="6eb89-132">Security is provided using SOAP message security.</span></span> <span data-ttu-id="6eb89-133">根據預設，SOAP 本文會經過加密與簽署。</span><span class="sxs-lookup"><span data-stu-id="6eb89-133">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="6eb89-134">這個模式提供各種功能，如超出範圍的用戶端是否可使用服務認證、使用的演算法套件，以及訊息主體要套用何種保護層級。</span><span class="sxs-lookup"><span data-stu-id="6eb89-134">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body.</span></span> <span data-ttu-id="6eb89-135">每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="6eb89-135">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="6eb89-136">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="6eb89-136">TransportWithMessageCredential</span></span>|<span data-ttu-id="6eb89-137">傳輸安全性會與訊息安全性結合在一起。</span><span class="sxs-lookup"><span data-stu-id="6eb89-137">Transport security is coupled with message security.</span></span> <span data-ttu-id="6eb89-138">傳輸安全性是由 TLS over TCP 或 SPNego 提供，並會確保完整性、機密性和伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="6eb89-138">Transport security is provided by TLS over TCP, or SPNego, and ensures integrity, confidentiality, and server authentication.</span></span> <span data-ttu-id="6eb89-139">SOAP 訊息安全性提供用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="6eb89-139">SOAP message security provides client authentication.</span></span> <span data-ttu-id="6eb89-140">根據預設，每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="6eb89-140">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6eb89-141">子元素</span><span class="sxs-lookup"><span data-stu-id="6eb89-141">Child Elements</span></span>  
  
|<span data-ttu-id="6eb89-142">項目</span><span class="sxs-lookup"><span data-stu-id="6eb89-142">Element</span></span>|<span data-ttu-id="6eb89-143">描述</span><span class="sxs-lookup"><span data-stu-id="6eb89-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6eb89-144">\<transport></span><span class="sxs-lookup"><span data-stu-id="6eb89-144">\<transport></span></span>](transport-of-nettcpbinding.md)|<span data-ttu-id="6eb89-145">定義傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="6eb89-145">Defines the security settings for the transport.</span></span> <span data-ttu-id="6eb89-146">此項目的型別為 <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="6eb89-146">This element is of type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span></span>|  
|[<span data-ttu-id="6eb89-147">\<message></span><span class="sxs-lookup"><span data-stu-id="6eb89-147">\<message></span></span>](message-element-of-nettcpbinding.md)|<span data-ttu-id="6eb89-148">定義訊息的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="6eb89-148">Defines the security settings for the message.</span></span> <span data-ttu-id="6eb89-149">此項目的型別為 <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>。</span><span class="sxs-lookup"><span data-stu-id="6eb89-149">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6eb89-150">父項目</span><span class="sxs-lookup"><span data-stu-id="6eb89-150">Parent Elements</span></span>  
  
|<span data-ttu-id="6eb89-151">項目</span><span class="sxs-lookup"><span data-stu-id="6eb89-151">Element</span></span>|<span data-ttu-id="6eb89-152">說明</span><span class="sxs-lookup"><span data-stu-id="6eb89-152">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6eb89-153">繫結</span><span class="sxs-lookup"><span data-stu-id="6eb89-153">binding</span></span>|<span data-ttu-id="6eb89-154">NetTcpBinding > 的 binding 元素。 [ \< ](nettcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="6eb89-154">The binding element of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6eb89-155">備註</span><span class="sxs-lookup"><span data-stu-id="6eb89-155">Remarks</span></span>  
 <span data-ttu-id="6eb89-156">每個標準繫結程序提供了控制傳輸安全性需求的參數。</span><span class="sxs-lookup"><span data-stu-id="6eb89-156">Each of the standard bindings provides parameters for controlling the transfer security requirements.</span></span> <span data-ttu-id="6eb89-157">這些參數通常會包含安全性模式，此模式會指定是否採用訊息層級或傳輸層級安全性，以及選擇用戶端認證型別。</span><span class="sxs-lookup"><span data-stu-id="6eb89-157">These parameters typically include the security mode that specified whether message-level or transport-level security is used and the choice of client credential type.</span></span> <span data-ttu-id="6eb89-158">根據這些參數所代表的選取選項，會以適當安全性來建構通道堆疊。</span><span class="sxs-lookup"><span data-stu-id="6eb89-158">Based on the choice of options these parameters present, a channel stack is constructed with appropriate security.</span></span>  
  
 <span data-ttu-id="6eb89-159">由 Windows Communication Foundation (WCF) 提供的系統提供繫結程序，是設計成符合某些最常見案例需求的一組繫結程序。</span><span class="sxs-lookup"><span data-stu-id="6eb89-159">The system-provided bindings supplied by Windows Communication Foundation (WCF) are a set designed to meet some of the most common scenario requirements.</span></span> <span data-ttu-id="6eb89-160">這些每個繫結程序都允許特定目標案例的安全性需求規格。</span><span class="sxs-lookup"><span data-stu-id="6eb89-160">Each of these bindings allows the specification of security requirements for some specific targeted scenarios.</span></span>  
  
 <span data-ttu-id="6eb89-161">這個組態項目會提供 `netTcpBinding` 的安全性規格。</span><span class="sxs-lookup"><span data-stu-id="6eb89-161">This configuration element provides the security specifications for `netTcpBinding`.</span></span> <span data-ttu-id="6eb89-162">這是一個安全、可靠且最佳的繫結，適用於跨電腦通訊。</span><span class="sxs-lookup"><span data-stu-id="6eb89-162">This is a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="6eb89-163">根據預設，它會產生一個執行階段通訊堆疊，可支援 TCP (供訊息傳遞使用)、Windows 安全性 (供訊息安全性與驗證使用)、WS-ReliableMessaging (提升可靠性) 以及二進位訊息編碼。</span><span class="sxs-lookup"><span data-stu-id="6eb89-163">By default it generates a runtime communication stack supporting TCP for message delivery and Windows Security for message security and authentication, WS-ReliableMessaging for reliability, and binary message encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eb89-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6eb89-164">See also</span></span>

- <xref:System.ServiceModel.NetTcpSecurity>
- <xref:System.ServiceModel.NetTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="6eb89-165">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="6eb89-165">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6eb89-166">繫結</span><span class="sxs-lookup"><span data-stu-id="6eb89-166">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6eb89-167">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="6eb89-167">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6eb89-168">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="6eb89-168">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="6eb89-169">\<binding></span><span class="sxs-lookup"><span data-stu-id="6eb89-169">\<binding></span></span>](../../../misc/binding.md)
