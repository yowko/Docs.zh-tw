---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: e3e65820fa4dc341371d4f67689a288cd3f63951
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152563"
---
# \<securityTokenHandlerConfiguration>
<span data-ttu-id="17364-101">提供權杖處理常式集合的設定。</span><span class="sxs-lookup"><span data-stu-id="17364-101">Provides configuration for the collection of token handlers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlerConfiguration>**  
  
## <a name="syntax"></a><span data-ttu-id="17364-102">語法</span><span class="sxs-lookup"><span data-stu-id="17364-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17364-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="17364-103">Attributes and Elements</span></span>  
 <span data-ttu-id="17364-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="17364-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17364-105">屬性</span><span class="sxs-lookup"><span data-stu-id="17364-105">Attributes</span></span>  
  
|<span data-ttu-id="17364-106">屬性</span><span class="sxs-lookup"><span data-stu-id="17364-106">Attribute</span></span>|<span data-ttu-id="17364-107">描述</span><span class="sxs-lookup"><span data-stu-id="17364-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="17364-108">saveBootstrapCoNtext</span><span class="sxs-lookup"><span data-stu-id="17364-108">saveBootstrapContext</span></span>|<span data-ttu-id="17364-109">指定啟動程式權杖是否應包含在會話權杖中。</span><span class="sxs-lookup"><span data-stu-id="17364-109">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="17364-110">您也可以藉由設定元素上的屬性，在權杖處理常式集合上設定此值 `saveBootstrapContext` [\<identityConfiguration>](identityconfiguration.md) 。</span><span class="sxs-lookup"><span data-stu-id="17364-110">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="17364-111">在權杖處理常式集合上設定的值會覆寫服務上設定的值。</span><span class="sxs-lookup"><span data-stu-id="17364-111">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="17364-112">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="17364-112">maximumClockSkew</span></span>|<span data-ttu-id="17364-113"><xref:System.TimeSpan>，指定允許的最大時鐘誤差。</span><span class="sxs-lookup"><span data-stu-id="17364-113">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="17364-114">控制執行時間緊迫作業時允許的時鐘誤差上限，例如驗證登入會話的到期時間。</span><span class="sxs-lookup"><span data-stu-id="17364-114">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="17364-115">預設值為5分鐘，"00:05:00"。</span><span class="sxs-lookup"><span data-stu-id="17364-115">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="17364-116">如需如何指定值的詳細資訊 <xref:System.TimeSpan> ，請參閱[Timespan 值](../windows-workflow-foundation/index.md)。</span><span class="sxs-lookup"><span data-stu-id="17364-116">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="17364-117">您也可以在專案上設定屬性，以在服務層級設定最大時鐘誤差 `maximumClockSkew` [\<identityConfiguration>](identityconfiguration.md) 。</span><span class="sxs-lookup"><span data-stu-id="17364-117">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="17364-118">在權杖處理常式集合上設定的值會覆寫服務上設定的值。</span><span class="sxs-lookup"><span data-stu-id="17364-118">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="17364-119">子元素</span><span class="sxs-lookup"><span data-stu-id="17364-119">Child Elements</span></span>  
  
|<span data-ttu-id="17364-120">元素</span><span class="sxs-lookup"><span data-stu-id="17364-120">Element</span></span>|<span data-ttu-id="17364-121">描述</span><span class="sxs-lookup"><span data-stu-id="17364-121">Description</span></span>|  
|-------------|-----------------|  
|[\<audienceUris>](audienceuris.md)|<span data-ttu-id="17364-122">指定 Uri 的集合，這是此信賴憑證者可接受的識別碼。</span><span class="sxs-lookup"><span data-stu-id="17364-122">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="17364-123">選擇性。</span><span class="sxs-lookup"><span data-stu-id="17364-123">Optional.</span></span>|  
|[\<caches>](caches.md)|<span data-ttu-id="17364-124">註冊用於會話權杖和權杖重新執行偵測的快取。</span><span class="sxs-lookup"><span data-stu-id="17364-124">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="17364-125">可以在服務層級或安全性權杖處理常式集合中指定。</span><span class="sxs-lookup"><span data-stu-id="17364-125">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="17364-126">選擇性。</span><span class="sxs-lookup"><span data-stu-id="17364-126">Optional.</span></span>|  
|[\<certificateValidation>](certificatevalidation.md)|<span data-ttu-id="17364-127">控制權杖處理常式用來驗證憑證的設定。</span><span class="sxs-lookup"><span data-stu-id="17364-127">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="17364-128">可以在服務層級或安全性權杖處理常式集合中指定。</span><span class="sxs-lookup"><span data-stu-id="17364-128">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="17364-129">如果特定處理常式已設定自己的驗證器，則會覆寫這些設定。</span><span class="sxs-lookup"><span data-stu-id="17364-129">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="17364-130">選擇性。</span><span class="sxs-lookup"><span data-stu-id="17364-130">Optional.</span></span>|  
|[\<issuerNameRegistry>](issuernameregistry.md)|<span data-ttu-id="17364-131">設定權杖處理常式集合中處理常式所使用的簽發者名稱登錄。</span><span class="sxs-lookup"><span data-stu-id="17364-131">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="17364-132">選擇性。</span><span class="sxs-lookup"><span data-stu-id="17364-132">Optional.</span></span>|  
|[\<issuerTokenResolver>](issuertokenresolver.md)|<span data-ttu-id="17364-133">註冊權杖處理常式集合中處理常式所使用的簽發者 token 解析程式。</span><span class="sxs-lookup"><span data-stu-id="17364-133">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="17364-134">簽發者權杖解析程式是用來解析傳入權杖和訊息上的簽署權杖。</span><span class="sxs-lookup"><span data-stu-id="17364-134">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="17364-135">選擇性。</span><span class="sxs-lookup"><span data-stu-id="17364-135">Optional.</span></span>|  
|[\<serviceTokenResolver>](servicetokenresolver.md)|<span data-ttu-id="17364-136">註冊權杖處理常式集合中處理常式所使用的服務 token 解析程式。</span><span class="sxs-lookup"><span data-stu-id="17364-136">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="17364-137">服務權杖解析程式是用來解析傳入權杖和訊息上的加密權杖。</span><span class="sxs-lookup"><span data-stu-id="17364-137">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="17364-138">選擇性。</span><span class="sxs-lookup"><span data-stu-id="17364-138">Optional.</span></span>|  
|[\<tokenReplayDetection>](tokenreplaydetection.md)|<span data-ttu-id="17364-139">啟用權杖重新執行偵測，並指定權杖的到期時間。</span><span class="sxs-lookup"><span data-stu-id="17364-139">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="17364-140">可以在服務層級或安全性權杖處理常式集合中指定。</span><span class="sxs-lookup"><span data-stu-id="17364-140">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="17364-141">選擇性。</span><span class="sxs-lookup"><span data-stu-id="17364-141">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="17364-142">父項目</span><span class="sxs-lookup"><span data-stu-id="17364-142">Parent Elements</span></span>  
  
|<span data-ttu-id="17364-143">元素</span><span class="sxs-lookup"><span data-stu-id="17364-143">Element</span></span>|<span data-ttu-id="17364-144">描述</span><span class="sxs-lookup"><span data-stu-id="17364-144">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="17364-145">指定已向端點註冊的安全性權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="17364-145">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17364-146">備註</span><span class="sxs-lookup"><span data-stu-id="17364-146">Remarks</span></span>  
 <span data-ttu-id="17364-147">本節提供物件的屬性值 <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> 。</span><span class="sxs-lookup"><span data-stu-id="17364-147">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="17364-148">在此區段中設定的設定會覆寫在服務上設定的設定。</span><span class="sxs-lookup"><span data-stu-id="17364-148">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="17364-149">其中有些設定可以覆寫為將處理常式加入至安全性權杖處理常式集合時所指定的設定。</span><span class="sxs-lookup"><span data-stu-id="17364-149">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17364-150">範例</span><span class="sxs-lookup"><span data-stu-id="17364-150">Example</span></span>  
  
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
