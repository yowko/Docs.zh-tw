---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: e1b8acd48ee185b3c6c50f70321bb9ca66e8e02b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793857"
---
# <a name="samlsecuritytokenrequirement"></a><span data-ttu-id="759ed-101">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="759ed-101">\<samlSecurityTokenRequirement></span></span>
<span data-ttu-id="759ed-102">提供組態<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>類別，<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>類別或其中一個這些類別的衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="759ed-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="759ed-103">由<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>類別。</span><span class="sxs-lookup"><span data-stu-id="759ed-103">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
 <span data-ttu-id="759ed-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="759ed-104">\<system.identityModel></span></span>  
<span data-ttu-id="759ed-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="759ed-105">\<identityConfiguration></span></span>  
<span data-ttu-id="759ed-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="759ed-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="759ed-107">\<add></span><span class="sxs-lookup"><span data-stu-id="759ed-107">\<add></span></span>  
<span data-ttu-id="759ed-108">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="759ed-108">\<samlSecurityTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="759ed-109">語法</span><span class="sxs-lookup"><span data-stu-id="759ed-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="759ed-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="759ed-110">Attributes and Elements</span></span>  
 <span data-ttu-id="759ed-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="759ed-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="759ed-112">屬性</span><span class="sxs-lookup"><span data-stu-id="759ed-112">Attributes</span></span>  
  
|<span data-ttu-id="759ed-113">屬性</span><span class="sxs-lookup"><span data-stu-id="759ed-113">Attribute</span></span>|<span data-ttu-id="759ed-114">描述</span><span class="sxs-lookup"><span data-stu-id="759ed-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="759ed-115">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="759ed-115">mapToWindows</span></span>|<span data-ttu-id="759ed-116">指定的權杖處理常式是否應該使用內送的 「 UPN 」 宣告，將驗證權杖對應至 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="759ed-116">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="759ed-117">預設值為"false"。</span><span class="sxs-lookup"><span data-stu-id="759ed-117">The default is "false".</span></span>|  
|<span data-ttu-id="759ed-118">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="759ed-118">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="759ed-119"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>值，指定要使用的 X.509 憑證的撤銷模式。</span><span class="sxs-lookup"><span data-stu-id="759ed-119">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="759ed-120">預設值為 「 上線 」。</span><span class="sxs-lookup"><span data-stu-id="759ed-120">The default value is "Online".</span></span>|  
|<span data-ttu-id="759ed-121">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="759ed-121">issuerCertificateValidationMode</span></span>|<span data-ttu-id="759ed-122"><xref:System.ServiceModel.Security.X509CertificateValidationMode>值，指定要使用的 X.509 憑證驗證模式。</span><span class="sxs-lookup"><span data-stu-id="759ed-122">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="759ed-123">預設值為"PeerOrChainTrust"。</span><span class="sxs-lookup"><span data-stu-id="759ed-123">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="759ed-124">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="759ed-124">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="759ed-125">A<xref:System.Security.Cryptography.X509Certificates.StoreLocation>值，指定 X.509 憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="759ed-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="759ed-126">預設值為"LocalMachine"。</span><span class="sxs-lookup"><span data-stu-id="759ed-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="759ed-127">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="759ed-127">issuerCertificateValidator</span></span>|<span data-ttu-id="759ed-128">自訂型別衍生自<xref:System.IdentityModel.Selectors.X509CertificateValidator>。</span><span class="sxs-lookup"><span data-stu-id="759ed-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="759ed-129">如果`issuerCertificateValidationMode`屬性是 「 自訂 」，此類型的執行個體使用的簽發者憑證驗證。</span><span class="sxs-lookup"><span data-stu-id="759ed-129">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="759ed-130">子元素</span><span class="sxs-lookup"><span data-stu-id="759ed-130">Child Elements</span></span>  
  
|<span data-ttu-id="759ed-131">項目</span><span class="sxs-lookup"><span data-stu-id="759ed-131">Element</span></span>|<span data-ttu-id="759ed-132">描述</span><span class="sxs-lookup"><span data-stu-id="759ed-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="759ed-133">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="759ed-133">\<nameClaimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/nameclaimtype.md)|<span data-ttu-id="759ed-134">設定指定的宣告型<xref:System.Security.Principal.IIdentity.Name%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="759ed-134">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="759ed-135">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="759ed-135">\<roleClaimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/roleclaimtype.md)|<span data-ttu-id="759ed-136">指定的集合中定義的角色類型宣告的宣告類型<xref:System.Security.Claims.ClaimsIdentity>所傳回的物件<xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>的權杖處理常式的方法。</span><span class="sxs-lookup"><span data-stu-id="759ed-136">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="759ed-137">父項目</span><span class="sxs-lookup"><span data-stu-id="759ed-137">Parent Elements</span></span>  
  
|<span data-ttu-id="759ed-138">項目</span><span class="sxs-lookup"><span data-stu-id="759ed-138">Element</span></span>|<span data-ttu-id="759ed-139">描述</span><span class="sxs-lookup"><span data-stu-id="759ed-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="759ed-140">\<add></span><span class="sxs-lookup"><span data-stu-id="759ed-140">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="759ed-141">將指定的安全性權杖處理常式加入至 權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="759ed-141">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="759ed-142">備註</span><span class="sxs-lookup"><span data-stu-id="759ed-142">Remarks</span></span>  
 <span data-ttu-id="759ed-143">`<samlSecurityTokenRequirement>`項目由<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>類別的物件模型中，並可用來設定`SamlSecurityTokenRequirement`上的屬性<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>或<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>。</span><span class="sxs-lookup"><span data-stu-id="759ed-143">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="759ed-144">範例</span><span class="sxs-lookup"><span data-stu-id="759ed-144">Example</span></span>  
  
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
