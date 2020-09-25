---
title: <federationConfiguration>
ms.date: 03/30/2017
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
author: BrucePerlerMS
ms.openlocfilehash: 39e96a161a2e75d5f00b73f6b08b1e4a0c109aee
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201352"
---
# \<federationConfiguration>

<span data-ttu-id="1b874-101"><xref:System.IdentityModel.Services.WSFederationAuthenticationModule> <xref:System.IdentityModel.Services.SessionAuthenticationModule> 使用透過 WS-同盟通訊協定的同盟驗證時，設定 (WSFAM) 和 (SAM) 。</span><span class="sxs-lookup"><span data-stu-id="1b874-101">Configures the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) when using federated authentication through the WS-Federation protocol.</span></span> <span data-ttu-id="1b874-102"><xref:System.Security.Claims.ClaimsAuthorizationManager>使用 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> 或 <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> 類別來提供宣告式存取控制時，設定。</span><span class="sxs-lookup"><span data-stu-id="1b874-102">Configures the <xref:System.Security.Claims.ClaimsAuthorizationManager> when using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<federationConfiguration>**  
  
## <a name="syntax"></a><span data-ttu-id="1b874-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="1b874-103">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b874-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1b874-104">Attributes and Elements</span></span>  

 <span data-ttu-id="1b874-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1b874-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b874-106">屬性</span><span class="sxs-lookup"><span data-stu-id="1b874-106">Attributes</span></span>  
  
|<span data-ttu-id="1b874-107">屬性</span><span class="sxs-lookup"><span data-stu-id="1b874-107">Attribute</span></span>|<span data-ttu-id="1b874-108">描述</span><span class="sxs-lookup"><span data-stu-id="1b874-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1b874-109">NAME</span><span class="sxs-lookup"><span data-stu-id="1b874-109">name</span></span>|<span data-ttu-id="1b874-110">這個聯合組態項目的名稱。</span><span class="sxs-lookup"><span data-stu-id="1b874-110">The name of this federation configuration element.</span></span> <span data-ttu-id="1b874-111">這個屬性主要是針對未來的通訊協定提供擴充點。</span><span class="sxs-lookup"><span data-stu-id="1b874-111">This attribute primarily provides an extensibility point for future protocols.</span></span> <span data-ttu-id="1b874-112">選擇性。</span><span class="sxs-lookup"><span data-stu-id="1b874-112">Optional.</span></span>|  
|<span data-ttu-id="1b874-113">identityConfigurationName</span><span class="sxs-lookup"><span data-stu-id="1b874-113">identityConfigurationName</span></span>|<span data-ttu-id="1b874-114">身分識別設定區段的名稱，如要使用的元素中所指定 [\<identityConfiguration>](identityconfiguration.md) 。</span><span class="sxs-lookup"><span data-stu-id="1b874-114">The name of the identity configuration section as specified in an [\<identityConfiguration>](identityconfiguration.md) element to use.</span></span> <span data-ttu-id="1b874-115">如果未指定此屬性，則會使用預設的身分識別設定區段。</span><span class="sxs-lookup"><span data-stu-id="1b874-115">If this attribute is not specified, the default identity configuration section is used.</span></span> <span data-ttu-id="1b874-116">選擇性。</span><span class="sxs-lookup"><span data-stu-id="1b874-116">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1b874-117">子元素</span><span class="sxs-lookup"><span data-stu-id="1b874-117">Child Elements</span></span>  
  
|<span data-ttu-id="1b874-118">項目</span><span class="sxs-lookup"><span data-stu-id="1b874-118">Element</span></span>|<span data-ttu-id="1b874-119">描述</span><span class="sxs-lookup"><span data-stu-id="1b874-119">Description</span></span>|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<span data-ttu-id="1b874-120">設定 SAM 所使用的 cookie 處理常式。</span><span class="sxs-lookup"><span data-stu-id="1b874-120">Configures the cookie handler used by the SAM.</span></span> <span data-ttu-id="1b874-121">選擇性。</span><span class="sxs-lookup"><span data-stu-id="1b874-121">Optional.</span></span>|  
|[\<serviceCertificate>](servicecertificate.md)|<span data-ttu-id="1b874-122">設定用來加密和解密權杖的憑證。</span><span class="sxs-lookup"><span data-stu-id="1b874-122">Configures the certificate that is used to encrypt and decrypt tokens.</span></span> <span data-ttu-id="1b874-123">選擇性。</span><span class="sxs-lookup"><span data-stu-id="1b874-123">Optional.</span></span>|  
|[\<wsFederation>](wsfederation.md)|<span data-ttu-id="1b874-124">設定 WS-同盟驗證模組 (WSFAM) 。</span><span class="sxs-lookup"><span data-stu-id="1b874-124">Configures the WS-Federation Authentication Module (WSFAM).</span></span> <span data-ttu-id="1b874-125">選擇性。</span><span class="sxs-lookup"><span data-stu-id="1b874-125">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1b874-126">父項目</span><span class="sxs-lookup"><span data-stu-id="1b874-126">Parent Elements</span></span>  
  
|<span data-ttu-id="1b874-127">項目</span><span class="sxs-lookup"><span data-stu-id="1b874-127">Element</span></span>|<span data-ttu-id="1b874-128">描述</span><span class="sxs-lookup"><span data-stu-id="1b874-128">Description</span></span>|  
|-------------|-----------------|  
|[\<system.identityModel.services>](system-identitymodel-services.md)|<span data-ttu-id="1b874-129">使用 WS-同盟通訊協定進行驗證的設定區段。</span><span class="sxs-lookup"><span data-stu-id="1b874-129">Configuration section for authentication using the WS-Federation protocol.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b874-130">備註</span><span class="sxs-lookup"><span data-stu-id="1b874-130">Remarks</span></span>  

 <span data-ttu-id="1b874-131">\<federationConfiguration>元素提供兩種不同案例中的設定：</span><span class="sxs-lookup"><span data-stu-id="1b874-131">The \<federationConfiguration> element provides settings in two different scenarios:</span></span>  
  
- <span data-ttu-id="1b874-132">在被動 Web 應用程式中使用 WS-同盟時，元素包含設定 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) 和 <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) 的設定。</span><span class="sxs-lookup"><span data-stu-id="1b874-132">When using WS-Federation in a passive Web application, the element contains settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM).</span></span> <span data-ttu-id="1b874-133">它也會參考用來設定安全性權杖處理常式和憑證的身分識別設定，以及宣告授權管理員和宣告驗證管理員等元件。</span><span class="sxs-lookup"><span data-stu-id="1b874-133">It also references the identity configuration to be used to configure security token handlers and certificates, and components like the claims authorization manager and the claims authentication manager.</span></span>  
  
- <span data-ttu-id="1b874-134">使用 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> 或 <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> 類別在您的程式碼中提供宣告型存取控制時，專案會參考設定宣告授權管理員的身分識別設定，以及用來進行授權決策的原則。</span><span class="sxs-lookup"><span data-stu-id="1b874-134">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the element references the identity configuration that configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="1b874-135">即使是在非被動 Web 案例的案例中，也是如此。例如，Windows Communication Foundation (WCF) 應用程式或不是以 Web 為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1b874-135">This is true, even in scenarios that are not passive Web scenarios; for example, Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="1b874-136">如果應用程式不是被動 Web 應用程式，則專案 [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) 會 (和其子原則元素，如果專案所參考的身分識別設定有) ，則 `<federationConfiguration>` 唯一適用的設定。</span><span class="sxs-lookup"><span data-stu-id="1b874-136">If the application is not a passive Web application, the [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) element (and its child policy elements, if present) of the identity configuration referenced by the `<federationConfiguration>` element are the only settings applied.</span></span> <span data-ttu-id="1b874-137">其他所有項目都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="1b874-137">All others are ignored.</span></span>  
  
 <span data-ttu-id="1b874-138">無論何種情況，執行時間都會載入預設同盟設定。</span><span class="sxs-lookup"><span data-stu-id="1b874-138">Regardless of the scenario, the runtime loads the default federation configuration.</span></span> <span data-ttu-id="1b874-139">此行為定義如下：</span><span class="sxs-lookup"><span data-stu-id="1b874-139">The behavior is defined as follows:</span></span>  
  
1. <span data-ttu-id="1b874-140">如果沒有任何專案 `<federationConfiguration>` ，執行時間會建立同盟設定，並以預設值填入。</span><span class="sxs-lookup"><span data-stu-id="1b874-140">If there is no `<federationConfiguration>` element present, the runtime creates a federation configuration and populates it with default values.</span></span> <span data-ttu-id="1b874-141">此預設同盟設定會參考預設身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="1b874-141">This default federation configuration will reference the default identity configuration.</span></span>  
  
2. <span data-ttu-id="1b874-142">如果有單一專案 `<federationConfiguration>` ，它就是預設的同盟設定，不論它是否命名或未命名。</span><span class="sxs-lookup"><span data-stu-id="1b874-142">If a single `<federationConfiguration>` element is present, it is the default federation configuration regardless of whether it is named or unnamed.</span></span> <span data-ttu-id="1b874-143">如果指定了其 `identityConfiguration` 屬性，則會參考命名身分識別設定，否則會參考預設身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="1b874-143">If its `identityConfiguration` attribute is specified, the named identity configuration is referenced; otherwise, the default identity configuration is referenced.</span></span>  
  
3. <span data-ttu-id="1b874-144">如果有未命名的 `<federationConfiguration>` 元素，則為預設的同盟設定。</span><span class="sxs-lookup"><span data-stu-id="1b874-144">If an unnamed `<federationConfiguration>` element is present, it is the default federation configuration.</span></span> <span data-ttu-id="1b874-145">如果指定了其 `identityConfiguration` 屬性，則會參考命名身分識別設定，否則會參考預設身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="1b874-145">If its `identityConfiguration` attribute is specified, the named identity configuration is referenced; otherwise, the default identity configuration is referenced.</span></span>  
  
4. <span data-ttu-id="1b874-146">如果有多個命名 `<federationConfiguration>` 元素存在，而且沒有未命名的 `<federationConfiguration>` 元素，則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1b874-146">If multiple named `<federationConfiguration>` elements are present and no unnamed `<federationConfiguration>` element is present, an exception is thrown.</span></span>  
  
 <span data-ttu-id="1b874-147">通常只 `<federationConfiguration>` 會定義一個區段。</span><span class="sxs-lookup"><span data-stu-id="1b874-147">Typically, only a single `<federationConfiguration>` section is defined.</span></span> <span data-ttu-id="1b874-148">此區段是預設的同盟設定。</span><span class="sxs-lookup"><span data-stu-id="1b874-148">This section is the default federation configuration.</span></span> <span data-ttu-id="1b874-149">您可以指定多個唯一命名的專案 `<federationConfiguration>` ; 不過，在此情況下，如果您想要載入非未命名的同盟設定，則必須提供的處理常式。</span><span class="sxs-lookup"><span data-stu-id="1b874-149">You may specify multiple, uniquely-named `<federationConfiguration>` elements; however, in this case, if you want to load a federation configuration other than the unnamed one, you must provide a handler for the.</span></span> <span data-ttu-id="1b874-150"><xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated> 事件，並將 <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> 處理常式中的屬性設定為 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> 使用 `<federationConfiguration>` 設定檔中適當元素的值初始化的物件。</span><span class="sxs-lookup"><span data-stu-id="1b874-150"><xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated> event and set the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType> property inside the handler to a <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> object initialized with values from the appropriate `<federationConfiguration>` element in the configuration file.</span></span>  
  
 <span data-ttu-id="1b874-151">`<federationConfiguration>`元素是由 <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> 類別表示。</span><span class="sxs-lookup"><span data-stu-id="1b874-151">The `<federationConfiguration>` element is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement> class.</span></span> <span data-ttu-id="1b874-152">設定物件本身是以 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> 類別表示。</span><span class="sxs-lookup"><span data-stu-id="1b874-152">The configuration object itself is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> class.</span></span> <span data-ttu-id="1b874-153">在 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> 屬性上設定單一實例 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> ，並為應用程式提供同盟設定。</span><span class="sxs-lookup"><span data-stu-id="1b874-153">A single <xref:System.IdentityModel.Services.Configuration.FederationConfiguration> instance is set on the <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType> property and provides federated configuration for the application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b874-154">範例</span><span class="sxs-lookup"><span data-stu-id="1b874-154">Example</span></span>  

 <span data-ttu-id="1b874-155">下列 XML `<federationConfiguration>` 會顯示指定 WSFAM 設定的專案，並指定預設的 cookie 處理常式 (類別的實例 <xref:System.IdentityModel.Services.ChunkedCookieHandler>) 由 SAM 使用。</span><span class="sxs-lookup"><span data-stu-id="1b874-155">The following XML shows a `<federationConfiguration>` element that specifies settings for the WSFAM and specifies that the default cookie handler (an instance of the <xref:System.IdentityModel.Services.ChunkedCookieHandler> class) be used by the SAM.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="1b874-156">在此範例中，cookie 處理常式和 WSFAM 都不需要使用 HTTPS。</span><span class="sxs-lookup"><span data-stu-id="1b874-156">In this example, neither the cookie handler nor WSFAM are required to use HTTPS.</span></span> <span data-ttu-id="1b874-157">這是因為 `requireHttps` 元素上的屬性 `<wsFederation>` 和上的 `requireSsl` 屬性 `<cookieHandlerElement>` 是 `false` 。</span><span class="sxs-lookup"><span data-stu-id="1b874-157">This is because the `requireHttps` attribute on the `<wsFederation>` element and the `requireSsl` attribute on the `<cookieHandlerElement>` are `false`.</span></span> <span data-ttu-id="1b874-158">這些設定不建議用於大部分的生產環境，因為它們可能會有安全性風險。</span><span class="sxs-lookup"><span data-stu-id="1b874-158">These settings are not recommended for most production environments as they may present a security risk.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1b874-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b874-159">See also</span></span>

- <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>
- <xref:System.IdentityModel.Services.SessionAuthenticationModule>
- <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>
- [\<identityConfiguration>](identityconfiguration.md)
