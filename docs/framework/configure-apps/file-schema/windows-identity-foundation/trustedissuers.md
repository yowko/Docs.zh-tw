---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 32aad3529ded6d0234b1bcb388ecbbc3b0a11c87
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944264"
---
# <a name="trustedissuers"></a><span data-ttu-id="a29c8-101">\<trustedIssuers></span><span class="sxs-lookup"><span data-stu-id="a29c8-101">\<trustedIssuers></span></span>
<span data-ttu-id="a29c8-102">設定以設定為基礎的簽發者名稱登錄 (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>) 所使用的受信任簽發者憑證清單。</span><span class="sxs-lookup"><span data-stu-id="a29c8-102">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
 <span data-ttu-id="a29c8-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="a29c8-103">\<system.identityModel></span></span>  
<span data-ttu-id="a29c8-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="a29c8-104">\<identityConfiguration></span></span>  
<span data-ttu-id="a29c8-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="a29c8-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="a29c8-106">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="a29c8-106">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="a29c8-107">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="a29c8-107">\<issuerNameRegistry></span></span>  
<span data-ttu-id="a29c8-108">\<trustedIssuers></span><span class="sxs-lookup"><span data-stu-id="a29c8-108">\<trustedIssuers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a29c8-109">語法</span><span class="sxs-lookup"><span data-stu-id="a29c8-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a29c8-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a29c8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a29c8-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="a29c8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a29c8-112">屬性</span><span class="sxs-lookup"><span data-stu-id="a29c8-112">Attributes</span></span>  
 <span data-ttu-id="a29c8-113">None</span><span class="sxs-lookup"><span data-stu-id="a29c8-113">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a29c8-114">子元素</span><span class="sxs-lookup"><span data-stu-id="a29c8-114">Child Elements</span></span>  
  
|<span data-ttu-id="a29c8-115">項目</span><span class="sxs-lookup"><span data-stu-id="a29c8-115">Element</span></span>|<span data-ttu-id="a29c8-116">描述</span><span class="sxs-lookup"><span data-stu-id="a29c8-116">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="a29c8-117">將憑證新增至受信任簽發者的集合。</span><span class="sxs-lookup"><span data-stu-id="a29c8-117">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="a29c8-118">憑證是以`thumbprint`屬性指定。</span><span class="sxs-lookup"><span data-stu-id="a29c8-118">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="a29c8-119">此為必要屬性, 且應包含憑證指紋的 asn.1 編碼形式。</span><span class="sxs-lookup"><span data-stu-id="a29c8-119">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="a29c8-120">屬性`name`是選擇性的, 可以用來指定憑證的易記名稱。</span><span class="sxs-lookup"><span data-stu-id="a29c8-120">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="a29c8-121">清除受信任簽發者集合中的所有憑證。</span><span class="sxs-lookup"><span data-stu-id="a29c8-121">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="a29c8-122">從受信任簽發者的集合中移除憑證。</span><span class="sxs-lookup"><span data-stu-id="a29c8-122">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="a29c8-123">憑證是以`thumbprint`屬性指定。</span><span class="sxs-lookup"><span data-stu-id="a29c8-123">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="a29c8-124">這是必要屬性。</span><span class="sxs-lookup"><span data-stu-id="a29c8-124">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a29c8-125">父項目</span><span class="sxs-lookup"><span data-stu-id="a29c8-125">Parent Elements</span></span>  
  
|<span data-ttu-id="a29c8-126">項目</span><span class="sxs-lookup"><span data-stu-id="a29c8-126">Element</span></span>|<span data-ttu-id="a29c8-127">描述</span><span class="sxs-lookup"><span data-stu-id="a29c8-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a29c8-128">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="a29c8-128">\<issuerNameRegistry></span></span>](issuernameregistry.md)|<span data-ttu-id="a29c8-129">設定簽發者名稱登錄。</span><span class="sxs-lookup"><span data-stu-id="a29c8-129">Configures the issuer name registry.</span></span> <span data-ttu-id="a29c8-130">**重要：** `<issuerNameRegistry>` <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>元素的`type`屬性必須`<trustedIssuers>`參考類別, 專案才會是有效的。</span><span class="sxs-lookup"><span data-stu-id="a29c8-130">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a29c8-131">備註</span><span class="sxs-lookup"><span data-stu-id="a29c8-131">Remarks</span></span>  
 <span data-ttu-id="a29c8-132">Windows Identity Foundation (WIF) 提供<xref:System.IdentityModel.Tokens.IssuerNameRegistry>類別<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>的單一實作為類別。</span><span class="sxs-lookup"><span data-stu-id="a29c8-132">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="a29c8-133">設定簽發者名稱登錄會維護從設定載入之受信任簽發者的清單。</span><span class="sxs-lookup"><span data-stu-id="a29c8-133">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="a29c8-134">此清單會將每個簽發者名稱與 x.509 憑證建立關聯, 以驗證簽發者所產生之權杖的簽章。</span><span class="sxs-lookup"><span data-stu-id="a29c8-134">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="a29c8-135">受信任簽發者憑證的清單是在`<trustedIssuers>`元素下指定。</span><span class="sxs-lookup"><span data-stu-id="a29c8-135">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="a29c8-136">清單中的每個元素會將助憶鍵簽發者名稱與 x.509 憑證產生關聯, 以驗證該簽發者所產生之權杖的簽章。</span><span class="sxs-lookup"><span data-stu-id="a29c8-136">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="a29c8-137">受信任的憑證是使用憑證指紋的 asn.1 編碼形式來指定, 並使用`<add>`元素來新增集合。</span><span class="sxs-lookup"><span data-stu-id="a29c8-137">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="a29c8-138">您可以使用`<clear>`和`<remove>`元素, 從清單中清除或移除簽發者 (憑證)。</span><span class="sxs-lookup"><span data-stu-id="a29c8-138">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="a29c8-139">`<issuerNameRegistry>` <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>元素的`type`屬性必須`<trustedIssuers>`參考類別, 專案才會是有效的。</span><span class="sxs-lookup"><span data-stu-id="a29c8-139">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a29c8-140">範例</span><span class="sxs-lookup"><span data-stu-id="a29c8-140">Example</span></span>  
 <span data-ttu-id="a29c8-141">下列 XML 顯示如何指定以設定為基礎的簽發者名稱登錄。</span><span class="sxs-lookup"><span data-stu-id="a29c8-141">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a29c8-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a29c8-142">See also</span></span>

- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
