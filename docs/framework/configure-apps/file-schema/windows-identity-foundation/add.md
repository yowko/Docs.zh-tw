---
title: '&lt;add&gt;'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
caps.latest.revision: 7
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: d863a0fc2b575aceef12370a57f7f7807261cb5a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="ltaddgt"></a>&lt;add&gt;
將指定的安全性權杖處理常式加入至權杖處理常式集合。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<add>  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type=xs:string>  
        <optionalConfigurationElement>  
        </optionalConfigurationElement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|類型|要加入的語彙基元處理常式的 CLR 型別名稱。 如需有關如何指定`type`屬性，請參閱[自訂型別參考](http://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24)。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|提供組態<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>類別<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>類別或衍生的類別中的這些類別的其中一個。|  
|[\<sessionTokenRequirement>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessiontokenrequirement.md)|提供組態<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>類別或衍生的類別。|  
|[\<userNameSecurityTokenHandlerRequirement>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/usernamesecuritytokenhandlerrequirement.md)|提供組態<xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>類別或衍生的類別。|  
|[\<x509SecurityTokenHandlerRequirement>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/x509securitytokenhandlerrequirement.md)|提供選擇性組態<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>類別或衍生的類別。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|指定註冊的端點的安全性權杖處理常式的集合。|  
  
## <a name="remarks"></a>備註  
 `<add>`項目可指定的語彙基元處理常式組態的單一子項目。 這是相依於處理常式類別是否透過參考`type`屬性`<add>`元素提供這項功能的支援。 權杖處理常式類別，提供此功能必須公開 （expose) 的建構函式<xref:System.Xml.XmlElement>物件。  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 數個內建安全性權杖處理常式類別並提供這項功能。 這些類別是<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>， <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>， <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>， <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>，和<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>。  
  
> [!IMPORTANT]
>  權杖處理常式集合只能包含單一的處理常式，任何給定的類型。 這表示，例如，如果您想要加入的處理常式，衍生自<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>類別加入集合中，您必須先移除<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>，它並根據預設，從集合存在。 您可以使用[\<移除 >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)項目移除的集合或使用單一處理常式[\<清除 >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)項目移除集合中的所有處理常式。  
  
 指定處理常式上設定覆寫下，權杖處理常式集合上指定的對等設定[ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)項目，並指定在服務層級下的[ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目。  
  
## <a name="example"></a>範例  
 下列 XML 程式碼將示範如何使用`<add>`和`<remove>`自訂工作階段權杖處理常式以取代預設工作階段權杖處理常式項目。 XML 取自`ClaimsAwareWebFarm`範例。  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
