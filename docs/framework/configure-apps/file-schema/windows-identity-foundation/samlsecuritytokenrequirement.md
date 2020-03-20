---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: b27f337189a7d0b66ffd38e032b5eb864e5094a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152628"
---
# <a name="samlsecuritytokenrequirement"></a><span data-ttu-id="160c1-101">\<samlSecurityToken 要求></span><span class="sxs-lookup"><span data-stu-id="160c1-101">\<samlSecurityTokenRequirement></span></span>
<span data-ttu-id="160c1-102">為這些<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>類之一的<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>類、類或派生類提供配置。</span><span class="sxs-lookup"><span data-stu-id="160c1-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="160c1-103">由類<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>表示。</span><span class="sxs-lookup"><span data-stu-id="160c1-103">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
<span data-ttu-id="160c1-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="160c1-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="160c1-105">&nbsp;&nbsp;[**\<系統.身份模型>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="160c1-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="160c1-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<身份配置>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="160c1-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="160c1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<安全權杖處理常式>**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="160c1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="160c1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<添加>**](add.md)</span><span class="sxs-lookup"><span data-stu-id="160c1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="160c1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityToken 要求>**</span><span class="sxs-lookup"><span data-stu-id="160c1-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="160c1-110">語法</span><span class="sxs-lookup"><span data-stu-id="160c1-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="160c1-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="160c1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="160c1-112">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="160c1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="160c1-113">屬性</span><span class="sxs-lookup"><span data-stu-id="160c1-113">Attributes</span></span>  
  
|<span data-ttu-id="160c1-114">屬性</span><span class="sxs-lookup"><span data-stu-id="160c1-114">Attribute</span></span>|<span data-ttu-id="160c1-115">描述</span><span class="sxs-lookup"><span data-stu-id="160c1-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="160c1-116">地圖到視窗</span><span class="sxs-lookup"><span data-stu-id="160c1-116">mapToWindows</span></span>|<span data-ttu-id="160c1-117">指定權杖處理常式是否應通過使用傳入的 UPN 聲明將驗證權杖映射到 Windows 帳戶。</span><span class="sxs-lookup"><span data-stu-id="160c1-117">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="160c1-118">預設值為 "false"。</span><span class="sxs-lookup"><span data-stu-id="160c1-118">The default is "false".</span></span>|  
|<span data-ttu-id="160c1-119">頒發者證書重新調用模式</span><span class="sxs-lookup"><span data-stu-id="160c1-119">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="160c1-120">指定<xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>要用於 X.509 憑證的吊銷模式的值。</span><span class="sxs-lookup"><span data-stu-id="160c1-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="160c1-121">預設值為"連線"。</span><span class="sxs-lookup"><span data-stu-id="160c1-121">The default value is "Online".</span></span>|  
|<span data-ttu-id="160c1-122">頒發者驗證模式</span><span class="sxs-lookup"><span data-stu-id="160c1-122">issuerCertificateValidationMode</span></span>|<span data-ttu-id="160c1-123">指定<xref:System.ServiceModel.Security.X509CertificateValidationMode>要用於 X.509 憑證的驗證模式的值。</span><span class="sxs-lookup"><span data-stu-id="160c1-123">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="160c1-124">預設值為"對等或鏈信任"。</span><span class="sxs-lookup"><span data-stu-id="160c1-124">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="160c1-125">頒發者證書信任存儲位置</span><span class="sxs-lookup"><span data-stu-id="160c1-125">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="160c1-126">指定<xref:System.Security.Cryptography.X509Certificates.StoreLocation>X.509 憑證存儲的值。</span><span class="sxs-lookup"><span data-stu-id="160c1-126">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="160c1-127">預設值為"本地電腦"。</span><span class="sxs-lookup"><span data-stu-id="160c1-127">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="160c1-128">頒發者證書驗證器</span><span class="sxs-lookup"><span data-stu-id="160c1-128">issuerCertificateValidator</span></span>|<span data-ttu-id="160c1-129">派生自<xref:System.IdentityModel.Selectors.X509CertificateValidator>的自訂類型。</span><span class="sxs-lookup"><span data-stu-id="160c1-129">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="160c1-130">如果`issuerCertificateValidationMode`屬性為"自訂"，則此類型的實例用於頒發者證書驗證。</span><span class="sxs-lookup"><span data-stu-id="160c1-130">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="160c1-131">子元素</span><span class="sxs-lookup"><span data-stu-id="160c1-131">Child Elements</span></span>  
  
|<span data-ttu-id="160c1-132">元素</span><span class="sxs-lookup"><span data-stu-id="160c1-132">Element</span></span>|<span data-ttu-id="160c1-133">描述</span><span class="sxs-lookup"><span data-stu-id="160c1-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="160c1-134">\<名稱 claimtype></span><span class="sxs-lookup"><span data-stu-id="160c1-134">\<nameClaimType></span></span>](nameclaimtype.md)|<span data-ttu-id="160c1-135">設置指定<xref:System.Security.Principal.IIdentity.Name%2A>屬性的聲明類型。</span><span class="sxs-lookup"><span data-stu-id="160c1-135">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="160c1-136">\<角色聲明類型></span><span class="sxs-lookup"><span data-stu-id="160c1-136">\<roleClaimType></span></span>](roleclaimtype.md)|<span data-ttu-id="160c1-137">指定定義權杖處理常式<xref:System.Security.Claims.ClaimsIdentity><xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>方法返回的物件集合中的角色類型聲明的聲明類型。</span><span class="sxs-lookup"><span data-stu-id="160c1-137">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="160c1-138">父項目</span><span class="sxs-lookup"><span data-stu-id="160c1-138">Parent Elements</span></span>  
  
|<span data-ttu-id="160c1-139">元素</span><span class="sxs-lookup"><span data-stu-id="160c1-139">Element</span></span>|<span data-ttu-id="160c1-140">描述</span><span class="sxs-lookup"><span data-stu-id="160c1-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="160c1-141">\<添加></span><span class="sxs-lookup"><span data-stu-id="160c1-141">\<add></span></span>](add.md)|<span data-ttu-id="160c1-142">將指定的安全權杖處理常式添加到權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="160c1-142">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="160c1-143">備註</span><span class="sxs-lookup"><span data-stu-id="160c1-143">Remarks</span></span>  
 <span data-ttu-id="160c1-144">元素`<samlSecurityTokenRequirement>`由<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>物件模型中的類表示，用於在`SamlSecurityTokenRequirement`<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>或 上配置屬性。 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler></span><span class="sxs-lookup"><span data-stu-id="160c1-144">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="160c1-145">範例</span><span class="sxs-lookup"><span data-stu-id="160c1-145">Example</span></span>  
  
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
