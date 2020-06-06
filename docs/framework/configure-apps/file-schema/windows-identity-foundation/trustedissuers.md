---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 50fc7194823fb0c5c426fb54ffd50b17c3714ed9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251750"
---
# \<trustedIssuers>
<span data-ttu-id="19c33-101">設定以設定為基礎的簽發者名稱登錄（）所使用的受信任簽發者憑證清單 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> 。</span><span class="sxs-lookup"><span data-stu-id="19c33-101">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerNameRegistry>**](issuernameregistry.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trustedIssuers>**  
  
## <a name="syntax"></a><span data-ttu-id="19c33-102">語法</span><span class="sxs-lookup"><span data-stu-id="19c33-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19c33-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="19c33-103">Attributes and Elements</span></span>  
 <span data-ttu-id="19c33-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="19c33-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19c33-105">屬性</span><span class="sxs-lookup"><span data-stu-id="19c33-105">Attributes</span></span>  
 <span data-ttu-id="19c33-106">無</span><span class="sxs-lookup"><span data-stu-id="19c33-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="19c33-107">子元素</span><span class="sxs-lookup"><span data-stu-id="19c33-107">Child Elements</span></span>  
  
|<span data-ttu-id="19c33-108">元素</span><span class="sxs-lookup"><span data-stu-id="19c33-108">Element</span></span>|<span data-ttu-id="19c33-109">描述</span><span class="sxs-lookup"><span data-stu-id="19c33-109">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="19c33-110">將憑證新增至受信任簽發者的集合。</span><span class="sxs-lookup"><span data-stu-id="19c33-110">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="19c33-111">憑證是以 `thumbprint` 屬性指定。</span><span class="sxs-lookup"><span data-stu-id="19c33-111">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="19c33-112">此為必要屬性，且應包含憑證指紋的 asn.1 編碼形式。</span><span class="sxs-lookup"><span data-stu-id="19c33-112">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="19c33-113">`name`屬性是選擇性的，可以用來指定憑證的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="19c33-113">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="19c33-114">清除受信任簽發者集合中的所有憑證。</span><span class="sxs-lookup"><span data-stu-id="19c33-114">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="19c33-115">從受信任簽發者的集合中移除憑證。</span><span class="sxs-lookup"><span data-stu-id="19c33-115">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="19c33-116">憑證是以 `thumbprint` 屬性指定。</span><span class="sxs-lookup"><span data-stu-id="19c33-116">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="19c33-117">這是必要屬性。</span><span class="sxs-lookup"><span data-stu-id="19c33-117">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="19c33-118">父項目</span><span class="sxs-lookup"><span data-stu-id="19c33-118">Parent Elements</span></span>  
  
|<span data-ttu-id="19c33-119">元素</span><span class="sxs-lookup"><span data-stu-id="19c33-119">Element</span></span>|<span data-ttu-id="19c33-120">描述</span><span class="sxs-lookup"><span data-stu-id="19c33-120">Description</span></span>|  
|-------------|-----------------|  
|[\<issuerNameRegistry>](issuernameregistry.md)|<span data-ttu-id="19c33-121">設定簽發者名稱登錄。</span><span class="sxs-lookup"><span data-stu-id="19c33-121">Configures the issuer name registry.</span></span> <span data-ttu-id="19c33-122">**重要事項：** `type`元素的屬性 `<issuerNameRegistry>` 必須參考類別，專案 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> `<trustedIssuers>` 才會是有效的。</span><span class="sxs-lookup"><span data-stu-id="19c33-122">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19c33-123">備註</span><span class="sxs-lookup"><span data-stu-id="19c33-123">Remarks</span></span>  
 <span data-ttu-id="19c33-124">Windows Identity Foundation （WIF）提供類別的單一實作為類別 <xref:System.IdentityModel.Tokens.IssuerNameRegistry> <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> 。</span><span class="sxs-lookup"><span data-stu-id="19c33-124">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="19c33-125">設定簽發者名稱登錄會維護從設定載入之受信任簽發者的清單。</span><span class="sxs-lookup"><span data-stu-id="19c33-125">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="19c33-126">此清單會將每個簽發者名稱與 x.509 憑證建立關聯，以驗證簽發者所產生之權杖的簽章。</span><span class="sxs-lookup"><span data-stu-id="19c33-126">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="19c33-127">受信任簽發者憑證的清單是在元素下指定 `<trustedIssuers>` 。</span><span class="sxs-lookup"><span data-stu-id="19c33-127">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="19c33-128">清單中的每個元素會將助憶鍵簽發者名稱與 x.509 憑證產生關聯，以驗證該簽發者所產生之權杖的簽章。</span><span class="sxs-lookup"><span data-stu-id="19c33-128">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="19c33-129">受信任的憑證是使用憑證指紋的 asn.1 編碼形式來指定，並使用元素來新增集合 `<add>` 。</span><span class="sxs-lookup"><span data-stu-id="19c33-129">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="19c33-130">您可以使用和元素，從清單中清除或移除簽發者（憑證） `<clear>` `<remove>` 。</span><span class="sxs-lookup"><span data-stu-id="19c33-130">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="19c33-131">`type`元素的屬性 `<issuerNameRegistry>` 必須參考類別，專案 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> `<trustedIssuers>` 才會是有效的。</span><span class="sxs-lookup"><span data-stu-id="19c33-131">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19c33-132">範例</span><span class="sxs-lookup"><span data-stu-id="19c33-132">Example</span></span>  
 <span data-ttu-id="19c33-133">下列 XML 顯示如何指定以設定為基礎的簽發者名稱登錄。</span><span class="sxs-lookup"><span data-stu-id="19c33-133">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="19c33-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19c33-134">See also</span></span>

- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
