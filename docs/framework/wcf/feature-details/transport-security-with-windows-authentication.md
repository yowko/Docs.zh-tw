---
title: Windows 驗證的傳輸安全性
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
author: BrucePerlerMS
ms.openlocfilehash: babafe369ee9f5c9261e3b5c8bc749d3d1d39ec4
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2018
ms.locfileid: "47236445"
---
# <a name="transport-security-with-windows-authentication"></a><span data-ttu-id="f6335-102">Windows 驗證的傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="f6335-102">Transport Security with Windows Authentication</span></span>
<span data-ttu-id="f6335-103">下列案例示範 Windows Communication Foundation (WCF) 用戶端和服務由 Windows 安全性保護。</span><span class="sxs-lookup"><span data-stu-id="f6335-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by Windows security.</span></span> <span data-ttu-id="f6335-104">如需程式設計的詳細資訊，請參閱[如何： 使用 Windows 認證的服務安全](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)。</span><span class="sxs-lookup"><span data-stu-id="f6335-104">For more information about programming, see [How to: Secure a Service with Windows Credentials](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span></span>  
  
 <span data-ttu-id="f6335-105">內部網路 Web 服務顯示人力資源資訊。</span><span class="sxs-lookup"><span data-stu-id="f6335-105">An intranet Web service displays human resources information.</span></span> <span data-ttu-id="f6335-106">用戶端為 Windows Form 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f6335-106">The client is a Windows Form application.</span></span> <span data-ttu-id="f6335-107">應用程式部署於由 Kerberos 控制站負責網域安全的網域內。</span><span class="sxs-lookup"><span data-stu-id="f6335-107">The application is deployed in a domain with a Kerberos controller securing the domain.</span></span>  
  
 <span data-ttu-id="f6335-108">![傳輸安全性使用 Windows 驗證](../../../../docs/framework/wcf/feature-details/media/securedbywindows.gif "SecuredByWindows")</span><span class="sxs-lookup"><span data-stu-id="f6335-108">![Transport security with Windows authentication](../../../../docs/framework/wcf/feature-details/media/securedbywindows.gif "SecuredByWindows")</span></span>  
  
|<span data-ttu-id="f6335-109">特性</span><span class="sxs-lookup"><span data-stu-id="f6335-109">Characteristic</span></span>|<span data-ttu-id="f6335-110">描述</span><span class="sxs-lookup"><span data-stu-id="f6335-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="f6335-111">安全性模式</span><span class="sxs-lookup"><span data-stu-id="f6335-111">Security Mode</span></span>|<span data-ttu-id="f6335-112">Transport</span><span class="sxs-lookup"><span data-stu-id="f6335-112">Transport</span></span>|  
|<span data-ttu-id="f6335-113">互通性</span><span class="sxs-lookup"><span data-stu-id="f6335-113">Interoperability</span></span>|<span data-ttu-id="f6335-114">WCF 只</span><span class="sxs-lookup"><span data-stu-id="f6335-114">WCF only</span></span>|  
|<span data-ttu-id="f6335-115">驗證 (伺服器)</span><span class="sxs-lookup"><span data-stu-id="f6335-115">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="f6335-116">驗證 (用戶端)</span><span class="sxs-lookup"><span data-stu-id="f6335-116">Authentication (Client)</span></span>|<span data-ttu-id="f6335-117">是 (使用 Windows 整合式驗證)</span><span class="sxs-lookup"><span data-stu-id="f6335-117">Yes (using Windows integrated authentication)</span></span><br /><br /> <span data-ttu-id="f6335-118">是 (使用 Windows 整合式驗證)</span><span class="sxs-lookup"><span data-stu-id="f6335-118">Yes (using Windows integrated authentication)</span></span>|  
|<span data-ttu-id="f6335-119">完整性</span><span class="sxs-lookup"><span data-stu-id="f6335-119">Integrity</span></span>|<span data-ttu-id="f6335-120">是</span><span class="sxs-lookup"><span data-stu-id="f6335-120">Yes</span></span>|  
|<span data-ttu-id="f6335-121">機密性</span><span class="sxs-lookup"><span data-stu-id="f6335-121">Confidentiality</span></span>|<span data-ttu-id="f6335-122">是</span><span class="sxs-lookup"><span data-stu-id="f6335-122">Yes</span></span>|  
|<span data-ttu-id="f6335-123">Transport</span><span class="sxs-lookup"><span data-stu-id="f6335-123">Transport</span></span>|<span data-ttu-id="f6335-124">NET.TCP</span><span class="sxs-lookup"><span data-stu-id="f6335-124">NET.TCP</span></span>|  
|<span data-ttu-id="f6335-125">繫結</span><span class="sxs-lookup"><span data-stu-id="f6335-125">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="f6335-126">服務</span><span class="sxs-lookup"><span data-stu-id="f6335-126">Service</span></span>  
 <span data-ttu-id="f6335-127">下列程式碼和組態要獨立執行。</span><span class="sxs-lookup"><span data-stu-id="f6335-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="f6335-128">執行下列任一步驟：</span><span class="sxs-lookup"><span data-stu-id="f6335-128">Do one of the following:</span></span>  
  
-   <span data-ttu-id="f6335-129">使用不含組態的程式碼建立獨立服務。</span><span class="sxs-lookup"><span data-stu-id="f6335-129">Create a stand-alone service using the code with no configuration.</span></span>  
  
-   <span data-ttu-id="f6335-130">使用提供的組態建立服務，但不要定義任何端點。</span><span class="sxs-lookup"><span data-stu-id="f6335-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f6335-131">程式碼</span><span class="sxs-lookup"><span data-stu-id="f6335-131">Code</span></span>  
 <span data-ttu-id="f6335-132">下列程式碼顯示如何建立使用 Windows 安全性的服務端點。</span><span class="sxs-lookup"><span data-stu-id="f6335-132">The following code shows how to create a service endpoint that uses a Windows security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a><span data-ttu-id="f6335-133">組態</span><span class="sxs-lookup"><span data-stu-id="f6335-133">Configuration</span></span>  
 <span data-ttu-id="f6335-134">可使用以下組態來取代程式碼設定服務端點。</span><span class="sxs-lookup"><span data-stu-id="f6335-134">The following configuration can be used instead of the code to set up the service endpoint:</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="f6335-135">用戶端</span><span class="sxs-lookup"><span data-stu-id="f6335-135">Client</span></span>  
 <span data-ttu-id="f6335-136">下列程式碼和組態要獨立執行。</span><span class="sxs-lookup"><span data-stu-id="f6335-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="f6335-137">執行下列任一步驟：</span><span class="sxs-lookup"><span data-stu-id="f6335-137">Do one of the following:</span></span>  
  
-   <span data-ttu-id="f6335-138">使用此程式碼 (和用戶端程式碼) 建立獨立用戶端。</span><span class="sxs-lookup"><span data-stu-id="f6335-138">Create a stand-alone client using the code (and client code).</span></span>  
  
-   <span data-ttu-id="f6335-139">建立未定義任何端點位址的用戶端，</span><span class="sxs-lookup"><span data-stu-id="f6335-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="f6335-140">然後改用可接受組態名稱當做引數的用戶端建構函式。</span><span class="sxs-lookup"><span data-stu-id="f6335-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="f6335-141">例如：</span><span class="sxs-lookup"><span data-stu-id="f6335-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="f6335-142">程式碼</span><span class="sxs-lookup"><span data-stu-id="f6335-142">Code</span></span>  
 <span data-ttu-id="f6335-143">下列程式碼會建立用戶端。</span><span class="sxs-lookup"><span data-stu-id="f6335-143">The following code creates the client.</span></span> <span data-ttu-id="f6335-144">繫結會設定為使用傳輸模式安全性，採用 TCP 傳輸，並將用戶端認證類型設為 Windows。</span><span class="sxs-lookup"><span data-stu-id="f6335-144">The binding is configured to use the Transport mode security, with the TCP transport, with the client credential type set to Windows.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a><span data-ttu-id="f6335-145">組態</span><span class="sxs-lookup"><span data-stu-id="f6335-145">Configuration</span></span>  
 <span data-ttu-id="f6335-146">可使用以下組態來取代程式碼建立用戶端。</span><span class="sxs-lookup"><span data-stu-id="f6335-146">The following configuration can be used instead of the code to create the client.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f6335-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6335-147">See Also</span></span>  
 [<span data-ttu-id="f6335-148">安全性概觀</span><span class="sxs-lookup"><span data-stu-id="f6335-148">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [<span data-ttu-id="f6335-149">如何：利用 Windows 認證保護服務的安全</span><span class="sxs-lookup"><span data-stu-id="f6335-149">How to: Secure a Service with Windows Credentials</span></span>](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)  
 [<span data-ttu-id="f6335-150">Windows Server App Fabric 的安全性模型</span><span class="sxs-lookup"><span data-stu-id="f6335-150">Security Model for Windows Server App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
