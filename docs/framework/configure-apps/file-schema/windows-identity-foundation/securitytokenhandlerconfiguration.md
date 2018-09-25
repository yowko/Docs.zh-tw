---
title: '&lt;Securitytokenhandlerconfiguration>&gt;'
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: d66771ec7ed52ace52df6bb3bfafdcf9cce989b5
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070925"
---
# <a name="ltsecuritytokenhandlerconfigurationgt"></a><span data-ttu-id="0aa98-102">&lt;Securitytokenhandlerconfiguration>&gt;</span><span class="sxs-lookup"><span data-stu-id="0aa98-102">&lt;securityTokenHandlerConfiguration&gt;</span></span>
<span data-ttu-id="0aa98-103">提供的權杖處理常式集合的組態。</span><span class="sxs-lookup"><span data-stu-id="0aa98-103">Provides configuration for the collection of token handlers.</span></span>  
  
 <span data-ttu-id="0aa98-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="0aa98-104">\<system.identityModel></span></span>  
<span data-ttu-id="0aa98-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="0aa98-105">\<identityConfiguration></span></span>  
<span data-ttu-id="0aa98-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="0aa98-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="0aa98-107">\<Securitytokenhandlerconfiguration> ></span><span class="sxs-lookup"><span data-stu-id="0aa98-107">\<securityTokenHandlerConfiguration></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0aa98-108">語法</span><span class="sxs-lookup"><span data-stu-id="0aa98-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0aa98-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0aa98-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0aa98-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0aa98-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0aa98-111">屬性</span><span class="sxs-lookup"><span data-stu-id="0aa98-111">Attributes</span></span>  
  
|<span data-ttu-id="0aa98-112">屬性</span><span class="sxs-lookup"><span data-stu-id="0aa98-112">Attribute</span></span>|<span data-ttu-id="0aa98-113">描述</span><span class="sxs-lookup"><span data-stu-id="0aa98-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0aa98-114">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="0aa98-114">saveBootstrapContext</span></span>|<span data-ttu-id="0aa98-115">指定是否應包含啟動程序權杖中的工作階段權杖。</span><span class="sxs-lookup"><span data-stu-id="0aa98-115">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="0aa98-116">值可能也會在集合上設定權杖處理常式設定`saveBootstrapContext`屬性[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目。</span><span class="sxs-lookup"><span data-stu-id="0aa98-116">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="0aa98-117">權杖處理常式集合上所設定的值會覆寫在服務上設定的值。</span><span class="sxs-lookup"><span data-stu-id="0aa98-117">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="0aa98-118">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="0aa98-118">maximumClockSkew</span></span>|<span data-ttu-id="0aa98-119">A <xref:System.TimeSpan> ，指定最大允許的時鐘誤差。</span><span class="sxs-lookup"><span data-stu-id="0aa98-119">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="0aa98-120">執行時間緊迫的作業，例如驗證登入工作階段的到期時間時，控制最大允許的時鐘誤差。</span><span class="sxs-lookup"><span data-stu-id="0aa98-120">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="0aa98-121">預設值為 5 分鐘，"00: 05:00"。</span><span class="sxs-lookup"><span data-stu-id="0aa98-121">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="0aa98-122">如需有關如何指定<xref:System.TimeSpan>值，請參閱[Timespan 值](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="0aa98-122">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="0aa98-123">最大時鐘誤差可能也會設定服務層級設定`maximumClockSkew`屬性[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目。</span><span class="sxs-lookup"><span data-stu-id="0aa98-123">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="0aa98-124">權杖處理常式集合上所設定的值會覆寫在服務上設定的值。</span><span class="sxs-lookup"><span data-stu-id="0aa98-124">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0aa98-125">子元素</span><span class="sxs-lookup"><span data-stu-id="0aa98-125">Child Elements</span></span>  
  
|<span data-ttu-id="0aa98-126">項目</span><span class="sxs-lookup"><span data-stu-id="0aa98-126">Element</span></span>|<span data-ttu-id="0aa98-127">描述</span><span class="sxs-lookup"><span data-stu-id="0aa98-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0aa98-128">\<audienceUris ></span><span class="sxs-lookup"><span data-stu-id="0aa98-128">\<audienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|<span data-ttu-id="0aa98-129">指定是可接受的識別項，此信賴憑證者的合作對象的 Uri 的集合。</span><span class="sxs-lookup"><span data-stu-id="0aa98-129">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="0aa98-130">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0aa98-130">Optional.</span></span>|  
|[<span data-ttu-id="0aa98-131">\<快取 ></span><span class="sxs-lookup"><span data-stu-id="0aa98-131">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="0aa98-132">註冊用於工作階段權杖和權杖重新執行偵測快取。</span><span class="sxs-lookup"><span data-stu-id="0aa98-132">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="0aa98-133">可以在服務層級或上指定的安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="0aa98-133">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="0aa98-134">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0aa98-134">Optional.</span></span>|  
|[<span data-ttu-id="0aa98-135">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="0aa98-135">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="0aa98-136">控制權杖處理常式用來驗證憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="0aa98-136">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="0aa98-137">可以在服務層級或上指定的安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="0aa98-137">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="0aa98-138">如果特定的處理常式設定為使用自己的驗證程式，則會覆寫這些設定。</span><span class="sxs-lookup"><span data-stu-id="0aa98-138">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="0aa98-139">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0aa98-139">Optional.</span></span>|  
|[<span data-ttu-id="0aa98-140">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="0aa98-140">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="0aa98-141">設定簽發者名稱登錄，可由權杖處理常式集合中的處理常式。</span><span class="sxs-lookup"><span data-stu-id="0aa98-141">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="0aa98-142">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0aa98-142">Optional.</span></span>|  
|[<span data-ttu-id="0aa98-143">\<issuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="0aa98-143">\<issuerTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|<span data-ttu-id="0aa98-144">註冊由權杖處理常式集合中的處理常式的簽發者權杖解析程式。</span><span class="sxs-lookup"><span data-stu-id="0aa98-144">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="0aa98-145">簽發者權杖解析程式用來解析簽署的權杖上傳入的權杖和訊息。</span><span class="sxs-lookup"><span data-stu-id="0aa98-145">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="0aa98-146">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0aa98-146">Optional.</span></span>|  
|[<span data-ttu-id="0aa98-147">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="0aa98-147">\<serviceTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|<span data-ttu-id="0aa98-148">註冊的服務權杖解析程式由權杖處理常式集合中的處理常式。</span><span class="sxs-lookup"><span data-stu-id="0aa98-148">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="0aa98-149">服務權杖解析程式用來解析上傳入的權杖和訊息的加密語彙基元。</span><span class="sxs-lookup"><span data-stu-id="0aa98-149">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="0aa98-150">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0aa98-150">Optional.</span></span>|  
|[<span data-ttu-id="0aa98-151">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="0aa98-151">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|<span data-ttu-id="0aa98-152">啟用權杖重新執行偵測，並指定權杖的到期時間。</span><span class="sxs-lookup"><span data-stu-id="0aa98-152">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="0aa98-153">可以在服務層級或上指定的安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="0aa98-153">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="0aa98-154">選擇性。</span><span class="sxs-lookup"><span data-stu-id="0aa98-154">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0aa98-155">父項目</span><span class="sxs-lookup"><span data-stu-id="0aa98-155">Parent Elements</span></span>  
  
|<span data-ttu-id="0aa98-156">項目</span><span class="sxs-lookup"><span data-stu-id="0aa98-156">Element</span></span>|<span data-ttu-id="0aa98-157">描述</span><span class="sxs-lookup"><span data-stu-id="0aa98-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0aa98-158">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="0aa98-158">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="0aa98-159">指定登錄與端點的安全性權杖處理常式的集合。</span><span class="sxs-lookup"><span data-stu-id="0aa98-159">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0aa98-160">備註</span><span class="sxs-lookup"><span data-stu-id="0aa98-160">Remarks</span></span>  
 <span data-ttu-id="0aa98-161">本節提供的屬性值的<xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration>物件。</span><span class="sxs-lookup"><span data-stu-id="0aa98-161">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="0aa98-162">在本節中的設定會覆寫服務上設定。</span><span class="sxs-lookup"><span data-stu-id="0aa98-162">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="0aa98-163">其中某些設定可以依次覆寫時的處理常式加入至安全性權杖處理常式集合中指定的設定。</span><span class="sxs-lookup"><span data-stu-id="0aa98-163">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0aa98-164">範例</span><span class="sxs-lookup"><span data-stu-id="0aa98-164">Example</span></span>  
  
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
