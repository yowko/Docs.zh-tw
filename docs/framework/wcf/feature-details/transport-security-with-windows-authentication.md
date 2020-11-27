---
title: Windows 驗證的傳輸安全性
description: 請參閱此案例，其中顯示受 Windows 安全性保護的 WCF 用戶端/服務。 在此範例中，內部網路服務會顯示人力資源資訊。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
ms.openlocfilehash: 47f5a2a3b2c8815e2ccb0cc4d4bf3c408f4992e2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251733"
---
# <a name="transport-security-with-windows-authentication"></a><span data-ttu-id="c07da-104">Windows 驗證的傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="c07da-104">Transport Security with Windows Authentication</span></span>

<span data-ttu-id="c07da-105">下列案例顯示 Windows Communication Foundation (WCF) 用戶端，以及受 Windows 安全性保護的服務。</span><span class="sxs-lookup"><span data-stu-id="c07da-105">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by Windows security.</span></span> <span data-ttu-id="c07da-106">如需程式設計的詳細資訊，請參閱 [如何：使用 Windows 認證保護服務](../how-to-secure-a-service-with-windows-credentials.md)。</span><span class="sxs-lookup"><span data-stu-id="c07da-106">For more information about programming, see [How to: Secure a Service with Windows Credentials](../how-to-secure-a-service-with-windows-credentials.md).</span></span>  
  
 <span data-ttu-id="c07da-107">內部網路 Web 服務顯示人力資源資訊。</span><span class="sxs-lookup"><span data-stu-id="c07da-107">An intranet Web service displays human resources information.</span></span> <span data-ttu-id="c07da-108">用戶端為 Windows Form 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c07da-108">The client is a Windows Form application.</span></span> <span data-ttu-id="c07da-109">應用程式部署於由 Kerberos 控制站負責網域安全的網域內。</span><span class="sxs-lookup"><span data-stu-id="c07da-109">The application is deployed in a domain with a Kerberos controller securing the domain.</span></span>  
  
 ![使用 Windows 驗證的傳輸安全性](./media/transport-security-with-windows-authentication/secured-windows-authentication.gif)  
  
|<span data-ttu-id="c07da-111">特性</span><span class="sxs-lookup"><span data-stu-id="c07da-111">Characteristic</span></span>|<span data-ttu-id="c07da-112">描述</span><span class="sxs-lookup"><span data-stu-id="c07da-112">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="c07da-113">安全性模式</span><span class="sxs-lookup"><span data-stu-id="c07da-113">Security Mode</span></span>|<span data-ttu-id="c07da-114">傳輸</span><span class="sxs-lookup"><span data-stu-id="c07da-114">Transport</span></span>|  
|<span data-ttu-id="c07da-115">互通性</span><span class="sxs-lookup"><span data-stu-id="c07da-115">Interoperability</span></span>|<span data-ttu-id="c07da-116">僅限 WCF</span><span class="sxs-lookup"><span data-stu-id="c07da-116">WCF only</span></span>|  
|<span data-ttu-id="c07da-117">驗證 (伺服器)</span><span class="sxs-lookup"><span data-stu-id="c07da-117">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="c07da-118">驗證 (用戶端)</span><span class="sxs-lookup"><span data-stu-id="c07da-118">Authentication (Client)</span></span>|<span data-ttu-id="c07da-119">是 (使用 Windows 整合式驗證)</span><span class="sxs-lookup"><span data-stu-id="c07da-119">Yes (using Windows integrated authentication)</span></span><br /><br /> <span data-ttu-id="c07da-120">是 (使用 Windows 整合式驗證)</span><span class="sxs-lookup"><span data-stu-id="c07da-120">Yes (using Windows integrated authentication)</span></span>|  
|<span data-ttu-id="c07da-121">完整性</span><span class="sxs-lookup"><span data-stu-id="c07da-121">Integrity</span></span>|<span data-ttu-id="c07da-122">Yes</span><span class="sxs-lookup"><span data-stu-id="c07da-122">Yes</span></span>|  
|<span data-ttu-id="c07da-123">機密性</span><span class="sxs-lookup"><span data-stu-id="c07da-123">Confidentiality</span></span>|<span data-ttu-id="c07da-124">是</span><span class="sxs-lookup"><span data-stu-id="c07da-124">Yes</span></span>|  
|<span data-ttu-id="c07da-125">傳輸</span><span class="sxs-lookup"><span data-stu-id="c07da-125">Transport</span></span>|<span data-ttu-id="c07da-126">NET.TCP</span><span class="sxs-lookup"><span data-stu-id="c07da-126">NET.TCP</span></span>|  
|<span data-ttu-id="c07da-127">繫結</span><span class="sxs-lookup"><span data-stu-id="c07da-127">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="c07da-128">服務</span><span class="sxs-lookup"><span data-stu-id="c07da-128">Service</span></span>  

 <span data-ttu-id="c07da-129">下列程式碼和組態要獨立執行。</span><span class="sxs-lookup"><span data-stu-id="c07da-129">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="c07da-130">請執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="c07da-130">Do one of the following:</span></span>  
  
- <span data-ttu-id="c07da-131">使用不含組態的程式碼建立獨立服務。</span><span class="sxs-lookup"><span data-stu-id="c07da-131">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="c07da-132">使用提供的組態建立服務，但不要定義任何端點。</span><span class="sxs-lookup"><span data-stu-id="c07da-132">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c07da-133">程式碼</span><span class="sxs-lookup"><span data-stu-id="c07da-133">Code</span></span>  

 <span data-ttu-id="c07da-134">下列程式碼顯示如何建立使用 Windows 安全性的服務端點。</span><span class="sxs-lookup"><span data-stu-id="c07da-134">The following code shows how to create a service endpoint that uses a Windows security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a><span data-ttu-id="c07da-135">設定</span><span class="sxs-lookup"><span data-stu-id="c07da-135">Configuration</span></span>  

 <span data-ttu-id="c07da-136">可使用以下組態來取代程式碼設定服務端點。</span><span class="sxs-lookup"><span data-stu-id="c07da-136">The following configuration can be used instead of the code to set up the service endpoint:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"
                  binding="netTcpBinding"  
          bindingConfiguration="WindowsClientOverTcp"
                  name="WindowsClientOverTcp"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="WindowsClientOverTcp">  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="c07da-137">用戶端</span><span class="sxs-lookup"><span data-stu-id="c07da-137">Client</span></span>  

 <span data-ttu-id="c07da-138">下列程式碼和組態要獨立執行。</span><span class="sxs-lookup"><span data-stu-id="c07da-138">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="c07da-139">請執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="c07da-139">Do one of the following:</span></span>  
  
- <span data-ttu-id="c07da-140">使用此程式碼 (和用戶端程式碼) 建立獨立用戶端。</span><span class="sxs-lookup"><span data-stu-id="c07da-140">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="c07da-141">建立未定義任何端點位址的用戶端，</span><span class="sxs-lookup"><span data-stu-id="c07da-141">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="c07da-142">然後改用可接受組態名稱當做引數的用戶端建構函式。</span><span class="sxs-lookup"><span data-stu-id="c07da-142">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="c07da-143">例如：</span><span class="sxs-lookup"><span data-stu-id="c07da-143">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="c07da-144">程式碼</span><span class="sxs-lookup"><span data-stu-id="c07da-144">Code</span></span>  

 <span data-ttu-id="c07da-145">下列程式碼會建立用戶端。</span><span class="sxs-lookup"><span data-stu-id="c07da-145">The following code creates the client.</span></span> <span data-ttu-id="c07da-146">繫結會設定為使用傳輸模式安全性，採用 TCP 傳輸，並將用戶端認證類型設為 Windows。</span><span class="sxs-lookup"><span data-stu-id="c07da-146">The binding is configured to use the Transport mode security, with the TCP transport, with the client credential type set to Windows.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a><span data-ttu-id="c07da-147">設定</span><span class="sxs-lookup"><span data-stu-id="c07da-147">Configuration</span></span>  

 <span data-ttu-id="c07da-148">可使用以下組態來取代程式碼建立用戶端。</span><span class="sxs-lookup"><span data-stu-id="c07da-148">The following configuration can be used instead of the code to create the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://localhost:8008/Calculator"
                binding="netTcpBinding"
                bindingConfiguration="NetTcpBinding_ICalculator"
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c07da-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c07da-149">See also</span></span>

- [<span data-ttu-id="c07da-150">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="c07da-150">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="c07da-151">作法：使用 Windows 認證來確保服務安全</span><span class="sxs-lookup"><span data-stu-id="c07da-151">How to: Secure a Service with Windows Credentials</span></span>](../how-to-secure-a-service-with-windows-credentials.md)
- <span data-ttu-id="c07da-152">[Windows Server AppFabric 的資訊安全模型](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="c07da-152">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
