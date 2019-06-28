---
title: 憑證用戶端的訊息安全性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99770573-c815-4428-a38c-e4335c8bd7ce
ms.openlocfilehash: fb68487746a7dc9cec1d1473b445bccc7b2b23c2
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2019
ms.locfileid: "67424882"
---
# <a name="message-security-with-a-certificate-client"></a><span data-ttu-id="d082e-102">憑證用戶端的訊息安全性</span><span class="sxs-lookup"><span data-stu-id="d082e-102">Message Security with a Certificate Client</span></span>
<span data-ttu-id="d082e-103">下列案例示範 Windows Communication Foundation (WCF) 用戶端和服務使用訊息安全性模式保護。</span><span class="sxs-lookup"><span data-stu-id="d082e-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured using message security mode.</span></span> <span data-ttu-id="d082e-104">用戶端與服務皆以憑證驗證。</span><span class="sxs-lookup"><span data-stu-id="d082e-104">Both the client and the service are authenticated with certificates.</span></span> <span data-ttu-id="d082e-105">如需詳細資訊，請參閱 <<c0> [ 分散式應用程式安全性](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)。</span><span class="sxs-lookup"><span data-stu-id="d082e-105">For more information, see [Distributed Application Security](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).</span></span>

 ![如果螢幕擷取畫面顯示具有憑證的用戶端。](./media/message-security-with-a-certificate-client/client-with-certificate.gif)  
  
 <span data-ttu-id="d082e-107">範例應用程式，請參閱[訊息安全性憑證](../../../../docs/framework/wcf/samples/message-security-certificate.md)。</span><span class="sxs-lookup"><span data-stu-id="d082e-107">For a sample application, see [Message Security Certificate](../../../../docs/framework/wcf/samples/message-security-certificate.md).</span></span>  

|<span data-ttu-id="d082e-108">特性</span><span class="sxs-lookup"><span data-stu-id="d082e-108">Characteristic</span></span>|<span data-ttu-id="d082e-109">描述</span><span class="sxs-lookup"><span data-stu-id="d082e-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="d082e-110">安全性模式</span><span class="sxs-lookup"><span data-stu-id="d082e-110">Security Mode</span></span>|<span data-ttu-id="d082e-111">Message</span><span class="sxs-lookup"><span data-stu-id="d082e-111">Message</span></span>|  
|<span data-ttu-id="d082e-112">互通性</span><span class="sxs-lookup"><span data-stu-id="d082e-112">Interoperability</span></span>|<span data-ttu-id="d082e-113">WCF 只</span><span class="sxs-lookup"><span data-stu-id="d082e-113">WCF only</span></span>|  
|<span data-ttu-id="d082e-114">驗證 (伺服器)</span><span class="sxs-lookup"><span data-stu-id="d082e-114">Authentication (Server)</span></span>|<span data-ttu-id="d082e-115">使用服務憑證</span><span class="sxs-lookup"><span data-stu-id="d082e-115">Using service certificate</span></span>|  
|<span data-ttu-id="d082e-116">驗證 (用戶端)</span><span class="sxs-lookup"><span data-stu-id="d082e-116">Authentication (Client)</span></span>|<span data-ttu-id="d082e-117">使用用戶端憑證</span><span class="sxs-lookup"><span data-stu-id="d082e-117">Using client certificate</span></span>|  
|<span data-ttu-id="d082e-118">完整性</span><span class="sxs-lookup"><span data-stu-id="d082e-118">Integrity</span></span>|<span data-ttu-id="d082e-119">是</span><span class="sxs-lookup"><span data-stu-id="d082e-119">Yes</span></span>|  
|<span data-ttu-id="d082e-120">機密性</span><span class="sxs-lookup"><span data-stu-id="d082e-120">Confidentiality</span></span>|<span data-ttu-id="d082e-121">是</span><span class="sxs-lookup"><span data-stu-id="d082e-121">Yes</span></span>|  
|<span data-ttu-id="d082e-122">Transport</span><span class="sxs-lookup"><span data-stu-id="d082e-122">Transport</span></span>|<span data-ttu-id="d082e-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="d082e-123">HTTP</span></span>|  
|<span data-ttu-id="d082e-124">繫結</span><span class="sxs-lookup"><span data-stu-id="d082e-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="d082e-125">服務</span><span class="sxs-lookup"><span data-stu-id="d082e-125">Service</span></span>  
 <span data-ttu-id="d082e-126">下列程式碼和組態要獨立執行。</span><span class="sxs-lookup"><span data-stu-id="d082e-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="d082e-127">執行下列任一步驟：</span><span class="sxs-lookup"><span data-stu-id="d082e-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="d082e-128">使用不含組態的程式碼建立獨立服務。</span><span class="sxs-lookup"><span data-stu-id="d082e-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="d082e-129">使用提供的組態建立服務，但不要定義任何端點。</span><span class="sxs-lookup"><span data-stu-id="d082e-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="d082e-130">程式碼</span><span class="sxs-lookup"><span data-stu-id="d082e-130">Code</span></span>  
 <span data-ttu-id="d082e-131">下列程式碼顯示如何建立使用訊息安全性產生安全內容的服務端點。</span><span class="sxs-lookup"><span data-stu-id="d082e-131">The following code shows how to create a service endpoint that uses message security to establish a secure context.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#10)]
 [!code-vb[C_SecurityScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#10)]  
  
### <a name="configuration"></a><span data-ttu-id="d082e-132">組態</span><span class="sxs-lookup"><span data-stu-id="d082e-132">Configuration</span></span>  
 <span data-ttu-id="d082e-133">可以使用以下組態來取代程式碼。</span><span class="sxs-lookup"><span data-stu-id="d082e-133">The following configuration can be used instead of the code.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="d082e-134">用戶端</span><span class="sxs-lookup"><span data-stu-id="d082e-134">Client</span></span>  
 <span data-ttu-id="d082e-135">下列程式碼和組態要獨立執行。</span><span class="sxs-lookup"><span data-stu-id="d082e-135">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="d082e-136">執行下列任一步驟：</span><span class="sxs-lookup"><span data-stu-id="d082e-136">Do one of the following:</span></span>  
  
- <span data-ttu-id="d082e-137">使用此程式碼 (和用戶端程式碼) 建立獨立用戶端。</span><span class="sxs-lookup"><span data-stu-id="d082e-137">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="d082e-138">建立未定義任何端點位址的用戶端，</span><span class="sxs-lookup"><span data-stu-id="d082e-138">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="d082e-139">然後改用可接受組態名稱當做引數的用戶端建構函式。</span><span class="sxs-lookup"><span data-stu-id="d082e-139">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="d082e-140">例如:</span><span class="sxs-lookup"><span data-stu-id="d082e-140">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="d082e-141">程式碼</span><span class="sxs-lookup"><span data-stu-id="d082e-141">Code</span></span>  
 <span data-ttu-id="d082e-142">下列程式碼會建立用戶端。</span><span class="sxs-lookup"><span data-stu-id="d082e-142">The following code creates the client.</span></span> <span data-ttu-id="d082e-143">繫結會使用訊息模式安全性，而且用戶端認證類型設為 `Certificate`。</span><span class="sxs-lookup"><span data-stu-id="d082e-143">The binding is to message mode security, and the client credential type is set to `Certificate`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#17)]
 [!code-vb[C_SecurityScenarios#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#17)]  
  
### <a name="configuration"></a><span data-ttu-id="d082e-144">組態</span><span class="sxs-lookup"><span data-stu-id="d082e-144">Configuration</span></span>  
 <span data-ttu-id="d082e-145">下列組態指定使用端點行為的用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="d082e-145">The following configuration specifies the client certificate using an endpoint behavior.</span></span> <span data-ttu-id="d082e-146">如需憑證的詳細資訊，請參閱[使用憑證](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。</span><span class="sxs-lookup"><span data-stu-id="d082e-146">For more information about certificates, see [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span> <span data-ttu-id="d082e-147">程式碼也會使用 <`identity`> 項目來指定預期的伺服器識別網域名稱系統 (DNS)。</span><span class="sxs-lookup"><span data-stu-id="d082e-147">The code also uses an <`identity`> element to specify a Domain Name System (DNS) of the expected server identity.</span></span> <span data-ttu-id="d082e-148">如需身分識別的詳細資訊，請參閱[服務身分識別和驗證](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)。</span><span class="sxs-lookup"><span data-stu-id="d082e-148">For more information about identity, see [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d082e-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d082e-149">See also</span></span>

- [<span data-ttu-id="d082e-150">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="d082e-150">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="d082e-151">服務身分識別和驗證</span><span class="sxs-lookup"><span data-stu-id="d082e-151">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [<span data-ttu-id="d082e-152">使用憑證</span><span class="sxs-lookup"><span data-stu-id="d082e-152">Working with Certificates</span></span>](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="d082e-153">Windows Server App Fabric 的安全性模型</span><span class="sxs-lookup"><span data-stu-id="d082e-153">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
