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
# <a name="samlsecuritytokenrequirement"></a>\<samlSecurityTokenRequirement>
<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>提供類別<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 、類別或其中任一個類別的衍生類別的設定。 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>以類別表示。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<新增 >** ](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<samlSecurityTokenRequirement >**  
  
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
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|mapToWindows|指定權杖處理常式是否應使用傳入的 UPN 宣告，將驗證權杖對應至 Windows 帳戶。 預設值為 "false"。|  
|issuerCertificateRevocationMode|<xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>值，指定要用於 x.509 憑證的撤銷模式。 預設值為 "Online"。|  
|issuerCertificateValidationMode|<xref:System.ServiceModel.Security.X509CertificateValidationMode>值，指定要用於 x.509 憑證的驗證模式。 預設值為 "PeerOrChainTrust"。|  
|issuerCertificateTrustedStoreLocation|<xref:System.Security.Cryptography.X509Certificates.StoreLocation>值，指定 x.509 憑證存放區。 預設值為 "LocalMachine"。|  
|issuerCertificateValidator|衍生自的自訂類型<xref:System.IdentityModel.Selectors.X509CertificateValidator>。 `issuerCertificateValidationMode`如果屬性為 "Custom"，則會使用此類型的實例進行簽發者憑證驗證。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<nameClaimType>](nameclaimtype.md)|設定指定<xref:System.Security.Principal.IIdentity.Name%2A>屬性的宣告類型。|  
|[\<roleClaimType>](roleclaimtype.md)|指定宣告類型，在權杖處理常式的<xref:System.Security.Claims.ClaimsIdentity> <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>方法所傳回的物件集合中，定義角色類型宣告。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<add>](add.md)|將指定的安全性權杖處理常式加入至權杖處理常式集合。|  
  
## <a name="remarks"></a>備註  
 `SamlSecurityTokenRequirement` <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>元素是由物件模型中的類別表示，並用於設定或上的屬性。 `<samlSecurityTokenRequirement>`  
  
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
