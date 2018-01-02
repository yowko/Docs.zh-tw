---
title: '&lt;trustedIssuers&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 26f3d4f0b272168083bed2bbe249532181a6db67
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="lttrustedissuersgt"></a><span data-ttu-id="f9244-102">&lt;trustedIssuers&gt;</span><span class="sxs-lookup"><span data-stu-id="f9244-102">&lt;trustedIssuers&gt;</span></span>
<span data-ttu-id="f9244-103">設定使用的組態為基礎的簽發者名稱登錄的受信任簽發者憑證的清單 (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>)。</span><span class="sxs-lookup"><span data-stu-id="f9244-103">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
 <span data-ttu-id="f9244-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="f9244-104">\<system.identityModel></span></span>  
<span data-ttu-id="f9244-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="f9244-105">\<identityConfiguration></span></span>  
<span data-ttu-id="f9244-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="f9244-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="f9244-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="f9244-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="f9244-108">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="f9244-108">\<issuerNameRegistry></span></span>  
<span data-ttu-id="f9244-109">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="f9244-109">\<trustedIssuers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9244-110">語法</span><span class="sxs-lookup"><span data-stu-id="f9244-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9244-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f9244-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f9244-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f9244-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9244-113">屬性</span><span class="sxs-lookup"><span data-stu-id="f9244-113">Attributes</span></span>  
 <span data-ttu-id="f9244-114">無</span><span class="sxs-lookup"><span data-stu-id="f9244-114">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f9244-115">子元素</span><span class="sxs-lookup"><span data-stu-id="f9244-115">Child Elements</span></span>  
  
|<span data-ttu-id="f9244-116">項目</span><span class="sxs-lookup"><span data-stu-id="f9244-116">Element</span></span>|<span data-ttu-id="f9244-117">描述</span><span class="sxs-lookup"><span data-stu-id="f9244-117">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="f9244-118">將憑證加入至受信任簽發者的集合。</span><span class="sxs-lookup"><span data-stu-id="f9244-118">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="f9244-119">使用指定的憑證`thumbprint`屬性。</span><span class="sxs-lookup"><span data-stu-id="f9244-119">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="f9244-120">這個屬性是必要，應該包含憑證指紋的 ASN.1 編碼格式。</span><span class="sxs-lookup"><span data-stu-id="f9244-120">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="f9244-121">`name`屬性是選擇性的而且可用來指定憑證的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="f9244-121">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="f9244-122">清除集合中的受信任簽發者的所有憑證。</span><span class="sxs-lookup"><span data-stu-id="f9244-122">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="f9244-123">從受信任簽發者的集合中移除憑證。</span><span class="sxs-lookup"><span data-stu-id="f9244-123">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="f9244-124">使用指定的憑證`thumbprint`屬性。</span><span class="sxs-lookup"><span data-stu-id="f9244-124">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="f9244-125">這是必要屬性。</span><span class="sxs-lookup"><span data-stu-id="f9244-125">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f9244-126">父項目</span><span class="sxs-lookup"><span data-stu-id="f9244-126">Parent Elements</span></span>  
  
|<span data-ttu-id="f9244-127">項目</span><span class="sxs-lookup"><span data-stu-id="f9244-127">Element</span></span>|<span data-ttu-id="f9244-128">描述</span><span class="sxs-lookup"><span data-stu-id="f9244-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9244-129">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="f9244-129">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="f9244-130">設定簽發者名稱登錄。</span><span class="sxs-lookup"><span data-stu-id="f9244-130">Configures the issuer name registry.</span></span> <span data-ttu-id="f9244-131">**重要事項：** `type`屬性`<issuerNameRegistry>`元素必須參考<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>類別`<trustedIssuers>`為有效的項目。</span><span class="sxs-lookup"><span data-stu-id="f9244-131">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9244-132">備註</span><span class="sxs-lookup"><span data-stu-id="f9244-132">Remarks</span></span>  
 <span data-ttu-id="f9244-133">Windows Identity Foundation (WIF) 提供的單一實作<xref:System.IdentityModel.Tokens.IssuerNameRegistry>類別，根據預設，<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>類別。</span><span class="sxs-lookup"><span data-stu-id="f9244-133">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="f9244-134">設定簽發者名稱登錄會維護從組態載入的受信任簽發者清單。</span><span class="sxs-lookup"><span data-stu-id="f9244-134">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="f9244-135">清單會將每個簽發者名稱關聯才能驗證權杖簽發者所產生的簽章的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="f9244-135">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="f9244-136">受信任簽發者憑證的清單下，會指定`<trustedIssuers>`項目。</span><span class="sxs-lookup"><span data-stu-id="f9244-136">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="f9244-137">在清單中的每個項目將與需要驗證的語彙基元的簽發者所產生的簽章的 X.509 憑證關聯的助憶鍵簽發者名稱。</span><span class="sxs-lookup"><span data-stu-id="f9244-137">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="f9244-138">受信任的憑證會指定使用 ASN.1 編碼的憑證指紋的格式，而且會加入集合，使用`<add>`項目。</span><span class="sxs-lookup"><span data-stu-id="f9244-138">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="f9244-139">您可以清除，或從清單中移除簽發者 （憑證），使用`<clear>`和`<remove>`項目。</span><span class="sxs-lookup"><span data-stu-id="f9244-139">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="f9244-140">`type`屬性`<issuerNameRegistry>`元素必須參考<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>類別`<trustedIssuers>`為有效的項目。</span><span class="sxs-lookup"><span data-stu-id="f9244-140">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9244-141">範例</span><span class="sxs-lookup"><span data-stu-id="f9244-141">Example</span></span>  
 <span data-ttu-id="f9244-142">下列 XML 會示範如何指定基礎設定簽發者名稱登錄。</span><span class="sxs-lookup"><span data-stu-id="f9244-142">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f9244-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="f9244-143">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
