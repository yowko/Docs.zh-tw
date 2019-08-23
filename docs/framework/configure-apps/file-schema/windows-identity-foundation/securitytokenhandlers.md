---
title: <securityTokenHandlers>
ms.date: 03/30/2017
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
author: BrucePerlerMS
ms.openlocfilehash: 678e5c705181c55257b1ddb853690ada60ecd17a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942464"
---
# <a name="securitytokenhandlers"></a>\<securityTokenHandlers>
指定已向端點註冊的安全性權杖處理常式集合。  
  
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
  
|屬性|說明|  
|---------------|-----------------|  
|NAME|指定權杖處理常式集合的名稱。 架構所能辨識的唯一值為 "ActAs" 和 "OnBehalfOf"。 如果使用上述其中一個名稱來指定權杖處理常式集合, 則會在分別處理 ActAs 或 OnBehalfOf 權杖時使用集合。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<add>](add.md)|將安全性權杖處理常式加入至權杖處理常式集合。|  
|[\<clear>](clear.md)|清除權杖處理常式集合中的所有安全性權杖處理常式。|  
|[\<remove>](remove.md)|從權杖處理常式集合中移除安全性權杖處理常式。|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|提供權杖處理常式集合的設定。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|指定服務層級的身分識別設定。|  
  
## <a name="remarks"></a>備註  
 您可以在服務設定中指定一或多個已命名的安全性權杖處理常式集合。 您可以使用`name`屬性來指定集合的名稱。 架構所處理的唯一名稱是 "ActAs" 和 "OnBehalfOf"。 如果處理常式存在於這些集合中, 則會由 Security Token Service (STS) 使用, 而不是處理`ActAs`和`OnBehalfOf`標記時的預設處理常式。  
  
 根據預設, 集合會填入下列處理<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>程式類型:、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>、 <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler> <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>、和<xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>。 您可以使用`<add>`、 `<remove>`和`<clear>`元素來修改集合。 您必須確定集合中只存在任何特定類型的單一處理程式。 例如, 如果您從<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>類別衍生處理常式, 則您的<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>處理常式或可以在單一集合中設定, 但不能同時在兩者中設定。  
  
 `<securityTokenHandlerConfiguration>`使用元素來指定集合中處理常式的設定。 透過這個專案指定的設定, 會透過[ \<identityConfiguration >](identityconfiguration.md)專案來覆寫在服務上指定的設定。 某些處理常式 (包括數個內建處理常式類型) 可以透過專案的子`<add>`專案支援其他設定。 在處理常式上指定的設定會覆寫集合或服務上指定的對等設定。
