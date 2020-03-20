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
# <a name="samlsecuritytokenrequirement"></a>\<samlSecurityToken 要求>
為這些<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>類之一的<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>類、類或派生類提供配置。 由類<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>表示。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統.身份模型>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<身份配置>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<安全權杖處理常式>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<添加>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityToken 要求>**  
  
## <a name="syntax"></a>語法  
  
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
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|地圖到視窗|指定權杖處理常式是否應通過使用傳入的 UPN 聲明將驗證權杖映射到 Windows 帳戶。 預設值為 "false"。|  
|頒發者證書重新調用模式|指定<xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>要用於 X.509 憑證的吊銷模式的值。 預設值為"連線"。|  
|頒發者驗證模式|指定<xref:System.ServiceModel.Security.X509CertificateValidationMode>要用於 X.509 憑證的驗證模式的值。 預設值為"對等或鏈信任"。|  
|頒發者證書信任存儲位置|指定<xref:System.Security.Cryptography.X509Certificates.StoreLocation>X.509 憑證存儲的值。 預設值為"本地電腦"。|  
|頒發者證書驗證器|派生自<xref:System.IdentityModel.Selectors.X509CertificateValidator>的自訂類型。 如果`issuerCertificateValidationMode`屬性為"自訂"，則此類型的實例用於頒發者證書驗證。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<名稱 claimtype>](nameclaimtype.md)|設置指定<xref:System.Security.Principal.IIdentity.Name%2A>屬性的聲明類型。|  
|[\<角色聲明類型>](roleclaimtype.md)|指定定義權杖處理常式<xref:System.Security.Claims.ClaimsIdentity><xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>方法返回的物件集合中的角色類型聲明的聲明類型。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<添加>](add.md)|將指定的安全權杖處理常式添加到權杖處理常式集合。|  
  
## <a name="remarks"></a>備註  
 元素`<samlSecurityTokenRequirement>`由<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>物件模型中的類表示，用於在`SamlSecurityTokenRequirement`<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>或 上配置屬性。 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
## <a name="example"></a>範例  
  
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
