---
title: '&lt;securityTokenHandlers&gt;'
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: e63f02add81495e474b59b6c5cc090bd69add3d2
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47206165"
---
# <a name="ltsecuritytokenhandlersgt"></a>&lt;securityTokenHandlers&gt;
指定登錄與端點的安全性權杖處理常式的集合。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|名稱|指定的權杖處理常式集合的名稱。 架構所辨識的唯一值是"ActAs"和"OnBehalfOf"。 如果使用這些名稱指定權杖處理常式集合，分別處理 ActAs 或 OnBehalfOf 權杖時，將會使用集合。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|將權杖處理常式集合中的安全性權杖處理常式。|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)|清除所有的安全性權杖處理常式，從權杖處理常式集合。|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)|從權杖處理常式集合中移除的安全性權杖處理常式。|  
|[\<Securitytokenhandlerconfiguration> >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|提供的權杖處理常式集合的組態。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|指定服務層級身分識別設定。|  
  
## <a name="remarks"></a>備註  
 您可以在服務組態中指定一個或多個安全性權杖處理常式的具名的集合。 您可以指定集合的名稱使用`name`屬性。 架構會處理的唯一名稱是"ActAs"和"OnBehalfOf"。 如果處理常式存在於這些集合，這些安全性權杖服務 (STS) 而不預設處理常式處理時使用`ActAs`和`OnBehalfOf`語彙基元。  
  
 根據預設，集合會填入下列處理常式類型： <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>， <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>， <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>， <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>， <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>， <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>，和<xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>。 您可以使用，以修改集合`<add>`， `<remove>`，和`<clear>`項目。 您必須確定任何特定的型別中的單一處理常式存在於集合。 比方說，如果您衍生從處理常式<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>類別，可能是您的處理常式或<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>可能在單一集合，但不是能同時設定。  
  
 使用`<securityTokenHandlerConfiguration>`項目來指定集合中的處理常式的組態設定。 透過這個項目指定的設定會覆寫透過在服務上指定[ \<Identityconfiguration> >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目。 有些 （包括數個內建的處理常式型別） 的處理常式可以支援額外的設定，透過的子項目`<add>`項目。 指定處理常式上設定覆寫集合或服務上所指定的對等設定。
