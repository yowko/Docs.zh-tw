---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 08cddd19f40f039f86e100cc7ee6a78633502eb2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185557"
---
# \<trustedIssuers>

<span data-ttu-id="1b5fe-101">設定以設定為基礎的簽發者名稱登錄 () 所使用的受信任簽發者憑證清單 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> 。</span><span class="sxs-lookup"><span data-stu-id="1b5fe-101">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerNameRegistry>**](issuernameregistry.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trustedIssuers>**  
  
## <a name="syntax"></a><span data-ttu-id="1b5fe-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="1b5fe-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b5fe-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1b5fe-103">Attributes and Elements</span></span>  

 <span data-ttu-id="1b5fe-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1b5fe-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b5fe-105">屬性</span><span class="sxs-lookup"><span data-stu-id="1b5fe-105">Attributes</span></span>  

 <span data-ttu-id="1b5fe-106">無</span><span class="sxs-lookup"><span data-stu-id="1b5fe-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1b5fe-107">子元素</span><span class="sxs-lookup"><span data-stu-id="1b5fe-107">Child Elements</span></span>  
  
|<span data-ttu-id="1b5fe-108">項目</span><span class="sxs-lookup"><span data-stu-id="1b5fe-108">Element</span></span>|<span data-ttu-id="1b5fe-109">描述</span><span class="sxs-lookup"><span data-stu-id="1b5fe-109">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="1b5fe-110">將憑證加入至受信任簽發者的集合。</span><span class="sxs-lookup"><span data-stu-id="1b5fe-110">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="1b5fe-111">憑證是以 `thumbprint` 屬性指定。</span><span class="sxs-lookup"><span data-stu-id="1b5fe-111">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="1b5fe-112">這個屬性是必要的，而且應該包含憑證指紋的 asn.1 編碼形式。</span><span class="sxs-lookup"><span data-stu-id="1b5fe-112">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="1b5fe-113">`name`屬性是選擇性的，可以用來指定憑證的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="1b5fe-113">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="1b5fe-114">清除受信任簽發者集合中的所有憑證。</span><span class="sxs-lookup"><span data-stu-id="1b5fe-114">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="1b5fe-115">從受信任簽發者的集合中移除憑證。</span><span class="sxs-lookup"><span data-stu-id="1b5fe-115">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="1b5fe-116">憑證是以 `thumbprint` 屬性指定。</span><span class="sxs-lookup"><span data-stu-id="1b5fe-116">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="1b5fe-117">這是必要屬性。</span><span class="sxs-lookup"><span data-stu-id="1b5fe-117">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1b5fe-118">父項目</span><span class="sxs-lookup"><span data-stu-id="1b5fe-118">Parent Elements</span></span>  
  
|<span data-ttu-id="1b5fe-119">項目</span><span class="sxs-lookup"><span data-stu-id="1b5fe-119">Element</span></span>|<span data-ttu-id="1b5fe-120">描述</span><span class="sxs-lookup"><span data-stu-id="1b5fe-120">Description</span></span>|  
|-------------|-----------------|  
|[\<issuerNameRegistry>](issuernameregistry.md)|<span data-ttu-id="1b5fe-121">設定簽發者名稱登錄。</span><span class="sxs-lookup"><span data-stu-id="1b5fe-121">Configures the issuer name registry.</span></span> <span data-ttu-id="1b5fe-122">**重要事項：**  專案的 `type` 屬性 `<issuerNameRegistry>` 必須參考 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> 類別， `<trustedIssuers>` 元素才能有效。</span><span class="sxs-lookup"><span data-stu-id="1b5fe-122">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b5fe-123">備註</span><span class="sxs-lookup"><span data-stu-id="1b5fe-123">Remarks</span></span>  

 <span data-ttu-id="1b5fe-124">Windows Identity Foundation (WIF) 提供類別的單一實作為類別 <xref:System.IdentityModel.Tokens.IssuerNameRegistry> <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> 。</span><span class="sxs-lookup"><span data-stu-id="1b5fe-124">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="1b5fe-125">設定簽發者名稱登錄會維護從設定載入的受信任簽發者清單。</span><span class="sxs-lookup"><span data-stu-id="1b5fe-125">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="1b5fe-126">此清單會將每個簽發者名稱與驗證簽發者所產生之權杖簽章所需的 x.509 憑證產生關聯。</span><span class="sxs-lookup"><span data-stu-id="1b5fe-126">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="1b5fe-127">受信任的簽發者憑證清單是在元素下指定 `<trustedIssuers>` 。</span><span class="sxs-lookup"><span data-stu-id="1b5fe-127">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="1b5fe-128">清單中的每個專案會將助記者名稱與 x.509 憑證產生關聯，以驗證該簽發者所產生之權杖的簽章。</span><span class="sxs-lookup"><span data-stu-id="1b5fe-128">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="1b5fe-129">受信任的憑證是使用憑證指紋的 asn.1 編碼形式來指定，並使用元素加入集合 `<add>` 。</span><span class="sxs-lookup"><span data-stu-id="1b5fe-129">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="1b5fe-130">您可以使用和元素，從清單中清除或移除簽發者 (憑證) `<clear>` `<remove>` 。</span><span class="sxs-lookup"><span data-stu-id="1b5fe-130">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="1b5fe-131">專案的 `type` 屬性 `<issuerNameRegistry>` 必須參考 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> 類別， `<trustedIssuers>` 元素才能有效。</span><span class="sxs-lookup"><span data-stu-id="1b5fe-131">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b5fe-132">範例</span><span class="sxs-lookup"><span data-stu-id="1b5fe-132">Example</span></span>  

 <span data-ttu-id="1b5fe-133">下列 XML 說明如何指定以設定為基礎的簽發者名稱登錄。</span><span class="sxs-lookup"><span data-stu-id="1b5fe-133">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1b5fe-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b5fe-134">See also</span></span>

- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
