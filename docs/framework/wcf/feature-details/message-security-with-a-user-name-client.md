---
title: "使用者名稱用戶端的訊息安全性"
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
ms.assetid: 36335cb9-76b8-4443-92c7-44f081eabb21
caps.latest.revision: "15"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 429136ab3e01f3f53f662db02bbac6096be48d11
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="message-security-with-a-user-name-client"></a><span data-ttu-id="5a762-102">使用者名稱用戶端的訊息安全性</span><span class="sxs-lookup"><span data-stu-id="5a762-102">Message Security with a User Name Client</span></span>
<span data-ttu-id="5a762-103">下圖示範使用訊息層級安全性保護的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務與用戶端。</span><span class="sxs-lookup"><span data-stu-id="5a762-103">The following illustration shows an [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service and client secured using message-level security.</span></span> <span data-ttu-id="5a762-104">服務會使用 X.509 憑證來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="5a762-104">The service is authenticated with an X.509 certificate.</span></span> <span data-ttu-id="5a762-105">用戶端會使用使用者名稱與密碼來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="5a762-105">The client authenticates using a user name and password.</span></span>  
  
 <span data-ttu-id="5a762-106">範例應用程式，請參閱[訊息安全性使用者名稱](../../../../docs/framework/wcf/samples/message-security-user-name.md)。</span><span class="sxs-lookup"><span data-stu-id="5a762-106">For a sample application, see [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md).</span></span>  
  
 <span data-ttu-id="5a762-107">![使用使用者名稱驗證的訊息安全性](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span><span class="sxs-lookup"><span data-stu-id="5a762-107">![Message security using username authentication](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span></span>  
  
|<span data-ttu-id="5a762-108">特性</span><span class="sxs-lookup"><span data-stu-id="5a762-108">Characteristic</span></span>|<span data-ttu-id="5a762-109">描述</span><span class="sxs-lookup"><span data-stu-id="5a762-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="5a762-110">安全性模式</span><span class="sxs-lookup"><span data-stu-id="5a762-110">Security Mode</span></span>|<span data-ttu-id="5a762-111">訊息</span><span class="sxs-lookup"><span data-stu-id="5a762-111">Message</span></span>|  
|<span data-ttu-id="5a762-112">互通性</span><span class="sxs-lookup"><span data-stu-id="5a762-112">Interoperability</span></span>|<span data-ttu-id="5a762-113">僅限 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a762-113">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] only</span></span>|  
|<span data-ttu-id="5a762-114">驗證 (伺服器)</span><span class="sxs-lookup"><span data-stu-id="5a762-114">Authentication (Server)</span></span>|<span data-ttu-id="5a762-115">初始交涉需要伺服器驗證</span><span class="sxs-lookup"><span data-stu-id="5a762-115">Initial negotiation requires server authentication</span></span>|  
|<span data-ttu-id="5a762-116">驗證 (用戶端)</span><span class="sxs-lookup"><span data-stu-id="5a762-116">Authentication (Client)</span></span>|<span data-ttu-id="5a762-117">使用者名稱/密碼</span><span class="sxs-lookup"><span data-stu-id="5a762-117">User name/password</span></span>|  
|<span data-ttu-id="5a762-118">完整性</span><span class="sxs-lookup"><span data-stu-id="5a762-118">Integrity</span></span>|<span data-ttu-id="5a762-119">是，使用共用安全性內容</span><span class="sxs-lookup"><span data-stu-id="5a762-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="5a762-120">機密性</span><span class="sxs-lookup"><span data-stu-id="5a762-120">Confidentiality</span></span>|<span data-ttu-id="5a762-121">是，使用共用安全性內容</span><span class="sxs-lookup"><span data-stu-id="5a762-121">Yes, using shared security context</span></span>|  
|<span data-ttu-id="5a762-122">Transport</span><span class="sxs-lookup"><span data-stu-id="5a762-122">Transport</span></span>|<span data-ttu-id="5a762-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="5a762-123">HTTP</span></span>|  
|<span data-ttu-id="5a762-124">繫結</span><span class="sxs-lookup"><span data-stu-id="5a762-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="5a762-125">服務</span><span class="sxs-lookup"><span data-stu-id="5a762-125">Service</span></span>  
 <span data-ttu-id="5a762-126">下列程式碼和組態要獨立執行。</span><span class="sxs-lookup"><span data-stu-id="5a762-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="5a762-127">執行下列任一步驟：</span><span class="sxs-lookup"><span data-stu-id="5a762-127">Do one of the following:</span></span>  
  
-   <span data-ttu-id="5a762-128">使用不含組態的程式碼建立獨立服務。</span><span class="sxs-lookup"><span data-stu-id="5a762-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="5a762-129">使用提供的組態建立服務，但不要定義任何端點。</span><span class="sxs-lookup"><span data-stu-id="5a762-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5a762-130">程式碼</span><span class="sxs-lookup"><span data-stu-id="5a762-130">Code</span></span>  
 <span data-ttu-id="5a762-131">下列程式碼會顯示如何建立會使用訊息安全性的服務端點。</span><span class="sxs-lookup"><span data-stu-id="5a762-131">The following code shows how to create a service endpoint that uses message security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#9)]
 [!code-vb[C_SecurityScenarios#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#9)]  
  
### <a name="configuration"></a><span data-ttu-id="5a762-132">組態</span><span class="sxs-lookup"><span data-stu-id="5a762-132">Configuration</span></span>  
 <span data-ttu-id="5a762-133">可使用下列組態來取代程式碼：</span><span class="sxs-lookup"><span data-stu-id="5a762-133">The following configuration can be used instead of the code:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"   
                                storeLocation="LocalMachine"  
                                storeName="My"     
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="ServiceCredentialsBehavior"  
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="MessageAndUserName"  
                  name="SecuredByTransportEndpoint"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="MessageAndUserName">  
          <security mode="Message">              
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="5a762-134">用戶端</span><span class="sxs-lookup"><span data-stu-id="5a762-134">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="5a762-135">程式碼</span><span class="sxs-lookup"><span data-stu-id="5a762-135">Code</span></span>  
 <span data-ttu-id="5a762-136">下列程式碼會建立用戶端。</span><span class="sxs-lookup"><span data-stu-id="5a762-136">The following code creates the client.</span></span> <span data-ttu-id="5a762-137">繫結會使用訊息模式安全性，而且用戶端認證類型設為 `UserName`。</span><span class="sxs-lookup"><span data-stu-id="5a762-137">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="5a762-138">使用者名稱和密碼只能使用程式碼 (它是不可設定的) 來指定。</span><span class="sxs-lookup"><span data-stu-id="5a762-138">The user name and password can only be specified using code (it is not configurable).</span></span> <span data-ttu-id="5a762-139">在此不示範傳回使用者名稱與密碼的程式碼，因為必須在應用程式層級才能完成這個動作。</span><span class="sxs-lookup"><span data-stu-id="5a762-139">The code to return the user name and password is not shown here because it must be done at the application level.</span></span> <span data-ttu-id="5a762-140">例如，使用 [Windows 表單] 對話方塊查詢使用者的資料。</span><span class="sxs-lookup"><span data-stu-id="5a762-140">For example, use a Windows Forms dialog box to query the user for the data.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#16)]
 [!code-vb[C_SecurityScenarios#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#16)]  
  
### <a name="configuration"></a><span data-ttu-id="5a762-141">組態</span><span class="sxs-lookup"><span data-stu-id="5a762-141">Configuration</span></span>  
 <span data-ttu-id="5a762-142">下列程式碼會設定用戶端。</span><span class="sxs-lookup"><span data-stu-id="5a762-142">The following code configures the client.</span></span> <span data-ttu-id="5a762-143">繫結會使用訊息模式安全性，而且用戶端認證類型設為 `UserName`。</span><span class="sxs-lookup"><span data-stu-id="5a762-143">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="5a762-144">使用者名稱和密碼只能使用程式碼 (它是不可設定的) 來指定。</span><span class="sxs-lookup"><span data-stu-id="5a762-144">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"   
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"   
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value ="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5a762-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a762-145">See Also</span></span>  
 [<span data-ttu-id="5a762-146">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="5a762-146">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="5a762-147">訊息安全性使用者名稱</span><span class="sxs-lookup"><span data-stu-id="5a762-147">Message Security User Name</span></span>](../../../../docs/framework/wcf/samples/message-security-user-name.md)  
 [<span data-ttu-id="5a762-148">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="5a762-148">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [<span data-ttu-id="5a762-149">\<身分識別 ></span><span class="sxs-lookup"><span data-stu-id="5a762-149">\<identity></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)  
 [<span data-ttu-id="5a762-150">Windows Server App Fabric 的安全性模型</span><span class="sxs-lookup"><span data-stu-id="5a762-150">Security Model for Windows Server App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
