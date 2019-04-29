---
title: HOW TO：建立自訂用戶端身分識別驗證器
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f2d34e43-fa8b-46d2-91cf-d2960e13e16b
ms.openlocfilehash: d8529929870b14611c136221f1eefe3eb4ba3d42
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61767256"
---
# <a name="how-to-create-a-custom-client-identity-verifier"></a>HOW TO：建立自訂用戶端身分識別驗證器
*識別*功能的 Windows Communication Foundation (WCF) 可讓用戶端預先指定預期的身分識別的服務。 每當伺服器向用戶端驗證自身時，就會比對預期身分識別來檢查身分識別  (如需身分識別及其運作方式的說明，請參閱 <<c0> [ 服務身分識別和驗證](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。)  
  
 必要時，可使用自訂身分識別驗證器來自訂驗證。 例如，您可以執行其他服務身分識別驗證檢查。 在這個範例中，自訂身分識別驗證器會檢查從伺服器所傳回的 X.509 憑證中的其他宣告。 範例應用程式，請參閱[服務身分識別範例](../../../../docs/framework/wcf/samples/service-identity-sample.md)。  
  
### <a name="to-extend-the-endpointidentity-class"></a>若要擴充 EndpointIdentity 類別  
  
1. 定義衍生自 <xref:System.ServiceModel.EndpointIdentity> 類別的新類別。 這個範例會將擴充功能命名為 `OrgEndpointIdentity`。  
  
2. 加入私用成員與擴充 <xref:System.ServiceModel.Security.IdentityVerifier> 類別將會使用的屬性，對服務所傳回安全性權杖中的宣告執行身分識別檢查。 這個範例會定義一個屬性：`OrganizationClaim` 屬性。  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
     [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
### <a name="to-extend-the-identityverifier-class"></a>若要擴充 IdentityVerifier 類別  
  
1. 定義衍生自 <xref:System.ServiceModel.Security.IdentityVerifier> 的新類別。 這個範例會將擴充功能命名為 `CustomIdentityVerifier`。  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#7)]
     [!code-vb[c_HowToSetCustomClientIdentity#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#7)]  
  
2. 覆寫 <xref:System.ServiceModel.Security.IdentityVerifier.CheckAccess%2A> 方法。 這個方法會判斷身分識別檢查是成功還是失敗。  
  
3. `CheckAccess` 方法有兩個參數。 第一個是 <xref:System.ServiceModel.EndpointIdentity> 類別的執行個體。 第二個是 <xref:System.IdentityModel.Policy.AuthorizationContext> 類別的執行個體。  
  
     在方法實作中，檢查 <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> 類別的 <xref:System.IdentityModel.Policy.AuthorizationContext> 屬性傳回的宣告集合，並執行必要的驗證檢查。 這個範例會先尋找 "Distinguished Name" 型別的任何宣告，然後比較名稱與 <xref:System.ServiceModel.EndpointIdentity> 的擴充功能 (`OrgEndpointIdentity`)。  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#1)]
     [!code-vb[c_HowToSetCustomClientIdentity#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#1)]  
  
### <a name="to-implement-the-trygetidentity-method"></a>若要實作 TryGetIdentity 方法  
  
1. 實作 <xref:System.ServiceModel.Security.IdentityVerifier.TryGetIdentity%2A> 方法，可判斷 <xref:System.ServiceModel.EndpointIdentity> 類別的執行個體是否可由用戶端傳回。 WCF 基礎結構呼叫的實作`TryGetIdentity`方法第一次，以從訊息擷取服務的身分識別。 接著，基礎結構會使用所傳回的 `CheckAccess` 和 `EndpointIdentity` 來呼叫 <xref:System.IdentityModel.Policy.AuthorizationContext> 實作。  
  
2. 在 `TryGetIdentity` 方法中，放入下列程式碼：  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#2)]
     [!code-vb[c_HowToSetCustomClientIdentity#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#2)]  
  
### <a name="to-implement-a-custom-binding-and-set-the-custom-identityverifier"></a>若要實作自訂繫結及設定自訂 IdentityVerifier  
  
1. 建立會傳回 <xref:System.ServiceModel.Channels.Binding> 物件的方法。 這個範例會先建立 <xref:System.ServiceModel.WSHttpBinding> 類別的執行個體，並將其安全性模式設定為 <xref:System.ServiceModel.SecurityMode.Message> 及其 <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> 設定為 <xref:System.ServiceModel.MessageCredentialType.None>。  
  
2. 使用 <xref:System.ServiceModel.Channels.BindingElementCollection> 方法來建立 <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A>。  
  
3. 從集合中傳回 <xref:System.ServiceModel.Channels.SecurityBindingElement> 並將其轉換為 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 變數。  
  
4. 將 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings.IdentityVerifier%2A> 類別的 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> 屬性設定為先前新建立的 `CustomIdentityVerifier` 類別執行個體。  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#3)]
     [!code-vb[c_HowToSetCustomClientIdentity#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#3)]  
  
5. 所傳回的自訂繫結會用來建立用戶端和類別的執行個體。 然後，用戶端就可以對服務執行自訂身分識別驗證檢查，如下列程式碼所示。  
  
     [!code-csharp[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#4)]
     [!code-vb[c_HowToSetCustomClientIdentity#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#4)]  
  
## <a name="example"></a>範例  
 下列範例會示範 <xref:System.ServiceModel.Security.IdentityVerifier> 類別的完整實作。  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#5)]
 [!code-vb[c_HowToSetCustomClientIdentity#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#5)]  
  
## <a name="example"></a>範例  
 下列範例會示範 <xref:System.ServiceModel.EndpointIdentity> 類別的完整實作。  
  
 [!code-csharp[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosetcustomclientidentity/cs/source.cs#6)]
 [!code-vb[c_HowToSetCustomClientIdentity#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosetcustomclientidentity/vb/source.vb#6)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- <xref:System.ServiceModel.EndpointIdentity>
- <xref:System.ServiceModel.Security.IdentityVerifier>
- [服務身分識別範例](../../../../docs/framework/wcf/samples/service-identity-sample.md)
- [授權原則](../../../../docs/framework/wcf/samples/authorization-policy.md)
