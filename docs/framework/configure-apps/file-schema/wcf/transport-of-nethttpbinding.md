---
title: <transport> 的 <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
ms.openlocfilehash: b975015a9c9a0af53117900c45d917ce1c1a53e9
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732820"
---
# <a name="transport-of-nethttpbinding"></a><span data-ttu-id="dbeae-102">\<netHttpBinding 的 \<傳輸 > ></span><span class="sxs-lookup"><span data-stu-id="dbeae-102">\<transport> of \<netHttpBinding></span></span>
<span data-ttu-id="dbeae-103">定義可控制 HTTP 傳輸之驗證參數的屬性。</span><span class="sxs-lookup"><span data-stu-id="dbeae-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
<span data-ttu-id="dbeae-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="dbeae-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="dbeae-105">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="dbeae-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="dbeae-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="dbeae-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="dbeae-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netHttpBinding >** ](nethttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="dbeae-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)</span></span>\
<span data-ttu-id="dbeae-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 ></span><span class="sxs-lookup"><span data-stu-id="dbeae-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="dbeae-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-of-nethttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="dbeae-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nethttpbinding.md)</span></span>\
<span data-ttu-id="dbeae-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**傳輸 >**</span><span class="sxs-lookup"><span data-stu-id="dbeae-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbeae-111">語法</span><span class="sxs-lookup"><span data-stu-id="dbeae-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dbeae-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dbeae-112">Attributes and Elements</span></span>  
 <span data-ttu-id="dbeae-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="dbeae-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dbeae-114">屬性</span><span class="sxs-lookup"><span data-stu-id="dbeae-114">Attributes</span></span>  
  
|<span data-ttu-id="dbeae-115">屬性</span><span class="sxs-lookup"><span data-stu-id="dbeae-115">Attribute</span></span>|<span data-ttu-id="dbeae-116">描述</span><span class="sxs-lookup"><span data-stu-id="dbeae-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dbeae-117">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="dbeae-117">clientCredentialType</span></span>|<span data-ttu-id="dbeae-118">-指定使用 HTTP 驗證執行用戶端驗證時，所要使用的認證類型。</span><span class="sxs-lookup"><span data-stu-id="dbeae-118">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="dbeae-119">預設為 `None`。</span><span class="sxs-lookup"><span data-stu-id="dbeae-119">The default is `None`.</span></span> <span data-ttu-id="dbeae-120">此屬性的型別為 <xref:System.ServiceModel.HttpClientCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="dbeae-120">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="dbeae-121">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="dbeae-121">proxyCredentialType</span></span>|<span data-ttu-id="dbeae-122">-指定在透過 HTTP 使用 proxy 從網域內執行用戶端驗證時，所要使用的認證類型。</span><span class="sxs-lookup"><span data-stu-id="dbeae-122">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="dbeae-123">這個屬性僅適用於父 `mode` 項目的 `security` 屬性是 `Transport` 或 `TransportCredentialsOnly` 時。</span><span class="sxs-lookup"><span data-stu-id="dbeae-123">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="dbeae-124">此屬性的型別為 <xref:System.ServiceModel.HttpProxyCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="dbeae-124">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="dbeae-125">realm</span><span class="sxs-lookup"><span data-stu-id="dbeae-125">realm</span></span>|<span data-ttu-id="dbeae-126">字串，指定摘要式驗證或基本驗證的 HTTP 驗證配置所使用的領域。</span><span class="sxs-lookup"><span data-stu-id="dbeae-126">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="dbeae-127">預設為空字串。</span><span class="sxs-lookup"><span data-stu-id="dbeae-127">The default is an empty string.</span></span>|  
|<span data-ttu-id="dbeae-128">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="dbeae-128">policyEnforcement</span></span>|<span data-ttu-id="dbeae-129">此列舉指定了應該強制執行 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 的時間。</span><span class="sxs-lookup"><span data-stu-id="dbeae-129">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="dbeae-130">1. 永不–永遠不會強制執行原則（已停用 [擴充保護]）。</span><span class="sxs-lookup"><span data-stu-id="dbeae-130">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="dbeae-131">2. WhenSupported-只有在用戶端支援擴充保護時，才會強制執行原則。</span><span class="sxs-lookup"><span data-stu-id="dbeae-131">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="dbeae-132">3. always –一律強制執行原則。</span><span class="sxs-lookup"><span data-stu-id="dbeae-132">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="dbeae-133">不支援延伸保護的用戶端將無法驗證。</span><span class="sxs-lookup"><span data-stu-id="dbeae-133">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="dbeae-134">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="dbeae-134">protectionScenario</span></span>|<span data-ttu-id="dbeae-135">此列舉會指定原則強制執行的保護案例。</span><span class="sxs-lookup"><span data-stu-id="dbeae-135">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="dbeae-136">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="dbeae-136">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="dbeae-137">值</span><span class="sxs-lookup"><span data-stu-id="dbeae-137">Value</span></span>|<span data-ttu-id="dbeae-138">描述</span><span class="sxs-lookup"><span data-stu-id="dbeae-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dbeae-139">None</span><span class="sxs-lookup"><span data-stu-id="dbeae-139">None</span></span>|<span data-ttu-id="dbeae-140">傳輸期間不會保護訊息的安全。</span><span class="sxs-lookup"><span data-stu-id="dbeae-140">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="dbeae-141">基本</span><span class="sxs-lookup"><span data-stu-id="dbeae-141">Basic</span></span>|<span data-ttu-id="dbeae-142">指定基本驗證。</span><span class="sxs-lookup"><span data-stu-id="dbeae-142">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="dbeae-143">摘要</span><span class="sxs-lookup"><span data-stu-id="dbeae-143">Digest</span></span>|<span data-ttu-id="dbeae-144">指定摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="dbeae-144">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="dbeae-145">Ntlm</span><span class="sxs-lookup"><span data-stu-id="dbeae-145">Ntlm</span></span>|<span data-ttu-id="dbeae-146">指定可能的情況下以及 Windows 驗證失敗時的 NTLM 驗證。</span><span class="sxs-lookup"><span data-stu-id="dbeae-146">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="dbeae-147">Windows</span><span class="sxs-lookup"><span data-stu-id="dbeae-147">Windows</span></span>|<span data-ttu-id="dbeae-148">指定 Windows 整合式驗證。</span><span class="sxs-lookup"><span data-stu-id="dbeae-148">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="dbeae-149">proxyCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="dbeae-149">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="dbeae-150">值</span><span class="sxs-lookup"><span data-stu-id="dbeae-150">Value</span></span>|<span data-ttu-id="dbeae-151">描述</span><span class="sxs-lookup"><span data-stu-id="dbeae-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="dbeae-152">None</span><span class="sxs-lookup"><span data-stu-id="dbeae-152">None</span></span>|<span data-ttu-id="dbeae-153">-傳輸期間不會保護訊息的安全。</span><span class="sxs-lookup"><span data-stu-id="dbeae-153">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="dbeae-154">基本</span><span class="sxs-lookup"><span data-stu-id="dbeae-154">Basic</span></span>|<span data-ttu-id="dbeae-155">指定依照 RFC 2617 – HTTP Authentication: Basic and Digest Authentication 所定義的基本驗證。</span><span class="sxs-lookup"><span data-stu-id="dbeae-155">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="dbeae-156">摘要</span><span class="sxs-lookup"><span data-stu-id="dbeae-156">Digest</span></span>|<span data-ttu-id="dbeae-157">指定依照 RFC 2617 – HTTP Authentication: Basic and Digest Authentication 所定義的摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="dbeae-157">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="dbeae-158">Ntlm</span><span class="sxs-lookup"><span data-stu-id="dbeae-158">Ntlm</span></span>|<span data-ttu-id="dbeae-159">指定可能的情況下以及 Windows 驗證失敗時的 NTLM 驗證。</span><span class="sxs-lookup"><span data-stu-id="dbeae-159">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="dbeae-160">Windows</span><span class="sxs-lookup"><span data-stu-id="dbeae-160">Windows</span></span>|<span data-ttu-id="dbeae-161">指定 Windows 整合式驗證。</span><span class="sxs-lookup"><span data-stu-id="dbeae-161">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="dbeae-162">憑證</span><span class="sxs-lookup"><span data-stu-id="dbeae-162">Certificate</span></span>|<span data-ttu-id="dbeae-163">使用憑證執行用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="dbeae-163">Performs client authentication using a certificate.</span></span> <span data-ttu-id="dbeae-164">這個選項只有在父 `Mode` 項目的 `security` 屬性設為 Transport 時才能使用，如果該屬性設為 TransportCredentialOnly，則無法使用。</span><span class="sxs-lookup"><span data-stu-id="dbeae-164">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dbeae-165">子項目</span><span class="sxs-lookup"><span data-stu-id="dbeae-165">Child Elements</span></span>  
 <span data-ttu-id="dbeae-166">None</span><span class="sxs-lookup"><span data-stu-id="dbeae-166">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dbeae-167">父項目</span><span class="sxs-lookup"><span data-stu-id="dbeae-167">Parent Elements</span></span>  
  
|<span data-ttu-id="dbeae-168">項目</span><span class="sxs-lookup"><span data-stu-id="dbeae-168">Element</span></span>|<span data-ttu-id="dbeae-169">描述</span><span class="sxs-lookup"><span data-stu-id="dbeae-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dbeae-170">\<security ></span><span class="sxs-lookup"><span data-stu-id="dbeae-170">\<security></span></span>](security-of-nethttpbinding.md)|<span data-ttu-id="dbeae-171">定義[\<netHttpBinding >](nethttpbinding.md)的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="dbeae-171">Defines the security capabilities for the [\<netHttpBinding>](nethttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="dbeae-172">範例</span><span class="sxs-lookup"><span data-stu-id="dbeae-172">Example</span></span>  
 <span data-ttu-id="dbeae-173">下列範例示範透過基本繫結來使用 SSL 傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="dbeae-173">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="dbeae-174">根據預設，基本繫結支援 HTTP 通訊。</span><span class="sxs-lookup"><span data-stu-id="dbeae-174">By default, the basic binding supports HTTP communication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dbeae-175">請參閱</span><span class="sxs-lookup"><span data-stu-id="dbeae-175">See also</span></span>

- <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="dbeae-176">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="dbeae-176">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="dbeae-177">繫結</span><span class="sxs-lookup"><span data-stu-id="dbeae-177">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="dbeae-178">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="dbeae-178">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="dbeae-179">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="dbeae-179">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="dbeae-180">\<binding ></span><span class="sxs-lookup"><span data-stu-id="dbeae-180">\<binding></span></span>](bindings.md)
