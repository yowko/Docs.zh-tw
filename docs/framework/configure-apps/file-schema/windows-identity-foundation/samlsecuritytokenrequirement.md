---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: b27f337189a7d0b66ffd38e032b5eb864e5094a1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152628"
---
# \<samlSecurityTokenRequirement>
<span data-ttu-id="3d969-101">提供 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 類別、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 類別或其中任一個類別的衍生類別的設定。</span><span class="sxs-lookup"><span data-stu-id="3d969-101">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="3d969-102">以類別表示 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> 。</span><span class="sxs-lookup"><span data-stu-id="3d969-102">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="3d969-103">語法</span><span class="sxs-lookup"><span data-stu-id="3d969-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d969-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3d969-104">Attributes and Elements</span></span>  
 <span data-ttu-id="3d969-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="3d969-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d969-106">屬性</span><span class="sxs-lookup"><span data-stu-id="3d969-106">Attributes</span></span>  
  
|<span data-ttu-id="3d969-107">屬性</span><span class="sxs-lookup"><span data-stu-id="3d969-107">Attribute</span></span>|<span data-ttu-id="3d969-108">描述</span><span class="sxs-lookup"><span data-stu-id="3d969-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3d969-109">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="3d969-109">mapToWindows</span></span>|<span data-ttu-id="3d969-110">指定權杖處理常式是否應使用傳入的 UPN 宣告，將驗證權杖對應至 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="3d969-110">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="3d969-111">預設值為 "false"。</span><span class="sxs-lookup"><span data-stu-id="3d969-111">The default is "false".</span></span>|  
|<span data-ttu-id="3d969-112">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="3d969-112">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="3d969-113"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>值，指定要用於 x.509 憑證的撤銷模式。</span><span class="sxs-lookup"><span data-stu-id="3d969-113">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="3d969-114">預設值為 "Online"。</span><span class="sxs-lookup"><span data-stu-id="3d969-114">The default value is "Online".</span></span>|  
|<span data-ttu-id="3d969-115">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="3d969-115">issuerCertificateValidationMode</span></span>|<span data-ttu-id="3d969-116"><xref:System.ServiceModel.Security.X509CertificateValidationMode>值，指定要用於 x.509 憑證的驗證模式。</span><span class="sxs-lookup"><span data-stu-id="3d969-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="3d969-117">預設值為 "PeerOrChainTrust"。</span><span class="sxs-lookup"><span data-stu-id="3d969-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="3d969-118">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="3d969-118">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="3d969-119"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>值，指定 x.509 憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="3d969-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="3d969-120">預設值為 "LocalMachine"。</span><span class="sxs-lookup"><span data-stu-id="3d969-120">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="3d969-121">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="3d969-121">issuerCertificateValidator</span></span>|<span data-ttu-id="3d969-122">衍生自的自訂類型 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 。</span><span class="sxs-lookup"><span data-stu-id="3d969-122">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="3d969-123">如果 `issuerCertificateValidationMode` 屬性為 "Custom"，則會使用此類型的實例進行簽發者憑證驗證。</span><span class="sxs-lookup"><span data-stu-id="3d969-123">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3d969-124">子元素</span><span class="sxs-lookup"><span data-stu-id="3d969-124">Child Elements</span></span>  
  
|<span data-ttu-id="3d969-125">元素</span><span class="sxs-lookup"><span data-stu-id="3d969-125">Element</span></span>|<span data-ttu-id="3d969-126">描述</span><span class="sxs-lookup"><span data-stu-id="3d969-126">Description</span></span>|  
|-------------|-----------------|  
|[\<nameClaimType>](nameclaimtype.md)|<span data-ttu-id="3d969-127">設定指定屬性的宣告類型 <xref:System.Security.Principal.IIdentity.Name%2A> 。</span><span class="sxs-lookup"><span data-stu-id="3d969-127">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[\<roleClaimType>](roleclaimtype.md)|<span data-ttu-id="3d969-128">指定宣告類型，在 <xref:System.Security.Claims.ClaimsIdentity> 權杖處理常式的方法所傳回的物件集合中，定義角色類型宣告 <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> 。</span><span class="sxs-lookup"><span data-stu-id="3d969-128">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3d969-129">父項目</span><span class="sxs-lookup"><span data-stu-id="3d969-129">Parent Elements</span></span>  
  
|<span data-ttu-id="3d969-130">元素</span><span class="sxs-lookup"><span data-stu-id="3d969-130">Element</span></span>|<span data-ttu-id="3d969-131">描述</span><span class="sxs-lookup"><span data-stu-id="3d969-131">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="3d969-132">將指定的安全性權杖處理常式加入至權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="3d969-132">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d969-133">備註</span><span class="sxs-lookup"><span data-stu-id="3d969-133">Remarks</span></span>  
 <span data-ttu-id="3d969-134">`<samlSecurityTokenRequirement>`元素是由 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> 物件模型中的類別表示，並用於設定 `SamlSecurityTokenRequirement` 或上的屬性 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 。</span><span class="sxs-lookup"><span data-stu-id="3d969-134">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d969-135">範例</span><span class="sxs-lookup"><span data-stu-id="3d969-135">Example</span></span>  
  
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
