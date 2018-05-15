---
title: '&lt;securityTokenHandlerConfiguration&gt;'
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 168bdc4fbf640b201ebc61462d04727c23f838f2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltsecuritytokenhandlerconfigurationgt"></a><span data-ttu-id="e92b0-102">&lt;securityTokenHandlerConfiguration&gt;</span><span class="sxs-lookup"><span data-stu-id="e92b0-102">&lt;securityTokenHandlerConfiguration&gt;</span></span>
<span data-ttu-id="e92b0-103">提供的語彙基元處理常式集合的組態。</span><span class="sxs-lookup"><span data-stu-id="e92b0-103">Provides configuration for the collection of token handlers.</span></span>  
  
 <span data-ttu-id="e92b0-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="e92b0-104">\<system.identityModel></span></span>  
<span data-ttu-id="e92b0-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="e92b0-105">\<identityConfiguration></span></span>  
<span data-ttu-id="e92b0-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="e92b0-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="e92b0-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="e92b0-107">\<securityTokenHandlerConfiguration></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e92b0-108">語法</span><span class="sxs-lookup"><span data-stu-id="e92b0-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration saveBootstrapContext=xs:boolean  
          maximumClockSkew=TimeSpan>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e92b0-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e92b0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e92b0-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e92b0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e92b0-111">屬性</span><span class="sxs-lookup"><span data-stu-id="e92b0-111">Attributes</span></span>  
  
|<span data-ttu-id="e92b0-112">屬性</span><span class="sxs-lookup"><span data-stu-id="e92b0-112">Attribute</span></span>|<span data-ttu-id="e92b0-113">描述</span><span class="sxs-lookup"><span data-stu-id="e92b0-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e92b0-114">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="e92b0-114">saveBootstrapContext</span></span>|<span data-ttu-id="e92b0-115">指定啟動程序的語彙基元是否應該包含在工作階段權杖。</span><span class="sxs-lookup"><span data-stu-id="e92b0-115">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="e92b0-116">值可能也會設定權杖處理常式集合的設定`saveBootstrapContext`屬性[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目。</span><span class="sxs-lookup"><span data-stu-id="e92b0-116">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="e92b0-117">權杖處理常式集合上設定的值會覆寫在服務上設定的值。</span><span class="sxs-lookup"><span data-stu-id="e92b0-117">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="e92b0-118">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="e92b0-118">maximumClockSkew</span></span>|<span data-ttu-id="e92b0-119">A <xref:System.TimeSpan> ，指定最大允許的時鐘誤差。</span><span class="sxs-lookup"><span data-stu-id="e92b0-119">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="e92b0-120">執行時間緊迫的作業，例如先驗證登入工作階段的到期時間時，控制允許的最大時鐘誤差。</span><span class="sxs-lookup"><span data-stu-id="e92b0-120">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="e92b0-121">預設值是 5 分鐘，"00: 05:00"。</span><span class="sxs-lookup"><span data-stu-id="e92b0-121">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="e92b0-122">如需有關如何指定<xref:System.TimeSpan>值，請參閱[Timespan 值](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="e92b0-122">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="e92b0-123">最大時鐘誤差可能也會設定服務層級設定`maximumClockSkew`屬性[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目。</span><span class="sxs-lookup"><span data-stu-id="e92b0-123">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="e92b0-124">權杖處理常式集合上設定的值會覆寫在服務上設定的值。</span><span class="sxs-lookup"><span data-stu-id="e92b0-124">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e92b0-125">子項目</span><span class="sxs-lookup"><span data-stu-id="e92b0-125">Child Elements</span></span>  
  
|<span data-ttu-id="e92b0-126">項目</span><span class="sxs-lookup"><span data-stu-id="e92b0-126">Element</span></span>|<span data-ttu-id="e92b0-127">描述</span><span class="sxs-lookup"><span data-stu-id="e92b0-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e92b0-128">\<audienceUris ></span><span class="sxs-lookup"><span data-stu-id="e92b0-128">\<audienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|<span data-ttu-id="e92b0-129">指定是可接受的識別項的此信賴憑證者的合作對象的 Uri 的集合。</span><span class="sxs-lookup"><span data-stu-id="e92b0-129">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="e92b0-130">選擇性。</span><span class="sxs-lookup"><span data-stu-id="e92b0-130">Optional.</span></span>|  
|[<span data-ttu-id="e92b0-131">\<會快取 ></span><span class="sxs-lookup"><span data-stu-id="e92b0-131">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="e92b0-132">註冊用於工作階段權杖，權杖重新執行偵測的快取。</span><span class="sxs-lookup"><span data-stu-id="e92b0-132">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="e92b0-133">可以指定在服務層級，或在安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="e92b0-133">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="e92b0-134">選擇性。</span><span class="sxs-lookup"><span data-stu-id="e92b0-134">Optional.</span></span>|  
|[<span data-ttu-id="e92b0-135">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="e92b0-135">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="e92b0-136">控制權杖處理常式用來驗證憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="e92b0-136">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="e92b0-137">可以指定在服務層級，或在安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="e92b0-137">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="e92b0-138">如果它自己的驗證程式以設定特定的處理常式，會覆寫這些設定。</span><span class="sxs-lookup"><span data-stu-id="e92b0-138">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="e92b0-139">選擇性。</span><span class="sxs-lookup"><span data-stu-id="e92b0-139">Optional.</span></span>|  
|[<span data-ttu-id="e92b0-140">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="e92b0-140">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="e92b0-141">設定簽發者名稱登錄，由權杖處理常式集合中的處理常式。</span><span class="sxs-lookup"><span data-stu-id="e92b0-141">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="e92b0-142">選擇性。</span><span class="sxs-lookup"><span data-stu-id="e92b0-142">Optional.</span></span>|  
|[<span data-ttu-id="e92b0-143">\<issuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="e92b0-143">\<issuerTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|<span data-ttu-id="e92b0-144">註冊由權杖處理常式集合中的處理常式的簽發者權杖解析程式。</span><span class="sxs-lookup"><span data-stu-id="e92b0-144">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="e92b0-145">簽發者的語彙基元解析程式用來解析內送的語彙基元和訊息簽署權杖。</span><span class="sxs-lookup"><span data-stu-id="e92b0-145">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="e92b0-146">選擇性。</span><span class="sxs-lookup"><span data-stu-id="e92b0-146">Optional.</span></span>|  
|[<span data-ttu-id="e92b0-147">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="e92b0-147">\<serviceTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|<span data-ttu-id="e92b0-148">註冊由權杖處理常式集合中的處理常式的服務權杖解析程式。</span><span class="sxs-lookup"><span data-stu-id="e92b0-148">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="e92b0-149">服務語彙基元解析程式用來解析連入權杖和訊息上的加密語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e92b0-149">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="e92b0-150">選擇性。</span><span class="sxs-lookup"><span data-stu-id="e92b0-150">Optional.</span></span>|  
|[<span data-ttu-id="e92b0-151">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="e92b0-151">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|<span data-ttu-id="e92b0-152">啟用權杖重新執行偵測，並指定權杖的到期時間。</span><span class="sxs-lookup"><span data-stu-id="e92b0-152">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="e92b0-153">可以指定在服務層級，或在安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="e92b0-153">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="e92b0-154">選擇性。</span><span class="sxs-lookup"><span data-stu-id="e92b0-154">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e92b0-155">父項目</span><span class="sxs-lookup"><span data-stu-id="e92b0-155">Parent Elements</span></span>  
  
|<span data-ttu-id="e92b0-156">項目</span><span class="sxs-lookup"><span data-stu-id="e92b0-156">Element</span></span>|<span data-ttu-id="e92b0-157">描述</span><span class="sxs-lookup"><span data-stu-id="e92b0-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e92b0-158">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="e92b0-158">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="e92b0-159">指定註冊的端點的安全性權杖處理常式的集合。</span><span class="sxs-lookup"><span data-stu-id="e92b0-159">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e92b0-160">備註</span><span class="sxs-lookup"><span data-stu-id="e92b0-160">Remarks</span></span>  
 <span data-ttu-id="e92b0-161">本節提供的屬性值的<xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration>物件。</span><span class="sxs-lookup"><span data-stu-id="e92b0-161">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="e92b0-162">本節中的設定會覆寫服務上所設定。</span><span class="sxs-lookup"><span data-stu-id="e92b0-162">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="e92b0-163">其中某些設定，接著，可覆寫處理常式加入至安全性權杖處理常式集合時指定的設定。</span><span class="sxs-lookup"><span data-stu-id="e92b0-163">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e92b0-164">範例</span><span class="sxs-lookup"><span data-stu-id="e92b0-164">Example</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>   
      <securityTokenHandlerConfiguration>  
  
        <audienceUris>  
          <clear/>  
          <add value="http://www.example.com/myapp/" />  
        </audienceUris>  
  
        <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel">  
          <trustedIssuers>  
            <add thumbprint="97249e1a … 4c9158de" name="contoso.com" />  
          </trustedIssuers>  
        </issuerNameRegistry>  
  
        <issuerTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
        <serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```
