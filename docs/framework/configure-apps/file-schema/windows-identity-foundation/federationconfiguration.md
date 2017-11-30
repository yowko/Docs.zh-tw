---
title: '&lt;federationConfiguration&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 9abe07c065dbea67c5ebc4a4490d9f88258130c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltfederationconfigurationgt"></a><span data-ttu-id="92888-102">&lt;federationConfiguration&gt;</span><span class="sxs-lookup"><span data-stu-id="92888-102">&lt;federationConfiguration&gt;</span></span>
<span data-ttu-id="92888-103">設定<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(WSFAM) 和<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM) 時使用同盟驗證透過 WS-同盟通訊協定。</span><span class="sxs-lookup"><span data-stu-id="92888-103">Configures the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) when using federated authentication through the WS-Federation protocol.</span></span> <span data-ttu-id="92888-104">設定<xref:System.Security.Claims.ClaimsAuthorizationManager>時使用<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>或<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>類別提供的宣告型存取控制。</span><span class="sxs-lookup"><span data-stu-id="92888-104">Configures the <xref:System.Security.Claims.ClaimsAuthorizationManager> when using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control.</span></span>  
  
 <span data-ttu-id="92888-105">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="92888-105">\<system.identityModel.services></span></span>  
<span data-ttu-id="92888-106">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="92888-106">\<federationConfiguration></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92888-107">語法</span><span class="sxs-lookup"><span data-stu-id="92888-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92888-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="92888-108">Attributes and Elements</span></span>  
 <span data-ttu-id="92888-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="92888-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92888-110">屬性</span><span class="sxs-lookup"><span data-stu-id="92888-110">Attributes</span></span>  
  
|<span data-ttu-id="92888-111">屬性</span><span class="sxs-lookup"><span data-stu-id="92888-111">Attribute</span></span>|<span data-ttu-id="92888-112">描述</span><span class="sxs-lookup"><span data-stu-id="92888-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="92888-113">name</span><span class="sxs-lookup"><span data-stu-id="92888-113">name</span></span>|<span data-ttu-id="92888-114">這個同盟的組態項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="92888-114">The name of this federation configuration element.</span></span> <span data-ttu-id="92888-115">這個屬性主要是提供的擴充點，未來的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="92888-115">This attribute primarily provides an extensibility point for future protocols.</span></span> <span data-ttu-id="92888-116">選擇項。</span><span class="sxs-lookup"><span data-stu-id="92888-116">Optional.</span></span>|  
|<span data-ttu-id="92888-117">identityConfigurationName</span><span class="sxs-lookup"><span data-stu-id="92888-117">identityConfigurationName</span></span>|<span data-ttu-id="92888-118">中所指定的身分識別組態區段名稱[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)来使用項目。</span><span class="sxs-lookup"><span data-stu-id="92888-118">The name of the identity configuration section as specified in an [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element to use.</span></span> <span data-ttu-id="92888-119">如果未指定此屬性，則會使用預設身分識別組態區段。</span><span class="sxs-lookup"><span data-stu-id="92888-119">If this attribute is not specified, the default identity configuration section is used.</span></span> <span data-ttu-id="92888-120">選擇項。</span><span class="sxs-lookup"><span data-stu-id="92888-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="92888-121">子元素</span><span class="sxs-lookup"><span data-stu-id="92888-121">Child Elements</span></span>  
  
|<span data-ttu-id="92888-122">項目</span><span class="sxs-lookup"><span data-stu-id="92888-122">Element</span></span>|<span data-ttu-id="92888-123">說明</span><span class="sxs-lookup"><span data-stu-id="92888-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="92888-124">\<Requiressl ></span><span class="sxs-lookup"><span data-stu-id="92888-124">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="92888-125">設定 SAM 所使用的 cookie 處理常式。</span><span class="sxs-lookup"><span data-stu-id="92888-125">Configures the cookie handler used by the SAM.</span></span> <span data-ttu-id="92888-126">選擇項。</span><span class="sxs-lookup"><span data-stu-id="92888-126">Optional.</span></span>|  
|[<span data-ttu-id="92888-127">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="92888-127">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|<span data-ttu-id="92888-128">設定用來加密和解密權杖的憑證。</span><span class="sxs-lookup"><span data-stu-id="92888-128">Configures the certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="92888-129">選擇項。</span><span class="sxs-lookup"><span data-stu-id="92888-129">Optional.</span></span>|  
|[<span data-ttu-id="92888-130">\<wsFederation ></span><span class="sxs-lookup"><span data-stu-id="92888-130">\<wsFederation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation.md)|<span data-ttu-id="92888-131">設定 WS-同盟驗證模組 (WSFAM)。</span><span class="sxs-lookup"><span data-stu-id="92888-131">Configures the WS-Federation Authentication Module (WSFAM).</span></span> <span data-ttu-id="92888-132">選擇項。</span><span class="sxs-lookup"><span data-stu-id="92888-132">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="92888-133">父項目</span><span class="sxs-lookup"><span data-stu-id="92888-133">Parent Elements</span></span>  
  
|<span data-ttu-id="92888-134">項目</span><span class="sxs-lookup"><span data-stu-id="92888-134">Element</span></span>|<span data-ttu-id="92888-135">說明</span><span class="sxs-lookup"><span data-stu-id="92888-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="92888-136">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="92888-136">\<system.identityModel.services></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)|<span data-ttu-id="92888-137">使用 WS-同盟通訊協定進行驗證的組態區段。</span><span class="sxs-lookup"><span data-stu-id="92888-137">Configuration section for authentication using the WS-Federation protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92888-138">備註</span><span class="sxs-lookup"><span data-stu-id="92888-138">Remarks</span></span>  
 <span data-ttu-id="92888-139">\<FederationConfiguration > 項目會提供兩個不同的案例中的設定：</span><span class="sxs-lookup"><span data-stu-id="92888-139">The \<federationConfiguration> element provides settings in two different scenarios:</span></span>  
  
-   <span data-ttu-id="92888-140">項目時使用 WS-同盟被動式 Web 應用程式中，包含設定的設定<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(WSFAM) 和<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM)。</span><span class="sxs-lookup"><span data-stu-id="92888-140">When using WS-Federation in a passive Web application, the element contains settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span> <span data-ttu-id="92888-141">它也會參考要用來設定安全性權杖處理常式和憑證，以及元件，例如 claims authorization manager 授權和宣告驗證管理員的身分識別組態。</span><span class="sxs-lookup"><span data-stu-id="92888-141">It also references the identity configuration to be used to configure security token handlers and certificates, and components like the claims authorization manager and the claims authentication manager.</span></span>  
  
-   <span data-ttu-id="92888-142">當使用<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>或<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>類別提供您的程式碼中的宣告型存取控制，項目會參考識別組態，以設定 claims authorization manager 授權和用來進行授權原則決策。</span><span class="sxs-lookup"><span data-stu-id="92888-142">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the element references the identity configuration that configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="92888-143">這是為 true，即使在情況不是被動 Web 案例。例如，Windows Communication Foundation (WCF) 應用程式或不是以 Web 為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="92888-143">This is true, even in scenarios that are not passive Web scenarios; for example, Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="92888-144">如果應用程式不是被動的 Web 應用程式， [ \<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md)元素 （和其子原則項目，如果有的話） 所參考的身分識別組態`<federationConfiguration>`項目只有設定會套用。</span><span class="sxs-lookup"><span data-stu-id="92888-144">If the application is not a passive Web application, the [\<claimsAuthorizationManager>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) element (and its child policy elements, if present) of the identity configuration referenced by the `<federationConfiguration>` element are the only settings applied.</span></span> <span data-ttu-id="92888-145">其他所有項目都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="92888-145">All others are ignored.</span></span>  
  
 <span data-ttu-id="92888-146">不論案例中，執行階段會載入預設的同盟設定。</span><span class="sxs-lookup"><span data-stu-id="92888-146">Regardless of the scenario, the runtime loads the default federation configuration.</span></span> <span data-ttu-id="92888-147">行為定義，如下所示：</span><span class="sxs-lookup"><span data-stu-id="92888-147">The behavior is defined as follows:</span></span>  
  
1.  <span data-ttu-id="92888-148">如果沒有任何`<federationConfiguration>`存在的項目，執行階段建立同盟設定，並填入預設值。</span><span class="sxs-lookup"><span data-stu-id="92888-148">If there is no `<federationConfiguration>` element present, the runtime creates a federation configuration and populates it with default values.</span></span> <span data-ttu-id="92888-149">這個預設同盟組態會參考預設身分識別組態。</span><span class="sxs-lookup"><span data-stu-id="92888-149">This default federation configuration will reference the default identity configuration.</span></span>  
  
2.  <span data-ttu-id="92888-150">如果單一`<federationConfiguration>`元素存在，它是預設的同盟設定，無論它是具名或未命名的。</span><span class="sxs-lookup"><span data-stu-id="92888-150">If a single `<federationConfiguration>` element is present, it is the default federation configuration regardless of whether it is named or unnamed.</span></span> <span data-ttu-id="92888-151">如果其`identityConfiguration`指定屬性時，參考具名的身分識別組態; 否則參照預設身分識別組態。</span><span class="sxs-lookup"><span data-stu-id="92888-151">If its `identityConfiguration` attribute is specified, the named identity configuration is referenced; otherwise, the default identity configuration is referenced.</span></span>  
  
3.  <span data-ttu-id="92888-152">如果有未命名`<federationConfiguration>`元素存在，它是預設的同盟設定。</span><span class="sxs-lookup"><span data-stu-id="92888-152">If an unnamed `<federationConfiguration>` element is present, it is the default federation configuration.</span></span> <span data-ttu-id="92888-153">如果其`identityConfiguration`指定屬性時，參考具名的身分識別組態; 否則參照預設身分識別組態。</span><span class="sxs-lookup"><span data-stu-id="92888-153">If its `identityConfiguration` attribute is specified, the named identity configuration is referenced; otherwise, the default identity configuration is referenced.</span></span>  
  
4.  <span data-ttu-id="92888-154">如果多個名為`<federationConfiguration>`項目確實存在且未具名`<federationConfiguration>`元素存在，擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="92888-154">If multiple named `<federationConfiguration>` elements are present and no unnamed `<federationConfiguration>` element is present, an exception is thrown.</span></span>  
  
 <span data-ttu-id="92888-155">一般而言，只有一個`<federationConfiguration>`區段定義。</span><span class="sxs-lookup"><span data-stu-id="92888-155">Typically, only a single `<federationConfiguration>` section is defined.</span></span> <span data-ttu-id="92888-156">此區段是預設的同盟設定。</span><span class="sxs-lookup"><span data-stu-id="92888-156">This section is the default federation configuration.</span></span> <span data-ttu-id="92888-157">您可以指定多個唯一命名`<federationConfiguration>`項目; 不過，在此情況下，如果您想要載入同盟設定未命名的以外，您必須提供的處理常式。</span><span class="sxs-lookup"><span data-stu-id="92888-157">You may specify multiple, uniquely-named `<federationConfiguration>` elements; however, in this case, if you want to load a federation configuration other than the unnamed one, you must provide a handler for the.</span></span> <span data-ttu-id="92888-158"><xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated>事件和組<xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType>屬性來處理常式內部<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>物件從適當的值初始化`<federationConfiguration>`組態檔中的項目。</span><span class="sxs-lookup"><span data-stu-id="92888-158"><xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated> event and set the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> property inside the handler to a <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> object initialized with values from the appropriate `<federationConfiguration>` element in the configuration file.</span></span>  
  
 <span data-ttu-id="92888-159">`<federationConfiguration>`項目由<xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement>類別。</span><span class="sxs-lookup"><span data-stu-id="92888-159">The `<federationConfiguration>` element is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> class.</span></span> <span data-ttu-id="92888-160">組態物件本身由<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>類別。</span><span class="sxs-lookup"><span data-stu-id="92888-160">The configuration object itself is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> class.</span></span> <span data-ttu-id="92888-161">單一<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>執行個體上設定<xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>屬性，並提供應用程式的同盟的設定。</span><span class="sxs-lookup"><span data-stu-id="92888-161">A single <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> instance is set on the <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> property and provides federated configuration for the application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92888-162">範例</span><span class="sxs-lookup"><span data-stu-id="92888-162">Example</span></span>  
 <span data-ttu-id="92888-163">下列 XML 會說明`<federationConfiguration>`項目，指定 WSFAM 設定，並指定預設 cookie 處理常式 (執行個體<xref:System.IdentityModel.Services.ChunkedCookieHandler>類別) 可供 SAM。</span><span class="sxs-lookup"><span data-stu-id="92888-163">The following XML shows a `<federationConfiguration>` element that specifies settings for the WSFAM and specifies that the default cookie handler (an instance of the <xref:System.IdentityModel.Services.ChunkedCookieHandler> class) be used by the SAM.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="92888-164">在此範例中，cookie 處理常式或 WSFAM 都不需要使用 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="92888-164">In this example, neither the cookie handler nor WSFAM are required to use HTTPS.</span></span> <span data-ttu-id="92888-165">這是因為`requireHttps`屬性`<wsFederation>`項目和`requireSsl`屬性`<cookieHandlerElement>`是`false`。</span><span class="sxs-lookup"><span data-stu-id="92888-165">This is because the `requireHttps` attribute on the `<wsFederation>` element and the `requireSsl` attribute on the `<cookieHandlerElement>` are `false`.</span></span> <span data-ttu-id="92888-166">因為它們可能會有安全性風險，這些設定不建議用於大部分的實際執行環境。</span><span class="sxs-lookup"><span data-stu-id="92888-166">These settings are not recommended for most production environments as they may present a security risk.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="92888-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92888-167">See Also</span></span>  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>  
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>  
 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="92888-168">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="92888-168">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)
