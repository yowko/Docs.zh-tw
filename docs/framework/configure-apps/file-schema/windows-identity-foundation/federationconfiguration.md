---
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: bcd8e00b770517e3faff011b4acee08ebdc5a0df
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152732"
---
# \<federationConfiguration>
<span data-ttu-id="105f7-101"><xref:System.IdentityModel.Services.WSFederationAuthenticationModule> <xref:System.IdentityModel.Services.SessionAuthenticationModule> 透過 WS-同盟通訊協定來使用聯合驗證時，會設定（WSFAM）和（SAM）。</span><span class="sxs-lookup"><span data-stu-id="105f7-101">Configures the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) when using federated authentication through the WS-Federation protocol.</span></span> <span data-ttu-id="105f7-102"><xref:System.Security.Claims.ClaimsAuthorizationManager>使用 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> 或 <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> 類別來提供宣告型存取控制時，設定。</span><span class="sxs-lookup"><span data-stu-id="105f7-102">Configures the <xref:System.Security.Claims.ClaimsAuthorizationManager> when using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<federationConfiguration>**  
  
## <a name="syntax"></a><span data-ttu-id="105f7-103">語法</span><span class="sxs-lookup"><span data-stu-id="105f7-103">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="105f7-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="105f7-104">Attributes and Elements</span></span>  
 <span data-ttu-id="105f7-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="105f7-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="105f7-106">屬性</span><span class="sxs-lookup"><span data-stu-id="105f7-106">Attributes</span></span>  
  
|<span data-ttu-id="105f7-107">屬性</span><span class="sxs-lookup"><span data-stu-id="105f7-107">Attribute</span></span>|<span data-ttu-id="105f7-108">描述</span><span class="sxs-lookup"><span data-stu-id="105f7-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="105f7-109">NAME</span><span class="sxs-lookup"><span data-stu-id="105f7-109">name</span></span>|<span data-ttu-id="105f7-110">這個聯合組態項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="105f7-110">The name of this federation configuration element.</span></span> <span data-ttu-id="105f7-111">這個屬性主要是針對未來的通訊協定提供擴充點。</span><span class="sxs-lookup"><span data-stu-id="105f7-111">This attribute primarily provides an extensibility point for future protocols.</span></span> <span data-ttu-id="105f7-112">選擇性。</span><span class="sxs-lookup"><span data-stu-id="105f7-112">Optional.</span></span>|  
|<span data-ttu-id="105f7-113">identityConfigurationName</span><span class="sxs-lookup"><span data-stu-id="105f7-113">identityConfigurationName</span></span>|<span data-ttu-id="105f7-114">身分識別設定區段的名稱，如要使用的元素中所指定 [\<identityConfiguration>](identityconfiguration.md) 。</span><span class="sxs-lookup"><span data-stu-id="105f7-114">The name of the identity configuration section as specified in an [\<identityConfiguration>](identityconfiguration.md) element to use.</span></span> <span data-ttu-id="105f7-115">如果未指定此屬性，則會使用預設的身分識別設定區段。</span><span class="sxs-lookup"><span data-stu-id="105f7-115">If this attribute is not specified, the default identity configuration section is used.</span></span> <span data-ttu-id="105f7-116">選擇性。</span><span class="sxs-lookup"><span data-stu-id="105f7-116">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="105f7-117">子元素</span><span class="sxs-lookup"><span data-stu-id="105f7-117">Child Elements</span></span>  
  
|<span data-ttu-id="105f7-118">元素</span><span class="sxs-lookup"><span data-stu-id="105f7-118">Element</span></span>|<span data-ttu-id="105f7-119">描述</span><span class="sxs-lookup"><span data-stu-id="105f7-119">Description</span></span>|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<span data-ttu-id="105f7-120">設定 SAM 所使用的 cookie 處理常式。</span><span class="sxs-lookup"><span data-stu-id="105f7-120">Configures the cookie handler used by the SAM.</span></span> <span data-ttu-id="105f7-121">選擇性。</span><span class="sxs-lookup"><span data-stu-id="105f7-121">Optional.</span></span>|  
|[\<serviceCertificate>](servicecertificate.md)|<span data-ttu-id="105f7-122">設定用來加密和解密權杖的憑證。</span><span class="sxs-lookup"><span data-stu-id="105f7-122">Configures the certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="105f7-123">選擇性。</span><span class="sxs-lookup"><span data-stu-id="105f7-123">Optional.</span></span>|  
|[\<wsFederation>](wsfederation.md)|<span data-ttu-id="105f7-124">設定 WS-同盟驗證模組（WSFAM）。</span><span class="sxs-lookup"><span data-stu-id="105f7-124">Configures the WS-Federation Authentication Module (WSFAM).</span></span> <span data-ttu-id="105f7-125">選擇性。</span><span class="sxs-lookup"><span data-stu-id="105f7-125">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="105f7-126">父項目</span><span class="sxs-lookup"><span data-stu-id="105f7-126">Parent Elements</span></span>  
  
|<span data-ttu-id="105f7-127">元素</span><span class="sxs-lookup"><span data-stu-id="105f7-127">Element</span></span>|<span data-ttu-id="105f7-128">描述</span><span class="sxs-lookup"><span data-stu-id="105f7-128">Description</span></span>|  
|-------------|-----------------|  
|[\<system.identityModel.services>](system-identitymodel-services.md)|<span data-ttu-id="105f7-129">使用 WS-同盟通訊協定進行驗證的設定區段。</span><span class="sxs-lookup"><span data-stu-id="105f7-129">Configuration section for authentication using the WS-Federation protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="105f7-130">備註</span><span class="sxs-lookup"><span data-stu-id="105f7-130">Remarks</span></span>  
 <span data-ttu-id="105f7-131">\<federationConfiguration>元素會在兩個不同的案例中提供設定：</span><span class="sxs-lookup"><span data-stu-id="105f7-131">The \<federationConfiguration> element provides settings in two different scenarios:</span></span>  
  
- <span data-ttu-id="105f7-132">在被動 Web 應用程式中使用 WS-同盟時，元素會包含設定 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> （WSFAM）和 <xref:System.IdentityModel.Services.SessionAuthenticationModule> （SAM）的設定。</span><span class="sxs-lookup"><span data-stu-id="105f7-132">When using WS-Federation in a passive Web application, the element contains settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span> <span data-ttu-id="105f7-133">它也會參考要用來設定安全性權杖處理常式和憑證的身分識別設定，以及宣告授權管理員和宣告驗證管理員等元件。</span><span class="sxs-lookup"><span data-stu-id="105f7-133">It also references the identity configuration to be used to configure security token handlers and certificates, and components like the claims authorization manager and the claims authentication manager.</span></span>  
  
- <span data-ttu-id="105f7-134">當使用 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> 或 <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> 類別在您的程式碼中提供宣告型存取控制時，元素會參考身分設定，以設定宣告授權管理員和原則，以用來進行授權決策。</span><span class="sxs-lookup"><span data-stu-id="105f7-134">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the element references the identity configuration that configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="105f7-135">即使在不是被動 Web 案例的情況下，也是如此。例如，Windows Communication Foundation （WCF）應用程式或不是以 Web 為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="105f7-135">This is true, even in scenarios that are not passive Web scenarios; for example, Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="105f7-136">如果應用程式不是被動 Web 應用程式，則專案所參考之身分 [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) 識別設定的專案（及其子原則元素（如果有的話） `<federationConfiguration>` 是唯一套用的設定。</span><span class="sxs-lookup"><span data-stu-id="105f7-136">If the application is not a passive Web application, the [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) element (and its child policy elements, if present) of the identity configuration referenced by the `<federationConfiguration>` element are the only settings applied.</span></span> <span data-ttu-id="105f7-137">其他所有項目都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="105f7-137">All others are ignored.</span></span>  
  
 <span data-ttu-id="105f7-138">不論是哪一種情況，執行時間都會載入預設的同盟設定。</span><span class="sxs-lookup"><span data-stu-id="105f7-138">Regardless of the scenario, the runtime loads the default federation configuration.</span></span> <span data-ttu-id="105f7-139">其行為定義如下：</span><span class="sxs-lookup"><span data-stu-id="105f7-139">The behavior is defined as follows:</span></span>  
  
1. <span data-ttu-id="105f7-140">如果沒有專案 `<federationConfiguration>` ，執行時間會建立同盟設定，並以預設值填入該設定。</span><span class="sxs-lookup"><span data-stu-id="105f7-140">If there is no `<federationConfiguration>` element present, the runtime creates a federation configuration and populates it with default values.</span></span> <span data-ttu-id="105f7-141">此預設同盟設定會參考預設的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="105f7-141">This default federation configuration will reference the default identity configuration.</span></span>  
  
2. <span data-ttu-id="105f7-142">如果單一專案 `<federationConfiguration>` 存在，則它是預設的同盟設定，不論其名稱為或未命名。</span><span class="sxs-lookup"><span data-stu-id="105f7-142">If a single `<federationConfiguration>` element is present, it is the default federation configuration regardless of whether it is named or unnamed.</span></span> <span data-ttu-id="105f7-143">如果指定了它 `identityConfiguration` 的屬性，就會參考指定的身分識別設定，否則會參考預設的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="105f7-143">If its `identityConfiguration` attribute is specified, the named identity configuration is referenced; otherwise, the default identity configuration is referenced.</span></span>  
  
3. <span data-ttu-id="105f7-144">如果未命名的 `<federationConfiguration>` 元素存在，則為預設的同盟設定。</span><span class="sxs-lookup"><span data-stu-id="105f7-144">If an unnamed `<federationConfiguration>` element is present, it is the default federation configuration.</span></span> <span data-ttu-id="105f7-145">如果指定了它 `identityConfiguration` 的屬性，就會參考指定的身分識別設定，否則會參考預設的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="105f7-145">If its `identityConfiguration` attribute is specified, the named identity configuration is referenced; otherwise, the default identity configuration is referenced.</span></span>  
  
4. <span data-ttu-id="105f7-146">如果有多個已命名的專案， `<federationConfiguration>` 而且沒有任何未命名的 `<federationConfiguration>` 元素存在，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="105f7-146">If multiple named `<federationConfiguration>` elements are present and no unnamed `<federationConfiguration>` element is present, an exception is thrown.</span></span>  
  
 <span data-ttu-id="105f7-147">通常只 `<federationConfiguration>` 會定義單一區段。</span><span class="sxs-lookup"><span data-stu-id="105f7-147">Typically, only a single `<federationConfiguration>` section is defined.</span></span> <span data-ttu-id="105f7-148">此區段是預設的同盟設定。</span><span class="sxs-lookup"><span data-stu-id="105f7-148">This section is the default federation configuration.</span></span> <span data-ttu-id="105f7-149">您可以指定多個以唯一命名的專案 `<federationConfiguration>` ; 不過，在此情況下，如果您想要載入未命名的同盟設定，則必須提供的處理常式。</span><span class="sxs-lookup"><span data-stu-id="105f7-149">You may specify multiple, uniquely-named `<federationConfiguration>` elements; however, in this case, if you want to load a federation configuration other than the unnamed one, you must provide a handler for the.</span></span> <span data-ttu-id="105f7-150"><xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated>事件，並將 <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> 處理常式內的屬性設定為 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> 使用 `<federationConfiguration>` 設定檔中適當專案的值來初始化的物件。</span><span class="sxs-lookup"><span data-stu-id="105f7-150"><xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated> event and set the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> property inside the handler to a <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> object initialized with values from the appropriate `<federationConfiguration>` element in the configuration file.</span></span>  
  
 <span data-ttu-id="105f7-151">`<federationConfiguration>`元素是由 <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> 類別表示。</span><span class="sxs-lookup"><span data-stu-id="105f7-151">The `<federationConfiguration>` element is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> class.</span></span> <span data-ttu-id="105f7-152">設定物件本身是以 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> 類別表示。</span><span class="sxs-lookup"><span data-stu-id="105f7-152">The configuration object itself is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> class.</span></span> <span data-ttu-id="105f7-153">在 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> 屬性上設定單一實例 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> ，並提供應用程式的同盟設定。</span><span class="sxs-lookup"><span data-stu-id="105f7-153">A single <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> instance is set on the <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> property and provides federated configuration for the application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="105f7-154">範例</span><span class="sxs-lookup"><span data-stu-id="105f7-154">Example</span></span>  
 <span data-ttu-id="105f7-155">下列 XML 顯示的 `<federationConfiguration>` 元素會指定 WSFAM 的設定，並指定 SAM 使用預設的 cookie 處理常式（類別的實例 <xref:System.IdentityModel.Services.ChunkedCookieHandler> ）。</span><span class="sxs-lookup"><span data-stu-id="105f7-155">The following XML shows a `<federationConfiguration>` element that specifies settings for the WSFAM and specifies that the default cookie handler (an instance of the <xref:System.IdentityModel.Services.ChunkedCookieHandler> class) be used by the SAM.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="105f7-156">在此範例中，cookie 處理常式或 WSFAM 都不需要使用 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="105f7-156">In this example, neither the cookie handler nor WSFAM are required to use HTTPS.</span></span> <span data-ttu-id="105f7-157">這是因為 `requireHttps` 元素上的屬性 `<wsFederation>` 和上的 `requireSsl` 屬性為 `<cookieHandlerElement>` `false` 。</span><span class="sxs-lookup"><span data-stu-id="105f7-157">This is because the `requireHttps` attribute on the `<wsFederation>` element and the `requireSsl` attribute on the `<cookieHandlerElement>` are `false`.</span></span> <span data-ttu-id="105f7-158">在大部分的生產環境中，不建議使用這些設定，因為它們可能會有安全性風險。</span><span class="sxs-lookup"><span data-stu-id="105f7-158">These settings are not recommended for most production environments as they may present a security risk.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="105f7-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="105f7-159">See also</span></span>

- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
- [\<identityConfiguration>](identityconfiguration.md)
