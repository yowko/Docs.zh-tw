---
title: "&lt;netTcpBinding&gt; 的 &lt;security&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
caps.latest.revision: "18"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: bf42da647e598ad698bc36e6abff0d31350f3d96
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="ltsecuritygt-of-ltnettcpbindinggt"></a><span data-ttu-id="41c63-102">&lt;netTcpBinding&gt; 的 &lt;security&gt;</span><span class="sxs-lookup"><span data-stu-id="41c63-102">&lt;security&gt; of &lt;netTcpBinding&gt;</span></span>
<span data-ttu-id="41c63-103">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="41c63-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="41c63-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="41c63-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="41c63-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="41c63-105">\<bindings></span></span>  
<span data-ttu-id="41c63-106">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="41c63-106">\<netTcpBinding></span></span>  
<span data-ttu-id="41c63-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="41c63-107">\<binding></span></span>  
<span data-ttu-id="41c63-108">\<security></span><span class="sxs-lookup"><span data-stu-id="41c63-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41c63-109">語法</span><span class="sxs-lookup"><span data-stu-id="41c63-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41c63-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="41c63-110">Attributes and Elements</span></span>  
 <span data-ttu-id="41c63-111">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="41c63-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41c63-112">屬性</span><span class="sxs-lookup"><span data-stu-id="41c63-112">Attributes</span></span>  
  
|<span data-ttu-id="41c63-113">屬性</span><span class="sxs-lookup"><span data-stu-id="41c63-113">Attribute</span></span>|<span data-ttu-id="41c63-114">描述</span><span class="sxs-lookup"><span data-stu-id="41c63-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="41c63-115">模式</span><span class="sxs-lookup"><span data-stu-id="41c63-115">mode</span></span>|<span data-ttu-id="41c63-116">選擇項。</span><span class="sxs-lookup"><span data-stu-id="41c63-116">Optional.</span></span> <span data-ttu-id="41c63-117">指定套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="41c63-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="41c63-118">有效值如下所示。</span><span class="sxs-lookup"><span data-stu-id="41c63-118">Valid values are shown below.</span></span> <span data-ttu-id="41c63-119">預設值是 `Transport`。</span><span class="sxs-lookup"><span data-stu-id="41c63-119">The default value is `Transport`.</span></span><br /><br /> <span data-ttu-id="41c63-120">此屬性的型別為 <xref:System.ServiceModel.SecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="41c63-120">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="41c63-121">mode 屬性</span><span class="sxs-lookup"><span data-stu-id="41c63-121">mode Attribute</span></span>  
  
|<span data-ttu-id="41c63-122">值</span><span class="sxs-lookup"><span data-stu-id="41c63-122">Value</span></span>|<span data-ttu-id="41c63-123">描述</span><span class="sxs-lookup"><span data-stu-id="41c63-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="41c63-124">無</span><span class="sxs-lookup"><span data-stu-id="41c63-124">None</span></span>|<span data-ttu-id="41c63-125">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="41c63-125">Security is disabled.</span></span>|  
|<span data-ttu-id="41c63-126">Transport</span><span class="sxs-lookup"><span data-stu-id="41c63-126">Transport</span></span>|<span data-ttu-id="41c63-127">使用 TLS over TCP 或 SPNego 來提供傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="41c63-127">Transport security is provided using TLS over TCP or SPNego.</span></span> <span data-ttu-id="41c63-128">服務必須使用 SSL 憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="41c63-128">The service may need to be configured with SSL certificates.</span></span> <span data-ttu-id="41c63-129">可使用這個模式控制保護層級。</span><span class="sxs-lookup"><span data-stu-id="41c63-129">It is possible to control the protection level with this mode.</span></span>|  
|<span data-ttu-id="41c63-130">訊息</span><span class="sxs-lookup"><span data-stu-id="41c63-130">Message</span></span>|<span data-ttu-id="41c63-131">系統會使用 SOAP 訊息安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="41c63-131">Security is provided using SOAP message security.</span></span> <span data-ttu-id="41c63-132">根據預設，SOAP 本文會經過加密與簽署。</span><span class="sxs-lookup"><span data-stu-id="41c63-132">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="41c63-133">這個模式提供各種功能，如超出範圍的用戶端是否可使用服務認證、使用的演算法套件，以及訊息主體要套用何種保護層級。</span><span class="sxs-lookup"><span data-stu-id="41c63-133">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body.</span></span> <span data-ttu-id="41c63-134">每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="41c63-134">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="41c63-135">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="41c63-135">TransportWithMessageCredential</span></span>|<span data-ttu-id="41c63-136">傳輸安全性會與訊息安全性結合在一起。</span><span class="sxs-lookup"><span data-stu-id="41c63-136">Transport security is coupled with message security.</span></span> <span data-ttu-id="41c63-137">傳輸安全性是由 TLS over TCP 或 SPNego 提供，並會確保完整性、機密性和伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="41c63-137">Transport security is provided by TLS over TCP, or SPNego, and ensures integrity, confidentiality, and server authentication.</span></span> <span data-ttu-id="41c63-138">SOAP 訊息安全性提供用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="41c63-138">SOAP message security provides client authentication.</span></span> <span data-ttu-id="41c63-139">根據預設，每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="41c63-139">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="41c63-140">子元素</span><span class="sxs-lookup"><span data-stu-id="41c63-140">Child Elements</span></span>  
  
|<span data-ttu-id="41c63-141">項目</span><span class="sxs-lookup"><span data-stu-id="41c63-141">Element</span></span>|<span data-ttu-id="41c63-142">描述</span><span class="sxs-lookup"><span data-stu-id="41c63-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="41c63-143">\<transport></span><span class="sxs-lookup"><span data-stu-id="41c63-143">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)|<span data-ttu-id="41c63-144">定義傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="41c63-144">Defines the security settings for the transport.</span></span> <span data-ttu-id="41c63-145">此項目的型別為 <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="41c63-145">This element is of type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span></span>|  
|[<span data-ttu-id="41c63-146">\<message></span><span class="sxs-lookup"><span data-stu-id="41c63-146">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)|<span data-ttu-id="41c63-147">定義訊息的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="41c63-147">Defines the security settings for the message.</span></span> <span data-ttu-id="41c63-148">此項目的型別為 <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>。</span><span class="sxs-lookup"><span data-stu-id="41c63-148">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="41c63-149">父項目</span><span class="sxs-lookup"><span data-stu-id="41c63-149">Parent Elements</span></span>  
  
|<span data-ttu-id="41c63-150">項目</span><span class="sxs-lookup"><span data-stu-id="41c63-150">Element</span></span>|<span data-ttu-id="41c63-151">描述</span><span class="sxs-lookup"><span data-stu-id="41c63-151">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="41c63-152">繫結</span><span class="sxs-lookup"><span data-stu-id="41c63-152">binding</span></span>|<span data-ttu-id="41c63-153">繫結項目[ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="41c63-153">The binding element of the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41c63-154">備註</span><span class="sxs-lookup"><span data-stu-id="41c63-154">Remarks</span></span>  
 <span data-ttu-id="41c63-155">每個標準繫結程序提供了控制傳輸安全性需求的參數。</span><span class="sxs-lookup"><span data-stu-id="41c63-155">Each of the standard bindings provides parameters for controlling the transfer security requirements.</span></span> <span data-ttu-id="41c63-156">這些參數通常會包含安全性模式，此模式會指定是否採用訊息層級或傳輸層級安全性，以及選擇用戶端認證型別。</span><span class="sxs-lookup"><span data-stu-id="41c63-156">These parameters typically include the security mode that specified whether message-level or transport-level security is used and the choice of client credential type.</span></span> <span data-ttu-id="41c63-157">根據這些參數所代表的選取選項，會以適當安全性來建構通道堆疊。</span><span class="sxs-lookup"><span data-stu-id="41c63-157">Based on the choice of options these parameters present, a channel stack is constructed with appropriate security.</span></span>  
  
 <span data-ttu-id="41c63-158">由 Windows Communication Foundation (WCF) 提供的系統提供繫結，是設計成符合某些最常見案例需求的一組繫結。</span><span class="sxs-lookup"><span data-stu-id="41c63-158">The system-provided bindings supplied by Windows Communication Foundation (WCF) are a set designed to meet some of the most common scenario requirements.</span></span> <span data-ttu-id="41c63-159">這些每個繫結都允許特定目標案例的安全性需求規格。</span><span class="sxs-lookup"><span data-stu-id="41c63-159">Each of these bindings allows the specification of security requirements for some specific targeted scenarios.</span></span>  
  
 <span data-ttu-id="41c63-160">這個組態項目會提供 `netTcpBinding` 的安全性規格。</span><span class="sxs-lookup"><span data-stu-id="41c63-160">This configuration element provides the security specifications for `netTcpBinding`.</span></span> <span data-ttu-id="41c63-161">這是一個安全、可靠且最佳的繫結，適用於跨電腦通訊。</span><span class="sxs-lookup"><span data-stu-id="41c63-161">This is a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="41c63-162">根據預設，它會產生一個執行階段通訊堆疊，可支援 TCP (供訊息傳遞使用)、Windows 安全性 (供訊息安全性與驗證使用)、WS-ReliableMessaging (提升可靠性) 以及二進位訊息編碼。</span><span class="sxs-lookup"><span data-stu-id="41c63-162">By default it generates a runtime communication stack supporting TCP for message delivery and Windows Security for message security and authentication, WS-ReliableMessaging for reliability, and binary message encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41c63-163">請參閱</span><span class="sxs-lookup"><span data-stu-id="41c63-163">See Also</span></span>  
 <xref:System.ServiceModel.NetTcpSecurity>  
 <xref:System.ServiceModel.NetTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [<span data-ttu-id="41c63-164">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="41c63-164">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="41c63-165">繫結</span><span class="sxs-lookup"><span data-stu-id="41c63-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="41c63-166">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="41c63-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="41c63-167">使用繫結來設定 Windows Communication Foundation 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="41c63-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="41c63-168">\<binding></span><span class="sxs-lookup"><span data-stu-id="41c63-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
