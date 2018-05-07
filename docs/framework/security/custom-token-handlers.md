---
title: 自訂權杖處理常式
ms.date: 03/30/2017
ms.assetid: 5062669f-8bfc-420a-a25d-d8ab992ab10e
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 18be4babf7e9cfbfe9ebfb43da6f98a8544b2fe6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="custom-token-handlers"></a>自訂權杖處理常式
本主題討論 WIF 中的權杖處理常式以及如何使用它們來處理權杖。 本主題也涵蓋建立權杖類型的自訂權杖處理常式所需的作業，而 WIF 中預設不支援這些權杖類型。  
  
## <a name="introduction-to-token-handlers-in-wif"></a>WIF 中的權杖處理常式簡介  
 WIF 依賴安全性權杖處理常式來建立、讀取、寫入和驗證信賴憑證者 (RP) 應用程式或安全性權杖服務 (STS) 的權杖。 權杖處理常式是擴充點，可讓您在 WIF 管線中新增自訂權杖處理常式，或自訂現有權杖處理常式管理權杖的方式。 WIF 提供九個內建安全性權杖處理常式，可視需要進行修改或完全覆寫以變更功能。  
  
## <a name="built-in-security-token-handlers-in-wif"></a>WIF 中的內建安全性權杖處理常式  
 WIF 4.5 包含衍生自抽象基底類別 <xref:System.IdentityModel.Tokens.SecurityTokenHandler> 的九個安全性權杖處理常式類別：  
  
-   <xref:System.IdentityModel.Tokens.EncryptedSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.KerberosSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.RsaSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.UserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.WindowsUserNameSecurityTokenHandler>  
  
-   <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>  
  
## <a name="adding-a-custom-token-handler"></a>新增自訂權杖處理常式  
 部分權杖類型 (例如簡單 Web 權杖 (SWT) 和 JSON Web 權杖 (JWT)) 沒有 WIF 所提供的內建權杖處理常式。 針對這些權杖類型以及沒有內建處理常式的權杖類型，您需要執行下列步驟來建立自訂權杖處理常式。  
  
#### <a name="adding-a-custom-token-handler"></a>新增自訂權杖處理常式  
  
1.  建立衍生自 <xref:System.IdentityModel.Tokens.SecurityTokenHandler> 的新類別。  
  
2.  覆寫下列方法，並提供您自己的實作：  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ReadToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanWriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.WriteToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.CanValidateToken%2A>  
  
    -   <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>  
  
3.  在 *Web.config* 或 *App.config* 檔案中套用 WIF 的 **\<system.identityModel>** 區段內，新增新自訂權杖處理常式的參考。 例如，下列組態標記會指定名為 **MyCustomTokenHandler** 且位在 **CustomToken** 命名空間中的新權杖處理常式。  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```  
  
     請注意，如果您要提供自己的權杖處理常式來處理已有內建權杖處理常式的權杖類型，則需要新增 **\<remove>** 項目來捨棄預設處理常式，並改為使用自訂處理常式。 例如，下列組態會將預設 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 取代為自訂權杖處理常式：  
  
    ```xml  
    <system.identityModel>  
        <identityConfiguration saveBootstrapContext="true">  
            <securityTokenHandlers>  
                <remove type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcdefg123456789">  
                <add type="CustomToken.MyCustomTokenHandler, CustomToken" />  
            </securityTokenHandlers>  
        </identityConfiguration>  
    </system.identityModel>  
    ```
