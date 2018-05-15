---
title: '&lt;issuerNameRegistry&gt;'
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: b695cc6d66e5b9e45bb6a5fd22d594bc22ea3cba
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltissuernameregistrygt"></a><span data-ttu-id="cd293-102">&lt;issuerNameRegistry&gt;</span><span class="sxs-lookup"><span data-stu-id="cd293-102">&lt;issuerNameRegistry&gt;</span></span>
<span data-ttu-id="cd293-103">設定簽發者名稱登錄，由權杖處理常式集合中的處理常式。</span><span class="sxs-lookup"><span data-stu-id="cd293-103">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
 <span data-ttu-id="cd293-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="cd293-104">\<system.identityModel></span></span>  
<span data-ttu-id="cd293-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="cd293-105">\<identityConfiguration></span></span>  
<span data-ttu-id="cd293-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="cd293-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="cd293-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="cd293-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="cd293-108">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="cd293-108">\<issuerNameRegistry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd293-109">語法</span><span class="sxs-lookup"><span data-stu-id="cd293-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry type=xs:string>  
          <optionalCustomConfigurationElements />  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd293-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cd293-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cd293-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="cd293-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd293-112">屬性</span><span class="sxs-lookup"><span data-stu-id="cd293-112">Attributes</span></span>  
  
|<span data-ttu-id="cd293-113">屬性</span><span class="sxs-lookup"><span data-stu-id="cd293-113">Attribute</span></span>|<span data-ttu-id="cd293-114">描述</span><span class="sxs-lookup"><span data-stu-id="cd293-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cd293-115">類型</span><span class="sxs-lookup"><span data-stu-id="cd293-115">type</span></span>|<span data-ttu-id="cd293-116">從衍生的型別<xref:System.IdentityModel.Tokens.IssuerNameRegistry>類別。</span><span class="sxs-lookup"><span data-stu-id="cd293-116">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="cd293-117">如需有關如何指定自訂`type`，請參閱 [自訂型別參考]。</span><span class="sxs-lookup"><span data-stu-id="cd293-117">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd293-118">子項目</span><span class="sxs-lookup"><span data-stu-id="cd293-118">Child Elements</span></span>  
  
|<span data-ttu-id="cd293-119">項目</span><span class="sxs-lookup"><span data-stu-id="cd293-119">Element</span></span>|<span data-ttu-id="cd293-120">描述</span><span class="sxs-lookup"><span data-stu-id="cd293-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cd293-121">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="cd293-121">\<trustedIssuers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)|<span data-ttu-id="cd293-122">當`type`屬性會指定以組態為基礎的簽發者名稱登錄 (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>類別)，則[ \<trustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)必須指定項目。</span><span class="sxs-lookup"><span data-stu-id="cd293-122">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="cd293-123">[ \<TrustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)項目可以採取`<add>`， `<clear>`，或`<remove>`子項目的項目。</span><span class="sxs-lookup"><span data-stu-id="cd293-123">The [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cd293-124">父項目</span><span class="sxs-lookup"><span data-stu-id="cd293-124">Parent Elements</span></span>  
  
|<span data-ttu-id="cd293-125">項目</span><span class="sxs-lookup"><span data-stu-id="cd293-125">Element</span></span>|<span data-ttu-id="cd293-126">描述</span><span class="sxs-lookup"><span data-stu-id="cd293-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cd293-127">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="cd293-127">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="cd293-128">提供組態集合的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="cd293-128">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd293-129">備註</span><span class="sxs-lookup"><span data-stu-id="cd293-129">Remarks</span></span>  
 <span data-ttu-id="cd293-130">使用簽發者名稱登錄驗證的所有簽發者權杖。</span><span class="sxs-lookup"><span data-stu-id="cd293-130">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="cd293-131">這是衍生自物件<xref:System.IdentityModel.Tokens.IssuerNameRegistry>類別。</span><span class="sxs-lookup"><span data-stu-id="cd293-131">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="cd293-132">簽發者名稱登錄用來產生關聯才能驗證語彙基元對應簽發者所產生的簽章的加密編譯內容的助憶鍵名稱。</span><span class="sxs-lookup"><span data-stu-id="cd293-132">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="cd293-133">簽發者名稱登錄會維護信賴憑證者的合作對象 (RP) 應用程式所信任的簽發者清單。</span><span class="sxs-lookup"><span data-stu-id="cd293-133">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="cd293-134">使用指定的簽發者名稱登錄類型`type`屬性。</span><span class="sxs-lookup"><span data-stu-id="cd293-134">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="cd293-135">`<issuerNameRegistry>`元素可能具有一或多個提供組態的指定類型的子元素。</span><span class="sxs-lookup"><span data-stu-id="cd293-135">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="cd293-136">您提供的邏輯來處理這些子項目覆寫<xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="cd293-136">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="cd293-137">WIF 提供單一的簽發者名稱登錄型別，根據預設，<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>類別。</span><span class="sxs-lookup"><span data-stu-id="cd293-137">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="cd293-138">這個類別會使用一組組態中指定的受信任簽發者憑證。</span><span class="sxs-lookup"><span data-stu-id="cd293-138">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="cd293-139">它需要的子組態項目，`<trustedIssuers>`下設定受信任簽發者憑證的集合。</span><span class="sxs-lookup"><span data-stu-id="cd293-139">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="cd293-140">受信任的憑證會指定使用 ASN.1 編碼格式的憑證指紋和新增或移除集合中使用`<add>`， `<clear>`，或`<remove>`項目。</span><span class="sxs-lookup"><span data-stu-id="cd293-140">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="cd293-141">`<issuerNameRegistry>`項目由<xref:System.IdentityModel.Configuration.IssuerNameRegistryElement>類別。</span><span class="sxs-lookup"><span data-stu-id="cd293-141">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cd293-142">指定`<issuerNameRegistry>`為的子元素的項目[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目已被取代，但仍支援回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="cd293-142">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="cd293-143">設定`<securityTokenHandlerConfiguration>`元素會覆寫上`<identityConfiguration>`項目。</span><span class="sxs-lookup"><span data-stu-id="cd293-143">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd293-144">範例</span><span class="sxs-lookup"><span data-stu-id="cd293-144">Example</span></span>  
 <span data-ttu-id="cd293-145">下列 XML 會示範如何指定基礎設定簽發者名稱登錄。</span><span class="sxs-lookup"><span data-stu-id="cd293-145">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cd293-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd293-146">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
