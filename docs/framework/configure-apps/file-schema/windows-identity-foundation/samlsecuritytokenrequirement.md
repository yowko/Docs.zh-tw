---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: cab7572518a7a6dc26f8bbcf67cd424fa1c01085
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251894"
---
# <a name="samlsecuritytokenrequirement"></a><span data-ttu-id="025ea-101">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="025ea-101">\<samlSecurityTokenRequirement></span></span>
<span data-ttu-id="025ea-102"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>提供類別<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 、類別或其中任一個類別的衍生類別的設定。</span><span class="sxs-lookup"><span data-stu-id="025ea-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="025ea-103"><xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>以類別表示。</span><span class="sxs-lookup"><span data-stu-id="025ea-103">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
<span data-ttu-id="025ea-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="025ea-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="025ea-105">&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="025ea-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="025ea-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="025ea-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="025ea-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="025ea-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="025ea-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<新增 >** ](add.md)</span><span class="sxs-lookup"><span data-stu-id="025ea-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="025ea-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<samlSecurityTokenRequirement >**</span><span class="sxs-lookup"><span data-stu-id="025ea-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="025ea-110">語法</span><span class="sxs-lookup"><span data-stu-id="025ea-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="025ea-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="025ea-111">Attributes and Elements</span></span>  
 <span data-ttu-id="025ea-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="025ea-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="025ea-113">屬性</span><span class="sxs-lookup"><span data-stu-id="025ea-113">Attributes</span></span>  
  
|<span data-ttu-id="025ea-114">屬性</span><span class="sxs-lookup"><span data-stu-id="025ea-114">Attribute</span></span>|<span data-ttu-id="025ea-115">說明</span><span class="sxs-lookup"><span data-stu-id="025ea-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="025ea-116">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="025ea-116">mapToWindows</span></span>|<span data-ttu-id="025ea-117">指定權杖處理常式是否應使用傳入的 UPN 宣告，將驗證權杖對應至 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="025ea-117">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="025ea-118">預設值為 "false"。</span><span class="sxs-lookup"><span data-stu-id="025ea-118">The default is "false".</span></span>|  
|<span data-ttu-id="025ea-119">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="025ea-119">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="025ea-120"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>值，指定要用於 x.509 憑證的撤銷模式。</span><span class="sxs-lookup"><span data-stu-id="025ea-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="025ea-121">預設值為 "Online"。</span><span class="sxs-lookup"><span data-stu-id="025ea-121">The default value is "Online".</span></span>|  
|<span data-ttu-id="025ea-122">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="025ea-122">issuerCertificateValidationMode</span></span>|<span data-ttu-id="025ea-123"><xref:System.ServiceModel.Security.X509CertificateValidationMode>值，指定要用於 x.509 憑證的驗證模式。</span><span class="sxs-lookup"><span data-stu-id="025ea-123">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="025ea-124">預設值為 "PeerOrChainTrust"。</span><span class="sxs-lookup"><span data-stu-id="025ea-124">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="025ea-125">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="025ea-125">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="025ea-126"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>值，指定 x.509 憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="025ea-126">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="025ea-127">預設值為 "LocalMachine"。</span><span class="sxs-lookup"><span data-stu-id="025ea-127">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="025ea-128">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="025ea-128">issuerCertificateValidator</span></span>|<span data-ttu-id="025ea-129">衍生自的自訂類型<xref:System.IdentityModel.Selectors.X509CertificateValidator>。</span><span class="sxs-lookup"><span data-stu-id="025ea-129">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="025ea-130">`issuerCertificateValidationMode`如果屬性為 "Custom"，則會使用此類型的實例進行簽發者憑證驗證。</span><span class="sxs-lookup"><span data-stu-id="025ea-130">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="025ea-131">子元素</span><span class="sxs-lookup"><span data-stu-id="025ea-131">Child Elements</span></span>  
  
|<span data-ttu-id="025ea-132">項目</span><span class="sxs-lookup"><span data-stu-id="025ea-132">Element</span></span>|<span data-ttu-id="025ea-133">描述</span><span class="sxs-lookup"><span data-stu-id="025ea-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="025ea-134">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="025ea-134">\<nameClaimType></span></span>](nameclaimtype.md)|<span data-ttu-id="025ea-135">設定指定<xref:System.Security.Principal.IIdentity.Name%2A>屬性的宣告類型。</span><span class="sxs-lookup"><span data-stu-id="025ea-135">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="025ea-136">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="025ea-136">\<roleClaimType></span></span>](roleclaimtype.md)|<span data-ttu-id="025ea-137">指定宣告類型，在權杖處理常式的<xref:System.Security.Claims.ClaimsIdentity> <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>方法所傳回的物件集合中，定義角色類型宣告。</span><span class="sxs-lookup"><span data-stu-id="025ea-137">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="025ea-138">父項目</span><span class="sxs-lookup"><span data-stu-id="025ea-138">Parent Elements</span></span>  
  
|<span data-ttu-id="025ea-139">項目</span><span class="sxs-lookup"><span data-stu-id="025ea-139">Element</span></span>|<span data-ttu-id="025ea-140">描述</span><span class="sxs-lookup"><span data-stu-id="025ea-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="025ea-141">\<add></span><span class="sxs-lookup"><span data-stu-id="025ea-141">\<add></span></span>](add.md)|<span data-ttu-id="025ea-142">將指定的安全性權杖處理常式加入至權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="025ea-142">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="025ea-143">備註</span><span class="sxs-lookup"><span data-stu-id="025ea-143">Remarks</span></span>  
 <span data-ttu-id="025ea-144">`SamlSecurityTokenRequirement` <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>元素是由物件模型中的類別表示，並用於設定或上的屬性。 `<samlSecurityTokenRequirement>`</span><span class="sxs-lookup"><span data-stu-id="025ea-144">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="025ea-145">範例</span><span class="sxs-lookup"><span data-stu-id="025ea-145">Example</span></span>  
  
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
