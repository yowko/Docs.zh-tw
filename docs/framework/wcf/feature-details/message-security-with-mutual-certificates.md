---
title: 相互憑證的訊息安全性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99d7a528-7ae4-4d39-a0f9-3066ea237de0
ms.openlocfilehash: 44d06762bf66950ea0cc06986c61ecd548ae2e0c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576404"
---
# <a name="message-security-with-mutual-certificates"></a><span data-ttu-id="7eaa8-102">相互憑證的訊息安全性</span><span class="sxs-lookup"><span data-stu-id="7eaa8-102">Message Security with Mutual Certificates</span></span>
<span data-ttu-id="7eaa8-103">下列案例顯示使用訊息安全性模式保護的 Windows Communication Foundation （WCF）服務和用戶端。</span><span class="sxs-lookup"><span data-stu-id="7eaa8-103">The following scenario shows a Windows Communication Foundation (WCF) service and client secured using message security mode.</span></span> <span data-ttu-id="7eaa8-104">用戶端與服務以憑證加以驗證。</span><span class="sxs-lookup"><span data-stu-id="7eaa8-104">The client and the service are authenticated with certificates.</span></span>  
  
 <span data-ttu-id="7eaa8-105">因為案例使用具有 X.509 憑證權杖設定檔的 WS-Security，所以這個案例是互通的。</span><span class="sxs-lookup"><span data-stu-id="7eaa8-105">This scenario is interoperable because it uses WS-Security with the X.509 certificate token profile.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7eaa8-106">這個案例並不執行服務憑證的交涉。</span><span class="sxs-lookup"><span data-stu-id="7eaa8-106">This scenario does not perform negotiation of the service certificate.</span></span> <span data-ttu-id="7eaa8-107">在任何通訊前，必須先對用戶端提供服務憑證。</span><span class="sxs-lookup"><span data-stu-id="7eaa8-107">The service certificate must be provided to the client in advance of any communication.</span></span> <span data-ttu-id="7eaa8-108">伺服器憑證可在應用程式散發，或在超出範圍通訊中提供。</span><span class="sxs-lookup"><span data-stu-id="7eaa8-108">The server certificate can be distributed with the application or provided in an out-of-band communication.</span></span>  
  
 <span data-ttu-id="7eaa8-109">![相互憑證的訊息安全性](media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span><span class="sxs-lookup"><span data-stu-id="7eaa8-109">![Message security with mutual certificates](media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span></span>  
  
|<span data-ttu-id="7eaa8-110">特性</span><span class="sxs-lookup"><span data-stu-id="7eaa8-110">Characteristic</span></span>|<span data-ttu-id="7eaa8-111">描述</span><span class="sxs-lookup"><span data-stu-id="7eaa8-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="7eaa8-112">安全性模式</span><span class="sxs-lookup"><span data-stu-id="7eaa8-112">Security Mode</span></span>|<span data-ttu-id="7eaa8-113">訊息</span><span class="sxs-lookup"><span data-stu-id="7eaa8-113">Message</span></span>|  
|<span data-ttu-id="7eaa8-114">互通性</span><span class="sxs-lookup"><span data-stu-id="7eaa8-114">Interoperability</span></span>|<span data-ttu-id="7eaa8-115">是的，採用 WS-Security 及 X.509 憑證權杖設定檔相容的用戶端及服務。</span><span class="sxs-lookup"><span data-stu-id="7eaa8-115">Yes, with WS-Security and X.509 certificate token profile compatible clients and services.</span></span>|  
|<span data-ttu-id="7eaa8-116">驗證</span><span class="sxs-lookup"><span data-stu-id="7eaa8-116">Authentication</span></span>|<span data-ttu-id="7eaa8-117">伺服器和用戶端的交互驗證。</span><span class="sxs-lookup"><span data-stu-id="7eaa8-117">Mutual authentication of the server and client.</span></span>|  
|<span data-ttu-id="7eaa8-118">完整性</span><span class="sxs-lookup"><span data-stu-id="7eaa8-118">Integrity</span></span>|<span data-ttu-id="7eaa8-119">是</span><span class="sxs-lookup"><span data-stu-id="7eaa8-119">Yes</span></span>|  
|<span data-ttu-id="7eaa8-120">保密</span><span class="sxs-lookup"><span data-stu-id="7eaa8-120">Confidentiality</span></span>|<span data-ttu-id="7eaa8-121">是</span><span class="sxs-lookup"><span data-stu-id="7eaa8-121">Yes</span></span>|  
|<span data-ttu-id="7eaa8-122">傳輸</span><span class="sxs-lookup"><span data-stu-id="7eaa8-122">Transport</span></span>|<span data-ttu-id="7eaa8-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="7eaa8-123">HTTP</span></span>|  
|<span data-ttu-id="7eaa8-124">繫結</span><span class="sxs-lookup"><span data-stu-id="7eaa8-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="7eaa8-125">服務</span><span class="sxs-lookup"><span data-stu-id="7eaa8-125">Service</span></span>  
 <span data-ttu-id="7eaa8-126">下列程式碼和組態要獨立執行。</span><span class="sxs-lookup"><span data-stu-id="7eaa8-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="7eaa8-127">執行下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="7eaa8-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="7eaa8-128">使用不含組態的程式碼建立獨立服務。</span><span class="sxs-lookup"><span data-stu-id="7eaa8-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="7eaa8-129">使用提供的組態建立服務，但不要定義任何端點。</span><span class="sxs-lookup"><span data-stu-id="7eaa8-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="7eaa8-130">程式碼</span><span class="sxs-lookup"><span data-stu-id="7eaa8-130">Code</span></span>  
 <span data-ttu-id="7eaa8-131">下列程式碼顯示建立使用訊息安全性的服務端點。</span><span class="sxs-lookup"><span data-stu-id="7eaa8-131">The following code shows creates a service endpoint that uses message security.</span></span> <span data-ttu-id="7eaa8-132">服務需要憑證來驗證自己。</span><span class="sxs-lookup"><span data-stu-id="7eaa8-132">The service requires a certificate to authenticate itself.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#13)]
 [!code-vb[C_SecurityScenarios#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#13)]  
  
### <a name="configuration"></a><span data-ttu-id="7eaa8-133">組態</span><span class="sxs-lookup"><span data-stu-id="7eaa8-133">Configuration</span></span>  
 <span data-ttu-id="7eaa8-134">您可使用下列組態來取代程式碼，以建立相同的服務。</span><span class="sxs-lookup"><span data-stu-id="7eaa8-134">The following configuration can be used instead of the code to create the same service.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="serviceCredentialBehavior">  
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
      <service behaviorConfiguration="serviceCredentialBehavior"
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"  
                  bindingConfiguration="InteropCertificateBinding"  
                  name="WSHttpBinding_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="InteropCertificateBinding">  
          <security mode="Message">  
            <message clientCredentialType="Certificate"  
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="7eaa8-135">用戶端</span><span class="sxs-lookup"><span data-stu-id="7eaa8-135">Client</span></span>  
 <span data-ttu-id="7eaa8-136">下列程式碼和組態要獨立執行。</span><span class="sxs-lookup"><span data-stu-id="7eaa8-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="7eaa8-137">執行下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="7eaa8-137">Do one of the following:</span></span>  
  
- <span data-ttu-id="7eaa8-138">使用此程式碼 (和用戶端程式碼) 建立獨立用戶端。</span><span class="sxs-lookup"><span data-stu-id="7eaa8-138">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="7eaa8-139">建立未定義任何端點位址的用戶端，</span><span class="sxs-lookup"><span data-stu-id="7eaa8-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="7eaa8-140">然後改用可接受組態名稱當做引數的用戶端建構函式。</span><span class="sxs-lookup"><span data-stu-id="7eaa8-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="7eaa8-141">例如：</span><span class="sxs-lookup"><span data-stu-id="7eaa8-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="7eaa8-142">程式碼</span><span class="sxs-lookup"><span data-stu-id="7eaa8-142">Code</span></span>  
 <span data-ttu-id="7eaa8-143">下列程式碼會建立用戶端。</span><span class="sxs-lookup"><span data-stu-id="7eaa8-143">The following code creates the client.</span></span> <span data-ttu-id="7eaa8-144">安全性模式設為訊息，而且用戶端認證類型設為憑證。</span><span class="sxs-lookup"><span data-stu-id="7eaa8-144">The security mode is set to Message, and the client credential type is set to Certificate.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#20)]
 [!code-vb[C_SecurityScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#20)]  
  
### <a name="configuration"></a><span data-ttu-id="7eaa8-145">組態</span><span class="sxs-lookup"><span data-stu-id="7eaa8-145">Configuration</span></span>  
 <span data-ttu-id="7eaa8-146">下列組態會設定用戶端。</span><span class="sxs-lookup"><span data-stu-id="7eaa8-146">The following configures the client.</span></span> <span data-ttu-id="7eaa8-147">您必須使用來指定用戶端憑證 [\<clientCertificate>](../../configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="7eaa8-147">A client certificate must be specified using the [\<clientCertificate>](../../configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span> <span data-ttu-id="7eaa8-148">此外，也會使用來指定服務憑證 [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="7eaa8-148">Also, the service certificate is specified using the [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCredentialsBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="Cohowinery.com"
                 storeLocation="CurrentUser"  
                 storeName="My"  
                 x509FindType="FindBySubjectName" />  
            <serviceCertificate>  
              <defaultCertificate findValue="Contoso.com"
                                  storeLocation="CurrentUser"  
                                  storeName="TrustedPeople"  
                                  x509FindType="FindBySubjectName" />  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Certificate"
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"
                behaviorConfiguration="ClientCredentialsBehavior"  
                binding="wsHttpBinding"
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <certificate encodedValue="Encoded_Value_Not_Shown" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7eaa8-149">請參閱</span><span class="sxs-lookup"><span data-stu-id="7eaa8-149">See also</span></span>

- [<span data-ttu-id="7eaa8-150">安全性總覽</span><span class="sxs-lookup"><span data-stu-id="7eaa8-150">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="7eaa8-151">[Windows Server AppFabric 的資訊安全模型](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="7eaa8-151">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
- <span data-ttu-id="7eaa8-152">[如何：在 WCF 中建立和安裝用於開發期間傳輸安全性的暫時憑證](https://docs.microsoft.com/previous-versions/msp-n-p/ff648498(v=pandp.10))</span><span class="sxs-lookup"><span data-stu-id="7eaa8-152">[How to: Create and Install Temporary Certificates in WCF for Transport Security During Development](https://docs.microsoft.com/previous-versions/msp-n-p/ff648498(v=pandp.10))</span></span>
