---
title: '&lt;netHttpBinding&gt; 的 &lt;transport&gt;'
ms.date: 03/30/2017
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
ms.openlocfilehash: 092072df2b88c59c7744a694175ce5ddf39cf79b
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48842641"
---
# <a name="lttransportgt-of-ltnethttpbindinggt"></a><span data-ttu-id="5cf7c-102">&lt;netHttpBinding&gt; 的 &lt;transport&gt;</span><span class="sxs-lookup"><span data-stu-id="5cf7c-102">&lt;transport&gt; of &lt;netHttpBinding&gt;</span></span>
<span data-ttu-id="5cf7c-103">定義可控制 HTTP 傳輸之驗證參數的屬性。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
<span data-ttu-id="5cf7c-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5cf7c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="5cf7c-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="5cf7c-105">\<bindings></span></span>  
<span data-ttu-id="5cf7c-106">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="5cf7c-106">\<netHttpBinding></span></span>  
<span data-ttu-id="5cf7c-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="5cf7c-107">\<binding></span></span>  
<span data-ttu-id="5cf7c-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="5cf7c-108">\<security></span></span>  
<span data-ttu-id="5cf7c-109">\<transport></span><span class="sxs-lookup"><span data-stu-id="5cf7c-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cf7c-110">語法</span><span class="sxs-lookup"><span data-stu-id="5cf7c-110">Syntax</span></span>  
  
```xml
<netHttpBinding>  
  <binding>  
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">  
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"  
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows" realm="string">  
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"  
                                  protectionScenario="TransportSelected|TrustedProxy">  
          <customServiceNames></customServiceNames>  
        </extendedProtectionPolicy>  
      </transport>  
    </security>  
  </binding>  
</netHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5cf7c-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5cf7c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5cf7c-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5cf7c-113">屬性</span><span class="sxs-lookup"><span data-stu-id="5cf7c-113">Attributes</span></span>  
  
|<span data-ttu-id="5cf7c-114">屬性</span><span class="sxs-lookup"><span data-stu-id="5cf7c-114">Attribute</span></span>|<span data-ttu-id="5cf7c-115">描述</span><span class="sxs-lookup"><span data-stu-id="5cf7c-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5cf7c-116">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="5cf7c-116">clientCredentialType</span></span>|<span data-ttu-id="5cf7c-117">-指定要執行使用 HTTP 驗證的用戶端驗證時使用的認證類型。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-117">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="5cf7c-118">預設為 `None`。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-118">The default is `None`.</span></span> <span data-ttu-id="5cf7c-119">此屬性的型別為 <xref:System.ServiceModel.HttpClientCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="5cf7c-120">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="5cf7c-120">proxyCredentialType</span></span>|<span data-ttu-id="5cf7c-121">-指定要執行使用 proxy over HTTP 網域內的用戶端驗證時使用的認證類型。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-121">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="5cf7c-122">這個屬性僅適用於父 `mode` 項目的 `security` 屬性是 `Transport` 或 `TransportCredentialsOnly` 時。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-122">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="5cf7c-123">此屬性的型別為 <xref:System.ServiceModel.HttpProxyCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-123">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="5cf7c-124">realm</span><span class="sxs-lookup"><span data-stu-id="5cf7c-124">realm</span></span>|<span data-ttu-id="5cf7c-125">字串，指定摘要式驗證或基本驗證的 HTTP 驗證配置所使用的領域。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-125">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="5cf7c-126">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-126">The default is an empty string.</span></span>|  
|<span data-ttu-id="5cf7c-127">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="5cf7c-127">policyEnforcement</span></span>|<span data-ttu-id="5cf7c-128">此列舉指定了應該強制執行 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 的時間。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-128">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="5cf7c-129">1.Never：絕不強制執行此原則 (延伸保護已停用)。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-129">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="5cf7c-130">2.WhenSupported：只有當用戶端支援延伸保護時，才強制執行此原則。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-130">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="5cf7c-131">3.Always：一律強制執行此原則。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-131">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="5cf7c-132">不支援延伸保護的用戶端將無法驗證。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-132">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="5cf7c-133">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="5cf7c-133">protectionScenario</span></span>|<span data-ttu-id="5cf7c-134">此列舉會指定原則強制執行的保護案例。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-134">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="5cf7c-135">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="5cf7c-135">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="5cf7c-136">值</span><span class="sxs-lookup"><span data-stu-id="5cf7c-136">Value</span></span>|<span data-ttu-id="5cf7c-137">描述</span><span class="sxs-lookup"><span data-stu-id="5cf7c-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5cf7c-138">無</span><span class="sxs-lookup"><span data-stu-id="5cf7c-138">None</span></span>|<span data-ttu-id="5cf7c-139">傳輸期間不會保護訊息的安全。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-139">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="5cf7c-140">基本</span><span class="sxs-lookup"><span data-stu-id="5cf7c-140">Basic</span></span>|<span data-ttu-id="5cf7c-141">指定基本驗證。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-141">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="5cf7c-142">摘要</span><span class="sxs-lookup"><span data-stu-id="5cf7c-142">Digest</span></span>|<span data-ttu-id="5cf7c-143">指定摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-143">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="5cf7c-144">Ntlm</span><span class="sxs-lookup"><span data-stu-id="5cf7c-144">Ntlm</span></span>|<span data-ttu-id="5cf7c-145">指定可能的情況下以及 Windows 驗證失敗時的 NTLM 驗證。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-145">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="5cf7c-146">Windows</span><span class="sxs-lookup"><span data-stu-id="5cf7c-146">Windows</span></span>|<span data-ttu-id="5cf7c-147">指定 Windows 整合式驗證。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-147">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="5cf7c-148">proxyCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="5cf7c-148">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="5cf7c-149">值</span><span class="sxs-lookup"><span data-stu-id="5cf7c-149">Value</span></span>|<span data-ttu-id="5cf7c-150">描述</span><span class="sxs-lookup"><span data-stu-id="5cf7c-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5cf7c-151">無</span><span class="sxs-lookup"><span data-stu-id="5cf7c-151">None</span></span>|<span data-ttu-id="5cf7c-152">訊息在傳輸期間並未受到保護。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-152">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="5cf7c-153">基本</span><span class="sxs-lookup"><span data-stu-id="5cf7c-153">Basic</span></span>|<span data-ttu-id="5cf7c-154">指定依照 RFC 2617 – HTTP Authentication: Basic and Digest Authentication 所定義的基本驗證。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-154">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="5cf7c-155">摘要</span><span class="sxs-lookup"><span data-stu-id="5cf7c-155">Digest</span></span>|<span data-ttu-id="5cf7c-156">指定依照 RFC 2617 – HTTP Authentication: Basic and Digest Authentication 所定義的摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-156">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="5cf7c-157">Ntlm</span><span class="sxs-lookup"><span data-stu-id="5cf7c-157">Ntlm</span></span>|<span data-ttu-id="5cf7c-158">指定可能的情況下以及 Windows 驗證失敗時的 NTLM 驗證。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-158">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="5cf7c-159">Windows</span><span class="sxs-lookup"><span data-stu-id="5cf7c-159">Windows</span></span>|<span data-ttu-id="5cf7c-160">指定 Windows 整合式驗證。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-160">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="5cf7c-161">憑證</span><span class="sxs-lookup"><span data-stu-id="5cf7c-161">Certificate</span></span>|<span data-ttu-id="5cf7c-162">使用憑證執行用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-162">Performs client authentication using a certificate.</span></span> <span data-ttu-id="5cf7c-163">這個選項只有在父 `Mode` 項目的 `security` 屬性設為 Transport 時才能使用，如果該屬性設為 TransportCredentialOnly，則無法使用。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-163">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5cf7c-164">子元素</span><span class="sxs-lookup"><span data-stu-id="5cf7c-164">Child Elements</span></span>  
 <span data-ttu-id="5cf7c-165">無</span><span class="sxs-lookup"><span data-stu-id="5cf7c-165">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5cf7c-166">父項目</span><span class="sxs-lookup"><span data-stu-id="5cf7c-166">Parent Elements</span></span>  
  
|<span data-ttu-id="5cf7c-167">項目</span><span class="sxs-lookup"><span data-stu-id="5cf7c-167">Element</span></span>|<span data-ttu-id="5cf7c-168">描述</span><span class="sxs-lookup"><span data-stu-id="5cf7c-168">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5cf7c-169">\<security></span><span class="sxs-lookup"><span data-stu-id="5cf7c-169">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nethttpbinding.md)|<span data-ttu-id="5cf7c-170">定義的安全性功能[ \<netHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nethttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-170">Defines the security capabilities for the [\<netHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/nethttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5cf7c-171">範例</span><span class="sxs-lookup"><span data-stu-id="5cf7c-171">Example</span></span>  
 <span data-ttu-id="5cf7c-172">下列範例示範透過基本繫結來使用 SSL 傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-172">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="5cf7c-173">根據預設，基本繫結支援 HTTP 通訊。</span><span class="sxs-lookup"><span data-stu-id="5cf7c-173">By default, the basic binding supports HTTP communication.</span></span>  
  
```xml
<system.serviceModel>  
  <services>  
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
      <endpoint address=""  
                binding="netHttpBinding"  
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
    <netHttpBinding>  
      <!-- Configure basicHttpBinding with Transport security -- >  
      <!-- mode and clientCredentialType set to None.-->  
      <binding name="Binding1">  
        <security mode="Transport">  
          <transport clientCredentialType="None"  
                     proxyCredentialType="None">  
            <extendedProtectionPolicy policyEnforcement="WhenSupported"  
                                      protectionScenario="TransportSelected">  
              <customServiceNames></customServiceNames>  
            </extendedProtectionPolicy>
          </transport> 
        </security>  
      </binding>  
    </netHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5cf7c-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5cf7c-174">See Also</span></span>  
 <span data-ttu-id="5cf7c-175"><xref:System.ServiceModel.BasicHttpSecurityMode.Transport> <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement></span><span class="sxs-lookup"><span data-stu-id="5cf7c-175"><xref:System.ServiceModel.BasicHttpSecurityMode.Transport> <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement></span></span>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 [<span data-ttu-id="5cf7c-176">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="5cf7c-176">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="5cf7c-177">繫結</span><span class="sxs-lookup"><span data-stu-id="5cf7c-177">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="5cf7c-178">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="5cf7c-178">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="5cf7c-179">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="5cf7c-179">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="5cf7c-180">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="5cf7c-180">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
