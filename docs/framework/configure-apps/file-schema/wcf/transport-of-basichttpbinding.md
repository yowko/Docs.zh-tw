---
title: <transport> 的 <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
ms.openlocfilehash: c563339e4f854cc4e60f92dd5b8c0b39112dc000
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736115"
---
# <a name="transport-of-basichttpbinding"></a><span data-ttu-id="76187-102">\<transport> 的 \<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="76187-102">\<transport> of \<basicHttpBinding></span></span>
<span data-ttu-id="76187-103">定義可控制 HTTP 傳輸之驗證參數的屬性。</span><span class="sxs-lookup"><span data-stu-id="76187-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="76187-104">語法</span><span class="sxs-lookup"><span data-stu-id="76187-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="76187-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="76187-105">Attributes and Elements</span></span>  
 <span data-ttu-id="76187-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="76187-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="76187-107">屬性</span><span class="sxs-lookup"><span data-stu-id="76187-107">Attributes</span></span>  
  
|<span data-ttu-id="76187-108">屬性</span><span class="sxs-lookup"><span data-stu-id="76187-108">Attribute</span></span>|<span data-ttu-id="76187-109">描述</span><span class="sxs-lookup"><span data-stu-id="76187-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="76187-110">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="76187-110">clientCredentialType</span></span>|<span data-ttu-id="76187-111">-指定使用 HTTP 驗證執行用戶端驗證時，所要使用的認證類型。</span><span class="sxs-lookup"><span data-stu-id="76187-111">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="76187-112">預設值為 `None`。</span><span class="sxs-lookup"><span data-stu-id="76187-112">The default is `None`.</span></span> <span data-ttu-id="76187-113">此屬性的型別為 <xref:System.ServiceModel.HttpClientCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="76187-113">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="76187-114">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="76187-114">proxyCredentialType</span></span>|<span data-ttu-id="76187-115">-指定在透過 HTTP 使用 proxy 從網域內執行用戶端驗證時，所要使用的認證類型。</span><span class="sxs-lookup"><span data-stu-id="76187-115">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="76187-116">這個屬性僅適用於父 `mode` 項目的 `security` 屬性是 `Transport` 或 `TransportCredentialsOnly` 時。</span><span class="sxs-lookup"><span data-stu-id="76187-116">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="76187-117">此屬性的型別為 <xref:System.ServiceModel.HttpProxyCredentialType>。</span><span class="sxs-lookup"><span data-stu-id="76187-117">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="76187-118">realm</span><span class="sxs-lookup"><span data-stu-id="76187-118">realm</span></span>|<span data-ttu-id="76187-119">字串，指定摘要式驗證或基本驗證的 HTTP 驗證配置所使用的領域。</span><span class="sxs-lookup"><span data-stu-id="76187-119">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="76187-120">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="76187-120">The default is an empty string.</span></span>|  
|<span data-ttu-id="76187-121">policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="76187-121">policyEnforcement</span></span>|<span data-ttu-id="76187-122">此列舉指定了應該強制執行 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 的時間。</span><span class="sxs-lookup"><span data-stu-id="76187-122">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="76187-123">1. 永不–永遠不會強制執行原則（已停用 [擴充保護]）。</span><span class="sxs-lookup"><span data-stu-id="76187-123">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="76187-124">2. WhenSupported-只有在用戶端支援擴充保護時，才會強制執行原則。</span><span class="sxs-lookup"><span data-stu-id="76187-124">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="76187-125">3. always –一律強制執行原則。</span><span class="sxs-lookup"><span data-stu-id="76187-125">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="76187-126">不支援延伸保護的用戶端將無法驗證。</span><span class="sxs-lookup"><span data-stu-id="76187-126">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="76187-127">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="76187-127">protectionScenario</span></span>|<span data-ttu-id="76187-128">此列舉會指定原則強制執行的保護案例。</span><span class="sxs-lookup"><span data-stu-id="76187-128">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="76187-129">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="76187-129">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="76187-130">值</span><span class="sxs-lookup"><span data-stu-id="76187-130">Value</span></span>|<span data-ttu-id="76187-131">描述</span><span class="sxs-lookup"><span data-stu-id="76187-131">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="76187-132">None</span><span class="sxs-lookup"><span data-stu-id="76187-132">None</span></span>|<span data-ttu-id="76187-133">傳輸期間不會保護訊息的安全。</span><span class="sxs-lookup"><span data-stu-id="76187-133">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="76187-134">基本</span><span class="sxs-lookup"><span data-stu-id="76187-134">Basic</span></span>|<span data-ttu-id="76187-135">指定基本驗證。</span><span class="sxs-lookup"><span data-stu-id="76187-135">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="76187-136">Digest</span><span class="sxs-lookup"><span data-stu-id="76187-136">Digest</span></span>|<span data-ttu-id="76187-137">指定摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="76187-137">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="76187-138">Ntlm</span><span class="sxs-lookup"><span data-stu-id="76187-138">Ntlm</span></span>|<span data-ttu-id="76187-139">指定可能的情況下以及 Windows 驗證失敗時的 NTLM 驗證。</span><span class="sxs-lookup"><span data-stu-id="76187-139">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="76187-140">Windows</span><span class="sxs-lookup"><span data-stu-id="76187-140">Windows</span></span>|<span data-ttu-id="76187-141">指定 Windows 整合式驗證。</span><span class="sxs-lookup"><span data-stu-id="76187-141">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="76187-142">proxyCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="76187-142">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="76187-143">值</span><span class="sxs-lookup"><span data-stu-id="76187-143">Value</span></span>|<span data-ttu-id="76187-144">描述</span><span class="sxs-lookup"><span data-stu-id="76187-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="76187-145">None</span><span class="sxs-lookup"><span data-stu-id="76187-145">None</span></span>|<span data-ttu-id="76187-146">-傳輸期間不會保護訊息的安全。</span><span class="sxs-lookup"><span data-stu-id="76187-146">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="76187-147">基本</span><span class="sxs-lookup"><span data-stu-id="76187-147">Basic</span></span>|<span data-ttu-id="76187-148">指定依照 RFC 2617 – HTTP Authentication: Basic and Digest Authentication 所定義的基本驗證。</span><span class="sxs-lookup"><span data-stu-id="76187-148">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="76187-149">Digest</span><span class="sxs-lookup"><span data-stu-id="76187-149">Digest</span></span>|<span data-ttu-id="76187-150">指定依照 RFC 2617 – HTTP Authentication: Basic and Digest Authentication 所定義的摘要式驗證。</span><span class="sxs-lookup"><span data-stu-id="76187-150">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="76187-151">Ntlm</span><span class="sxs-lookup"><span data-stu-id="76187-151">Ntlm</span></span>|<span data-ttu-id="76187-152">指定可能的情況下以及 Windows 驗證失敗時的 NTLM 驗證。</span><span class="sxs-lookup"><span data-stu-id="76187-152">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="76187-153">Windows</span><span class="sxs-lookup"><span data-stu-id="76187-153">Windows</span></span>|<span data-ttu-id="76187-154">指定 Windows 整合式驗證。</span><span class="sxs-lookup"><span data-stu-id="76187-154">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="76187-155">憑證</span><span class="sxs-lookup"><span data-stu-id="76187-155">Certificate</span></span>|<span data-ttu-id="76187-156">使用憑證執行用戶端驗證。</span><span class="sxs-lookup"><span data-stu-id="76187-156">Performs client authentication using a certificate.</span></span> <span data-ttu-id="76187-157">這個選項只有在父 `Mode` 項目的 `security` 屬性設為 Transport 時才能使用，如果該屬性設為 TransportCredentialOnly，則無法使用。</span><span class="sxs-lookup"><span data-stu-id="76187-157">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="76187-158">子元素</span><span class="sxs-lookup"><span data-stu-id="76187-158">Child Elements</span></span>  
 <span data-ttu-id="76187-159">無</span><span class="sxs-lookup"><span data-stu-id="76187-159">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="76187-160">父項目</span><span class="sxs-lookup"><span data-stu-id="76187-160">Parent Elements</span></span>  
  
|<span data-ttu-id="76187-161">元素</span><span class="sxs-lookup"><span data-stu-id="76187-161">Element</span></span>|<span data-ttu-id="76187-162">描述</span><span class="sxs-lookup"><span data-stu-id="76187-162">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|<span data-ttu-id="76187-163">定義的安全性功能 [\<basicHttpBinding>](basichttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="76187-163">Defines the security capabilities for the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="76187-164">範例</span><span class="sxs-lookup"><span data-stu-id="76187-164">Example</span></span>  
 <span data-ttu-id="76187-165">下列範例示範透過基本繫結來使用 SSL 傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="76187-165">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="76187-166">根據預設，基本繫結支援 HTTP 通訊。</span><span class="sxs-lookup"><span data-stu-id="76187-166">By default, the basic binding supports HTTP communication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="76187-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="76187-167">See also</span></span>

- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>
- <xref:System.ServiceModel.HttpTransportSecurity>
- [<span data-ttu-id="76187-168">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="76187-168">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="76187-169">繫結</span><span class="sxs-lookup"><span data-stu-id="76187-169">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="76187-170">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="76187-170">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="76187-171">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="76187-171">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
