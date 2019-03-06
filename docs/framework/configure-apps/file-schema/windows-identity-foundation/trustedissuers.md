---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: bb4cb5178885b90ef25ee827c2f11593ead6e73d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354553"
---
# <a name="trustedissuers"></a><span data-ttu-id="bc426-101">\<trustedIssuers></span><span class="sxs-lookup"><span data-stu-id="bc426-101">\<trustedIssuers></span></span>
<span data-ttu-id="bc426-102">設定使用的組態為基礎的簽發者名稱登錄的受信任簽發者憑證的清單 (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>)。</span><span class="sxs-lookup"><span data-stu-id="bc426-102">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
 <span data-ttu-id="bc426-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="bc426-103">\<system.identityModel></span></span>  
<span data-ttu-id="bc426-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="bc426-104">\<identityConfiguration></span></span>  
<span data-ttu-id="bc426-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="bc426-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="bc426-106">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="bc426-106">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="bc426-107">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="bc426-107">\<issuerNameRegistry></span></span>  
<span data-ttu-id="bc426-108">\<trustedIssuers></span><span class="sxs-lookup"><span data-stu-id="bc426-108">\<trustedIssuers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc426-109">語法</span><span class="sxs-lookup"><span data-stu-id="bc426-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc426-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bc426-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bc426-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="bc426-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc426-112">屬性</span><span class="sxs-lookup"><span data-stu-id="bc426-112">Attributes</span></span>  
 <span data-ttu-id="bc426-113">無</span><span class="sxs-lookup"><span data-stu-id="bc426-113">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="bc426-114">子元素</span><span class="sxs-lookup"><span data-stu-id="bc426-114">Child Elements</span></span>  
  
|<span data-ttu-id="bc426-115">項目</span><span class="sxs-lookup"><span data-stu-id="bc426-115">Element</span></span>|<span data-ttu-id="bc426-116">描述</span><span class="sxs-lookup"><span data-stu-id="bc426-116">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="bc426-117">將憑證加入至受信任簽發者的集合。</span><span class="sxs-lookup"><span data-stu-id="bc426-117">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="bc426-118">使用指定的憑證`thumbprint`屬性。</span><span class="sxs-lookup"><span data-stu-id="bc426-118">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="bc426-119">這個屬性是必要的而且應該包含憑證指紋的 ASN.1 編碼形式。</span><span class="sxs-lookup"><span data-stu-id="bc426-119">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="bc426-120">`name`屬性是選擇性的而且可用來指定憑證的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="bc426-120">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="bc426-121">清除集合中的受信任簽發者的所有憑證。</span><span class="sxs-lookup"><span data-stu-id="bc426-121">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="bc426-122">從受信任簽發者的集合中移除憑證。</span><span class="sxs-lookup"><span data-stu-id="bc426-122">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="bc426-123">使用指定的憑證`thumbprint`屬性。</span><span class="sxs-lookup"><span data-stu-id="bc426-123">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="bc426-124">這是必要屬性。</span><span class="sxs-lookup"><span data-stu-id="bc426-124">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="bc426-125">父項目</span><span class="sxs-lookup"><span data-stu-id="bc426-125">Parent Elements</span></span>  
  
|<span data-ttu-id="bc426-126">項目</span><span class="sxs-lookup"><span data-stu-id="bc426-126">Element</span></span>|<span data-ttu-id="bc426-127">描述</span><span class="sxs-lookup"><span data-stu-id="bc426-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc426-128">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="bc426-128">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="bc426-129">設定簽發者名稱登錄。</span><span class="sxs-lookup"><span data-stu-id="bc426-129">Configures the issuer name registry.</span></span> <span data-ttu-id="bc426-130">**重要：**`type`的屬性`<issuerNameRegistry>`元素必須參照<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>類別`<trustedIssuers>`為有效的項目。</span><span class="sxs-lookup"><span data-stu-id="bc426-130">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc426-131">備註</span><span class="sxs-lookup"><span data-stu-id="bc426-131">Remarks</span></span>  
 <span data-ttu-id="bc426-132">Windows Identity Foundation (WIF) 提供的單一實作<xref:System.IdentityModel.Tokens.IssuerNameRegistry>根據預設，類別<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>類別。</span><span class="sxs-lookup"><span data-stu-id="bc426-132">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="bc426-133">設定簽發者名稱登錄會維護從組態載入信任的簽發者清單。</span><span class="sxs-lookup"><span data-stu-id="bc426-133">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="bc426-134">清單會將每個簽發者名稱關聯才能驗證簽發者所產生之權杖的簽章的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="bc426-134">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="bc426-135">受信任的簽發者憑證的清單下，會指定`<trustedIssuers>`項目。</span><span class="sxs-lookup"><span data-stu-id="bc426-135">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="bc426-136">在清單中的每個項目關聯，才能驗證該簽發者所產生之權杖的簽章的 X.509 憑證的助憶鍵簽發者名稱。</span><span class="sxs-lookup"><span data-stu-id="bc426-136">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="bc426-137">受信任的憑證使用 ASN.1 編碼的憑證指紋的格式指定，而且會藉由新增集合`<add>`項目。</span><span class="sxs-lookup"><span data-stu-id="bc426-137">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="bc426-138">您可以清除，或從清單中移除簽發者 （憑證），使用`<clear>`和`<remove>`項目。</span><span class="sxs-lookup"><span data-stu-id="bc426-138">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="bc426-139">`type`的屬性`<issuerNameRegistry>`元素必須參照<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>類別`<trustedIssuers>`為有效的項目。</span><span class="sxs-lookup"><span data-stu-id="bc426-139">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc426-140">範例</span><span class="sxs-lookup"><span data-stu-id="bc426-140">Example</span></span>  
 <span data-ttu-id="bc426-141">下列 XML 程式碼顯示如何指定組態的簽發者名稱登錄。</span><span class="sxs-lookup"><span data-stu-id="bc426-141">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bc426-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc426-142">See also</span></span>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
