---
title: <transport> 的 <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
ms.openlocfilehash: 521aaf3913a1d30d10a674b71d4d98affcabc296
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399347"
---
# <a name="transport-of-nethttpbinding"></a><span data-ttu-id="a823c-102">\<netHttpBinding > 的\<傳輸 ></span><span class="sxs-lookup"><span data-stu-id="a823c-102">\<transport> of \<netHttpBinding></span></span>
<span data-ttu-id="a823c-103">定義可控制 HTTP 傳輸之驗證參數的屬性。</span><span class="sxs-lookup"><span data-stu-id="a823c-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
<span data-ttu-id="a823c-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a823c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a823c-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a823c-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a823c-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="a823c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="a823c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netHttpBinding >** ](nethttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="a823c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)</span></span>\
<span data-ttu-id="a823c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="a823c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="a823c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-of-nethttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="a823c-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nethttpbinding.md)</span></span>\
<span data-ttu-id="a823c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<傳輸 >**</span><span class="sxs-lookup"><span data-stu-id="a823c-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a823c-111">語法</span><span class="sxs-lookup"><span data-stu-id="a823c-111">Syntax</span></span>  
  
```xml  
<netHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="string">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</netHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a823c-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a823c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="a823c-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a823c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a823c-114">屬性</span><span class="sxs-lookup"><span data-stu-id="a823c-114">Attributes</span></span>  
  
|<span data-ttu-id="a823c-115">屬性</span><span class="sxs-lookup"><span data-stu-id="a823c-115">Attribute</span></span>|<span data-ttu-id="a823c-116">描述</span><span class="sxs-lookup"><span data-stu-id="a823c-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a823c-117">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="a823c-117">clientCredentialType</span></span>|<span data-ttu-id="a823c-118">-指定使用 HTTP 驗證執行用戶端驗證時，所要使用的認證類型。</span><span class="sxs-lookup"><span data-stu-id="a823c-118">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="a823c-119">預設為 `None`。</span><span class="sxs-lookup"><span data-stu-id="a823c-119">The default is `None`.</span></span> <span data-ttu-id="a823c-120">此屬性的型別為 <xref:System.ServiceModel.HttpClientCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="a823c-120">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="a823c-121">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="a823c-121">proxyCredentialType</span></span>|<span data-ttu-id="a823c-122">-指定在透過 HTTP 使用 proxy 從網域內執行用戶端驗證時，所要使用的認證類型。</span><span class="sxs-lookup"><span data-stu-id="a823c-122">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="a823c-123">這個屬性僅適用於父 `mode` 項目的 `security` 屬性是 `Transport` 或 `TransportCredentialsOnly` 時。</span><span class="sxs-lookup"><span data-stu-id="a823c-123">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="a823c-124">此屬性的型別為 <xref:System.ServiceModel.HttpProxyCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="a823c-124">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="a823c-125">realm</span><span class="sxs-lookup"><span data-stu-id="a823c-125">realm</span></span>|<span data-ttu-id="a823c-126">字串，指定摘要式驗證或基本驗證的 HTTP 驗證配置所使用的領域。</span><span class="sxs-lookup"><span data-stu-id="a823c-126">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="a823c-127">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="a823c-127">The default is an empty string.</span></span>|  
|<span data-ttu-id="a823c-128">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="a823c-128">policyEnforcement</span></span>|<span data-ttu-id="a823c-129">此列舉指定了應該強制執行 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 的時間。</span><span class="sxs-lookup"><span data-stu-id="a823c-129">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="a823c-130">1.Never：絕不強制執行此原則 (延伸保護已停用)。</span><span class="sxs-lookup"><span data-stu-id="a823c-130">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="a823c-131">2.WhenSupported：只有當用戶端支援延伸保護時，才強制執行此原則。</span><span class="sxs-lookup"><span data-stu-id="a823c-131">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="a823c-132">3.Always：一律強制執行此原則。</span><span class="sxs-lookup"><span data-stu-id="a823c-132">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="a823c-133">不支援延伸保護的用戶端將無法驗證。</span><span class="sxs-lookup"><span data-stu-id="a823c-133">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="a823c-134">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="a823c-134">protectionScenario</span></span>|<span data-ttu-id="a823c-135">此列舉會指定原則強制執行的保護案例。</span><span class="sxs-lookup"><span data-stu-id="a823c-135">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="a823c-136">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="a823c-136">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="a823c-137">值</span><span class="sxs-lookup"><span data-stu-id="a823c-137">Value</span></span>|<span data-ttu-id="a823c-138">描述</span><span class="sxs-lookup"><span data-stu-id="a823c-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a823c-139">無</span><span class="sxs-lookup"><span data-stu-id="a823c-139">None</span></span>|<span data-ttu-id="a823c-140">傳輸期間不會保護訊息的安全。</span><span class="sxs-lookup"><span data-stu-id="a823c-140">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="a823c-141">基本</span><span class="sxs-lookup"><span data-stu-id="a823c-141">Basic</span></span>|<span data-ttu-id="a823c-142">指定基本驗證。</span><span class="sxs-lookup"><span data-stu-id="a823c-142">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="a823c-143">摘要</span><span class="sxs-lookup"><span data-stu-id="a823c-143">Digest</span></span>|<span data-ttu-id="a823c-144">指定摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="a823c-144">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="a823c-145">Ntlm</span><span class="sxs-lookup"><span data-stu-id="a823c-145">Ntlm</span></span>|<span data-ttu-id="a823c-146">指定可能的情況下以及 Windows 驗證失敗時的 NTLM 驗證。</span><span class="sxs-lookup"><span data-stu-id="a823c-146">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="a823c-147">Windows</span><span class="sxs-lookup"><span data-stu-id="a823c-147">Windows</span></span>|<span data-ttu-id="a823c-148">指定 Windows 整合式驗證。</span><span class="sxs-lookup"><span data-stu-id="a823c-148">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="a823c-149">proxyCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="a823c-149">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="a823c-150">值</span><span class="sxs-lookup"><span data-stu-id="a823c-150">Value</span></span>|<span data-ttu-id="a823c-151">描述</span><span class="sxs-lookup"><span data-stu-id="a823c-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a823c-152">無</span><span class="sxs-lookup"><span data-stu-id="a823c-152">None</span></span>|<span data-ttu-id="a823c-153">-傳輸期間不會保護訊息的安全。</span><span class="sxs-lookup"><span data-stu-id="a823c-153">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="a823c-154">基本</span><span class="sxs-lookup"><span data-stu-id="a823c-154">Basic</span></span>|<span data-ttu-id="a823c-155">指定 RFC 2617-HTTP 驗證所定義的基本驗證：基本和摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="a823c-155">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="a823c-156">摘要</span><span class="sxs-lookup"><span data-stu-id="a823c-156">Digest</span></span>|<span data-ttu-id="a823c-157">指定依 RFC 2617-HTTP 驗證所定義的摘要式驗證：基本和摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="a823c-157">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="a823c-158">Ntlm</span><span class="sxs-lookup"><span data-stu-id="a823c-158">Ntlm</span></span>|<span data-ttu-id="a823c-159">指定可能的情況下以及 Windows 驗證失敗時的 NTLM 驗證。</span><span class="sxs-lookup"><span data-stu-id="a823c-159">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="a823c-160">Windows</span><span class="sxs-lookup"><span data-stu-id="a823c-160">Windows</span></span>|<span data-ttu-id="a823c-161">指定 Windows 整合式驗證。</span><span class="sxs-lookup"><span data-stu-id="a823c-161">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="a823c-162">憑證</span><span class="sxs-lookup"><span data-stu-id="a823c-162">Certificate</span></span>|<span data-ttu-id="a823c-163">使用憑證執行用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="a823c-163">Performs client authentication using a certificate.</span></span> <span data-ttu-id="a823c-164">這個選項只有在父 `Mode` 項目的 `security` 屬性設為 Transport 時才能使用，如果該屬性設為 TransportCredentialOnly，則無法使用。</span><span class="sxs-lookup"><span data-stu-id="a823c-164">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a823c-165">子元素</span><span class="sxs-lookup"><span data-stu-id="a823c-165">Child Elements</span></span>  
 <span data-ttu-id="a823c-166">None</span><span class="sxs-lookup"><span data-stu-id="a823c-166">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a823c-167">父項目</span><span class="sxs-lookup"><span data-stu-id="a823c-167">Parent Elements</span></span>  
  
|<span data-ttu-id="a823c-168">項目</span><span class="sxs-lookup"><span data-stu-id="a823c-168">Element</span></span>|<span data-ttu-id="a823c-169">描述</span><span class="sxs-lookup"><span data-stu-id="a823c-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a823c-170">\<security></span><span class="sxs-lookup"><span data-stu-id="a823c-170">\<security></span></span>](security-of-nethttpbinding.md)|<span data-ttu-id="a823c-171">定義[ \<netHttpBinding >](nethttpbinding.md)的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="a823c-171">Defines the security capabilities for the [\<netHttpBinding>](nethttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a823c-172">範例</span><span class="sxs-lookup"><span data-stu-id="a823c-172">Example</span></span>  
 <span data-ttu-id="a823c-173">下列範例示範透過基本繫結來使用 SSL 傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="a823c-173">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="a823c-174">根據預設，基本繫結支援 HTTP 通訊。</span><span class="sxs-lookup"><span data-stu-id="a823c-174">By default, the basic binding supports HTTP communication.</span></span>  
  
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
      <!-- Configure basicHttpBinding with Transport security -->
      <!-- mode and clientCredentialType set to None. -->
      <binding name="Binding1">
        <security mode="Transport">
          <transport clientCredentialType="None"
                     proxyCredentialType="None">
            <extendedProtectionPolicy policyEnforcement="WhenSupported"
                                      protectionScenario="TransportSelected">
              <customServiceNames>
              </customServiceNames>
            </extendedProtectionPolicy>
          </transport>
        </security>
      </binding>
    </netHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="a823c-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a823c-175">See also</span></span>

- <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="a823c-176">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="a823c-176">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a823c-177">繫結</span><span class="sxs-lookup"><span data-stu-id="a823c-177">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a823c-178">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="a823c-178">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a823c-179">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="a823c-179">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="a823c-180">\<binding></span><span class="sxs-lookup"><span data-stu-id="a823c-180">\<binding></span></span>](../../../misc/binding.md)
