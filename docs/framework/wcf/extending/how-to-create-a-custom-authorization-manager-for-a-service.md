---
title: "HOW TO：為服務建立自訂授權管理員"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Communication Foundation, extending
- OperationRequirement class
ms.assetid: 6214afde-44c1-4bf5-ba07-5ad6493620ea
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7b8d934509940bf712ccb7463156c88540027407
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-custom-authorization-manager-for-a-service"></a>HOW TO：為服務建立自訂授權管理員
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中的「身分識別模型」基礎結構支援可延伸的宣告授權模型。 從語彙基元擷取的宣告可以選擇性地由自訂授權原則進行處理並放入 <xref:System.IdentityModel.Policy.AuthorizationContext>。 授權管理員會檢查 <xref:System.IdentityModel.Policy.AuthorizationContext> 中的宣告來做出授權決策。  
  
 根據預設，<xref:System.ServiceModel.ServiceAuthorizationManager> 類別會做出授權決策，不過，您也可以建立自訂的授權管理員來覆寫這些決策。 若要建立自訂的授權管理員，請建立衍生自 <xref:System.ServiceModel.ServiceAuthorizationManager> 的類別，然後實作 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> 方法。 授權決策會在 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> 方法中進行，並在授與存取權時傳回 `true`，在拒絕存取權時傳回 `false`。  
  
 如果授權決策取決於訊息本文的內容，則使用 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> 方法。  
  
 基於效能考量，如果可以，您應該重新設計應用程式，讓授權決策不需要存取訊息本文。  
  
 您也可以透過程式碼或組態，為服務註冊自訂授權管理員。  
  
### <a name="to-create-a-custom-authorization-manager"></a>若要建立自訂授權管理員  
  
1.  從 <xref:System.ServiceModel.ServiceAuthorizationManager> 類別衍生類別。  
  
     [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
     [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]  
  
2.  覆寫 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> 方法。  
  
     使用傳遞至 <xref:System.ServiceModel.OperationContext> 方法的 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> 來做出授權決策。  
  
     下列程式碼範例使用 <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> 方法來找出自訂宣告 `http://www.contoso.com/claims/allowedoperation`，以便做出授權決策。  
  
     [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
     [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]  
  
### <a name="to-register-a-custom-authorization-manager-using-code"></a>若要使用程式碼來註冊自訂授權管理員  
  
1.  建立自訂授權管理員的執行個體，然後將它指派給 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> 屬性。  
  
     <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> 可以透過使用 <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> 屬性來存取。  
  
     下列程式碼範例會註冊 `MyServiceAuthorizationManager` 自訂授權管理員。  
  
     [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
     [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]  
  
### <a name="to-register-a-custom-authorization-manager-using-configuration"></a>若要使用組態來註冊自訂授權管理員  
  
1.  開啟服務的組態檔。  
  
2.  新增[ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)至[\<行為 >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)。  
  
     若要[ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)，新增`serviceAuthorizationManagerType`屬性，並將其值設定為代表自訂授權管理員的型別。  
  
3.  新增繫結，以便保護用戶端與服務之間的通訊安全。  
  
     選定用在此通訊上的繫結會決定新增至 <xref:System.IdentityModel.Policy.AuthorizationContext> 的宣告，而自訂授權管理員會使用此宣告來做出授權決策。 如需有關系統提供繫結的詳細資訊，請參閱[之繫結](../../../../docs/framework/wcf/system-provided-bindings.md)。  
  
4.  關聯的行為至服務端點，藉由新增[\<服務 >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md)項目和設定的值`behaviorConfiguration`屬性的名稱屬性的值[\<行為>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)項目。  
  
     如需有關如何設定服務端點的詳細資訊，請參閱[How to： 在組態中建立服務端點](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)。  
  
     下列程式碼範例會註冊自訂授權管理員 `Samples.MyServiceAuthorizationManager`。  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service   
              name="Microsoft.ServiceModel.Samples.CalculatorService"  
              behaviorConfiguration="CalculatorServiceBehavior">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
              </baseAddresses>  
            </host>  
            <endpoint address=""  
                      binding="wsHttpBinding_Calculator"  
                      contract="Microsoft.ServiceModel.Samples.ICalculator" />  
          </service>  
        </services>  
        <bindings>  
          <WSHttpBinding>  
           <binding name = "wsHttpBinding_Calculator">  
             <security mode="Message">  
               <message clientCredentialType="Windows"/>  
             </security>  
            </binding>  
          </WSHttpBinding>  
    </bindings>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="CalculatorServiceBehavior">  
              <serviceAuthorization serviceAuthorizationManagerType="Samples.MyServiceAuthorizationManager,MyAssembly" />  
             </behavior>  
         </serviceBehaviors>  
       </behaviors>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
    > [!WARNING]
    >  請注意，當您指定 serviceAuthorizationManagerType 時，字串必須包含完整的型別名稱。 逗號和已定義型別之組件的名稱。 如果您省略組件名稱，WCF 會嘗試從 System.ServiceModel.dll 載入型別。  
  
## <a name="example"></a>範例  
 下列程式碼範例示範包含覆寫 <xref:System.ServiceModel.ServiceAuthorizationManager> 方法的基本 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> 類別實作。 此範例程式碼會檢查自訂宣告的 <xref:System.IdentityModel.Policy.AuthorizationContext>，並在該自訂宣告符合來自 `true` 的動作值時傳回 <xref:System.ServiceModel.OperationContext>。 如需更完整實作的<xref:System.ServiceModel.ServiceAuthorizationManager>類別，請參閱[授權原則](../../../../docs/framework/wcf/samples/authorization-policy.md)。  
  
 [!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
 [!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [授權原則](../../../../docs/framework/wcf/samples/authorization-policy.md)  
 [授權原則](../../../../docs/framework/wcf/samples/authorization-policy.md)
