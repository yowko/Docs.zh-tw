---
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: d892fbd802ed366ca7af9b85fbf5c23d4d27e0f1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157001"
---
# \<securityTokenHandlers>

指定向端點註冊的安全性權杖處理常式集合。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlers>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|NAME|指定權杖處理常式集合的名稱。 架構唯一能辨識的值為 "ActAs" 和 "OnBehalfOf"。 如果使用其中一個名稱指定權杖處理常式集合，則會在分別處理 ActAs 或 OnBehalfOf 權杖時使用集合。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<add>](add.md)|將安全性權杖處理常式新增至權杖處理常式集合。|  
|[\<clear>](clear.md)|從權杖處理常式集合中清除所有安全性權杖處理常式。|  
|[\<remove>](remove.md)|從權杖處理常式集合中移除安全性權杖處理常式。|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|提供權杖處理常式集合的設定。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|指定服務層級的身分識別設定。|  
  
## <a name="remarks"></a>備註  

 您可以在服務設定中指定一或多個已命名的安全性權杖處理常式集合。 您可以使用屬性來指定集合的名稱 `name` 。 架構所處理的唯一名稱為 "ActAs" 和 "OnBehalfOf"。 如果處理常式存在於這些集合中，安全性權杖服務會使用這些處理常式 (STS) ，而不是處理和權杖時的預設處理常式 `ActAs` `OnBehalfOf` 。  
  
 根據預設，集合會填入下列處理常式類型： <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 、 <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler> 、 <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler> 、 <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler> 、 <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> 和 <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler> 。 您可以使用 `<add>` 、和元素來修改集合 `<remove>` `<clear>` 。 您必須確定集合中只存在任何特定類型的單一處理程式。 例如，如果您從類別衍生處理常式 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> ，您的處理常式或 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 可以在單一集合中設定，但不能同時設定兩者。  
  
 您 `<securityTokenHandlerConfiguration>` 可以使用元素來指定集合中處理常式的配置設定。 透過這個專案指定的設定會透過專案覆寫服務上指定的設定 [\<identityConfiguration>](identityconfiguration.md) 。 某些處理常式 (包括數個內建處理常式類型) 可透過專案的子項目支援其他設定 `<add>` 。 處理常式上指定的設定會覆寫集合或服務上指定的對等設定。
