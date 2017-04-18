---
title: "&lt;issuerNameRegistry&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
caps.latest.revision: 13
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 12
---
# &lt;issuerNameRegistry&gt;
設定發行者名稱登錄所使用的語彙基元的處理常式集合中的處理常式。  
  
## 語法  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry type=xs:string>  
          <optionalCustomConfigurationElements />  
        </issuerNameRegistry>  
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
|type|型別衍生自<xref:System.IdentityModel.Tokens.IssuerNameRegistry>類別。  如需有關如何指定自訂的`type`，請參閱[Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_CustomTypeReferences)。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<trustedIssuers\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)|當`type`屬性會指定組態為基礎的發照者的名稱登錄 \( <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>類別\)、 [\<trustedIssuers\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)必須指定項目。  [\<trustedIssuers\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/trustedissuers.md)項目可以採取`<add>`， `<clear>`，或`<remove>`與項目子系元素。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|提供組態集合的安全性語彙基元的處理常式。|  
  
## 備註  
 所有的發照者語彙基元會經過驗證，使用簽發者名稱登錄。  這是一個物件，是衍生自<xref:System.IdentityModel.Tokens.IssuerNameRegistry>類別。  發照者的名稱登錄用來將助憶鍵的名稱以驗證簽章的語彙基元所產生的相對應的發照者所需的密碼編譯資料產生關聯。  發照者的名稱登錄會維護一份由信賴憑證者的合作對象 \(RP\) 應用程式所信任的發行者。  使用指定的發行者名稱登錄型別`type`屬性。  `<issuerNameRegistry>`項目可擁有一或多個提供組態指定的型別子項目。  您提供的邏輯來處理這些子項目，藉由覆寫<xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A>方法。  
  
 WIF 提供單一的發照者名稱\] 方塊中，用完的登錄型別<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>類別。  這個類別會使用一組在組態中指定的受信任的發行者憑證。  它需要的子系組態項目中， `<trustedIssuers>`，在已設定的受信任的發行者的憑證集合。  受信任的憑證會指定使用 ASN.1 編碼形式的憑證指模以及新增或移除集合中藉由使用`<add>`， `<clear>`，或`<remove>`項目。  
  
 `<issuerNameRegistry>`項目會以<xref:System.IdentityModel.Configuration.IssuerNameRegistryElement>類別。  
  
> [!NOTE]
>  指定`<issuerNameRegistry>`項目做為子項目， [\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)項目已被取代，但仍然支援回溯相容性。  設定在`<securityTokenHandlerConfiguration>`項目會覆寫那些在`<identityConfiguration>`項目。  
  
## 範例  
 下列 XML 程式碼會示範如何指定基礎設定發行者名稱登錄。  
  
```  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
  
```  
  
## 請參閱  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>   
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>