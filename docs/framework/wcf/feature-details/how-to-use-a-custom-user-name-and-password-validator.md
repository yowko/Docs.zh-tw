---
title: "HOW TO：使用自訂使用者名稱與密碼驗證程式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF, 使用者名稱和密碼"
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# HOW TO：使用自訂使用者名稱與密碼驗證程式
根據預設，使用使用者名稱和密碼進行驗證時，[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 會使用 Windows 驗證使用者名稱和密碼。不過，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 允許自訂的使用者名稱和密碼驗證結構描述，也稱為*驗證程式*。若要納入自訂的使用者名稱和密碼驗證程式，請建立衍生自 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> 的類別，然後予以設定。  
  
 如需範例應用程式，請參閱 [使用者名稱密碼驗證程式](../../../../docs/framework/wcf/samples/user-name-password-validator.md)  
  
### 建立自訂的使用者名稱和密碼驗證程式  
  
1.  建立衍生自 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> 的類別。  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]  
  
2.  覆寫 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> 方法，實作自訂驗證結構描述。  
  
     請勿在實際執行環境使用下列範例中會覆寫 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> 方法的程式碼。將此程式碼以自訂的使用者名稱和密碼驗證結構描述取代，其中可能包含從資料庫擷取使用者名稱和密碼組。  
  
     若要將驗證錯誤傳回至用戶端，請在 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> 方法中擲回 <xref:System.ServiceModel.FaultException>。  
  
     [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
     [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]  
  
### 將服務設定為使用自訂的使用者名稱和密碼驗證程式  
  
1.  設定繫結，此繫結會在 HTTP\(S\) 上的任何傳輸或傳輸層級安全性使用訊息安全性。  
  
     使用訊息安全性時，請新增其中一個系統提供的繫結，例如 [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)，或是支援訊息安全性和 `UserName` 認證類型的 [\<customBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)。  
  
     在 HTTP\(S\) 上使用傳輸層級安全性時，請新增 [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)、[\<basicHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)、[\<netTcpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)，或者使用 HTTP\(S\) 和 `Basic` 驗證配置的 [\<customBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)。  
  
    > [!NOTE]
    >  使用 [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] \(含\) 以後版本時，您可以將自訂使用者名稱和密碼驗證器搭配訊息安全性和傳輸安全性使用。透過 [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)]，自訂使用者名稱和密碼驗證器只能與訊息安全性配合使用。  
  
    > [!TIP]
    >  如需在此內容中使用 \<netTcpBinding\> 的詳細資訊，請參閱 [\<安全性\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)。  
  
    1.  在組態檔的 [\<system.serviceModel\>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) 項目中新增 [\<繫結\>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) 項目。  
  
    2.  將 [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) 或 [\<basicHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) 項目加入至繫結區段。[!INCLUDE[crabout](../../../../includes/crabout-md.md)]建立 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 繫結項目，請參閱 [HOW TO：指定組態中的服務繫結](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)。  
  
    3.  將 [\<安全性\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)或 [\<安全性\>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) 的 `mode` 屬性設定為 `Message`、`Transport`、`or``TransportWithMessageCredential`。  
  
    4.  設定 [\<訊息\>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)或 [\<transport\>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) 的 `clientCredentialType` 屬性。  
  
         使用訊息安全性時，將 [\<訊息\>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)的 `clientCredentialType` 屬性設定為 `UserName`。  
  
         在 HTTP\(S\) 上使用傳輸層級安全性時，將 [\<transport\>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) 或 [\<transport\>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) 的 `clientCredentialType` 屬性設定為 `Basic`。  
  
        > [!NOTE]
        >  當 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務使用傳輸層級安全性裝載在網際網路資訊服務 \(IIS\) 中，並且 <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> 屬性設定為 <xref:System.ServiceModel.Security.UserNamePasswordValidationMode> 時，自訂驗證配置會使用 Windows 驗證的子集。這是因為在這種情況中，IIS 會在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 叫用自訂驗證器之前，先執行 Windows 驗證。  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 建立 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 繫結項目，請參閱 [HOW TO：指定組態中的服務繫結](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)。  
  
     下列程式碼範例顯示繫結的組態程式碼。  
  
    ```  
    <system.serviceModel>   
      <bindings>  
      <wsHttpBinding>  
          <binding name="Binding1">  
            <security mode="Message">  
              <message clientCredentialType="UserName" />  
            </security>  
          </binding>          
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
2.  設定行為，指定自訂使用者名稱和密碼驗證程式用來驗證傳入之 <xref:System.IdentityModel.Tokens.UserNameSecurityToken> 安全性權杖的使用者名稱和密碼組。  
  
    1.  加入 [\<行為\>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) 項目做為 [\<system.serviceModel\>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) 項目的子系。  
  
    2.  將 [\<serviceBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)加入至 [\<行為\>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) 項目。  
  
    3.  加入 [\<行為\>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) 項目，並將 `name` 屬性設定為適當值。  
  
    4.  將 [\<serviceCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)加入至 [\<行為\>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) 項目。  
  
    5.  將 [\<userNameAuthentication\>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md)加入至 [\<serviceCredentials\>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)。  
  
    6.  將 `userNamePasswordValidationMode` 設定為 `Custom`。  
  
        > [!IMPORTANT]
        >  如果沒有設定 `userNamePasswordValidationMode` 值，則 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會使用 Windows 驗證，而不會使用自訂的使用者名稱和密碼驗證程式。  
  
    7.  將 `customUserNamePasswordValidatorType` 設為代表自訂使用者名稱和密碼驗證程式的類型。  
  
     下列範例顯示目前的 `<serviceCredentials>` 片段。  
  
    ```  
    <serviceCredentials>  
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />  
    </serviceCredentials>  
    ```  
  
## 範例  
 以下程式碼範例將示範如何建立自訂的使用者名稱和密碼驗證程式。請勿在實際執行環境使用會覆寫 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> 方法的程式碼。將此程式碼以自訂的使用者名稱和密碼驗證結構描述取代，其中可能包含從資料庫擷取使用者名稱和密碼組。  
  
 [!code-csharp[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
 [!code-vb[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]  
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]  
  
## 請參閱  
 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>   
 [HOW TO：使用 ASP.NET 成員資格提供者](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)   
 [驗證](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)