---
title: '&lt;netTcpBinding&gt; 的 &lt;transport&gt;'
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 8416701ce4e787a49ee0a4bdd4829c6592cde94c
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147326"
---
# <a name="lttransportgt-of-ltnettcpbindinggt"></a><span data-ttu-id="a39d0-102">&lt;netTcpBinding&gt; 的 &lt;transport&gt;</span><span class="sxs-lookup"><span data-stu-id="a39d0-102">&lt;transport&gt; of &lt;netTcpBinding&gt;</span></span>
<span data-ttu-id="a39d0-103">定義設定之端點的訊息層級安全性需求的型別[ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="a39d0-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>  
  
 <span data-ttu-id="a39d0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a39d0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a39d0-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="a39d0-105">\<bindings></span></span>  
<span data-ttu-id="a39d0-106">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="a39d0-106">\<netTcpBinding></span></span>  
<span data-ttu-id="a39d0-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="a39d0-107">\<binding></span></span>  
<span data-ttu-id="a39d0-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="a39d0-108">\<security></span></span>  
<span data-ttu-id="a39d0-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="a39d0-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a39d0-110">語法</span><span class="sxs-lookup"><span data-stu-id="a39d0-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a39d0-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a39d0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a39d0-112">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="a39d0-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a39d0-113">屬性</span><span class="sxs-lookup"><span data-stu-id="a39d0-113">Attributes</span></span>  
  
|<span data-ttu-id="a39d0-114">屬性</span><span class="sxs-lookup"><span data-stu-id="a39d0-114">Attribute</span></span>|<span data-ttu-id="a39d0-115">描述</span><span class="sxs-lookup"><span data-stu-id="a39d0-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a39d0-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="a39d0-116">clientCredentialType</span></span>|<span data-ttu-id="a39d0-117">選擇項。</span><span class="sxs-lookup"><span data-stu-id="a39d0-117">Optional.</span></span> <span data-ttu-id="a39d0-118">指定當使用傳輸安全性執行用戶端驗證時，要使用的認證類型。</span><span class="sxs-lookup"><span data-stu-id="a39d0-118">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="a39d0-119">-預設值是`Windows`。</span><span class="sxs-lookup"><span data-stu-id="a39d0-119">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="a39d0-120">-此屬性為類型<xref:System.ServiceModel.TcpClientCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="a39d0-120">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="a39d0-121">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="a39d0-121">protectionLevel</span></span>|<span data-ttu-id="a39d0-122">選擇項。</span><span class="sxs-lookup"><span data-stu-id="a39d0-122">Optional.</span></span> <span data-ttu-id="a39d0-123">定義 TCP 傳輸層級的安全性。</span><span class="sxs-lookup"><span data-stu-id="a39d0-123">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="a39d0-124">簽章訊息可降低訊息在傳輸期間遭第三方竄改的風險。</span><span class="sxs-lookup"><span data-stu-id="a39d0-124">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="a39d0-125">加密會提供傳輸期間的資料層級隱私權。</span><span class="sxs-lookup"><span data-stu-id="a39d0-125">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="a39d0-126">預設值為 `EncryptAndSign`。</span><span class="sxs-lookup"><span data-stu-id="a39d0-126">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="a39d0-127">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="a39d0-127">sslProtocols</span></span>|<span data-ttu-id="a39d0-128">SslProtocols 列舉旗標值，可指定所支援的 SslProtocols。</span><span class="sxs-lookup"><span data-stu-id="a39d0-128">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="a39d0-129">預設值是 Tls&#124;Tls11&#124;Tls12。</span><span class="sxs-lookup"><span data-stu-id="a39d0-129">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="a39d0-130">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="a39d0-130">policyEnforcement</span></span>|<span data-ttu-id="a39d0-131">此列舉指定了應該強制執行 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 的時間。</span><span class="sxs-lookup"><span data-stu-id="a39d0-131">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="a39d0-132">1.Never：絕不強制執行此原則 (延伸保護已停用)。</span><span class="sxs-lookup"><span data-stu-id="a39d0-132">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="a39d0-133">2.WhenSupported：只有當用戶端支援延伸保護時，才強制執行此原則。</span><span class="sxs-lookup"><span data-stu-id="a39d0-133">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="a39d0-134">3.Always：一律強制執行此原則。</span><span class="sxs-lookup"><span data-stu-id="a39d0-134">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="a39d0-135">不支援延伸保護的用戶端將無法驗證。</span><span class="sxs-lookup"><span data-stu-id="a39d0-135">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="a39d0-136">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="a39d0-136">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="a39d0-137">值</span><span class="sxs-lookup"><span data-stu-id="a39d0-137">Value</span></span>|<span data-ttu-id="a39d0-138">描述</span><span class="sxs-lookup"><span data-stu-id="a39d0-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a39d0-139">無</span><span class="sxs-lookup"><span data-stu-id="a39d0-139">None</span></span>|<span data-ttu-id="a39d0-140">用戶端為匿名。</span><span class="sxs-lookup"><span data-stu-id="a39d0-140">The client is anonymous.</span></span> <span data-ttu-id="a39d0-141">這需要服務的憑證。</span><span class="sxs-lookup"><span data-stu-id="a39d0-141">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="a39d0-142">Windows</span><span class="sxs-lookup"><span data-stu-id="a39d0-142">Windows</span></span>|<span data-ttu-id="a39d0-143">使用 SP Negotiation (Kerberos 交涉) 指定用戶端的 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="a39d0-143">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="a39d0-144">憑證</span><span class="sxs-lookup"><span data-stu-id="a39d0-144">Certificate</span></span>|<span data-ttu-id="a39d0-145">用戶端會透過憑證來驗證。</span><span class="sxs-lookup"><span data-stu-id="a39d0-145">The client is authenticated using a certificate.</span></span> <span data-ttu-id="a39d0-146">這會使用 SSL Negotiation，並需要服務的憑證。</span><span class="sxs-lookup"><span data-stu-id="a39d0-146">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="a39d0-147">protectionLevel 屬性</span><span class="sxs-lookup"><span data-stu-id="a39d0-147">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="a39d0-148">值</span><span class="sxs-lookup"><span data-stu-id="a39d0-148">Value</span></span>|<span data-ttu-id="a39d0-149">描述</span><span class="sxs-lookup"><span data-stu-id="a39d0-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a39d0-150">無</span><span class="sxs-lookup"><span data-stu-id="a39d0-150">None</span></span>|<span data-ttu-id="a39d0-151">無保護。</span><span class="sxs-lookup"><span data-stu-id="a39d0-151">No protection.</span></span>|  
|<span data-ttu-id="a39d0-152">Sign</span><span class="sxs-lookup"><span data-stu-id="a39d0-152">Sign</span></span>|<span data-ttu-id="a39d0-153">訊息會經過簽署。</span><span class="sxs-lookup"><span data-stu-id="a39d0-153">Messages are signed.</span></span>|  
|<span data-ttu-id="a39d0-154">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="a39d0-154">EncryptAndSign</span></span>|<span data-ttu-id="a39d0-155">-訊息會經過加密及簽署。</span><span class="sxs-lookup"><span data-stu-id="a39d0-155">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a39d0-156">子元素</span><span class="sxs-lookup"><span data-stu-id="a39d0-156">Child Elements</span></span>  
 <span data-ttu-id="a39d0-157">無</span><span class="sxs-lookup"><span data-stu-id="a39d0-157">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a39d0-158">父項目</span><span class="sxs-lookup"><span data-stu-id="a39d0-158">Parent Elements</span></span>  
  
|<span data-ttu-id="a39d0-159">項目</span><span class="sxs-lookup"><span data-stu-id="a39d0-159">Element</span></span>|<span data-ttu-id="a39d0-160">描述</span><span class="sxs-lookup"><span data-stu-id="a39d0-160">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a39d0-161">\<security></span><span class="sxs-lookup"><span data-stu-id="a39d0-161">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|<span data-ttu-id="a39d0-162">指定的安全性功能[ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="a39d0-162">Specifies the security capabilities of the [\<netTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a39d0-163">備註</span><span class="sxs-lookup"><span data-stu-id="a39d0-163">Remarks</span></span>  
 <span data-ttu-id="a39d0-164">使用傳輸安全性來達成 SOAP 訊息的完整性與機密性，以及交互驗證。</span><span class="sxs-lookup"><span data-stu-id="a39d0-164">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="a39d0-165">如果在繫結上選取這個安全性模式，便會使用安全性傳輸設定通道堆疊，並以傳輸安全性 (如 Windows Negotiate 或 SSL over TCP) 保護 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="a39d0-165">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a39d0-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a39d0-166">See Also</span></span>  
 <xref:System.ServiceModel.TcpTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>  
 [<span data-ttu-id="a39d0-167">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="a39d0-167">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="a39d0-168">繫結</span><span class="sxs-lookup"><span data-stu-id="a39d0-168">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="a39d0-169">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="a39d0-169">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="a39d0-170">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="a39d0-170">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="a39d0-171">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="a39d0-171">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
