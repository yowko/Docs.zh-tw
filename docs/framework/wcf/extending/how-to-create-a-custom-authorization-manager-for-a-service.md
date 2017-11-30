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
# <a name="how-to-create-a-custom-authorization-manager-for-a-service"></a><span data-ttu-id="cad10-102">HOW TO：為服務建立自訂授權管理員</span><span class="sxs-lookup"><span data-stu-id="cad10-102">How to: Create a Custom Authorization Manager for a Service</span></span>
<span data-ttu-id="cad10-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中的「身分識別模型」基礎結構支援可延伸的宣告授權模型。</span><span class="sxs-lookup"><span data-stu-id="cad10-103">The Identity Model infrastructure in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] supports an extensible claims-based authorization model.</span></span> <span data-ttu-id="cad10-104">從語彙基元擷取的宣告可以選擇性地由自訂授權原則進行處理並放入 <xref:System.IdentityModel.Policy.AuthorizationContext>。</span><span class="sxs-lookup"><span data-stu-id="cad10-104">Claims are extracted from tokens and optionally processed by custom authorization policies and then placed into an <xref:System.IdentityModel.Policy.AuthorizationContext>.</span></span> <span data-ttu-id="cad10-105">授權管理員會檢查 <xref:System.IdentityModel.Policy.AuthorizationContext> 中的宣告來做出授權決策。</span><span class="sxs-lookup"><span data-stu-id="cad10-105">An authorization manager examines the claims in the <xref:System.IdentityModel.Policy.AuthorizationContext> to make authorization decisions.</span></span>  
  
 <span data-ttu-id="cad10-106">根據預設，<xref:System.ServiceModel.ServiceAuthorizationManager> 類別會做出授權決策，不過，您也可以建立自訂的授權管理員來覆寫這些決策。</span><span class="sxs-lookup"><span data-stu-id="cad10-106">By default, authorization decisions are made by the <xref:System.ServiceModel.ServiceAuthorizationManager> class; however these decisions can be overridden by creating a custom authorization manager.</span></span> <span data-ttu-id="cad10-107">若要建立自訂的授權管理員，請建立衍生自 <xref:System.ServiceModel.ServiceAuthorizationManager> 的類別，然後實作 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="cad10-107">To create a custom authorization manager, create a class that derives from <xref:System.ServiceModel.ServiceAuthorizationManager> and implement <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="cad10-108">授權決策會在 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> 方法中進行，並在授與存取權時傳回 `true`，在拒絕存取權時傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="cad10-108">Authorization decisions are made in the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method, which returns `true` when access is granted and `false` when access is denied.</span></span>  
  
 <span data-ttu-id="cad10-109">如果授權決策取決於訊息本文的內容，則使用 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="cad10-109">If the authorization decision depends on the contents of the message body, use the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method.</span></span>  
  
 <span data-ttu-id="cad10-110">基於效能考量，如果可以，您應該重新設計應用程式，讓授權決策不需要存取訊息本文。</span><span class="sxs-lookup"><span data-stu-id="cad10-110">Because of performance issues, if possible you should redesign your application so that the authorization decision does not require access to the message body.</span></span>  
  
 <span data-ttu-id="cad10-111">您也可以透過程式碼或組態，為服務註冊自訂授權管理員。</span><span class="sxs-lookup"><span data-stu-id="cad10-111">Registration of the custom authorization manager for a service can be done in code or configuration.</span></span>  
  
### <a name="to-create-a-custom-authorization-manager"></a><span data-ttu-id="cad10-112">若要建立自訂授權管理員</span><span class="sxs-lookup"><span data-stu-id="cad10-112">To create a custom authorization manager</span></span>  
  
1.  <span data-ttu-id="cad10-113">從 <xref:System.ServiceModel.ServiceAuthorizationManager> 類別衍生類別。</span><span class="sxs-lookup"><span data-stu-id="cad10-113">Derive a class from the <xref:System.ServiceModel.ServiceAuthorizationManager> class.</span></span>  
  
     [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
     [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]  
  
2.  <span data-ttu-id="cad10-114">覆寫 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> 方法。</span><span class="sxs-lookup"><span data-stu-id="cad10-114">Override the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> method.</span></span>  
  
     <span data-ttu-id="cad10-115">使用傳遞至 <xref:System.ServiceModel.OperationContext> 方法的 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> 來做出授權決策。</span><span class="sxs-lookup"><span data-stu-id="cad10-115">Use the <xref:System.ServiceModel.OperationContext> that is passed to the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> method to make authorization decisions.</span></span>  
  
     <span data-ttu-id="cad10-116">下列程式碼範例使用 <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> 方法來找出自訂宣告 `http://www.contoso.com/claims/allowedoperation`，以便做出授權決策。</span><span class="sxs-lookup"><span data-stu-id="cad10-116">The following code example uses the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> method to find the custom claim `http://www.contoso.com/claims/allowedoperation` to make an authorization decision.</span></span>  
  
     [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
     [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]  
  
### <a name="to-register-a-custom-authorization-manager-using-code"></a><span data-ttu-id="cad10-117">若要使用程式碼來註冊自訂授權管理員</span><span class="sxs-lookup"><span data-stu-id="cad10-117">To register a custom authorization manager using code</span></span>  
  
1.  <span data-ttu-id="cad10-118">建立自訂授權管理員的執行個體，然後將它指派給 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="cad10-118">Create an instance of the custom authorization manager and assign it to the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> property.</span></span>  
  
     <span data-ttu-id="cad10-119"><xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> 可以透過使用 <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> 屬性來存取。</span><span class="sxs-lookup"><span data-stu-id="cad10-119">The <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> can be accessed using <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> property.</span></span>  
  
     <span data-ttu-id="cad10-120">下列程式碼範例會註冊 `MyServiceAuthorizationManager` 自訂授權管理員。</span><span class="sxs-lookup"><span data-stu-id="cad10-120">The following code example registers the `MyServiceAuthorizationManager` custom authorization manager.</span></span>  
  
     [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
     [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]  
  
### <a name="to-register-a-custom-authorization-manager-using-configuration"></a><span data-ttu-id="cad10-121">若要使用組態來註冊自訂授權管理員</span><span class="sxs-lookup"><span data-stu-id="cad10-121">To register a custom authorization manager using configuration</span></span>  
  
1.  <span data-ttu-id="cad10-122">開啟服務的組態檔。</span><span class="sxs-lookup"><span data-stu-id="cad10-122">Open the configuration file for the service.</span></span>  
  
2.  <span data-ttu-id="cad10-123">新增[ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)至[\<行為 >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)。</span><span class="sxs-lookup"><span data-stu-id="cad10-123">Add a [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md).</span></span>  
  
     <span data-ttu-id="cad10-124">若要[ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)，新增`serviceAuthorizationManagerType`屬性，並將其值設定為代表自訂授權管理員的型別。</span><span class="sxs-lookup"><span data-stu-id="cad10-124">To the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md), add a `serviceAuthorizationManagerType` attribute and set its value to the type that represents the custom authorization manager.</span></span>  
  
3.  <span data-ttu-id="cad10-125">新增繫結，以便保護用戶端與服務之間的通訊安全。</span><span class="sxs-lookup"><span data-stu-id="cad10-125">Add a binding that secures the communication between the client and service.</span></span>  
  
     <span data-ttu-id="cad10-126">選定用在此通訊上的繫結會決定新增至 <xref:System.IdentityModel.Policy.AuthorizationContext> 的宣告，而自訂授權管理員會使用此宣告來做出授權決策。</span><span class="sxs-lookup"><span data-stu-id="cad10-126">The binding that is chosen for this communication determines the claims that are added to the <xref:System.IdentityModel.Policy.AuthorizationContext>, which the custom authorization manager uses to make authorization decisions.</span></span> <span data-ttu-id="cad10-127">如需有關系統提供繫結的詳細資訊，請參閱[之繫結](../../../../docs/framework/wcf/system-provided-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="cad10-127">For more details about the system-provided bindings, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
4.  <span data-ttu-id="cad10-128">關聯的行為至服務端點，藉由新增[\<服務 >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md)項目和設定的值`behaviorConfiguration`屬性的名稱屬性的值[\<行為>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)項目。</span><span class="sxs-lookup"><span data-stu-id="cad10-128">Associate the behavior to a service endpoint, by adding a [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) element and set the value of the `behaviorConfiguration` attribute to the value of the name attribute for the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>  
  
     <span data-ttu-id="cad10-129">如需有關如何設定服務端點的詳細資訊，請參閱[How to： 在組態中建立服務端點](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="cad10-129">For more information about configuring a service endpoint, see [How to: Create a Service Endpoint in Configuration](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md).</span></span>  
  
     <span data-ttu-id="cad10-130">下列程式碼範例會註冊自訂授權管理員 `Samples.MyServiceAuthorizationManager`。</span><span class="sxs-lookup"><span data-stu-id="cad10-130">The following code example registers the custom authorization manager `Samples.MyServiceAuthorizationManager`.</span></span>  
  
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
    >  <span data-ttu-id="cad10-131">請注意，當您指定 serviceAuthorizationManagerType 時，字串必須包含完整的型別名稱。</span><span class="sxs-lookup"><span data-stu-id="cad10-131">Note that when you specify the serviceAuthorizationManagerType, the string must contain the fully qualified type name.</span></span> <span data-ttu-id="cad10-132">逗號和已定義型別之組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="cad10-132">a comma, and the name of the assembly in which the type is defined.</span></span> <span data-ttu-id="cad10-133">如果您省略組件名稱，WCF 會嘗試從 System.ServiceModel.dll 載入型別。</span><span class="sxs-lookup"><span data-stu-id="cad10-133">If you leave out the assembly name, WCF will attempt to load the type from System.ServiceModel.dll.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cad10-134">範例</span><span class="sxs-lookup"><span data-stu-id="cad10-134">Example</span></span>  
 <span data-ttu-id="cad10-135">下列程式碼範例示範包含覆寫 <xref:System.ServiceModel.ServiceAuthorizationManager> 方法的基本 <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> 類別實作。</span><span class="sxs-lookup"><span data-stu-id="cad10-135">The following code example demonstrates a basic implementation of a <xref:System.ServiceModel.ServiceAuthorizationManager> class that includes overriding the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method.</span></span> <span data-ttu-id="cad10-136">此範例程式碼會檢查自訂宣告的 <xref:System.IdentityModel.Policy.AuthorizationContext>，並在該自訂宣告符合來自 `true` 的動作值時傳回 <xref:System.ServiceModel.OperationContext>。</span><span class="sxs-lookup"><span data-stu-id="cad10-136">The example code examines the <xref:System.IdentityModel.Policy.AuthorizationContext> for a custom claim and returns `true` when the resource for that custom claim matches the action value from the <xref:System.ServiceModel.OperationContext>.</span></span> <span data-ttu-id="cad10-137">如需更完整實作的<xref:System.ServiceModel.ServiceAuthorizationManager>類別，請參閱[授權原則](../../../../docs/framework/wcf/samples/authorization-policy.md)。</span><span class="sxs-lookup"><span data-stu-id="cad10-137">For a more complete implementation of a <xref:System.ServiceModel.ServiceAuthorizationManager> class, see [Authorization Policy](../../../../docs/framework/wcf/samples/authorization-policy.md).</span></span>  
  
 [!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
 [!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="cad10-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cad10-138">See Also</span></span>  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
 [<span data-ttu-id="cad10-139">授權原則</span><span class="sxs-lookup"><span data-stu-id="cad10-139">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)  
 [<span data-ttu-id="cad10-140">授權原則</span><span class="sxs-lookup"><span data-stu-id="cad10-140">Authorization Policy</span></span>](../../../../docs/framework/wcf/samples/authorization-policy.md)
