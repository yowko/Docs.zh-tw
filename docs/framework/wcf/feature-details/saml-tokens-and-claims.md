---
title: SAML 權杖與宣告
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
- issued tokens
- SAML token
ms.assetid: 930b6e34-9eab-4e95-826c-4e06659bb977
ms.openlocfilehash: f1f7a15d1457390bf77f5e53c7fd657304725df6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218208"
---
# <a name="saml-tokens-and-claims"></a>SAML 權杖與宣告
安全性判斷提示標記語言 (SAML)*語彙基元*宣告的 XML 表示。 根據預設，會在聯合的安全性案例中，使用 Windows Communication Foundation (WCF) 的 SAML 權杖*發行的權杖*。  
  
 SAML 權杖包含一實體對另一實體所做出之宣告集合的陳述式。 例如，在聯合安全性案例中，陳述式是由系統中關於使用者的安全性權杖服務所表示。 安全性權杖服務會簽署 SAML 權杖，以表示權杖中所含陳述式的真實性。 除此之外，SAML 權杖會與 SAML 權杖使用者證實知悉的密碼編譯金鑰內容產生關聯。 這項證明能滿足信賴憑證者，證實該 SAML 權杖確實簽發至該使用者。 例如，在典型的案例中：  
  
1.  用戶端向安全性權杖服務要求 SAML 權杖，藉由使用 Windows 認證，驗證至該安全性權杖服務。  
  
2.  安全性權杖服務簽發 SAML 權杖至用戶端。 SAML 權杖是以與安全性權杖服務相關的憑證進行簽署，並且包含針對目標服務加密的證明金鑰。  
  
3.  用戶端也會收到一份*證明金鑰*。 用戶端接著會向應用程式服務的 SAML 權杖 (*信賴憑證者的合作對象*)，並以該證明金鑰簽署訊息。  
  
4.  SAML 權杖上的簽章會告訴信賴憑證者，這是由安全性權杖服務所簽發的權杖。 使用證明金鑰所建立的訊息簽章會告訴信賴憑證者，該權杖曾簽發至用戶端。  
  
## <a name="from-claims-to-samlattributes"></a>從宣告到 SamlAttributes  
 在 WCF 中，在 SAML 權杖中的陳述式會模型化為<xref:System.IdentityModel.Tokens.SamlAttribute>可以直接從填入的物件<xref:System.IdentityModel.Claims.Claim>所提供的物件<xref:System.IdentityModel.Claims.Claim>物件具有<xref:System.IdentityModel.Claims.Claim.Right%2A>屬性<xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>而<xref:System.IdentityModel.Claims.Claim.Resource%2A>屬性屬於型別<xref:System.String>。 例如:   
  
 [!code-csharp[c_CreateSTS#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#8)]
 [!code-vb[c_CreateSTS#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#8)]  
  
> [!NOTE]
>  當 SAML 權杖在訊息中序列化，不論是當這些權杖是安全性權杖服務所核發，或是當這些權杖由用戶端視為驗證的一部分提供至服務，訊息大小配額上限必須大到足以容納 SAML 權杖及其他訊息部分。 正常情況下，預設訊息大小配額應足夠。 然而，若 SAML 權杖因為包含數百個宣告而變很大時，您可能需要增加配額以容納序列化的權杖。 如需詳細資訊，請參閱 <<c0> [ 資料的安全性考量](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)。  
  
## <a name="from-samlattributes-to-claims"></a>從 SamlAttributes 到宣告  
 當 SAML 權杖在訊息內接收時，SAML 權杖內的各種陳述式會轉變成 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> 物件，置於 <xref:System.IdentityModel.Policy.AuthorizationContext>之內。 來自每個 SAML 陳述式的宣告均由 <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> 的 <xref:System.IdentityModel.Policy.AuthorizationContext> 屬性傳回，並且可進行檢查以決定是否驗證並授權使用者。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IdentityModel.Policy.AuthorizationContext>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- <xref:System.IdentityModel.Claims.ClaimSet>
- [同盟](../../../../docs/framework/wcf/feature-details/federation.md)
- [HOW TO：建立同盟用戶端](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [HOW TO：設定同盟服務的認證](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [使用身分識別模型來管理宣告與授權](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [宣告與權杖](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
- [宣告建立與資源值](../../../../docs/framework/wcf/feature-details/claim-creation-and-resource-values.md)
- [HOW TO：建立自訂宣告](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
