---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: 330e52bd73a8032e4073fe434c852e5bdf8e1d47
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251880"
---
# <a name="securitytokenhandlerconfiguration"></a><span data-ttu-id="99f39-101">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="99f39-101">\<securityTokenHandlerConfiguration></span></span>
<span data-ttu-id="99f39-102">提供權杖處理常式集合的設定。</span><span class="sxs-lookup"><span data-stu-id="99f39-102">Provides configuration for the collection of token handlers.</span></span>  
  
<span data-ttu-id="99f39-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="99f39-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="99f39-104">&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="99f39-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="99f39-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="99f39-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="99f39-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="99f39-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="99f39-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<securityTokenHandlerConfiguration >**</span><span class="sxs-lookup"><span data-stu-id="99f39-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlerConfiguration>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99f39-108">語法</span><span class="sxs-lookup"><span data-stu-id="99f39-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99f39-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="99f39-109">Attributes and Elements</span></span>  
 <span data-ttu-id="99f39-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="99f39-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99f39-111">屬性</span><span class="sxs-lookup"><span data-stu-id="99f39-111">Attributes</span></span>  
  
|<span data-ttu-id="99f39-112">屬性</span><span class="sxs-lookup"><span data-stu-id="99f39-112">Attribute</span></span>|<span data-ttu-id="99f39-113">說明</span><span class="sxs-lookup"><span data-stu-id="99f39-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="99f39-114">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="99f39-114">saveBootstrapContext</span></span>|<span data-ttu-id="99f39-115">指定啟動程式權杖是否應包含在會話權杖中。</span><span class="sxs-lookup"><span data-stu-id="99f39-115">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="99f39-116">您也可以在`saveBootstrapContext` [ \<identityConfiguration >](identityconfiguration.md)專案上設定屬性，以在權杖處理常式集合上設定此值。</span><span class="sxs-lookup"><span data-stu-id="99f39-116">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="99f39-117">在權杖處理常式集合上設定的值會覆寫服務上設定的值。</span><span class="sxs-lookup"><span data-stu-id="99f39-117">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="99f39-118">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="99f39-118">maximumClockSkew</span></span>|<span data-ttu-id="99f39-119"><xref:System.TimeSpan> ，指定允許的最大時鐘誤差。</span><span class="sxs-lookup"><span data-stu-id="99f39-119">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="99f39-120">控制執行時間緊迫作業時允許的時鐘誤差上限，例如驗證登入會話的到期時間。</span><span class="sxs-lookup"><span data-stu-id="99f39-120">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="99f39-121">預設值為5分鐘，"00:05:00"。</span><span class="sxs-lookup"><span data-stu-id="99f39-121">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="99f39-122">如需如何指定<xref:System.TimeSpan>值的詳細資訊，請參閱[Timespan 值](../windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="99f39-122">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="99f39-123">您也可以在`maximumClockSkew` [ \<identityConfiguration >](identityconfiguration.md)專案上設定屬性，以在服務層級設定最大時鐘誤差。</span><span class="sxs-lookup"><span data-stu-id="99f39-123">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="99f39-124">在權杖處理常式集合上設定的值會覆寫服務上設定的值。</span><span class="sxs-lookup"><span data-stu-id="99f39-124">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99f39-125">子元素</span><span class="sxs-lookup"><span data-stu-id="99f39-125">Child Elements</span></span>  
  
|<span data-ttu-id="99f39-126">項目</span><span class="sxs-lookup"><span data-stu-id="99f39-126">Element</span></span>|<span data-ttu-id="99f39-127">描述</span><span class="sxs-lookup"><span data-stu-id="99f39-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99f39-128">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="99f39-128">\<audienceUris></span></span>](audienceuris.md)|<span data-ttu-id="99f39-129">指定 Uri 的集合，這是此信賴憑證者可接受的識別碼。</span><span class="sxs-lookup"><span data-stu-id="99f39-129">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="99f39-130">選擇性。</span><span class="sxs-lookup"><span data-stu-id="99f39-130">Optional.</span></span>|  
|[<span data-ttu-id="99f39-131">\<caches></span><span class="sxs-lookup"><span data-stu-id="99f39-131">\<caches></span></span>](caches.md)|<span data-ttu-id="99f39-132">註冊用於會話權杖和權杖重新執行偵測的快取。</span><span class="sxs-lookup"><span data-stu-id="99f39-132">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="99f39-133">可以在服務層級或安全性權杖處理常式集合中指定。</span><span class="sxs-lookup"><span data-stu-id="99f39-133">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="99f39-134">選擇性。</span><span class="sxs-lookup"><span data-stu-id="99f39-134">Optional.</span></span>|  
|[<span data-ttu-id="99f39-135">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="99f39-135">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="99f39-136">控制權杖處理常式用來驗證憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="99f39-136">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="99f39-137">可以在服務層級或安全性權杖處理常式集合中指定。</span><span class="sxs-lookup"><span data-stu-id="99f39-137">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="99f39-138">如果特定處理常式已設定自己的驗證器，則會覆寫這些設定。</span><span class="sxs-lookup"><span data-stu-id="99f39-138">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="99f39-139">選擇性。</span><span class="sxs-lookup"><span data-stu-id="99f39-139">Optional.</span></span>|  
|[<span data-ttu-id="99f39-140">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="99f39-140">\<issuerNameRegistry></span></span>](issuernameregistry.md)|<span data-ttu-id="99f39-141">設定權杖處理常式集合中處理常式所使用的簽發者名稱登錄。</span><span class="sxs-lookup"><span data-stu-id="99f39-141">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="99f39-142">選擇性。</span><span class="sxs-lookup"><span data-stu-id="99f39-142">Optional.</span></span>|  
|[<span data-ttu-id="99f39-143">\<issuerTokenResolver></span><span class="sxs-lookup"><span data-stu-id="99f39-143">\<issuerTokenResolver></span></span>](issuertokenresolver.md)|<span data-ttu-id="99f39-144">註冊權杖處理常式集合中處理常式所使用的簽發者 token 解析程式。</span><span class="sxs-lookup"><span data-stu-id="99f39-144">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="99f39-145">簽發者權杖解析程式是用來解析傳入權杖和訊息上的簽署權杖。</span><span class="sxs-lookup"><span data-stu-id="99f39-145">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="99f39-146">選擇性。</span><span class="sxs-lookup"><span data-stu-id="99f39-146">Optional.</span></span>|  
|[<span data-ttu-id="99f39-147">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="99f39-147">\<serviceTokenResolver></span></span>](servicetokenresolver.md)|<span data-ttu-id="99f39-148">註冊權杖處理常式集合中處理常式所使用的服務 token 解析程式。</span><span class="sxs-lookup"><span data-stu-id="99f39-148">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="99f39-149">服務權杖解析程式是用來解析傳入權杖和訊息上的加密權杖。</span><span class="sxs-lookup"><span data-stu-id="99f39-149">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="99f39-150">選擇性。</span><span class="sxs-lookup"><span data-stu-id="99f39-150">Optional.</span></span>|  
|[<span data-ttu-id="99f39-151">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="99f39-151">\<tokenReplayDetection></span></span>](tokenreplaydetection.md)|<span data-ttu-id="99f39-152">啟用權杖重新執行偵測，並指定權杖的到期時間。</span><span class="sxs-lookup"><span data-stu-id="99f39-152">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="99f39-153">可以在服務層級或安全性權杖處理常式集合中指定。</span><span class="sxs-lookup"><span data-stu-id="99f39-153">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="99f39-154">選擇性。</span><span class="sxs-lookup"><span data-stu-id="99f39-154">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="99f39-155">父項目</span><span class="sxs-lookup"><span data-stu-id="99f39-155">Parent Elements</span></span>  
  
|<span data-ttu-id="99f39-156">項目</span><span class="sxs-lookup"><span data-stu-id="99f39-156">Element</span></span>|<span data-ttu-id="99f39-157">描述</span><span class="sxs-lookup"><span data-stu-id="99f39-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="99f39-158">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="99f39-158">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="99f39-159">指定已向端點註冊的安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="99f39-159">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99f39-160">備註</span><span class="sxs-lookup"><span data-stu-id="99f39-160">Remarks</span></span>  
 <span data-ttu-id="99f39-161">本節提供<xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration>物件的屬性值。</span><span class="sxs-lookup"><span data-stu-id="99f39-161">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="99f39-162">在此區段中設定的設定會覆寫在服務上設定的設定。</span><span class="sxs-lookup"><span data-stu-id="99f39-162">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="99f39-163">其中有些設定可以覆寫為將處理常式加入至安全性權杖處理常式集合時所指定的設定。</span><span class="sxs-lookup"><span data-stu-id="99f39-163">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99f39-164">範例</span><span class="sxs-lookup"><span data-stu-id="99f39-164">Example</span></span>  
  
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
