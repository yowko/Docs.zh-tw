---
title: <transport> 的 <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 49462e0a-66e1-463f-b3e1-c83a441673c6
ms.openlocfilehash: 4ef08ad73a03dea21d27217364a7bacb46a3848e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73735928"
---
# <a name="transport-of-nettcpbinding"></a><span data-ttu-id="4f28a-102">\<transport> 的 \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="4f28a-102">\<transport> of \<netTcpBinding></span></span>
<span data-ttu-id="4f28a-103">定義以設定之端點的訊息層級安全性需求類型 [\<netTcpBinding>](nettcpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="4f28a-103">Defines the type of message-level security requirements for an endpoint configured with the [\<netTcpBinding>](nettcpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="4f28a-104">語法</span><span class="sxs-lookup"><span data-stu-id="4f28a-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f28a-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4f28a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="4f28a-106">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="4f28a-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f28a-107">屬性</span><span class="sxs-lookup"><span data-stu-id="4f28a-107">Attributes</span></span>  
  
|<span data-ttu-id="4f28a-108">屬性</span><span class="sxs-lookup"><span data-stu-id="4f28a-108">Attribute</span></span>|<span data-ttu-id="4f28a-109">描述</span><span class="sxs-lookup"><span data-stu-id="4f28a-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4f28a-110">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="4f28a-110">clientCredentialType</span></span>|<span data-ttu-id="4f28a-111">選擇性。</span><span class="sxs-lookup"><span data-stu-id="4f28a-111">Optional.</span></span> <span data-ttu-id="4f28a-112">指定當使用傳輸安全性執行用戶端驗證時，要使用的認證類型。</span><span class="sxs-lookup"><span data-stu-id="4f28a-112">Specifies the type of credential to be used when performing client authentication using Transport security.</span></span><br /><br /> <span data-ttu-id="4f28a-113">-預設值是 `Windows` 。</span><span class="sxs-lookup"><span data-stu-id="4f28a-113">-   The default value is `Windows`.</span></span><br /><span data-ttu-id="4f28a-114">-這個屬性的類型為 <xref:System.ServiceModel.TcpClientCredentialType> 。</span><span class="sxs-lookup"><span data-stu-id="4f28a-114">-   This attribute is of type <xref:System.ServiceModel.TcpClientCredentialType>.</span></span>|  
|<span data-ttu-id="4f28a-115">protectionLevel</span><span class="sxs-lookup"><span data-stu-id="4f28a-115">protectionLevel</span></span>|<span data-ttu-id="4f28a-116">選擇性。</span><span class="sxs-lookup"><span data-stu-id="4f28a-116">Optional.</span></span> <span data-ttu-id="4f28a-117">定義 TCP 傳輸層級的安全性。</span><span class="sxs-lookup"><span data-stu-id="4f28a-117">Defines security at the level of the TCP transport.</span></span> <span data-ttu-id="4f28a-118">簽署訊息可以降低訊息在傳輸時遭到第三者竄改的風險。</span><span class="sxs-lookup"><span data-stu-id="4f28a-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="4f28a-119">加密可在傳輸時提供資料等級的隱私權。</span><span class="sxs-lookup"><span data-stu-id="4f28a-119">Encryption provides data-level privacy during transport.</span></span><br /><br /> <span data-ttu-id="4f28a-120">預設值是 `EncryptAndSign`。</span><span class="sxs-lookup"><span data-stu-id="4f28a-120">The default value is `EncryptAndSign`.</span></span>|  
|<span data-ttu-id="4f28a-121">sslProtocols</span><span class="sxs-lookup"><span data-stu-id="4f28a-121">sslProtocols</span></span>|<span data-ttu-id="4f28a-122">SslProtocols 列舉旗標值，可指定所支援的 SslProtocols。</span><span class="sxs-lookup"><span data-stu-id="4f28a-122">A SslProtocols enum flag value that specifies which SslProtocols are supported.</span></span> <span data-ttu-id="4f28a-123">預設值為 [Tls&#124;Tls11&#124;Tls12]。</span><span class="sxs-lookup"><span data-stu-id="4f28a-123">The default is Tls&#124;Tls11&#124;Tls12.</span></span>|  
|<span data-ttu-id="4f28a-124">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="4f28a-124">policyEnforcement</span></span>|<span data-ttu-id="4f28a-125">此列舉指定了應該強制執行 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 的時間。</span><span class="sxs-lookup"><span data-stu-id="4f28a-125">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="4f28a-126">1. 永不–永遠不會強制執行原則（已停用 [擴充保護]）。</span><span class="sxs-lookup"><span data-stu-id="4f28a-126">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="4f28a-127">2. WhenSupported-只有在用戶端支援擴充保護時，才會強制執行原則。</span><span class="sxs-lookup"><span data-stu-id="4f28a-127">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="4f28a-128">3. always –一律強制執行原則。</span><span class="sxs-lookup"><span data-stu-id="4f28a-128">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="4f28a-129">不支援延伸保護的用戶端將無法驗證。</span><span class="sxs-lookup"><span data-stu-id="4f28a-129">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="4f28a-130">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="4f28a-130">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="4f28a-131">值</span><span class="sxs-lookup"><span data-stu-id="4f28a-131">Value</span></span>|<span data-ttu-id="4f28a-132">描述</span><span class="sxs-lookup"><span data-stu-id="4f28a-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4f28a-133">None</span><span class="sxs-lookup"><span data-stu-id="4f28a-133">None</span></span>|<span data-ttu-id="4f28a-134">用戶端為匿名。</span><span class="sxs-lookup"><span data-stu-id="4f28a-134">The client is anonymous.</span></span> <span data-ttu-id="4f28a-135">這需要服務的憑證。</span><span class="sxs-lookup"><span data-stu-id="4f28a-135">This requires a certificate for the service.</span></span>|  
|<span data-ttu-id="4f28a-136">Windows</span><span class="sxs-lookup"><span data-stu-id="4f28a-136">Windows</span></span>|<span data-ttu-id="4f28a-137">使用 SP Negotiation (Kerberos 交涉) 指定用戶端的 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="4f28a-137">Specifies Windows authentication of the client using SP Negotiation (Kerberos negotiation).</span></span>|  
|<span data-ttu-id="4f28a-138">憑證</span><span class="sxs-lookup"><span data-stu-id="4f28a-138">Certificate</span></span>|<span data-ttu-id="4f28a-139">用戶端會透過憑證來驗證。</span><span class="sxs-lookup"><span data-stu-id="4f28a-139">The client is authenticated using a certificate.</span></span> <span data-ttu-id="4f28a-140">這會使用 SSL Negotiation，並需要服務的憑證。</span><span class="sxs-lookup"><span data-stu-id="4f28a-140">This uses SSL Negotiation and requires a certificate for the service.</span></span>|  
  
## <a name="protectionlevel-attribute"></a><span data-ttu-id="4f28a-141">protectionLevel 屬性</span><span class="sxs-lookup"><span data-stu-id="4f28a-141">protectionLevel Attribute</span></span>  
  
|<span data-ttu-id="4f28a-142">值</span><span class="sxs-lookup"><span data-stu-id="4f28a-142">Value</span></span>|<span data-ttu-id="4f28a-143">描述</span><span class="sxs-lookup"><span data-stu-id="4f28a-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="4f28a-144">None</span><span class="sxs-lookup"><span data-stu-id="4f28a-144">None</span></span>|<span data-ttu-id="4f28a-145">無保護。</span><span class="sxs-lookup"><span data-stu-id="4f28a-145">No protection.</span></span>|  
|<span data-ttu-id="4f28a-146">簽署</span><span class="sxs-lookup"><span data-stu-id="4f28a-146">Sign</span></span>|<span data-ttu-id="4f28a-147">訊息會經過簽署。</span><span class="sxs-lookup"><span data-stu-id="4f28a-147">Messages are signed.</span></span>|  
|<span data-ttu-id="4f28a-148">EncryptAndSign</span><span class="sxs-lookup"><span data-stu-id="4f28a-148">EncryptAndSign</span></span>|<span data-ttu-id="4f28a-149">-訊息會經過加密和簽署。</span><span class="sxs-lookup"><span data-stu-id="4f28a-149">-   Messages are encrypted and signed.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4f28a-150">子元素</span><span class="sxs-lookup"><span data-stu-id="4f28a-150">Child Elements</span></span>  
 <span data-ttu-id="4f28a-151">無</span><span class="sxs-lookup"><span data-stu-id="4f28a-151">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4f28a-152">父項目</span><span class="sxs-lookup"><span data-stu-id="4f28a-152">Parent Elements</span></span>  
  
|<span data-ttu-id="4f28a-153">元素</span><span class="sxs-lookup"><span data-stu-id="4f28a-153">Element</span></span>|<span data-ttu-id="4f28a-154">描述</span><span class="sxs-lookup"><span data-stu-id="4f28a-154">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nettcpbinding.md)|<span data-ttu-id="4f28a-155">指定的安全性功能 [\<netTcpBinding>](nettcpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="4f28a-155">Specifies the security capabilities of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f28a-156">備註</span><span class="sxs-lookup"><span data-stu-id="4f28a-156">Remarks</span></span>  
 <span data-ttu-id="4f28a-157">使用傳輸安全性來達成 SOAP 訊息的完整性與機密性，以及交互驗證。</span><span class="sxs-lookup"><span data-stu-id="4f28a-157">Use Transport security for integrity and confidentiality of the SOAP message and for mutual authentication.</span></span> <span data-ttu-id="4f28a-158">如果在繫結上選取這個安全性模式，便會使用安全性傳輸設定通道堆疊，並以傳輸安全性 (如 Windows Negotiate 或 SSL over TCP) 保護 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="4f28a-158">If this security mode is selected on a binding, the channel stack is configured using a secure transport and the SOAP messages are secured using transport security such as Windows (Negotiate) or SSL over TCP.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f28a-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f28a-159">See also</span></span>

- <xref:System.ServiceModel.TcpTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetTcpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="4f28a-160">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="4f28a-160">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="4f28a-161">繫結</span><span class="sxs-lookup"><span data-stu-id="4f28a-161">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4f28a-162">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="4f28a-162">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="4f28a-163">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="4f28a-163">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
