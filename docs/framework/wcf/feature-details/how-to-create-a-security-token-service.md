---
title: HOW TO：建立安全性權杖服務
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 98e82101-4cff-4bb8-a220-f7abed3556e5
ms.openlocfilehash: 1d4964cf0379b35c4955bf45d8a7c0fd40477c9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787669"
---
# <a name="how-to-create-a-security-token-service"></a>HOW TO：建立安全性權杖服務
安全性權杖服務實作於 WS-Trust 規格定義的通訊協定。 此通訊協定定義用來核發、更新、取消及驗證安全性權杖的訊息格式以及訊息交換模式。 指定的安全性權杖服務提供一個或一個以上的這些功能。 此主題檢視最常見的狀況：實作權杖核發。  
  
## <a name="issuing-tokens"></a>核發權杖  
 WS-Trust 根據 `RequestSecurityToken` XML Schema 定義語言 (XSD) 結構描述項目以及執行權杖核發的 `RequestSecurityTokenResponse` XSD 結構描述項目，定義訊息的格式。 除此之外，它還定義關聯的動作統一資源識別源 (URI)。 URI 相關聯的動作`RequestSecurityToken`訊息是 `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue` 。 URI 相關聯的動作`RequestSecurityTokenResponse`訊息是 `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue` 。  
  
### <a name="request-message-structure"></a>要求訊息結構  
 發出要求訊息結構通常包括下列項目：  
  
- 要求輸入的 URI 值為`http://schemas.xmlsoap.org/ws/2005/02/trust/Issue`。
  
- 語彙基元型別 URI。 此 URI 的值是安全性判斷提示標記語言 (SAML) 1.1 權杖 `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1` 。  
  
- 此金鑰大小值表示關聯於核發之權杖的金鑰位元數。  
  
- 金鑰型別 URI。 對稱金鑰，這個 URI 的值是 `http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey` 。  
  
 此外，也許存在一些其他項目：  
  
- 用戶端提供的金錀資料。  
  
- 表示將使用已發行權杖之目標服務的範圍資訊。  
  
 安全性權杖服務在建構發出回應 (Issue Response) 訊息時，使用發出要求訊息內的資訊。  
  
## <a name="response-message-structure"></a>回應訊息結構  
 發出回應訊息結構通常包括下列項目：  
  
- 例如，核發的安全性權杖為 SAML 1.1 判斷提示。  
  
- 與安全性權杖相關聯的證明權杖。 就對稱金鑰而言，這經常是金鑰資料的加密格式。  
  
- 核發的安全性權杖的參照。 一般而言，安全性權杖服務會於已核發權杖出現於用戶端發出的後續訊息時，傳回可使用的參照，以及另一個當後續訊息無權杖時可使用的參照。  
  
 此外，也許存在一些其他項目：  
  
- 安全性權杖服務提供的金錀資料。  
  
- 要計算共用金鑰所需的演算法。  
  
- 核發權杖的存留期資訊。  
  
## <a name="processing-request-messages"></a>處理要求訊息  
 安全性權杖服務檢查各個要求訊息以處理核發要求，並且確保能核發滿足要求的權杖。 在建構要核發的權杖前，安全性權杖服務必須決定下列項目：  
  
- 所謂要求其實是核發權杖的要求。  
  
- 安全性權杖服務支援要求的權杖類型。  
  
- 要求者獲得授權提出要求。  
  
- 安全性權杖服務可滿足要求者對金鑰資料的期望。  
  
 建構權杖的兩個重要部分為決定要使用什麼金鑰簽署權杖，以及共用金鑰要用什麼金鑰加密。 權杖需要簽署，這樣當用戶端對目標服務提出權杖時，該服務才能判斷此權杖是否為自己信賴之安全性權杖服務所核發的權杖。 金鑰資料需要以目標服務能解密金鑰資料的方式進行加密。  
  
 簽署 SAML 判斷提示包括建立 <xref:System.IdentityModel.Tokens.SigningCredentials> 執行個體。 此類別的建構函式接受下列項目：  
  
- <xref:System.IdentityModel.Tokens.SecurityKey> 用於金鑰簽署 SAML 判斷提示。  
  
- 識別要使用之簽署演算法的字串。  
  
- 識別要使用之摘要演算法的字串。  
  
- 或者，<xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> 識別要用來簽署判斷提示的金鑰。  
  
 [!code-csharp[c_CreateSTS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#1)]
 [!code-vb[c_CreateSTS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#1)]  
  
 加密共用金鑰包含將金鑰資料以金鑰加密，目標服務能使用此金鑰解密共用金鑰。 一般而言，會使用目標服務的公開金鑰。  
  
 [!code-csharp[c_CreateSTS#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#2)]
 [!code-vb[c_CreateSTS#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#2)]  
  
 除此之外，加密金鑰還需要 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>。  
  
 [!code-csharp[c_CreateSTS#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#3)]
 [!code-vb[c_CreateSTS#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#3)]  
  
 然後使用 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> 建立 `SamlSubject` 做為 `SamlToken` 的一部分。  
  
 [!code-csharp[c_CreateSTS#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#4)]
 [!code-vb[c_CreateSTS#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#4)]  
  
 如需詳細資訊，請參閱 <<c0> [ 聯合範例](../../../../docs/framework/wcf/samples/federation-sample.md)。  
  
## <a name="creating-response-messages"></a>建立回應訊息  
 一旦安全性權杖服務處理發出的要求，並且建構出要核發之權杖以及證明金鑰後，就需要建構回應訊息，至少包括要求的權杖、證明權杖以及核發的權杖參照。 此核發的權杖一般而言是 <xref:System.IdentityModel.Tokens.SamlSecurityToken> 自 <xref:System.IdentityModel.Tokens.SamlAssertion>所建造，如以下範例所示。  
  
 [!code-csharp[c_CreateSTS#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#5)]
 [!code-vb[c_CreateSTS#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#5)]  
  
 當安全性權杖服務提供共用金鑰資料時，證明權杖就是由建立 <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken> 加以建構。  
  
 [!code-csharp[c_CreateSTS#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#6)]
 [!code-vb[c_CreateSTS#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#6)]  
  
 如需如何建構證明權杖，當用戶端和安全性權杖服務都提供共用金鑰的金鑰內容的詳細資訊，請參閱[聯合範例](../../../../docs/framework/wcf/samples/federation-sample.md)。  
  
 核發的權杖參照以建立 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> 類別執行個體而建構。  
  
 [!code-csharp[c_CreateSTS#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#7)]
 [!code-vb[c_CreateSTS#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#7)]  
  
 然後將這些不同的值序列化成回應訊息傳回用戶端。  
  
## <a name="example"></a>範例  
 安全性權杖服務的完整程式碼，請參閱[聯合範例](../../../../docs/framework/wcf/samples/federation-sample.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IdentityModel.Tokens.SigningCredentials>
- <xref:System.IdentityModel.Tokens.SecurityKey>
- <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>
- <xref:System.IdentityModel.Tokens.SamlSecurityToken>
- <xref:System.IdentityModel.Tokens.SamlAssertion>
- <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>
- <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause>
- [同盟範例](../../../../docs/framework/wcf/samples/federation-sample.md)
