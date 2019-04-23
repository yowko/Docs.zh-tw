---
title: HOW TO：建立自訂權杖
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SecurityTokenParameters class
- security [WCF], creating custom tokens
- WSSecurityTokenSerializer class
- SecurityToken class
ms.assetid: 6d892973-1558-4115-a9e1-696777776125
ms.openlocfilehash: 9fae195247dea4cbd049f7157f04e87bb97d6f4d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304658"
---
# <a name="how-to-create-a-custom-token"></a>HOW TO：建立自訂權杖
本主題說明如何使用 <xref:System.IdentityModel.Tokens.SecurityToken> 類別來建立自訂安全性權杖，以及如何將它與自訂安全性權杖提供者和驗證器整合。 如需完整的程式碼範例，請參閱[自訂語彙基元](../../../../docs/framework/wcf/samples/custom-token.md)範例。  
  
 A*安全性權杖*是本質上由 Windows Communication Foundation (WCF) 安全性架構用來代表 SOAP 訊息內的寄件者的相關宣告的 XML 項目。 WCF 安全性系統提供的驗證模式提供各種權杖。 範例包括 <xref:System.IdentityModel.Tokens.X509SecurityToken> 類別所代表的 X.509 憑證安全性權杖，或是 <xref:System.IdentityModel.Tokens.UserNameSecurityToken> 類別所代表的使用者名稱安全性權杖。  
  
 有時候提供的類型並不支援驗證模式或認證。 在此情況下，您就需要建立自訂安全性權杖，以便在 SOAP 訊息內部提供自訂認證的 XML 表示法。  
  
 下列程序顯示如何建立自訂安全性權杖，以及如何將它與 WCF 安全性基礎結構整合。 本主題將建立信用卡權杖，它可以用來將用戶端的信用卡相關資訊傳遞給伺服器。  
  
 如需有關自訂認證和安全性權杖管理員的詳細資訊，請參閱[逐步解說：建立自訂用戶端和服務認證](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)。  
  
 如需其他代表安全性權杖的類別，請參閱 <xref:System.IdentityModel.Tokens> 命名空間。  
  
## <a name="procedures"></a>程序  
 您必須提供用戶端應用程式為安全性基礎結構指定信用卡資訊的方式， 此資訊可由自訂用戶端認證類別提供給應用程式使用。 第一步就是為自訂用戶端認證建立代表信用卡資訊的類別。  
  
#### <a name="to-create-a-class-that-represents-credit-card-information-inside-client-credentials"></a>若要在用戶端認證內部建立代表信用卡資訊的類別  
  
1. 為應用程式定義代表信用卡資訊的新類別。 下列範例將類別命名為 `CreditCardInfo`。  
  
2. 將適當的屬性加入至類別，讓應用程式能夠設定自訂權杖所需的必要資訊。 在此範例中，類別具有三種屬性：`CardNumber`、`CardIssuer` 和 `ExpirationDate`。  
  
     [!code-csharp[c_CustomToken#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#4)]
     [!code-vb[c_CustomToken#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#4)]  
  
 接下來，必須建立可代表自訂安全性權杖的類別。 這個類別的安全性權杖提供者、 驗證程式和序列化程式類別來傳遞安全性權杖與 WCF 安全性基礎結構的相關資訊。  
  
#### <a name="to-create-a-custom-security-token-class"></a>若要建立自訂安全性權杖類別  
  
1. 定義衍生自 <xref:System.IdentityModel.Tokens.SecurityToken> 類別的新類別。 本範例會建立名為 `CreditCardToken` 的類別。  
  
2. 覆寫 <xref:System.IdentityModel.Tokens.SecurityToken.Id%2A> 屬性。 這個屬性是用來取得安全性權杖的區域識別項，該識別項則是用來指向 SOAP 訊息內來自其他項目的安全性權杖 XML 表示法。 在此範例中，可以將權杖識別項當成建構函式參數傳遞給它，否則每次建立安全性權杖執行個體時，就會產生新的隨機權杖識別項。  
  
3. 實作 <xref:System.IdentityModel.Tokens.SecurityToken.SecurityKeys%2A> 屬性。 此屬性會傳回安全性權杖執行個體所代表的安全性金鑰集合。 WCF 可以使用這類金鑰來簽署或加密部分 SOAP 訊息。 在此範例中，信用卡安全性權杖無法包含任何安全性金鑰；因此，實作一律會傳回空的集合。  
  
4. 覆寫 <xref:System.IdentityModel.Tokens.SecurityToken.ValidFrom%2A> 和 <xref:System.IdentityModel.Tokens.SecurityToken.ValidTo%2A> 屬性。 這些屬性可由 WCF 決定安全性權杖執行個體的有效性。 在此範例中，信用卡安全性權杖只擁有一個到期日，因此 `ValidFrom` 屬性會傳回 <xref:System.DateTime>，這個值代表執行個體的建立日期與時間。  
  
     [!code-csharp[c_CustomToken#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#1)]
     [!code-vb[c_CustomToken#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#1)]  
  
 新的安全性權杖類型建立完畢後，需要實作 <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> 類別。 這項實作會在安全性繫結項目組態中用來代表新的權杖類型。 安全性權杖參數類別可當成範本，用來比對實際安全性權杖執行個體與訊息處理時間。 範本所提供的其他屬性可供應用程式用來指定準則，安全性權杖必須符合這個準則才能加以使用或驗證。 下列範例不會新增任何額外的屬性，因此只會比對時，WCF 基礎結構搜尋安全性權杖執行個體使用，或驗證的語彙基元型別安全性。  
  
#### <a name="to-create-a-custom-security-token-parameters-class"></a>若要建立自訂安全性權杖參數類別  
  
1. 定義衍生自 <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> 類別的新類別。  
  
2. 實作 <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.CloneCore%2A> 方法。 複製類別中已定義的所有內部欄位 (如果有的話)。 此範例並未定義任何其他欄位。  
  
3. 實作 <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsClientAuthentication%2A> 唯讀屬性。 如果此類別所代表的安全性權杖類型可用來驗證服務的用戶端，則這個屬性會傳回 `true`。 在此範例中，信用卡安全性權杖可用來驗證服務的用戶端。  
  
4. 實作 <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsServerAuthentication%2A> 唯讀屬性。 如果此類別所代表的安全性權杖類型可用來驗證用戶端服務，則這個屬性會傳回 `true`。 在此範例中，信用卡安全性權杖不可用來驗證用戶端服務。  
  
5. 實作 <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.SupportsClientWindowsIdentity%2A> 唯讀屬性。 如果此類別所代表的安全性權杖類型可用來對應至 Windows 帳戶，則這個屬性會傳回 `true`。 因此，驗證結果會由 <xref:System.Security.Principal.WindowsIdentity> 類別執行個體來表示。 在此範例中，權杖無法對應至 Windows 帳戶。  
  
6. 實作 <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.CreateKeyIdentifierClause%28System.IdentityModel.Tokens.SecurityToken%2CSystem.ServiceModel.Security.Tokens.SecurityTokenReferenceStyle%29> 方法。 如果需要此安全性權杖參數類別所代表的安全性權杖執行個體的參考，則 WCF 安全性架構會呼叫這個方法。 實際安全性權杖執行個體與可指定所要求之參考型別的 <xref:System.ServiceModel.Security.Tokens.SecurityTokenReferenceStyle> 會同時當成引數傳遞至此方法。 在此範例中，信用卡安全性權杖僅支援內部參考。 <xref:System.IdentityModel.Tokens.SecurityToken> 類別具有建立內部參考的功能，因此實作不需要其他程式碼。  
  
7. 實作 <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.InitializeSecurityTokenRequirement%28System.IdentityModel.Selectors.SecurityTokenRequirement%29> 方法。 會呼叫這個方法，將安全性權杖參數類別執行個體轉換成的執行個體的 wcf<xref:System.IdentityModel.Selectors.SecurityTokenRequirement>類別。 安全性權杖提供者會使用此結果來建立適當的安全性權杖執行個體。  
  
     [!code-csharp[c_CustomToken#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#2)]
     [!code-vb[c_CustomToken#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#2)]  
  
 安全性權杖會在 SOAP 訊息內傳輸，這麼做需要在記憶體中的安全性權杖表示與網路上的表示之間使用轉譯機制。 WCF 會使用安全性權杖序列化程式來完成這項工作。 每個自訂權杖必須搭配自訂安全性權杖序列化程式，這個程式可以序列化與還原序列化來自 SOAP 訊息的自訂安全性權杖。  
  
> [!NOTE]
>  衍生金鑰預設為啟用。 如果您建立自訂安全性權杖，並使用它當做主要權杖時，WCF 會從它衍生金鑰。 這時，它會呼叫自訂安全性權杖序列化程式來寫入自訂安全性權杖的 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause>，同時將 `DerivedKeyToken` 序列化至連線。 在接收端，將連線上的權杖還原序列化時，`DerivedKeyToken` 序列化程式需要 `SecurityTokenReference` 項目做為它底下的最上層子項目。 如果自訂安全性權杖序列化程式在序列化其子句型別時未加入 `SecurityTokenReference` 項目，則會擲回例外狀況。  
  
#### <a name="to-create-a-custom-security-token-serializer"></a>若要建立自訂安全性權杖序列化程式  
  
1. 定義衍生自 <xref:System.ServiceModel.Security.WSSecurityTokenSerializer> 類別的新類別。  
  
2. 覆寫 <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.CanReadTokenCore%28System.Xml.XmlReader%29> 方法，這個方法需要靠 <xref:System.Xml.XmlReader> 讀取 XML 串流。 如果序列化程式實作可以根據目前指定的項目來還原序列化安全性權杖，則方法會傳回 `true`。 在此範例中，此方法會檢查 XML 讀取器目前的 XML 項目是否具備正確的項目名稱與命名空間。 如果不具備的話，它會呼叫此方法的基底類別實作來處理 XML 項目。  
  
3. 覆寫 <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.ReadTokenCore%28System.Xml.XmlReader%2CSystem.IdentityModel.Selectors.SecurityTokenResolver%29> 方法。 此方法會讀取安全性權杖的 XML 內容，並且為權杖建構適當的記憶體內部表示法。 如果它無法辨識傳入之 XML 讀取器所在的 XML 項目，則會呼叫基底類別實作來處理系統提供的權杖類型。  
  
4. 覆寫 <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.CanWriteTokenCore%28System.IdentityModel.Tokens.SecurityToken%29> 方法。 如果此方法可將記憶體內部的權杖表示法 (當成引數傳入) 轉換為 XML 表示法，則會傳回 `true`。 如果無法轉換，則會呼叫基底類別實作。  
  
5. 覆寫 <xref:System.ServiceModel.Security.WSSecurityTokenSerializer.WriteTokenCore%28System.Xml.XmlWriter%2CSystem.IdentityModel.Tokens.SecurityToken%29> 方法。 此方法會將記憶體內部的安全性權杖表示法轉換為 XML 表示法。 如果無法轉換，則會呼叫基底類別實作。  
  
     [!code-csharp[c_CustomToken#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#3)]
     [!code-vb[c_CustomToken#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#3)]  
  
 在完成上述四個程序之後，請將自訂安全性權杖與安全性權杖提供者、驗證器、管理員，以及用戶端與服務認證，全部整合在一起。  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-provider"></a>若要將自訂安全性權杖與安全性權杖提供者整合  
  
1. 安全性權杖提供者會建立、修改 (視需要) 和傳回權杖的執行個體。 若要建立自訂安全性權杖的自訂提供者，請建立繼承自 <xref:System.IdentityModel.Selectors.SecurityTokenProvider> 類別的類別。 下列範例會覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> 方法以傳回 `CreditCardToken` 的執行個體。 如需有關自訂安全性權杖提供者的詳細資訊，請參閱[How to:建立自訂安全性權杖提供者](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)。  
  
     [!code-csharp[c_CustomToken#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#6)]
     [!code-vb[c_CustomToken#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#6)]  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-authenticator"></a>若要將自訂安全性權杖與安全性權杖驗證器整合  
  
1. 當安全性權杖從訊息中擷取出來時，安全性權杖驗證器會驗證其內容。 若要建立自訂安全性權杖的自訂驗證器，請建立繼承自 <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> 類別的類別。 下列範例會覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.ValidateTokenCore%2A> 方法。 如需有關自訂安全性權杖驗證器的詳細資訊，請參閱[How to:建立自訂安全性權杖驗證器](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)。  
  
     [!code-csharp[c_CustomToken#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#7)]
     [!code-vb[c_CustomToken#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#7)]  
  
     [!code-csharp[c_CustomToken#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#12)]
     [!code-vb[c_CustomToken#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#12)]  
  
#### <a name="to-integrate-the-custom-security-token-with-a-security-token-manager"></a>若要將自訂安全性權杖與安全性權杖管理員整合  
  
1. 安全性權杖管理員會建立適當的權杖提供者、安全性驗證器，以及權杖序列化程式執行個體。 若要建立自訂的權杖管理員，請建立繼承自 <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> 類別的類別。 該類別的主要方法會使用 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> 來建立適當的提供者與用戶端或服務認證。 如需有關自訂安全性權杖管理員的詳細資訊，請參閱[逐步解說：建立自訂用戶端和服務認證](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)。  
  
     [!code-csharp[c_CustomToken#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#8)]
     [!code-vb[c_CustomToken#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#8)]  
  
     [!code-csharp[c_CustomToken#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#9)]
     [!code-vb[c_CustomToken#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#9)]  
  
#### <a name="to-integrate-the-custom-security-token-with-custom-client-and-service-credentials"></a>若要將自訂安全性權杖與自訂用戶端及服務認證整合  
  
1. 您必須新增自訂的用戶端及服務認證才能提供應用程式的 API，以便指定自訂權杖資訊，而先前建立的自訂安全性權杖基礎結構會使用這項資訊來提供並驗證自訂安全性權杖內容。 下列範例會示範執行此作業的方法。 如需有關自訂用戶端和服務認證的詳細資訊，請參閱[逐步解說：建立自訂用戶端和服務認證](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)。  
  
     [!code-csharp[c_CustomToken#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#10)]
     [!code-vb[c_CustomToken#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#10)]  
  
     [!code-csharp[c_customToken#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#11)]
     [!code-vb[c_customToken#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#11)]  
  
 先前建立的自訂安全性權杖參數類別用來告知 WCF 安全性架構與服務通訊時，必須使用自訂安全性權杖。 下列程序會示範執行此作業的方法。  
  
#### <a name="to-integrate-the-custom-security-token-with-the-binding"></a>若要將自訂安全性權杖與繫結整合  
  
1. 您必須在 <xref:System.ServiceModel.Channels.SecurityBindingElement> 類別上公開的其中一個權杖參數集合指定自訂安全性權杖參數類別。 下列範例會使用 `SignedEncrypted` 所傳回的集合。 程式碼會將信用卡自訂權杖新增至每個從服務用戶端傳送的訊息，並且自動簽署並加密其內容。  
  
     [!code-csharp[c_CustomToken#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtoken/cs/source.cs#13)]
     [!code-vb[c_CustomToken#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtoken/vb/source.vb#13)]  
  
 本主題顯示實作和使用自訂權杖所需的各種程式碼。 若要查看完整的範例方式的所有這些程式碼拼湊在一起，請參閱 <<c0> [ 自訂語彙基元](../../../../docs/framework/wcf/samples/custom-token.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IdentityModel.Tokens.SecurityToken>
- <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters>
- <xref:System.ServiceModel.Security.WSSecurityTokenSerializer>
- <xref:System.IdentityModel.Selectors.SecurityTokenProvider>
- <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>
- <xref:System.IdentityModel.Selectors.SecurityTokenManager>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceCredentials>
- <xref:System.ServiceModel.Channels.SecurityBindingElement>
- [逐步解說：建立自訂用戶端和服務認證](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)
- [如何：建立自訂安全性權杖驗證器](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)
- [如何：建立自訂安全性權杖提供者](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)
