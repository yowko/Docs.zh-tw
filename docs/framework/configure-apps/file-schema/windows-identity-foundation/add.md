---
title: "&lt;add&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
caps.latest.revision: 7
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# &lt;add&gt;
將指定的安全性語彙基元的處理常式加入語彙基元的處理常式集合。  
  
## 語法  
  
```  
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
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|type|要加入語彙基元的處理常式的 CLR 型別名稱。  如需有關如何指定`type`屬性，請參閱[Custom Type References](http://msdn.microsoft.com/zh-tw/7286d2e3-c63d-49fd-abdc-ce2705f22c24)。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<samlSecurityTokenRequirement\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|提供設定<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>類別， <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>類別或衍生的類別的任一種類別。|  
|[\<sessionTokenRequirement\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessiontokenrequirement.md)|提供設定<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>類別或衍生的類別。|  
|[\<userNameSecurityTokenHandlerRequirement\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/usernamesecuritytokenhandlerrequirement.md)|提供設定<xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>類別或衍生的類別。|  
|[\<x509SecurityTokenHandlerRequirement\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/x509securitytokenhandlerrequirement.md)|提供選擇性的設定，如<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>類別或衍生的類別。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<securityTokenHandlers\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|指定登錄與端點的安全性語彙基元處理常式的集合。|  
  
## 備註  
 `<add>`項目可以取得指定語彙基元的處理常式組態的單一子項目。  這是取決於處理常式類別是否參考到`type`屬性的`<add>`項目會提供這項功能的支援。  語彙基元的處理常式類別，可以提供這項功能必須公開 \(expose\) 使用的建構函式<xref:System.Xml.XmlElement>物件。  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 有幾個內建的安全性語彙基元的處理常式的類別有提供這項功能。  These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.  
  
> [!IMPORTANT]
>  語彙基元的處理常式集合只能包含單一的處理任何的常式指定的型別。  這表示，例如，如果您想要加入的處理常式，衍生自<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>類別加入集合中，您必須先移除<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>，也就是預設為存在，集合中。  您可以使用[\<remove\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md)若要移除之集合或使用單一的處理常式的項目[\<clear\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md)要從集合移除所有的處理常式的項目。  
  
 在處理常式中指定的設定會覆寫下的語彙基元的處理常式集合上所指定的對等設定[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)項目，並指定在服務層級下的[\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目。  
  
## 範例  
 下列 XML 程式碼示範如何使用`<add>`和`<remove>`來取代預設的工作階段權杖處理常式和自訂工作階段的語彙基元處理常式的項目。  XML 來自`ClaimsAwareWebFarm`範例。  
  
```  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```