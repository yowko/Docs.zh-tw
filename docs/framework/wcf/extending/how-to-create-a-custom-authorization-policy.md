---
title: HOW TO：建立自訂授權原則
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 05b0549b-882d-4660-b6f0-5678543e5475
ms.openlocfilehash: 0bacf874e09aca82b2f2685a146612cdef0673db
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804231"
---
# <a name="how-to-create-a-custom-authorization-policy"></a>HOW TO：建立自訂授權原則
識別模型基礎結構中 Windows Communication Foundation (WCF) 支援宣告型授權模型。 宣告會從權杖擷取出來 (可以選擇性地由自訂授權原則進行處理)，接著會放置到可隨後進行檢查以做出授權決策的 <xref:System.IdentityModel.Policy.AuthorizationContext>。 自訂原則可用於將來自傳入權杖的宣告轉換為應用程式所需要的宣告。 如此一來，應用程式層都可以 WCF 支援的不同權杖類型所服務之不同宣告的詳細資料達成隔離。 本主題會說明如何實作自訂授權原則，以及如何將該原則新增至服務所使用的原則集合。  
  
### <a name="to-implement-a-custom-authorization-policy"></a>實作自訂授權原則  
  
1.  定義衍生自 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> 的新類別。  
  
2.  透過在類別的建構函式 (Constructor) 中產生唯一字串，並在每次存取該屬性時傳回該字串，便可實作唯讀的 <xref:System.IdentityModel.Policy.IAuthorizationComponent.Id%2A> 屬性。  
  
3.  透過傳回表示原則簽發者的 <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Issuer%2A>，便可實作唯讀的 <xref:System.IdentityModel.Claims.ClaimSet> 屬性。 這可能是表示應用程式的 `ClaimSet` 或內建的 `ClaimSet` (例如，由靜態 `ClaimSet` 屬性傳回的 <xref:System.IdentityModel.Claims.ClaimSet.System%2A>)。  
  
4.  實作 <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> 方法，如下列程序所述。  
  
### <a name="to-implement-the-evaluate-method"></a>實作 Evaluate 方法  
  
1.  有兩個參數會傳遞至這個方法：即 <xref:System.IdentityModel.Policy.EvaluationContext> 類別的執行個體，以及某個物件參考。  
  
2.  如果自訂授權原則新增<xref:System.IdentityModel.Claims.ClaimSet>執行個體，而不考慮目前的內容<xref:System.IdentityModel.Policy.EvaluationContext>，然後新增每個`ClaimSet`藉由呼叫<xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29>方法，並傳回`true`從<xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%2A>方法。 傳回 `true`，就是向授權基礎結構表示該授權原則已執行其工作，因此不需要重新呼叫。  
  
3.  如果自訂授權原則只會在 `EvaluationContext` 中已出現某些宣告時新增宣告集，則請檢查 `ClaimSet` 屬性所傳回的 <xref:System.IdentityModel.Policy.EvaluationContext.ClaimSets%2A> 執行個體來查看這些宣告。 如果這些宣告有存在，則呼叫 <xref:System.IdentityModel.Policy.EvaluationContext.AddClaimSet%28System.IdentityModel.Policy.IAuthorizationPolicy%2CSystem.IdentityModel.Claims.ClaimSet%29> 方法來新增新的宣告集，如果沒有要新增其他宣告集，則傳回 `true`，向授權基礎結構表示授權原則已完成其工作。 如果沒有存在這些宣告，則傳回 `false`，表示如果有其他授權原則要新增更多宣告集至 `EvaluationContext`，就應該重新呼叫授權原則。  
  
4.  在更複雜的處理案例中，<xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> 方法的第二個參數可用來儲存狀態變數，也就是授權基礎結構後來要進行特定評估而呼叫 <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> 方法時所傳回的變數。  
  
### <a name="to-specify-a-custom-authorization-policy-through-configuration"></a>透過組態指定自訂授權原則  
  
1.  在 `policyType` 項目之 `add` 項目的 `authorizationPolicies` 項目的 `serviceAuthorization` 屬性中，指定自訂授權原則的類型。  
  
    ```xml  
    <configuration>  
     <system.serviceModel>  
      <behaviors>  
        <serviceAuthorization serviceAuthorizationManagerType=  
                  "Samples.MyServiceAuthorizationManager" >  
          <authorizationPolicies>         
            <add policyType="Samples.MyAuthorizationPolicy"  
          </authorizationPolicies>  
        </serviceAuthorization>  
      </behaviors>  
     </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="to-specify-a-custom-authorization-policy-through-code"></a>透過程式碼指定自訂授權原則  
  
1.  建立 <xref:System.Collections.Generic.List%601> 的 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>。  
  
2.  建立自訂授權原則的執行個體。  
  
3.  新增授權原則執行個體至清單中。  
  
4.  針對每個自訂授權原則重複步驟 2 和 3。  
  
5.  指派唯讀的清單版本至 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ExternalAuthorizationPolicies%2A> 屬性。  
  
     [!code-csharp[c_CustomAuthPol#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#8)]
     [!code-vb[c_CustomAuthPol#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#8)]  
  
## <a name="example"></a>範例  
 下列範例會示範完整的 <xref:System.IdentityModel.Policy.IAuthorizationPolicy> 實作。  
  
 [!code-csharp[c_CustomAuthPol#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthpol/cs/c_customauthpol.cs#5)]
 [!code-vb[c_CustomAuthPol#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthpol/vb/source.vb#5)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [如何：比較宣告](../../../../docs/framework/wcf/extending/how-to-compare-claims.md)  
 [如何：為服務建立自訂授權管理員](../../../../docs/framework/wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md)  
 [授權原則](../../../../docs/framework/wcf/samples/authorization-policy.md)
