---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: ae263a4590cc523c64306ff5d53e54b5190ca510
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202517"
---
# <a name="issuernameregistry"></a><span data-ttu-id="2358c-101">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="2358c-101">\<issuerNameRegistry></span></span>
<span data-ttu-id="2358c-102">設定簽發者名稱登錄，可由權杖處理常式集合中的處理常式。</span><span class="sxs-lookup"><span data-stu-id="2358c-102">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
 <span data-ttu-id="2358c-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="2358c-103">\<system.identityModel></span></span>  
<span data-ttu-id="2358c-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="2358c-104">\<identityConfiguration></span></span>  
<span data-ttu-id="2358c-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="2358c-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="2358c-106">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="2358c-106">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="2358c-107">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="2358c-107">\<issuerNameRegistry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2358c-108">語法</span><span class="sxs-lookup"><span data-stu-id="2358c-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2358c-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2358c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2358c-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2358c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2358c-111">屬性</span><span class="sxs-lookup"><span data-stu-id="2358c-111">Attributes</span></span>  
  
|<span data-ttu-id="2358c-112">屬性</span><span class="sxs-lookup"><span data-stu-id="2358c-112">Attribute</span></span>|<span data-ttu-id="2358c-113">描述</span><span class="sxs-lookup"><span data-stu-id="2358c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2358c-114">類型</span><span class="sxs-lookup"><span data-stu-id="2358c-114">type</span></span>|<span data-ttu-id="2358c-115">衍生自類型<xref:System.IdentityModel.Tokens.IssuerNameRegistry>類別。</span><span class="sxs-lookup"><span data-stu-id="2358c-115">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="2358c-116">如需有關如何指定自訂`type`，請參閱 [自訂型別參考]。</span><span class="sxs-lookup"><span data-stu-id="2358c-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2358c-117">子元素</span><span class="sxs-lookup"><span data-stu-id="2358c-117">Child Elements</span></span>  
  
|<span data-ttu-id="2358c-118">項目</span><span class="sxs-lookup"><span data-stu-id="2358c-118">Element</span></span>|<span data-ttu-id="2358c-119">描述</span><span class="sxs-lookup"><span data-stu-id="2358c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2358c-120">\<trustedIssuers></span><span class="sxs-lookup"><span data-stu-id="2358c-120">\<trustedIssuers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)|<span data-ttu-id="2358c-121">當`type`屬性會指定以組態為基礎的簽發者名稱登錄 (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>類別)，則[ \<trustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)必須指定項目。</span><span class="sxs-lookup"><span data-stu-id="2358c-121">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="2358c-122">[ \<TrustedIssuers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)項目可以採取`<add>`， `<clear>`，或`<remove>`項目與子項目。</span><span class="sxs-lookup"><span data-stu-id="2358c-122">The [\<trustedIssuers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2358c-123">父項目</span><span class="sxs-lookup"><span data-stu-id="2358c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2358c-124">項目</span><span class="sxs-lookup"><span data-stu-id="2358c-124">Element</span></span>|<span data-ttu-id="2358c-125">描述</span><span class="sxs-lookup"><span data-stu-id="2358c-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2358c-126">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="2358c-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="2358c-127">提供組態集合的安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="2358c-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2358c-128">備註</span><span class="sxs-lookup"><span data-stu-id="2358c-128">Remarks</span></span>  
 <span data-ttu-id="2358c-129">所有簽發者權杖會使用簽發者名稱登錄進行驗證。</span><span class="sxs-lookup"><span data-stu-id="2358c-129">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="2358c-130">這是衍生自物件<xref:System.IdentityModel.Tokens.IssuerNameRegistry>類別。</span><span class="sxs-lookup"><span data-stu-id="2358c-130">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="2358c-131">簽發者名稱登錄來建立助憶名稱，才能驗證對應簽發者所產生之權杖的簽章的加密編譯內容。</span><span class="sxs-lookup"><span data-stu-id="2358c-131">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="2358c-132">簽發者名稱登錄會維護信賴憑證者 (rp) 應用程式所信任的簽發者清單。</span><span class="sxs-lookup"><span data-stu-id="2358c-132">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="2358c-133">使用指定的簽發者名稱登錄型別`type`屬性。</span><span class="sxs-lookup"><span data-stu-id="2358c-133">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="2358c-134">`<issuerNameRegistry>`元素可能具有一或多個的子元素會提供指定之類型的組態。</span><span class="sxs-lookup"><span data-stu-id="2358c-134">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="2358c-135">提供藉由覆寫會處理這些子元素的邏輯<xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="2358c-135">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="2358c-136">WIF 提供單一的簽發者名稱登錄型別，根據預設，<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>類別。</span><span class="sxs-lookup"><span data-stu-id="2358c-136">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="2358c-137">這個類別會使用一組的組態中指定的受信任簽發者憑證。</span><span class="sxs-lookup"><span data-stu-id="2358c-137">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="2358c-138">它需要的子組態項目， `<trustedIssuers>`，在設定受信任簽發者憑證的集合。</span><span class="sxs-lookup"><span data-stu-id="2358c-138">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="2358c-139">受信任的憑證會指定使用 ASN.1 編碼的憑證指紋的格式及新增或移除集合中使用`<add>`， `<clear>`，或`<remove>`項目。</span><span class="sxs-lookup"><span data-stu-id="2358c-139">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="2358c-140">`<issuerNameRegistry>`項目由<xref:System.IdentityModel.Configuration.IssuerNameRegistryElement>類別。</span><span class="sxs-lookup"><span data-stu-id="2358c-140">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2358c-141">指定`<issuerNameRegistry>`元素的子元素當做[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目已被取代，但仍支援回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="2358c-141">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="2358c-142">上的設定`<securityTokenHandlerConfiguration>`項目會覆寫上`<identityConfiguration>`項目。</span><span class="sxs-lookup"><span data-stu-id="2358c-142">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2358c-143">範例</span><span class="sxs-lookup"><span data-stu-id="2358c-143">Example</span></span>  
 <span data-ttu-id="2358c-144">下列 XML 程式碼顯示如何指定組態的簽發者名稱登錄。</span><span class="sxs-lookup"><span data-stu-id="2358c-144">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2358c-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2358c-145">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
