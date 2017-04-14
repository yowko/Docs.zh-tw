---
title: "&lt;audienceUris&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7a3d8515-d756-4afe-a22d-07cbe2217ee3
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# &lt;audienceUris&gt;
指定是信賴憑證者 \(RP\) 可接受的識別項的 Uri 集合。  將不會接受語彙基元，除非它們範圍的其中一個允許的對象的 Uri。  
  
## 語法  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <audienceUris mode=xs:string>  
          <add value=xs:string />  
          <clear />  
          <remove value=xs:string />  
        </audienceUris>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|mode|<xref:System.IdentityModel.Selectors.AudienceUriMode>值，指定是否要對象限制套用到連入的語彙基元。  可能的值是"始終"、"Never"和"BearerKeyOnly"。  預設值是"始終"。  選擇項。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|`<add value=xs:string>`|將所指定的 URI `value`屬性設定為 audienceUris 集合。  `value` 屬性 \(Attribute\) 是必要項。  URI 是區分大小寫的。|  
|`<clear>`|清除 audienceUris 集合。  從集合移除所有的識別項。|  
|`<remove value=xs:string>`|移除所指定的 URI `value` audienceUris 集合中的屬性。  `value` 屬性 \(Attribute\) 是必要項。  URI 是區分大小寫的。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|提供組態集合的安全性語彙基元的處理常式。|  
  
## 備註  
 根據預設，這個集合是空的。 使用`<add>`， `<clear>`，以及`<remove>`來修改集合的項目。  <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>與<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>物件來設定的對象的 URI 集合中的值允許對象的 URI 有限制的使用<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>物件。  
  
 `<audienceUris>`項目會以<xref:System.IdentityModel.Configuration.AudienceUriElementCollection>類別。  加入至集合的個別 URI 由<xref:System.IdentityModel.Configuration.AudienceUriElement>類別。  
  
> [!NOTE]
>  使用`<audienceUris>`項目做為子項目， [\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目已被取代，但仍然支援回溯相容性。  設定在`<securityTokenHandlerConfiguration>`項目會覆寫那些在`<identityConfiguration>`項目。  
  
## 範例  
 下列 XML 程式碼會示範如何設定應用程式的可接受對象的 Uri。  本範例將單一的 URI。  範圍設定為此 URI 的語彙基元將會被接受，會拒絕其他所有服務。  
  
```  
<audienceUris>  
  <add value="http://localhost:19851/"/>  
</audienceUris>  
```