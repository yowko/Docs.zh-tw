---
title: <transport> 的 <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
ms.openlocfilehash: 2cf69c48a51ce2c687ebcfe9f87f7c22f5f86084
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399377"
---
# <a name="transport-of-basichttpbinding"></a><span data-ttu-id="c2dd4-102">\<basicHttpBinding > 的\<傳輸 ></span><span class="sxs-lookup"><span data-stu-id="c2dd4-102">\<transport> of \<basicHttpBinding></span></span>
<span data-ttu-id="c2dd4-103">定義可控制 HTTP 傳輸之驗證參數的屬性。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
<span data-ttu-id="c2dd4-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c2dd4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c2dd4-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c2dd4-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c2dd4-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="c2dd4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="c2dd4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<basicHttpBinding >** ](basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="c2dd4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)</span></span>\
<span data-ttu-id="c2dd4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="c2dd4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="c2dd4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-of-basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="c2dd4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-basichttpbinding.md)</span></span>\
<span data-ttu-id="c2dd4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<傳輸 >**</span><span class="sxs-lookup"><span data-stu-id="c2dd4-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2dd4-111">語法</span><span class="sxs-lookup"><span data-stu-id="c2dd4-111">Syntax</span></span>  
  
```xml  
<basicHttpBinding>
  <binding>
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows"
                 realm="String">
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"
                                  protectionScenario="TransportSelected|TrustedProxy">
          <customServiceNames>
          </customServiceNames>
        </extendedProtectionPolicy>
      </transport>
    </security>
  </binding>
</basicHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2dd4-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c2dd4-112">Attributes and Elements</span></span>  
 <span data-ttu-id="c2dd4-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2dd4-114">屬性</span><span class="sxs-lookup"><span data-stu-id="c2dd4-114">Attributes</span></span>  
  
|<span data-ttu-id="c2dd4-115">屬性</span><span class="sxs-lookup"><span data-stu-id="c2dd4-115">Attribute</span></span>|<span data-ttu-id="c2dd4-116">描述</span><span class="sxs-lookup"><span data-stu-id="c2dd4-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c2dd4-117">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="c2dd4-117">clientCredentialType</span></span>|<span data-ttu-id="c2dd4-118">-指定使用 HTTP 驗證執行用戶端驗證時，所要使用的認證類型。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-118">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="c2dd4-119">預設為 `None`。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-119">The default is `None`.</span></span> <span data-ttu-id="c2dd4-120">此屬性的型別為 <xref:System.ServiceModel.HttpClientCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-120">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="c2dd4-121">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="c2dd4-121">proxyCredentialType</span></span>|<span data-ttu-id="c2dd4-122">-指定在透過 HTTP 使用 proxy 從網域內執行用戶端驗證時，所要使用的認證類型。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-122">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="c2dd4-123">這個屬性僅適用於父 `mode` 項目的 `security` 屬性是 `Transport` 或 `TransportCredentialsOnly` 時。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-123">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="c2dd4-124">此屬性的型別為 <xref:System.ServiceModel.HttpProxyCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-124">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="c2dd4-125">realm</span><span class="sxs-lookup"><span data-stu-id="c2dd4-125">realm</span></span>|<span data-ttu-id="c2dd4-126">字串，指定摘要式驗證或基本驗證的 HTTP 驗證配置所使用的領域。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-126">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="c2dd4-127">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-127">The default is an empty string.</span></span>|  
|<span data-ttu-id="c2dd4-128">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="c2dd4-128">policyEnforcement</span></span>|<span data-ttu-id="c2dd4-129">此列舉指定了應該強制執行 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 的時間。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-129">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="c2dd4-130">1.Never：絕不強制執行此原則 (延伸保護已停用)。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-130">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="c2dd4-131">2.WhenSupported：只有當用戶端支援延伸保護時，才強制執行此原則。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-131">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="c2dd4-132">3.Always：一律強制執行此原則。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-132">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="c2dd4-133">不支援延伸保護的用戶端將無法驗證。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-133">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="c2dd4-134">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="c2dd4-134">protectionScenario</span></span>|<span data-ttu-id="c2dd4-135">此列舉會指定原則強制執行的保護案例。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-135">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="c2dd4-136">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="c2dd4-136">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="c2dd4-137">值</span><span class="sxs-lookup"><span data-stu-id="c2dd4-137">Value</span></span>|<span data-ttu-id="c2dd4-138">描述</span><span class="sxs-lookup"><span data-stu-id="c2dd4-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c2dd4-139">None</span><span class="sxs-lookup"><span data-stu-id="c2dd4-139">None</span></span>|<span data-ttu-id="c2dd4-140">傳輸期間不會保護訊息的安全。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-140">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="c2dd4-141">基本</span><span class="sxs-lookup"><span data-stu-id="c2dd4-141">Basic</span></span>|<span data-ttu-id="c2dd4-142">指定基本驗證。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-142">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="c2dd4-143">摘要</span><span class="sxs-lookup"><span data-stu-id="c2dd4-143">Digest</span></span>|<span data-ttu-id="c2dd4-144">指定摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-144">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="c2dd4-145">Ntlm</span><span class="sxs-lookup"><span data-stu-id="c2dd4-145">Ntlm</span></span>|<span data-ttu-id="c2dd4-146">指定可能的情況下以及 Windows 驗證失敗時的 NTLM 驗證。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-146">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="c2dd4-147">Windows</span><span class="sxs-lookup"><span data-stu-id="c2dd4-147">Windows</span></span>|<span data-ttu-id="c2dd4-148">指定 Windows 整合式驗證。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-148">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="c2dd4-149">proxyCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="c2dd4-149">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="c2dd4-150">值</span><span class="sxs-lookup"><span data-stu-id="c2dd4-150">Value</span></span>|<span data-ttu-id="c2dd4-151">說明</span><span class="sxs-lookup"><span data-stu-id="c2dd4-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c2dd4-152">無</span><span class="sxs-lookup"><span data-stu-id="c2dd4-152">None</span></span>|<span data-ttu-id="c2dd4-153">-傳輸期間不會保護訊息的安全。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-153">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="c2dd4-154">基本</span><span class="sxs-lookup"><span data-stu-id="c2dd4-154">Basic</span></span>|<span data-ttu-id="c2dd4-155">指定 RFC 2617-HTTP 驗證所定義的基本驗證：基本和摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-155">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="c2dd4-156">摘要</span><span class="sxs-lookup"><span data-stu-id="c2dd4-156">Digest</span></span>|<span data-ttu-id="c2dd4-157">指定依 RFC 2617-HTTP 驗證所定義的摘要式驗證：基本和摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-157">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="c2dd4-158">Ntlm</span><span class="sxs-lookup"><span data-stu-id="c2dd4-158">Ntlm</span></span>|<span data-ttu-id="c2dd4-159">指定可能的情況下以及 Windows 驗證失敗時的 NTLM 驗證。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-159">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="c2dd4-160">Windows</span><span class="sxs-lookup"><span data-stu-id="c2dd4-160">Windows</span></span>|<span data-ttu-id="c2dd4-161">指定 Windows 整合式驗證。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-161">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="c2dd4-162">憑證</span><span class="sxs-lookup"><span data-stu-id="c2dd4-162">Certificate</span></span>|<span data-ttu-id="c2dd4-163">使用憑證執行用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-163">Performs client authentication using a certificate.</span></span> <span data-ttu-id="c2dd4-164">這個選項只有在父 `Mode` 項目的 `security` 屬性設為 Transport 時才能使用，如果該屬性設為 TransportCredentialOnly，則無法使用。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-164">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2dd4-165">子元素</span><span class="sxs-lookup"><span data-stu-id="c2dd4-165">Child Elements</span></span>  
 <span data-ttu-id="c2dd4-166">None</span><span class="sxs-lookup"><span data-stu-id="c2dd4-166">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c2dd4-167">父項目</span><span class="sxs-lookup"><span data-stu-id="c2dd4-167">Parent Elements</span></span>  
  
|<span data-ttu-id="c2dd4-168">項目</span><span class="sxs-lookup"><span data-stu-id="c2dd4-168">Element</span></span>|<span data-ttu-id="c2dd4-169">描述</span><span class="sxs-lookup"><span data-stu-id="c2dd4-169">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c2dd4-170">\<security></span><span class="sxs-lookup"><span data-stu-id="c2dd4-170">\<security></span></span>](security-of-basichttpbinding.md)|<span data-ttu-id="c2dd4-171">定義[ \<basicHttpBinding >](basichttpbinding.md)的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-171">Defines the security capabilities for the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c2dd4-172">範例</span><span class="sxs-lookup"><span data-stu-id="c2dd4-172">Example</span></span>  
 <span data-ttu-id="c2dd4-173">下列範例示範透過基本繫結來使用 SSL 傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-173">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="c2dd4-174">根據預設，基本繫結支援 HTTP 通訊。</span><span class="sxs-lookup"><span data-stu-id="c2dd4-174">By default, the basic binding supports HTTP communication.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
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
    </basicHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="c2dd4-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2dd4-175">See also</span></span>

- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="c2dd4-176">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="c2dd4-176">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="c2dd4-177">繫結</span><span class="sxs-lookup"><span data-stu-id="c2dd4-177">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c2dd4-178">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="c2dd4-178">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="c2dd4-179">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="c2dd4-179">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="c2dd4-180">\<binding></span><span class="sxs-lookup"><span data-stu-id="c2dd4-180">\<binding></span></span>](../../../misc/binding.md)
