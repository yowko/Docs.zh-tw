---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: f93ec0007b537e306a570b166eaa4cd2fe7f81e2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157027"
---
# \<samlSecurityTokenRequirement>

<span data-ttu-id="65a0a-101">提供 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 類別、類別或其中一個類別的 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 衍生類別的設定。</span><span class="sxs-lookup"><span data-stu-id="65a0a-101">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="65a0a-102">由類別表示 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> 。</span><span class="sxs-lookup"><span data-stu-id="65a0a-102">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="65a0a-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="65a0a-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65a0a-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="65a0a-104">Attributes and Elements</span></span>  

 <span data-ttu-id="65a0a-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="65a0a-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65a0a-106">屬性</span><span class="sxs-lookup"><span data-stu-id="65a0a-106">Attributes</span></span>  
  
|<span data-ttu-id="65a0a-107">屬性</span><span class="sxs-lookup"><span data-stu-id="65a0a-107">Attribute</span></span>|<span data-ttu-id="65a0a-108">描述</span><span class="sxs-lookup"><span data-stu-id="65a0a-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="65a0a-109">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="65a0a-109">mapToWindows</span></span>|<span data-ttu-id="65a0a-110">指定權杖處理常式是否應該使用連入的 UPN 宣告，將驗證權杖對應至 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="65a0a-110">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="65a0a-111">預設值為 "false"。</span><span class="sxs-lookup"><span data-stu-id="65a0a-111">The default is "false".</span></span>|  
|<span data-ttu-id="65a0a-112">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="65a0a-112">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="65a0a-113"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>值，指定要用於 x.509 憑證的撤銷模式。</span><span class="sxs-lookup"><span data-stu-id="65a0a-113">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="65a0a-114">預設值為 "Online"。</span><span class="sxs-lookup"><span data-stu-id="65a0a-114">The default value is "Online".</span></span>|  
|<span data-ttu-id="65a0a-115">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="65a0a-115">issuerCertificateValidationMode</span></span>|<span data-ttu-id="65a0a-116"><xref:System.ServiceModel.Security.X509CertificateValidationMode>值，指定要用於 x.509 憑證的驗證模式。</span><span class="sxs-lookup"><span data-stu-id="65a0a-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="65a0a-117">預設值為 "PeerOrChainTrust"。</span><span class="sxs-lookup"><span data-stu-id="65a0a-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="65a0a-118">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="65a0a-118">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="65a0a-119"><xref:System.Security.Cryptography.X509Certificates.StoreLocation>指定 x.509 憑證存放區的值。</span><span class="sxs-lookup"><span data-stu-id="65a0a-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="65a0a-120">預設值為 "LocalMachine"。</span><span class="sxs-lookup"><span data-stu-id="65a0a-120">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="65a0a-121">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="65a0a-121">issuerCertificateValidator</span></span>|<span data-ttu-id="65a0a-122">衍生自的自訂型別 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 。</span><span class="sxs-lookup"><span data-stu-id="65a0a-122">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="65a0a-123">如果 `issuerCertificateValidationMode` 屬性為「自訂」，則會使用此類型的實例進行簽發者憑證驗證。</span><span class="sxs-lookup"><span data-stu-id="65a0a-123">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="65a0a-124">子元素</span><span class="sxs-lookup"><span data-stu-id="65a0a-124">Child Elements</span></span>  
  
|<span data-ttu-id="65a0a-125">項目</span><span class="sxs-lookup"><span data-stu-id="65a0a-125">Element</span></span>|<span data-ttu-id="65a0a-126">描述</span><span class="sxs-lookup"><span data-stu-id="65a0a-126">Description</span></span>|  
|-------------|-----------------|  
|[\<nameClaimType>](nameclaimtype.md)|<span data-ttu-id="65a0a-127">設定指定屬性的宣告類型 <xref:System.Security.Principal.IIdentity.Name%2A> 。</span><span class="sxs-lookup"><span data-stu-id="65a0a-127">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[\<roleClaimType>](roleclaimtype.md)|<span data-ttu-id="65a0a-128">指定宣告類型，定義 <xref:System.Security.Claims.ClaimsIdentity> <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> 權杖處理常式方法所傳回的物件集合中的角色類型宣告。</span><span class="sxs-lookup"><span data-stu-id="65a0a-128">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="65a0a-129">父項目</span><span class="sxs-lookup"><span data-stu-id="65a0a-129">Parent Elements</span></span>  
  
|<span data-ttu-id="65a0a-130">項目</span><span class="sxs-lookup"><span data-stu-id="65a0a-130">Element</span></span>|<span data-ttu-id="65a0a-131">描述</span><span class="sxs-lookup"><span data-stu-id="65a0a-131">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="65a0a-132">將指定的安全性權杖處理常式新增至權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="65a0a-132">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65a0a-133">備註</span><span class="sxs-lookup"><span data-stu-id="65a0a-133">Remarks</span></span>  

 <span data-ttu-id="65a0a-134">專案 `<samlSecurityTokenRequirement>` 是以 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> 物件模型中的類別表示，並且用來設定 `SamlSecurityTokenRequirement` 或上的屬性 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 。</span><span class="sxs-lookup"><span data-stu-id="65a0a-134">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65a0a-135">範例</span><span class="sxs-lookup"><span data-stu-id="65a0a-135">Example</span></span>  
  
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
