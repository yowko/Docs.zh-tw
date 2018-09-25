---
title: 如何： 建立自訂安全性權杖驗證器
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
ms.assetid: 10e245f7-d31e-42e7-82a2-d5780325d372
author: BrucePerlerMS
ms.openlocfilehash: cbedab4064173186251defead8394735de033cf7
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47111798"
---
# <a name="how-to-create-a-custom-security-token-authenticator"></a>如何： 建立自訂安全性權杖驗證器
本主題會示範如何建立自訂安全性權杖驗證器，以及如何將其與自訂的安全性權杖管理員整合。 安全性權杖驗證器會驗證傳入訊息所提供之安全性權杖的內容。 如果驗證成功，驗證器便會傳回在進行評估時會傳回一組宣告之 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> 執行個體的集合。  
  
 若要使用的自訂安全性權杖驗證器的 Windows Communication Foundation (WCF) 中，您必須先建立自訂認證和安全性權杖管理員實作。 如需建立自訂認證和安全性權杖管理員的詳細資訊，請參閱 <<c0> [ 逐步解說： 建立自訂用戶端和服務認證](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)。 如需有關認證、 安全性權杖管理員，以及提供者和驗證器類別的詳細資訊，請參閱 <<c0> [ 安全性架構](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)。  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-create-a-custom-security-token-authenticator"></a>建立自訂安全性權杖驗證器  
  
1.  定義衍生自 <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> 類別的新類別。  
  
2.  覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateTokenCore%2A> 方法。 該方法會根據自訂驗證器是否能夠驗證傳入的權杖類型，傳回 `true` 或 `false`。  
  
3.  覆寫 <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.ValidateTokenCore%2A> 方法。 這個方法需要適當地驗證權杖內容。 如果權杖通過驗證步驟，此方法就會傳回 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> 執行個體的集合。 下列範例會使用將在下一個程序中建立的自訂授權原則實作。  
  
     [!code-csharp[C_CustomTokenAuthenticator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#1)]
     [!code-vb[C_CustomTokenAuthenticator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#1)]  
  
 上述程式碼會透過 <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator.CanValidateToken%28System.IdentityModel.Tokens.SecurityToken%29> 方法傳回授權原則的集合。 WCF 不會提供這個介面的公用實作。 下列程序會示範如何根據您的需求來完成這項工作。  
  
#### <a name="to-create-a-custom-authorization-policy"></a>建立自訂授權原則  
  
1.  定義實作 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> 介面的新類別。  
  
2.  實作 <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> 唯讀屬性。 使用類別建構函式 (Constructor) 來產生全域唯一識別項 (GUID)，並在每次要求此屬性的值時將其傳回，就是實作此原則的一種方式  
  
3.  實作 <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A> 唯讀屬性。 這個屬性需要傳回從權杖取得之宣告集的簽發者。 這個簽發者應該會對應至權杖的簽發者，或是負責驗證該權杖內容的授權單位。 下列範例會使用從上述程序所建立自訂安全性權杖驗證器傳遞到這個類別的簽發者宣告。 自訂安全性權杖驗證器會使用系統提供的宣告集 (由 <xref:System.IdentityModel.Claims.ClaimSet.System%2A> 屬性傳回) 來表示使用者名稱權杖的簽發者。  
  
4.  實作 <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A> 方法。 這個方法會用以傳入安全性權杖內容為基礎的宣告，填入 (Populate) <xref:System.IdentityModel.Policy.EvaluationContext> 類別的執行個體 (當做引數傳入)。 此方法會在完成評估時傳回 `true`。 當實作依賴對評估內容提供其他資訊之授權原則的存在，而需要的資訊尚未存在於評估內容時，這個方法便會傳回 `false`。 在此情況下，WCF 會在評估所有其他內送訊息產生，如果至少一個授權原則，這些修改評估內容的授權原則之後，再次呼叫方法。  
  
     [!code-csharp[c_CustomTokenAuthenticator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#3)]
     [!code-vb[c_CustomTokenAuthenticator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#3)]  

 [逐步解說： 建立自訂用戶端和服務認證](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)說明如何建立自訂認證和自訂安全性權杖管理員。 為了使用在此建立的自訂安全性權杖驗證器，安全性權杖管理員的實作會經過修改，以便從 <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> 方法傳回自訂驗證器。 若有傳入適當的安全性權杖需求，此方法便會傳回驗證器。  
  
#### <a name="to-integrate-a-custom-security-token-authenticator-with-a-custom-security-token-manager"></a>將自訂安全性權杖驗證器與自訂安全性權杖管理員整合  
  
1.  覆寫自訂安全性權杖管理員實作中的 <xref:System.IdentityModel.Selectors.SecurityTokenManager.CreateSecurityTokenAuthenticator%2A> 方法。  
  
2.  將邏輯新增到方法中，讓方法能夠根據 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> 參數傳回自訂安全性權杖驗證器。 如果在權杖需求中權杖類型為使用者名稱 (由 <xref:System.IdentityModel.Tokens.SecurityTokenTypes.UserName%2A> 屬性表示)，而且安全性權杖驗證器被要求的訊息方向為輸入時 (由 <xref:System.ServiceModel.Description.MessageDirection.Input> 欄位表示)，下列範例就會傳回自訂安全性權杖驗證器。  
  
     [!code-csharp[c_CustomTokenAuthenticator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customtokenauthenticator/cs/source.cs#2)]
     [!code-vb[c_CustomTokenAuthenticator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customtokenauthenticator/vb/source.vb#2)]  
 
## <a name="see-also"></a>另請參閱  
 <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SecurityTokenRequirement>  
 <xref:System.IdentityModel.Selectors.SecurityTokenManager>  
 <xref:System.IdentityModel.Tokens.UserNameSecurityToken>  
 [逐步解說：建立自訂用戶端和服務認證](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 [如何：建立自訂安全性權杖提供者](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 [安全性架構](https://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
