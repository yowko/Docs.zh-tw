---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: e3e65820fa4dc341371d4f67689a288cd3f63951
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152563"
---
# <a name="securitytokenhandlerconfiguration"></a><span data-ttu-id="f21e3-101">\<安全權杖處理常式配置></span><span class="sxs-lookup"><span data-stu-id="f21e3-101">\<securityTokenHandlerConfiguration></span></span>
<span data-ttu-id="f21e3-102">提供權杖處理常式集合的配置。</span><span class="sxs-lookup"><span data-stu-id="f21e3-102">Provides configuration for the collection of token handlers.</span></span>  
  
<span data-ttu-id="f21e3-103">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f21e3-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f21e3-104">&nbsp;&nbsp;[**\<系統.身份模型>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="f21e3-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="f21e3-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<身份配置>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="f21e3-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="f21e3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<安全權杖處理常式>**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="f21e3-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="f21e3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<安全權杖處理常式配置>**</span><span class="sxs-lookup"><span data-stu-id="f21e3-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlerConfiguration>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f21e3-108">語法</span><span class="sxs-lookup"><span data-stu-id="f21e3-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f21e3-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f21e3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f21e3-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f21e3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f21e3-111">屬性</span><span class="sxs-lookup"><span data-stu-id="f21e3-111">Attributes</span></span>  
  
|<span data-ttu-id="f21e3-112">屬性</span><span class="sxs-lookup"><span data-stu-id="f21e3-112">Attribute</span></span>|<span data-ttu-id="f21e3-113">描述</span><span class="sxs-lookup"><span data-stu-id="f21e3-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f21e3-114">保存引導上下文</span><span class="sxs-lookup"><span data-stu-id="f21e3-114">saveBootstrapContext</span></span>|<span data-ttu-id="f21e3-115">指定是否應在會話權杖中包括引導標記。</span><span class="sxs-lookup"><span data-stu-id="f21e3-115">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="f21e3-116">還可以通過在`saveBootstrapContext`[\<標識配置>](identityconfiguration.md)元素上設置屬性，在權杖處理常式集合上設置該值。</span><span class="sxs-lookup"><span data-stu-id="f21e3-116">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="f21e3-117">權杖處理常式集合上設置的值將覆蓋服務上設置的值。</span><span class="sxs-lookup"><span data-stu-id="f21e3-117">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="f21e3-118">最大時鐘</span><span class="sxs-lookup"><span data-stu-id="f21e3-118">maximumClockSkew</span></span>|<span data-ttu-id="f21e3-119">指定<xref:System.TimeSpan>允許的最大時鐘偏斜的 。</span><span class="sxs-lookup"><span data-stu-id="f21e3-119">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="f21e3-120">控制執行時間敏感操作（如驗證登錄會話的過期時間）時允許的最大時鐘偏差。</span><span class="sxs-lookup"><span data-stu-id="f21e3-120">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="f21e3-121">預設值為 5 分鐘，"00：05：00"。</span><span class="sxs-lookup"><span data-stu-id="f21e3-121">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="f21e3-122">有關如何指定<xref:System.TimeSpan>值的詳細資訊，請參閱[時間跨度值](../windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="f21e3-122">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="f21e3-123">還可以通過在`maximumClockSkew`[\<標識配置>](identityconfiguration.md)元素上設置屬性，在服務等級設置最大時鐘偏斜。</span><span class="sxs-lookup"><span data-stu-id="f21e3-123">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="f21e3-124">權杖處理常式集合上設置的值將覆蓋服務上設置的值。</span><span class="sxs-lookup"><span data-stu-id="f21e3-124">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f21e3-125">子元素</span><span class="sxs-lookup"><span data-stu-id="f21e3-125">Child Elements</span></span>  
  
|<span data-ttu-id="f21e3-126">元素</span><span class="sxs-lookup"><span data-stu-id="f21e3-126">Element</span></span>|<span data-ttu-id="f21e3-127">描述</span><span class="sxs-lookup"><span data-stu-id="f21e3-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f21e3-128">\<觀眾尤裡斯·></span><span class="sxs-lookup"><span data-stu-id="f21e3-128">\<audienceUris></span></span>](audienceuris.md)|<span data-ttu-id="f21e3-129">指定此依賴方可接受的識別碼的 URI 集。</span><span class="sxs-lookup"><span data-stu-id="f21e3-129">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="f21e3-130">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f21e3-130">Optional.</span></span>|  
|[<span data-ttu-id="f21e3-131">\<緩存></span><span class="sxs-lookup"><span data-stu-id="f21e3-131">\<caches></span></span>](caches.md)|<span data-ttu-id="f21e3-132">註冊用於會話權杖和權杖重播檢測的緩存。</span><span class="sxs-lookup"><span data-stu-id="f21e3-132">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="f21e3-133">可以在服務等級或安全權杖處理常式集合上指定。</span><span class="sxs-lookup"><span data-stu-id="f21e3-133">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="f21e3-134">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f21e3-134">Optional.</span></span>|  
|[<span data-ttu-id="f21e3-135">\<證書驗證></span><span class="sxs-lookup"><span data-stu-id="f21e3-135">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="f21e3-136">控制權杖處理常式用於驗證憑證的設置。</span><span class="sxs-lookup"><span data-stu-id="f21e3-136">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="f21e3-137">可以在服務等級或安全權杖處理常式集合上指定。</span><span class="sxs-lookup"><span data-stu-id="f21e3-137">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="f21e3-138">如果特定處理常式配置了自己的驗證器，則這些設置將被覆蓋。</span><span class="sxs-lookup"><span data-stu-id="f21e3-138">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="f21e3-139">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f21e3-139">Optional.</span></span>|  
|[<span data-ttu-id="f21e3-140">\<發行人名稱註冊></span><span class="sxs-lookup"><span data-stu-id="f21e3-140">\<issuerNameRegistry></span></span>](issuernameregistry.md)|<span data-ttu-id="f21e3-141">配置權杖處理常式集合中處理常式使用的頒發者名稱註冊表。</span><span class="sxs-lookup"><span data-stu-id="f21e3-141">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="f21e3-142">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f21e3-142">Optional.</span></span>|  
|[<span data-ttu-id="f21e3-143">\<頒發者權杖解析器></span><span class="sxs-lookup"><span data-stu-id="f21e3-143">\<issuerTokenResolver></span></span>](issuertokenresolver.md)|<span data-ttu-id="f21e3-144">註冊權杖處理常式集合中處理常式使用的頒發者權杖解析器。</span><span class="sxs-lookup"><span data-stu-id="f21e3-144">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="f21e3-145">頒發者權杖解析器用於解析傳入權杖和消息上的簽名權杖。</span><span class="sxs-lookup"><span data-stu-id="f21e3-145">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="f21e3-146">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f21e3-146">Optional.</span></span>|  
|[<span data-ttu-id="f21e3-147">\<服務權杖解析器></span><span class="sxs-lookup"><span data-stu-id="f21e3-147">\<serviceTokenResolver></span></span>](servicetokenresolver.md)|<span data-ttu-id="f21e3-148">註冊權杖處理常式集合中處理常式使用的服務權杖解析器。</span><span class="sxs-lookup"><span data-stu-id="f21e3-148">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="f21e3-149">服務權杖解析器用於解析傳入權杖和消息上的加密權杖。</span><span class="sxs-lookup"><span data-stu-id="f21e3-149">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="f21e3-150">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f21e3-150">Optional.</span></span>|  
|[<span data-ttu-id="f21e3-151">\<權杖重播檢測></span><span class="sxs-lookup"><span data-stu-id="f21e3-151">\<tokenReplayDetection></span></span>](tokenreplaydetection.md)|<span data-ttu-id="f21e3-152">啟用權杖重播檢測並指定權杖的過期時間。</span><span class="sxs-lookup"><span data-stu-id="f21e3-152">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="f21e3-153">可以在服務等級或安全權杖處理常式集合上指定。</span><span class="sxs-lookup"><span data-stu-id="f21e3-153">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="f21e3-154">選擇性。</span><span class="sxs-lookup"><span data-stu-id="f21e3-154">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f21e3-155">父項目</span><span class="sxs-lookup"><span data-stu-id="f21e3-155">Parent Elements</span></span>  
  
|<span data-ttu-id="f21e3-156">元素</span><span class="sxs-lookup"><span data-stu-id="f21e3-156">Element</span></span>|<span data-ttu-id="f21e3-157">描述</span><span class="sxs-lookup"><span data-stu-id="f21e3-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f21e3-158">\<安全權杖處理常式></span><span class="sxs-lookup"><span data-stu-id="f21e3-158">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="f21e3-159">指定向終結點註冊的安全權杖處理常式的集合。</span><span class="sxs-lookup"><span data-stu-id="f21e3-159">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f21e3-160">備註</span><span class="sxs-lookup"><span data-stu-id="f21e3-160">Remarks</span></span>  
 <span data-ttu-id="f21e3-161">本節提供<xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration>物件的屬性值。</span><span class="sxs-lookup"><span data-stu-id="f21e3-161">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="f21e3-162">本節中配置的設置將覆蓋服務上配置的設置。</span><span class="sxs-lookup"><span data-stu-id="f21e3-162">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="f21e3-163">反過來，其中一些設置可以被在將處理常式添加到安全權杖處理常式集合時指定的設置覆蓋。</span><span class="sxs-lookup"><span data-stu-id="f21e3-163">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f21e3-164">範例</span><span class="sxs-lookup"><span data-stu-id="f21e3-164">Example</span></span>  
  
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
