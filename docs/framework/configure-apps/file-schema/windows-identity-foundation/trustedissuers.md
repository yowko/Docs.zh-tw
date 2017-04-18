---
title: "&lt;trustedIssuers&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
caps.latest.revision: 7
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# &lt;trustedIssuers&gt;
設定組態為基礎的發照者的名稱登錄所使用的受信任的發行者憑證的清單 \(<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>\)。  
  
## 語法  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry>  
          <trustedIssuers>  
            <add thumbprint=xs:string name=xs:string>  
            <clear>  
            <remove thumbprint=xs:string>  
          </trustedIssuers>  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
 None  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|`<add thumbprint=xs:string name=xs:string>`|將憑證加入至受信任之發照者的集合。  憑證以指定`thumbprint`屬性。  這個屬性是必要的並且應該包含憑證指紋的 ASN.1 編碼形式。  `name`屬性是選擇性的而且可以用來指定憑證的易記名稱。|  
|`<clear>`|清除集合中的受信任之發照者的所有憑證。|  
|`<remove thumbprint=xs:string>`|移除集合中的受信任之發照者的憑證。  憑證以指定`thumbprint`屬性。  這是必要屬性。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<issuerNameRegistry\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|設定發照者的名稱登錄。 **Important:**  `type`屬性的`<issuerNameRegistry>`項目必須參考<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>類別的`<trustedIssuers>`為有效的項目。|  
  
## 備註  
 Windows 識別基礎 \(WIF\) 提供的單一實作<xref:System.IdentityModel.Tokens.IssuerNameRegistry>類別\] 方塊中，用完<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>類別。  組態發照者的名稱登錄會維護一份受信任之發照者從組態載入。  清單會將每個發照者的名稱與所需來驗證簽章的語彙基元所產生的發照者的 X.509 憑證相關聯。  在指定受信任的發行者憑證的清單，則`<trustedIssuers>`項目。  在清單中的每個項目將助憶鍵的發行者名稱關聯到所需來驗證簽章的語彙基元所產生的該發行者的 X.509 憑證。  受信任的憑證指定使用 ASN.1 編碼的憑證指模的表單，並會藉由加入集合`<add>`項目。  您可以清除，或從清單中移除之發照者 \(憑證\)，藉由使用`<clear>`和`<remove>`項目。  
  
 `type`屬性的`<issuerNameRegistry>`項目必須參考<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>類別的`<trustedIssuers>`為有效的項目。  
  
## 範例  
 下列 XML 程式碼會示範如何指定基礎設定發行者名稱登錄。  
  
```  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
  
```  
  
## 請參閱  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>   
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>