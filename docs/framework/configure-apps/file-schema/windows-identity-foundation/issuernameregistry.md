---
title: '&lt;issuerNameRegistry&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 0c0552e06564e09832cf78afeb8f183a0a0dc94c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltissuernameregistrygt"></a><span data-ttu-id="a2ebd-102">&lt;issuerNameRegistry&gt;</span><span class="sxs-lookup"><span data-stu-id="a2ebd-102">&lt;issuerNameRegistry&gt;</span></span>
<span data-ttu-id="a2ebd-103">設定簽發者名稱登錄，由權杖處理常式集合中的處理常式。</span><span class="sxs-lookup"><span data-stu-id="a2ebd-103">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
 <span data-ttu-id="a2ebd-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="a2ebd-104">\<system.identityModel></span></span>  
<span data-ttu-id="a2ebd-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="a2ebd-105">\<identityConfiguration></span></span>  
<span data-ttu-id="a2ebd-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="a2ebd-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="a2ebd-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="a2ebd-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="a2ebd-108">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="a2ebd-108">\<issuerNameRegistry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2ebd-109">語法</span><span class="sxs-lookup"><span data-stu-id="a2ebd-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2ebd-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a2ebd-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a2ebd-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a2ebd-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2ebd-112">屬性</span><span class="sxs-lookup"><span data-stu-id="a2ebd-112">Attributes</span></span>  
  
|<span data-ttu-id="a2ebd-113">屬性</span><span class="sxs-lookup"><span data-stu-id="a2ebd-113">Attribute</span></span>|<span data-ttu-id="a2ebd-114">描述</span><span class="sxs-lookup"><span data-stu-id="a2ebd-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a2ebd-115">類型</span><span class="sxs-lookup"><span data-stu-id="a2ebd-115">type</span></span>|<span data-ttu-id="a2ebd-116">從衍生的型別<xref:System.IdentityModel.Tokens.IssuerNameRegistry>類別。</span><span class="sxs-lookup"><span data-stu-id="a2ebd-116">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="a2ebd-117">如需有關如何指定自訂`type`，請參閱 [自訂型別參考]。</span><span class="sxs-lookup"><span data-stu-id="a2ebd-117">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a2ebd-118">子元素</span><span class="sxs-lookup"><span data-stu-id="a2ebd-118">Child Elements</span></span>  
  
|<span data-ttu-id="a2ebd-119">項目</span><span class="sxs-lookup"><span data-stu-id="a2ebd-119">Element</span></span>|<span data-ttu-id="a2ebd-120">說明</span><span class="sxs-lookup"><span data-stu-id="a2ebd-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a2ebd-121">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="a2ebd-121">\<trustedIssuers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)|<span data-ttu-id="a2ebd-122">當`type`屬性會指定以組態為基礎的簽發者名稱登錄 (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>類別)，則[ \<trustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)必須指定項目。</span><span class="sxs-lookup"><span data-stu-id="a2ebd-122">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="a2ebd-123">[ \<TrustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)項目可以採取`<add>`， `<clear>`，或`<remove>`子項目的項目。</span><span class="sxs-lookup"><span data-stu-id="a2ebd-123">The [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a2ebd-124">父項目</span><span class="sxs-lookup"><span data-stu-id="a2ebd-124">Parent Elements</span></span>  
  
|<span data-ttu-id="a2ebd-125">項目</span><span class="sxs-lookup"><span data-stu-id="a2ebd-125">Element</span></span>|<span data-ttu-id="a2ebd-126">說明</span><span class="sxs-lookup"><span data-stu-id="a2ebd-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a2ebd-127">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="a2ebd-127">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="a2ebd-128">提供組態集合的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="a2ebd-128">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2ebd-129">備註</span><span class="sxs-lookup"><span data-stu-id="a2ebd-129">Remarks</span></span>  
 <span data-ttu-id="a2ebd-130">使用簽發者名稱登錄驗證的所有簽發者權杖。</span><span class="sxs-lookup"><span data-stu-id="a2ebd-130">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="a2ebd-131">這是衍生自物件<xref:System.IdentityModel.Tokens.IssuerNameRegistry>類別。</span><span class="sxs-lookup"><span data-stu-id="a2ebd-131">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="a2ebd-132">簽發者名稱登錄用來產生關聯才能驗證語彙基元對應簽發者所產生的簽章的加密編譯內容的助憶鍵名稱。</span><span class="sxs-lookup"><span data-stu-id="a2ebd-132">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="a2ebd-133">簽發者名稱登錄會維護信賴憑證者的合作對象 (RP) 應用程式所信任的簽發者清單。</span><span class="sxs-lookup"><span data-stu-id="a2ebd-133">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="a2ebd-134">使用指定的簽發者名稱登錄類型`type`屬性。</span><span class="sxs-lookup"><span data-stu-id="a2ebd-134">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="a2ebd-135">`<issuerNameRegistry>`元素可能具有一或多個提供組態的指定類型的子元素。</span><span class="sxs-lookup"><span data-stu-id="a2ebd-135">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="a2ebd-136">您提供的邏輯來處理這些子項目覆寫<xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="a2ebd-136">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="a2ebd-137">WIF 提供單一的簽發者名稱登錄型別，根據預設，<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>類別。</span><span class="sxs-lookup"><span data-stu-id="a2ebd-137">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="a2ebd-138">這個類別會使用一組組態中指定的受信任簽發者憑證。</span><span class="sxs-lookup"><span data-stu-id="a2ebd-138">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="a2ebd-139">它需要的子組態項目，`<trustedIssuers>`下設定受信任簽發者憑證的集合。</span><span class="sxs-lookup"><span data-stu-id="a2ebd-139">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="a2ebd-140">受信任的憑證會指定使用 ASN.1 編碼格式的憑證指紋和新增或移除集合中使用`<add>`， `<clear>`，或`<remove>`項目。</span><span class="sxs-lookup"><span data-stu-id="a2ebd-140">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="a2ebd-141">`<issuerNameRegistry>`項目由<xref:System.IdentityModel.Configuration.IssuerNameRegistryElement>類別。</span><span class="sxs-lookup"><span data-stu-id="a2ebd-141">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2ebd-142">指定`<issuerNameRegistry>`為的子元素的項目[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目已被取代，但仍支援回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="a2ebd-142">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="a2ebd-143">設定`<securityTokenHandlerConfiguration>`元素會覆寫上`<identityConfiguration>`項目。</span><span class="sxs-lookup"><span data-stu-id="a2ebd-143">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2ebd-144">範例</span><span class="sxs-lookup"><span data-stu-id="a2ebd-144">Example</span></span>  
 <span data-ttu-id="a2ebd-145">下列 XML 會示範如何指定基礎設定簽發者名稱登錄。</span><span class="sxs-lookup"><span data-stu-id="a2ebd-145">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a2ebd-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2ebd-146">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
