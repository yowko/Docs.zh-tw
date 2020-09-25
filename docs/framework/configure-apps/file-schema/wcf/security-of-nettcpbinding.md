---
title: <security> 的 <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
ms.openlocfilehash: d39e3e5e655817aa91c5301274a860a00a6ab7ef
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91169982"
---
# <a name="security-of-nettcpbinding"></a><span data-ttu-id="373c8-102">\<security> 的 \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="373c8-102">\<security> of \<netTcpBinding></span></span>

<span data-ttu-id="373c8-103">定義繫結的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="373c8-103">Defines the security settings for a binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="373c8-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="373c8-104">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             protectionLevel="None/Sign/EncryptAndSign" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="373c8-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="373c8-105">Attributes and Elements</span></span>  

 <span data-ttu-id="373c8-106">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="373c8-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="373c8-107">屬性</span><span class="sxs-lookup"><span data-stu-id="373c8-107">Attributes</span></span>  
  
|<span data-ttu-id="373c8-108">屬性</span><span class="sxs-lookup"><span data-stu-id="373c8-108">Attribute</span></span>|<span data-ttu-id="373c8-109">描述</span><span class="sxs-lookup"><span data-stu-id="373c8-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="373c8-110">mode</span><span class="sxs-lookup"><span data-stu-id="373c8-110">mode</span></span>|<span data-ttu-id="373c8-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="373c8-111">Optional.</span></span> <span data-ttu-id="373c8-112">指定套用的安全性類型。</span><span class="sxs-lookup"><span data-stu-id="373c8-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="373c8-113">有效值如下所示。</span><span class="sxs-lookup"><span data-stu-id="373c8-113">Valid values are shown below.</span></span> <span data-ttu-id="373c8-114">預設值是 `Transport`。</span><span class="sxs-lookup"><span data-stu-id="373c8-114">The default value is `Transport`.</span></span><br /><br /> <span data-ttu-id="373c8-115">此屬性的型別為 <xref:System.ServiceModel.SecurityMode>。</span><span class="sxs-lookup"><span data-stu-id="373c8-115">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="373c8-116">mode 屬性</span><span class="sxs-lookup"><span data-stu-id="373c8-116">mode Attribute</span></span>  
  
|<span data-ttu-id="373c8-117">值</span><span class="sxs-lookup"><span data-stu-id="373c8-117">Value</span></span>|<span data-ttu-id="373c8-118">描述</span><span class="sxs-lookup"><span data-stu-id="373c8-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="373c8-119">無</span><span class="sxs-lookup"><span data-stu-id="373c8-119">None</span></span>|<span data-ttu-id="373c8-120">停用安全性。</span><span class="sxs-lookup"><span data-stu-id="373c8-120">Security is disabled.</span></span>|  
|<span data-ttu-id="373c8-121">傳輸</span><span class="sxs-lookup"><span data-stu-id="373c8-121">Transport</span></span>|<span data-ttu-id="373c8-122">使用 TLS over TCP 或 SPNego 來提供傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="373c8-122">Transport security is provided using TLS over TCP or SPNego.</span></span> <span data-ttu-id="373c8-123">服務必須使用 SSL 憑證來設定。</span><span class="sxs-lookup"><span data-stu-id="373c8-123">The service may need to be configured with SSL certificates.</span></span> <span data-ttu-id="373c8-124">您可以使用此模式來控制保護等級。</span><span class="sxs-lookup"><span data-stu-id="373c8-124">It is possible to control the protection level with this mode.</span></span>|  
|<span data-ttu-id="373c8-125">訊息</span><span class="sxs-lookup"><span data-stu-id="373c8-125">Message</span></span>|<span data-ttu-id="373c8-126">系統會使用 SOAP 訊息安全性來提供安全性。</span><span class="sxs-lookup"><span data-stu-id="373c8-126">Security is provided using SOAP message security.</span></span> <span data-ttu-id="373c8-127">根據預設，SOAP 本文會經過加密與簽署。</span><span class="sxs-lookup"><span data-stu-id="373c8-127">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="373c8-128">這個模式提供各種功能，如超出範圍的用戶端是否可使用服務認證、使用的演算法套件，以及訊息主體要套用何種保護層級。</span><span class="sxs-lookup"><span data-stu-id="373c8-128">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body.</span></span> <span data-ttu-id="373c8-129">每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="373c8-129">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="373c8-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="373c8-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="373c8-131">傳輸安全性會與訊息安全性結合在一起。</span><span class="sxs-lookup"><span data-stu-id="373c8-131">Transport security is coupled with message security.</span></span> <span data-ttu-id="373c8-132">傳輸安全性是由 TLS over TCP 或 SPNego 提供，並會確保完整性、機密性和伺服器驗證。</span><span class="sxs-lookup"><span data-stu-id="373c8-132">Transport security is provided by TLS over TCP, or SPNego, and ensures integrity, confidentiality, and server authentication.</span></span> <span data-ttu-id="373c8-133">SOAP 訊息安全性提供用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="373c8-133">SOAP message security provides client authentication.</span></span> <span data-ttu-id="373c8-134">根據預設，每個工作階段會執行一次用戶端驗證，並會快取工作階段期間的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="373c8-134">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="373c8-135">子元素</span><span class="sxs-lookup"><span data-stu-id="373c8-135">Child Elements</span></span>  
  
|<span data-ttu-id="373c8-136">項目</span><span class="sxs-lookup"><span data-stu-id="373c8-136">Element</span></span>|<span data-ttu-id="373c8-137">描述</span><span class="sxs-lookup"><span data-stu-id="373c8-137">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-nettcpbinding.md)|<span data-ttu-id="373c8-138">定義傳輸的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="373c8-138">Defines the security settings for the transport.</span></span> <span data-ttu-id="373c8-139">此項目的型別為 <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>。</span><span class="sxs-lookup"><span data-stu-id="373c8-139">This element is of type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span></span>|  
|[\<message>](message-element-of-nettcpbinding.md)|<span data-ttu-id="373c8-140">定義訊息的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="373c8-140">Defines the security settings for the message.</span></span> <span data-ttu-id="373c8-141">此項目的型別為 <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>。</span><span class="sxs-lookup"><span data-stu-id="373c8-141">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="373c8-142">父項目</span><span class="sxs-lookup"><span data-stu-id="373c8-142">Parent Elements</span></span>  
  
|<span data-ttu-id="373c8-143">項目</span><span class="sxs-lookup"><span data-stu-id="373c8-143">Element</span></span>|<span data-ttu-id="373c8-144">描述</span><span class="sxs-lookup"><span data-stu-id="373c8-144">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="373c8-145">繫結</span><span class="sxs-lookup"><span data-stu-id="373c8-145">binding</span></span>|<span data-ttu-id="373c8-146">的繫結項目 [\<netTcpBinding>](nettcpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="373c8-146">The binding element of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="373c8-147">備註</span><span class="sxs-lookup"><span data-stu-id="373c8-147">Remarks</span></span>  

 <span data-ttu-id="373c8-148">每個標準繫結程序提供了控制傳輸安全性需求的參數。</span><span class="sxs-lookup"><span data-stu-id="373c8-148">Each of the standard bindings provides parameters for controlling the transfer security requirements.</span></span> <span data-ttu-id="373c8-149">這些參數通常會包含安全性模式，此模式會指定是否採用訊息層級或傳輸層級安全性，以及選擇用戶端認證型別。</span><span class="sxs-lookup"><span data-stu-id="373c8-149">These parameters typically include the security mode that specified whether message-level or transport-level security is used and the choice of client credential type.</span></span> <span data-ttu-id="373c8-150">根據這些參數所代表的選取選項，會以適當安全性來建構通道堆疊。</span><span class="sxs-lookup"><span data-stu-id="373c8-150">Based on the choice of options these parameters present, a channel stack is constructed with appropriate security.</span></span>  
  
 <span data-ttu-id="373c8-151">由 Windows Communication Foundation (WCF) 提供的系統提供繫結程序，是設計成符合某些最常見案例需求的一組繫結程序。</span><span class="sxs-lookup"><span data-stu-id="373c8-151">The system-provided bindings supplied by Windows Communication Foundation (WCF) are a set designed to meet some of the most common scenario requirements.</span></span> <span data-ttu-id="373c8-152">這些每個繫結程序都允許特定目標案例的安全性需求規格。</span><span class="sxs-lookup"><span data-stu-id="373c8-152">Each of these bindings allows the specification of security requirements for some specific targeted scenarios.</span></span>  
  
 <span data-ttu-id="373c8-153">這個組態項目會提供 `netTcpBinding` 的安全性規格。</span><span class="sxs-lookup"><span data-stu-id="373c8-153">This configuration element provides the security specifications for `netTcpBinding`.</span></span> <span data-ttu-id="373c8-154">這是一個安全、可靠且最佳的繫結，適用於跨電腦通訊。</span><span class="sxs-lookup"><span data-stu-id="373c8-154">This is a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="373c8-155">根據預設，它會產生一個執行階段通訊堆疊，可支援 TCP (供訊息傳遞使用)、Windows 安全性 (供訊息安全性與驗證使用)、WS-ReliableMessaging (提升可靠性) 以及二進位訊息編碼。</span><span class="sxs-lookup"><span data-stu-id="373c8-155">By default it generates a runtime communication stack supporting TCP for message delivery and Windows Security for message security and authentication, WS-ReliableMessaging for reliability, and binary message encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="373c8-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="373c8-156">See also</span></span>

- <xref:System.ServiceModel.NetTcpSecurity>
- <xref:System.ServiceModel.NetTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="373c8-157">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="373c8-157">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="373c8-158">繫結</span><span class="sxs-lookup"><span data-stu-id="373c8-158">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="373c8-159">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="373c8-159">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="373c8-160">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="373c8-160">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
