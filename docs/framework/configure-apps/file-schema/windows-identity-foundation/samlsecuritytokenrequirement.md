---
title: '&lt;samlSecurityTokenRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: c9856dae971691baf9dabe845bdecae90cbc8aa5
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2018
ms.locfileid: "48847293"
---
# <a name="ltsamlsecuritytokenrequirementgt"></a><span data-ttu-id="85325-102">&lt;samlSecurityTokenRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="85325-102">&lt;samlSecurityTokenRequirement&gt;</span></span>
<span data-ttu-id="85325-103">提供組態<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>類別，<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>類別或其中一個這些類別的衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="85325-103">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="85325-104">由<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>類別。</span><span class="sxs-lookup"><span data-stu-id="85325-104">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
 <span data-ttu-id="85325-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="85325-105">\<system.identityModel></span></span>  
<span data-ttu-id="85325-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="85325-106">\<identityConfiguration></span></span>  
<span data-ttu-id="85325-107">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="85325-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="85325-108">\<add></span><span class="sxs-lookup"><span data-stu-id="85325-108">\<add></span></span>  
<span data-ttu-id="85325-109">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="85325-109">\<samlSecurityTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85325-110">語法</span><span class="sxs-lookup"><span data-stu-id="85325-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement   
            issuerCertificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
            issuerCertificateRevocationMode="NoCheck||Offline||Online"  
            issuerCertificateTrustedStoreLocation="CurrentLocation||LocalMachine"  
            issuerCertificateValidator="Namespace.Class Assembly"  
            mapToWindows=xs:boolean  
          <nameClaimType value=xs:string />  
          <roleClaimType value=xs:string />  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85325-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="85325-111">Attributes and Elements</span></span>  
 <span data-ttu-id="85325-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="85325-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85325-113">屬性</span><span class="sxs-lookup"><span data-stu-id="85325-113">Attributes</span></span>  
  
|<span data-ttu-id="85325-114">屬性</span><span class="sxs-lookup"><span data-stu-id="85325-114">Attribute</span></span>|<span data-ttu-id="85325-115">描述</span><span class="sxs-lookup"><span data-stu-id="85325-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="85325-116">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="85325-116">mapToWindows</span></span>|<span data-ttu-id="85325-117">指定的權杖處理常式是否應該使用內送的 「 UPN 」 宣告，將驗證權杖對應至 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="85325-117">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="85325-118">預設值為"false"。</span><span class="sxs-lookup"><span data-stu-id="85325-118">The default is "false".</span></span>|  
|<span data-ttu-id="85325-119">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="85325-119">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="85325-120"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>值，指定要使用的 X.509 憑證的撤銷模式。</span><span class="sxs-lookup"><span data-stu-id="85325-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="85325-121">預設值為 「 上線 」。</span><span class="sxs-lookup"><span data-stu-id="85325-121">The default value is "Online".</span></span>|  
|<span data-ttu-id="85325-122">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="85325-122">issuerCertificateValidationMode</span></span>|<span data-ttu-id="85325-123"><xref:System.ServiceModel.Security.X509CertificateValidationMode>值，指定要使用的 X.509 憑證驗證模式。</span><span class="sxs-lookup"><span data-stu-id="85325-123">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="85325-124">預設值為"PeerOrChainTrust"。</span><span class="sxs-lookup"><span data-stu-id="85325-124">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="85325-125">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="85325-125">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="85325-126">A<xref:System.Security.Cryptography.X509Certificates.StoreLocation>值，指定 X.509 憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="85325-126">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="85325-127">預設值為"LocalMachine"。</span><span class="sxs-lookup"><span data-stu-id="85325-127">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="85325-128">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="85325-128">issuerCertificateValidator</span></span>|<span data-ttu-id="85325-129">自訂型別衍生自<xref:System.IdentityModel.Selectors.X509CertificateValidator>。</span><span class="sxs-lookup"><span data-stu-id="85325-129">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="85325-130">如果`issuerCertificateValidationMode`屬性是 「 自訂 」，此類型的執行個體使用的簽發者憑證驗證。</span><span class="sxs-lookup"><span data-stu-id="85325-130">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="85325-131">子元素</span><span class="sxs-lookup"><span data-stu-id="85325-131">Child Elements</span></span>  
  
|<span data-ttu-id="85325-132">項目</span><span class="sxs-lookup"><span data-stu-id="85325-132">Element</span></span>|<span data-ttu-id="85325-133">描述</span><span class="sxs-lookup"><span data-stu-id="85325-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85325-134">\<nameClaimType ></span><span class="sxs-lookup"><span data-stu-id="85325-134">\<nameClaimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/nameclaimtype.md)|<span data-ttu-id="85325-135">設定指定的宣告型<xref:System.Security.Principal.IIdentity.Name%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="85325-135">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="85325-136">\<roleClaimType ></span><span class="sxs-lookup"><span data-stu-id="85325-136">\<roleClaimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/roleclaimtype.md)|<span data-ttu-id="85325-137">指定的集合中定義的角色類型宣告的宣告類型<xref:System.Security.Claims.ClaimsIdentity>所傳回的物件<xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>的權杖處理常式的方法。</span><span class="sxs-lookup"><span data-stu-id="85325-137">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="85325-138">父項目</span><span class="sxs-lookup"><span data-stu-id="85325-138">Parent Elements</span></span>  
  
|<span data-ttu-id="85325-139">項目</span><span class="sxs-lookup"><span data-stu-id="85325-139">Element</span></span>|<span data-ttu-id="85325-140">描述</span><span class="sxs-lookup"><span data-stu-id="85325-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85325-141">\<add></span><span class="sxs-lookup"><span data-stu-id="85325-141">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="85325-142">將指定的安全性權杖處理常式加入至 權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="85325-142">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85325-143">備註</span><span class="sxs-lookup"><span data-stu-id="85325-143">Remarks</span></span>  
 <span data-ttu-id="85325-144">`<samlSecurityTokenRequirement>`項目由<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>類別的物件模型中，並可用來設定`SamlSecurityTokenRequirement`上的屬性<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>或<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>。</span><span class="sxs-lookup"><span data-stu-id="85325-144">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85325-145">範例</span><span class="sxs-lookup"><span data-stu-id="85325-145">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement issuerCertificateValidationMode="PeerOrChainTrust"  
                                  issuerCertificateRevocationMode="Online"  
                                  issuerCertificateTrustedStoreLocation="LocalMachine"  
                                  mapToWindows="false">  
  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```
