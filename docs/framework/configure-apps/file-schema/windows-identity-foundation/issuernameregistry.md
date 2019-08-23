---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: d0a1f8dd0c29aaee56c2ca1162cc70cc1e5ed106
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942672"
---
# <a name="issuernameregistry"></a><span data-ttu-id="c2bc1-101">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="c2bc1-101">\<issuerNameRegistry></span></span>
<span data-ttu-id="c2bc1-102">設定權杖處理常式集合中處理常式所使用的簽發者名稱登錄。</span><span class="sxs-lookup"><span data-stu-id="c2bc1-102">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
 <span data-ttu-id="c2bc1-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="c2bc1-103">\<system.identityModel></span></span>  
<span data-ttu-id="c2bc1-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="c2bc1-104">\<identityConfiguration></span></span>  
<span data-ttu-id="c2bc1-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="c2bc1-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="c2bc1-106">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="c2bc1-106">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="c2bc1-107">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="c2bc1-107">\<issuerNameRegistry></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2bc1-108">語法</span><span class="sxs-lookup"><span data-stu-id="c2bc1-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2bc1-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c2bc1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c2bc1-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c2bc1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2bc1-111">屬性</span><span class="sxs-lookup"><span data-stu-id="c2bc1-111">Attributes</span></span>  
  
|<span data-ttu-id="c2bc1-112">屬性</span><span class="sxs-lookup"><span data-stu-id="c2bc1-112">Attribute</span></span>|<span data-ttu-id="c2bc1-113">描述</span><span class="sxs-lookup"><span data-stu-id="c2bc1-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c2bc1-114">型別</span><span class="sxs-lookup"><span data-stu-id="c2bc1-114">type</span></span>|<span data-ttu-id="c2bc1-115">衍生自<xref:System.IdentityModel.Tokens.IssuerNameRegistry>類別的類型。</span><span class="sxs-lookup"><span data-stu-id="c2bc1-115">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="c2bc1-116">如需如何指定自訂`type`的詳細資訊, 請參閱 [自訂類型參考]。</span><span class="sxs-lookup"><span data-stu-id="c2bc1-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c2bc1-117">子元素</span><span class="sxs-lookup"><span data-stu-id="c2bc1-117">Child Elements</span></span>  
  
|<span data-ttu-id="c2bc1-118">項目</span><span class="sxs-lookup"><span data-stu-id="c2bc1-118">Element</span></span>|<span data-ttu-id="c2bc1-119">描述</span><span class="sxs-lookup"><span data-stu-id="c2bc1-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c2bc1-120">\<trustedIssuers></span><span class="sxs-lookup"><span data-stu-id="c2bc1-120">\<trustedIssuers></span></span>](trustedissuers.md)|<span data-ttu-id="c2bc1-121">當屬性指定以設定為基礎的簽發者名稱登錄<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> (類別) 時, [ \<必須指定 s >](trustedissuers.md)元素。 `type`</span><span class="sxs-lookup"><span data-stu-id="c2bc1-121">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="c2bc1-122">S > 元素可以接受`<add>`、 `<clear>`或`<remove>`專案做為子專案。 [ \< ](trustedissuers.md)</span><span class="sxs-lookup"><span data-stu-id="c2bc1-122">The [\<trustedIssuers>](trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c2bc1-123">父項目</span><span class="sxs-lookup"><span data-stu-id="c2bc1-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c2bc1-124">項目</span><span class="sxs-lookup"><span data-stu-id="c2bc1-124">Element</span></span>|<span data-ttu-id="c2bc1-125">描述</span><span class="sxs-lookup"><span data-stu-id="c2bc1-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c2bc1-126">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="c2bc1-126">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="c2bc1-127">提供安全性權杖處理常式集合的設定。</span><span class="sxs-lookup"><span data-stu-id="c2bc1-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2bc1-128">備註</span><span class="sxs-lookup"><span data-stu-id="c2bc1-128">Remarks</span></span>  
 <span data-ttu-id="c2bc1-129">所有簽發者權杖都會使用簽發者名稱登錄來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="c2bc1-129">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="c2bc1-130">這是衍生自<xref:System.IdentityModel.Tokens.IssuerNameRegistry>類別的物件。</span><span class="sxs-lookup"><span data-stu-id="c2bc1-130">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="c2bc1-131">簽發者名稱登錄是用來建立助憶鍵名稱與密碼編譯資料的關聯性, 以驗證對應簽發者所產生之權杖的簽章。</span><span class="sxs-lookup"><span data-stu-id="c2bc1-131">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="c2bc1-132">簽發者名稱登錄會維護信賴憑證者 (RP) 應用程式所信任的 issuer 清單。</span><span class="sxs-lookup"><span data-stu-id="c2bc1-132">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="c2bc1-133">簽發者名稱登錄的類型是使用`type`屬性所指定。</span><span class="sxs-lookup"><span data-stu-id="c2bc1-133">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="c2bc1-134">`<issuerNameRegistry>`元素可以有一個或多個子專案, 以提供指定之類型的設定。</span><span class="sxs-lookup"><span data-stu-id="c2bc1-134">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="c2bc1-135">您可以藉由覆寫<xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A>方法來提供處理這些子專案的邏輯。</span><span class="sxs-lookup"><span data-stu-id="c2bc1-135">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="c2bc1-136">WIF 提供一個現成的簽發者名稱登錄類型, 也就是<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>類別。</span><span class="sxs-lookup"><span data-stu-id="c2bc1-136">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="c2bc1-137">此類別會使用設定中指定的一組受信任的簽發者憑證。</span><span class="sxs-lookup"><span data-stu-id="c2bc1-137">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="c2bc1-138">它需要子設定元素, `<trustedIssuers>`在此專案下, 會在此專案中設定受信任簽發者憑證的集合。</span><span class="sxs-lookup"><span data-stu-id="c2bc1-138">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="c2bc1-139">受信任的憑證是使用憑證指紋的 asn.1 編碼形式來指定, 並使用`<add>`、 `<clear>`或`<remove>`專案從集合中加入或移除。</span><span class="sxs-lookup"><span data-stu-id="c2bc1-139">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="c2bc1-140">`<issuerNameRegistry>`元素是<xref:System.IdentityModel.Configuration.IssuerNameRegistryElement>由類別表示。</span><span class="sxs-lookup"><span data-stu-id="c2bc1-140">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c2bc1-141">將專案指定為[ \<identityConfiguration >](identityconfiguration.md)專案的子項目已被取代, 但仍支援回溯相容性。 `<issuerNameRegistry>`</span><span class="sxs-lookup"><span data-stu-id="c2bc1-141">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="c2bc1-142">元素上的`<securityTokenHandlerConfiguration>`設定會覆寫專案`<identityConfiguration>`上的專案。</span><span class="sxs-lookup"><span data-stu-id="c2bc1-142">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2bc1-143">範例</span><span class="sxs-lookup"><span data-stu-id="c2bc1-143">Example</span></span>  
 <span data-ttu-id="c2bc1-144">下列 XML 顯示如何指定以設定為基礎的簽發者名稱登錄。</span><span class="sxs-lookup"><span data-stu-id="c2bc1-144">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c2bc1-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2bc1-145">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
