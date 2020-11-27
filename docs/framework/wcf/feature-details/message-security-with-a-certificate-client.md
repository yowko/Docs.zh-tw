---
title: 憑證用戶端的訊息安全性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99770573-c815-4428-a38c-e4335c8bd7ce
ms.openlocfilehash: 4a1cb6d804d313f438fc8e7a92946d55f73b9ee5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288576"
---
# <a name="message-security-with-a-certificate-client"></a><span data-ttu-id="791ae-102">憑證用戶端的訊息安全性</span><span class="sxs-lookup"><span data-stu-id="791ae-102">Message Security with a Certificate Client</span></span>

<span data-ttu-id="791ae-103">下列案例顯示 Windows Communication Foundation (使用訊息安全性模式保護的 WCF) 用戶端和服務。</span><span class="sxs-lookup"><span data-stu-id="791ae-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured using message security mode.</span></span> <span data-ttu-id="791ae-104">用戶端與服務皆以憑證驗證。</span><span class="sxs-lookup"><span data-stu-id="791ae-104">Both the client and the service are authenticated with certificates.</span></span> <span data-ttu-id="791ae-105">如需詳細資訊，請參閱 [分散式應用程式安全性](distributed-application-security.md)。</span><span class="sxs-lookup"><span data-stu-id="791ae-105">For more information, see [Distributed Application Security](distributed-application-security.md).</span></span>

 ![顯示具有憑證之用戶端的螢幕擷取畫面。](./media/message-security-with-a-certificate-client/client-with-certificate.gif)  
  
 <span data-ttu-id="791ae-107">如需範例應用程式，請參閱 [訊息安全性憑證](../samples/message-security-certificate.md)。</span><span class="sxs-lookup"><span data-stu-id="791ae-107">For a sample application, see [Message Security Certificate](../samples/message-security-certificate.md).</span></span>  

|<span data-ttu-id="791ae-108">特性</span><span class="sxs-lookup"><span data-stu-id="791ae-108">Characteristic</span></span>|<span data-ttu-id="791ae-109">描述</span><span class="sxs-lookup"><span data-stu-id="791ae-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="791ae-110">安全性模式</span><span class="sxs-lookup"><span data-stu-id="791ae-110">Security Mode</span></span>|<span data-ttu-id="791ae-111">訊息</span><span class="sxs-lookup"><span data-stu-id="791ae-111">Message</span></span>|  
|<span data-ttu-id="791ae-112">互通性</span><span class="sxs-lookup"><span data-stu-id="791ae-112">Interoperability</span></span>|<span data-ttu-id="791ae-113">僅限 WCF</span><span class="sxs-lookup"><span data-stu-id="791ae-113">WCF only</span></span>|  
|<span data-ttu-id="791ae-114">驗證 (伺服器)</span><span class="sxs-lookup"><span data-stu-id="791ae-114">Authentication (Server)</span></span>|<span data-ttu-id="791ae-115">使用服務憑證</span><span class="sxs-lookup"><span data-stu-id="791ae-115">Using service certificate</span></span>|  
|<span data-ttu-id="791ae-116">驗證 (用戶端)</span><span class="sxs-lookup"><span data-stu-id="791ae-116">Authentication (Client)</span></span>|<span data-ttu-id="791ae-117">使用用戶端憑證</span><span class="sxs-lookup"><span data-stu-id="791ae-117">Using client certificate</span></span>|  
|<span data-ttu-id="791ae-118">完整性</span><span class="sxs-lookup"><span data-stu-id="791ae-118">Integrity</span></span>|<span data-ttu-id="791ae-119">Yes</span><span class="sxs-lookup"><span data-stu-id="791ae-119">Yes</span></span>|  
|<span data-ttu-id="791ae-120">機密性</span><span class="sxs-lookup"><span data-stu-id="791ae-120">Confidentiality</span></span>|<span data-ttu-id="791ae-121">是</span><span class="sxs-lookup"><span data-stu-id="791ae-121">Yes</span></span>|  
|<span data-ttu-id="791ae-122">傳輸</span><span class="sxs-lookup"><span data-stu-id="791ae-122">Transport</span></span>|<span data-ttu-id="791ae-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="791ae-123">HTTP</span></span>|  
|<span data-ttu-id="791ae-124">繫結</span><span class="sxs-lookup"><span data-stu-id="791ae-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="791ae-125">服務</span><span class="sxs-lookup"><span data-stu-id="791ae-125">Service</span></span>  

 <span data-ttu-id="791ae-126">下列程式碼和組態要獨立執行。</span><span class="sxs-lookup"><span data-stu-id="791ae-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="791ae-127">請執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="791ae-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="791ae-128">使用不含組態的程式碼建立獨立服務。</span><span class="sxs-lookup"><span data-stu-id="791ae-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="791ae-129">使用提供的組態建立服務，但不要定義任何端點。</span><span class="sxs-lookup"><span data-stu-id="791ae-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="791ae-130">程式碼</span><span class="sxs-lookup"><span data-stu-id="791ae-130">Code</span></span>  

 <span data-ttu-id="791ae-131">下列程式碼顯示如何建立使用訊息安全性產生安全內容的服務端點。</span><span class="sxs-lookup"><span data-stu-id="791ae-131">The following code shows how to create a service endpoint that uses message security to establish a secure context.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#10)]
 [!code-vb[C_SecurityScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#10)]  
  
### <a name="configuration"></a><span data-ttu-id="791ae-132">設定</span><span class="sxs-lookup"><span data-stu-id="791ae-132">Configuration</span></span>  

 <span data-ttu-id="791ae-133">可以使用以下組態來取代程式碼。</span><span class="sxs-lookup"><span data-stu-id="791ae-133">The following configuration can be used instead of the code.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"  
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
                  bindingConfiguration="MessageAndCertificateClient"
                  name="SecuredByClientCertificate"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator">  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="791ae-134">用戶端</span><span class="sxs-lookup"><span data-stu-id="791ae-134">Client</span></span>  

 <span data-ttu-id="791ae-135">下列程式碼和組態要獨立執行。</span><span class="sxs-lookup"><span data-stu-id="791ae-135">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="791ae-136">請執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="791ae-136">Do one of the following:</span></span>  
  
- <span data-ttu-id="791ae-137">使用此程式碼 (和用戶端程式碼) 建立獨立用戶端。</span><span class="sxs-lookup"><span data-stu-id="791ae-137">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="791ae-138">建立未定義任何端點位址的用戶端，</span><span class="sxs-lookup"><span data-stu-id="791ae-138">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="791ae-139">然後改用可接受組態名稱當做引數的用戶端建構函式。</span><span class="sxs-lookup"><span data-stu-id="791ae-139">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="791ae-140">例如：</span><span class="sxs-lookup"><span data-stu-id="791ae-140">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="791ae-141">程式碼</span><span class="sxs-lookup"><span data-stu-id="791ae-141">Code</span></span>  

 <span data-ttu-id="791ae-142">下列程式碼會建立用戶端。</span><span class="sxs-lookup"><span data-stu-id="791ae-142">The following code creates the client.</span></span> <span data-ttu-id="791ae-143">繫結會使用訊息模式安全性，而且用戶端認證類型設為 `Certificate`。</span><span class="sxs-lookup"><span data-stu-id="791ae-143">The binding is to message mode security, and the client credential type is set to `Certificate`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#17)]
 [!code-vb[C_SecurityScenarios#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#17)]  
  
### <a name="configuration"></a><span data-ttu-id="791ae-144">設定</span><span class="sxs-lookup"><span data-stu-id="791ae-144">Configuration</span></span>  

 <span data-ttu-id="791ae-145">下列組態指定使用端點行為的用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="791ae-145">The following configuration specifies the client certificate using an endpoint behavior.</span></span> <span data-ttu-id="791ae-146">如需憑證的詳細資訊，請參閱[使用憑證](working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="791ae-146">For more information about certificates, see [Working with Certificates](working-with-certificates.md).</span></span> <span data-ttu-id="791ae-147">程式碼也會使用 <`identity`> 專案來指定網域名稱系統 (DNS) 的預期伺服器身分識別。</span><span class="sxs-lookup"><span data-stu-id="791ae-147">The code also uses an <`identity`> element to specify a Domain Name System (DNS) of the expected server identity.</span></span> <span data-ttu-id="791ae-148">如需有關身分識別的詳細資訊，請參閱 [服務身分識別和驗證](service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="791ae-148">For more information about identity, see [Service Identity and Authentication](service-identity-and-authentication.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="endpointCredentialsBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="Cohowinery.com"
               storeLocation="LocalMachine"  
              x509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"
                behaviorConfiguration="endpointCredentialsBehavior"  
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="791ae-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="791ae-149">See also</span></span>

- [<span data-ttu-id="791ae-150">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="791ae-150">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="791ae-151">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="791ae-151">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)
- [<span data-ttu-id="791ae-152">使用憑證</span><span class="sxs-lookup"><span data-stu-id="791ae-152">Working with Certificates</span></span>](working-with-certificates.md)
- <span data-ttu-id="791ae-153">[Windows Server AppFabric 的資訊安全模型](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="791ae-153">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
