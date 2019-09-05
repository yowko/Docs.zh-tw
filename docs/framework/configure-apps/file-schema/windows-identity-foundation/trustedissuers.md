---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 50fc7194823fb0c5c426fb54ffd50b17c3714ed9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251750"
---
# <a name="trustedissuers"></a><span data-ttu-id="9faf5-101">\<trustedIssuers></span><span class="sxs-lookup"><span data-stu-id="9faf5-101">\<trustedIssuers></span></span>
<span data-ttu-id="9faf5-102">設定以設定為基礎的簽發者名稱登錄 (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>) 所使用的受信任簽發者憑證清單。</span><span class="sxs-lookup"><span data-stu-id="9faf5-102">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
<span data-ttu-id="9faf5-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9faf5-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9faf5-104">&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="9faf5-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="9faf5-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="9faf5-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="9faf5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="9faf5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="9faf5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="9faf5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="9faf5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuerNameRegistry >** ](issuernameregistry.md)</span><span class="sxs-lookup"><span data-stu-id="9faf5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerNameRegistry>**](issuernameregistry.md)</span></span>\
<span data-ttu-id="9faf5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<s >**</span><span class="sxs-lookup"><span data-stu-id="9faf5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trustedIssuers>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9faf5-110">語法</span><span class="sxs-lookup"><span data-stu-id="9faf5-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry>  
          <trustedIssuers>  
            <add thumbprint=xs:string name=xs:string>  
            <clear>  
            <remove thumbprint=xs:string>  
          </trustedIssuers>  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9faf5-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9faf5-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9faf5-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9faf5-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9faf5-113">屬性</span><span class="sxs-lookup"><span data-stu-id="9faf5-113">Attributes</span></span>  
 <span data-ttu-id="9faf5-114">None</span><span class="sxs-lookup"><span data-stu-id="9faf5-114">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9faf5-115">子元素</span><span class="sxs-lookup"><span data-stu-id="9faf5-115">Child Elements</span></span>  
  
|<span data-ttu-id="9faf5-116">項目</span><span class="sxs-lookup"><span data-stu-id="9faf5-116">Element</span></span>|<span data-ttu-id="9faf5-117">描述</span><span class="sxs-lookup"><span data-stu-id="9faf5-117">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="9faf5-118">將憑證新增至受信任簽發者的集合。</span><span class="sxs-lookup"><span data-stu-id="9faf5-118">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="9faf5-119">憑證是以`thumbprint`屬性指定。</span><span class="sxs-lookup"><span data-stu-id="9faf5-119">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="9faf5-120">此為必要屬性, 且應包含憑證指紋的 asn.1 編碼形式。</span><span class="sxs-lookup"><span data-stu-id="9faf5-120">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="9faf5-121">屬性`name`是選擇性的, 可以用來指定憑證的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="9faf5-121">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="9faf5-122">清除受信任簽發者集合中的所有憑證。</span><span class="sxs-lookup"><span data-stu-id="9faf5-122">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="9faf5-123">從受信任簽發者的集合中移除憑證。</span><span class="sxs-lookup"><span data-stu-id="9faf5-123">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="9faf5-124">憑證是以`thumbprint`屬性指定。</span><span class="sxs-lookup"><span data-stu-id="9faf5-124">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="9faf5-125">這是必要屬性。</span><span class="sxs-lookup"><span data-stu-id="9faf5-125">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9faf5-126">父項目</span><span class="sxs-lookup"><span data-stu-id="9faf5-126">Parent Elements</span></span>  
  
|<span data-ttu-id="9faf5-127">項目</span><span class="sxs-lookup"><span data-stu-id="9faf5-127">Element</span></span>|<span data-ttu-id="9faf5-128">描述</span><span class="sxs-lookup"><span data-stu-id="9faf5-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9faf5-129">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="9faf5-129">\<issuerNameRegistry></span></span>](issuernameregistry.md)|<span data-ttu-id="9faf5-130">設定簽發者名稱登錄。</span><span class="sxs-lookup"><span data-stu-id="9faf5-130">Configures the issuer name registry.</span></span> <span data-ttu-id="9faf5-131">**重要：** `<issuerNameRegistry>` <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>元素的`type`屬性必須`<trustedIssuers>`參考類別, 專案才會是有效的。</span><span class="sxs-lookup"><span data-stu-id="9faf5-131">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9faf5-132">備註</span><span class="sxs-lookup"><span data-stu-id="9faf5-132">Remarks</span></span>  
 <span data-ttu-id="9faf5-133">Windows Identity Foundation (WIF) 提供<xref:System.IdentityModel.Tokens.IssuerNameRegistry>類別<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>的單一實作為類別。</span><span class="sxs-lookup"><span data-stu-id="9faf5-133">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="9faf5-134">設定簽發者名稱登錄會維護從設定載入之受信任簽發者的清單。</span><span class="sxs-lookup"><span data-stu-id="9faf5-134">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="9faf5-135">此清單會將每個簽發者名稱與 x.509 憑證建立關聯, 以驗證簽發者所產生之權杖的簽章。</span><span class="sxs-lookup"><span data-stu-id="9faf5-135">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="9faf5-136">受信任簽發者憑證的清單是在`<trustedIssuers>`元素下指定。</span><span class="sxs-lookup"><span data-stu-id="9faf5-136">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="9faf5-137">清單中的每個元素會將助憶鍵簽發者名稱與 x.509 憑證產生關聯, 以驗證該簽發者所產生之權杖的簽章。</span><span class="sxs-lookup"><span data-stu-id="9faf5-137">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="9faf5-138">受信任的憑證是使用憑證指紋的 asn.1 編碼形式來指定, 並使用`<add>`元素來新增集合。</span><span class="sxs-lookup"><span data-stu-id="9faf5-138">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="9faf5-139">您可以使用`<clear>`和`<remove>`元素, 從清單中清除或移除簽發者 (憑證)。</span><span class="sxs-lookup"><span data-stu-id="9faf5-139">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="9faf5-140">`<issuerNameRegistry>` <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>元素的`type`屬性必須`<trustedIssuers>`參考類別, 專案才會是有效的。</span><span class="sxs-lookup"><span data-stu-id="9faf5-140">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9faf5-141">範例</span><span class="sxs-lookup"><span data-stu-id="9faf5-141">Example</span></span>  
 <span data-ttu-id="9faf5-142">下列 XML 顯示如何指定以設定為基礎的簽發者名稱登錄。</span><span class="sxs-lookup"><span data-stu-id="9faf5-142">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9faf5-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9faf5-143">See also</span></span>

- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
