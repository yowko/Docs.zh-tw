---
title: 逐步解說：建立自訂用戶端與服務認證
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b5ba5c3-0c6c-48e9-9e46-54acaec443ba
ms.openlocfilehash: eb60bc474ae0dd8cec85ca36f68b12764d46044d
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040212"
---
# <a name="walkthrough-creating-custom-client-and-service-credentials"></a>逐步解說：建立自訂用戶端與服務認證

此主題顯示如何實作自訂用戶端和服務認證，以及如何使用來自應用程式碼的自訂認證。

## <a name="credentials-extensibility-classes"></a>認證擴充性類別

<xref:System.ServiceModel.Description.ClientCredentials> 和<xref:System.ServiceModel.Description.ServiceCredentials>類別是 Windows Communication Foundation (WCF) 安全性擴充性的主要進入點。 這些認證類別提供能夠讓應用程式碼設定認證資訊，以及將認證類型轉換為安全性權杖的 API (*安全性權杖*是用來在 SOAP 訊息內傳輸認證資訊的格式)。這些認證類別的責任可以分為兩部分：

- 提供 API 讓應用程式設定認證資訊。

- 執行當做 <xref:System.IdentityModel.Selectors.SecurityTokenManager> 實作的處理站。

<xref:System.ServiceModel.Description.ClientCredentials> 和 <xref:System.ServiceModel.Description.ServiceCredentials> 類別都繼承自定義傳回 <xref:System.ServiceModel.Security.SecurityCredentialsManager> 之合約的抽象 <xref:System.IdentityModel.Selectors.SecurityTokenManager> 類別。

WCF 中提供的預設實現支援系統提供的認證類型, 並建立能夠處理這些認證類型的安全性權杖管理員。

## <a name="reasons-to-customize"></a>自訂原因

有幾項自訂用戶端或服務認證類別的原因。 最重要的是, 變更處理系統提供之認證類型的預設 WCF 安全性行為的需求, 特別是基於下列原因:

- 使用其他擴充點無法進行若干變更。

- 為了加入新的認證類型。

- 為了加入新的自訂安全性權杖類型。

此主題描述如何實作自訂用戶端和服務認證，以及如何在應用程式碼使用它們。

## <a name="first-in-a-series"></a>第一步

建立自訂認證類別只是第一個步驟, 因為自訂認證的原因是要變更關於認證布建、安全性權杖序列化或驗證的 WCF 行為。 本章節中的其他主題描述如何建立自訂序列化程式和驗證器。 就這一點而言，建立自訂認證類別是所有步驟的第一個主題。 只有在建立自訂認證後才能完成後續動作 (建立自訂序列化程式和驗證器)。 建構在此主題上的其他主題包含：

- [如何：建立自訂安全性權杖提供者](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)

- [如何：建立自訂安全性權杖驗證器](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)

- [如何：建立自訂權杖](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)。

## <a name="procedures"></a>程序

#### <a name="to-implement-custom-client-credentials"></a>實作自訂用戶端認證

1. 定義衍生自 <xref:System.ServiceModel.Description.ClientCredentials> 類別的新類別。

2. 選擇性。 為新的認證類型加入新方法或屬性。 如果您不需要新增新的認證類型，請略過這個步驟。 下列範例即是加入 `CreditCardNumber` 屬性。

3. 覆寫 <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> 方法。 當使用自訂用戶端認證時, WCF 安全性基礎結構會自動呼叫此方法。 這個方法是負責建立和傳回 <xref:System.IdentityModel.Selectors.SecurityTokenManager> 類別實作的執行個體。

    > [!IMPORTANT]
    > 請注意，覆寫 <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> 方法以建立自訂安全性權杖管理員是很重要的。 衍生自 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> 的安全性權杖管理員，必須傳回衍生自 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 的自訂安全性權杖提供者，以建立實際的安全性權杖。 若未依照這個模式建立安全性權杖，應用程式在快取 <xref:System.ServiceModel.ChannelFactory> 物件時 (此乃 WCF 用戶端 Proxy 的預設行為) 可能會運作不正常，以致難免遭受提高權限攻擊。 自訂認證物件是快取為 <xref:System.ServiceModel.ChannelFactory> 的一部分。 不過，自訂 <xref:System.IdentityModel.Selectors.SecurityTokenManager> 則為每次叫用時所建立，因而只要將權仗建立邏輯置於 <xref:System.IdentityModel.Selectors.SecurityTokenManager> 中，便能減緩安全性威脅。

4. 覆寫 <xref:System.ServiceModel.Description.ClientCredentials.CloneCore%2A> 方法。

    [!code-csharp[c_CustomCredentials#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#1)]
    [!code-vb[c_CustomCredentials#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#1)]

#### <a name="to-implement-a-custom-client-security-token-manager"></a>實作自訂用戶端安全性權杖管理員

1. 定義衍生自 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> 的新類別。

2. 選擇性。 如果必須建立自訂 <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> 實作，請覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 方法。 如需有關自訂安全性權杖提供者的[詳細資訊, 請參閱如何:建立自訂安全性權杖提供](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)者。

3. 選擇性。 如果必須建立自訂 <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%28System.IdentityModel.Selectors.SecurityTokenRequirement%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%40%29> 實作，請覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> 方法。 如需有關自訂安全性權杖驗證器的詳細[資訊, 請參閱如何:建立自訂安全性權杖驗證](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)器。

4. 選擇性。 如果必須建立自訂 <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%2A>，請覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> 方法。 如需有關自訂安全性權杖和自訂安全性權杖序列化程式[的詳細資訊, 請參閱如何:建立自訂權杖](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)。

    [!code-csharp[c_CustomCredentials#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#2)]
    [!code-vb[c_CustomCredentials#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#2)]

#### <a name="to-use-a-custom-client-credentials-from-application-code"></a>使用來自應用程式碼的自訂用戶端認證

1. 建立所產生之用戶端的執行個體以代表服務介面，或建立 <xref:System.ServiceModel.ChannelFactory> 的執行個體指向想要通訊的服務。

2. 從 <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> 集合中移除系統提供的用戶端認證行為，您可以透過 <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> 屬性存取這個集合。

3. 建立自訂用戶端認證類別的新執行個體，並將其新增至 <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> 集合中，您可以透過 <xref:System.ServiceModel.ChannelFactory.Endpoint%2A> 屬性存取這個集合。

    [!code-csharp[c_CustomCredentials#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#3)]
    [!code-vb[c_CustomCredentials#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/client/client.vb#3)]

前面的程序示範如何從應用程式程式碼使用用戶端認證。 WCF 認證也可以使用應用程式佈建檔來設定。 在硬式編碼方面通常偏好使用應用程式組態，因為能夠在不修改原始程式碼、重新編譯和重新部署的情況下修改應用程式參數。

下一個程序描述如何提供自訂認證組態的支援。

#### <a name="creating-a-configuration-handler-for-custom-client-credentials"></a>建立自訂用戶端認證的組態處理常式

1. 定義衍生自 <xref:System.ServiceModel.Configuration.ClientCredentialsElement> 的新類別。

2. 選擇性。 針對想要透過應用程式組態公開的所有其他組態參數新增屬性。 下列範例會新增一個名為 `CreditCardNumber` 的屬性。

3. 覆寫 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.BehaviorType%2A> 屬性以傳回使用組態項目建立之自訂用戶端認證類別的型別。

4. 覆寫 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement.CreateBehavior%2A> 方法。 這個方法會根據從組態檔載入的設定，負責建立和傳回自訂認證類別的執行個體。 請呼叫這個方法的基底 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ApplyConfiguration%28System.ServiceModel.Description.ClientCredentials%29> 方法，擷取已載入自訂用戶端認證執行個體之系統提供的認證設定。

5. 選擇性。 如果您在步驟 2 新增其他屬性，就需要覆寫 <xref:System.Configuration.ConfigurationElement.Properties%2A> 屬性以登錄組態架構的其他組態設定，才能加以辨認。 結合屬性與基底類別屬性，以便透過這個自訂用戶端認證組態項目設定系統提供的設定。

    [!code-csharp[c_CustomCredentials#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#7)]
    [!code-vb[c_CustomCredentials#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#7)]

一旦有了設定處理常式類別, 它就可以整合到 WCF 設定架構中。 就能夠在用戶端端點行為項目中使用自訂用戶端認證，如同下一個程序中所示。

#### <a name="to-register-and-use-a-custom-client-credentials-configuration-handler-in-the-application-configuration"></a>在應用程式組態中登錄和使用自訂用戶端認證組態處理常式

1. 將 <`extensions`> 元素和 <`behaviorExtensions`> 專案新增至設定檔。

2. 將 <`add`> 元素新增至 <`behaviorExtensions`的`name` > 專案, 並將屬性設定為適當的值。

3. 將 `type` 屬性設定為完整型別名稱。 同時包含組件名稱和其他組件屬性。

    ```xml
    <system.serviceModel>
      <extensions>
        <behaviorExtensions>
          <add name="myClientCredentials" type="Microsoft.ServiceModel.Samples.MyClientCredentialsConfigHandler, CustomCredentials, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />
        </behaviorExtensions>
      </extensions>
    <system.serviceModel>
    ```

4. 在註冊您的設定處理常式之後, 您可以在相同的設定檔中使用自訂認證元素, 而不`clientCredentials`是系統提供的 < > 元素。 您可以同時使用系統提供的屬性，以及新增至組態處理常式實作的任何新屬性。 下列程式碼範例會使用 `creditCardNumber` 屬性 (Attribute) 設定自訂屬性 (Property) 的值。

    ```xml
    <behaviors>
      <endpointBehaviors>
        <behavior name="myClientCredentialsBehavior">
          <myClientCredentials creditCardNumber="123-123-123"/>
        </behavior>
      </endpointBehaviors>
    </behaviors>
    ```

#### <a name="to-implement-custom-service-credentials"></a>實作自訂服務認證

1. 定義衍生自 <xref:System.ServiceModel.Description.ServiceCredentials> 的新類別。

2. 選擇性。 新增新的屬性以提供已新增之新認證值的 API。 如果您不需要新增新的認證值，請略過這個步驟。 下列程式碼範例會新增 `AdditionalCertificate` 屬性。

3. 覆寫 <xref:System.ServiceModel.Security.SecurityCredentialsManager.CreateSecurityTokenManager%2A> 方法。 當使用自訂用戶端認證時, WCF 基礎結構會自動呼叫此方法。 這個方法是負責建立和傳回 <xref:System.IdentityModel.Selectors.SecurityTokenManager> 類別實作的執行個體 (在下一個程序中會描述)。

4. 選擇性。 覆寫 <xref:System.ServiceModel.Description.ServiceCredentials.CloneCore%2A> 方法。 只有在將新屬性或內部欄位新增至自訂用戶端認證實作時才會需要這麼做。

    [!code-csharp[c_CustomCredentials#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#4)]
    [!code-vb[c_CustomCredentials#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#4)]

#### <a name="to-implement-a-custom-service-security-token-manager"></a>實作自訂服務安全性權杖管理員

1. 定義衍生自 <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> 類別的新類別。

2. 選擇性。 如果必須建立自訂 <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenProvider%2A> 實作，請覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 方法。 如需有關自訂安全性權杖提供者的[詳細資訊, 請參閱如何:建立自訂安全性權杖提供](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)者。

3. 選擇性。 如果必須建立自訂 <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> 實作，請覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> 方法。 如需有關自訂安全性權杖驗證器的詳細[資訊, 請參閱如何:建立自訂安全性權杖驗證](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)器主題。

4. 選擇性。 如果必須建立自訂 <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenSerializer%28System.IdentityModel.Selectors.SecurityTokenVersion%29>，請覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenSerializer> 方法。 如需有關自訂安全性權杖和自訂安全性權杖序列化程式[的詳細資訊, 請參閱如何:建立自訂權杖](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)。

    [!code-csharp[c_CustomCredentials#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#5)]
    [!code-vb[c_CustomCredentials#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#5)]

#### <a name="to-use-custom-service-credentials-from-application-code"></a>使用來自應用程式碼的自訂服務認證

1. 建立 <xref:System.ServiceModel.ServiceHost>的執行個體。

2. 從 <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> 集合移除系統提供的服務認證行為。

3. 建立自訂服務認證類別的新執行個體，並將其新增至 <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> 集合。

    [!code-csharp[c_CustomCredentials#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customcredentials/cs/source.cs#6)]
    [!code-vb[c_CustomCredentials#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customcredentials/vb/service/service.vb#6)]

使用上列程序「`To create a configuration handler for custom client credentials`」和「`To register and use a custom client credentials configuration handler in the application configuration`」中描述的步驟加入對組態的支援。唯一的差別是使用 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement> 類別而不是 <xref:System.ServiceModel.Configuration.ClientCredentialsElement> 類別，當做組態處理常式的基底類別。 然後可以在使用系統提供 `<serviceCredentials>` 項目的地方使用自訂服務認證項目。

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.Security.SecurityCredentialsManager>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement>
- [如何：建立自訂安全性權杖提供者](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)
- [如何：建立自訂安全性權杖驗證器](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)
- [如何：建立自訂權杖](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)
