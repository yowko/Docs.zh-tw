---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: 9991430f09cb6a63d0a3cdde24a4ff03d3dd746d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165048"
---
# \<issuerNameRegistry>

<span data-ttu-id="a7f11-101">設定權杖處理常式集合中處理常式所使用的簽發者名稱登錄。</span><span class="sxs-lookup"><span data-stu-id="a7f11-101">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerNameRegistry>**  
  
## <a name="syntax"></a><span data-ttu-id="a7f11-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="a7f11-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7f11-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a7f11-103">Attributes and Elements</span></span>  

 <span data-ttu-id="a7f11-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a7f11-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7f11-105">屬性</span><span class="sxs-lookup"><span data-stu-id="a7f11-105">Attributes</span></span>  
  
|<span data-ttu-id="a7f11-106">屬性</span><span class="sxs-lookup"><span data-stu-id="a7f11-106">Attribute</span></span>|<span data-ttu-id="a7f11-107">描述</span><span class="sxs-lookup"><span data-stu-id="a7f11-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a7f11-108">type</span><span class="sxs-lookup"><span data-stu-id="a7f11-108">type</span></span>|<span data-ttu-id="a7f11-109">衍生自類別的型別 <xref:System.IdentityModel.Tokens.IssuerNameRegistry> 。</span><span class="sxs-lookup"><span data-stu-id="a7f11-109">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="a7f11-110">如需如何指定自訂的詳細資訊 `type` ，請參閱 [自訂類型參考]。</span><span class="sxs-lookup"><span data-stu-id="a7f11-110">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a7f11-111">子元素</span><span class="sxs-lookup"><span data-stu-id="a7f11-111">Child Elements</span></span>  
  
|<span data-ttu-id="a7f11-112">項目</span><span class="sxs-lookup"><span data-stu-id="a7f11-112">Element</span></span>|<span data-ttu-id="a7f11-113">描述</span><span class="sxs-lookup"><span data-stu-id="a7f11-113">Description</span></span>|  
|-------------|-----------------|  
|[\<trustedIssuers>](trustedissuers.md)|<span data-ttu-id="a7f11-114">當屬性指定以設定為 `type` 基礎的簽發者名稱登錄 (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> 類別) 時， [\<trustedIssuers>](trustedissuers.md) 必須指定元素。</span><span class="sxs-lookup"><span data-stu-id="a7f11-114">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="a7f11-115">專案 [\<trustedIssuers>](trustedissuers.md) 可以將 `<add>` 、 `<clear>` 或元素做 `<remove>` 為子項目。</span><span class="sxs-lookup"><span data-stu-id="a7f11-115">The [\<trustedIssuers>](trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a7f11-116">父項目</span><span class="sxs-lookup"><span data-stu-id="a7f11-116">Parent Elements</span></span>  
  
|<span data-ttu-id="a7f11-117">項目</span><span class="sxs-lookup"><span data-stu-id="a7f11-117">Element</span></span>|<span data-ttu-id="a7f11-118">描述</span><span class="sxs-lookup"><span data-stu-id="a7f11-118">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="a7f11-119">提供安全性權杖處理常式集合的設定。</span><span class="sxs-lookup"><span data-stu-id="a7f11-119">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7f11-120">備註</span><span class="sxs-lookup"><span data-stu-id="a7f11-120">Remarks</span></span>  

 <span data-ttu-id="a7f11-121">所有簽發者權杖都會使用簽發者名稱登錄進行驗證。</span><span class="sxs-lookup"><span data-stu-id="a7f11-121">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="a7f11-122">這是衍生自類別的物件 <xref:System.IdentityModel.Tokens.IssuerNameRegistry> 。</span><span class="sxs-lookup"><span data-stu-id="a7f11-122">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="a7f11-123">簽發者名稱登錄用來將助憶鍵名稱與所需的密碼編譯內容產生關聯，以驗證對應的簽發者所產生的權杖簽章。</span><span class="sxs-lookup"><span data-stu-id="a7f11-123">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="a7f11-124">簽發者名稱登錄會維護信賴憑證者 (RP) 應用程式信任的簽發者清單。</span><span class="sxs-lookup"><span data-stu-id="a7f11-124">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="a7f11-125">簽發者名稱登錄的類型是使用屬性來指定 `type` 。</span><span class="sxs-lookup"><span data-stu-id="a7f11-125">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="a7f11-126">`<issuerNameRegistry>`元素可以有一或多個子專案，以提供指定類型的設定。</span><span class="sxs-lookup"><span data-stu-id="a7f11-126">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="a7f11-127">您可以藉由覆寫方法，提供處理這些子項目的邏輯 <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> 。</span><span class="sxs-lookup"><span data-stu-id="a7f11-127">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="a7f11-128">WIF 會提供一種現成的單一簽發者名稱登錄類型，也就是 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> 類別。</span><span class="sxs-lookup"><span data-stu-id="a7f11-128">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="a7f11-129">此類別會使用設定中指定的一組受信任的簽發者憑證。</span><span class="sxs-lookup"><span data-stu-id="a7f11-129">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="a7f11-130">它需要子設定元素，在此專案中， `<trustedIssuers>` 會設定信任的簽發者憑證集合。</span><span class="sxs-lookup"><span data-stu-id="a7f11-130">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="a7f11-131">受信任的憑證是使用憑證指紋的 asn.1 編碼形式來指定，並使用、或專案在集合中加入或 `<add>` 移除 `<clear>` `<remove>` 。</span><span class="sxs-lookup"><span data-stu-id="a7f11-131">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="a7f11-132">`<issuerNameRegistry>`元素是由 <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> 類別表示。</span><span class="sxs-lookup"><span data-stu-id="a7f11-132">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a7f11-133">將 `<issuerNameRegistry>` 元素指定為專案的子項目 [\<identityConfiguration>](identityconfiguration.md) 已被取代，但仍支援回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="a7f11-133">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="a7f11-134">元素上的設定會覆 `<securityTokenHandlerConfiguration>` 寫元素上的設定 `<identityConfiguration>` 。</span><span class="sxs-lookup"><span data-stu-id="a7f11-134">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7f11-135">範例</span><span class="sxs-lookup"><span data-stu-id="a7f11-135">Example</span></span>  

 <span data-ttu-id="a7f11-136">下列 XML 說明如何指定以設定為基礎的簽發者名稱登錄。</span><span class="sxs-lookup"><span data-stu-id="a7f11-136">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a7f11-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7f11-137">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
