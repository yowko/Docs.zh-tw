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
提供 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 類別、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 類別或其中任一個類別的衍生類別的設定。 以類別表示 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> 。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenRequirement>**  
  
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
|mapToWindows|指定權杖處理常式是否應使用傳入的 UPN 宣告，將驗證權杖對應至 Windows 帳戶。 預設值為 "false"。|  
|issuerCertificateRevocationMode|<xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>值，指定要用於 x.509 憑證的撤銷模式。 預設值為 "Online"。|  
|issuerCertificateValidationMode|<xref:System.ServiceModel.Security.X509CertificateValidationMode>值，指定要用於 x.509 憑證的驗證模式。 預設值為 "PeerOrChainTrust"。|  
|issuerCertificateTrustedStoreLocation|<xref:System.Security.Cryptography.X509Certificates.StoreLocation>值，指定 x.509 憑證存放區。 預設值為 "LocalMachine"。|  
|issuerCertificateValidator|衍生自的自訂類型 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 。 如果 `issuerCertificateValidationMode` 屬性為 "Custom"，則會使用此類型的實例進行簽發者憑證驗證。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<nameClaimType>](nameclaimtype.md)|設定指定屬性的宣告類型 <xref:System.Security.Principal.IIdentity.Name%2A> 。|  
|[\<roleClaimType>](roleclaimtype.md)|指定宣告類型，在 <xref:System.Security.Claims.ClaimsIdentity> 權杖處理常式的方法所傳回的物件集合中，定義角色類型宣告 <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> 。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<add>](add.md)|將指定的安全性權杖處理常式加入至權杖處理常式集合。|  
  
## <a name="remarks"></a>備註  
 `<samlSecurityTokenRequirement>`元素是由 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> 物件模型中的類別表示，並用於設定 `SamlSecurityTokenRequirement` 或上的屬性 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 。  
  
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
