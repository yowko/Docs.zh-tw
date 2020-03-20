---
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: bcd8e00b770517e3faff011b4acee08ebdc5a0df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152732"
---
# <a name="federationconfiguration"></a><span data-ttu-id="edcaf-101">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="edcaf-101">\<federationConfiguration></span></span>
<span data-ttu-id="edcaf-102">通過 WS-聯合協定使用識別身分同盟時配置<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>（WSFAM） 和<xref:System.IdentityModel.Services.SessionAuthenticationModule>（SAM）。</span><span class="sxs-lookup"><span data-stu-id="edcaf-102">Configures the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) when using federated authentication through the WS-Federation protocol.</span></span> <span data-ttu-id="edcaf-103">配置<xref:System.Security.Claims.ClaimsAuthorizationManager>使用<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>或<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>類時提供基於聲明的存取控制。</span><span class="sxs-lookup"><span data-stu-id="edcaf-103">Configures the <xref:System.Security.Claims.ClaimsAuthorizationManager> when using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control.</span></span>  
  
<span data-ttu-id="edcaf-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="edcaf-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="edcaf-105">&nbsp;&nbsp;[**\<系統.身份模型.服務>**](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="edcaf-105">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="edcaf-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<聯合配置>**</span><span class="sxs-lookup"><span data-stu-id="edcaf-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<federationConfiguration>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edcaf-107">語法</span><span class="sxs-lookup"><span data-stu-id="edcaf-107">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="edcaf-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="edcaf-108">Attributes and Elements</span></span>  
 <span data-ttu-id="edcaf-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="edcaf-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="edcaf-110">屬性</span><span class="sxs-lookup"><span data-stu-id="edcaf-110">Attributes</span></span>  
  
|<span data-ttu-id="edcaf-111">屬性</span><span class="sxs-lookup"><span data-stu-id="edcaf-111">Attribute</span></span>|<span data-ttu-id="edcaf-112">描述</span><span class="sxs-lookup"><span data-stu-id="edcaf-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="edcaf-113">NAME</span><span class="sxs-lookup"><span data-stu-id="edcaf-113">name</span></span>|<span data-ttu-id="edcaf-114">這個聯合組態項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="edcaf-114">The name of this federation configuration element.</span></span> <span data-ttu-id="edcaf-115">此屬性主要為未來的協定提供擴充點。</span><span class="sxs-lookup"><span data-stu-id="edcaf-115">This attribute primarily provides an extensibility point for future protocols.</span></span> <span data-ttu-id="edcaf-116">選擇性。</span><span class="sxs-lookup"><span data-stu-id="edcaf-116">Optional.</span></span>|  
|<span data-ttu-id="edcaf-117">標識配置名稱</span><span class="sxs-lookup"><span data-stu-id="edcaf-117">identityConfigurationName</span></span>|<span data-ttu-id="edcaf-118">標識配置中指定的標識配置部分的名稱>要使用的元素。 [ \< ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="edcaf-118">The name of the identity configuration section as specified in an [\<identityConfiguration>](identityconfiguration.md) element to use.</span></span> <span data-ttu-id="edcaf-119">如果未指定此屬性，則使用預設標識配置部分。</span><span class="sxs-lookup"><span data-stu-id="edcaf-119">If this attribute is not specified, the default identity configuration section is used.</span></span> <span data-ttu-id="edcaf-120">選擇性。</span><span class="sxs-lookup"><span data-stu-id="edcaf-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="edcaf-121">子元素</span><span class="sxs-lookup"><span data-stu-id="edcaf-121">Child Elements</span></span>  
  
|<span data-ttu-id="edcaf-122">元素</span><span class="sxs-lookup"><span data-stu-id="edcaf-122">Element</span></span>|<span data-ttu-id="edcaf-123">描述</span><span class="sxs-lookup"><span data-stu-id="edcaf-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="edcaf-124">\<餅乾漢德勒></span><span class="sxs-lookup"><span data-stu-id="edcaf-124">\<cookieHandler></span></span>](cookiehandler.md)|<span data-ttu-id="edcaf-125">配置 SAM 使用的 Cookie 處理常式。</span><span class="sxs-lookup"><span data-stu-id="edcaf-125">Configures the cookie handler used by the SAM.</span></span> <span data-ttu-id="edcaf-126">選擇性。</span><span class="sxs-lookup"><span data-stu-id="edcaf-126">Optional.</span></span>|  
|[<span data-ttu-id="edcaf-127">\<服務證書></span><span class="sxs-lookup"><span data-stu-id="edcaf-127">\<serviceCertificate></span></span>](servicecertificate.md)|<span data-ttu-id="edcaf-128">配置用於加密和解密權杖的證書。</span><span class="sxs-lookup"><span data-stu-id="edcaf-128">Configures the certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="edcaf-129">選擇性。</span><span class="sxs-lookup"><span data-stu-id="edcaf-129">Optional.</span></span>|  
|[<span data-ttu-id="edcaf-130">\<ws聯邦></span><span class="sxs-lookup"><span data-stu-id="edcaf-130">\<wsFederation></span></span>](wsfederation.md)|<span data-ttu-id="edcaf-131">配置 WS-識別身分同盟模組 （WSFAM）。</span><span class="sxs-lookup"><span data-stu-id="edcaf-131">Configures the WS-Federation Authentication Module (WSFAM).</span></span> <span data-ttu-id="edcaf-132">選擇性。</span><span class="sxs-lookup"><span data-stu-id="edcaf-132">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="edcaf-133">父項目</span><span class="sxs-lookup"><span data-stu-id="edcaf-133">Parent Elements</span></span>  
  
|<span data-ttu-id="edcaf-134">元素</span><span class="sxs-lookup"><span data-stu-id="edcaf-134">Element</span></span>|<span data-ttu-id="edcaf-135">描述</span><span class="sxs-lookup"><span data-stu-id="edcaf-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="edcaf-136">\<系統.身份模型.服務></span><span class="sxs-lookup"><span data-stu-id="edcaf-136">\<system.identityModel.services></span></span>](system-identitymodel-services.md)|<span data-ttu-id="edcaf-137">使用 WS-聯合協定進行身份驗證的配置部分。</span><span class="sxs-lookup"><span data-stu-id="edcaf-137">Configuration section for authentication using the WS-Federation protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="edcaf-138">備註</span><span class="sxs-lookup"><span data-stu-id="edcaf-138">Remarks</span></span>  
 <span data-ttu-id="edcaf-139">聯合\<配置>元素在兩種不同的方案中提供設置：</span><span class="sxs-lookup"><span data-stu-id="edcaf-139">The \<federationConfiguration> element provides settings in two different scenarios:</span></span>  
  
- <span data-ttu-id="edcaf-140">在被動 Web 應用程式中使用 WS-聯合時，元素包含配置<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>（WSFAM） 和 （SAM） 的<xref:System.IdentityModel.Services.SessionAuthenticationModule>設置。</span><span class="sxs-lookup"><span data-stu-id="edcaf-140">When using WS-Federation in a passive Web application, the element contains settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span> <span data-ttu-id="edcaf-141">它還引用用於配置安全權杖處理常式和證書的標識配置，以及聲明授權管理員和聲明身份驗證管理器等元件。</span><span class="sxs-lookup"><span data-stu-id="edcaf-141">It also references the identity configuration to be used to configure security token handlers and certificates, and components like the claims authorization manager and the claims authentication manager.</span></span>  
  
- <span data-ttu-id="edcaf-142">當使用<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>或<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>類在代碼中提供基於聲明的存取控制時，元素引用標識配置，該配置用於做出授權決策的聲明授權管理員和策略。</span><span class="sxs-lookup"><span data-stu-id="edcaf-142">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the element references the identity configuration that configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="edcaf-143">這是事實，即使在不是被動 Web 方案的情況下也是如此;例如，Windows 通信基礎 （WCF） 應用程式或非基於 Web 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="edcaf-143">This is true, even in scenarios that are not passive Web scenarios; for example, Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="edcaf-144">如果應用程式不是被動 Web 應用程式，則`<federationConfiguration>`該元素引用的標識配置[\<的聲明授權管理員>](claimsauthorizationmanager.md)元素（及其子策略元素（如果存在）是應用的唯一設置。</span><span class="sxs-lookup"><span data-stu-id="edcaf-144">If the application is not a passive Web application, the [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) element (and its child policy elements, if present) of the identity configuration referenced by the `<federationConfiguration>` element are the only settings applied.</span></span> <span data-ttu-id="edcaf-145">其他所有項目都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="edcaf-145">All others are ignored.</span></span>  
  
 <span data-ttu-id="edcaf-146">無論方案如何，運行時都會載入預設識別身分同盟配置。</span><span class="sxs-lookup"><span data-stu-id="edcaf-146">Regardless of the scenario, the runtime loads the default federation configuration.</span></span> <span data-ttu-id="edcaf-147">行為的定義如下：</span><span class="sxs-lookup"><span data-stu-id="edcaf-147">The behavior is defined as follows:</span></span>  
  
1. <span data-ttu-id="edcaf-148">如果沒有`<federationConfiguration>`元素存在，運行時將創建聯合配置，並將其填充為預設值。</span><span class="sxs-lookup"><span data-stu-id="edcaf-148">If there is no `<federationConfiguration>` element present, the runtime creates a federation configuration and populates it with default values.</span></span> <span data-ttu-id="edcaf-149">此預設識別身分同盟配置將引用預設標識配置。</span><span class="sxs-lookup"><span data-stu-id="edcaf-149">This default federation configuration will reference the default identity configuration.</span></span>  
  
2. <span data-ttu-id="edcaf-150">如果存在單個`<federationConfiguration>`元素，則無論它是命名還是未命名，它都是預設的聯合配置。</span><span class="sxs-lookup"><span data-stu-id="edcaf-150">If a single `<federationConfiguration>` element is present, it is the default federation configuration regardless of whether it is named or unnamed.</span></span> <span data-ttu-id="edcaf-151">如果指定`identityConfiguration`了其屬性，則引用命名標識配置;如果指定標識配置被引用。否則，將引用預設標識配置。</span><span class="sxs-lookup"><span data-stu-id="edcaf-151">If its `identityConfiguration` attribute is specified, the named identity configuration is referenced; otherwise, the default identity configuration is referenced.</span></span>  
  
3. <span data-ttu-id="edcaf-152">如果存在未命名的`<federationConfiguration>`元素，則它是預設的聯合配置。</span><span class="sxs-lookup"><span data-stu-id="edcaf-152">If an unnamed `<federationConfiguration>` element is present, it is the default federation configuration.</span></span> <span data-ttu-id="edcaf-153">如果指定`identityConfiguration`了其屬性，則引用命名標識配置;如果指定標識配置被引用。否則，將引用預設標識配置。</span><span class="sxs-lookup"><span data-stu-id="edcaf-153">If its `identityConfiguration` attribute is specified, the named identity configuration is referenced; otherwise, the default identity configuration is referenced.</span></span>  
  
4. <span data-ttu-id="edcaf-154">如果存在多個命名`<federationConfiguration>`元素，並且不存在未命名`<federationConfiguration>`元素，則引發異常。</span><span class="sxs-lookup"><span data-stu-id="edcaf-154">If multiple named `<federationConfiguration>` elements are present and no unnamed `<federationConfiguration>` element is present, an exception is thrown.</span></span>  
  
 <span data-ttu-id="edcaf-155">通常，只定義單個`<federationConfiguration>`節。</span><span class="sxs-lookup"><span data-stu-id="edcaf-155">Typically, only a single `<federationConfiguration>` section is defined.</span></span> <span data-ttu-id="edcaf-156">此部分是預設聯合配置。</span><span class="sxs-lookup"><span data-stu-id="edcaf-156">This section is the default federation configuration.</span></span> <span data-ttu-id="edcaf-157">您可以指定多個唯一命名的元素;`<federationConfiguration>`但是，您可以指定多個唯一命名的元素。但是，在這種情況下，如果要載入非命名配置以外的聯合配置，則必須為 提供處理常式。</span><span class="sxs-lookup"><span data-stu-id="edcaf-157">You may specify multiple, uniquely-named `<federationConfiguration>` elements; however, in this case, if you want to load a federation configuration other than the unnamed one, you must provide a handler for the.</span></span> <span data-ttu-id="edcaf-158"><xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated>事件，並將處理常式<xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType>內的屬性設置為使用設定檔中<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>相應元素中的值`<federationConfiguration>`初始化的物件。</span><span class="sxs-lookup"><span data-stu-id="edcaf-158"><xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated> event and set the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> property inside the handler to a <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> object initialized with values from the appropriate `<federationConfiguration>` element in the configuration file.</span></span>  
  
 <span data-ttu-id="edcaf-159">元素`<federationConfiguration>`由類<xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement>表示。</span><span class="sxs-lookup"><span data-stu-id="edcaf-159">The `<federationConfiguration>` element is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> class.</span></span> <span data-ttu-id="edcaf-160">設定物件本身由類<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>表示。</span><span class="sxs-lookup"><span data-stu-id="edcaf-160">The configuration object itself is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> class.</span></span> <span data-ttu-id="edcaf-161">在<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>屬性上設置單個實例<xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>，並為應用程式提供聯合配置。</span><span class="sxs-lookup"><span data-stu-id="edcaf-161">A single <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> instance is set on the <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> property and provides federated configuration for the application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="edcaf-162">範例</span><span class="sxs-lookup"><span data-stu-id="edcaf-162">Example</span></span>  
 <span data-ttu-id="edcaf-163">以下 XML 顯示了`<federationConfiguration>`一個元素，該元素指定 WSFAM 的設置，並指定 SAM 使用<xref:System.IdentityModel.Services.ChunkedCookieHandler>預設 Cookie 處理常式（類的實例）。</span><span class="sxs-lookup"><span data-stu-id="edcaf-163">The following XML shows a `<federationConfiguration>` element that specifies settings for the WSFAM and specifies that the default cookie handler (an instance of the <xref:System.IdentityModel.Services.ChunkedCookieHandler> class) be used by the SAM.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="edcaf-164">在此示例中，不需要 Cookie 處理常式和 WSFAM 使用 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="edcaf-164">In this example, neither the cookie handler nor WSFAM are required to use HTTPS.</span></span> <span data-ttu-id="edcaf-165">這是因為`requireHttps``<wsFederation>`元素上的屬性和`requireSsl`上的屬性`<cookieHandlerElement>`是`false`。</span><span class="sxs-lookup"><span data-stu-id="edcaf-165">This is because the `requireHttps` attribute on the `<wsFederation>` element and the `requireSsl` attribute on the `<cookieHandlerElement>` are `false`.</span></span> <span data-ttu-id="edcaf-166">不建議大多數生產環境使用這些設置，因為它們可能會帶來安全風險。</span><span class="sxs-lookup"><span data-stu-id="edcaf-166">These settings are not recommended for most production environments as they may present a security risk.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="edcaf-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="edcaf-167">See also</span></span>

- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
- [<span data-ttu-id="edcaf-168">\<身份配置></span><span class="sxs-lookup"><span data-stu-id="edcaf-168">\<identityConfiguration></span></span>](identityconfiguration.md)
