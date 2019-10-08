---
title: HOW TO：使用自訂使用者名稱與密碼驗證程式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 98ffad7e717aac949509fa701c77d8ba2b80a695
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834699"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a>HOW TO：使用自訂使用者名稱與密碼驗證程式

根據預設，當使用使用者名稱和密碼進行驗證時，Windows Communication Foundation （WCF）會使用 Windows 來驗證使用者名稱和密碼。 不過，WCF 允許自訂的使用者名稱和密碼驗證配置，也稱為*驗證*程式。 若要納入自訂的使用者名稱和密碼驗證程式，請建立衍生自 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> 的類別，然後予以設定。

如需範例應用程式，請參閱[使用者名稱密碼驗證](../samples/user-name-password-validator.md)程式。

### <a name="to-create-a-custom-user-name-and-password-validator"></a>建立自訂的使用者名稱和密碼驗證程式

1. 建立衍生自 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> 的類別。

    [!code-csharp[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]

2. 覆寫 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> 方法，實作自訂驗證結構描述。

    請勿在實際執行環境使用下列範例中會覆寫 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> 方法的程式碼。 將此程式碼以自訂的使用者名稱和密碼驗證結構描述取代，其中可能包含從資料庫擷取使用者名稱和密碼組。

    若要將驗證錯誤傳回至用戶端，請在 <xref:System.ServiceModel.FaultException> 方法中擲回 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>。

    [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]

### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a>將服務設定為使用自訂的使用者名稱和密碼驗證程式

1. 設定繫結，此繫結會在 HTTP(S) 上的任何傳輸或傳輸層級安全性使用訊息安全性。

    使用訊息安全性時，請新增其中一個系統提供的系結，例如[@no__t 1wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)，或是支援訊息安全性和 `UserName` 認證類型的[@no__t 3customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) 。

    在 HTTP （S）上使用傳輸層級安全性時，請新增[\<wsHttpBinding >](../../configure-apps/file-schema/wcf/wshttpbinding.md)或[\<basicHttpBinding >](../../configure-apps/file-schema/wcf/basichttpbinding.md)、 [@no__t 5netTcpBinding >](../../configure-apps/file-schema/wcf/nettcpbinding.md)或使用 HTTP （s）的[@no__t 7customBinding >](../../configure-apps/file-schema/wcf/custombinding.md) ，以及@no__t 8 驗證配置。

    > [!NOTE]
    > 使用 [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] (含) 以後版本時，您可以將自訂使用者名稱和密碼驗證器搭配訊息安全性和傳輸安全性使用。 有了 WinFX，自訂使用者名稱和密碼驗證程式只能搭配訊息安全性使用。

    > [!TIP]
    > 如需在此內容中使用 @no__t 0netTcpBinding > 的詳細資訊，請參閱[@no__t 2security >](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)。

    1. 在設定檔中的[\<System system.servicemodel >](../../configure-apps/file-schema/wcf/system-servicemodel.md)元素底下，新增[@no__t 3bindings 的 >](../../configure-apps/file-schema/wcf/bindings.md)元素。

    2. 將[@no__t 1wsHttpBinding >](../../configure-apps/file-schema/wcf/wshttpbinding.md)或[@no__t 3basicHttpBinding >](../../configure-apps/file-schema/wcf/basichttpbinding.md)專案新增至 [系結] 區段。 如需建立 WCF 繫結項目的詳細資訊，請參閱 [How to：在設定中](../how-to-specify-a-service-binding-in-configuration.md)指定服務系結。

    3. 將[\<security >](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md)或[\<security >](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md)的 `mode` 屬性設定為 `Message`、`Transport` 或 `TransportWithMessageCredential`。

    4. 設定[\<message >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)或[\<transport >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)的 `clientCredentialType` 屬性。

        當使用訊息安全性時，請將[@no__t 2message >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md)的 `clientCredentialType` 屬性設定為 `UserName`。

        在 HTTP （S）上使用傳輸層級安全性時，請將[\<transport >](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)的 `clientCredentialType` 屬性或[@no__t 4transport >](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md)設定為 `Basic`。

        > [!NOTE]
        > 當 WCF 服務裝載于使用傳輸層級安全性的 Internet Information Services （IIS）中，而 <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> 屬性設定為 <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom> 時，自訂驗證配置會使用 Windows 驗證的子集。 這是因為在此案例中，IIS 會在 WCF 叫用自訂驗證器之前執行 Windows 驗證。

    如需建立 WCF 繫結項目的詳細資訊，請參閱 [How to：在設定中](../how-to-specify-a-service-binding-in-configuration.md)指定服務系結。

    下列範例顯示系結的設定程式碼：

    ```xml
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

2. 設定行為，指定自訂使用者名稱和密碼驗證程式用來驗證傳入之 <xref:System.IdentityModel.Tokens.UserNameSecurityToken> 安全性權杖的使用者名稱和密碼組。

    1. 做為[\<system >](../../configure-apps/file-schema/wcf/system-servicemodel.md)元素的子系，請新增[@no__t 3behaviors >](../../configure-apps/file-schema/wcf/behaviors.md)專案。

    2. 將[@no__t 1serviceBehaviors >](../../configure-apps/file-schema/wcf/servicebehaviors.md)新增至[\<behaviors >](../../configure-apps/file-schema/wcf/behaviors.md)元素。

    3. 新增[@no__t 1behavior >](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)元素，並將 @no__t 2 屬性設定為適當的值。

    4. 將[@no__t 1serviceCredentials >](../../configure-apps/file-schema/wcf/servicecredentials.md)新增至[\<behavior >](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)元素。

    5. 將[@no__t 1userNameAuthentication >](../../configure-apps/file-schema/wcf/usernameauthentication.md)新增至[@no__t 3serviceCredentials >](../../configure-apps/file-schema/wcf/servicecredentials.md)。

    6. 將 `userNamePasswordValidationMode` 設定為 `Custom`。

        > [!IMPORTANT]
        > 如果未設定 `userNamePasswordValidationMode` 值，WCF 會使用 Windows 驗證，而不是自訂使用者名稱和密碼驗證程式。

    7. 將 `customUserNamePasswordValidatorType` 設為代表自訂使用者名稱和密碼驗證程式的類型。

    下列範例會顯示此點的 `<serviceCredentials>` 片段：

    ```xml
    <serviceCredentials>
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />
    </serviceCredentials>
    ```

## <a name="example"></a>範例

以下程式碼範例將示範如何建立自訂的使用者名稱和密碼驗證程式。 請勿在實際執行環境使用會覆寫 <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> 方法的程式碼。 將此程式碼以自訂的使用者名稱和密碼驗證結構描述取代，其中可能包含從資料庫擷取使用者名稱和密碼組。

[!code-csharp[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
[!code-vb[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]

## <a name="see-also"></a>另請參閱

- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- [如何：使用 ASP.NET 成員資格提供者 @ no__t-0
- [驗證](authentication-in-wcf.md)
