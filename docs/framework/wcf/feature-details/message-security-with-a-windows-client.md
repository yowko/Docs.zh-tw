---
title: Windows 用戶端的訊息安全性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 01e7d0b8-10f9-45c3-a4c5-53d44dc61eb8
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 34f6078baba86868fa03f37873731c39e73ac81f
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44337430"
---
# <a name="message-security-with-a-windows-client"></a><span data-ttu-id="29599-102">Windows 用戶端的訊息安全性</span><span class="sxs-lookup"><span data-stu-id="29599-102">Message Security with a Windows Client</span></span>
<span data-ttu-id="29599-103">這個案例示範 Windows Communication Foundation (WCF) 用戶端與受保護的訊息安全性模式的伺服器。</span><span class="sxs-lookup"><span data-stu-id="29599-103">This scenario shows a Windows Communication Foundation (WCF) client and server secured by message security mode.</span></span> <span data-ttu-id="29599-104">此用戶端和伺服器會以 Windows 認證進行驗證。</span><span class="sxs-lookup"><span data-stu-id="29599-104">The client and service are authenticated using Windows credentials.</span></span>  
  
 <span data-ttu-id="29599-105">![訊息安全性的 Windows 用戶端](../../../../docs/framework/wcf/feature-details/media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span><span class="sxs-lookup"><span data-stu-id="29599-105">![Message security with a Windows client](../../../../docs/framework/wcf/feature-details/media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span></span>  
  
|<span data-ttu-id="29599-106">特性</span><span class="sxs-lookup"><span data-stu-id="29599-106">Characteristic</span></span>|<span data-ttu-id="29599-107">描述</span><span class="sxs-lookup"><span data-stu-id="29599-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="29599-108">安全性模式</span><span class="sxs-lookup"><span data-stu-id="29599-108">Security Mode</span></span>|<span data-ttu-id="29599-109">訊息</span><span class="sxs-lookup"><span data-stu-id="29599-109">Message</span></span>|  
|<span data-ttu-id="29599-110">互通性</span><span class="sxs-lookup"><span data-stu-id="29599-110">Interoperability</span></span>|<span data-ttu-id="29599-111">WCF 只</span><span class="sxs-lookup"><span data-stu-id="29599-111">WCF Only</span></span>|  
|<span data-ttu-id="29599-112">驗證 (伺服器)</span><span class="sxs-lookup"><span data-stu-id="29599-112">Authentication (Server)</span></span>|<span data-ttu-id="29599-113">交互驗證伺服器和用戶端</span><span class="sxs-lookup"><span data-stu-id="29599-113">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="29599-114">驗證 (用戶端)</span><span class="sxs-lookup"><span data-stu-id="29599-114">Authentication (Client)</span></span>|<span data-ttu-id="29599-115">交互驗證伺服器和用戶端</span><span class="sxs-lookup"><span data-stu-id="29599-115">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="29599-116">完整性</span><span class="sxs-lookup"><span data-stu-id="29599-116">Integrity</span></span>|<span data-ttu-id="29599-117">是，使用共用安全性內容</span><span class="sxs-lookup"><span data-stu-id="29599-117">Yes, using shared security context</span></span>|  
|<span data-ttu-id="29599-118">機密性</span><span class="sxs-lookup"><span data-stu-id="29599-118">Confidentiality</span></span>|<span data-ttu-id="29599-119">是，使用共用安全性內容</span><span class="sxs-lookup"><span data-stu-id="29599-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="29599-120">Transport</span><span class="sxs-lookup"><span data-stu-id="29599-120">Transport</span></span>|<span data-ttu-id="29599-121">NET.TCP</span><span class="sxs-lookup"><span data-stu-id="29599-121">NET.TCP</span></span>|  
|<span data-ttu-id="29599-122">繫結</span><span class="sxs-lookup"><span data-stu-id="29599-122">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="29599-123">服務</span><span class="sxs-lookup"><span data-stu-id="29599-123">Service</span></span>  
 <span data-ttu-id="29599-124">下列程式碼和組態要獨立執行。</span><span class="sxs-lookup"><span data-stu-id="29599-124">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="29599-125">執行下列任一步驟：</span><span class="sxs-lookup"><span data-stu-id="29599-125">Do one of the following:</span></span>  
  
-   <span data-ttu-id="29599-126">使用不含組態的程式碼建立獨立服務。</span><span class="sxs-lookup"><span data-stu-id="29599-126">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="29599-127">使用提供的組態建立服務，但不要定義任何端點。</span><span class="sxs-lookup"><span data-stu-id="29599-127">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="29599-128">程式碼</span><span class="sxs-lookup"><span data-stu-id="29599-128">Code</span></span>  
 <span data-ttu-id="29599-129">下列程式碼會示範如何建立服務端點，而這個服務端點會使用訊息安全性來建立 Windows 電腦的安全內容。</span><span class="sxs-lookup"><span data-stu-id="29599-129">The following code shows how to create a service endpoint that uses message security to establish a secure context with a Windows machine.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#11)]
 [!code-vb[C_SecurityScenarios#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#11)]  
  
### <a name="configuration"></a><span data-ttu-id="29599-130">組態</span><span class="sxs-lookup"><span data-stu-id="29599-130">Configuration</span></span>  
 <span data-ttu-id="29599-131">可以使用下列組態取代程式碼來設定服務：</span><span class="sxs-lookup"><span data-stu-id="29599-131">The following configuration can be used instead of the code to set up the service:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration=""  
               name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"  
                  binding="netTcpBinding"  
                  bindingConfiguration="Windows"  
                  name="WindowsOverMessage"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="Windows">  
          <security mode="Message">  
            <message clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="29599-132">用戶端</span><span class="sxs-lookup"><span data-stu-id="29599-132">Client</span></span>  
 <span data-ttu-id="29599-133">下列程式碼和組態要獨立執行。</span><span class="sxs-lookup"><span data-stu-id="29599-133">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="29599-134">執行下列任一步驟：</span><span class="sxs-lookup"><span data-stu-id="29599-134">Do one of the following:</span></span>  
  
-   <span data-ttu-id="29599-135">使用此程式碼 (和用戶端程式碼) 建立獨立用戶端。</span><span class="sxs-lookup"><span data-stu-id="29599-135">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="29599-136">建立未定義任何端點位址的用戶端，</span><span class="sxs-lookup"><span data-stu-id="29599-136">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="29599-137">然後改用可接受組態名稱當做引數的用戶端建構函式。</span><span class="sxs-lookup"><span data-stu-id="29599-137">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="29599-138">例如：</span><span class="sxs-lookup"><span data-stu-id="29599-138">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="29599-139">程式碼</span><span class="sxs-lookup"><span data-stu-id="29599-139">Code</span></span>  
 <span data-ttu-id="29599-140">下列程式碼會建立用戶端。</span><span class="sxs-lookup"><span data-stu-id="29599-140">The following code creates a client.</span></span> <span data-ttu-id="29599-141">繫結會使用訊息模式安全性，而且用戶端認證類型設為 `Windows`。</span><span class="sxs-lookup"><span data-stu-id="29599-141">The binding is to Message mode security, and the client credential type is set to `Windows`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#18)]
 [!code-vb[C_SecurityScenarios#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#18)]  
  
### <a name="configuration"></a><span data-ttu-id="29599-142">組態</span><span class="sxs-lookup"><span data-stu-id="29599-142">Configuration</span></span>  
 <span data-ttu-id="29599-143">可使用下列組態來設定用戶端屬性。</span><span class="sxs-lookup"><span data-stu-id="29599-143">The following configuration is used to set the client properties.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
         <security mode="Message">  
            <message clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://machineName:8008/Calculator"   
                binding="netTcpBinding"  
                bindingConfiguration="NetTcpBinding_ICalculator"  
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">          
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="29599-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29599-144">See Also</span></span>  
 [<span data-ttu-id="29599-145">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="29599-145">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="29599-146">Windows Server App Fabric 的安全性模型</span><span class="sxs-lookup"><span data-stu-id="29599-146">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
