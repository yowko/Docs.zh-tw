---
title: "SAML 權杖與宣告 | Microsoft Docs"
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
  - "聯合"
  - "發行的權杖"
  - "SAML 權杖"
  - "WCF, 聯合"
ms.assetid: 930b6e34-9eab-4e95-826c-4e06659bb977
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# SAML 權杖與宣告
安全性判斷提示標記語言 \(SAML\)「*權杖*」\(token\) 為宣告的 XML 表示。根據預設，聯合安全性案例使用的 SAML 權杖 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 為「*發行權杖*」\(issued token\)。  
  
 SAML 權杖包含一實體對另一實體所做出之宣告集合的陳述式。例如，在聯合安全性案例中，陳述式是由系統中關於使用者的安全性權杖服務所表示。安全性權杖服務會簽署 SAML 權杖，以表示權杖中所含陳述式的真實性。除此之外，SAML 權杖會與 SAML 權杖使用者證實知悉的密碼編譯金鑰內容產生關聯。這項證明能滿足信賴憑證者，證實該 SAML 權杖確實簽發至該使用者。例如，在典型的案例中：  
  
1.  用戶端向安全性權杖服務要求 SAML 權杖，藉由使用 Windows 認證，驗證至該安全性權杖服務。  
  
2.  安全性權杖服務簽發 SAML 權杖至用戶端。SAML 權杖是以與安全性權杖服務相關的憑證進行簽署，並且包含針對目標服務加密的證明金鑰。  
  
3.  用戶端也會收到一份「*證明金鑰*」\(proof key\)。然後，用戶端會對應用程式服務 \(「*信賴憑證者*」\(relying party\) \) 提出 SAML 權杖，並以該證明金鑰簽署訊息。  
  
4.  SAML 權杖上的簽章會告訴信賴憑證者，這是由安全性權杖服務所簽發的權杖。使用證明金鑰所建立的訊息簽章會告訴信賴憑證者，該權杖曾簽發至用戶端。  
  
## 從宣告到 SamlAttributes  
 在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中，SAML 權杖中的陳述式會以 <xref:System.IdentityModel.Tokens.SamlAttribute> 物件做為模型，可從 <xref:System.IdentityModel.Claims.Claim> 物件直接填入，前提是 <xref:System.IdentityModel.Claims.Claim> 物件擁有 <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> 的 <xref:System.IdentityModel.Claims.Claim.Right%2A> 屬性，且 <xref:System.IdentityModel.Claims.Claim.Resource%2A> 屬性為 <xref:System.String> 型別。例如：  
  
 [!code-csharp[c_CreateSTS#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#8)]
 [!code-vb[c_CreateSTS#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#8)]  
  
> [!NOTE]
>  當 SAML 權杖在訊息中序列化，不論是當這些權杖是安全性權杖服務所核發，或是當這些權杖由用戶端視為驗證的一部分提供至服務，訊息大小配額上限必須大到足以容納 SAML 權杖及其他訊息部分。正常情況下，預設訊息大小配額應足夠。然而，若 SAML 權杖因為包含數百個宣告而變很大時，您可能需要增加配額以容納序列化的權杖。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][資料的安全性考量](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
## 從 SamlAttributes 到宣告  
 當 SAML 權杖在訊息內接收時，SAML 權杖內的各種陳述式會轉變成 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> 物件，置於 <xref:System.IdentityModel.Policy.AuthorizationContext> 之內。來自每個 SAML 陳述式的宣告均由 <xref:System.IdentityModel.Policy.AuthorizationContext> 的 <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> 屬性傳回，並且可進行檢查以決定是否驗證並授權使用者。  
  
## 請參閱  
 <xref:System.IdentityModel.Policy.AuthorizationContext>   
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>   
 <xref:System.IdentityModel.Claims.ClaimSet>   
 [聯合](../../../../docs/framework/wcf/feature-details/federation.md)   
 [HOW TO：建立聯合用戶端](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)   
 [HOW TO：設定聯合服務的認證](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)   
 [使用身分識別模型來管理宣告與授權](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)   
 [宣告與權杖](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)   
 [宣告建立與資源值](../../../../docs/framework/wcf/feature-details/claim-creation-and-resource-values.md)   
 [HOW TO：建立自訂宣告](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)