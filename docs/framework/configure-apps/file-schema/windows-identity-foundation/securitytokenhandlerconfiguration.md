---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: 0aefaa808dfc32085a208420fcd582b1671acc64
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942450"
---
# <a name="securitytokenhandlerconfiguration"></a><span data-ttu-id="692ae-101">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="692ae-101">\<securityTokenHandlerConfiguration></span></span>
<span data-ttu-id="692ae-102">提供權杖處理常式集合的設定。</span><span class="sxs-lookup"><span data-stu-id="692ae-102">Provides configuration for the collection of token handlers.</span></span>  
  
 <span data-ttu-id="692ae-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="692ae-103">\<system.identityModel></span></span>  
<span data-ttu-id="692ae-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="692ae-104">\<identityConfiguration></span></span>  
<span data-ttu-id="692ae-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="692ae-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="692ae-106">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="692ae-106">\<securityTokenHandlerConfiguration></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="692ae-107">語法</span><span class="sxs-lookup"><span data-stu-id="692ae-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="692ae-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="692ae-108">Attributes and Elements</span></span>  
 <span data-ttu-id="692ae-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="692ae-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="692ae-110">屬性</span><span class="sxs-lookup"><span data-stu-id="692ae-110">Attributes</span></span>  
  
|<span data-ttu-id="692ae-111">屬性</span><span class="sxs-lookup"><span data-stu-id="692ae-111">Attribute</span></span>|<span data-ttu-id="692ae-112">描述</span><span class="sxs-lookup"><span data-stu-id="692ae-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="692ae-113">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="692ae-113">saveBootstrapContext</span></span>|<span data-ttu-id="692ae-114">指定啟動程式權杖是否應包含在會話權杖中。</span><span class="sxs-lookup"><span data-stu-id="692ae-114">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="692ae-115">您也可以在`saveBootstrapContext` [ \<identityConfiguration >](identityconfiguration.md)專案上設定屬性, 以在權杖處理常式集合上設定此值。</span><span class="sxs-lookup"><span data-stu-id="692ae-115">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="692ae-116">在權杖處理常式集合上設定的值會覆寫服務上設定的值。</span><span class="sxs-lookup"><span data-stu-id="692ae-116">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="692ae-117">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="692ae-117">maximumClockSkew</span></span>|<span data-ttu-id="692ae-118"><xref:System.TimeSpan> , 指定允許的最大時鐘誤差。</span><span class="sxs-lookup"><span data-stu-id="692ae-118">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="692ae-119">控制執行時間緊迫作業時允許的時鐘誤差上限, 例如驗證登入會話的到期時間。</span><span class="sxs-lookup"><span data-stu-id="692ae-119">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="692ae-120">預設值為5分鐘, "00:05:00"。</span><span class="sxs-lookup"><span data-stu-id="692ae-120">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="692ae-121">如需如何指定<xref:System.TimeSpan>值的詳細資訊, 請參閱[Timespan 值](../windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="692ae-121">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="692ae-122">您也可以在`maximumClockSkew` [ \<identityConfiguration >](identityconfiguration.md)專案上設定屬性, 以在服務層級設定最大時鐘誤差。</span><span class="sxs-lookup"><span data-stu-id="692ae-122">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="692ae-123">在權杖處理常式集合上設定的值會覆寫服務上設定的值。</span><span class="sxs-lookup"><span data-stu-id="692ae-123">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="692ae-124">子元素</span><span class="sxs-lookup"><span data-stu-id="692ae-124">Child Elements</span></span>  
  
|<span data-ttu-id="692ae-125">項目</span><span class="sxs-lookup"><span data-stu-id="692ae-125">Element</span></span>|<span data-ttu-id="692ae-126">說明</span><span class="sxs-lookup"><span data-stu-id="692ae-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="692ae-127">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="692ae-127">\<audienceUris></span></span>](audienceuris.md)|<span data-ttu-id="692ae-128">指定 Uri 的集合, 這是此信賴憑證者可接受的識別碼。</span><span class="sxs-lookup"><span data-stu-id="692ae-128">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="692ae-129">選擇性。</span><span class="sxs-lookup"><span data-stu-id="692ae-129">Optional.</span></span>|  
|[<span data-ttu-id="692ae-130">\<caches></span><span class="sxs-lookup"><span data-stu-id="692ae-130">\<caches></span></span>](caches.md)|<span data-ttu-id="692ae-131">註冊用於會話權杖和權杖重新執行偵測的快取。</span><span class="sxs-lookup"><span data-stu-id="692ae-131">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="692ae-132">可以在服務層級或安全性權杖處理常式集合中指定。</span><span class="sxs-lookup"><span data-stu-id="692ae-132">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="692ae-133">選擇性。</span><span class="sxs-lookup"><span data-stu-id="692ae-133">Optional.</span></span>|  
|[<span data-ttu-id="692ae-134">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="692ae-134">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="692ae-135">控制權杖處理常式用來驗證憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="692ae-135">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="692ae-136">可以在服務層級或安全性權杖處理常式集合中指定。</span><span class="sxs-lookup"><span data-stu-id="692ae-136">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="692ae-137">如果特定處理常式已設定自己的驗證器, 則會覆寫這些設定。</span><span class="sxs-lookup"><span data-stu-id="692ae-137">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="692ae-138">選擇性。</span><span class="sxs-lookup"><span data-stu-id="692ae-138">Optional.</span></span>|  
|[<span data-ttu-id="692ae-139">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="692ae-139">\<issuerNameRegistry></span></span>](issuernameregistry.md)|<span data-ttu-id="692ae-140">設定權杖處理常式集合中處理常式所使用的簽發者名稱登錄。</span><span class="sxs-lookup"><span data-stu-id="692ae-140">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="692ae-141">選擇性。</span><span class="sxs-lookup"><span data-stu-id="692ae-141">Optional.</span></span>|  
|[<span data-ttu-id="692ae-142">\<issuerTokenResolver></span><span class="sxs-lookup"><span data-stu-id="692ae-142">\<issuerTokenResolver></span></span>](issuertokenresolver.md)|<span data-ttu-id="692ae-143">註冊權杖處理常式集合中處理常式所使用的簽發者 token 解析程式。</span><span class="sxs-lookup"><span data-stu-id="692ae-143">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="692ae-144">簽發者權杖解析程式是用來解析傳入權杖和訊息上的簽署權杖。</span><span class="sxs-lookup"><span data-stu-id="692ae-144">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="692ae-145">選擇性。</span><span class="sxs-lookup"><span data-stu-id="692ae-145">Optional.</span></span>|  
|[<span data-ttu-id="692ae-146">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="692ae-146">\<serviceTokenResolver></span></span>](servicetokenresolver.md)|<span data-ttu-id="692ae-147">註冊權杖處理常式集合中處理常式所使用的服務 token 解析程式。</span><span class="sxs-lookup"><span data-stu-id="692ae-147">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="692ae-148">服務權杖解析程式是用來解析傳入權杖和訊息上的加密權杖。</span><span class="sxs-lookup"><span data-stu-id="692ae-148">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="692ae-149">選擇性。</span><span class="sxs-lookup"><span data-stu-id="692ae-149">Optional.</span></span>|  
|[<span data-ttu-id="692ae-150">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="692ae-150">\<tokenReplayDetection></span></span>](tokenreplaydetection.md)|<span data-ttu-id="692ae-151">啟用權杖重新執行偵測, 並指定權杖的到期時間。</span><span class="sxs-lookup"><span data-stu-id="692ae-151">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="692ae-152">可以在服務層級或安全性權杖處理常式集合中指定。</span><span class="sxs-lookup"><span data-stu-id="692ae-152">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="692ae-153">選擇性。</span><span class="sxs-lookup"><span data-stu-id="692ae-153">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="692ae-154">父項目</span><span class="sxs-lookup"><span data-stu-id="692ae-154">Parent Elements</span></span>  
  
|<span data-ttu-id="692ae-155">項目</span><span class="sxs-lookup"><span data-stu-id="692ae-155">Element</span></span>|<span data-ttu-id="692ae-156">說明</span><span class="sxs-lookup"><span data-stu-id="692ae-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="692ae-157">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="692ae-157">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="692ae-158">指定已向端點註冊的安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="692ae-158">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="692ae-159">備註</span><span class="sxs-lookup"><span data-stu-id="692ae-159">Remarks</span></span>  
 <span data-ttu-id="692ae-160">本節提供<xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration>物件的屬性值。</span><span class="sxs-lookup"><span data-stu-id="692ae-160">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="692ae-161">在此區段中設定的設定會覆寫在服務上設定的設定。</span><span class="sxs-lookup"><span data-stu-id="692ae-161">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="692ae-162">其中有些設定可以覆寫為將處理常式加入至安全性權杖處理常式集合時所指定的設定。</span><span class="sxs-lookup"><span data-stu-id="692ae-162">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="692ae-163">範例</span><span class="sxs-lookup"><span data-stu-id="692ae-163">Example</span></span>  
  
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
