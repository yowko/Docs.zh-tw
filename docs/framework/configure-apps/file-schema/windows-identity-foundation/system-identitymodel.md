---
title: "&lt;system.identityModel&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 210ce7e9-d07b-400c-800f-5f525dcf95e8
caps.latest.revision: 5
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 5
---
# &lt;system.identityModel&gt;
提供組態對於啟用應用程式中的 Windows 識別基礎 \(WIF\) 選項。  
  
 \<system.identityModel\>  
  
## 語法  
  
```  
<system.identityModel>  
</system.identityModel>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
 None  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|指定服務層級識別設定。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|`<configuration>`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
  
## 備註  
 新增`<system.identityModel>`一節，若要設定的服務或應用程式使用 Windows 識別基礎 \(WIF\) 的組態檔。  `<system.identityModel>`項目會以<xref:System.IdentityModel.Configuration.SystemIdentityModelSection>類別。  
  
## 範例  
 下列範例顯示如何將`<system.identityModel>`一節，以組態檔。  您必須先將組態區段和命名空間宣告，在`<configSections>`項目。  然後您可以將`<system.IdentityModel>`到您的組態檔，以指定一或多個身分識別設定的項目。  
  
```  
<configuration>  
  <configSections>  
    <!--WIF 4.5 sections -->  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089"/>  
  </configSections>  
  
  ...  
  
  <system.identityModel>  
    <identityConfiguration>  
      <audienceUris>  
        <add value="http://localhost/WebApplication1/" />  
      </audienceUris>  
      <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089">  
        <trustedIssuers>  
          <add thumbprint="313D3B … 9106A9EC" name="SelfSTS" />  
        </trustedIssuers>  
      </issuerNameRegistry>  
      <certificateValidation certificateValidationMode="None"/>  
    </identityConfiguration>  
  </system.identityModel>  
  
  ...  
  
</configuration>  
```  
  
## 請參閱  
 <xref:System.IdentityModel.Configuration.SystemIdentityModelSection>