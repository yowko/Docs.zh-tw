---
title: '&lt;netTcpBinding&gt; 的 &lt;security&gt;'
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
author: BrucePerlerMS
ms.openlocfilehash: 8db4fd0a123ac798cae803240b0db98a7057fa97
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48777379"
---
# <a name="ltsecuritygt-of-ltnettcpbindinggt"></a><span data-ttu-id="dd489-102">&lt;netTcpBinding&gt; 的 &lt;security&gt;</span><span class="sxs-lookup"><span data-stu-id="dd489-102">&lt;security&gt; of &lt;netTcpBinding&gt;</span></span>
<span data-ttu-id="dd489-103">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="dd489-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="dd489-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="dd489-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="dd489-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="dd489-105">\<bindings></span></span>  
<span data-ttu-id="dd489-106">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="dd489-106">\<netTcpBinding></span></span>  
<span data-ttu-id="dd489-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="dd489-107">\<binding></span></span>  
<span data-ttu-id="dd489-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="dd489-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd489-109">語法</span><span class="sxs-lookup"><span data-stu-id="dd489-109">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
           protectionLevel="None/Sign/EncryptAndSign" />  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd489-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dd489-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dd489-111">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="dd489-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd489-112">屬性</span><span class="sxs-lookup"><span data-stu-id="dd489-112">Attributes</span></span>  
  
|<span data-ttu-id="dd489-113">屬性</span><span class="sxs-lookup"><span data-stu-id="dd489-113">Attribute</span></span>|<span data-ttu-id="dd489-114">描述</span><span class="sxs-lookup"><span data-stu-id="dd489-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dd489-115">模式</span><span class="sxs-lookup"><span data-stu-id="dd489-115">mode</span></span>|<span data-ttu-id="dd489-116">選擇項。</span><span class="sxs-lookup"><span data-stu-id="dd489-116">Optional.</span></span> <span data-ttu-id="dd489-117">指定套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="dd489-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="dd489-118">有效值如下所示。</span><span class="sxs-lookup"><span data-stu-id="dd489-118">Valid values are shown below.</span></span> <span data-ttu-id="dd489-119">預設值是 `Transport`。</span><span class="sxs-lookup"><span data-stu-id="dd489-119">The default value is `Transport`.</span></span><br /><br /> <span data-ttu-id="dd489-120">此屬性的型別為 <xref:System.ServiceModel.SecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="dd489-120">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="dd489-121">mode 屬性</span><span class="sxs-lookup"><span data-stu-id="dd489-121">mode Attribute</span></span>  
  
|<span data-ttu-id="dd489-122">值</span><span class="sxs-lookup"><span data-stu-id="dd489-122">Value</span></span>|<span data-ttu-id="dd489-123">描述</span><span class="sxs-lookup"><span data-stu-id="dd489-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dd489-124">無</span><span class="sxs-lookup"><span data-stu-id="dd489-124">None</span></span>|<span data-ttu-id="dd489-125">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="dd489-125">Security is disabled.</span></span>|  
|<span data-ttu-id="dd489-126">Transport</span><span class="sxs-lookup"><span data-stu-id="dd489-126">Transport</span></span>|<span data-ttu-id="dd489-127">使用 TLS over TCP 或 SPNego 來提供傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="dd489-127">Transport security is provided using TLS over TCP or SPNego.</span></span> <span data-ttu-id="dd489-128">服務必須使用 SSL 憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="dd489-128">The service may need to be configured with SSL certificates.</span></span> <span data-ttu-id="dd489-129">可使用這個模式控制保護層級。</span><span class="sxs-lookup"><span data-stu-id="dd489-129">It is possible to control the protection level with this mode.</span></span>|  
|<span data-ttu-id="dd489-130">訊息</span><span class="sxs-lookup"><span data-stu-id="dd489-130">Message</span></span>|<span data-ttu-id="dd489-131">系統會使用 SOAP 訊息安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="dd489-131">Security is provided using SOAP message security.</span></span> <span data-ttu-id="dd489-132">根據預設，SOAP 本文會經過加密與簽署。</span><span class="sxs-lookup"><span data-stu-id="dd489-132">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="dd489-133">這個模式提供各種功能，如超出範圍的用戶端是否可使用服務認證、使用的演算法套件，以及訊息主體要套用何種保護層級。</span><span class="sxs-lookup"><span data-stu-id="dd489-133">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body.</span></span> <span data-ttu-id="dd489-134">每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="dd489-134">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="dd489-135">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="dd489-135">TransportWithMessageCredential</span></span>|<span data-ttu-id="dd489-136">傳輸安全性會與訊息安全性結合在一起。</span><span class="sxs-lookup"><span data-stu-id="dd489-136">Transport security is coupled with message security.</span></span> <span data-ttu-id="dd489-137">傳輸安全性是由 TLS over TCP 或 SPNego 提供，並會確保完整性、機密性和伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="dd489-137">Transport security is provided by TLS over TCP, or SPNego, and ensures integrity, confidentiality, and server authentication.</span></span> <span data-ttu-id="dd489-138">SOAP 訊息安全性提供用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="dd489-138">SOAP message security provides client authentication.</span></span> <span data-ttu-id="dd489-139">根據預設，每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="dd489-139">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd489-140">子元素</span><span class="sxs-lookup"><span data-stu-id="dd489-140">Child Elements</span></span>  
  
|<span data-ttu-id="dd489-141">項目</span><span class="sxs-lookup"><span data-stu-id="dd489-141">Element</span></span>|<span data-ttu-id="dd489-142">描述</span><span class="sxs-lookup"><span data-stu-id="dd489-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd489-143">\<transport></span><span class="sxs-lookup"><span data-stu-id="dd489-143">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)|<span data-ttu-id="dd489-144">定義傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="dd489-144">Defines the security settings for the transport.</span></span> <span data-ttu-id="dd489-145">此項目的型別為 <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="dd489-145">This element is of type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span></span>|  
|[<span data-ttu-id="dd489-146">\<message></span><span class="sxs-lookup"><span data-stu-id="dd489-146">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)|<span data-ttu-id="dd489-147">定義訊息的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="dd489-147">Defines the security settings for the message.</span></span> <span data-ttu-id="dd489-148">此項目的型別為 <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>。</span><span class="sxs-lookup"><span data-stu-id="dd489-148">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dd489-149">父項目</span><span class="sxs-lookup"><span data-stu-id="dd489-149">Parent Elements</span></span>  
  
|<span data-ttu-id="dd489-150">項目</span><span class="sxs-lookup"><span data-stu-id="dd489-150">Element</span></span>|<span data-ttu-id="dd489-151">描述</span><span class="sxs-lookup"><span data-stu-id="dd489-151">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dd489-152">繫結</span><span class="sxs-lookup"><span data-stu-id="dd489-152">binding</span></span>|<span data-ttu-id="dd489-153">繫結項目[ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="dd489-153">The binding element of the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd489-154">備註</span><span class="sxs-lookup"><span data-stu-id="dd489-154">Remarks</span></span>  
 <span data-ttu-id="dd489-155">每個標準繫結程序提供了控制傳輸安全性需求的參數。</span><span class="sxs-lookup"><span data-stu-id="dd489-155">Each of the standard bindings provides parameters for controlling the transfer security requirements.</span></span> <span data-ttu-id="dd489-156">這些參數通常會包含安全性模式，此模式會指定是否採用訊息層級或傳輸層級安全性，以及選擇用戶端認證型別。</span><span class="sxs-lookup"><span data-stu-id="dd489-156">These parameters typically include the security mode that specified whether message-level or transport-level security is used and the choice of client credential type.</span></span> <span data-ttu-id="dd489-157">根據這些參數所代表的選取選項，會以適當安全性來建構通道堆疊。</span><span class="sxs-lookup"><span data-stu-id="dd489-157">Based on the choice of options these parameters present, a channel stack is constructed with appropriate security.</span></span>  
  
 <span data-ttu-id="dd489-158">由 Windows Communication Foundation (WCF) 提供的系統提供繫結，是設計成符合某些最常見案例需求的一組繫結。</span><span class="sxs-lookup"><span data-stu-id="dd489-158">The system-provided bindings supplied by Windows Communication Foundation (WCF) are a set designed to meet some of the most common scenario requirements.</span></span> <span data-ttu-id="dd489-159">這些每個繫結都允許特定目標案例的安全性需求規格。</span><span class="sxs-lookup"><span data-stu-id="dd489-159">Each of these bindings allows the specification of security requirements for some specific targeted scenarios.</span></span>  
  
 <span data-ttu-id="dd489-160">這個組態項目會提供 `netTcpBinding` 的安全性規格。</span><span class="sxs-lookup"><span data-stu-id="dd489-160">This configuration element provides the security specifications for `netTcpBinding`.</span></span> <span data-ttu-id="dd489-161">這是一個安全、可靠且最佳的繫結，適用於跨電腦通訊。</span><span class="sxs-lookup"><span data-stu-id="dd489-161">This is a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="dd489-162">根據預設，它會產生一個執行階段通訊堆疊，可支援 TCP (供訊息傳遞使用)、Windows 安全性 (供訊息安全性與驗證使用)、WS-ReliableMessaging (提升可靠性) 以及二進位訊息編碼。</span><span class="sxs-lookup"><span data-stu-id="dd489-162">By default it generates a runtime communication stack supporting TCP for message delivery and Windows Security for message security and authentication, WS-ReliableMessaging for reliability, and binary message encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd489-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd489-163">See Also</span></span>  
 <xref:System.ServiceModel.NetTcpSecurity>  
 <xref:System.ServiceModel.NetTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [<span data-ttu-id="dd489-164">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="dd489-164">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="dd489-165">繫結</span><span class="sxs-lookup"><span data-stu-id="dd489-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="dd489-166">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="dd489-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="dd489-167">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="dd489-167">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="dd489-168">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="dd489-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
