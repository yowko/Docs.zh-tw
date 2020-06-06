---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: 209e702da80f2569f2b6c068f50f1af4489157f6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251958"
---
# \<issuerNameRegistry>
<span data-ttu-id="eba4c-101">設定權杖處理常式集合中處理常式所使用的簽發者名稱登錄。</span><span class="sxs-lookup"><span data-stu-id="eba4c-101">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerNameRegistry>**  
  
## <a name="syntax"></a><span data-ttu-id="eba4c-102">語法</span><span class="sxs-lookup"><span data-stu-id="eba4c-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eba4c-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="eba4c-103">Attributes and Elements</span></span>  
 <span data-ttu-id="eba4c-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="eba4c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eba4c-105">屬性</span><span class="sxs-lookup"><span data-stu-id="eba4c-105">Attributes</span></span>  
  
|<span data-ttu-id="eba4c-106">屬性</span><span class="sxs-lookup"><span data-stu-id="eba4c-106">Attribute</span></span>|<span data-ttu-id="eba4c-107">描述</span><span class="sxs-lookup"><span data-stu-id="eba4c-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eba4c-108">type</span><span class="sxs-lookup"><span data-stu-id="eba4c-108">type</span></span>|<span data-ttu-id="eba4c-109">衍生自類別的類型 <xref:System.IdentityModel.Tokens.IssuerNameRegistry> 。</span><span class="sxs-lookup"><span data-stu-id="eba4c-109">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="eba4c-110">如需如何指定自訂的詳細資訊 `type` ，請參閱 [自訂類型參考]。</span><span class="sxs-lookup"><span data-stu-id="eba4c-110">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eba4c-111">子元素</span><span class="sxs-lookup"><span data-stu-id="eba4c-111">Child Elements</span></span>  
  
|<span data-ttu-id="eba4c-112">元素</span><span class="sxs-lookup"><span data-stu-id="eba4c-112">Element</span></span>|<span data-ttu-id="eba4c-113">描述</span><span class="sxs-lookup"><span data-stu-id="eba4c-113">Description</span></span>|  
|-------------|-----------------|  
|[\<trustedIssuers>](trustedissuers.md)|<span data-ttu-id="eba4c-114">當屬性指定以設定為 `type` 基礎的簽發者名稱登錄（ <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> 類別）時， [\<trustedIssuers>](trustedissuers.md) 必須指定元素。</span><span class="sxs-lookup"><span data-stu-id="eba4c-114">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="eba4c-115">[\<trustedIssuers>](trustedissuers.md)元素可以接受 `<add>` 、或專案 `<clear>` `<remove>` 做為子專案。</span><span class="sxs-lookup"><span data-stu-id="eba4c-115">The [\<trustedIssuers>](trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eba4c-116">父項目</span><span class="sxs-lookup"><span data-stu-id="eba4c-116">Parent Elements</span></span>  
  
|<span data-ttu-id="eba4c-117">元素</span><span class="sxs-lookup"><span data-stu-id="eba4c-117">Element</span></span>|<span data-ttu-id="eba4c-118">描述</span><span class="sxs-lookup"><span data-stu-id="eba4c-118">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="eba4c-119">提供安全性權杖處理常式集合的設定。</span><span class="sxs-lookup"><span data-stu-id="eba4c-119">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eba4c-120">備註</span><span class="sxs-lookup"><span data-stu-id="eba4c-120">Remarks</span></span>  
 <span data-ttu-id="eba4c-121">所有簽發者權杖都會使用簽發者名稱登錄來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="eba4c-121">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="eba4c-122">這是衍生自類別的物件 <xref:System.IdentityModel.Tokens.IssuerNameRegistry> 。</span><span class="sxs-lookup"><span data-stu-id="eba4c-122">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="eba4c-123">簽發者名稱登錄是用來建立助憶鍵名稱與密碼編譯資料的關聯性，以驗證對應簽發者所產生之權杖的簽章。</span><span class="sxs-lookup"><span data-stu-id="eba4c-123">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="eba4c-124">簽發者名稱登錄會維護信賴憑證者（RP）應用程式所信任的 issuer 清單。</span><span class="sxs-lookup"><span data-stu-id="eba4c-124">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="eba4c-125">簽發者名稱登錄的類型是使用屬性所指定 `type` 。</span><span class="sxs-lookup"><span data-stu-id="eba4c-125">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="eba4c-126">`<issuerNameRegistry>`元素可以有一個或多個子專案，以提供指定之類型的設定。</span><span class="sxs-lookup"><span data-stu-id="eba4c-126">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="eba4c-127">您可以藉由覆寫方法來提供處理這些子專案的邏輯 <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> 。</span><span class="sxs-lookup"><span data-stu-id="eba4c-127">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="eba4c-128">WIF 提供一個現成的簽發者名稱登錄類型，也就是 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> 類別。</span><span class="sxs-lookup"><span data-stu-id="eba4c-128">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="eba4c-129">此類別會使用設定中指定的一組受信任的簽發者憑證。</span><span class="sxs-lookup"><span data-stu-id="eba4c-129">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="eba4c-130">它需要子設定元素，在此專案 `<trustedIssuers>` 下，會在此專案中設定受信任簽發者憑證的集合。</span><span class="sxs-lookup"><span data-stu-id="eba4c-130">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="eba4c-131">受信任的憑證是使用憑證指紋的 asn.1 編碼形式來指定，並使用、或專案從集合中加入或 `<add>` 移除 `<clear>` `<remove>` 。</span><span class="sxs-lookup"><span data-stu-id="eba4c-131">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="eba4c-132">`<issuerNameRegistry>`元素是由 <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> 類別表示。</span><span class="sxs-lookup"><span data-stu-id="eba4c-132">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eba4c-133">將專案指定為專案的 `<issuerNameRegistry>` 子項目 [\<identityConfiguration>](identityconfiguration.md) 已被取代，但仍支援回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="eba4c-133">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="eba4c-134">元素上的設定會覆寫專案上的專案 `<securityTokenHandlerConfiguration>` `<identityConfiguration>` 。</span><span class="sxs-lookup"><span data-stu-id="eba4c-134">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eba4c-135">範例</span><span class="sxs-lookup"><span data-stu-id="eba4c-135">Example</span></span>  
 <span data-ttu-id="eba4c-136">下列 XML 顯示如何指定以設定為基礎的簽發者名稱登錄。</span><span class="sxs-lookup"><span data-stu-id="eba4c-136">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eba4c-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eba4c-137">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
