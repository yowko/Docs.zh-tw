---
title: <transport> 的 <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 41f11be9b4ae8f7a7535c9766965de8575cff784
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399300"
---
# <a name="transport-of-nettcpbinding"></a><span data-ttu-id="b9f59-102">\<netTcpBinding> 的 \<transport></span><span class="sxs-lookup"><span data-stu-id="b9f59-102">\<transport> of \<netTcpBinding></span></span>
<span data-ttu-id="b9f59-103">定義使用[ \<netTcpBinding >](nettcpbinding.md)設定之端點的訊息層級安全性需求類型。</span><span class="sxs-lookup"><span data-stu-id="b9f59-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](nettcpbinding.md).</span></span>  
  
<span data-ttu-id="b9f59-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b9f59-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b9f59-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b9f59-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b9f59-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="b9f59-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="b9f59-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netTcpBinding >** ](nettcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="b9f59-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)</span></span>\
<span data-ttu-id="b9f59-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="b9f59-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="b9f59-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-of-nettcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="b9f59-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nettcpbinding.md)</span></span>\
<span data-ttu-id="b9f59-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<傳輸 >**</span><span class="sxs-lookup"><span data-stu-id="b9f59-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9f59-111">語法</span><span class="sxs-lookup"><span data-stu-id="b9f59-111">Syntax</span></span>  
  
```xml  
<netTcpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential">
      <transport clientCredentialType="None|Windows|Certificate"
                 protectionLevel="None|Sign|EncryptAndSign"
                 sslProtocols="Tls|Tls11|Tls12">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</netTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b9f59-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b9f59-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b9f59-113">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="b9f59-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b9f59-114">屬性</span><span class="sxs-lookup"><span data-stu-id="b9f59-114">Attributes</span></span>  
  
|<span data-ttu-id="b9f59-115">屬性</span><span class="sxs-lookup"><span data-stu-id="b9f59-115">Attribute</span></span>|<span data-ttu-id="b9f59-116">描述</span><span class="sxs-lookup"><span data-stu-id="b9f59-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b9f59-117">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="b9f59-117">clientCredentialType</span></span>|<span data-ttu-id="b9f59-118">選擇性。</span><span class="sxs-lookup"><span data-stu-id="b9f59-118">Optional.</span></span> <span data-ttu-id="b9f59-119">指定當使用傳輸安全性執行用戶端驗證時，要使用的認證類型。</span><span class="sxs-lookup"><span data-stu-id="b9f59-119">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="b9f59-120">-預設值是`Windows`。</span><span class="sxs-lookup"><span data-stu-id="b9f59-120">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="b9f59-121">-這個屬性的類型<xref:System.ServiceModel.TcpClientCredentialType>為。</span><span class="sxs-lookup"><span data-stu-id="b9f59-121">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="b9f59-122">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="b9f59-122">protectionLevel</span></span>|<span data-ttu-id="b9f59-123">選擇性。</span><span class="sxs-lookup"><span data-stu-id="b9f59-123">Optional.</span></span> <span data-ttu-id="b9f59-124">定義 TCP 傳輸層級的安全性。</span><span class="sxs-lookup"><span data-stu-id="b9f59-124">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="b9f59-125">簽章訊息可降低訊息在傳輸期間遭第三方竄改的風險。</span><span class="sxs-lookup"><span data-stu-id="b9f59-125">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="b9f59-126">加密會提供傳輸期間的資料層級隱私權。</span><span class="sxs-lookup"><span data-stu-id="b9f59-126">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="b9f59-127">預設值為 `EncryptAndSign`。</span><span class="sxs-lookup"><span data-stu-id="b9f59-127">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="b9f59-128">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="b9f59-128">sslProtocols</span></span>|<span data-ttu-id="b9f59-129">SslProtocols 列舉旗標值，可指定所支援的 SslProtocols。</span><span class="sxs-lookup"><span data-stu-id="b9f59-129">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="b9f59-130">預設值為 [&#124;Tls&#124;Tls11 Tls12]。</span><span class="sxs-lookup"><span data-stu-id="b9f59-130">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="b9f59-131">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="b9f59-131">policyEnforcement</span></span>|<span data-ttu-id="b9f59-132">此列舉指定了應該強制執行 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 的時間。</span><span class="sxs-lookup"><span data-stu-id="b9f59-132">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="b9f59-133">1.Never：絕不強制執行此原則 (延伸保護已停用)。</span><span class="sxs-lookup"><span data-stu-id="b9f59-133">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="b9f59-134">2.WhenSupported：只有當用戶端支援延伸保護時，才強制執行此原則。</span><span class="sxs-lookup"><span data-stu-id="b9f59-134">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="b9f59-135">3.Always：一律強制執行此原則。</span><span class="sxs-lookup"><span data-stu-id="b9f59-135">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="b9f59-136">不支援延伸保護的用戶端將無法驗證。</span><span class="sxs-lookup"><span data-stu-id="b9f59-136">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="b9f59-137">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="b9f59-137">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="b9f59-138">值</span><span class="sxs-lookup"><span data-stu-id="b9f59-138">Value</span></span>|<span data-ttu-id="b9f59-139">描述</span><span class="sxs-lookup"><span data-stu-id="b9f59-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b9f59-140">無</span><span class="sxs-lookup"><span data-stu-id="b9f59-140">None</span></span>|<span data-ttu-id="b9f59-141">用戶端為匿名。</span><span class="sxs-lookup"><span data-stu-id="b9f59-141">The client is anonymous.</span></span> <span data-ttu-id="b9f59-142">這需要服務的憑證。</span><span class="sxs-lookup"><span data-stu-id="b9f59-142">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="b9f59-143">Windows</span><span class="sxs-lookup"><span data-stu-id="b9f59-143">Windows</span></span>|<span data-ttu-id="b9f59-144">使用 SP Negotiation (Kerberos 交涉) 指定用戶端的 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="b9f59-144">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="b9f59-145">憑證</span><span class="sxs-lookup"><span data-stu-id="b9f59-145">Certificate</span></span>|<span data-ttu-id="b9f59-146">用戶端會透過憑證來驗證。</span><span class="sxs-lookup"><span data-stu-id="b9f59-146">The client is authenticated using a certificate.</span></span> <span data-ttu-id="b9f59-147">這會使用 SSL Negotiation，並需要服務的憑證。</span><span class="sxs-lookup"><span data-stu-id="b9f59-147">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="b9f59-148">protectionLevel 屬性</span><span class="sxs-lookup"><span data-stu-id="b9f59-148">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="b9f59-149">值</span><span class="sxs-lookup"><span data-stu-id="b9f59-149">Value</span></span>|<span data-ttu-id="b9f59-150">描述</span><span class="sxs-lookup"><span data-stu-id="b9f59-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b9f59-151">無</span><span class="sxs-lookup"><span data-stu-id="b9f59-151">None</span></span>|<span data-ttu-id="b9f59-152">無保護。</span><span class="sxs-lookup"><span data-stu-id="b9f59-152">No protection.</span></span>|  
|<span data-ttu-id="b9f59-153">Sign</span><span class="sxs-lookup"><span data-stu-id="b9f59-153">Sign</span></span>|<span data-ttu-id="b9f59-154">訊息會經過簽署。</span><span class="sxs-lookup"><span data-stu-id="b9f59-154">Messages are signed.</span></span>|  
|<span data-ttu-id="b9f59-155">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="b9f59-155">EncryptAndSign</span></span>|<span data-ttu-id="b9f59-156">-訊息會經過加密和簽署。</span><span class="sxs-lookup"><span data-stu-id="b9f59-156">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b9f59-157">子元素</span><span class="sxs-lookup"><span data-stu-id="b9f59-157">Child Elements</span></span>  
 <span data-ttu-id="b9f59-158">無</span><span class="sxs-lookup"><span data-stu-id="b9f59-158">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b9f59-159">父項目</span><span class="sxs-lookup"><span data-stu-id="b9f59-159">Parent Elements</span></span>  
  
|<span data-ttu-id="b9f59-160">項目</span><span class="sxs-lookup"><span data-stu-id="b9f59-160">Element</span></span>|<span data-ttu-id="b9f59-161">描述</span><span class="sxs-lookup"><span data-stu-id="b9f59-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b9f59-162">\<security></span><span class="sxs-lookup"><span data-stu-id="b9f59-162">\<security></span></span>](security-of-nettcpbinding.md)|<span data-ttu-id="b9f59-163">指定[ \<netTcpBinding >](nettcpbinding.md)的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="b9f59-163">Specifies the security capabilities of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9f59-164">備註</span><span class="sxs-lookup"><span data-stu-id="b9f59-164">Remarks</span></span>  
 <span data-ttu-id="b9f59-165">使用傳輸安全性來達成 SOAP 訊息的完整性與機密性，以及交互驗證。</span><span class="sxs-lookup"><span data-stu-id="b9f59-165">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="b9f59-166">如果在繫結上選取這個安全性模式，便會使用安全性傳輸設定通道堆疊，並以傳輸安全性 (如 Windows Negotiate 或 SSL over TCP) 保護 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="b9f59-166">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9f59-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9f59-167">See also</span></span>

- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="b9f59-168">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="b9f59-168">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="b9f59-169">繫結</span><span class="sxs-lookup"><span data-stu-id="b9f59-169">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b9f59-170">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="b9f59-170">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b9f59-171">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="b9f59-171">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="b9f59-172">\<binding></span><span class="sxs-lookup"><span data-stu-id="b9f59-172">\<binding></span></span>](../../../misc/binding.md)
