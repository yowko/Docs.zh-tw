---
title: '&lt;certificateValidation&gt;'
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: 29881be43f02d275ad135efd97dc8b25a7409beb
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48838327"
---
# <a name="ltcertificatevalidationgt"></a>&lt;certificateValidation&gt;
控制權杖處理常式用來驗證憑證的設定。 如果特定的處理常式設定為使用自己的驗證程式，則會覆寫這些設定。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<certificateValidation >  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation  
      certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
      revocationMode="NoCheck||Offline||Online"  
      trustedStoreLocation="CurrentLocation||LocalMachine" >  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|certificateValidationMode|<xref:System.ServiceModel.Security.X509CertificateValidationMode>值，指定要使用的 X.509 憑證驗證模式。 預設值為"PeerOrChainTrust"。 若要指定自訂驗證程式，此屬性設定為"Custom"，並指定使用的驗證[ \<certificateValidator >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)項目。 選擇性。|  
|revocationMode|<xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>值，指定要使用的 X.509 憑證的撤銷模式。 預設值為 「 上線 」。 選擇性。|  
|trustedStoreLocation|A<xref:System.Security.Cryptography.X509Certificates.StoreLocation>值，指定 X.509 憑證存放區。 預設值為"LocalMachine"。 選擇性。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<certificateValidator >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)|指定自訂憑證驗證類型。 只有，會使用這個型別`certificateValidationMode`的屬性[ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)元素設定為"Custom"。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|指定服務層級身分識別設定。|  
|[\<Securitytokenhandlerconfiguration> >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|提供組態集合的安全性權杖處理常式。|  
  
## <a name="remarks"></a>備註  
 A`<certificateValidation>`項目可以指定服務層級底下`<identityConfiguration>`項目或之下的安全性權杖處理常式集合層級`<securityTokenHandlerConfiguration>`項目。 權杖處理常式集合上的設定會覆寫所指定的服務。 某些權杖處理常式可讓您在組態中指定的憑證驗證設定。 服務層級和安全性權杖處理常式集合上設定個別的語彙基元處理常式覆寫所指定。  
  
## <a name="example"></a>範例  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
