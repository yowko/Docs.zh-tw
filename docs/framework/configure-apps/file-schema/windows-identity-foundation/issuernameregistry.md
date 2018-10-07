---
title: '&lt;issuerNameRegistry&gt;'
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: de3ceb5d84d17307c69e9155834a0a584e6920a1
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48845420"
---
# <a name="ltissuernameregistrygt"></a><span data-ttu-id="213ef-102">&lt;issuerNameRegistry&gt;</span><span class="sxs-lookup"><span data-stu-id="213ef-102">&lt;issuerNameRegistry&gt;</span></span>
<span data-ttu-id="213ef-103">設定簽發者名稱登錄，可由權杖處理常式集合中的處理常式。</span><span class="sxs-lookup"><span data-stu-id="213ef-103">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
 <span data-ttu-id="213ef-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="213ef-104">\<system.identityModel></span></span>  
<span data-ttu-id="213ef-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="213ef-105">\<identityConfiguration></span></span>  
<span data-ttu-id="213ef-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="213ef-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="213ef-107">\<Securitytokenhandlerconfiguration> ></span><span class="sxs-lookup"><span data-stu-id="213ef-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="213ef-108">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="213ef-108">\<issuerNameRegistry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="213ef-109">語法</span><span class="sxs-lookup"><span data-stu-id="213ef-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="213ef-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="213ef-110">Attributes and Elements</span></span>  
 <span data-ttu-id="213ef-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="213ef-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="213ef-112">屬性</span><span class="sxs-lookup"><span data-stu-id="213ef-112">Attributes</span></span>  
  
|<span data-ttu-id="213ef-113">屬性</span><span class="sxs-lookup"><span data-stu-id="213ef-113">Attribute</span></span>|<span data-ttu-id="213ef-114">描述</span><span class="sxs-lookup"><span data-stu-id="213ef-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="213ef-115">類型</span><span class="sxs-lookup"><span data-stu-id="213ef-115">type</span></span>|<span data-ttu-id="213ef-116">衍生自類型<xref:System.IdentityModel.Tokens.IssuerNameRegistry>類別。</span><span class="sxs-lookup"><span data-stu-id="213ef-116">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="213ef-117">如需有關如何指定自訂`type`，請參閱 [自訂型別參考]。</span><span class="sxs-lookup"><span data-stu-id="213ef-117">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="213ef-118">子元素</span><span class="sxs-lookup"><span data-stu-id="213ef-118">Child Elements</span></span>  
  
|<span data-ttu-id="213ef-119">項目</span><span class="sxs-lookup"><span data-stu-id="213ef-119">Element</span></span>|<span data-ttu-id="213ef-120">描述</span><span class="sxs-lookup"><span data-stu-id="213ef-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="213ef-121">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="213ef-121">\<trustedIssuers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)|<span data-ttu-id="213ef-122">當`type`屬性會指定以組態為基礎的簽發者名稱登錄 (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>類別)，則[ \<trustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)必須指定項目。</span><span class="sxs-lookup"><span data-stu-id="213ef-122">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="213ef-123">[ \<TrustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)項目可以採取`<add>`， `<clear>`，或`<remove>`項目與子項目。</span><span class="sxs-lookup"><span data-stu-id="213ef-123">The [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="213ef-124">父項目</span><span class="sxs-lookup"><span data-stu-id="213ef-124">Parent Elements</span></span>  
  
|<span data-ttu-id="213ef-125">項目</span><span class="sxs-lookup"><span data-stu-id="213ef-125">Element</span></span>|<span data-ttu-id="213ef-126">描述</span><span class="sxs-lookup"><span data-stu-id="213ef-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="213ef-127">\<Securitytokenhandlerconfiguration> ></span><span class="sxs-lookup"><span data-stu-id="213ef-127">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="213ef-128">提供組態集合的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="213ef-128">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="213ef-129">備註</span><span class="sxs-lookup"><span data-stu-id="213ef-129">Remarks</span></span>  
 <span data-ttu-id="213ef-130">所有簽發者權杖會使用簽發者名稱登錄進行驗證。</span><span class="sxs-lookup"><span data-stu-id="213ef-130">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="213ef-131">這是衍生自物件<xref:System.IdentityModel.Tokens.IssuerNameRegistry>類別。</span><span class="sxs-lookup"><span data-stu-id="213ef-131">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="213ef-132">簽發者名稱登錄來建立助憶名稱，才能驗證對應簽發者所產生之權杖的簽章的加密編譯內容。</span><span class="sxs-lookup"><span data-stu-id="213ef-132">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="213ef-133">簽發者名稱登錄會維護信賴憑證者 (rp) 應用程式所信任的簽發者清單。</span><span class="sxs-lookup"><span data-stu-id="213ef-133">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="213ef-134">使用指定的簽發者名稱登錄型別`type`屬性。</span><span class="sxs-lookup"><span data-stu-id="213ef-134">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="213ef-135">`<issuerNameRegistry>`元素可能具有一或多個的子元素會提供指定之類型的組態。</span><span class="sxs-lookup"><span data-stu-id="213ef-135">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="213ef-136">提供藉由覆寫會處理這些子元素的邏輯<xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="213ef-136">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="213ef-137">WIF 提供單一的簽發者名稱登錄型別，根據預設，<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>類別。</span><span class="sxs-lookup"><span data-stu-id="213ef-137">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="213ef-138">這個類別會使用一組的組態中指定的受信任簽發者憑證。</span><span class="sxs-lookup"><span data-stu-id="213ef-138">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="213ef-139">它需要的子組態項目， `<trustedIssuers>`，在設定受信任簽發者憑證的集合。</span><span class="sxs-lookup"><span data-stu-id="213ef-139">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="213ef-140">受信任的憑證會指定使用 ASN.1 編碼的憑證指紋的格式及新增或移除集合中使用`<add>`， `<clear>`，或`<remove>`項目。</span><span class="sxs-lookup"><span data-stu-id="213ef-140">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="213ef-141">`<issuerNameRegistry>`項目由<xref:System.IdentityModel.Configuration.IssuerNameRegistryElement>類別。</span><span class="sxs-lookup"><span data-stu-id="213ef-141">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="213ef-142">指定`<issuerNameRegistry>`元素的子元素當做[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目已被取代，但仍支援回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="213ef-142">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="213ef-143">上的設定`<securityTokenHandlerConfiguration>`項目會覆寫上`<identityConfiguration>`項目。</span><span class="sxs-lookup"><span data-stu-id="213ef-143">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="213ef-144">範例</span><span class="sxs-lookup"><span data-stu-id="213ef-144">Example</span></span>  
 <span data-ttu-id="213ef-145">下列 XML 程式碼顯示如何指定組態的簽發者名稱登錄。</span><span class="sxs-lookup"><span data-stu-id="213ef-145">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="213ef-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="213ef-146">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
