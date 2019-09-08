---
title: 作法：使用個別 X.509 憑證簽署與加密
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, extensibility
- ClientCredentials class
- ClientCredentialsSecurityTokenManager class
ms.assetid: 0b06ce4e-7835-4d82-8baf-d525c71a0e49
ms.openlocfilehash: e464aff46f311ede1cd629fb459ade9a6e627d59
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796955"
---
# <a name="how-to-use-separate-x509-certificates-for-signing-and-encryption"></a>作法：使用個別 X.509 憑證簽署與加密

本主題說明如何將 Windows Communication Foundation （WCF）設定為在用戶端和服務上使用不同憑證來進行訊息簽章和加密。

若要啟用用於簽署和加密的個別憑證，必須建立自訂用戶端或服務認證（或兩者），因為 WCF 不會提供可設定多個用戶端或服務憑證的 API。 此外，必須提供安全性權杖管理員才能運用多份憑證的資訊，以及建立可用於特定金鑰使用方式和訊息方向的適當安全性權杖提供者。

下方圖表會顯示所使用的主要類別、它們繼承的來源類別 (以上指標示)，以及特定方向和屬性所傳回的類別。

- `MyClientCredentials` 為 <xref:System.ServiceModel.Description.ClientCredentials> 的自訂實作。

  - 它在圖表中所顯示的屬性都會傳回 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> 的執行個體。

  - 它的方法 <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> 會傳回 `MyClientCredentialsSecurityTokenManager` 的執行個體。

- `MyClientCredentialsSecurityTokenManager` 為 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> 的自訂實作。

  - 它的方法 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> 會傳回 <xref:System.IdentityModel.Selectors.X509SecurityTokenProvider> 的執行個體。

![顯示如何使用用戶端認證的圖表](./media/e4971edd-a59f-4571-b36f-7e6b2f0d610f.gif "e4971edd-a59f-4571-b36f-7e6b2f0d610f")

如需自訂認證的詳細資訊[，請參閱逐步解說：建立自訂用戶端和](walkthrough-creating-custom-client-and-service-credentials.md)服務認證。

此外，您必須建立自訂身分識別驗證器，並將驗證器以自訂繫結連結到一個安全性繫結項目。 同時，不要使用預設認證，而必須使用自訂認證。

以下的圖表會顯示自訂繫結中使用的類別，以及自訂身分識別驗證器所連結的方法。 其中包含幾個繫結項目，全部都是繼承自 <xref:System.ServiceModel.Channels.BindingElement>。 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> 有 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings><xref:System.ServiceModel.Security.IdentityVerifier>屬性，會傳回 `MyIdentityVerifier`(便是自訂 的來源)的執行個體。

![顯示自訂繫結項目的圖表](./media/dddea4a2-0bb4-4921-9bf4-20d4d82c3da5.gif "dddea4a2-0bb4-4921-9bf4-20d4d82c3da5")

如需建立自訂身分識別驗證器的詳細資訊，請參閱如何：[如何：建立自訂用戶端身分](how-to-create-a-custom-client-identity-verifier.md)識別驗證器。

### <a name="to-use-separate-certificates-for-signing-and-encryption"></a>使用個別憑證簽署與加密

1. 定義從 <xref:System.ServiceModel.Description.ClientCredentials> 類別繼承的新用戶端認證類別。 建立四個新屬性即可允許使用多個憑證規格：`ClientSigningCertificate`、`ClientEncryptingCertificate`、`ServiceSigningCertificate``ServiceEncryptingCertificate`及 。 此外，覆寫 <xref:System.ServiceModel.Description.ClientCredentials.CreateSecurityTokenManager%2A> 方法，以傳回下一步所定義之自訂 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> 類別的執行個體。

     [!code-csharp[c_FourCerts#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#1)]
     [!code-vb[c_FourCerts#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#1)]

2. 定義從 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> 類別繼承的新用戶端安全性權杖管理員。 覆寫 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> 方法，即可建立適當的安全性權杖提供者。 `requirement` 參數 (<xref:System.IdentityModel.Selectors.SecurityTokenRequirement>) 可提供訊息方向和金鑰使用方式。

     [!code-csharp[c_FourCerts#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#2)]
     [!code-vb[c_FourCerts#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#2)]

3. 定義從 <xref:System.ServiceModel.Description.ServiceCredentials> 類別繼承的新服務認證類別。 建立四個新屬性即可允許使用多個憑證規格：`ClientSigningCertificate`、`ClientEncryptingCertificate`、`ServiceSigningCertificate``ServiceEncryptingCertificate`及 。 此外，覆寫 <xref:System.ServiceModel.Description.ServiceCredentials.CreateSecurityTokenManager%2A> 方法，以傳回下一步所定義之自訂 <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> 類別的執行個體。

     [!code-csharp[c_FourCerts#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#3)]
     [!code-vb[c_FourCerts#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#3)]

4. 定義從 <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> 類別繼承的新服務安全性權杖管理員。 覆寫 <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager.CreateSecurityTokenProvider%2A> 方法，即可建立已指定傳入訊息方向和金鑰使用方式的適當安全性權杖提供者。

     [!code-csharp[c_FourCerts#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#4)]
     [!code-vb[c_FourCerts#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#4)]

### <a name="to-use-multiple-certificates-on-the-client"></a>使用用戶端上的多個憑證

1. 建立自訂繫結。 安全性繫結項目必須在雙工模式下運作，才能在要求和回應時提供不同的安全性權杖提供者。 執行這項作業的一種方法是使用具雙工能力的傳輸或使用 <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>，如下列程式碼所示。 將下一步所定義的自訂 <xref:System.ServiceModel.Security.IdentityVerifier> 連結到安全性繫結項目。 以先前建立的自訂用戶端認證取代預設的用戶端認證。

     [!code-csharp[c_FourCerts#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#5)]
     [!code-vb[c_FourCerts#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#5)]

2. 定義一個自訂的 <xref:System.ServiceModel.Security.IdentityVerifier>。 服務會擁有多個識別，因為此時會使用不同的憑證來加密要求及簽署回應。

    > [!NOTE]
    > 在下列範例中所提供的自訂識別驗證器，並不會示範執行任何的端點識別檢查。 但是在實際執行程式碼 (Production Code) 中不建議這樣做。

     [!code-csharp[c_FourCerts#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#6)]
     [!code-vb[c_FourCerts#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#6)]

### <a name="to-use-multiple-certificates-on-the-service"></a>使用服務上的多個憑證

1. 建立自訂繫結。 安全性繫結項目必須在雙工模式下運作，才能在要求和回應時提供不同的安全性權杖提供者。 在用戶端上，使用具雙工能力的傳輸或使用 <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>，如下列程式碼所示。 以先前建立的自訂服務認證取代預設的服務認證。

     [!code-csharp[c_FourCerts#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_fourcerts/cs/source.cs#7)]
     [!code-vb[c_FourCerts#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_fourcerts/vb/source.vb#7)]

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager>
- <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager>
- <xref:System.ServiceModel.Security.IdentityVerifier>
- [逐步解說：建立自訂用戶端和服務認證](walkthrough-creating-custom-client-and-service-credentials.md)
