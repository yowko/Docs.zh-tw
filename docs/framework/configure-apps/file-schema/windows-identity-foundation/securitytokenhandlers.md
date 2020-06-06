---
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: 017309436660991c69da569e9cc4219e842ecaa3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251868"
---
# \<securityTokenHandlers>
指定已向端點註冊的安全性權杖處理常式集合。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlers>**  
  
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
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|NAME|指定權杖處理常式集合的名稱。 架構所能辨識的唯一值為 "ActAs" 和 "OnBehalfOf"。 如果使用上述其中一個名稱來指定權杖處理常式集合，則會在分別處理 ActAs 或 OnBehalfOf 權杖時使用集合。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<add>](add.md)|將安全性權杖處理常式加入至權杖處理常式集合。|  
|[\<clear>](clear.md)|清除權杖處理常式集合中的所有安全性權杖處理常式。|  
|[\<remove>](remove.md)|從權杖處理常式集合中移除安全性權杖處理常式。|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|提供權杖處理常式集合的設定。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|指定服務層級的身分識別設定。|  
  
## <a name="remarks"></a>備註  
 您可以在服務設定中指定一或多個已命名的安全性權杖處理常式集合。 您可以使用屬性來指定集合的名稱 `name` 。 架構所處理的唯一名稱是 "ActAs" 和 "OnBehalfOf"。 如果處理常式存在於這些集合中，則會由 Security Token Service （STS）使用，而不是處理和標記時的預設處理常式 `ActAs` `OnBehalfOf` 。  
  
 根據預設，集合會填入下列處理常式類型： <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 、 <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler> 、、、 <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler> <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler> <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> 和 <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler> 。 您可以使用 `<add>` 、和元素來修改集合 `<remove>` `<clear>` 。 您必須確定集合中只存在任何特定類型的單一處理程式。 例如，如果您從類別衍生處理常式 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> ，則您的處理常式或 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 可以在單一集合中設定，但不能同時在兩者中設定。  
  
 使用 `<securityTokenHandlerConfiguration>` 元素來指定集合中處理常式的設定。 透過這個專案指定的設定，會透過專案覆寫在服務上指定的設定 [\<identityConfiguration>](identityconfiguration.md) 。 某些處理常式（包括數個內建處理常式類型）可以透過專案的子專案支援其他設定 `<add>` 。 在處理常式上指定的設定會覆寫集合或服務上指定的對等設定。
