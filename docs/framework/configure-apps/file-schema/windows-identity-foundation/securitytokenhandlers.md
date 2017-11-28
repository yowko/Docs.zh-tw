---
title: '&lt;securityTokenHandlers&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f11a631d-4094-4e11-bb03-4ede74b30281
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 3151ec3511bca598e5aaabc72b821bdd3aed0b7b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltsecuritytokenhandlersgt"></a>&lt;securityTokenHandlers&gt;
指定註冊的端點的安全性權杖處理常式的集合。  
  
 \<system.identityModel >  
\<identityConfiguration >  
\<securityTokenHandlers >  
  
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
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|name|指定權杖處理常式集合的名稱。 架構所辨識的值為"ActAs"和"OnBehalfOf"。 如果這些名稱的其中一種指定語彙基元處理常式的集合，集合會分別處理 ActAs 或 OnBehalfOf 權杖時使用。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|將安全性權杖處理常式加入至權杖處理常式集合。|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)|清除所有的安全性權杖處理常式，從權杖處理常式集合。|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)|從權杖處理常式集合中移除安全性權杖處理常式。|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|提供的語彙基元處理常式集合的組態。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|指定服務層級身分識別設定。|  
  
## <a name="remarks"></a>備註  
 您可以在服務組態中指定一個或多個安全性權杖處理常式的具名的集合。 您可以指定集合的名稱使用`name`屬性。 唯一的 framework 如何處理名稱為"ActAs"和"OnBehalfOf"。 如果處理常式存在這些集合中，則會使用安全性權杖服務 (STS) 而不是預設處理常式處理時`ActAs`和`OnBehalfOf`語彙基元。  
  
 根據預設，集合會填入下列處理常式類型： <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>， <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>， <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>， <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>， <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>， <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>，和<xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>。 您可修改該集合使用`<add>`， `<remove>`，和`<clear>`項目。 您必須確定集合中有任何特定類型的單一處理常式。 比方說，如果衍生的處理常式從<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>類別，可能是您的處理常式或<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>可能設定在單一的集合，但非兩者。  
  
 使用`<securityTokenHandlerConfiguration>`項目集合中指定的處理常式的組態設定。 透過這個項目指定的設定會覆寫透過服務上指定[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目。 （包括數個內建的處理常式型別） 的一些處理常式可以支援額外的設定，透過的子項目`<add>`項目。 指定處理常式上設定覆寫指定集合或服務上的對等設定。
