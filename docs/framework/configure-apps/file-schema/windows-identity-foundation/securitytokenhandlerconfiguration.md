---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: 29e18cdda9e18addef4f0f32fd30e9abf6af78fc
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360403"
---
# <a name="securitytokenhandlerconfiguration"></a><span data-ttu-id="87395-101">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="87395-101">\<securityTokenHandlerConfiguration></span></span>
<span data-ttu-id="87395-102">提供的權杖處理常式集合的組態。</span><span class="sxs-lookup"><span data-stu-id="87395-102">Provides configuration for the collection of token handlers.</span></span>  
  
 <span data-ttu-id="87395-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="87395-103">\<system.identityModel></span></span>  
<span data-ttu-id="87395-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="87395-104">\<identityConfiguration></span></span>  
<span data-ttu-id="87395-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="87395-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="87395-106">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="87395-106">\<securityTokenHandlerConfiguration></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87395-107">語法</span><span class="sxs-lookup"><span data-stu-id="87395-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87395-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="87395-108">Attributes and Elements</span></span>  
 <span data-ttu-id="87395-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="87395-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87395-110">屬性</span><span class="sxs-lookup"><span data-stu-id="87395-110">Attributes</span></span>  
  
|<span data-ttu-id="87395-111">屬性</span><span class="sxs-lookup"><span data-stu-id="87395-111">Attribute</span></span>|<span data-ttu-id="87395-112">描述</span><span class="sxs-lookup"><span data-stu-id="87395-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="87395-113">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="87395-113">saveBootstrapContext</span></span>|<span data-ttu-id="87395-114">指定是否應包含啟動程序權杖中的工作階段權杖。</span><span class="sxs-lookup"><span data-stu-id="87395-114">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="87395-115">值可能也會在集合上設定權杖處理常式設定`saveBootstrapContext`屬性[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目。</span><span class="sxs-lookup"><span data-stu-id="87395-115">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="87395-116">權杖處理常式集合上所設定的值會覆寫在服務上設定的值。</span><span class="sxs-lookup"><span data-stu-id="87395-116">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="87395-117">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="87395-117">maximumClockSkew</span></span>|<span data-ttu-id="87395-118">A <xref:System.TimeSpan> ，指定最大允許的時鐘誤差。</span><span class="sxs-lookup"><span data-stu-id="87395-118">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="87395-119">執行時間緊迫的作業，例如驗證登入工作階段的到期時間時，控制最大允許的時鐘誤差。</span><span class="sxs-lookup"><span data-stu-id="87395-119">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="87395-120">預設值為 5 分鐘，"00: 05:00"。</span><span class="sxs-lookup"><span data-stu-id="87395-120">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="87395-121">如需有關如何指定<xref:System.TimeSpan>值，請參閱[Timespan 值](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="87395-121">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="87395-122">最大時鐘誤差可能也會設定服務層級設定`maximumClockSkew`屬性[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目。</span><span class="sxs-lookup"><span data-stu-id="87395-122">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="87395-123">權杖處理常式集合上所設定的值會覆寫在服務上設定的值。</span><span class="sxs-lookup"><span data-stu-id="87395-123">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87395-124">子元素</span><span class="sxs-lookup"><span data-stu-id="87395-124">Child Elements</span></span>  
  
|<span data-ttu-id="87395-125">項目</span><span class="sxs-lookup"><span data-stu-id="87395-125">Element</span></span>|<span data-ttu-id="87395-126">描述</span><span class="sxs-lookup"><span data-stu-id="87395-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87395-127">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="87395-127">\<audienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|<span data-ttu-id="87395-128">指定是可接受的識別項，此信賴憑證者的合作對象的 Uri 的集合。</span><span class="sxs-lookup"><span data-stu-id="87395-128">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="87395-129">選擇性。</span><span class="sxs-lookup"><span data-stu-id="87395-129">Optional.</span></span>|  
|[<span data-ttu-id="87395-130">\<caches></span><span class="sxs-lookup"><span data-stu-id="87395-130">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="87395-131">註冊用於工作階段權杖和權杖重新執行偵測快取。</span><span class="sxs-lookup"><span data-stu-id="87395-131">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="87395-132">可以在服務層級或上指定的安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="87395-132">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="87395-133">選擇性。</span><span class="sxs-lookup"><span data-stu-id="87395-133">Optional.</span></span>|  
|[<span data-ttu-id="87395-134">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="87395-134">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="87395-135">控制權杖處理常式用來驗證憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="87395-135">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="87395-136">可以在服務層級或上指定的安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="87395-136">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="87395-137">如果特定的處理常式設定為使用自己的驗證程式，則會覆寫這些設定。</span><span class="sxs-lookup"><span data-stu-id="87395-137">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="87395-138">選擇性。</span><span class="sxs-lookup"><span data-stu-id="87395-138">Optional.</span></span>|  
|[<span data-ttu-id="87395-139">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="87395-139">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="87395-140">設定簽發者名稱登錄，可由權杖處理常式集合中的處理常式。</span><span class="sxs-lookup"><span data-stu-id="87395-140">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="87395-141">選擇性。</span><span class="sxs-lookup"><span data-stu-id="87395-141">Optional.</span></span>|  
|[<span data-ttu-id="87395-142">\<issuerTokenResolver></span><span class="sxs-lookup"><span data-stu-id="87395-142">\<issuerTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|<span data-ttu-id="87395-143">註冊由權杖處理常式集合中的處理常式的簽發者權杖解析程式。</span><span class="sxs-lookup"><span data-stu-id="87395-143">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="87395-144">簽發者權杖解析程式用來解析簽署的權杖上傳入的權杖和訊息。</span><span class="sxs-lookup"><span data-stu-id="87395-144">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="87395-145">選擇性。</span><span class="sxs-lookup"><span data-stu-id="87395-145">Optional.</span></span>|  
|[<span data-ttu-id="87395-146">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="87395-146">\<serviceTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|<span data-ttu-id="87395-147">註冊的服務權杖解析程式由權杖處理常式集合中的處理常式。</span><span class="sxs-lookup"><span data-stu-id="87395-147">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="87395-148">服務權杖解析程式用來解析上傳入的權杖和訊息的加密語彙基元。</span><span class="sxs-lookup"><span data-stu-id="87395-148">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="87395-149">選擇性。</span><span class="sxs-lookup"><span data-stu-id="87395-149">Optional.</span></span>|  
|[<span data-ttu-id="87395-150">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="87395-150">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|<span data-ttu-id="87395-151">啟用權杖重新執行偵測，並指定權杖的到期時間。</span><span class="sxs-lookup"><span data-stu-id="87395-151">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="87395-152">可以在服務層級或上指定的安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="87395-152">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="87395-153">選擇性。</span><span class="sxs-lookup"><span data-stu-id="87395-153">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="87395-154">父項目</span><span class="sxs-lookup"><span data-stu-id="87395-154">Parent Elements</span></span>  
  
|<span data-ttu-id="87395-155">項目</span><span class="sxs-lookup"><span data-stu-id="87395-155">Element</span></span>|<span data-ttu-id="87395-156">描述</span><span class="sxs-lookup"><span data-stu-id="87395-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87395-157">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="87395-157">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="87395-158">指定登錄與端點的安全性權杖處理常式的集合。</span><span class="sxs-lookup"><span data-stu-id="87395-158">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87395-159">備註</span><span class="sxs-lookup"><span data-stu-id="87395-159">Remarks</span></span>  
 <span data-ttu-id="87395-160">本節提供的屬性值的<xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration>物件。</span><span class="sxs-lookup"><span data-stu-id="87395-160">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="87395-161">在本節中的設定會覆寫服務上設定。</span><span class="sxs-lookup"><span data-stu-id="87395-161">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="87395-162">其中某些設定可以依次覆寫時的處理常式加入至安全性權杖處理常式集合中指定的設定。</span><span class="sxs-lookup"><span data-stu-id="87395-162">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87395-163">範例</span><span class="sxs-lookup"><span data-stu-id="87395-163">Example</span></span>  
  
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
