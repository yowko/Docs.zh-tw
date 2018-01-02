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
ms.openlocfilehash: 08e9f1f3b2145d94f491933639211a6eabd3c9fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-of-ltnettcpbindinggt"></a><span data-ttu-id="368bf-102">&lt;netTcpBinding&gt; 的 &lt;security&gt;</span><span class="sxs-lookup"><span data-stu-id="368bf-102">&lt;security&gt; of &lt;netTcpBinding&gt;</span></span>
<span data-ttu-id="368bf-103">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="368bf-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="368bf-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="368bf-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="368bf-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="368bf-105">\<bindings></span></span>  
<span data-ttu-id="368bf-106">\<netTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="368bf-106">\<netTcpBinding></span></span>  
<span data-ttu-id="368bf-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="368bf-107">\<binding></span></span>  
<span data-ttu-id="368bf-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="368bf-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="368bf-109">語法</span><span class="sxs-lookup"><span data-stu-id="368bf-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="368bf-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="368bf-110">Attributes and Elements</span></span>  
 <span data-ttu-id="368bf-111">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="368bf-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="368bf-112">屬性</span><span class="sxs-lookup"><span data-stu-id="368bf-112">Attributes</span></span>  
  
|<span data-ttu-id="368bf-113">屬性</span><span class="sxs-lookup"><span data-stu-id="368bf-113">Attribute</span></span>|<span data-ttu-id="368bf-114">描述</span><span class="sxs-lookup"><span data-stu-id="368bf-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="368bf-115">模式</span><span class="sxs-lookup"><span data-stu-id="368bf-115">mode</span></span>|<span data-ttu-id="368bf-116">選擇項。</span><span class="sxs-lookup"><span data-stu-id="368bf-116">Optional.</span></span> <span data-ttu-id="368bf-117">指定套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="368bf-117">Specifies the type of security that is applied.</span></span> <span data-ttu-id="368bf-118">有效值如下所示。</span><span class="sxs-lookup"><span data-stu-id="368bf-118">Valid values are shown below.</span></span> <span data-ttu-id="368bf-119">預設值是 `Transport`。</span><span class="sxs-lookup"><span data-stu-id="368bf-119">The default value is `Transport`.</span></span><br /><br /> <span data-ttu-id="368bf-120">此屬性的型別為 <xref:System.ServiceModel.SecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="368bf-120">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="368bf-121">mode 屬性</span><span class="sxs-lookup"><span data-stu-id="368bf-121">mode Attribute</span></span>  
  
|<span data-ttu-id="368bf-122">值</span><span class="sxs-lookup"><span data-stu-id="368bf-122">Value</span></span>|<span data-ttu-id="368bf-123">描述</span><span class="sxs-lookup"><span data-stu-id="368bf-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="368bf-124">無</span><span class="sxs-lookup"><span data-stu-id="368bf-124">None</span></span>|<span data-ttu-id="368bf-125">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="368bf-125">Security is disabled.</span></span>|  
|<span data-ttu-id="368bf-126">Transport</span><span class="sxs-lookup"><span data-stu-id="368bf-126">Transport</span></span>|<span data-ttu-id="368bf-127">使用 TLS over TCP 或 SPNego 來提供傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="368bf-127">Transport security is provided using TLS over TCP or SPNego.</span></span> <span data-ttu-id="368bf-128">服務必須使用 SSL 憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="368bf-128">The service may need to be configured with SSL certificates.</span></span> <span data-ttu-id="368bf-129">可使用這個模式控制保護層級。</span><span class="sxs-lookup"><span data-stu-id="368bf-129">It is possible to control the protection level with this mode.</span></span>|  
|<span data-ttu-id="368bf-130">訊息</span><span class="sxs-lookup"><span data-stu-id="368bf-130">Message</span></span>|<span data-ttu-id="368bf-131">系統會使用 SOAP 訊息安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="368bf-131">Security is provided using SOAP message security.</span></span> <span data-ttu-id="368bf-132">根據預設，SOAP 本文會經過加密與簽署。</span><span class="sxs-lookup"><span data-stu-id="368bf-132">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="368bf-133">這個模式提供各種功能，如超出範圍的用戶端是否可使用服務認證、使用的演算法套件，以及訊息主體要套用何種保護層級。</span><span class="sxs-lookup"><span data-stu-id="368bf-133">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body.</span></span> <span data-ttu-id="368bf-134">每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="368bf-134">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="368bf-135">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="368bf-135">TransportWithMessageCredential</span></span>|<span data-ttu-id="368bf-136">傳輸安全性會與訊息安全性結合在一起。</span><span class="sxs-lookup"><span data-stu-id="368bf-136">Transport security is coupled with message security.</span></span> <span data-ttu-id="368bf-137">傳輸安全性是由 TLS over TCP 或 SPNego 提供，並會確保完整性、機密性和伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="368bf-137">Transport security is provided by TLS over TCP, or SPNego, and ensures integrity, confidentiality, and server authentication.</span></span> <span data-ttu-id="368bf-138">SOAP 訊息安全性提供用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="368bf-138">SOAP message security provides client authentication.</span></span> <span data-ttu-id="368bf-139">根據預設，每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="368bf-139">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="368bf-140">子元素</span><span class="sxs-lookup"><span data-stu-id="368bf-140">Child Elements</span></span>  
  
|<span data-ttu-id="368bf-141">項目</span><span class="sxs-lookup"><span data-stu-id="368bf-141">Element</span></span>|<span data-ttu-id="368bf-142">描述</span><span class="sxs-lookup"><span data-stu-id="368bf-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="368bf-143">\<傳輸 ></span><span class="sxs-lookup"><span data-stu-id="368bf-143">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)|<span data-ttu-id="368bf-144">定義傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="368bf-144">Defines the security settings for the transport.</span></span> <span data-ttu-id="368bf-145">此項目的型別為 <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="368bf-145">This element is of type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span></span>|  
|[<span data-ttu-id="368bf-146">\<訊息 ></span><span class="sxs-lookup"><span data-stu-id="368bf-146">\<message></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)|<span data-ttu-id="368bf-147">定義訊息的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="368bf-147">Defines the security settings for the message.</span></span> <span data-ttu-id="368bf-148">此項目的型別為 <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>。</span><span class="sxs-lookup"><span data-stu-id="368bf-148">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="368bf-149">父項目</span><span class="sxs-lookup"><span data-stu-id="368bf-149">Parent Elements</span></span>  
  
|<span data-ttu-id="368bf-150">項目</span><span class="sxs-lookup"><span data-stu-id="368bf-150">Element</span></span>|<span data-ttu-id="368bf-151">描述</span><span class="sxs-lookup"><span data-stu-id="368bf-151">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="368bf-152">繫結</span><span class="sxs-lookup"><span data-stu-id="368bf-152">binding</span></span>|<span data-ttu-id="368bf-153">繫結項目[ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="368bf-153">The binding element of the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="368bf-154">備註</span><span class="sxs-lookup"><span data-stu-id="368bf-154">Remarks</span></span>  
 <span data-ttu-id="368bf-155">每個標準繫結程序提供了控制傳輸安全性需求的參數。</span><span class="sxs-lookup"><span data-stu-id="368bf-155">Each of the standard bindings provides parameters for controlling the transfer security requirements.</span></span> <span data-ttu-id="368bf-156">這些參數通常會包含安全性模式，此模式會指定是否採用訊息層級或傳輸層級安全性，以及選擇用戶端認證型別。</span><span class="sxs-lookup"><span data-stu-id="368bf-156">These parameters typically include the security mode that specified whether message-level or transport-level security is used and the choice of client credential type.</span></span> <span data-ttu-id="368bf-157">根據這些參數所代表的選取選項，會以適當安全性來建構通道堆疊。</span><span class="sxs-lookup"><span data-stu-id="368bf-157">Based on the choice of options these parameters present, a channel stack is constructed with appropriate security.</span></span>  
  
 <span data-ttu-id="368bf-158">由 Windows Communication Foundation (WCF) 提供的系統提供繫結，是設計成符合某些最常見案例需求的一組繫結。</span><span class="sxs-lookup"><span data-stu-id="368bf-158">The system-provided bindings supplied by Windows Communication Foundation (WCF) are a set designed to meet some of the most common scenario requirements.</span></span> <span data-ttu-id="368bf-159">這些每個繫結都允許特定目標案例的安全性需求規格。</span><span class="sxs-lookup"><span data-stu-id="368bf-159">Each of these bindings allows the specification of security requirements for some specific targeted scenarios.</span></span>  
  
 <span data-ttu-id="368bf-160">這個組態項目會提供 `netTcpBinding` 的安全性規格。</span><span class="sxs-lookup"><span data-stu-id="368bf-160">This configuration element provides the security specifications for `netTcpBinding`.</span></span> <span data-ttu-id="368bf-161">這是一個安全、可靠且最佳的繫結，適用於跨電腦通訊。</span><span class="sxs-lookup"><span data-stu-id="368bf-161">This is a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="368bf-162">根據預設，它會產生一個執行階段通訊堆疊，可支援 TCP (供訊息傳遞使用)、Windows 安全性 (供訊息安全性與驗證使用)、WS-ReliableMessaging (提升可靠性) 以及二進位訊息編碼。</span><span class="sxs-lookup"><span data-stu-id="368bf-162">By default it generates a runtime communication stack supporting TCP for message delivery and Windows Security for message security and authentication, WS-ReliableMessaging for reliability, and binary message encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="368bf-163">請參閱</span><span class="sxs-lookup"><span data-stu-id="368bf-163">See Also</span></span>  
 <xref:System.ServiceModel.NetTcpSecurity>  
 <xref:System.ServiceModel.NetTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [<span data-ttu-id="368bf-164">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="368bf-164">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="368bf-165">繫結</span><span class="sxs-lookup"><span data-stu-id="368bf-165">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="368bf-166">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="368bf-166">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="368bf-167">使用繫結來設定 Windows Communication Foundation 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="368bf-167">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="368bf-168">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="368bf-168">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
