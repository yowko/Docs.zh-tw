---
title: <identityConfiguration>
ms.date: 03/30/2017
ms.assetid: 1db76253-07da-447b-9e7a-3705c7228cf4
author: BrucePerlerMS
ms.openlocfilehash: 9f5e0c5ded3d750a1102492c7a506e6d5643b2d4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942742"
---
# <a name="identityconfiguration"></a><span data-ttu-id="87262-101">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="87262-101">\<identityConfiguration></span></span>

<span data-ttu-id="87262-102">指定服務層級的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="87262-102">Specifies service-level identity settings.</span></span>

 <span data-ttu-id="87262-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="87262-103">\<system.identityModel></span></span>\
<span data-ttu-id="87262-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="87262-104">\<identityConfiguration></span></span>

## <a name="syntax"></a><span data-ttu-id="87262-105">語法</span><span class="sxs-lookup"><span data-stu-id="87262-105">Syntax</span></span>

```xml
<system.identityModel>
  <identityConfiguration
      name=xs:string
      saveBootstrapContext=xs:boolean>
      maximumClockSkew=TimeSpan >
  </identityConfiguration>
</system.identityModel>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="87262-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="87262-106">Attributes and Elements</span></span>

<span data-ttu-id="87262-107">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="87262-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="87262-108">屬性</span><span class="sxs-lookup"><span data-stu-id="87262-108">Attributes</span></span>

|<span data-ttu-id="87262-109">屬性</span><span class="sxs-lookup"><span data-stu-id="87262-109">Attribute</span></span>|<span data-ttu-id="87262-110">描述</span><span class="sxs-lookup"><span data-stu-id="87262-110">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="87262-111">NAME</span><span class="sxs-lookup"><span data-stu-id="87262-111">name</span></span>|<span data-ttu-id="87262-112">身分識別設定區段的名稱。</span><span class="sxs-lookup"><span data-stu-id="87262-112">The name of the identity configuration section.</span></span> <span data-ttu-id="87262-113">您可以使用這個名稱來參考特定的設定區段。</span><span class="sxs-lookup"><span data-stu-id="87262-113">You can use this name to reference a specific configuration section.</span></span> <span data-ttu-id="87262-114">如果未`name`指定任何屬性, 區段會定義預設設定。</span><span class="sxs-lookup"><span data-stu-id="87262-114">If no `name` attribute is specified, the section defines the default configuration.</span></span> <span data-ttu-id="87262-115">預設設定一律用於被動同盟案例。</span><span class="sxs-lookup"><span data-stu-id="87262-115">The default configuration is always used for passive federation scenarios.</span></span> <span data-ttu-id="87262-116">如需詳細資訊, 請參閱[ \<federationConfiguration >](federationconfiguration.md)元素。</span><span class="sxs-lookup"><span data-stu-id="87262-116">For more information, see the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>|
|<span data-ttu-id="87262-117">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="87262-117">saveBootstrapContext</span></span>|<span data-ttu-id="87262-118">指定啟動程式權杖是否應包含在會話權杖中。</span><span class="sxs-lookup"><span data-stu-id="87262-118">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="87262-119">您也可以在`saveBootstrapContext` [ \<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md)專案上設定屬性, 以在權杖處理常式集合上設定此值。</span><span class="sxs-lookup"><span data-stu-id="87262-119">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element.</span></span> <span data-ttu-id="87262-120">在權杖處理常式集合上設定的值會覆寫服務上設定的值。</span><span class="sxs-lookup"><span data-stu-id="87262-120">A value set on the token handler collection overrides the value set on the service.</span></span>|
|<span data-ttu-id="87262-121">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="87262-121">maximumClockSkew</span></span>|<span data-ttu-id="87262-122"><xref:System.TimeSpan> , 指定允許的最大時鐘誤差。</span><span class="sxs-lookup"><span data-stu-id="87262-122">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="87262-123">控制執行時間緊迫作業時允許的時鐘誤差上限, 例如驗證登入會話的到期時間。</span><span class="sxs-lookup"><span data-stu-id="87262-123">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="87262-124">預設值為5分鐘, "00:05:00"。</span><span class="sxs-lookup"><span data-stu-id="87262-124">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="87262-125">如需如何指定<xref:System.TimeSpan>值的詳細資訊, 請參閱[Timespan 值](../windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="87262-125">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="87262-126">您也可以在`maximumClockSkew` [ \<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md)專案上設定屬性, 以在權杖處理常式集合上設定最大時鐘誤差。</span><span class="sxs-lookup"><span data-stu-id="87262-126">The maximum clock skew may also be set on a token handler collection by setting the `maximumClockSkew` attribute on the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element.</span></span> <span data-ttu-id="87262-127">在權杖處理常式集合上設定的值會覆寫服務上設定的值。</span><span class="sxs-lookup"><span data-stu-id="87262-127">A value set on the token handler collection overrides the value set on the service.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="87262-128">子元素</span><span class="sxs-lookup"><span data-stu-id="87262-128">Child Elements</span></span>

|<span data-ttu-id="87262-129">項目</span><span class="sxs-lookup"><span data-stu-id="87262-129">Element</span></span>|<span data-ttu-id="87262-130">描述</span><span class="sxs-lookup"><span data-stu-id="87262-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="87262-131">\<caches></span><span class="sxs-lookup"><span data-stu-id="87262-131">\<caches></span></span>](caches.md)|<span data-ttu-id="87262-132">註冊用於會話權杖和權杖重新執行偵測的快取。</span><span class="sxs-lookup"><span data-stu-id="87262-132">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="87262-133">可以在服務層級或安全性權杖處理常式集合中指定。</span><span class="sxs-lookup"><span data-stu-id="87262-133">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="87262-134">選擇性。</span><span class="sxs-lookup"><span data-stu-id="87262-134">Optional.</span></span>|
|[<span data-ttu-id="87262-135">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="87262-135">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="87262-136">控制權杖處理常式用來驗證憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="87262-136">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="87262-137">可以在服務層級或安全性權杖處理常式集合中指定。</span><span class="sxs-lookup"><span data-stu-id="87262-137">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="87262-138">選擇性。</span><span class="sxs-lookup"><span data-stu-id="87262-138">Optional.</span></span>|
|[<span data-ttu-id="87262-139">\<claimsAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="87262-139">\<claimsAuthenticationManager></span></span>](claimsauthenticationmanager.md)|<span data-ttu-id="87262-140">為傳入宣告註冊宣告驗證管理員。</span><span class="sxs-lookup"><span data-stu-id="87262-140">Registers a claims authentication manager for the incoming claims.</span></span> <span data-ttu-id="87262-141">選擇性。</span><span class="sxs-lookup"><span data-stu-id="87262-141">Optional.</span></span>|
|[<span data-ttu-id="87262-142">\<claimsAuthorizationManager></span><span class="sxs-lookup"><span data-stu-id="87262-142">\<claimsAuthorizationManager></span></span>](claimsauthorizationmanager.md)|<span data-ttu-id="87262-143">為傳入宣告註冊宣告授權管理員。</span><span class="sxs-lookup"><span data-stu-id="87262-143">Registers a claims authorization manager for the incoming claims.</span></span> <span data-ttu-id="87262-144">選擇性。</span><span class="sxs-lookup"><span data-stu-id="87262-144">Optional.</span></span>|
|[<span data-ttu-id="87262-145">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="87262-145">\<claimTypeRequired></span></span>](claimtyperequired.md)|<span data-ttu-id="87262-146">指定傳入安全性權杖的必要宣告集合。</span><span class="sxs-lookup"><span data-stu-id="87262-146">Specifies the set of required claims for incoming security tokens.</span></span> <span data-ttu-id="87262-147">選擇性。</span><span class="sxs-lookup"><span data-stu-id="87262-147">Optional.</span></span>|
|[<span data-ttu-id="87262-148">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="87262-148">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="87262-149">指定安全性權杖處理常式的集合。</span><span class="sxs-lookup"><span data-stu-id="87262-149">Specifies a collection of security token handlers.</span></span> <span data-ttu-id="87262-150">可以指定零個或多個安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="87262-150">Zero or more collections of security token handlers can be specified.</span></span> <span data-ttu-id="87262-151">選擇性。</span><span class="sxs-lookup"><span data-stu-id="87262-151">Optional.</span></span>|
|[<span data-ttu-id="87262-152">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="87262-152">\<tokenReplayDetection></span></span>](tokenreplaydetection.md)|<span data-ttu-id="87262-153">啟用權杖重新執行偵測, 並指定權杖的到期時間。</span><span class="sxs-lookup"><span data-stu-id="87262-153">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="87262-154">可以在服務層級或安全性權杖處理常式集合中指定。</span><span class="sxs-lookup"><span data-stu-id="87262-154">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="87262-155">選擇性。</span><span class="sxs-lookup"><span data-stu-id="87262-155">Optional.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="87262-156">父項目</span><span class="sxs-lookup"><span data-stu-id="87262-156">Parent Elements</span></span>

|<span data-ttu-id="87262-157">項目</span><span class="sxs-lookup"><span data-stu-id="87262-157">Element</span></span>|<span data-ttu-id="87262-158">說明</span><span class="sxs-lookup"><span data-stu-id="87262-158">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="87262-159">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="87262-159">\<system.identityModel></span></span>](system-identitymodel.md)|<span data-ttu-id="87262-160">提供在應用程式中啟用 Windows Identity Foundation (WIF) 選項的設定。</span><span class="sxs-lookup"><span data-stu-id="87262-160">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="87262-161">備註</span><span class="sxs-lookup"><span data-stu-id="87262-161">Remarks</span></span>

<span data-ttu-id="87262-162">可以定義多個身分識別設定, 每個都有唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="87262-162">Multiple identity configurations may be defined, each with a unique name.</span></span> <span data-ttu-id="87262-163">其行為如下所示:</span><span class="sxs-lookup"><span data-stu-id="87262-163">The behavior is as follows:</span></span>

1. <span data-ttu-id="87262-164">如果未`<identityConfiguration>`指定任何元素, 則為。</span><span class="sxs-lookup"><span data-stu-id="87262-164">If no `<identityConfiguration>` element is specified.</span></span> <span data-ttu-id="87262-165">預設身分識別設定會在執行時間建立, 並以預設值填入。</span><span class="sxs-lookup"><span data-stu-id="87262-165">A default identity configuration is created at runtime and populated with default values.</span></span>

2. <span data-ttu-id="87262-166">如果已指定`<identityConfiguration>`單一元素, 則為。</span><span class="sxs-lookup"><span data-stu-id="87262-166">If a single `<identityConfiguration>` element is specified.</span></span> <span data-ttu-id="87262-167">這是預設的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="87262-167">It is the default identity configuration.</span></span> <span data-ttu-id="87262-168">無論是命名或未命名, 都不重要。</span><span class="sxs-lookup"><span data-stu-id="87262-168">It does not matter whether it is named or unnamed.</span></span>

3. <span data-ttu-id="87262-169">如果指定`<identityConfiguration>`了多個元素, 則為。</span><span class="sxs-lookup"><span data-stu-id="87262-169">If multiple `<identityConfiguration>` elements are specified.</span></span> <span data-ttu-id="87262-170">未命名的元素會指定預設的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="87262-170">The unnamed element specifies the default identity configuration.</span></span> <span data-ttu-id="87262-171">建議您在指定多個`<identityConfiguration>`元素時, 其中一個專案應該是未命名的。</span><span class="sxs-lookup"><span data-stu-id="87262-171">It is recommended that when you specify multiple `<identityConfiguration>` elements, one of them should be unnamed.</span></span>

> [!WARNING]
> <span data-ttu-id="87262-172">如果您指定多`<identityConfiguration>`個元素, 其中一個專案應為未命名。</span><span class="sxs-lookup"><span data-stu-id="87262-172">If you specify multiple `<identityConfiguration>` elements, one of them should be unnamed.</span></span> <span data-ttu-id="87262-173">未命名的元素會是預設的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="87262-173">The unnamed element will be the default identity configuration.</span></span>

 <span data-ttu-id="87262-174">在專案中`<identityConfiguration>`指定的部分設定可以由安全性權杖處理常式集合上的設定或個別安全性權杖處理常式的設定覆寫。</span><span class="sxs-lookup"><span data-stu-id="87262-174">Some of the settings specified in the `<identityConfiguration>` element can be overridden by settings on a security token handler collection or by settings on individual security token handlers.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="87262-175">當使用<xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>或類別在您的程式碼中提供宣告型存取控制時, `<federationConfiguration>`元素所參考的身分識別設定會設定宣告授權管理員和原則, 以用來進行授權決策。</span><span class="sxs-lookup"><span data-stu-id="87262-175">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the identity configuration that is referenced by the `<federationConfiguration>` element configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="87262-176">這也適用于非被動 Web 案例的情況, 例如 Windows Communication Foundation (WCF) 應用程式或不是以 Web 為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="87262-176">This is true, even in scenarios that are not passive Web scenarios, for example Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="87262-177">如果應用程式不是被動 Web 應用程式, [ \<](claimsauthorizationmanager.md)則只會套用所參考身分識別設定的 claimsAuthorizationManager > 專案 (及其子原則元素, 如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="87262-177">If the application is not a passive Web application, the [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) element (and its child policy elements, if present) of the referenced identity configuration are the only settings applied.</span></span> <span data-ttu-id="87262-178">所有其他設定都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="87262-178">All other settings are ignored.</span></span> <span data-ttu-id="87262-179">如需詳細資訊, 請參閱[ \<federationConfiguration >](federationconfiguration.md)元素。</span><span class="sxs-lookup"><span data-stu-id="87262-179">For more information, see the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>

<span data-ttu-id="87262-180">`<identityConfiguration>`元素是<xref:System.IdentityModel.Configuration.IdentityConfigurationElement>由類別表示。</span><span class="sxs-lookup"><span data-stu-id="87262-180">The `<identityConfiguration>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityConfigurationElement> class.</span></span> <span data-ttu-id="87262-181">身分識別設定區段是由<xref:System.IdentityModel.Configuration.IdentityConfiguration>類別表示。</span><span class="sxs-lookup"><span data-stu-id="87262-181">An identity configuration section is represented by the <xref:System.IdentityModel.Configuration.IdentityConfiguration> class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="87262-182">將下列專案指定為專案的子`<identityConfiguration>`專案已被取代, 但仍支援此行為以提供回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="87262-182">Specifying the following elements as child elements of the `<identityConfiguration>` element has been deprecated, although the behavior is still supported for backward compatibility.</span></span> <span data-ttu-id="87262-183">這些元素應改為在[ \<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md)元素下指定。</span><span class="sxs-lookup"><span data-stu-id="87262-183">These elements should, instead, be specified under the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element.</span></span>
>
> - [<span data-ttu-id="87262-184">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="87262-184">\<audienceUris></span></span>](audienceuris.md)
> - [<span data-ttu-id="87262-185">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="87262-185">\<issuerNameRegistry></span></span>](issuernameregistry.md)
> - [<span data-ttu-id="87262-186">\<issuerTokenResolver></span><span class="sxs-lookup"><span data-stu-id="87262-186">\<issuerTokenResolver></span></span>](issuertokenresolver.md)
> - [<span data-ttu-id="87262-187">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="87262-187">\<serviceTokenResolver></span></span>](servicetokenresolver.md)

## <a name="example"></a><span data-ttu-id="87262-188">範例</span><span class="sxs-lookup"><span data-stu-id="87262-188">Example</span></span>

<span data-ttu-id="87262-189">下列範例會建立名為 "alternateConfiguration" 的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="87262-189">The following example creates an identity configuration named "alternateConfiguration".</span></span> <span data-ttu-id="87262-190">身分識別設定會指定預設值。</span><span class="sxs-lookup"><span data-stu-id="87262-190">The identity configuration specifies default settings.</span></span>

```xml
<system.identityModel>
    <identityConfiguration name="alternateConfiguration"/>
</system.identityModel>
```

## <a name="see-also"></a><span data-ttu-id="87262-191">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87262-191">See also</span></span>

- <xref:System.IdentityModel.Configuration.IdentityConfiguration>
- <xref:System.IdentityModel.Configuration.IdentityConfigurationElement>
