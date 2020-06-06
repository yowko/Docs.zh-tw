---
title: <identityConfiguration>
ms.date: 03/30/2017
ms.assetid: 1db76253-07da-447b-9e7a-3705c7228cf4
author: BrucePerlerMS
ms.openlocfilehash: 0fa8c574fd5663606cf081f1000a24884306edfe
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251987"
---
# \<identityConfiguration>

<span data-ttu-id="e6f29-101">指定服務層級的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="e6f29-101">Specifies service-level identity settings.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<identityConfiguration>**  

## <a name="syntax"></a><span data-ttu-id="e6f29-102">語法</span><span class="sxs-lookup"><span data-stu-id="e6f29-102">Syntax</span></span>

```xml
<system.identityModel>
  <identityConfiguration
      name=xs:string
      saveBootstrapContext=xs:boolean>
      maximumClockSkew=TimeSpan >
  </identityConfiguration>
</system.identityModel>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e6f29-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e6f29-103">Attributes and Elements</span></span>

<span data-ttu-id="e6f29-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e6f29-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e6f29-105">屬性</span><span class="sxs-lookup"><span data-stu-id="e6f29-105">Attributes</span></span>

|<span data-ttu-id="e6f29-106">屬性</span><span class="sxs-lookup"><span data-stu-id="e6f29-106">Attribute</span></span>|<span data-ttu-id="e6f29-107">描述</span><span class="sxs-lookup"><span data-stu-id="e6f29-107">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="e6f29-108">NAME</span><span class="sxs-lookup"><span data-stu-id="e6f29-108">name</span></span>|<span data-ttu-id="e6f29-109">身分識別設定區段的名稱。</span><span class="sxs-lookup"><span data-stu-id="e6f29-109">The name of the identity configuration section.</span></span> <span data-ttu-id="e6f29-110">您可以使用這個名稱來參考特定的設定區段。</span><span class="sxs-lookup"><span data-stu-id="e6f29-110">You can use this name to reference a specific configuration section.</span></span> <span data-ttu-id="e6f29-111">如果未 `name` 指定任何屬性，區段會定義預設設定。</span><span class="sxs-lookup"><span data-stu-id="e6f29-111">If no `name` attribute is specified, the section defines the default configuration.</span></span> <span data-ttu-id="e6f29-112">預設設定一律用於被動同盟案例。</span><span class="sxs-lookup"><span data-stu-id="e6f29-112">The default configuration is always used for passive federation scenarios.</span></span> <span data-ttu-id="e6f29-113">如需詳細資訊，請參閱 [\<federationConfiguration>](federationconfiguration.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="e6f29-113">For more information, see the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>|
|<span data-ttu-id="e6f29-114">saveBootstrapCoNtext</span><span class="sxs-lookup"><span data-stu-id="e6f29-114">saveBootstrapContext</span></span>|<span data-ttu-id="e6f29-115">指定啟動程式權杖是否應包含在會話權杖中。</span><span class="sxs-lookup"><span data-stu-id="e6f29-115">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="e6f29-116">您也可以藉由設定元素上的屬性，在權杖處理常式集合上設定此值 `saveBootstrapContext` [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) 。</span><span class="sxs-lookup"><span data-stu-id="e6f29-116">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element.</span></span> <span data-ttu-id="e6f29-117">在權杖處理常式集合上設定的值會覆寫服務上設定的值。</span><span class="sxs-lookup"><span data-stu-id="e6f29-117">A value set on the token handler collection overrides the value set on the service.</span></span>|
|<span data-ttu-id="e6f29-118">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="e6f29-118">maximumClockSkew</span></span>|<span data-ttu-id="e6f29-119"><xref:System.TimeSpan>，指定允許的最大時鐘誤差。</span><span class="sxs-lookup"><span data-stu-id="e6f29-119">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="e6f29-120">控制執行時間緊迫作業時允許的時鐘誤差上限，例如驗證登入會話的到期時間。</span><span class="sxs-lookup"><span data-stu-id="e6f29-120">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="e6f29-121">預設值為5分鐘，"00:05:00"。</span><span class="sxs-lookup"><span data-stu-id="e6f29-121">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="e6f29-122">如需如何指定值的詳細資訊 <xref:System.TimeSpan> ，請參閱[Timespan 值](../windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="e6f29-122">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="e6f29-123">您也可以透過在專案上設定屬性，在權杖處理常式集合上設定最大時鐘誤差 `maximumClockSkew` [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) 。</span><span class="sxs-lookup"><span data-stu-id="e6f29-123">The maximum clock skew may also be set on a token handler collection by setting the `maximumClockSkew` attribute on the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element.</span></span> <span data-ttu-id="e6f29-124">在權杖處理常式集合上設定的值會覆寫服務上設定的值。</span><span class="sxs-lookup"><span data-stu-id="e6f29-124">A value set on the token handler collection overrides the value set on the service.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="e6f29-125">子元素</span><span class="sxs-lookup"><span data-stu-id="e6f29-125">Child Elements</span></span>

|<span data-ttu-id="e6f29-126">元素</span><span class="sxs-lookup"><span data-stu-id="e6f29-126">Element</span></span>|<span data-ttu-id="e6f29-127">描述</span><span class="sxs-lookup"><span data-stu-id="e6f29-127">Description</span></span>|
|-------------|-----------------|
|[\<caches>](caches.md)|<span data-ttu-id="e6f29-128">註冊用於會話權杖和權杖重新執行偵測的快取。</span><span class="sxs-lookup"><span data-stu-id="e6f29-128">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="e6f29-129">可以在服務層級或安全性權杖處理常式集合中指定。</span><span class="sxs-lookup"><span data-stu-id="e6f29-129">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="e6f29-130">選擇性。</span><span class="sxs-lookup"><span data-stu-id="e6f29-130">Optional.</span></span>|
|[\<certificateValidation>](certificatevalidation.md)|<span data-ttu-id="e6f29-131">控制權杖處理常式用來驗證憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="e6f29-131">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="e6f29-132">可以在服務層級或安全性權杖處理常式集合中指定。</span><span class="sxs-lookup"><span data-stu-id="e6f29-132">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="e6f29-133">選擇性。</span><span class="sxs-lookup"><span data-stu-id="e6f29-133">Optional.</span></span>|
|[\<claimsAuthenticationManager>](claimsauthenticationmanager.md)|<span data-ttu-id="e6f29-134">為傳入宣告註冊宣告驗證管理員。</span><span class="sxs-lookup"><span data-stu-id="e6f29-134">Registers a claims authentication manager for the incoming claims.</span></span> <span data-ttu-id="e6f29-135">選擇性。</span><span class="sxs-lookup"><span data-stu-id="e6f29-135">Optional.</span></span>|
|[\<claimsAuthorizationManager>](claimsauthorizationmanager.md)|<span data-ttu-id="e6f29-136">為傳入宣告註冊宣告授權管理員。</span><span class="sxs-lookup"><span data-stu-id="e6f29-136">Registers a claims authorization manager for the incoming claims.</span></span> <span data-ttu-id="e6f29-137">選擇性。</span><span class="sxs-lookup"><span data-stu-id="e6f29-137">Optional.</span></span>|
|[\<claimTypeRequired>](claimtyperequired.md)|<span data-ttu-id="e6f29-138">指定傳入安全性權杖的必要宣告集合。</span><span class="sxs-lookup"><span data-stu-id="e6f29-138">Specifies the set of required claims for incoming security tokens.</span></span> <span data-ttu-id="e6f29-139">選擇性。</span><span class="sxs-lookup"><span data-stu-id="e6f29-139">Optional.</span></span>|
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="e6f29-140">指定安全性權杖處理常式的集合。</span><span class="sxs-lookup"><span data-stu-id="e6f29-140">Specifies a collection of security token handlers.</span></span> <span data-ttu-id="e6f29-141">可以指定零個或多個安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="e6f29-141">Zero or more collections of security token handlers can be specified.</span></span> <span data-ttu-id="e6f29-142">選擇性。</span><span class="sxs-lookup"><span data-stu-id="e6f29-142">Optional.</span></span>|
|[\<tokenReplayDetection>](tokenreplaydetection.md)|<span data-ttu-id="e6f29-143">啟用權杖重新執行偵測，並指定權杖的到期時間。</span><span class="sxs-lookup"><span data-stu-id="e6f29-143">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="e6f29-144">可以在服務層級或安全性權杖處理常式集合中指定。</span><span class="sxs-lookup"><span data-stu-id="e6f29-144">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="e6f29-145">選擇性。</span><span class="sxs-lookup"><span data-stu-id="e6f29-145">Optional.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e6f29-146">父項目</span><span class="sxs-lookup"><span data-stu-id="e6f29-146">Parent Elements</span></span>

|<span data-ttu-id="e6f29-147">元素</span><span class="sxs-lookup"><span data-stu-id="e6f29-147">Element</span></span>|<span data-ttu-id="e6f29-148">描述</span><span class="sxs-lookup"><span data-stu-id="e6f29-148">Description</span></span>|
|-------------|-----------------|
|[\<system.identityModel>](system-identitymodel.md)|<span data-ttu-id="e6f29-149">提供在應用程式中啟用 Windows Identity Foundation （WIF）選項的設定。</span><span class="sxs-lookup"><span data-stu-id="e6f29-149">Provides configuration for enabling Windows Identity Foundation (WIF) options in applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e6f29-150">備註</span><span class="sxs-lookup"><span data-stu-id="e6f29-150">Remarks</span></span>

<span data-ttu-id="e6f29-151">可以定義多個身分識別設定，每個都有唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="e6f29-151">Multiple identity configurations may be defined, each with a unique name.</span></span> <span data-ttu-id="e6f29-152">其行為如下所示：</span><span class="sxs-lookup"><span data-stu-id="e6f29-152">The behavior is as follows:</span></span>

1. <span data-ttu-id="e6f29-153">如果未 `<identityConfiguration>` 指定任何元素，則為。</span><span class="sxs-lookup"><span data-stu-id="e6f29-153">If no `<identityConfiguration>` element is specified.</span></span> <span data-ttu-id="e6f29-154">預設身分識別設定會在執行時間建立，並以預設值填入。</span><span class="sxs-lookup"><span data-stu-id="e6f29-154">A default identity configuration is created at runtime and populated with default values.</span></span>

2. <span data-ttu-id="e6f29-155">如果 `<identityConfiguration>` 已指定單一元素，則為。</span><span class="sxs-lookup"><span data-stu-id="e6f29-155">If a single `<identityConfiguration>` element is specified.</span></span> <span data-ttu-id="e6f29-156">這是預設的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="e6f29-156">It is the default identity configuration.</span></span> <span data-ttu-id="e6f29-157">無論是命名或未命名，都不重要。</span><span class="sxs-lookup"><span data-stu-id="e6f29-157">It does not matter whether it is named or unnamed.</span></span>

3. <span data-ttu-id="e6f29-158">如果指定了多個元素，則 `<identityConfiguration>` 為。</span><span class="sxs-lookup"><span data-stu-id="e6f29-158">If multiple `<identityConfiguration>` elements are specified.</span></span> <span data-ttu-id="e6f29-159">未命名的元素會指定預設的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="e6f29-159">The unnamed element specifies the default identity configuration.</span></span> <span data-ttu-id="e6f29-160">建議您在指定多個元素時 `<identityConfiguration>` ，其中一個專案應該是未命名的。</span><span class="sxs-lookup"><span data-stu-id="e6f29-160">It is recommended that when you specify multiple `<identityConfiguration>` elements, one of them should be unnamed.</span></span>

> [!WARNING]
> <span data-ttu-id="e6f29-161">如果您指定多個 `<identityConfiguration>` 元素，其中一個專案應為未命名。</span><span class="sxs-lookup"><span data-stu-id="e6f29-161">If you specify multiple `<identityConfiguration>` elements, one of them should be unnamed.</span></span> <span data-ttu-id="e6f29-162">未命名的元素會是預設的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="e6f29-162">The unnamed element will be the default identity configuration.</span></span>

 <span data-ttu-id="e6f29-163">在專案中指定的部分設定 `<identityConfiguration>` 可以由安全性權杖處理常式集合上的設定或個別安全性權杖處理常式的設定覆寫。</span><span class="sxs-lookup"><span data-stu-id="e6f29-163">Some of the settings specified in the `<identityConfiguration>` element can be overridden by settings on a security token handler collection or by settings on individual security token handlers.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e6f29-164">當使用 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> 或 <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> 類別在您的程式碼中提供宣告型存取控制時，元素所參考的身分識別設定會設定 `<federationConfiguration>` 宣告授權管理員和原則，以用來進行授權決策。</span><span class="sxs-lookup"><span data-stu-id="e6f29-164">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the identity configuration that is referenced by the `<federationConfiguration>` element configures the claims authorization manager and policy that is used to make authorization decisions.</span></span> <span data-ttu-id="e6f29-165">這也適用于非被動 Web 案例的情況，例如 Windows Communication Foundation （WCF）應用程式或不是以 Web 為基礎的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e6f29-165">This is true, even in scenarios that are not passive Web scenarios, for example Windows Communication Foundation (WCF) applications or an application that is not Web-based.</span></span> <span data-ttu-id="e6f29-166">如果應用程式不是被動的 Web 應用程式，則會套用所 [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) 參考身分識別設定的專案（及其子原則元素（如果有的話））。</span><span class="sxs-lookup"><span data-stu-id="e6f29-166">If the application is not a passive Web application, the [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) element (and its child policy elements, if present) of the referenced identity configuration are the only settings applied.</span></span> <span data-ttu-id="e6f29-167">其他所有設定都會被略過。</span><span class="sxs-lookup"><span data-stu-id="e6f29-167">All other settings are ignored.</span></span> <span data-ttu-id="e6f29-168">如需詳細資訊，請參閱 [\<federationConfiguration>](federationconfiguration.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="e6f29-168">For more information, see the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>

<span data-ttu-id="e6f29-169">`<identityConfiguration>`元素是由 <xref:System.IdentityModel.Configuration.IdentityConfigurationElement> 類別表示。</span><span class="sxs-lookup"><span data-stu-id="e6f29-169">The `<identityConfiguration>` element is represented by the <xref:System.IdentityModel.Configuration.IdentityConfigurationElement> class.</span></span> <span data-ttu-id="e6f29-170">身分識別設定區段是由類別表示 <xref:System.IdentityModel.Configuration.IdentityConfiguration> 。</span><span class="sxs-lookup"><span data-stu-id="e6f29-170">An identity configuration section is represented by the <xref:System.IdentityModel.Configuration.IdentityConfiguration> class.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e6f29-171">將下列專案指定為專案的子專案 `<identityConfiguration>` 已被取代，但仍支援此行為以提供回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="e6f29-171">Specifying the following elements as child elements of the `<identityConfiguration>` element has been deprecated, although the behavior is still supported for backward compatibility.</span></span> <span data-ttu-id="e6f29-172">這些元素應改為在專案底下指定 [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) 。</span><span class="sxs-lookup"><span data-stu-id="e6f29-172">These elements should, instead, be specified under the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element.</span></span>
>
> - [\<audienceUris>](audienceuris.md)
> - [\<issuerNameRegistry>](issuernameregistry.md)
> - [\<issuerTokenResolver>](issuertokenresolver.md)
> - [\<serviceTokenResolver>](servicetokenresolver.md)

## <a name="example"></a><span data-ttu-id="e6f29-173">範例</span><span class="sxs-lookup"><span data-stu-id="e6f29-173">Example</span></span>

<span data-ttu-id="e6f29-174">下列範例會建立名為 "alternateConfiguration" 的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="e6f29-174">The following example creates an identity configuration named "alternateConfiguration".</span></span> <span data-ttu-id="e6f29-175">身分識別設定會指定預設值。</span><span class="sxs-lookup"><span data-stu-id="e6f29-175">The identity configuration specifies default settings.</span></span>

```xml
<system.identityModel>
    <identityConfiguration name="alternateConfiguration"/>
</system.identityModel>
```

## <a name="see-also"></a><span data-ttu-id="e6f29-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6f29-176">See also</span></span>

- <xref:System.IdentityModel.Configuration.IdentityConfiguration>
- <xref:System.IdentityModel.Configuration.IdentityConfigurationElement>
