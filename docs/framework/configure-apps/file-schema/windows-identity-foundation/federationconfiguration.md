---
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: 148b2f3e12fbfbf85b800f0ca7f5dc7dc1845d24
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252006"
---
# <a name="federationconfiguration"></a><span data-ttu-id="93eb9-101">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="93eb9-101">\<federationConfiguration></span></span>
<span data-ttu-id="93eb9-102">透過 WS-同盟通訊協定來<xref:System.IdentityModel.Services.SessionAuthenticationModule>使用聯合驗證時, 會設定(WSFAM)和(SAM)。<xref:System.IdentityModel.Services.WSFederationAuthenticationModule></span><span class="sxs-lookup"><span data-stu-id="93eb9-102">Configures the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) when using federated authentication through the WS-Federation protocol.</span></span> <span data-ttu-id="93eb9-103">使用或<xref:System.Security.Claims.ClaimsAuthorizationManager> 類別<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>來提供宣告型存取控制時, 設定。 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission></span><span class="sxs-lookup"><span data-stu-id="93eb9-103">Configures the <xref:System.Security.Claims.ClaimsAuthorizationManager> when using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control.</span></span>  
  
<span data-ttu-id="93eb9-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="93eb9-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="93eb9-105">&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="93eb9-105">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="93eb9-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<federationConfiguration >**</span><span class="sxs-lookup"><span data-stu-id="93eb9-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<federationConfiguration>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93eb9-107">語法</span><span class="sxs-lookup"><span data-stu-id="93eb9-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93eb9-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="93eb9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="93eb9-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="93eb9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93eb9-110">屬性</span><span class="sxs-lookup"><span data-stu-id="93eb9-110">Attributes</span></span>  
  
|<span data-ttu-id="93eb9-111">屬性</span><span class="sxs-lookup"><span data-stu-id="93eb9-111">Attribute</span></span>|<span data-ttu-id="93eb9-112">描述</span><span class="sxs-lookup"><span data-stu-id="93eb9-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="93eb9-113">NAME</span><span class="sxs-lookup"><span data-stu-id="93eb9-113">name</span></span>|<span data-ttu-id="93eb9-114">此同盟設定元素的名稱。</span><span class="sxs-lookup"><span data-stu-id="93eb9-114">The name of this federation configuration element.</span></span> <span data-ttu-id="93eb9-115">這個屬性主要是針對未來的通訊協定提供擴充點。</span><span class="sxs-lookup"><span data-stu-id="93eb9-115">This attribute primarily provides an extensibility point for future protocols.</span></span> <span data-ttu-id="93eb9-116">選擇性。</span><span class="sxs-lookup"><span data-stu-id="93eb9-116">Optional.</span></span>|  
|<span data-ttu-id="93eb9-117">identityConfigurationName</span><span class="sxs-lookup"><span data-stu-id="93eb9-117">identityConfigurationName</span></span>|<span data-ttu-id="93eb9-118">要使用之[ \<identityConfiguration >](identityconfiguration.md)專案中所指定的身分識別設定區段的名稱。</span><span class="sxs-lookup"><span data-stu-id="93eb9-118">The name of the identity configuration section as specified in an [\<identityConfiguration>](identityconfiguration.md) element to use.</span></span> <span data-ttu-id="93eb9-119">如果未指定此屬性, 則會使用預設的身分識別設定區段。</span><span class="sxs-lookup"><span data-stu-id="93eb9-119">If this attribute is not specified, the default identity configuration section is used.</span></span> <span data-ttu-id="93eb9-120">選擇性。</span><span class="sxs-lookup"><span data-stu-id="93eb9-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="93eb9-121">子元素</span><span class="sxs-lookup"><span data-stu-id="93eb9-121">Child Elements</span></span>  
  
|<span data-ttu-id="93eb9-122">項目</span><span class="sxs-lookup"><span data-stu-id="93eb9-122">Element</span></span>|<span data-ttu-id="93eb9-123">描述</span><span class="sxs-lookup"><span data-stu-id="93eb9-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93eb9-124">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="93eb9-124">\<cookieHandler></span></span>](cookiehandler.md)|<span data-ttu-id="93eb9-125">設定 SAM 所使用的 cookie 處理常式。</span><span class="sxs-lookup"><span data-stu-id="93eb9-125">Configures the cookie handler used by the SAM.</span></span> <span data-ttu-id="93eb9-126">選擇性。</span><span class="sxs-lookup"><span data-stu-id="93eb9-126">Optional.</span></span>|  
|[<span data-ttu-id="93eb9-127">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="93eb9-127">\<serviceCertificate></span></span>](servicecertificate.md)|<span data-ttu-id="93eb9-128">設定用來加密和解密權杖的憑證。</span><span class="sxs-lookup"><span data-stu-id="93eb9-128">Configures the certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="93eb9-129">選擇性。</span><span class="sxs-lookup"><span data-stu-id="93eb9-129">Optional.</span></span>|  
|[<span data-ttu-id="93eb9-130">\<wsFederation></span><span class="sxs-lookup"><span data-stu-id="93eb9-130">\<wsFederation></span></span>](wsfederation.md)|<span data-ttu-id="93eb9-131">設定 WS-同盟驗證模組 (WSFAM)。</span><span class="sxs-lookup"><span data-stu-id="93eb9-131">Configures the WS-Federation Authentication Module (WSFAM).</span></span> <span data-ttu-id="93eb9-132">選擇性。</span><span class="sxs-lookup"><span data-stu-id="93eb9-132">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="93eb9-133">父項目</span><span class="sxs-lookup"><span data-stu-id="93eb9-133">Parent Elements</span></span>  
  
|<span data-ttu-id="93eb9-134">項目</span><span class="sxs-lookup"><span data-stu-id="93eb9-134">Element</span></span>|<span data-ttu-id="93eb9-135">描述</span><span class="sxs-lookup"><span data-stu-id="93eb9-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93eb9-136">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="93eb9-136">\<system.identityModel.services></span></span>](system-identitymodel-services.md)|<span data-ttu-id="93eb9-137">使用 WS-同盟通訊協定進行驗證的設定區段。</span><span class="sxs-lookup"><span data-stu-id="93eb9-137">Configuration section for authentication using the WS-Federation protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93eb9-138">備註</span><span class="sxs-lookup"><span data-stu-id="93eb9-138">Remarks</span></span>  
 <span data-ttu-id="93eb9-139">\<FederationConfiguration > 元素會在兩個不同的案例中提供設定:</span><span class="sxs-lookup"><span data-stu-id="93eb9-139">The \<federationConfiguration> element provides settings in two different scenarios:</span></span>  
  
- <span data-ttu-id="93eb9-140">在被動 Web 應用程式中使用 WS-同盟時, 元素會<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>包含設定 (WSFAM) <xref:System.IdentityModel.Services.SessionAuthenticationModule>和 (SAM) 的設定。</span><span class="sxs-lookup"><span data-stu-id="93eb9-140">When using WS-Federation in a passive Web application, the element contains settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span> <span data-ttu-id="93eb9-141">它也會參考要用來設定安全性權杖處理常式和憑證的身分識別設定, 以及宣告授權管理員和宣告驗證管理員等元件。</span><span class="sxs-lookup"><span data-stu-id="93eb9-141">It also references the identity configuration to be used to configure security token handlers and certificates, and components like the claims authorization manager and the claims authentication manager.</span></span>  
  
- <span data-ttu-id="93eb9-142">當使用<xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>或類別在您的程式碼中提供宣告型存取控制時, 元素會參考身分設定, 以設定宣告授權管理員和用來進行授權的原則。決策.</span><span class="sxs-lookup"><span data-stu-id="93eb9-142">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the element references the identity configuration that configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="93eb9-143">即使在不是被動 Web 案例的情況下, 也是如此。例如, Windows Communication Foundation (WCF) 應用程式或不是以 Web 為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="93eb9-143">This is true, even in scenarios that are not passive Web scenarios; for example, Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="93eb9-144">如果應用程式不是被動 Web 應用程式, `<federationConfiguration>` [ \<](claimsauthorizationmanager.md)則專案所參考之身分識別設定的 claimsAuthorizationManager > 專案 (及其子原則元素, 如果有的話) 是唯一的設定套用.</span><span class="sxs-lookup"><span data-stu-id="93eb9-144">If the application is not a passive Web application, the [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) element (and its child policy elements, if present) of the identity configuration referenced by the `<federationConfiguration>` element are the only settings applied.</span></span> <span data-ttu-id="93eb9-145">其他所有項目都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="93eb9-145">All others are ignored.</span></span>  
  
 <span data-ttu-id="93eb9-146">不論是哪一種情況, 執行時間都會載入預設的同盟設定。</span><span class="sxs-lookup"><span data-stu-id="93eb9-146">Regardless of the scenario, the runtime loads the default federation configuration.</span></span> <span data-ttu-id="93eb9-147">其行為定義如下:</span><span class="sxs-lookup"><span data-stu-id="93eb9-147">The behavior is defined as follows:</span></span>  
  
1. <span data-ttu-id="93eb9-148">如果沒有專案, `<federationConfiguration>`執行時間會建立同盟設定, 並以預設值填入該設定。</span><span class="sxs-lookup"><span data-stu-id="93eb9-148">If there is no `<federationConfiguration>` element present, the runtime creates a federation configuration and populates it with default values.</span></span> <span data-ttu-id="93eb9-149">此預設同盟設定會參考預設的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="93eb9-149">This default federation configuration will reference the default identity configuration.</span></span>  
  
2. <span data-ttu-id="93eb9-150">如果單一`<federationConfiguration>`專案存在, 則它是預設的同盟設定, 不論其名稱為或未命名。</span><span class="sxs-lookup"><span data-stu-id="93eb9-150">If a single `<federationConfiguration>` element is present, it is the default federation configuration regardless of whether it is named or unnamed.</span></span> <span data-ttu-id="93eb9-151">如果指定`identityConfiguration`了它的屬性, 就會參考指定的身分識別設定, 否則會參考預設的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="93eb9-151">If its `identityConfiguration` attribute is specified, the named identity configuration is referenced; otherwise, the default identity configuration is referenced.</span></span>  
  
3. <span data-ttu-id="93eb9-152">如果未命名`<federationConfiguration>`的元素存在, 則為預設的同盟設定。</span><span class="sxs-lookup"><span data-stu-id="93eb9-152">If an unnamed `<federationConfiguration>` element is present, it is the default federation configuration.</span></span> <span data-ttu-id="93eb9-153">如果指定`identityConfiguration`了它的屬性, 就會參考指定的身分識別設定, 否則會參考預設的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="93eb9-153">If its `identityConfiguration` attribute is specified, the named identity configuration is referenced; otherwise, the default identity configuration is referenced.</span></span>  
  
4. <span data-ttu-id="93eb9-154">如果有多`<federationConfiguration>`個已命名的專案, `<federationConfiguration>`而且沒有任何未命名的元素存在, 則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="93eb9-154">If multiple named `<federationConfiguration>` elements are present and no unnamed `<federationConfiguration>` element is present, an exception is thrown.</span></span>  
  
 <span data-ttu-id="93eb9-155">通常只會定義單一`<federationConfiguration>`區段。</span><span class="sxs-lookup"><span data-stu-id="93eb9-155">Typically, only a single `<federationConfiguration>` section is defined.</span></span> <span data-ttu-id="93eb9-156">此區段是預設的同盟設定。</span><span class="sxs-lookup"><span data-stu-id="93eb9-156">This section is the default federation configuration.</span></span> <span data-ttu-id="93eb9-157">您可以指定多個以唯一命名`<federationConfiguration>`的專案; 不過, 在此情況下, 如果您想要載入未命名的同盟設定, 則必須提供的處理常式。</span><span class="sxs-lookup"><span data-stu-id="93eb9-157">You may specify multiple, uniquely-named `<federationConfiguration>` elements; however, in this case, if you want to load a federation configuration other than the unnamed one, you must provide a handler for the.</span></span> <span data-ttu-id="93eb9-158"><xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated>事件, 並將<xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType>處理常式內的屬性設定<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>為使用設定檔中適當`<federationConfiguration>`專案的值來初始化的物件。</span><span class="sxs-lookup"><span data-stu-id="93eb9-158"><xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated> event and set the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> property inside the handler to a <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> object initialized with values from the appropriate `<federationConfiguration>` element in the configuration file.</span></span>  
  
 <span data-ttu-id="93eb9-159">`<federationConfiguration>`元素是<xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement>由類別表示。</span><span class="sxs-lookup"><span data-stu-id="93eb9-159">The `<federationConfiguration>` element is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> class.</span></span> <span data-ttu-id="93eb9-160">設定物件本身是以<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>類別表示。</span><span class="sxs-lookup"><span data-stu-id="93eb9-160">The configuration object itself is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> class.</span></span> <span data-ttu-id="93eb9-161">在<xref:System.IdentityModel.Services.Configuration.FederationConfiguration> 屬性<xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>上設定單一實例, 並提供應用程式的同盟設定。</span><span class="sxs-lookup"><span data-stu-id="93eb9-161">A single <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> instance is set on the <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> property and provides federated configuration for the application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93eb9-162">範例</span><span class="sxs-lookup"><span data-stu-id="93eb9-162">Example</span></span>  
 <span data-ttu-id="93eb9-163">下列 XML 顯示`<federationConfiguration>`的元素會指定 WSFAM 的設定, 並指定 SAM 使用預設的 cookie 處理常式 ( <xref:System.IdentityModel.Services.ChunkedCookieHandler>類別的實例)。</span><span class="sxs-lookup"><span data-stu-id="93eb9-163">The following XML shows a `<federationConfiguration>` element that specifies settings for the WSFAM and specifies that the default cookie handler (an instance of the <xref:System.IdentityModel.Services.ChunkedCookieHandler> class) be used by the SAM.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="93eb9-164">在此範例中, cookie 處理常式或 WSFAM 都不需要使用 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="93eb9-164">In this example, neither the cookie handler nor WSFAM are required to use HTTPS.</span></span> <span data-ttu-id="93eb9-165">`requireHttps`這是因為`false` `<cookieHandlerElement>` `requireSsl`元素上的屬性和上的屬性為。 `<wsFederation>`</span><span class="sxs-lookup"><span data-stu-id="93eb9-165">This is because the `requireHttps` attribute on the `<wsFederation>` element and the `requireSsl` attribute on the `<cookieHandlerElement>` are `false`.</span></span> <span data-ttu-id="93eb9-166">在大部分的生產環境中, 不建議使用這些設定, 因為它們可能會有安全性風險。</span><span class="sxs-lookup"><span data-stu-id="93eb9-166">These settings are not recommended for most production environments as they may present a security risk.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="93eb9-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93eb9-167">See also</span></span>

- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
- [<span data-ttu-id="93eb9-168">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="93eb9-168">\<identityConfiguration></span></span>](identityconfiguration.md)
