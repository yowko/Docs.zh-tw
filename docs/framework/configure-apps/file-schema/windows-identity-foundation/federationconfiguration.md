---
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: 102aadaaa7d7780f1266e1abcea46f0fcf95671e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622544"
---
# <a name="federationconfiguration"></a><span data-ttu-id="7471c-101">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="7471c-101">\<federationConfiguration></span></span>
<span data-ttu-id="7471c-102">會設定<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(WSFAM) 和<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM) 時使用同盟驗證透過 WS-同盟通訊協定。</span><span class="sxs-lookup"><span data-stu-id="7471c-102">Configures the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) when using federated authentication through the WS-Federation protocol.</span></span> <span data-ttu-id="7471c-103">會設定<xref:System.Security.Claims.ClaimsAuthorizationManager>使用時<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>或<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>類別提供的宣告型存取控制。</span><span class="sxs-lookup"><span data-stu-id="7471c-103">Configures the <xref:System.Security.Claims.ClaimsAuthorizationManager> when using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control.</span></span>  
  
 <span data-ttu-id="7471c-104">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="7471c-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="7471c-105">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="7471c-105">\<federationConfiguration></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7471c-106">語法</span><span class="sxs-lookup"><span data-stu-id="7471c-106">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7471c-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7471c-107">Attributes and Elements</span></span>  
 <span data-ttu-id="7471c-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7471c-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7471c-109">屬性</span><span class="sxs-lookup"><span data-stu-id="7471c-109">Attributes</span></span>  
  
|<span data-ttu-id="7471c-110">屬性</span><span class="sxs-lookup"><span data-stu-id="7471c-110">Attribute</span></span>|<span data-ttu-id="7471c-111">描述</span><span class="sxs-lookup"><span data-stu-id="7471c-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7471c-112">名稱</span><span class="sxs-lookup"><span data-stu-id="7471c-112">name</span></span>|<span data-ttu-id="7471c-113">這個同盟組態項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="7471c-113">The name of this federation configuration element.</span></span> <span data-ttu-id="7471c-114">這個屬性主要是提供的擴充點，針對未來的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="7471c-114">This attribute primarily provides an extensibility point for future protocols.</span></span> <span data-ttu-id="7471c-115">選擇性。</span><span class="sxs-lookup"><span data-stu-id="7471c-115">Optional.</span></span>|  
|<span data-ttu-id="7471c-116">identityConfigurationName</span><span class="sxs-lookup"><span data-stu-id="7471c-116">identityConfigurationName</span></span>|<span data-ttu-id="7471c-117">身分識別組態區段中所指定的名稱[ \<Identityconfiguration> >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)若要使用的項目。</span><span class="sxs-lookup"><span data-stu-id="7471c-117">The name of the identity configuration section as specified in an [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element to use.</span></span> <span data-ttu-id="7471c-118">如果未指定此屬性，則會使用預設的身分識別組態區段。</span><span class="sxs-lookup"><span data-stu-id="7471c-118">If this attribute is not specified, the default identity configuration section is used.</span></span> <span data-ttu-id="7471c-119">選擇性。</span><span class="sxs-lookup"><span data-stu-id="7471c-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7471c-120">子元素</span><span class="sxs-lookup"><span data-stu-id="7471c-120">Child Elements</span></span>  
  
|<span data-ttu-id="7471c-121">項目</span><span class="sxs-lookup"><span data-stu-id="7471c-121">Element</span></span>|<span data-ttu-id="7471c-122">描述</span><span class="sxs-lookup"><span data-stu-id="7471c-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7471c-123">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="7471c-123">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="7471c-124">設定 SAM 所使用的 cookie 處理常式。</span><span class="sxs-lookup"><span data-stu-id="7471c-124">Configures the cookie handler used by the SAM.</span></span> <span data-ttu-id="7471c-125">選擇性。</span><span class="sxs-lookup"><span data-stu-id="7471c-125">Optional.</span></span>|  
|[<span data-ttu-id="7471c-126">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="7471c-126">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|<span data-ttu-id="7471c-127">設定用來加密和解密權杖的憑證。</span><span class="sxs-lookup"><span data-stu-id="7471c-127">Configures the certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="7471c-128">選擇性。</span><span class="sxs-lookup"><span data-stu-id="7471c-128">Optional.</span></span>|  
|[<span data-ttu-id="7471c-129">\<wsFederation></span><span class="sxs-lookup"><span data-stu-id="7471c-129">\<wsFederation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation.md)|<span data-ttu-id="7471c-130">設定 WS-同盟驗證模組 (WSFAM)。</span><span class="sxs-lookup"><span data-stu-id="7471c-130">Configures the WS-Federation Authentication Module (WSFAM).</span></span> <span data-ttu-id="7471c-131">選擇性。</span><span class="sxs-lookup"><span data-stu-id="7471c-131">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7471c-132">父項目</span><span class="sxs-lookup"><span data-stu-id="7471c-132">Parent Elements</span></span>  
  
|<span data-ttu-id="7471c-133">項目</span><span class="sxs-lookup"><span data-stu-id="7471c-133">Element</span></span>|<span data-ttu-id="7471c-134">描述</span><span class="sxs-lookup"><span data-stu-id="7471c-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7471c-135">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="7471c-135">\<system.identityModel.services></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)|<span data-ttu-id="7471c-136">使用 WS-同盟通訊協定進行驗證的組態區段。</span><span class="sxs-lookup"><span data-stu-id="7471c-136">Configuration section for authentication using the WS-Federation protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7471c-137">備註</span><span class="sxs-lookup"><span data-stu-id="7471c-137">Remarks</span></span>  
 <span data-ttu-id="7471c-138">\<Federationconfiguration> > 項目會提供兩種不同案例中的設定：</span><span class="sxs-lookup"><span data-stu-id="7471c-138">The \<federationConfiguration> element provides settings in two different scenarios:</span></span>  
  
- <span data-ttu-id="7471c-139">項目時使用 WS-同盟被動式 Web 應用程式中，包含設定的設定<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(WSFAM) 和<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM)。</span><span class="sxs-lookup"><span data-stu-id="7471c-139">When using WS-Federation in a passive Web application, the element contains settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span> <span data-ttu-id="7471c-140">它也會參考用來設定安全性權杖處理常式和憑證，以及元件，例如宣告授權管理員和宣告驗證管理員的身分識別組態。</span><span class="sxs-lookup"><span data-stu-id="7471c-140">It also references the identity configuration to be used to configure security token handlers and certificates, and components like the claims authorization manager and the claims authentication manager.</span></span>  
  
- <span data-ttu-id="7471c-141">使用時<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>或<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>類別提供您的程式碼中的宣告型存取控制，項目會參考的識別組態，以設定宣告授權管理員和用來進行授權的原則決策。</span><span class="sxs-lookup"><span data-stu-id="7471c-141">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the element references the identity configuration that configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="7471c-142">這是為 true，即使在不是被動的 Web 案例; 的案例比方說，Windows Communication Foundation (WCF) 應用程式或不是以 Web 為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7471c-142">This is true, even in scenarios that are not passive Web scenarios; for example, Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="7471c-143">如果應用程式不是被動的 Web 應用程式中， [ \<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md)項目 （和其子原則項目，如果有的話） 所參考的識別組態的`<federationConfiguration>`項目唯一的設定會套用。</span><span class="sxs-lookup"><span data-stu-id="7471c-143">If the application is not a passive Web application, the [\<claimsAuthorizationManager>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) element (and its child policy elements, if present) of the identity configuration referenced by the `<federationConfiguration>` element are the only settings applied.</span></span> <span data-ttu-id="7471c-144">其他所有項目都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="7471c-144">All others are ignored.</span></span>  
  
 <span data-ttu-id="7471c-145">此案例中，不論執行階段會載入預設的同盟設定。</span><span class="sxs-lookup"><span data-stu-id="7471c-145">Regardless of the scenario, the runtime loads the default federation configuration.</span></span> <span data-ttu-id="7471c-146">定義行為，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7471c-146">The behavior is defined as follows:</span></span>  
  
1. <span data-ttu-id="7471c-147">如果沒有任何`<federationConfiguration>`元素，執行階段會建立同盟設定，並填入預設值。</span><span class="sxs-lookup"><span data-stu-id="7471c-147">If there is no `<federationConfiguration>` element present, the runtime creates a federation configuration and populates it with default values.</span></span> <span data-ttu-id="7471c-148">這個預設的同盟組態會參考預設身分識別組態。</span><span class="sxs-lookup"><span data-stu-id="7471c-148">This default federation configuration will reference the default identity configuration.</span></span>  
  
2. <span data-ttu-id="7471c-149">如果單一`<federationConfiguration>`項目已存在，它是預設的同盟設定，不論它是具名或未命名的。</span><span class="sxs-lookup"><span data-stu-id="7471c-149">If a single `<federationConfiguration>` element is present, it is the default federation configuration regardless of whether it is named or unnamed.</span></span> <span data-ttu-id="7471c-150">如果其`identityConfiguration`指定屬性時，參考具名的身分識別組態，否則參考預設身分識別組態。</span><span class="sxs-lookup"><span data-stu-id="7471c-150">If its `identityConfiguration` attribute is specified, the named identity configuration is referenced; otherwise, the default identity configuration is referenced.</span></span>  
  
3. <span data-ttu-id="7471c-151">如果有未命名`<federationConfiguration>`項目已存在，它是預設的同盟設定。</span><span class="sxs-lookup"><span data-stu-id="7471c-151">If an unnamed `<federationConfiguration>` element is present, it is the default federation configuration.</span></span> <span data-ttu-id="7471c-152">如果其`identityConfiguration`指定屬性時，參考具名的身分識別組態，否則參考預設身分識別組態。</span><span class="sxs-lookup"><span data-stu-id="7471c-152">If its `identityConfiguration` attribute is specified, the named identity configuration is referenced; otherwise, the default identity configuration is referenced.</span></span>  
  
4. <span data-ttu-id="7471c-153">如果多個名為`<federationConfiguration>`項目會存在且未具名`<federationConfiguration>`項目存在，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7471c-153">If multiple named `<federationConfiguration>` elements are present and no unnamed `<federationConfiguration>` element is present, an exception is thrown.</span></span>  
  
 <span data-ttu-id="7471c-154">一般而言，只有一個`<federationConfiguration>`區段定義。</span><span class="sxs-lookup"><span data-stu-id="7471c-154">Typically, only a single `<federationConfiguration>` section is defined.</span></span> <span data-ttu-id="7471c-155">本節是預設的同盟設定。</span><span class="sxs-lookup"><span data-stu-id="7471c-155">This section is the default federation configuration.</span></span> <span data-ttu-id="7471c-156">您可以指定多個唯一命名`<federationConfiguration>`項目; 不過，在此情況下，如果您想要載入非未命名的同盟設定，您必須提供的處理常式。</span><span class="sxs-lookup"><span data-stu-id="7471c-156">You may specify multiple, uniquely-named `<federationConfiguration>` elements; however, in this case, if you want to load a federation configuration other than the unnamed one, you must provide a handler for the.</span></span> <span data-ttu-id="7471c-157"><xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated> 事件和設定<xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType>內的處理常式屬性<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>物件從適當的值初始化`<federationConfiguration>`組態檔中的項目。</span><span class="sxs-lookup"><span data-stu-id="7471c-157"><xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated> event and set the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> property inside the handler to a <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> object initialized with values from the appropriate `<federationConfiguration>` element in the configuration file.</span></span>  
  
 <span data-ttu-id="7471c-158">`<federationConfiguration>`項目由<xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement>類別。</span><span class="sxs-lookup"><span data-stu-id="7471c-158">The `<federationConfiguration>` element is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> class.</span></span> <span data-ttu-id="7471c-159">設定物件本身由<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>類別。</span><span class="sxs-lookup"><span data-stu-id="7471c-159">The configuration object itself is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> class.</span></span> <span data-ttu-id="7471c-160">單一<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>上設定執行個體<xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>屬性，並提供應用程式的同盟的設定。</span><span class="sxs-lookup"><span data-stu-id="7471c-160">A single <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> instance is set on the <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> property and provides federated configuration for the application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7471c-161">範例</span><span class="sxs-lookup"><span data-stu-id="7471c-161">Example</span></span>  
 <span data-ttu-id="7471c-162">下列 XML 會說明`<federationConfiguration>`項目，指定 WSFAM 設定，並指定預設的 cookie 處理常式 (的執行個體<xref:System.IdentityModel.Services.ChunkedCookieHandler>類別) 可供 SAM。</span><span class="sxs-lookup"><span data-stu-id="7471c-162">The following XML shows a `<federationConfiguration>` element that specifies settings for the WSFAM and specifies that the default cookie handler (an instance of the <xref:System.IdentityModel.Services.ChunkedCookieHandler> class) be used by the SAM.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="7471c-163">在此範例中，cookie 處理常式和 WSFAM 都不需要使用 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="7471c-163">In this example, neither the cookie handler nor WSFAM are required to use HTTPS.</span></span> <span data-ttu-id="7471c-164">這是因為`requireHttps`屬性`<wsFederation>`項目並`requireSsl`屬性`<cookieHandlerElement>`是`false`。</span><span class="sxs-lookup"><span data-stu-id="7471c-164">This is because the `requireHttps` attribute on the `<wsFederation>` element and the `requireSsl` attribute on the `<cookieHandlerElement>` are `false`.</span></span> <span data-ttu-id="7471c-165">因為它們可能會有安全性風險，這些設定不建議用於大部分的生產環境。</span><span class="sxs-lookup"><span data-stu-id="7471c-165">These settings are not recommended for most production environments as they may present a security risk.</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <wsFederation passiveRedirectEnabled="true"   
      issuer="http://localhost:15839/wsFederationSTS/Issue"   
      realm="http://localhost:50969/" reply="http://localhost:50969/"   
      requireHttps="false"   
      signOutReply="http://localhost:50969/SignedOutPage.html"   
      signOutQueryString="Param1=value2&Param2=value2"   
      persistentCookiesOnPassiveRedirects="true" />  
    <cookieHandler requireSsl="false" />  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7471c-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7471c-166">See also</span></span>

- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
- [<span data-ttu-id="7471c-167">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="7471c-167">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)
