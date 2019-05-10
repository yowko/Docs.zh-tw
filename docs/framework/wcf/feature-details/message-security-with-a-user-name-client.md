---
title: 使用者名稱用戶端的訊息安全性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 36335cb9-76b8-4443-92c7-44f081eabb21
ms.openlocfilehash: a5e3e96ce8c8bb3304c8abcc93a881998382c6ec
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638004"
---
# <a name="message-security-with-a-user-name-client"></a><span data-ttu-id="62683-102">使用者名稱用戶端的訊息安全性</span><span class="sxs-lookup"><span data-stu-id="62683-102">Message Security with a User Name Client</span></span>
<span data-ttu-id="62683-103">下圖顯示 Windows Communication Foundation (WCF) 服務和用戶端使用訊息層級安全性保護。</span><span class="sxs-lookup"><span data-stu-id="62683-103">The following illustration shows an Windows Communication Foundation (WCF) service and client secured using message-level security.</span></span> <span data-ttu-id="62683-104">服務會使用 X.509 憑證來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="62683-104">The service is authenticated with an X.509 certificate.</span></span> <span data-ttu-id="62683-105">用戶端會使用使用者名稱與密碼來進行驗證。</span><span class="sxs-lookup"><span data-stu-id="62683-105">The client authenticates using a user name and password.</span></span>  
  
 <span data-ttu-id="62683-106">範例應用程式，請參閱[訊息安全性使用者名稱](../../../../docs/framework/wcf/samples/message-security-user-name.md)。</span><span class="sxs-lookup"><span data-stu-id="62683-106">For a sample application, see [Message Security User Name](../../../../docs/framework/wcf/samples/message-security-user-name.md).</span></span>  
  
 <span data-ttu-id="62683-107">![使用使用者名稱驗證的訊息安全性](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span><span class="sxs-lookup"><span data-stu-id="62683-107">![Message security using username authentication](../../../../docs/framework/wcf/feature-details/media/1fb10a61-7e1d-42f5-b1af-195bfee5b3c6.gif "1fb10a61-7e1d-42f5-b1af-195bfee5b3c6")</span></span>  
  
|<span data-ttu-id="62683-108">特性</span><span class="sxs-lookup"><span data-stu-id="62683-108">Characteristic</span></span>|<span data-ttu-id="62683-109">描述</span><span class="sxs-lookup"><span data-stu-id="62683-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="62683-110">安全性模式</span><span class="sxs-lookup"><span data-stu-id="62683-110">Security Mode</span></span>|<span data-ttu-id="62683-111">訊息</span><span class="sxs-lookup"><span data-stu-id="62683-111">Message</span></span>|  
|<span data-ttu-id="62683-112">互通性</span><span class="sxs-lookup"><span data-stu-id="62683-112">Interoperability</span></span>|<span data-ttu-id="62683-113">Windows Communication Foundation (WCF) 只</span><span class="sxs-lookup"><span data-stu-id="62683-113">Windows Communication Foundation (WCF) only</span></span>|  
|<span data-ttu-id="62683-114">驗證 (伺服器)</span><span class="sxs-lookup"><span data-stu-id="62683-114">Authentication (Server)</span></span>|<span data-ttu-id="62683-115">初始交涉需要伺服器驗證</span><span class="sxs-lookup"><span data-stu-id="62683-115">Initial negotiation requires server authentication</span></span>|  
|<span data-ttu-id="62683-116">驗證 (用戶端)</span><span class="sxs-lookup"><span data-stu-id="62683-116">Authentication (Client)</span></span>|<span data-ttu-id="62683-117">使用者名稱/密碼</span><span class="sxs-lookup"><span data-stu-id="62683-117">User name/password</span></span>|  
|<span data-ttu-id="62683-118">完整性</span><span class="sxs-lookup"><span data-stu-id="62683-118">Integrity</span></span>|<span data-ttu-id="62683-119">是，使用共用安全性內容</span><span class="sxs-lookup"><span data-stu-id="62683-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="62683-120">機密性</span><span class="sxs-lookup"><span data-stu-id="62683-120">Confidentiality</span></span>|<span data-ttu-id="62683-121">是，使用共用安全性內容</span><span class="sxs-lookup"><span data-stu-id="62683-121">Yes, using shared security context</span></span>|  
|<span data-ttu-id="62683-122">Transport</span><span class="sxs-lookup"><span data-stu-id="62683-122">Transport</span></span>|<span data-ttu-id="62683-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="62683-123">HTTP</span></span>|  
|<span data-ttu-id="62683-124">繫結</span><span class="sxs-lookup"><span data-stu-id="62683-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="62683-125">服務</span><span class="sxs-lookup"><span data-stu-id="62683-125">Service</span></span>  
 <span data-ttu-id="62683-126">下列程式碼和組態要獨立執行。</span><span class="sxs-lookup"><span data-stu-id="62683-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="62683-127">執行下列任一步驟：</span><span class="sxs-lookup"><span data-stu-id="62683-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="62683-128">使用不含組態的程式碼建立獨立服務。</span><span class="sxs-lookup"><span data-stu-id="62683-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="62683-129">使用提供的組態建立服務，但不要定義任何端點。</span><span class="sxs-lookup"><span data-stu-id="62683-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="62683-130">程式碼</span><span class="sxs-lookup"><span data-stu-id="62683-130">Code</span></span>  
 <span data-ttu-id="62683-131">下列程式碼會顯示如何建立會使用訊息安全性的服務端點。</span><span class="sxs-lookup"><span data-stu-id="62683-131">The following code shows how to create a service endpoint that uses message security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#9)]
 [!code-vb[C_SecurityScenarios#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#9)]  
  
### <a name="configuration"></a><span data-ttu-id="62683-132">組態</span><span class="sxs-lookup"><span data-stu-id="62683-132">Configuration</span></span>  
 <span data-ttu-id="62683-133">可使用下列組態來取代程式碼：</span><span class="sxs-lookup"><span data-stu-id="62683-133">The following configuration can be used instead of the code:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="62683-134">用戶端</span><span class="sxs-lookup"><span data-stu-id="62683-134">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="62683-135">程式碼</span><span class="sxs-lookup"><span data-stu-id="62683-135">Code</span></span>  
 <span data-ttu-id="62683-136">下列程式碼會建立用戶端。</span><span class="sxs-lookup"><span data-stu-id="62683-136">The following code creates the client.</span></span> <span data-ttu-id="62683-137">繫結會使用訊息模式安全性，而且用戶端認證類型設為 `UserName`。</span><span class="sxs-lookup"><span data-stu-id="62683-137">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="62683-138">使用者名稱和密碼只能使用程式碼 (它是不可設定的) 來指定。</span><span class="sxs-lookup"><span data-stu-id="62683-138">The user name and password can only be specified using code (it is not configurable).</span></span> <span data-ttu-id="62683-139">在此不示範傳回使用者名稱與密碼的程式碼，因為必須在應用程式層級才能完成這個動作。</span><span class="sxs-lookup"><span data-stu-id="62683-139">The code to return the user name and password is not shown here because it must be done at the application level.</span></span> <span data-ttu-id="62683-140">例如，使用 [Windows 表單] 對話方塊查詢使用者的資料。</span><span class="sxs-lookup"><span data-stu-id="62683-140">For example, use a Windows Forms dialog box to query the user for the data.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#16](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#16)]
 [!code-vb[C_SecurityScenarios#16](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#16)]  
  
### <a name="configuration"></a><span data-ttu-id="62683-141">組態</span><span class="sxs-lookup"><span data-stu-id="62683-141">Configuration</span></span>  
 <span data-ttu-id="62683-142">下列程式碼會設定用戶端。</span><span class="sxs-lookup"><span data-stu-id="62683-142">The following code configures the client.</span></span> <span data-ttu-id="62683-143">繫結會使用訊息模式安全性，而且用戶端認證類型設為 `UserName`。</span><span class="sxs-lookup"><span data-stu-id="62683-143">The binding is to message mode security, and the client credential type is set to `UserName`.</span></span> <span data-ttu-id="62683-144">使用者名稱和密碼只能使用程式碼 (它是不可設定的) 來指定。</span><span class="sxs-lookup"><span data-stu-id="62683-144">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="62683-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62683-145">See also</span></span>

- [<span data-ttu-id="62683-146">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="62683-146">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="62683-147">訊息安全性使用者名稱</span><span class="sxs-lookup"><span data-stu-id="62683-147">Message Security User Name</span></span>](../../../../docs/framework/wcf/samples/message-security-user-name.md)
- [<span data-ttu-id="62683-148">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="62683-148">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="62683-149">\<identity></span><span class="sxs-lookup"><span data-stu-id="62683-149">\<identity></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
- [<span data-ttu-id="62683-150">Windows Server App Fabric 的安全性模型</span><span class="sxs-lookup"><span data-stu-id="62683-150">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
