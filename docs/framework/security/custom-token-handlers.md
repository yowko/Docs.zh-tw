---
title: "自訂權杖處理常式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5062669f-8bfc-420a-a25d-d8ab992ab10e
caps.latest.revision: 4
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 4
---
# 自訂權杖處理常式
本主題將討論 WIF 語彙基元的處理常式，以及如何使用它們在處理語彙基元。  這個主題也包含功能需要建立預設在 WIF 不支援的語彙基元型別的自訂語彙基元的處理常式。  
  
## 語彙基元的處理常式簡介 WIF 的  
 WIF 需要安全性權杖建立處理常式，讀取，寫入，並驗證相依的一方 \(RP\) 應用程式或安全性權杖服務 \(STS\) 的語彙基元。  語彙基元管理員為您的擴充點可以加入 WIF 管線的自訂語彙基元的處理常式，或自訂現有的語彙基元的處理常式處理語彙基元的方法。  WIF 提供可修改或完全覆寫視需要變更功能的九個內建安全性語彙基元的處理常式。  
  
## 內建 WIF 的安全性語彙基元的處理常式。  
 WIF 4.5 包含從抽象基底類別 <xref:System.IdentityModel.Tokens.SecurityTokenHandler>衍生的九個安全性權杖管理員類別:  
  
-   <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.UserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>  
  
## 將自訂語彙基元的處理常式。  
 某些語彙基元型別，例如簡單 Web 語彙基元 \(SWT\) 和 JSON Web 語彙基元 \(JWT\) 不 WIF 所提供的內建語彙基元的處理常式。  如需這些語彙基元型別並不提供內建的處理常式的其他的，您必須執行下列步驟來建立自訂語彙基元的處理常式。  
  
#### 將自訂語彙基元的處理常式。  
  
1.  若要從 <xref:System.IdentityModel.Tokens.SecurityTokenHandler>衍生自的新類別。  
  
2.  會覆寫下列方法並提供自己的實作:  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3.  加入新的自訂語彙基元處理常式的參考在 *Web.config 或* App.configfile *，* 一個適用於 WIF 的 **\<system.identityModel\>** 區段中。  例如，下列設定標記中指定 **CustomToken** 位於命名空間中的新語彙基元的處理常式 **MyCustomTokenHandler** 。  
  
    ```  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```  
  
     請注意，如果您提供自己語彙基元的處理常式已經將固定語彙基元管理員來建立語彙基元型別，您需要加入 **\<remove\>** 項目置放在預設處理常式並使用您的自訂處理常式。  例如，下列設定是這個自訂語彙基元管理員取代預設 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> :  
  
    ```  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <remove type=”System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcdefg123456789”>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```